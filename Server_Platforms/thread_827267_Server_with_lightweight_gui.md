---
title: "Server with lightweight gui"
date: 2008-06-12
forum: Server Platforms
---

### Post by snorkytheweasel on 2008-06-12
Whatdo I need to install to get a LAMP/DNS server with a lightweight gui?

---

### Post by molotov00 on 2008-06-12
Download and install the server version then install a lightweight gui... You could either install gnome-core or xubuntu, which doesnt come with many apps at all. (far fewer than ubuntu or kubuntu)

I'd go xfce, but read up on lightweight guis, there are many.

Oh, and as far as LAMP, DNS, they are options when you install the server version, which doesnt come with a gui by default. Installing a gui after-the-fact is as easy as: sudo apt-get install <package>. It is automatically configured and boots into the GUI next time you boot.

---

### Post by Nythain on 2008-06-12
other options include
the *box window managers blackbox, openbox, fluxbox (all are in the repos)
tiling window managers wmii, xmonad, awesome (best if built from source for current version reasons
a few really lightweight wm's icewm and peckwm

and as already mentioned teh "core" of the two popular desktop environments gnome-core and i forget what the very base kde package is, i think its like kde-base???

---

### Post by crtlbreak on 2008-06-17
Dear molotov00
I tried the
#sudo apt-get install gnome-core - all transpired fine but trying to #startX it delivers errors 
"cannot stat /etc/X11/X (no such file or directory)"
I had to additionally run a 
#sudo apt-get install xorg
and ter completion a
#startx
delivered a desktop
regards
crtlbreak

---

### Post by FakeOutdoorsman on 2008-06-17
An alternative to using a GUI is to run [Webmin]("https://help.ubuntu.com/community/WebMin") or [eBox]("https://help.ubuntu.com/community/eBox"), which will allow you to configure your server through your browser.

---

### Post by gtdaqua on 2008-06-18
> **FakeOutdoorsman said:**
> An alternative to using a GUI is to run [Webmin]("https://help.ubuntu.com/community/WebMin") or [eBox]("https://help.ubuntu.com/community/eBox"), which will allow you to configure your server through your browser.

I agree. Even with a GUI, I dont think you would be able to administer a server with it. You still need to rely on CLI for administration. If you want only a light-weight desktop consider this: 

```

sudo apt-get install kdebase kdm x-window-system-core

```

Installs only minimal components required for KDE. Or Learn CLI. You will find this increasingly useful than GUI.

---

### Post by windependence on 2008-06-18
I agree with gtdaqua. I used to use WindowMaker when I first started, but now I do not load a GUI at all. Once you start, you will never want to go back.

Also some poeple don't realize the server kernel is much different from the desktop kernel and is optimized to run server functions. 

-Tim

---

### Post by crtlbreak on 2008-06-18
> **FakeOutdoorsman said:**
> An alternative to using a GUI is to run [Webmin]("https://help.ubuntu.com/community/WebMin") or [eBox]("https://help.ubuntu.com/community/eBox"), which will allow you to configure your server through your browser.

Hi fakeoutdoorsman
not sure I understand - a browser needs x to run, correct? :confused:
regards

---

### Post by windependence on 2008-06-18
> **crtlbreak said:**
> Hi fakeoutdoorsman
not sure I understand - a browser needs x to run, correct? :confused:
regards

You do it from another machine. For example for WebMin:

[https://yourserverIP:10000](https://yourserverIP:10000)

-Tim

---

### Post by crtlbreak on 2008-06-18
Thank you Tim
That was what I thought
I cannot even connect locally from a browser to my own IP on port 10000 - So i need to look at my fw settings or acl's in order t allow traffic.
Once I can connect locally I will attempt to connect remotely to ubuntuserver.
Is it defaulted to port 10000? i know that everything is configurable and it will be on whatever port one changes it to - but by default?
regards

---

### Post by crtlbreak on 2008-06-18
hmm - as I clicked send I realised I dnt have WebMin installed on the server - that might make a little difference? :lolflag:
cheers

---

### Post by windependence on 2008-06-18
Looks like we have a troll. I'm not feeding it.

-Tim

---

### Post by FAO56 on 2008-06-18
> **windependence said:**
> Looks like we have a troll. I'm not feeding it.

-Tim

Do you see what I am talkimg about?

---

### Post by crtlbreak on 2008-06-18
seems the troll has been kicked off his bridge?
three cheers for the big billy goat gruff.

---

