---
title: "Web interface for cd dvd writer burn"
date: 2009-06-28
forum: Server Platforms
---

### Post by Mouth on 2009-06-28
Hi All,

Am looking for a web interface to burning/writing to CD or DVD, but can't seem to find anything.

Using Ubuntu server for samba file server (amongst other things, incl. apache) and the server has a dvd writer within. So, via web interface, I would like to be able to select some file(s) and/or ISO stored on the server, and tell it to write/burn to the server DVD drive.

So all a user (read: wife, who can't/won't use ssh and command line) has to do is insert blank CD/DVD into the server's drive and then from her PC use the web interface to select file(s) and or ISO to write/burn to the inserted disc. A short time later, viola! disk is written.

Anyone seen anything to do this? I searched the PHP script sites but found nothing.

Thanks.

---

### Post by marcus2004 on 2009-06-28
I had a look online and saw:
[http://joerghaeger.de/webCDwriter/]("http://joerghaeger.de/webCDwriter/")
I haven't tried it.
I have been kind of looking for something like this as well. Right now I just have the wife use VNC or freenx to connect the computer, but I would like to make it a true server with no desktop.

---

### Post by bigbearomaha on 2009-06-29
One of the featurees in Webmin is a cd/dvd writing module.  It allows you to log in to Webmin and burn to a writer over the Webmin web interface

Big Bear

---

