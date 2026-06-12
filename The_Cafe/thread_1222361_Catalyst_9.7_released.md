---
title: "Catalyst 9.7 released"
date: 2009-07-24
forum: The Cafe
---

### Post by markbuntu on 2009-07-24
Catalyst 9.7 is now available.

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

 looks like just some bug fixes and added support for red flag. Has anyone tried it yet?

---

### Post by markbuntu on 2009-07-25
Ok, I installed it. I do not notice any serious borkages and I was fianlly able to, with much fiddling around, get my three monitors working the way I wanted just with CCC. At least they are in the correct order now.

I have a 20 inch and 24 inch widescreens on a HD3650 and a 19 inch on a 3450. What I wanted was a big desktop on the 3650 monitors and a separate session on the hd3450. I can get the big desktop set up with compiz when the 3450 monitor is disabled. But once I enabled the third monitor and xinerama then I had to set up separate sessions for each screen. That works, I now have a 16800x1050 and 1920x1200 and 1280x1024 native resolutions and can drag windows around between them. 

But no compiz  Visual Effects claims there is no composite avalable though Xorg.0.log says that composite is loaded. I also keep getting little popups about no randr when some applications open.

I am pretty sure this all has to do with randr and xinerama.

---

### Post by lavinog on 2009-07-25
> But no compiz Visual Effects claims there is no composite avalable though Xorg.0.log says that composite is loaded.

I noticed that moving the window with desktop effects enabled produces the old behaivor (pre 9.3 issue) of lagging the window.  Looks like something broke.
On the otherhand, I have read that others are seeing significant fps improvements in some games, and wine. (As noted on the 9.5 thread, I got almost double the fps on glxgears)

---

### Post by markbuntu on 2009-07-25
Before I enabled xinerama I had compiz working and it was fine. 

I think it has something to do wth randr being disabled so xinerama can work. 

I usually set everything to max override in the 3D section of CCC. That seems to speed things up and make them look nicer. There is also a setting in compiz configuration manager for fglrx, maybe you should try that and see if it helps.

---

### Post by Zikona on 2009-07-26
markbuntu:

Can you share your xorg.conf? I am running similar set-up with 3 monitors and 2xHD4670. I just simply can not get the 3 monitor to get same resolution as the other 2 monitors.

Note: My current xorg.conf is attached.

---

### Post by martinbaselier on 2009-07-26
@zikona with the ati driver the xorg.conf is overridden by the ati config file.

---

### Post by Zikona on 2009-07-26
Okey martinbaselier, where is the ati config file location so I can share it with you guys?

---

### Post by AKADAP on 2009-07-26
> **please said:**
> Okay, 9.7th iterations of this SHITTTY driver!

That's so unbelievable! Never, i said well** NEVER **the FireGL driver worked at the first time in **9 YEARS**!  
And i am not even talking about the code itself - shitty also - but the install software! It hangs or it crashes while messing with the terminal!
And when it works, it runs 10 minutes before lagging as a crap to the death!

That's incredible, i tried to give a chance at each new release hoping for something at least allowing me to use my ATI HD4850 but, i get always that pain in my a**!

My ATI M10 T2 and X600 worked great with the opensource driver.

That's why i'm really disappointed, i know how hard the opensource devs are working to make radeonHD shinning from all its bits while those bastards of AMD/ATI are selling lots of cards relying on the good ads and the hard work that the community is making about their products!
It makes me thinking about socialists! We think these guys are with us but they are mainly misusing us! :)

I dislike Nvidia but at least their product works and really well but i don't want to support this fact!

So, as a good willing Linux user, i still getting f****d.

Pleaser, you here having tested this driver, stop promoting this driver it doesn't work!
I'm using Jaunty in a standard manner, let's say without any customization or whatever and this **** (FGL) simply doesn't work!

Gee, I followed the instructions: uninstalled the old driver first, rebooted, installed the new driver, rebooted. Worked fine.

Doesn't seem to have changed anything from 9.6 though. I discovered just before I upgraded that using opengl for MythTV greatly improved the picture quality. Vertical sync actually occurs between frames instead of right in the middle of them, and channel changing does not confuse the decoder anymore.

Interlaced video is still a problem however, any motion and I get horrible feathering (Correction, seems I missed the fact that deinterlacing was turned off on the next page. look like I have a bunch of options to try out). Some HD channels work fine, some skip frames. It is a work in progress, and not nearly done.

---

