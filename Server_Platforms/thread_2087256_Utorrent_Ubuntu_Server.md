---
title: "Utorrent Ubuntu Server"
date: 2012-11-23
forum: Server Platforms
---

### Post by nonly1n on 2012-11-23
Hi, 

I have utserver installed and running on a box with Ubuntu Server 12.10. 

Its my first time running the server version of Ubuntu and have limited knowledge on how to go about doing certain things.

Returning to the utserver problem. When I was running ordinary ubuntu what I'd usually have to do is go to localhost:8080/gui/ to access the webui. My question is, how do I go  about going to this webUI from another computer. 

I've already tried ipaddress:port/gui/ but to no avail.

is there a particular way i should set it up and btw I don't have any desktop environments installed (don't intend on doing this)

If anyone knows a workaround or a link to instructions on how to do this please let me know.

---

### Post by grahammechanical on 2012-11-23
First, may I say that the Networking and Wireless section of the forum is the best place to ask this question. It is the section set aside for networking problems. Whereas, this section is set aside for those using the development release of Ubuntu - Ubuntu+1 (Raring ringtail) and you are using 12.10 which is now a released version.

You ask this:

> how do I go about going to this webUI from another computer?

What operating system is on that computer? Is that not relevant? If you are trying to access Ubuntu server from a Ubuntu 12.10 computer then this may be of help:

[http://www.omgubuntu.co.uk/2012/09/ubuntu-12-10-login-screen-adds-remote-desktop-access]("http://www.omgubuntu.co.uk/2012/09/ubuntu-12-10-login-screen-adds-remote-desktop-access")

The people with networking experience give help on the Networking and wireless section of the forum.

Regards.

---

### Post by nonly1n on 2012-11-23
Go ya didn't realise where I was posting this. but thanks for the heads up and its from a computer running OS X 10.8

> **grahammechanical said:**
> First, may I say that the Networking and Wireless section of the forum is the best place to ask this question. It is the section set aside for networking problems. Whereas, this section is set aside for those using the development release of Ubuntu - Ubuntu+1 (Raring ringtail) and you are using 12.10 which is now a released version.

You ask this:



What operating system is on that computer? Is that not relevant? If you are trying to access Ubuntu server from a Ubuntu 12.10 computer then this may be of help:

[http://www.omgubuntu.co.uk/2012/09/ubuntu-12-10-login-screen-adds-remote-desktop-access]("http://www.omgubuntu.co.uk/2012/09/ubuntu-12-10-login-screen-adds-remote-desktop-access")

The people with networking experience give help on the Networking and wireless section of the forum.

Regards.

---

### Post by cariboo on 2012-11-23
Moved to server platforms.

---

### Post by darkod on 2012-11-23
If you didn't enabled any firewall on the server, you should be able to access the same GUI with:
ip:8080

Try without the gui in the address line because sometimes it might be added automatically or can work without it.

Also, make sure you know the exact IP of the server and that it's static, so that it doesn't change.

---

### Post by nonly1n on 2012-12-29
> **darkod said:**
> If you didn't enabled any firewall on the server, you should be able to access the same GUI with:
ip:8080

Try without the gui in the address line because sometimes it might be added automatically or can work without it.

Also, make sure you know the exact IP of the server and that it's static, so that it doesn't change.

Ip is static and whenever i put in my ip:8080 i get this (see below) which just pretty much tells me its running... sorry for the late response I've been caught up with life problems. 

[HTML]It works !

If you're seeing this page via a web browser, it means you've setup Tomcat successfully. Congratulations!

This is the default Tomcat home page. It can be found on the local filesystem at: /var/lib/tomcat7/webapps/ROOT/index.html

Tomcat7 veterans might be pleased to learn that this system instance of Tomcat is installed with CATALINA_HOME in /usr/share/tomcat7 and CATALINA_BASE in /var/lib/tomcat7, following the rules from /usr/share/doc/tomcat7-common/RUNNING.txt.gz.

You might consider installing the following packages, if you haven't already done so:

tomcat7-docs: This package installs a web application that allows to browse the Tomcat 7 documentation locally. Once installed, you can access it by clicking here.

tomcat7-examples: This package installs a web application that allows to access the Tomcat 7 Servlet and JSP examples. Once installed, you can access it by clicking here.

tomcat7-admin: This package installs two web applications that can help managing this Tomcat instance. Once installed, you can access the manager webapp and the host-manager webapp.

NOTE: For security reasons, using the manager webapp is restricted to users with role "manager-gui". The host-manager webapp is restricted to users with role "admin-gui". Users are defined in /etc/tomcat7/tomcat-users.xml.[/HTML]

---

### Post by darkod on 2012-12-29
As the message says, that is the default Tomcat confirmation page which means the webserver is functioning properly.

Next you need to figure out why the web interface is not opening up and whether you need to do some adjustments.

I have no idea how utserver works, maybe you can refer to some documentation which can help you.

---

