---
title: "SOAP extension in Apache"
date: 2010-06-18
forum: Server Platforms
---

### Post by penguin1309 on 2010-06-18
I'm completely new to Linux- started on Sunday....

I've just set up Ubuntu Server 10.04 with LAMP, SSH and Tomcat setup. I've installed Red5 and openmeetings and got everything working successfully. I now just need to add SOAP and I think cURL extensions to apache.

I've used apt-get install to install php-soap and cURL libraries. How do I now activate them? I've looked in the the 2 php.ini files I could find- apparently you need to remove a ";" from the line describing the extension? I could not find anything for SOAP? 

Can anyone provide some direction or advise on how to do this?

I've been successful in setting this all up in WAMP in Windows before- but I really want to get it working in Linux- I think it will be better in the long run...

---

### Post by Ryan Dwyer on 2010-06-18
These are PHP extensions, not Apache modules. You can install them using:

sudo apt-get install php5-curl php-soap

---

### Post by penguin1309 on 2010-06-19
Sorry about the title...

I have already installed them- do I need to activate them somehow?

---

### Post by Ryan Dwyer on 2010-06-19
For soap, you can just write $soap = new soapclient; in your PHP script.

For curl, you should be able to use the curl functions documented at [http://php.net/curl](http://php.net/curl). If it doesn't work, check /etc/php5/conf.d/curl.ini - the extension line should be uncommented.

---

