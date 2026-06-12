---
title: "Ati problem"
date: 2011-07-22
forum: Ubuntu Studio
---

### Post by overspeed on 2011-07-22
Hi,

I have a "hp g62-a40ep" and just installed Ubuntu Studio. I propperly installed compiz but nothing take any effect. 
Might it be a problem with the graphics card? How can i update the ati Graphics card?

direct rendering is on.


Thank you in advance

---

### Post by overspeed on 2011-07-22
if i try to open catalyst control center i get this error:

"  p, li { white-space: pre-wrap; }  There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.
 
 No ATI graphics driver is installed, or the ATI driver is not functioning properly.
 Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig.
"

---

### Post by marseille on 2011-07-23
``First, check your graphic card name and chipset'' at the command line:

```
$lspci -nn | grep VGA
```

check out these pages too:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)

and maybe search the documentation:
[https://help.ubuntu.com/search.html?cof=FORID%3A9&cx=003883529982892832976%3Ae2vwumte3fq&ie=UTF-8&q=ATI&sa=Search](https://help.ubuntu.com/search.html?cof=FORID%3A9&cx=003883529982892832976%3Ae2vwumte3fq&ie=UTF-8&q=ATI&sa=Search)

---

### Post by 2F4U on 2011-07-23
Does Ubuntu offer you different drivers through the Additional Drivers application?

---

### Post by overspeed on 2011-07-23
> **marseille said:**
> ``First, check your graphic card name and chipset'' at the command line:

```
$lspci -nn | grep VGA
```check out these pages too:[]("https://help.ubuntu.com/search.html?cof=FORID%3A9&cx=003883529982892832976%3Ae2vwumte3fq&ie=UTF-8&q=ATI&sa=Search")

Hi Merseille,

Thank you for the reply. The result is:

00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series] [1002:68e0]

---

### Post by overspeed on 2011-07-23
> **2F4U said:**
> Does Ubuntu offer you different drivers through the Additional Drivers application?

Thank you 2F4u,

I have them installed properly with the message:

"3D-accelerated proprietary graphics driver for ATI cards.

This driver is required to fully utilise the 3D potential of some ATI graphics cards, as well as provide 2D acceleration of newer cards. "


the problem is that i cant run compiz effects and wine apps. I think the card isnt properly installed.

---

### Post by marseille on 2011-07-23
I saw this on WineHQ:

[INDENT]

**6.10.4. I'm using Desktop Effects with Compiz, Fusion, or XGL and get poor performance/odd messages/broken applications**

Using compositing managers in X11 tends to cripple OpenGL performance or break OpenGL entirely (this does not apply to the Mac OS X compositor, which cannot be disabled). We recommend that you disable them entirely before trying to use Wine. If you are using one and experiencing slow performance then please do not file bugs in Wine, as these are bugs in your window manager or your video drivers. Also, disabling the Composite extension within /etc/X11/xorg.conf will most certainly prevent any compositing from affecting Wine.[/INDENT]

[http://wiki.winehq.org/FAQ#head-db2fa150a8b8f906508959b92beb00768ec6ec47](http://wiki.winehq.org/FAQ#head-db2fa150a8b8f906508959b92beb00768ec6ec47)

---

### Post by overspeed on 2011-07-23
> **marseille said:**
> I saw this on WineHQ:
[INDENT]

**6.10.4. I'm using Desktop Effects with Compiz, Fusion, or XGL and get poor performance/odd messages/broken applications**

Using compositing managers in X11 tends to cripple OpenGL performance or break OpenGL entirely (this does not apply to the Mac OS X compositor, which cannot be disabled). We recommend that you disable them entirely before trying to use Wine. If you are using one and experiencing slow performance then please do not file bugs in Wine, as these are bugs in your window manager or your video drivers. Also, disabling the Composite extension within /etc/X11/xorg.conf will most certainly prevent any compositing from affecting Wine.[/INDENT][http://wiki.winehq.org/FAQ#head-db2fa150a8b8f906508959b92beb00768ec6ec47](http://wiki.winehq.org/FAQ#head-db2fa150a8b8f906508959b92beb00768ec6ec47)

I removed compiz and still have the same problem. If i try to run catalyst control center i get 

"  p, li { white-space: pre-wrap; }  There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.
 
 No ATI graphics driver is installed, or the ATI driver is not functioning properly.
 Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig."

---

### Post by marseille on 2011-07-23
Overspeed, I'm not a guru but I don't know if that's a good idea. Last I remember, you can just turn compiz off... another thread says to just ``Go to'':

```
System -> Preferences -> Desktop Effects > select "None"
```

The author went on to write:

> Compiz is actually an important part of your system, simply removing it is not the right thing to do. You have to replace it with something lighter. The something lighter is called Metacity. You can hit Alt + F2 and type

Code:
```
 metacity --replace
```


> This is equivalent to desktop effects being set to none, except it will be temporary until you reboot (or type compiz --replace).


source url [http://ubuntuforums.org/showpost.php?p=10031590&postcount=2](http://ubuntuforums.org/showpost.php?p=10031590&postcount=2)

The **Ubuntu Documentation Wiki on `Composite Manager CompizFusion'** elaborates:

> If you want to stop Compiz and start the old window manager (metacity or kwin), just press Alt+F2 and put in the following for Ubuntu

```
metacity --replace
```

# Alternate syntax if you receive: 'Window Manager error: Unable to Open X display'
# when using the above command.  The correct --display= value can be determined by 
# issuing the 'who' command and noting the values in parenthesis at line-end.

```
metacity --display=:0.0 --replace
```


[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)



But like I said, I'm not a guru... just up late to  figure out some technical issues. So if you're gonna keep at it right now, **check out documentation**. Take a look at these search results and see if you can't find something:

[https://help.ubuntu.com/search.html?cof=FORID%3A9&cx=003883529982892832976%3Ae2vwumte3fq&ie=UTF-8&q=compiz&sa=Search](https://help.ubuntu.com/search.html?cof=FORID%3A9&cx=003883529982892832976%3Ae2vwumte3fq&ie=UTF-8&q=compiz&sa=Search)[/QUOTE]

Sometimes ATI is worth a visit too (over at AMD now, isn't it) and Intel (if that's other one) to look up your cards and see what they say about linux support... and maybe how they work in tandem (if that info is even out there), as well.

---

### Post by overspeed on 2011-07-23
Thank you all for the help

I continue to have the problem.
I reinstalled the driver but, in compiz settings, i select rotate cube or wobbly windows effect and nothing happen. Compiz doesnt change anything.

Any ideas?

Thank you

---

### Post by overspeed on 2011-07-23
Hi,

I fixed it. I followed these steps [http://askubuntu.com/questions/46976/ati-catalyst-control-center-gives-error-natty-64bit-radeon-hd-6470m](http://askubuntu.com/questions/46976/ati-catalyst-control-center-gives-error-natty-64bit-radeon-hd-6470m) and then i installed Compiz Fusion Icon and selected "reload window manager".

Thanks all for the effort.

---

### Post by marseille on 2011-07-23
Sweet! I'm glad it's working out for you :KS

---

