---
title: "VirtualBox &amp; VMWare ... My experience ... and hence doubts !!!"
date: 2016-02-01
forum: Virtualisation
---

### Post by Muzafsh on 2016-02-01
Hello Community,

As the title of the thread reads, my experience of more than 5 years of VirtualBox on Ubuntu and my less than a few days of VMWare Workstation experience has led me to start this thread and clarify on my too good to be true observations.

I have been an Ubuntu user for more than 5 years, my work entails me to use Coreldraw, this being the only reason for me to still be connected to Windows, Not willing to go down the road of dual booting into Windows OS(in spite of having that option) for using Coreldraw, I was let to explore the world of Virtualization, hence came across VirtualBox and i have been using it ever since.

I have conky running on my desktop with the memory & CPU graphs running realtime.

All throughout my VirtualBox use, my VBox VM used to take up the entire RAM allocated to it and my conky would display accordingly, Eg. If my VBox VM was assigned 4GB of RAM for Windows 7 Guest, my conky would show around 6GB of RAM as being used which makes perfect sense.

Recently a few days ago i thought of trying VMWare Workstation on a trial basis ... TO MY TOO GOOD TO BE TRUE MOMENT ... i discovered that an exact same VM configuration being run on VMWare Workstation with 4GB of RAM when booted into show very little RAM being consumed.

My conky desktop shows that my total RAM consumption with my 4GB VMWare VM running Windows 7 actively with Coreldraw, Adobe Photoshop and Picassa album being opened in it show no more than 15%(of my total of 16GB RAM) of memory usage with RAM being used displayed as less than 2.5GB, at times going as high as 3GB, never more than 3.5GB.

The response of the Windows 7 guest running on VMWare Workstation is soooooo smooth that i just can't believe it, i am just not convinced that things are running waaaaaaay smoother MOST IMPORTANTLY WITH LESS THAN 3.5GB OF total RAM being used by both the Host and Guest machines simultaneously.

assuming it must be conky mis-reporting, i checked inside Ubuntu System Monitor, and that confirms the readings displayed by the Conky desktop widget.

HOW IS THIS EVEN POSSIBLE ?

Is VMWare equipped to take only that much RAM that it requires and not Block the total RAM allocated to it in the VM settings, Atleast VirtualBox does seem to do so, blocking the entire RAM allocated to it. In this case 4GB with 1.5-2GB which is being used by the Ubuntu Host totalling to 5-6GB memory usage display on Conky and the same confirmed on Ubuntu System Monitor as well, I WOULD LIKE TO ADD THAT THE RESPONSIVENESS OF Windows 7 is not as smooth on VBox VM as being experienced on VMWare currently ... JUST CAN'T BELIEVE IT.


VMWare VM : "Host + Guest" RAM Consumption = not more than 3.5 GB ----------- JUST UNBELIEVABLE !!! (Experience Waaaaaaaaaay Smooother)
VBox VM : "Host + Guest" RAM Consumption = 5-6 GB ------------------------------- MAKES SENSE (normal as my experience of more than 5 yrs with it)


IS THAT EVEN POSSIBLE ???

thanks in advance for any clarifications.

---

### Post by sammiev on 2016-02-01
VMWare has been the one for me over all the ones I have tried.

I never tried Windows as a Guest, my Linux OS and its programs use little memory as the programs are small.

Enjoyed reading your post.

---

### Post by Muzafsh on 2016-02-01
thanks,
Seems like its already started being the one for me now, now that i like its snappy response on the win7 guest, With some nifty shortcuts, i am in and out of it in a jiffy, literately hibernating in and out of it.

I would still like to know(if any experts hangout around here) if the VMWare does really have a tiny memory footprint or its some miscalculation which the gnome-system-monitor(& conky) are failing to pickup !!!

---

### Post by Brent_Crossland on 2016-02-01
I'm curious if you notice any video performance issues with VMWare?  I read recently that VMWare provides the guest with better access to the GPU.  Made me wonder if I should move.

I have been 'weaning' myself off Windows for the past year but still use it about 20% of the time. I have VirtualBox running on Ubuntu 15.10 and recently upgraded the Win7 guest to Win10.

---

### Post by KillerKelvUK on 2016-02-02
Hey guys, just sharing some observations as they're kind of aligned, hopefully a VMWare guy may give you a more direct response.

