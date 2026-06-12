---
title: "Lamp server error: Permission denied to call method XMLHttpRequest.open"
date: 2008-11-24
forum: Server Platforms
---

### Post by rocheteau on 2008-11-24
Hi, 

I am trying to get to know AJAX but when I browse to the following index.html file on my Ubuntu LAMP server I get the following error message:

Permission denied to call method XMLHttpRequest.open

found via the Firefox JavaScript Console (and a much less informative Permission Denied message in Internet Explorer). 

If you can help it would be greatly appreciated.

Code for index.html:

<html>
  <head>
    <title>Ajax at work</title>
    <script language = "javascript">
       var XMLHttpRequestObject = false;
       if (window.XMLHttpRequest) {
         XMLHttpRequestObject = new XMLHttpRequest();
       } else if (window.ActiveXObject) {
         XMLHttpRequestObject = new ActiveXObject("Microsoft.XMLHTTP");
       }
       function getData(dataSource, divID)
       {
         if(XMLHttpRequestObject) {
           var obj = document.getElementById(divID);
           XMLHttpRequestObject.open("GET", dataSource);
           XMLHttpRequestObject.onreadystatechange = function()
           {
             if (XMLHttpRequestObject.readyState == 4 &&
               XMLHttpRequestObject.status == 200) {
                 obj.innerHTML = XMLHttpRequestObject.responseText;
             }
           }
           XMLHttpRequestObject.send(null);
         }
       }
    </script>
  </head>
  <body>
    <H1>Fetching data with Ajax</H1>
    <form>
      <input type = "button" value = "Display Message"
        onclick = "getData('http://localhost/ch02/data.txt',
        'targetDiv')">
    </form>
    <div id="targetDiv">
      <p>The fetched data will go here.</p>
    </div>
  </body>
</html>


I have not supplied the contents of data.txt i.e. it's just a line of text to test things out.

Thanks again in advance, 
R.

---

