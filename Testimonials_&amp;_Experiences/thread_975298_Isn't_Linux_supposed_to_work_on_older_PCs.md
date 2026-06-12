---
title: "Isn't Linux supposed to work on older PCs?"
date: 2008-11-08
forum: Testimonials &amp; Experiences
---

### Post by webheadjunky on 2008-11-08
Hi

I've been happily using Linux for 15 months now and have been completely Windoze free. I do have a technical question but before I get there, I want to know why a decision was taken to remove support for older restricted nvidia drivers in Ibex?

How is that supposed to help the user community?

I now find I can't run compiz, cairo dock, google earth, screensavers and a whole lot of other stuff that requires 3d acceleration

In fact, my current desktop has no more graphical enhancements than the Windows 3.1 desktop I used 15 years ago!

I have downloaded envy ng and installed the correct nvidia driver 96.43.08 and have tried to edit the xorg.conf file 

Still no joy

Hope someone can help me fix this otherwise I will reluctantly have to try another distro 

Thanks for reading

Raaj

---

### Post by Funnnny on 2008-11-08
What VGA you are using ?.
If you can't get it work, just use 8.04, it's fine and Long term support

---

### Post by bodhi.zazen on 2008-11-08
Well there are several issues here.

First, this is as much as issue with X and the Nvidia drivers as anything else. You should direct your nvidia complaints at nvidia. The nvidia drivers are maintained by nvidia (they are propriarty) not the Ubuntu developers. If ATI / Nvidia open sourced thier drivers then it would be different.

Second I have to disagree, running compiz and 3d effects is not the same as running Linux.

Third you need to match your OS with your box. I am sure you could not run Vista on that old box either. Indeed you may be better off with a different OS on that box. I personally like Slackware for older boxes.

Foruth, if an older version of Ubuntu is working, there is no need to upgrade.

---

### Post by Alexia_Death on 2008-11-08
I presume you are talking about the chips nvidia no longer supports in newest glx drivers? it is true, nvidia-glx-legacy package is no longer available and nvidia-glx does not support them, but it suggests a list of packages that replace it when you try to install it. And by a quick look, what you need is nvidia-glx-71. 

See here for supported cards:
[http://packages.ubuntu.com/intrepid/nvidia-glx-71](http://packages.ubuntu.com/intrepid/nvidia-glx-71)

It lists RIVA cards that are AFAIK dropped in new versions, so all other dropped then should be available.

PS: You may also make a note that you are not limited to what the repro provides. If it weren't available from the repro(and I do think it is), then you could just go and get it from nvidia. installation would be a bit bigger of a pain tho. Had to resort to that once or twice when running Intrepid in its broken stage, long before first alpha.

---

### Post by webheadjunky on 2008-11-08
Thanks for the quick responses!

I have a P4 2.4Ghz with 2Gb RAM and a 128mb graphics card and have used both ubuntu and kubuntu

I still don't understand why a version upgrade should cut out users

I happen to like compiz and google earth but the point is I have no 3d acceleration following an upgrade to Ibex

Thanks again

Raaj

---

### Post by webheadjunky on 2008-11-08
Hi 
According to the latest version of the Envy NG, the recommended driver to use was the 93 version. Should I ignore that and try the 71 version?
Thanks
Raaj

---

### Post by philinux on 2008-11-08
Try each one see which works best.

---

### Post by Alexia_Death on 2008-11-08
> **webheadjunky said:**
> Hi 
According to the latest version of the Envy NG, the recommended driver to use was the 93 version. Should I ignore that and try the 71 version?
Thanks
Raaj

Well, 71 should at least work. I dont know what card you have, but next one the repro has is nvidia-glx-96... You can try both.

---

### Post by igknighted on 2008-11-08
71 doesn't have composite, so Compiz will be a no go.  And I don't know if you need it for other things like google earth.

---

### Post by webheadjunky on 2008-11-09
Thanks everybody for your advice. 

Having struggled with this issue for over a week, I'm giving up now and moving to OpenSuse 11. I might return to ubunutu/kubuntu if the Jaunty Jackalope works better with my hardware

Whilst I appreciate nvidia's proprietary drivers are nvidia's responsibility, from a user perspective it seems I now either have to choose between new functionality (e.g improved wireless networking in Ibex compared to the dodgy experience I had with Kubuntu Heron) or sticking with an older version i.e Heron, because that let's me get basic 3d acceleration 

But there appears to be no easy option for me to have both the basic 3d support and enjoy the new improvements in the latest release as well

I used XP Pro on this machine for years so I don't think there is anything wrong with my hardware, nor do I intend to spend money on it npw. I just need to find a distro that will work for me

Thanks again

Raaj

---

### Post by hysteresis on 2008-11-10
I just upgraded to intrepid this morning. My Geforce4 MX4000 was able to work after upgrading my drivers in System-Administration-Hardware Drivers to version 96.43.09-0ubuntu1. On previous attempts to upgrade to intrepid this did not work. Does this mean the Nvidia legacy driver issue has been solved in 8.10?

---

