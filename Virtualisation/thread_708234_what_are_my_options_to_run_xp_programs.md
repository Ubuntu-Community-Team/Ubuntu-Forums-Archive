---
title: "what are my options to run xp programs?"
date: 2008-02-26
forum: Virtualisation
---

### Post by noremacyug on 2008-02-26
ok, i'm a new ubuntu convert and, as many people, still need to run a couple apps that are windows based.  now i know i could dual boot, but i really don't want to fool with that.  i've tried wine, but was not impressed.  i assume wine is not in the same class as a virualization app, perhaps i'm wrong.  and that's why i'm posting this.  to find out the difference and learn whether or not it is what i need.

what, if any, is the difference between wine/cedega and vmware/virtualbox.?

i'm looking to run maybe a couple games (steam/counterstrike and warcraft III) as well as run the software for my harmony remote. and then perhaps a program or two more along the way if i see fit.

as always, thanks!

---

### Post by Dojan5 on 2008-02-26
> **noremacyug said:**
> ok, i'm a new ubuntu convert and, as many people, still need to run a couple apps that are windows based.  now i know i could dual boot, but i really don't want to fool with that.  i've tried wine, but was not impressed.  i assume wine is not in the same class as a virualization app, perhaps i'm wrong.  and that's why i'm posting this.  to find out the difference and learn whether or not it is what i need.

what, if any, is the difference between wine/cedega and vmware/virtualbox.?

i'm looking to run maybe a couple games (steam/counterstrike and warcraft III) as well as run the software for my harmony remote. and then perhaps a program or two more along the way if i see fit.

as always, thanks!

To run CS (And steam) i would probably try CrossOver Linux PRO, since last time i used it it had a option to install Steam

---

### Post by noremacyug on 2008-02-26
i'll look into that.  much appreciated

---

### Post by akudewan on 2008-02-26
> **noremacyug said:**
> 
what, if any, is the difference between wine/cedega and vmware/virtualbox.?


From what I understand, Wine is an alternate implementation of the Windows API, that is, they've actually made linux-counterparts of windows libraries.

In case of virtual machines like VMWare and Virtualbox, you actually "boot" windows from Linux. So you would need your own copy of windows and possibly install it using the virtual machine. (But I think VMWare can also boot your existing windows installation).

(Please correct me if I'm wrong)

---

### Post by noremacyug on 2008-02-26
i have winxp so that would be no problem.  i was just wondering how well it worked compared to wine.  is it so much like running windows that any windows based program would run in it or is it hit and miss like wine is?

also, i have steam up and running via crossover linux pro.  next is to see if counterstrike will run.

---

### Post by Steve1961 on 2008-02-26
> **noremacyug said:**
> i have winxp so that would be no problem.  i was just wondering how well it worked compared to wine.  is it so much like running windows that any windows based program would run in it or is it hit and miss like wine is?

also, i have steam up and running via crossover linux pro.  next is to see if counterstrike will run.

If you run xp in virtualbox it runs seamlessly - a full version of xp in a window (or full screen if you want).  I use it to run dreamweaver and photoshop, but as it uses a virtual graphics card I'm not sure that it would be up to running graphics intensive games.  You might be better off sticking with wine for them, or even Cedega (a piece of proprietary software based on wine that is designed to run windows games)

---

### Post by noremacyug on 2008-02-26
i may give virtualbox a try as well then.  i tried cedega and couldn't get it to cooperate.  perhaps crossover will suffice for the couple of games i would play on computer (i mostly game on 360) and then virtualbox for stuff like movie editing and the sorts.  thanks.

---

### Post by roaldz on 2008-02-26
You can´t run 3D games in a virtual machine like VMware or Virtualbox. If I were you, I´d go to [http://appdb.winehq.org/](http://appdb.winehq.org/) and look if your program is supported. If it is, it´s worth the effort of trying.
[Counterstrike]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731") is supported (rated Gold)
[Warcraft 3]("http://appdb.winehq.org/appview.php?iVersionId=1177") is supported too (rated Platinum)
So I think Wine is for you!

Roald

---

### Post by HermanAB on 2008-02-26
Movie editing on Windows?  Considering that Pixar makes movies on Linux...

You can probably do what you need with Blender and Avidemux.

---

### Post by noremacyug on 2008-02-27
> **HermanAB said:**
> Movie editing on Windows?  Considering that Pixar makes movies on Linux...

You can probably do what you need with Blender and Avidemux.

yeah, i used pinnacle studio 11 and now i'm thinking bout trying cyberlink powerdirector.  i'll deffinately check out blender and avidemux.  i'd much rather run a linux prog over windows.

---

