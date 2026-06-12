---
title: "[SOLVED] Wine fonts garbled"
date: 2008-12-13
forum: Wine
---

### Post by [censored] on 2008-12-13
Please Help! Since upgrading to Intrepid, wine fonts have become unreadable. (See attached screenshot)

The problem goes away if I raise wine's dpi above 140, but unfortunately, if I do that, wine windows become too big to fit on my screen.

I am using wine-1.1.10,  1.1.10~winehq0~ubuntu~8.10-0ubuntu. 

I have an 1152x864@75Hz resolution. 

Video card is a GeForce4 MX 4000, with the standard pty drivers nvidia-glx-96, 96.43.09-0ubuntu1.  

I have tried installing all fonts and ms core fonts using the winetricks script.

I have msttcorefonts installed via apt-get.

---

### Post by union two levers on 2008-12-14
hi, try uninstalling the nvidia hardware driver version 96 that you probably installed shortly after installing 8.10 then restart the computer.it worked for me.

---

### Post by [censored] on 2008-12-14
union two levers, 

thanks. But if I uninstall nvidia, I won't have 3d graphics. Isn't that so?

---

### Post by Bakon Jarser on 2008-12-15
I'm having the same problem.  Tried clean installs, msttcorefonts, disabling compiz effects, and all that good stuff.  Deactivating the NVidia restricted driver fixes this but it is a horrible solution.  I have to have wine.  Does anybody know how to fix this?

---

### Post by Bakon Jarser on 2008-12-15
Here's a link to the launchpad bug report.

[https://bugs.edge.launchpad.net/ubuntu/+source/wine/+bug/300476](https://bugs.edge.launchpad.net/ubuntu/+source/wine/+bug/300476)

Here is the fix.

Go to the .wine directory in your home folder (make sure you have view hidden files enabled).  Creat a new document called 'settings.txt'.  Paste the following line into this file:

[HKEY_CURRENT_USER\Software\Wine\X11 Driver]
"ClientSideWithRender"="N"

Open a terminal and do the following

```
cd ~/.wine
regedit settings.txt
```

That's it!

---

### Post by [censored] on 2008-12-15
Thank you ever so much Bakon Jarser! Will look on launchpad for solutions in future.

---

### Post by striants on 2009-01-10
Hello from me too. I had the exact same font problem and I followed the proposed solution. 
The problem now is that the toolbar icons in Thunderbird portable are not visible (see attached screenshot)

any ideas on how to solve this?

Thanks in advance!

---

### Post by Eric Qel-Droma on 2009-01-10
Thank you so much for this, Bakon Jarser.  Very helpful!

---

### Post by Chris Weaver on 2009-02-16
Worked for me too. Using the Nvidia driver. Thanks for that.

---

### Post by davygravy on 2009-03-16
Yes!  woooohooo! Fixed.

:D

---

### Post by masque7 on 2009-04-03
Thank you, worked for me with no issues at all. :)

---

### Post by gatorbrit on 2009-04-23
> **Bakon Jarser said:**
> Here's a link to the launchpad bug report.

[https://bugs.edge.launchpad.net/ubuntu/+source/wine/+bug/300476](https://bugs.edge.launchpad.net/ubuntu/+source/wine/+bug/300476)

Here is the fix.

Go to the .wine directory in your home folder (make sure you have view hidden files enabled).  Creat a new document called 'settings.txt'.  Paste the following line into this file:

[HKEY_CURRENT_USER\Software\Wine\X11 Driver]
"ClientSideWithRender"="N"

Open a terminal and do the following

```
cd ~/.wine
regedit settings.txt
```

That's it!


I did this and it helped the fonts in winecfg - they now render perfectly.  But when I run word 2007 the fonts in the document are still garbled.   Particularly times new roman.


Thanks

---

### Post by freackout on 2009-08-27
> **'[censored] said:**
> Please Help! Since upgrading to Intrepid, wine fonts have become unreadable. (See attached screenshot)

The problem goes away if I raise wine's dpi above 140, but unfortunately, if I do that, wine windows become too big to fit on my screen.

I am using wine-1.1.10,  1.1.10~winehq0~ubuntu~8.10-0ubuntu. 

I have an 1152x864@75Hz resolution. 

Video card is a GeForce4 MX 4000, with the standard pty drivers nvidia-glx-96, 96.43.09-0ubuntu1.  

I have tried installing all fonts and ms core fonts using the winetricks script.

I have msttcorefonts installed via apt-get.

hi many probs with fomts ect ok this one shows up 4 you, try downloading the source and compiling you get missing files ie dependancies ok so put those in try ./compile again till there gone only a couple then notice xfree86.dev  is not installed also others ie ttf-xfree86-nonfree ect... try looking at the messages it helps alot,ok.

---

### Post by freackout on 2009-08-27
> **freackout said:**
> hi many probs with fomts ect ok this one shows up 4 you, try downloading the source and compiling you get missing files ie dependancies ok so put those in try ./compile again till there gone only a couple then notice xfree86.dev  is not installed also others ie ttf-xfree86-nonfree ect... try looking at the messages it helps alot,ok.

and then there is freetype also ie ./configure againe spot the doing it bit :-) all dlls going nicely now ok doods np. make then sudo make install then go and get ie4 ubuntu intrepid and ie6 works for you.

---

### Post by freackout on 2009-08-27
> **freackout said:**
> and then there is freetype also ie ./configure againe spot the doing it bit :-) all dlls going nicely now ok doods np. make then sudo make install then go and get ie4 ubuntu intrepid and ie6 works for you.

note warnings are simply that,warning you only.
errors are the ones to watch for.

---

### Post by freackout on 2009-08-28
> **freackout said:**
> note warnings are simply that,warning you only.
errors are the ones to watch for.

./tools/wineinstall

thats the one which will also compile make and install.

---