### Post by AKADAP on 2009-07-27
> **AKADAP said:**
> 
Interlaced video is still a problem however, any motion and I get horrible feathering (Correction, seems I missed the fact that deinterlacing was turned off on the next page. look like I have a bunch of options to try out). 

A few experiments, and my picture quality is much improved. Still not perfect, get little bits of feathering here and there, but definitely better than before.
I'm using greedy-highmotion. yadif seemed to distort scrolling text, others seemed to cause the picture to go soft if anything moved in the picture.

---

### Post by MaxIBoy on 2009-07-27
Catalyst control center works for me now! And I was able to setup a "big desktop mode" without using xinerama! Which means I can re-enable Compiz! Which means I'm really exited! Which means I feel like ending everything I type with exclamation points!

---

### Post by lavinog on 2009-07-27
> **MaxIBoy said:**
>  Which means I'm really exited! Which means I feel like ending everything I type with exclamation points!
At least it wasn't in all caps! ;)

---

### Post by Zikona on 2009-07-27
My experience with new catalyst driver was also a positive one. I was finally able to enable my 3rd monitor and change the resolution on it. Although video quality and dragging windows across all 3 monitors was not too successful. I'll keep on working on it and perhaps try big desktop mode without enabling xinerama.

---

### Post by MaxIBoy on 2009-07-28
> **lavinog said:**
> At least it wasn't in all caps! ;)
I only do that when I'm angry.

---

