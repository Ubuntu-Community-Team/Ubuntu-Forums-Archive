---
title: "Possible major breakage with nVida after updates"
date: 2014-02-08
forum: Ubuntu Development Version
---

### Post by ventrical on 2014-02-08
Just a followup. Just got some major breakage with a system using a nVidia GeForce 210/218. GRuB menu will allow for a recovery session so I can only try to look there for probs or try and reinstall nouveau as it seems to be using some generic VESA driver that slows it right down to molasses in reovery mode and then drops back to black screen after hard boot.

---

### Post by ventrical on 2014-02-08
All is well with SandyBridge.

---

### Post by rrnbtter on 2014-02-08
Greetings,
I have two Intel chipsets with Intel video, one Celeron and one Atom   dual core and both are working perfectly with all current updates   including  3.13.0-8-generic kernel. Sorry about your problems hope this   helps narrow it down.

---

### Post by rrnbtter on 2014-02-08
Greetings,
Could be that if you wait until tomorrow and then update from the terminal it may come back up.  Seems like I did that once on a no-boot situation.

---

### Post by ventrical on 2014-02-08
Thanks .. It appears to be with nVidia only.

---

### Post by ventrical on 2014-02-08
> **rrnbtter said:**
> Greetings,
Could be that if you wait until tomorrow and then update from the terminal it may come back up.  Seems like I did that once on a no-boot situation.

I removed the nVidia card and am back on Intel graphics. All is well. 

 I just report  these bugs here as that is what we do.

---

### Post by QDR06VV9 on 2014-02-08
> **ventrical said:**
> I removed the nVidia card and am back on Intel graphics. All is well. 

 I just report  these bugs here as that is what we do.

Got to give him props for coming to your rescue anyway:P 
Vent I just had problems with current updates(midsum mismatch) waited about 30 minutes
updated again and upgrade and dist-upgrade all is good with Nvidia Drivers.:)
And yes we just report  these bugs here as that is what we do.
Oh we are getting your polar vortex also..lol

---

### Post by ventrical on 2014-02-08
> **runrickus said:**
> Got to give him props for coming to your rescue anyway:P 
Vent I just had problems with current updates waited about 30 minutes
updated again and upgrade and dist-upgrade all is good with Nvidia Drivers.:)
And yes we just report  these bugs here as that is what we do.
Oh we are getting your polar vortex also..lol


Yes .. on this other machine all is ok. But I do not think it is nVidia drivers but nouveau drivers that was borked .. or mabey something else.

As for the Polar Vortex ... :) sheesh .. this winter has been somthing up here in Canada ..

doh .. service call ... :)

---

### Post by QDR06VV9 on 2014-02-08
> **ventrical said:**
> As for the Polar Vortex ... :) sheesh .. this winter has been somthing up here in Canada ..

I Have a friend that just got back from there taking care of a family member, and she said it was [COLOR=#0000ff]**bloody cold**[/COLOR] and 
Lots and Lots of Snow..;)

---

### Post by cariboo on 2014-02-08
I thought I had a similar problem after the latest kernel update, my system was running just plain weirdly. It looked like it was a graphics driver problem, but when I did get it to boot, it would run fine until it timed out and went into lock mode. The hard drive light was on constantly, and the cpu and graphics adapter fans were running at full bore.

I finally tracked it down to one of the data cables had worked loose from one of the hard drives, after re-seating the plugs, things are back to normal. I have the same GeForce 210/GT218 as ventrical and I'm running the default nvidia 331.38 drivers from the repositories.

---

### Post by Elfy on 2014-02-09
Got same card here as well , I actually booted the nvidia install yesterday, got updates for it (not been in it for a while), working fine earlier today.

---

### Post by ventrical on 2014-02-09
> **cariboo907 said:**
> I thought I had a similar problem after the latest kernel update, my system was running just plain weirdly. It looked like it was a graphics driver problem, but when I did get it to boot, it would run fine until it timed out and went into lock mode. The hard drive light was on constantly, and the cpu and graphics adapter fans were running at full bore.

I finally tracked it down to one of the data cables had worked loose from one of the hard drives, after re-seating the plugs, things are back to normal. I have the same GeForce 210/GT218 as ventrical and I'm running the default nvidia 331.38 drivers from the repositories.

Actually  , after looking in the repositories, none of the nVidia drivers are installed nor is (was) the nouveau driver installed.

Best I can do to verifiy this is reinstall the card, go to terminal from GRuB Recovery Option and install the drivers from there, although the Intel driver is working much better now.

---

### Post by ventrical on 2014-02-09
> **Elfy said:**
> Got same card here as well , I actually booted the nvidia install yesterday, got updates for it (not been in it for a while), working fine earlier today.

Thanks Elfy .. just realized that no nVidia drivers are installed.

:)

---

### Post by ventrical on 2014-02-09
After trying both nvidia and nouveau drivers I only get some screen version of llvmpipe as it cannot sync with the monitor (nvidia). 

However I do not blame ubuntu install as this was a swap out from another PC so I could only file a bug if I did a fresh install on this PC with the nVidia graphics adapter card installed during the installation process. I know from past experience that Ubuntu is very versatile with jockying card swaps but sometimes with some machines this is not always the case and a fresh install is needed to report a proper testing result.

---

### Post by ventrical on 2014-02-09
On the particular machine in question I have two (2) installs of Trusty i386.:) On the second install (which has not been updated for a while) nouveau is working just swell so there must have been something borked during the last update (on the prior install).  I will now update/upgrade this install on the same system and see what gives.

edit : 
btw .. this current  was orignally a xubuntu install with Ubuntu Unity desktop installed.

