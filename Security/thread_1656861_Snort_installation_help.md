---
title: "Snort installation help"
date: 2010-12-31
forum: Security
---

### Post by Silas1066 on 2010-12-31
:confused:I built an Ubuntu 10.1 server to run the latest version of Snort, but I am having some trouble with the installation.
 
I managed to get Snort pretty much installed, along with MySQL, and I got the database configured. Webmin and Gnome are also installed on the machine.
 
However, according to the Snort documentation I have been using, I need to install BASE and Abodb by issuing the commands
 
[FONT=Courier New]pear install --alldeps Mail[/FONT]
[FONT=Courier New]pear install --alldeps Mail_Mime[/FONT]
pear install --alldeps Image_Canvas-0.3.2
pear install --alldeps Image_Graph-0.7.2
 
When I type the first command, I don't get anything. System just sits there like the process is hung up. I'm not familiar with Pear, so I am not sure what this is trying to do.
 
I've been using the documentation at
 
[http://it.thelibrarie.com/weblog/2010/06/installing-snort-on-ubuntu-10-04/](http://it.thelibrarie.com/weblog/2010/06/installing-snort-on-ubuntu-10-04/)
 
Any help here would be greatly appreciated!

---

### Post by mail2345 on 2010-12-31
Try this instead(worked for me):
```
pear install Image_Color Image_Canvas-alpha Image_Graph-alpha Mail Mail_Mime
```
Both commands install various dependencies for BASE, but this command only installs the needed packages, unlike the command you tried, which installs optional packages as well.

---