I use KVM/Qemu to virtualise my guests including Windows10 but I have a couple of linux server vm's also.  Up until recently I've just used virtual gfx adapters and SPICE for remote access to my Windows vm which gives me a very smooth desktop experience...my only tie to Windows being for work/corporate use.  Recently however I've introduced a dedicated GFX card into the Windows vm and use VFIO passthrough...my intentions being for gaming.  Now to the point of this thread and my post...to further improve performance of the guest one of the configurations I introduced was memory backing pages...won't bore you with the details (as I'm still wrapping my head around them) but in summary the committed memory for the guest isn't reported as consumed by my host OS (Ubuntu using a conky desktop like you ;))...but the Windows guest clearly thinks it has 8GB available and with the games I'm running this is definitely being used.

So as I have virtual machines where the host OS does report the memory allocation and some that don't (as a result of the memory management process I've introduced) I would say its certainly possible that VMWare Workstation is managing its resources in a way that Conky and the standard Ubuntu resource monitoring binaries cannot discern.

---

### Post by Muzafsh on 2016-02-02
Well ... interesting observations ... not a gaming buff, but never the less i might need your observation in future with regard to efficiently utilizing graphics inside my VM's ... planing to introduce an external graphics card into my setup.

In the meanwhile i was researching on possible clues of any leaks with gnome-system-monitor (& conky).

I hit upon this interesting website [http://www.linuxatemyram.com/](http://www.linuxatemyram.com/), going by this site it seems ... too good to be true ... is actually TRUE !!!

AND DATS REALLY EXCITING !!!

**_With my VMWare VM running ..._**

terminal command : free
outputs the following ...

command@terminal:~$  free
                                           total            used           free        shared        buffers     cached
Mem:                              16341920      **[COLOR=#a9a9a9]7224860[/COLOR]**    9117060    4554316       3308      4835540
-/+ buffers/cache:             **[COLOR=#ff0000]2386012[/COLOR]**     [COLOR=#33cc00]**13955908**[/COLOR]
Swap:                             17425404          0          17425404

gnome-system-monitor reports - **[COLOR=#ff0000]2.3 GB[/COLOR]** (**[COLOR=#ff0000]14.7%[/COLOR]**) of 15.6GB ... of RAM in use. ----------- conky has picked up **[COLOR=#ff0000]2.29GB[/COLOR]** (**[COLOR=#ff0000]14%[/COLOR]**) ... same as System Monitor



**_With my VBox VM running ..._**

terminal command : free
outputs the following ...

command@terminal:~$  free
                                           total            used           free        shared        buffers     cached

Mem:                               16341920     [COLOR=#a9a9a9]**7146540**[/COLOR]     9195380    376272         2716     638200
-/+ buffers/cache:             **[COLOR=#ff0000]6505624[/COLOR]**       [COLOR=#33cc00]**9836296**[/COLOR]
Swap:                             17425404          0   17425404

gnome-system-monitor reports - **[COLOR=#ff0000]6.3 GB[/COLOR]** (**[COLOR=#ff0000]40.4%[/COLOR]**) of 15.6GB ... of RAM in use. ----------- conky has picked up **[COLOR=#ff0000]6.2GB[/COLOR]** (**[COLOR=#ff0000]40%[/COLOR]**) ... same as System Monitor.


-----------------
If you read from the above ... the RAM marked in GREY is what i was reading ... and ... i was almost certain that there was a leak in calculating on the part of gnome-system-monitor(& conky which might have relied on GSMonitor) as both were pretty much at the same place ... as far as memory consumption went.

[B]VBox       -      VMWare
[/B]**[COLOR=#A9A9A9]7224860 -     [/COLOR]**[COLOR=#a9a9a9]**7146540**[/COLOR]
-----------------------

[B]BUT ...
[/B]
As [www.linuxatemyram.com]("http://www.linuxatemyram.com") ... goes ... the total RAM available for use is the one marked in GREEN above.

[U]**VBox** Vs [B]VMWare
[/B][/U]
[COLOR=#ff0000]**6.3 GB (40.4%)**[/COLOR] against [COLOR=#33cc00][B]2.3 GB (14.7%)
[/B][/COLOR]
CAN I ... safely ... CALL THIS IMPRESSIVE !!!

If only some expert could vet the same for me !!!



PS : Not being a fanboy or anything, just surprised at the recent observations and how can 2 competing products have such a distance in the technologies between them !!!


thanks for looking !!!

---

