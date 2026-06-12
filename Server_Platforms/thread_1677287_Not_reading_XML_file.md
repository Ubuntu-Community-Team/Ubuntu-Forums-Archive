---
title: "Not reading XML file"
date: 2011-01-28
forum: Server Platforms
---

### Post by rgoessl on 2011-01-28
Hello,
 
I recently set up a server in my house using Apache 2 running off Ubuntu 10.10 Netbook edition (no, the computer is a desktop). I tried running the website on a few computers in house and all the images and scripts seem to load fine but it is unable to read from the data.xml file through javascript. This leaves all of the web pages empty because all of the content is parsed from the xml file through javascript. I tried debugging with google chrome and after running this code to load the xml file:
 
if (window.XMLHttpRequest) {
      // For IE7+, Firefox, Chrome, Opera, Safari
      xmlhttp = new XMLHttpRequest();
}
else {
      // IE6, IE5
      xmlhttp = new ActiveXObject("Microsoft.XMLHTTP");
}
 
xmlhttp.open("GET", "../data.xml", false);
xmlhttp.send();
 
xmlDoc = xmlhttp.responseXML;
 
the xmlhttp.responseXML is null and the script crashes. Could this be a permission issue? I tried setting the data.xml file to read-write permission for any user but that didn't work. Any help would be appreciated.

---

### Post by rgoessl on 2011-01-29
Okay, I figured it out. It was actually something really stupid. It turns out that the call to "../data.xml" was from the directory where the index.html file was rather than from the directory where the script was located (if that makes sense). In other words, it was looking for the file outside of the directory of the website and couldn't find the file :P. This must be some odd Ubuntu convention because it works fine when hosted from my windows computer.

---

