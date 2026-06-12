---
title: "Citrix server equivalent"
date: 2007-01-22
forum: Server Platforms
---

### Post by dawesy on 2007-01-22
I'm a Linux noob, and defiently a Linux server noob, with an edgy box I've built up with Apache and MySQL supporting Bugzilla and subversion, which we integrated.  The business owner of the server would also like to set it up so we can use it like a citrix server, where they can log into a GUI environmtnt remotely and run some apps.  The box was overspeced for this reason.

Problems is I have never ruun Linix with GUI before, this one is still CLI only.  Looked at VNC and FreeNX but they have limitatoins, and for multiple sessions they don't work.  Can I do this with the native X, assuming I can find a Windows client (I think I used one called reflection X at another company as a User)?  Any direction to some focused (ie for dummies) doco to get me started would be appreciated.  I have searched hard but only found remote admin solutions that won't work when I have 5 people connecting at once, and I don't want to have to maintain a console session, in fact if I can avoid running the GUI on the console i'd be happy as I'll never sit there so why take the resources!

Also, while free is good, if we have to use something commercial (say the full freeNX) to get an elegant solution we probably can, but I can't imagine it's needed.

Thanks.

---

### Post by dawesy on 2007-01-30
Wow, though this would be a no-brainer... perhaps it is and the deafening silence is a quiet RTFM?  Hope so as I guess I'm googling this one!!

---

### Post by Hanzerik on 2007-01-30
With VNC you can have more then one user logged in. The same user can have multiple sessions even. BUT, they will need to know which vnc session they are logging into.

Say I fire up my first vnc session and it is listening on port 5901, when I start up another the port will auto increment one up to 5902.

So in theory you can setup your vnc client to connect to that server as many times as you have different vnc sessions.

And if you are worried about speed, then use a lighter window manager instead of Gnome. I personnaly use fluxbox. And vnc4server performs better then ealier versions. Do not use VINO as it is a major bandwidth hog. I have never used nx, and it's been a very long time since I setup and configured a Citrix Client/Server system.

Another option, if you will only be using a few different apps, may be X forwarding to run those apps on the Linux box, but display them on a local machine. I have only used one windows based x server (HummingBird Exceed), so I don't know of any other right off hand. 

Here is a topic that may help you out. [http://www.ubuntuforums.org/showthread.php?t=122402&highlight=resumable+sessions](http://www.ubuntuforums.org/showthread.php?t=122402&highlight=resumable+sessions)

Oh, by the way did you install the server install from the server iso, or did you install a full blown Ubuntu install?

---

### Post by Hanzerik on 2007-01-30
Here is another link, not Ubuntu specific, but may help you out. 
[http://www.debian-administration.org/articles/432](http://www.debian-administration.org/articles/432)

This is the method I used on my own server, except I didn't install a login manager, (I didn't need a login manager because all I wanted was a remote desktop running with the fewest processes running. I just installed:
apt-get install xserver-xorg-core xorg
apt-get install fluxbox
apt-get install vnc4server

I have a script to fire up my vnc session that I run by logging in through ssh, then executing the script and log out of ssh, My vnc session is up and running waiting for me to login.

---

### Post by dawesy on 2007-01-31
Thanks, about to start some reading.

The install was formn the server ISO yes, so it's quite minimal, which is my preference.  COming from a Windows world this has been as steep learning curve.  I've done work on Linux before, but mostly programming and some apache 1 managemant.  In any case, I can see myself moving towards Linux more in the future.

---