```

 *-display
                description: VGA compatible controller
                product: GT218 [GeForce 210]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:49 memory:92000000-92ffffff memory:80000000-8fffffff memory:90000000-91ffffff ioport:2000(size=128) memory:93080000-930fffff
           *-multimedia

```

---

### Post by ventrical on 2014-02-09
update/upgraded and nouveau works well. One caveat though. The update/upgrade actually knocked out lightdm unity greeter and replaced it with gdm!

---

### Post by Elfy on 2014-02-10
>  replaced it with gdm! did it boot, if it did woohoo - earlier in the cycle I got hit with this [https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1267442](https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1267442) :)

---

### Post by ventrical on 2014-02-10
wow ! .. Thanks for that link. I may be able to fix the first installation. As for this one with the switched lightdm to gdm .. I just booted it , using it now and it works exceptionally, but this one is using nouveau.

---

### Post by ventrical on 2014-02-10
ok.. In /lightdm/lightdm.conf.d I only have the file 10-unity-system-compositor.conf which contains:

[CODE]
[SeatDefaults]
type=unity;xlocal
unity-compositor-command=unity-system-compositor.sleep
[CODE]
  
@elfy
 so I do not see where I can apply some of the suggestions here from your bug report

---

### Post by Elfy on 2014-02-10
> @elfy
so I do not see where I can apply some of the suggestions here from your bug report It wasn't really intended to - I'm sure since then there's been some changes in lightdm that make it all 'too old' 

Or at least that's how it's appeared the few times I've looked at those files since then. To be honest I don't do much more in this sub-forum than look for the 1% of threads that aren't Ubuntu related - the majority don't interest me too much. Sometimes I might comment in a non-something other than Ubuntu thread ;)

---

### Post by zika on 2014-02-10
/etc/lightdm/lightdm.conf

---

### Post by Elfy on 2014-02-10
> **zika said:**
> /etc/lightdm/lightdm.conf

Installed studio today 

> /media/hob/Studio/etc/lightdm$ ls
lightdm.conf.d            lightdm-gtk-greeter-ubuntu.conf
lightdm-gtk-greeter.conf  users.conf

---

### Post by jamesmudry on 2014-02-10
Hi I'm trying to update drivers for Nvidia 9800 gtx+ and getting no where I'm new to linux and xubuntu
So how do I do this

---

### Post by jamesmudry on 2014-02-10
oh I'm on my son's pc and he got the Nvidia 9800 gtx+

---

### Post by QDR06VV9 on 2014-02-10
> **jamesmudry said:**
> Hi I'm trying to update drivers for Nvidia 9800 gtx+ and getting no where I'm new to linux and xubuntu
So how do I do this
Update or Install?
Are you aware you are in a Development Forum?
If you are just trying to install them
```
sudo apt-get update && sudo apt-get install nvidia-331
```
You will have to reboot to get your new driver..
Welcome to Ubuntu!
Regards:)

---

### Post by ventrical on 2014-02-10
> **zika said:**
> /etc/lightdm/lightdm.conf

 Thats the whole thing zika. On the system in question there is no lightdm.conf  Only lightdm.conf.d which contains the file 10-unity-system-compositor.conf

regards..

---

### Post by ventrical on 2014-02-10
> **runrickus said:**
> Update or Install?
Are you aware you are in a Development Forum?
If you are just trying to install them
```
sudo apt-get update && sudo apt-get install nvidia-331
```
You will have to reboot to get your new driver..
Welcome to Ubuntu!
Regards:)


 Maybe this is where I have been doing somthing wrong. I have been using:

```

sudo apt-get install nvidia-current

```

regards..

---

### Post by zika on 2014-02-10
> **Elfy said:**
> Installed studio today
> **ventrical said:**
> Thats the whole thing zika. On the system in question there is no lightdm.conf  Only lightdm.conf.d which contains the file 10-unity-system-compositor.conf
regards..I've just answered to the question @ventrical asked about which fle is in the bug report mentioned earlier...
> **Elfy said:**
> did it boot, if it did woohoo - earlier in the cycle I got hit with this [https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1267442](https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1267442) [IMG]http://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG]
> **ventrical said:**
> @elfy
 so I do not see where I can apply some of the suggestions here from your bug report

---

### Post by ventrical on 2014-02-10
> **zika said:**
> I've just answered to the question @ventrical asked about which fle is in the bug report mentioned earlier...


Thanks for the clarification.

my bad here..

---

### Post by Elfy on 2014-02-10
2 of us ...

---

### Post by jamesmudry on 2014-02-10
Ok sorry runrickus I didn't know the area I was in but I did do what you said code 
sudo apt-get update && sudo apt-get install nvidia-331
and than rebooted and try to run steam
and steam says when I start it " your system is running older proprietary nVidia video driver
steam requires drivers version 304.22 or higher"
so can you tell me where to go in the forum to get the help so I won't be posting here where I shouldn't be Thanks

---

### Post by Elfy on 2014-02-10
> **jamesmudry said:**
> ...
so can you tell me where to go in the forum to get the help so I won't be posting here where I shouldn't be Thanks

Try here [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

---

### Post by jamesmudry on 2014-02-10
> **Elfy said:**
> Try here [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)
Thanks

---

### Post by zika on 2014-02-10
> **ventrical said:**
> Thanks for the clarification.
my bad here..
> **Elfy said:**
> 2 of us ...
Even though /etc/lightdm/lightdm.conf is depreciated (as is xorg.conf) I think that it is „in the loop“ and it is being read on the start of LightDM... I could be wrong, it would not be the first time...

---

### Post by ventrical on 2014-02-10
I updated the trusty daily and reinstalled without formatting, saving all my files .. etc..  I certainly haven't solved the bug  or have determined what happened but I'll mark this solved for now.

---

