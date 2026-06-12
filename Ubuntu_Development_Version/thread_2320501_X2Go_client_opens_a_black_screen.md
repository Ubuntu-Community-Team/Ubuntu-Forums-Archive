---
title: "X2Go client opens a black screen"
date: 2016-04-14
forum: Ubuntu Development Version
---

### Post by izznogooood on 2016-04-14
Has anyone had any success  with X2Go and Unity in 16.04?

All i get is a black screen when i connect. The connection seems fine but the window stay black
I should add that the client is run from mac and the selected Desktop is Unity.

---

### Post by TheFu on 2016-04-15
Unity isn't supported under x2go. Use lxde, xfce or a plain, non-compositing WM like openbox. This is documented on the x2go project pages.

---

### Post by izznogooood on 2016-04-15
Now this is strange, as Unity is a choice when choosing desktop. But for the record, i also tried XFCE and have the same issue. Connection ok,Black screen.

---

### Post by howefield on 2016-04-15
> **izznogooood said:**
> ...as Unity is a choice when choosing desktop.

Probably worked well enough with the 2D version of Unity that came with Ubuntu 12.04 (supported for another year or so) hence it being an option but not with any Unity version since (3D).

> ..But for the record, i also tried XFCE and have the same issue. Connection ok,Black screen.

I hear a lot of good things about the MATE desktop working well enough with x2go but my preference is for a vanilla xfce4 environment.

Is there anything about your xfce that is "customised " ?

[http://wiki.x2go.org/doku.php/doc:de-compat](http://wiki.x2go.org/doku.php/doc:de-compat)

---

### Post by izznogooood on 2016-04-15
No, I'm afraid not. Its just a clean install "apt install xfce4" on top of Ubuntu.

I think this might be a mac related problem, i will try connecting from linux and see. But if this does not support Unity i think this is not for me, as i was under the impression this could work as a "citrix" solution allowing me to connect multiple desktops. And of course i want to be able to customize :/.

---

### Post by TheFu on 2016-04-15
I vaguely remember there are Mac issues with x2go.  Also check that the needed fonts are installed on the Mac.

I use openbox, no DE.  Have for a few years now. Can't imagine my daily life without x2go. Use it from 2ft away, across the hall, and across the world.  Win7 and Linux as the clients.  On Windows, I was lazy and just installed all the fonts.  On Linux, just the client, no extra fonts needed.

You can have multiple virtual desktops using almost any window manager from 1996 or later. Unity isn't needed.  There are also specific keyboard add-ons per DE. I've never touched those either. KISS makes it simple.

I have no clue about Mac.

---

### Post by izznogooood on 2016-04-16
Turns out its the same when i try and connect from a laptop with Ubuntu... (I use MATE as my desktop of choice when trying to connect...)

Is there any thing you configure on the server side or do you just install it and it works out of the box, sure looks like that in the wiki.

It connects then autodisconnect before i even get a chance to see the login :(

---

### Post by TheFu on 2016-04-16
Does ssh already work?  I setup ssh (no GUI) before touching x2go on every machine.  ssh is the swissarmknife for all my connections.

---

### Post by izznogooood on 2016-04-16
> **TheFu said:**
> Does ssh already work?


Yes, that's always my nr1 job...

---

### Post by TheFu on 2016-04-16
sudo apt-get install x2goserver x2goserver-xsession openbox

xsession is required.

---

### Post by izznogooood on 2016-04-16
got it :/... Maybe its my kernel 4.6-rc-2... I cant boot the Ubuntu std kernel because the Nvidia modules does not load properly  but thats a whole other problem. I will fix that so i can boot the "propper" kernel and come back to this thread. 

Oh, if time was unlimited ;)

---

