---
title: "error 403 with cups administration"
date: 2008-03-26
forum: Server Platforms
---

### Post by tmillic on 2008-03-26
The web-browser based administration tool for CUPS results in error "403  Forbidden" pages for several of the tabs. I have added a printer successfully from a neighboring machine using ssh and printed a test page. I would like to be able to make this machine's printer available to other machines on the local network, but can't get past the forbidden pages. How do I fix the Error 403 problem?
I'm using Ubuntu 7.10, Server Edition with no GUI.
The printer is an HP Laser Jet 2300d.
Thanks.

---

### Post by sillyxone on 2008-03-26
edit /etc/cups/cupsd.conf, change the <location> settings to allow certain users to access. You can define <location /jobs>, <location /printers> separately too.

Look here for more information:
[http://cups.org/documentation.php/man-cupsd.conf.html](http://cups.org/documentation.php/man-cupsd.conf.html)

For example, my cupsd.conf:

> 
<Location />
  Allow all
  Order allow,deny
  Allow all
</Location>

<Location /admin>
  AuthType Default
  Require user @SYSTEM
  # Allow remote administration...
  Allow all
  Order allow,deny
</Location>

<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  Allow localhost
  Order allow,deny
</Location>


---

### Post by tmillic on 2008-03-27
Thanks.
That helped with the remote administration! 
:-)

---

### Post by dark_harmonics on 2008-05-04
> **sillyxone said:**
> edit /etc/cups/cupsd.conf, change the <location> settings to allow certain users to access. You can define <location /jobs>, <location /printers> separately too.

Look here for more information:
[http://cups.org/documentation.php/man-cupsd.conf.html](http://cups.org/documentation.php/man-cupsd.conf.html)

For example, my cupsd.conf:

This solved my access problem after hours of websearching!

---

