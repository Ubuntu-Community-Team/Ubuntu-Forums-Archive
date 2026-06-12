---
title: "Best distro for LAMP?"
date: 2007-05-09
forum: Server Platforms
---

### Post by TheGameAh on 2007-05-09
Getting ready to build a LAMP server for a small website and MySQL database.  Nothing fancy really.  Just a website that people will touch (employees and some sales reps).

Is there any reason to use one distro over another for LAMP?  I've got a lamp server running on Ubuntu 6.10.  No real problems with it, stable.  My buddy says though he uses Fedore Core, but couldn't offer a reason why.  I simply know Ubuntu better, so I was going to stick with it.  Any reason not to?

---

### Post by nix4me on 2007-05-09
Nope, stick with Ubuntu.  It's stable and supported.  Personal preference always plays into people's decisions.

nix4me

---

### Post by zvacet on 2007-05-09
Stick with Ubuntu.It will be supported for years.

---

### Post by Wim Sturkenboom on 2007-05-10
If it works, stick to it

PS  I use Slackware for my webservers as I grew up with it. I don't have experience with the Ubuntu LAMP setup, but Slackware is very easy to configure. Will probably move some of them to RH Enterprise due to business requirements.

---

### Post by TheGameAh on 2007-05-10
Thanks guys.

Next question.

Is there any real difference to use server over desktop version?  I admit, I'm used to a GUI.  Have trouble adding users or setting up FTP without it.  Could I just setup the desktop version will all I need then configure to boot without a GUI?

---

### Post by az on 2007-05-10
Just having the packages on your system already goes against best practices.  That being said, if this is just a small, private site, I wouldn't be worried.

Running a GUI on a webserver is not a security vulnerability in of itself.  The advantage is in not having to manage security for anything other than the webserver.  Anything more than just the webserver is more potential for vulerabilities.

---

### Post by StarMonkee on 2007-05-10
There isn't really a "best distro" for LAMP, it's all personal choices. I prefer debian/ubuntu because they are easy to setup and configure, and the support on the forums is very good.

---

### Post by Wim Sturkenboom on 2007-05-10
I would not use the GUI; a little reading will get you a long way. And in my opinion, you get a bit more insight as well from reading (man pages and the internet are your friends).

---

### Post by gonzalov on 2007-05-10
Well, for a server I wouldn't use Desktop as most daemons do not have GUIs for configuration. I use Ubuntu Dapper (LTS) server, no GUI, and I installed webmin. Works great and I have all the settings for everything. Just be sure to limit the access to your webmin server and close your firewall.

Webmin is not in any repository, you must download and dpkg to install. It's a little messy but I (mostly) wrote down the stuff I did when I installed it. If you're interested I'll look it up and post it.

---

### Post by dmizer on 2007-05-10
i'll second the "most daemons do not have gui".  if you're running a pure server, you'll find very little reason to use a gui.  in situations where it's convenient to use a point and click interface i'll also second the suggestion to make use of [webmin](http://www.webmin.com/).  webmin is a web interface where you can make adjustments to any of the server configurations via a point and click browser interface.

also seconding to make sure webmin's port isn't open to the world.

---

