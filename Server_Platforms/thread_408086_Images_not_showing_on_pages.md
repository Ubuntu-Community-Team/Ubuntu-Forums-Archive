---
title: "Images not showing on pages"
date: 2007-04-12
forum: Server Platforms
---

### Post by kenboyles72 on 2007-04-12
I got Apache config'd and running. Transferred all my files to web folder, but when I go to my site, none of the pics show up. Here's the addy for my site, [easttexasmicrotech.com/]("http://www.easttexasmicrotech.com/"). Here's a sample code for one of my images.

<div align="center"><img alt="East_Texas_Microtech_Ngreen_banner.jpg" src="images/East_Texas_Microtech_Ngreen_banner.jpg"/></div>

the file structure and paths are the same as it is on my windows server running Apache.

---

### Post by Zwalther on 2007-04-12
Your directory is called "Images" and the src attribute says "images".

The filesystem is case sensitive.

---

### Post by kenboyles72 on 2007-04-12
dang, forgot about Linux being picky about upper/lower case letters. :rolleyes: no biggy, thats an easy fix.

---

