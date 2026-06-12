---
title: "WebKit-GTK Compiled for Ubuntu"
date: 2007-09-07
forum: The Cafe
---

### Post by Kimm on 2007-09-07
I have compiled an SVN version of the WebKit GTK Port. I would like to share it with everyone, but I dont know where to host it.

I have packaged it (along with the WebKit-GTK Test Browser) in a checkinstall package which seems to work nicely :)

Untill I find a host, feel free to add me on Jabber: [email]mrkimm@jabber.org[/email] and I will send it to you :) (2.8 Mb).

Note: I built this with hopes to build epiphany with the WebKit engine, but it seems that epiphany needs a version of GLib and GTK not found in the repositories (an unstable version at that), so my dreams of that didnt come true. The Test browser is very simple, fun to try though.

I've attached a screenshot of the testbrowser. To run it, type: webkit-gtk-test in your terminal.

---

### Post by Anthem on 2007-09-07
I think you're looking for this:

[http://live.gnome.org/Epiphany/WebKit](http://live.gnome.org/Epiphany/WebKit)

---

### Post by Anthem on 2007-09-07
Or this:

[http://blogs.gnome.org/epiphany/2007/07/30/epiphany-2196-released-webkit-back-end/](http://blogs.gnome.org/epiphany/2007/07/30/epiphany-2196-released-webkit-back-end/)

---

### Post by Kimm on 2007-09-07
> **Anthem said:**
> I think you're looking for this:

[http://live.gnome.org/Epiphany/WebKit](http://live.gnome.org/Epiphany/WebKit)

...
I'm not looking for anything, I have WebKit compiled allredy, was woundering if anyone else was interested...

---

### Post by Altarbo on 2007-09-07
That's pretty cool.  How stable is it?  A lot of fun bugs to report or just business now?

---

### Post by ButteBlues on 2007-09-09
I added you so I can nab a copy of it.

---

### Post by a12ctic on 2007-09-09
I'm interested in this. 

why not host it on rapidshare or mediafire?

---

### Post by Kimm on 2007-09-10
Rapidshare.de didnt seem to want to work. I uploaded it to Mediafire though (didnt know about that site).

Here's a link: [http://www.mediafire.com/?31z1dm2msoi](http://www.mediafire.com/?31z1dm2msoi)

Its fairly stable (I only notice problems with Flash (causes crash)). But I haven't used it much.

Enjoy :)

---

### Post by bruce89 on 2007-09-10
[http://packages.ubuntu.com/gutsy/source/webkit](http://packages.ubuntu.com/gutsy/source/webkit)

If you have Gutsy, you can install the test browser with

```
sudo aptitude install libwebkitgdk0d
```

and run it with

```
./usr/lib/WebKit/GdkLauncher
```

If you have Feisty or below, Pbuilder is your friend.

---

### Post by davim on 2007-09-10
you can host it at [http://www.getdeb.net/](http://www.getdeb.net/)

---

