Creating a static website using Flask is straightforward. Although Flask is often used for dynamic websites, it can also serve static files like HTML, CSS, and JavaScript to build a simple static site.

Here’s a step-by-step guide for setting up a static website using Flask.

### 1. Project Structure
To create a static website, set up your project like this:
```
my_flask_app/
├── app.py
├── static/
│   ├── css/
│   │   └── style.css
│   ├── js/
│   │   └── script.js
│   └── images/
│       └── logo.png
└── templates/
    └── index.html
```

- **`app.py`**: Main Flask application file.
- **`static/`**: Folder to store static files like CSS, JavaScript, and images.
- **`templates/`**: Folder to store HTML files (using Flask’s templating engine, Jinja2).

### 2. Writing the Flask Application (`app.py`)
This is the main application file where we’ll create a Flask app to serve the static website.

```python
from flask import Flask, render_template

app = Flask(__name__)

@app.route("/")
def home():
    return render_template("index.html")

if __name__ == "__main__":
    app.run(debug=True)
```

- **`@app.route("/")`**: This defines the root route (`/`) that serves the main page.
- **`render_template("index.html")`**: Renders the `index.html` template located in the `templates` folder.

### 3. Creating the HTML Template (`templates/index.html`)
Create an HTML file with the basic structure for your static website.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Static Site</title>
    <link rel="stylesheet" href="{{ url_for('static', filename='css/style.css') }}">
</head>
<body>
    <header>
        <h1>Welcome to My Static Site</h1>
        <img src="{{ url_for('static', filename='images/logo.png') }}" alt="Logo">
    </header>
    <main>
        <p>This is a static site built with Flask.</p>
    </main>
    <script src="{{ url_for('static', filename='js/script.js') }}"></script>
</body>
</html>
```

- **`{{ url_for('static', filename='css/style.css') }}`**: This Jinja2 function generates the URL for static files, pointing to `style.css`.
- **`{{ url_for('static', filename='images/logo.png') }}`**: Similarly, this points to an image file in the `static/images` directory.

### 4. Adding CSS (`static/css/style.css`)
In the `static/css` folder, add a CSS file to style your page.

```css
body {
    font-family: Arial, sans-serif;
    text-align: center;
    color: #333;
}

header {
    background-color: #f8f9fa;
    padding: 20px;
    border-bottom: 1px solid #ddd;
}

main {
    margin: 20px;
}
```

### 5. Adding JavaScript (Optional) (`static/js/script.js`)
If you need JavaScript, create a file in `static/js/script.js`:

```javascript
document.addEventListener("DOMContentLoaded", function() {
    console.log("JavaScript is loaded!");
});
```

### 6. Running the Application
Run the application by executing the following command in your terminal:

```bash
python app.py
```

Go to `http://127.0.0.1:5000/` in your browser, and you should see the static website served by Flask!

### Summary
This setup allows Flask to serve static assets like CSS, JavaScript, and images. Although this approach uses Flask’s templating engine, the site remains static as it doesn’t have any backend processing or dynamic content. This setup is also a good starting point if you plan to later expand the site with dynamic elements.