### Post by r2-d2 on 2009-07-28
Still does not work with hd3650 cards. :-(

---

### Post by praveesh on 2009-07-28
Iam sorry , I don't know what catalyst is. Can you please tell me what it is?

---

### Post by days_of_ruin on 2009-07-28
> **praveesh said:**
> Iam sorry , I don't know what catalyst is. Can you please tell me what it is?

The proprietary driver for AMD/ATI graphics cards.

---

### Post by CJ Master on 2009-07-28
> **days_of_ruin said:**
> The proprietary driver for AMD/ATI graphics cards.

Nah... correct me if I'm wrong, but fglrx (or something like that) is the propriety driver, and Catalyst is the program that configures it.

---

### Post by MaxIBoy on 2009-07-28
The program which configures it is "Catalyst Control Center." The actual driver is called "FGLRX," which is in version 8.630 or something. The package of both together is simply called "Catalyst," which is in version 9.7.

Or something like that.

---

### Post by brendanpiater on 2009-07-28
Hi All,

I've been less then impressed with 9.5/6/7. Major bugs like the backfill issues and graphic corruptions plaguing my day... Major regressions from 9.4 used in Intrepid. 

This of course has to do with the new x server versions and features but surely... 3 versions later... common ATI/AMD

Performance wise, pretty good. Video and WoW on wine works fine.

The only real show stopper (and the thing that makes my blood boil) is the graphics corruption. At least once a day I'll have to attempt to save all my work and restart without loosing anything with a garbled screen... no fun over 6 "screens"... So much for reliability I keep going on about to my mates...

Any thoughts on how to cure this?

Running 9.04 amd64, ATI X3670 with on an external monitor.

Cheers
B

---

### Post by Dawei87 on 2009-07-28
any word on how this works with radeon hd3200 cards?

---

### Post by MaxIBoy on 2009-07-28
> **Dawei87 said:**
> any word on how this works with radeon hd3200 cards?Older versions worked okay when I had to use my HD3200 "hybrid graphics" integrated chip.

---

### Post by lavinog on 2009-07-28
> **r2-d2 said:**
> Still does not work with hd3650 cards. :-(

Can you be specific as to what isn't working.

It works on my hd3650 and my hd3200.

I get the graphics corruption issue that brendanpiater mentions, but it isn't a show stopper for me...then again, I don't do a lot with 3d on my machine.
I think it is a memory addressing thing because it gets worse the longer the computer is up.

[quote=brendanpiater]This of course has to do with the new x server versions and features but surely... 3 versions later... common ATI/AMD
[/quote]
ATI works on 3 versions simultaneously. Many times corruption bugs like this get fixed on the 4th version, unless the bug is serious.

---

### Post by markbuntu on 2009-07-29
> **Zikona said:**
> markbuntu:

Can you share your xorg.conf? I am running similar set-up with 3 monitors and 2xHD4670. I just simply can not get the 3 monitor to get same resolution as the other 2 monitors.

Note: My current xorg.conf is attached.

My monitors all run on different resolutions. It was tricky to get it all working. It involved some backing and forthing and a lot of reboots but basically what I did was after a 

aticonfig --initial -f

This gave me only one active gpu with 2 displays. At this point CCC will not let you set independent displays (weird) or xinerama. So I enabled the third gpu/monitor and then could turn on xinerama. Then, to get the monitors in the correct order, I disabled the third display and set the first two to independent and then enabled the third display again. This put them in the 2,1,3 order I wanted with xinerama. I had to reboot after each step or things got really messed up.
I had no problems setting the resolution of each display after I did all that. 

It took a lot of fooling around to get it to work, mostly to get the displays in the correct order.  Big desktop did not work properly once xinerama was enabled, it tried to work but the resolutions were all screwed up and could not be adjusted, etc so I set all three as independent with xinerama. 


It seem that if you do a aticonfig --adapters=all then the monitors will be set up in 1,3,2 or 2,3,1 order. Never in 1,2,3 or 2,1,3 order. At least that is what I experienced with two monitors on my HD3650(gpu0) and one on my HD3450(gpu1).
 
I am not so big a fan of desktop effects anyway so it does not bother me to be without them. Three monitors without is better for me than only two with.

I hope that helps.

---

### Post by r2-d2 on 2009-07-30
> **lavinog said:**
> Can you be specific as to what isn't working.
 
It works on my hd3650 and my hd3200.
 
I get the graphics corruption issue that brendanpiater mentions, but it isn't a show stopper for me...then again, I don't do a lot with 3d on my machine.
I think it is a memory addressing thing because it gets worse the longer the computer is up.
 
 
ATI works on 3 versions simultaneously. Many times corruption bugs like this get fixed on the 4th version, unless the bug is serious.
 
I agree as far as the memory thing goes, and i agree as far as the computer uptime/performance goes. When using "default" xorg.conf configuration i can boot up normaly but with poor performance, after installing Catalyst 9.7 fglrx driver, i allways end up with black screen. I tried number of workarounds even with POSIX memory share and still ends up with black screen after reboot. I'm not using much of 3d also, but to have nice performance is not asking too much, right ?

---

### Post by brendanpiater on 2009-07-30
> **lavinog said:**
> ATI works on 3 versions simultaneously. Many times corruption bugs like this get fixed on the 4th version, unless the bug is serious.

Here's hoping! ;) Seems they been working on more bug fixes than new features which is a good thing. So fingers crossed we get some stability soon.

Good luck with your other issues, hope you can find a solution soon.

Cheers
B

---

### Post by r2-d2 on 2009-07-30
Just upgraded to kernel version 2.6.28-14. Installed patch xorg-server (2:1.6.0-0ubuntu14.1~nobackfill~1. Now, with "default" xorg.conf configuration i'm having much better performance than with kernel 2.6.28-13 or 11. Got my gdm up & running. Gonna install prop. drivers from AMD/ATI website just to see if im gonna have dose dkms errors again.

---

### Post by r2-d2 on 2009-07-30
> **r2-d2 said:**
> Just upgraded to kernel version 2.6.28-14. Installed patch xorg-server (2:1.6.0-0ubuntu14.1~nobackfill~1. Now, with "default" xorg.conf configuration i'm having much better performance than with kernel 2.6.28-13 or 11. Got my gdm up & running. Gonna install prop. drivers from AMD/ATI website just to see if im gonna have dose dkms errors again.

Problem Solved !!!! at least for me...
BIOS settings on T500 Lenovo on default conf uses Switchable graphics, changed it to Discrete and disabled option that OS should check for switchable graphics, got everything working like a charm ! Instaled 9.7 Cat form AMD/ATI website, rebooted and it works. Just make sure to have pre-installed new linux headers and lib6. Got both of my monitors, 22 inch, working on 1680x1050 16:10.    :popcorn:

---

### Post by lavinog on 2009-08-17
9.8 was released today.
It looks like dri is working again.
So far no black box corruption.

Firefox scrolling is slow with desktop effects enabled, but I think there was a workaround already addressed.

(Tested on radeon 3200)

---

### Post by pszpak on 2009-08-31
Radeon 4770 with one monitor and catalyst 9.8.

Everything works. Compiz, video (no problems).

---

### Post by brendanpiater on 2009-09-01
ATI 3670 working well so far on 9.8 drivers

WoW players on wine, mini-map works indoors now!!!! that's worth the upgrade alone :)

Laters
B

---

### Post by MarcusW on 2009-09-01
No 3d acceleration for me with 9.8. :( Back to 9.7 'til next release I suppose.

---

### Post by shrndegruv on 2009-11-03
has anyone gotten suspend/hibernate and resume to work?  For me, when resuming i always get stuck with a blank screen...

---

