---
title: "Will Ubuntu server run html?"
date: 2009-02-04
forum: Server Platforms
---

### Post by AngusMcBurger on 2009-02-04
I'm really not very clever with linux software and wanted to ask, will ubuntu server edition 8.10 run html webpage coding? It might sound a bit obvious but I'm very new to linux,
Cheers!

---

### Post by Simian Man on 2009-02-04
The only thing that "runs" HTML is a web browser.  All operating systems come with a web browser so yes.  If you want to set up a web server to answer requests for HTML pages then you need Apache installed.

What exactly do you want?

---

### Post by ridetheteapot on 2009-02-04
yes. apache.

otherwise jetty on a workstation will work to

---

### Post by AngusMcBurger on 2009-02-04
Well just a server to run a website on if you know what I mean! Or in your words, answer requests for html!!

---

### Post by Simian Man on 2009-02-04
Ah OK it sounded like you maybe just wanted to learn HTML.  Yeah Ubuntu server is a good web server then.

---

### Post by tubezninja on 2009-02-04
When you install Ubuntu Server edition from CD, one of the options is to set up a LAMP (**L**inux **A**pache **M**ySQL **P**HP) configuration.  This is the easiest way to get a viable web server up and running, and it also includes scripting (PHP) and back end database (MySQL) functions if you want to host dynamically created web content.  

Once installed, you throw all of your HTML into the /var/www directory, and the server will serve the content.

There also this documentation if you want to know more (or know how to set up LAMP on an already-running system:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

This page refers to some older versions of Ubuntu, but the commands to install, as well how to configure everything, is still relevant to current versions of Ubuntu.

---

