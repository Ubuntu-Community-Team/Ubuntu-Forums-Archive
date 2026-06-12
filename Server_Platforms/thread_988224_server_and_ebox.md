---
title: "server and ebox"
date: 2008-11-20
forum: Server Platforms
---

### Post by happyhacker on 2008-11-20
Read about ebox for gui management. Followed a couple of tutorials:

[Here]("http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p3")
and
[here for the install]("http://www.howtoforge.com/running-a-file-and-print-server-with-ebox-on-ubuntu8.04-server")

Put this address in sources.list:

deb [http://ppa.launchpad.net/juruen/ubuntu](http://ppa.launchpad.net/juruen/ubuntu) intrepid main

ran "apt-get update" but this came up with a 404 so I guess no point in trying an install!

So far I've managed to install intrepid but have no GUI. Anyone help?

---

### Post by happyhacker on 2008-11-20
I have also seen this:[advice]("https://help.ubuntu.com/8.10/serverguide/C/ebox.html")

But if I follow this I get (not all reply typed here) "Some packages could not ...."
"The following packages have unmet dependancies. ebox: depends: libapache-authcookie-perl but it is not installable. E: Broken packages."

Totally stumped now. Adivce appreciated.

---

### Post by scottuss on 2008-11-20
I don't know if this helps or not, but I would recommend Webmin as opposed to ebox. I have used both and find Webmin to be miles better.

[http://www.webmin.com/download.html](http://www.webmin.com/download.html)

P.S There is a bug in Intrepid, I will look for the workaround that I found, if you decide you still want to use ebox

---

### Post by happyhacker on 2008-11-20
Thanks, scottuss. I am moving towards Webmin now. I suspect my installation may be in a bit of a mess because I have followed some threads to get ebox installed. Anyway I'm just downloading the desktop so will attempt webmin after that.

Is there a way of uninstalling Open Office as I won't be using it on the server and need the space?

---

### Post by andydurham on 2008-11-20
If you still want to try ebox.  

There is a new version out for 8.10.  Its not 100% stable I believe but may be worth a go.

deb [http://ppa.launchpad.net/ebox-unstable/ubuntu](http://ppa.launchpad.net/ebox-unstable/ubuntu) intrepid main

Apart from that I know nothing about it as I havent tried it yet.  Ive been recommended it as friends have said its better than webmin, which I was in the middle of setting up.

Cheers

Andy

---

### Post by scottuss on 2008-11-20
If you installed using the server CD you wont have open office installed by default. If you install the desktop meta package and therefore get Open Office as part of that you can just do sudo apt-get remove openoffice.org-common and that should get rid of it for you.

I wouldn't recommend installing the full GUI for a server though, I would definitely use the server install CD and get Webmin installed from there. To be honest, there isn't much Webmin cant do that the standard Gnome desktop can do (obviously it looks a lot different being run in a browser! :) )


Ah I just re-read your post, you say you're going to use the Desktop cd, if you do, follow my instructions above to remove open office, otherwise I would highly recommend the server install

---

### Post by happyhacker on 2008-11-21
Thanks for your reply. I have decided to reinstall the server version (or maybe it's easier to uninstall the desktop - is that easy?). I will go for the browser with Webmin - assumeing it works on 8.10, ebox does not seem to be available. I assume you are refering to accessing it from another PC with it's browser and typing in 192.168.0.2 (the IP I've used).

As said above I would prefer to uninstall the GUI as I've setup the eth0 and the router has recognised the PC. I have also set the IP on Ubuntu anyway. I have also removed the package recommended in the guide (other post). Maybe it's cleaner to start again. I've only got a 40Gb drive so space is a premium.

Advice appreciated.

---

### Post by scottuss on 2008-11-21
Yeah I would definitely start again to be honest. You can remove the desktop packages, but I would imagine they leave behind lots of "residue"

Go for a server install, that's what I have on my 40 gig server. If you have any issues getting it set up, post back :)

---

### Post by happyhacker on 2008-11-21
Will do, next week sometime but no doubt I'll be back thanks.

---

