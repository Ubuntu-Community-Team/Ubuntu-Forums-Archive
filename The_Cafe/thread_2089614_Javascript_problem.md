---
title: "Javascript problem?"
date: 2012-11-29
forum: The Cafe
---

### Post by Gogeden on 2012-11-29
I need some help with something I'm developing.
  

I'm trying to make it so that a person can pass an URL into a text  field, hit a submit button, and have some javascript replace URLs inside object tags with the URL that was submitted in the text box and then the page  refreshes and that new video is spooled up.
  

I'm struggling with the replacing the URL in the code part. How can I use string.replace or something similar in JS to replace the  URLs in the object  tags with the one in the text field when someone clicks the  submit button underneath it?
  Thank you! :)

---

### Post by pqwoerituytrueiwoq on 2012-11-29
if this is homework stop reading now and go to w3schools.com
i am confided by what you are trying to do
if you want to change the url in a video element yuo can change the source's url
```
document.getElementById("MyVIdeoElementId").childNodes[0].src="MY_URL";
``````
var ele=document.getElementById("MyVIdeoElementId").childNodes[0];
ele.src=ele.src.replace('find me','replace with');
```to click a button use the click function
```
document.getElementById("MyButtonId").click();
```
it set text in a input field set the value attribute
```
myinputfield.value='myvalue';
```

---

