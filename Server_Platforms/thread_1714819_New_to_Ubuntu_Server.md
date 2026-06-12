---
title: "New to Ubuntu Server"
date: 2011-03-25
forum: Server Platforms
---

### Post by ShadowInTheDark on 2011-03-25
I'm completely new to Ubuntu Server, and I've looked around everywhere for information on setting it up, but it's like I can't follow a lot of the instruction guides very well (usually there's a problem, like I started differently than the instruction guide and it completely messes everything up).

I don't know exactly how to wire up the computer (right now I need my internet so I can keep learning how to do it obviously ><, but later I don't know how to set it up). One of my problems is I don't have internet connection (atleast I don't think I do), and I don't know how much of an issue this would be.. But my major priority right now is to get OpenSSH set up so I can have my other computer as Remote controller.

So far about only thing I've done successfully is edit the "/etc/network/interfaces" to a static IP. And when I type "sudo nano /etc/resolv.conf" it gives me a blank file.

(don't even know if I posted this in right place ><)

---

### Post by lisati on 2011-03-26
Welcome to the forum.

Ubuntu server is capable of doing many server-type tasks and I'd suggest focussing on one thing at a time. Some examples of what it can do include file sharing, email and web pages.

What kind of server do you want to focus on first?

---

### Post by ShadowInTheDark on 2011-03-26
I suppose file sharing. I wanted a home server that I could connect all computers to.

---

### Post by SeijiSensei on 2011-03-26
If you've never used Ubuntu (or Linux) before, and even if you have, I recommend installing the normal desktop version, then installing the server packages you discover you need along the way.  After you get comfortable with the desktop, I'd next install the "samba" packages which will let you set up the machine to be a file server for Windows, Macs, and Linux machines.  You'll find lots of tutorials on using Samba to serve files like [this one]("https://help.ubuntu.com/community/Samba").

Anything you can install on the server version can be installed on the desktop version as well.  If you're not especially comfortable using the command line, the desktop version is a better starting point.

---

### Post by ShadowInTheDark on 2011-03-26
I'm comfortable with using the command lines, I just don't know exactly what to do.. especially when files like "/etc/resolv.conf" are missing.. which seems to be rare.. I heard that I need that file to connect to internet...

---

### Post by ShadowInTheDark on 2011-03-26
I got OpenSSH working and now I can remotely connect to the computer with my main one. Now I'm a little more lost in exactly where to go next. ><

---

### Post by SeijiSensei on 2011-03-27
I'd start with [this](https://help.ubuntu.com/community/Samba).

---

### Post by mw4jet on 2011-03-27
I have set up a few headless servers using putty and webmin from internet page. The how to I have linked below is intended to be "a don't skip any steps" way to do it, but I have used some and not all. The how to in my opinion is what kept me from throwing in the towel on command line. seems I'm getting into it more and more and actually am enjoying it!!
 
Kevin Woodel is linked somewhere on this board I just can't find it now. He uses Debian, but I find Ubuntu to be nearly identical after the initial install.
 
[http://woodel.com/](http://woodel.com/)
 
Mark

---

### Post by nosebreaker on 2011-03-27
If you could ask a more specific question you'll probably get more specific answers :)  If you could provide more information about your existing network that would be good as well.  For example do you have 2 computers (your windows desktop and the ubuntu desktop you are trying to setup), along with a home router (like a linksys) that shares your internet connection?

Are you looking to share files?  Try the samba link above.  Are you looking to run a webserver internally?

---

