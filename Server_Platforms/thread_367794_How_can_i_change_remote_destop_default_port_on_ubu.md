---
title: "How can i change remote destop default port on ubuntu"
date: 2007-02-22
forum: Server Platforms
---

### Post by edoras81 on 2007-02-22
as much as i know deault port is :5900  on remote desktop
How can i change remote destop default port  on ubuntu
for example (5900 to 10001)

or is it posible?
or do you have any advice for VNC securty..

---

### Post by AmazingRando on 2007-02-25
I've been searching online for about an hour without finding an answer to this same question.  :confused: 

At some point I want to do SSH and all that fancy stuff, but for right now I just need a quick solution so that I can access my machine when I'm in my school's library.  They block almost every port, so I need to set it at a port that's open (e.g. 3000).  With UltraVNC or TightVNC on Windows it's super simple. I don't understand why it should be anymore difficult on Ubuntu.

I did look at /etc/vnc.conf, but nothing about ports there.  Another site suggested /usr/bin/vncserver, but that's not there in this distro.

Anyone got any ideas?

AR

---

### Post by gitti on 2007-03-31
> **edoras81 said:**
> as much as i know deault port is :5900  on remote desktop
How can i change remote destop default port  on ubuntu
for example (5900 to 10001)

or is it posible?
or do you have any advice for VNC securty..

I have the same question.

---

### Post by gitti on 2007-04-01
> **gitti said:**
> I have the same question.

up

---

### Post by marvin0185 on 2007-06-22
Not much info on this, spent a hour or so googling but eventually found it.

[http://www.bani.com.br/2007/04/25/hidden-features-of-vino-remote-desktop-access/](http://www.bani.com.br/2007/04/25/hidden-features-of-vino-remote-desktop-access/)
^ Guide to changing port and setting vino to use the alternative port

[http://bugzilla.gnome.org/show_bug.cgi?id=361891](http://bugzilla.gnome.org/show_bug.cgi?id=361891)
^ This discusses the option of adding this into the preferences dialog in the future

Screengrab of my gconf-editor running

[IMG]http://members.iinet.net.au/~steven01/remote_access.png[/IMG]

Hope this helps.

Regards

Steven

---

### Post by gaten on 2007-06-22
>  or do you have any advice for VNC securty..

I'm going to shamelessly plug my own HOWTO for VNC over SSH, which will increase the security of your VNC session dramatically. The tutorial is in my sig if you're interested.

---

