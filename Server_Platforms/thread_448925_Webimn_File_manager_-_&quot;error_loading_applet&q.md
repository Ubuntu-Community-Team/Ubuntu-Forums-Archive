---
title: "Webimn File manager - &quot;error loading applet&quot;"
date: 2007-05-19
forum: Server Platforms
---

### Post by tiger.woods on 2007-05-19
Anyone know how to fix Webmin's "error loading applet" problem??

TW,

---

### Post by Bill007 on 2007-05-19
Its not a Webmin Problem

This is a Browser Problem You need to look into your JAVA module EXTENSIONS

Try IN Mozilla Firefox  TOOLS > OPTIONS>CONTENT  Make sure all the java boxes are checked there make sure you have the latest download of java extension

Also you could  have a few older versions of JAVA sitting there 

 The browser can call old versions over the new Versions  even though it may say you have the latest version the browser can still reference the old version  You can google this Ive had to do but cant remember exactly how but it is easy

Also try in a windowz Browser JAVA BUILT IN HERE  see if it works in that for the time being 


BILL

---

### Post by tiger.woods on 2007-05-20
Dead on! I simply had to install jre with apt-get.

Thanks,

---

