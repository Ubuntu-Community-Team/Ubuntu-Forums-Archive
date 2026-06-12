---
title: "Metatrader 4 no toolbar icons and other problems"
date: 2011-02-08
forum: Wine
---

### Post by elempe on 2011-02-08
I'm running Lucid with vncserver windows manager (tried several - xfce4,fluxbox,gnome) and wine on it. I can run Metatrader normally and everything functions as supposed, but the problem is with toolbar icons and some configuration dialogs. It will be much easier to understand if you take a look at attached screenshot. As you can see there is even pressed buttons in toolbar but no icons shown. You can see opened dialog box too. There on very left hand are checkboxes at every line. Some of them are checked some not. As you can see in screenshot it is not possible to see checkbox at all.
There is a lot of messages:
fixme:xrender:XRender_AlphaBlend Unable to AlphaBlend without Xrender
in the terminal where I'm running wine

I have tried wine 1.3 and 1.2

Wine: dpkg -l | grep wine
ii  ttf-symbol-replacement-wine1.3       1.3.11-0ubuntu1~lucidppa1                       Free font with the same metrics as Symbol
rc  wine1.2                              1.2.2-1ubuntu1~lucid1                           Microsoft Windows Compatibility Layer (Binar
ii  wine1.3                              1.3.11-0ubuntu1~lucidppa1                       Microsoft Windows Compatibility Layer (Binar
ii  wine1.3-gecko                        1.1.0-0ubuntu1~lucidppa1                        Microsoft Windows Compatibility Layer (Web B
ii  winetricks                           0.0+20110105-0ubuntu1~ppa1                      Microsoft Windows Compatibility Layer (winet

With winetricks I hav installed vcrun6 and experimented with comctl32 native and builtin.
Tightvnc i start something like this:
vncserver :1 -geometry 800x600 -depth 16
have tried different depth (8,24)
What can be the problem? I have a feeling that I'm missing something probably there is problem in some configuration.
On my laptop - Lucid then upgraded to Maverick everything works well in both lucid and maverick.

---

### Post by dino99 on 2011-02-08
with winetricks:
 remove all dll overrides (check both: alldlls=builtin alldlls=default)

winetricks vcrun6sp6 

with synaptic, install: ttf-opensymbol

[http://superuser.com/questions/72191/wine-alphablend-problem](http://superuser.com/questions/72191/wine-alphablend-problem)

---

### Post by elempe on 2011-02-08
> **dino99 said:**
> with winetricks:
 remove all dll overrides (check both: alldlls=builtin alldlls=default)

winetricks vcrun6sp6 

with synaptic, install: ttf-opensymbol

[http://superuser.com/questions/72191/wine-alphablend-problem](http://superuser.com/questions/72191/wine-alphablend-problem)

Thanks, did everything as you say, unfortunately didn't help - MT looks exactly as before. 
Now I have some more messages in terminal output, a lot of:
err:ole:marshal_object couldn't get IPSFactory buffer for interface {00000122-0000-0000-c000-000000000046}
err:ole:StdMarshalImpl_MarshalInterface Failed to create ifstub, hres=0x80040155
err:ole:CoMarshalInterface Failed to marshal the interface {00000122-0000-0000-c000-000000000046}, 80040155

---

### Post by dino99 on 2011-02-08
these issues are related to vnc (see link of 1st post)

---

### Post by elempe on 2011-02-09
> **dino99 said:**
> these issues are related to vnc (see link of 1st post)

Yes indeed I have read this post and many more (google :D ), but haven't succeed in my problem. I have tried other vnc servers too, vnc4 and x11vnc with no luck. Realvnc needs old shared library, I managed to get it running, but was unstable, so not usable and didn't help either.
Unfortunately I'm not strong in X configuration and stuff.

now I have dirty workaround: ssh -X -l <user> <hostname> 
wine <path_to>/teminal.exe
It works fine, bat it has one big drawback, I relay on network connection and can't restart workstation.
As this is not wine issue probably it i not right place to look for solution.

Thanks for help anyway :)

---

