# Ex.07 Design of Interactive Image Gallery
# Date:15-12-25
# AIM:
To design a web application for an inteactive image gallery with minimum five images.

# DESIGN STEPS:
## Step 1:
Clone the github repository and create Django admin interface.

## Step 2:
Change settings.py file to allow request from all hosts.

## Step 3:
Use CSS for positioning and styling.

## Step 4:
Write JavaScript program for implementing interactivity.

## Step 5:
Validate the HTML and CSS code.

## Step 6:
Publish the website in the given URL.

# PROGRAM :
gallery.html
```
{% load static %}
<html>
<head>

    <title>Image Gallery</title>
    <link rel="stylesheet" href="{% static 'gal.css' %}"
</head>
<body>

<h1>My Image Gallery</h1>

<div class="gallery" id="gallery">
    <img src="{% static 'cat1.jpg' %}" onclick="openImage(this)">
    <img src="{% static 'cat2.jpg' %}" onclick="openImage(this)">
    <img src="{% static 'cat3.jpg' %}" onclick="openImage(this)">
    <img src="{% static 'cat4.jpg' %}" onclick="openImage(this)">
    <img src="{% static 'cat5.jpg' %}" onclick="openImage(this)">
</div>

<div id="zoombox">
    <span class="close" onclick="closeImage()">&times;</span>
    <img id="zoombox-img">
</div>
<script>
    function openImage(img) {
        const zoombox = document.getElementById("zoombox");
        const zoomboxImg = document.getElementById("zoombox-img");
        const gallery = document.getElementById("gallery");

        zoombox.style.display = "flex";
        zoomboxImg.src = img.src;
        gallery.classList.add("fade");
    }

    function closeImage() {
        document.getElementById("zoombox").style.display = "none";
        document.getElementById("gallery").classList.remove("fade");
    }
</script>

</body>
</html>
```
gal.css
```
body {
    font-family: Arial, sans-serif;
    text-align: center;
    background: #f5f5f5;
}

.gallery {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    gap: 15px;
}

.gallery img {
    width: 100%;
    max-width: 320px;   
    height: 220px;      
    object-fit: cover;
    cursor: pointer;
    transition: transform 0.3s , opacity 0.3s ;
}

.gallery img:hover {
    transform: scale(1.1);
}
#zoombox{
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    display: none;
    background: rgba(0, 0, 0, 0.85);
    justify-content: center;
    align-items: center;
    z-index: 1000;
}

#zoombox img {
    max-width: 80%;
    max-height: 80%;
}

.close {
    position: absolute;
    top: 20px;
    right: 40px;
    font-size: 40px;
    color: white;
    cursor: pointer;
}

.gallery.fade img {
    opacity: 0.3;
}
```
urls.py
```
from django.contrib import admin
from django.urls import path
from myapp import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('',views.gal),
    

]
```
views.py
```
from django.shortcuts import render
def gal(request):
    return render(request,'gallery.html')


```
# OUTPUT:

![alt text](<Screenshot (125).png>)
![alt text](<Screenshot (126).png>)
![alt text](<Screenshot (127).png>)
![alt text](<Screenshot (128).png>)
![alt text](<Screenshot (129).png>)
![alt text](<Screenshot (130).png>)






# RESULT:
The program for designing an interactive image gallery using HTML, CSS and JavaScript is executed successfully.
