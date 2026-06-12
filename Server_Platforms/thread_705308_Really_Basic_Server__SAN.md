---
title: "Really Basic Server / SAN"
date: 2008-02-23
forum: Server Platforms
---

### Post by tmoore4748 on 2008-02-23
I'm hoping to create my own SAN / NAS with Ubuntu, but here's the hard part: I'm basically familiar with Ubuntu/Linux, but I'm still beginning.  I've been using FreeNAS for a while, but it won't recognize my SATA drive without a controller card, which is just more money to spend.

What I want is a basic server (or glorified NAS, if you want it put that way) that I can administer through a web interface.  I've seen a few programs that I could install under Ubuntu that would allow me to do just that, but the choices are far too confusing.  Anyone got any ideas?

---

### Post by jonabyte on 2008-02-23
Try using the desktop version of Ubuntu, then install Samba to serve your files.
I have a system at home with a sata drive and 7.04 was able to install without any issues.

---

### Post by tmoore4748 on 2008-02-23
what is it that you mean by installing Samba?  Just put in the file protocol package?

If it's just that, the it's easy.  But, there's one big problem: I need a web interface to make the server headless.  If I can't do that, I'll probably still install all the stuff, but I don't want to of I don't have to.  By using a web interface, I can administer from any computer, as well as have a guaranteed static route to use over the internet if necessary

---

### Post by littlegreiger on 2008-02-23
For my headless server I use [Webmin]("http://www.webmin.com/") and it works great. It lets you do pretty much anything you want. It even has a configuration tool for samba shares. Or you could go with a VNC program, unfortunately I haven't tried any on Ubuntu so I can't comment on that.

---

