# my_flask_app
Flask app demo
Prerequisites
Python 3 installed on your system.
pip, the Python package installer, installed. 
1. Install Flask
Open your terminal or command prompt and run the following command to install Flask: 
bash
pip install Flask
Use code with caution.

This command installs the Flask library, providing the necessary tools to build your web application. 
2. Create the Flask app
Create a project directory: Create a new folder for your project and navigate into it using your terminal:
bash
mkdir my_flask_app
cd my_flask_app
Use code with caution.

This helps organize your project files.
Create app.py: Create a new Python file named app.py within your project directory. This file will contain your Flask application code.
python
# Import the Flask class from the flask module
from flask import Flask

# Create an instance of the Flask class
app = Flask(__name__)

# Define a route and a function to handle requests to that route
@app.route('/')
def hello_world():
    return 'Hello, World!'

# Run the application
if __name__ == '__main__':
    app.run(debug=True) # Enables debug mode, showing errors in the browser and auto-reloading changes
Use code with caution.

from flask import Flask: Imports the Flask class, which is used to create and manage the web application.
app = Flask(__name__): Creates an instance of the Flask class. The __name__ variable tells Flask the module's name, helping it locate resources like templates and static files.
@app.route('/'): This is a decorator that tells Flask which URL should trigger the associated function. In this case, / represents the root URL of your application.
def hello_world():: This function is executed when the root URL is accessed. It returns the string "Hello, World!", which will be displayed in the browser.
if __name__ == '__main__': app.run(debug=True): This code ensures the application runs only when the script is executed directly (not imported as a module). debug=True activates debug mode, which provides helpful error messages in the browser and automatically reloads the server when code changes are detected. 
3. Run the web application
Save the app.py file and return to your terminal. Navigate to your project directory (if you're not already there) and run the following command: 
bash
python app.py
Use code with caution.

You should see output similar to this: 
 * Serving Flask app 'app'
 * Debug mode: on
 * Running on http://127.0.0.1:5000 (Press CTRL+C to quit)
Open your web browser and navigate to the URL provided (usually http://127.0.0.1:5000). You should now see the "Hello, World!" message displayed in your browser. 
4. Using HTML templates (optional but recommended for dynamic content)
Flask integrates with the Jinja2 template engine to create more visually appealing and dynamic web pages, according to Flask documentation. 
Create a templates folder: Create a folder named templates in your project directory (at the same level as app.py). Flask automatically looks for HTML templates in this folder by default.
Create an index.html file: Inside the templates folder, create a new HTML file named index.html and add the following content:
html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Flask App</title>
</head>
<body>
    <h1>{{ message }}</h1>
</body>
</html>
Use code with caution.

The double curly braces {{ message }} use Jinja2 syntax to render variables passed from the Flask app.
Modify app.py to render the template: Update your app.py file to render the index.html template and pass a variable to it:
python
from flask import Flask, render_template

app = Flask(__name__)

@app.route('/')
def home():
    return render_template('index.html', message='Welcome to my Flask App!')

if __name__ == '__main__':
    app.run(debug=True)
Use code with caution.

from flask import Flask, render_template: render_template is imported to display HTML templates.
return render_template('index.html', message='Welcome to my Flask App!'): This line tells Flask to render the index.html template and pass the string "Welcome to my Flask App!" as the message variable.
Restart the web app and refresh: Restart your Flask application (stop it using CTRL+C and rerun python app.py) and refresh your browser. The message from your index.html template, "Welcome to my Flask App!" should now be visible 