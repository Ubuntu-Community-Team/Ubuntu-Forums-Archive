---
title: "Need a Web server with GUI"
date: 2009-08-19
forum: Server Platforms
---

### Post by Jerry.S on 2009-08-19
What I want to do is to set up a server with a lite weight GUI with no other programs except XAMPP.

First Idea: Ubuntu server, a lite weight desktop gui and be able to in stall xampp

Second idea: Ubuntu Server built with the lamp option and then install a web gui and a lite desktop with what i need to access the lamp programs.

By the way I have a extra computer to build this on

---

### Post by TwiceOver on 2009-08-19
Option 2.  XAMPP is great and all, but you can have all of that installed by default on the server install.

If all you need a GUI for is administrating your LAMP server, why not look at webmin instead.  That way you don't have to run a GUI at all.

---

### Post by Jerry.S on 2009-08-20
Ok after reading alot of post reguarding servers, gui's and security I have decided to dump the gui end and go with webmin.

Next Q? How to in stall webmin. Would I just (sudo apt-get install webmin) or do I need to use something diffrent

---

### Post by jerz on 2009-08-21
[http://www.webmin.com/deb.html](http://www.webmin.com/deb.html)
I would recommend using the APT repo as all dependencies are resolved automatically.

---

