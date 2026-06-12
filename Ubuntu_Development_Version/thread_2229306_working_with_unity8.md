---
title: "working with unity8"
date: 2014-06-12
forum: Ubuntu Development Version
---

### Post by ventrical on 2014-06-12
There were major updates today. (I am starting a new thread because I do not want to interfere with the unity-next iso thread.) The actual hard install works very well now. The only problem I have is that it is asking for an Ubuntu One Account when I try to one many of the several apps available. So I guess I'll have to make an Ubuntu One Account :) The browser still does not work .. but the functionality has become more stable. It even has an Outlook app  (from Outlook Express days) from Microsoft but I am concerned if it is secure enough yet because I would have to enter my e-mail password online (or within the app itself. These are just some general notes on the unity8+mir flavour.

Regards..

---

### Post by cariboo on 2014-06-12
Why would you create another Ubuntu One account when you already have one, as it's needed to log into the Forum. We've seen way to many people have problems because of having two Ubuntu One accounts.

---

### Post by ventrical on 2014-06-12
> **cariboo907 said:**
> Why would you create another Ubuntu One account when you already have on, as it's needed to log into the Forum. We've seen way to many people have problems because of having two Ubuntu One accounts.


Well thanks Cariboo907 for answering my followup question. :) lol

Can I log in with my SSO?

Yes. 

Ok... that solves that .. whew...


thnx

Regards..

---

### Post by ventrical on 2014-06-12
ok .. unity updates .. mir updates .. etc.. now I just have big white mouse arrow:) lol

---

### Post by grahammechanical on 2014-06-13
@ventrical

I have been unable to get an install. I cannot figure out how to get the loading process to let me enter that boot command that you said would give us an install process. The two daily images I have tried load to the login screen without any error messages before hand.

Regards.

---

### Post by ventrical on 2014-06-13
> **grahammechanical said:**
> @ventrical

I have been unable to get an install. I cannot figure out how to get the loading process to let me enter that boot command that you said would give us an install process. The two daily images I have tried load to the login screen without any error messages before hand.

Regards.


Hi Graham,

Here is link of how I did it.

Don't forget to hit the TAB key just when the USB startup disk is booting.

[https://www.youtube.com/watch?v=J8X1K2I-nC0&feature=youtu.be](https://www.youtube.com/watch?v=J8X1K2I-nC0&feature=youtu.be)

Regards..

---

### Post by ventrical on 2014-06-13
Okay .. more libunity and mir updates plus api updates .. etc...

These updates restored the unity8+mir desktop and now I have the 'phablet' login screen.  (Can't take a screen shot just yet but I'll get a pic if I have time. ) 

  I recall graham, myself and a few others experimenting with the 'phablet' thingy and now it is here on the unity-next updates. Browser still does not work. I'll take a look around.

:)

---

### Post by ventrical on 2014-06-13
> **ventrical said:**
> Well thanks Cariboo907 for answering my followup question. :) lol

Can I log in with my SSO?

Yes. 

Ok... that solves that .. whew...


thnx

Regards..

Ok.. I was able to log on to Ubuntu One with my SSO. !! That was a fast update fix for sure.

Just remember.. anyone trying this out... it is like an iPhone tablet. Sometimes there appears to be problems when there really aren't any problems. For example; when I clicked <system settings>user accounts>ubuntu one> ... it all came up but it appeared that the keyboard would not allow me to enter my email and password. I then looked to the right side of the screen where the <system settings<   menu<  was being displayed with all it's widgets and I had to swipe it away , off from the screen with the mouse (no touch screen here) and then I was able to type in my email and password.

 It appears the developers are working very hard as the updates/upgrades are coming consistenly throughout the day.

Regards..

---

### Post by QDR06VV9 on 2014-06-13
Thats the ventrical we all know and love.;)

> **ventrical said:**
> Last edited by ventrical; 1 Hour Ago at 04:54 PM.                                                      _ Reason: curbing enthusiasm :) lol_

---

### Post by ventrical on 2014-06-14
:)

---

### Post by grahammechanical on 2014-06-14
@ventrical

Thanks for the video. The machine is still fighting against me. I have the Asus P5B delux Mboard that must be similar to the board you were demonstrating with. I have disabled Quick start and the BIOS splash screen. I have discovered the use of F8 to bring a boot selection popup menu where I can select which disk to boot from without changing the boot priority in the BIOS but I am still not getting an option to type in live-install.

So, it looks like I shall have to wait until the devs fix the autologin bug. Thanks for the effort.

Regards.

---

### Post by ventrical on 2014-06-14
> **grahammechanical said:**
> @ventrical

Thanks for the video. The machine is still fighting against me. I have the Asus P5B delux Mboard that must be similar to the board you were demonstrating with. I have disabled Quick start and the BIOS splash screen. I have discovered the use of F8 to bring a boot selection popup menu where I can select which disk to boot from without changing the boot priority in the BIOS but I am still not getting an option to type in live-install.

So, it looks like I shall have to wait until the devs fix the autologin bug. Thanks for the effort.

Regards.

With that mother board ... I have to go into BIOS each time I put in a bootable USB device. I then choose <Harddrive Configuration>  from the Boot menu of the regular BIOS. It will then show you the USB Flash Drive and you have to highlight it and then press SHIFT plus '+' to bring it up to the top of the boot menu the Save&Exit as normal and it should boot into the Ubu-next.iso, unless your BIOS is different than mine. Some of those BIOSes are weird like that where they will not automatically detect a USB bootable flash unless you go into the CMOS and set the harddrive config. The newer Intel boards from 2007 and up are like that too where there is this weird setting to get it to remember to boot from USB.

 Regards.

---

### Post by grahammechanical on 2014-06-14
@ventrical

I have no difficulty setting the boot priority to the optical driver or the USB port. I was just unaware that I had an F8 option that would let me choose to boot from sda or sdb or whatever was sitting in the DVD drive or USB port.

I was looking on planet.ubuntu and I found this blog I think it explains why you got that request for a Ubuntu One account.

> [COLOR=#333333][FONT=Ubuntu]Ubuntu phone (and tablet) users sign into their Ubuntu One account on their device in order to download or update the applications on their phone.[/FONT][/COLOR]

[http://developer.ubuntu.com/2014/06/10000-users-of-ubuntu-phone/](http://developer.ubuntu.com/2014/06/10000-users-of-ubuntu-phone/)

Another one of life's mysteries explained. Today's image has the autologin bug fixed. No more login screen. Now if only the desktop did not freeze the system. I think that is to do with Nvidia graphic adapters.

Regards.

---

### Post by ventrical on 2014-06-14
> **grahammechanical said:**
> @ventrical

I have no difficulty setting the boot priority to the optical driver or the USB port. I was just unaware that I had an F8 option that would let me choose to boot from sda or sdb or whatever was sitting in the DVD drive or USB port.

I was looking on planet.ubuntu and I found this blog I think it explains why you got that request for a Ubuntu One account.



[http://developer.ubuntu.com/2014/06/10000-users-of-ubuntu-phone/](http://developer.ubuntu.com/2014/06/10000-users-of-ubuntu-phone/)

Another one of life's mysteries explained. Today's image has the autologin bug fixed. No more login screen. Now if only the desktop did not freeze the system. I think that is to do with Nvidia graphic adapters.

Regards.


Ahhh.. thanks. I am using Intel Graphics. haven't tried any of my nVidia based machines. As for Ubuntu One.. sure .. I can now log-on to Ubu One but the apps will still not work, The Pictures app works and the 'Notes' app works but not much more than tan .. oh yes .. Accuweather works .. etc..  I took a video but it is  too low quality to put up atm.

Regards..

---

### Post by craig10x on 2014-06-18
Just Curious...does anyone know if unity 8 and mir are supposed to become the default in 14.10?  I have read conflicting reports...some say yes and others say it is still a long way off and that it likely won't become the default until the next LTS (16.04)...Thanks ;)

---

### Post by Elfy on 2014-06-18
I'm pretty sure that the default in 14.10 will be the same as 14.04. 

I'm also pretty sure that they are aiming for 16.04 for the big changes - I've not seen anything to the contrary in m/l.

---

### Post by ventrical on 2014-06-18
> **Elfy said:**
> I'm pretty sure that the default in 14.10 will be the same as 14.04. 

I'm also pretty sure that they are aiming for 16.04 for the big changes - I've not seen anything to the contrary in m/l.

Long ways away. :) I'll keep unity8 on the shelf a bit then. Lots of other work to do. :)

---

### Post by grahammechanical on 2014-06-18
The recent Ubuntu Online summit had a session where a convergence progress report was presented. About 14 minutes into the session there is a slide - roadmap to the converged desktop.

[http://summit.ubuntu.com/uos-1406/meeting/22246/convergence-progress-report/](http://summit.ubuntu.com/uos-1406/meeting/22246/convergence-progress-report/)

Twice it was said, this is not written in stone. 

> 14.10 - focus on mobile
Ubuntu Desktop, Unity 7
Ubuntu touch, Unity 8

15.04 - focus on convergence
Ubuntu Desktop, Unity 7
Ubuntu touch, Unity 8

15.10 - convergence shake out
Ubuntu, Unity 8

16.04 LTS - focus on stability and long Term Support.

I find this Ubuntu Desktop Next ISO image to be very interesting. It is where convergence code gets its first airing. Convergence is going on right now. Testing desktop next over the next two development cycles will be much more interesting than the usual development branch. By the 16.04 development cycle it will be back to boring.

Regards.

---

### Post by craig10x on 2014-06-18
Thanks guys...that's what i thought it would be (not until 16.04)...i guess for now they are concentrating on just improving unity 7 as much as possible until 8 is ready to take over :)

---

### Post by Alan F on 2014-06-18
> **craig10x said:**
> Thanks guys...that's what i thought it would be (not until 16.04)...

That's not what the slides say. There is no mention of Unity 7 in 15.10, only Unity 8.

Thus we can assume that Unity 8 will become default sometime in the 15.10 dev cycle and Unity 7 removed. 

This makes sense as no sane person would want Unity 8 to be introduced to the community in the LTS 16.04.

---

### Post by grahammechanical on 2014-06-18
> [COLOR=#000000]Thus we can assume that Unity 8 will become default sometime in the 15.10 dev cycle and Unity 7 removed. [/COLOR]

+1

We have to think in terms of development cycles and not release dates. If the Ubuntu Desktop Next code branch is stable and equal to the 15.04 development branch by the time of 15.04's release with all major problems solved, then there must be a switch over of branches during the 15.10 development cycle. Or at the very least the beginning of the 16.04 development cycle.  According to my method of guessing, anyway. Better to have two cycles of user testing before releasing an LTS.

---

### Post by ventrical on 2014-06-18
> **Alan F said:**
> That's not what the slides say. There is no mention of Unity 7 in 15.10, only Unity 8.

Thus we can assume that Unity 8 will become default sometime in the 15.10 dev cycle and Unity 7 removed. 

This makes sense as no sane person would want Unity 8 to be introduced to the community in the LTS 16.04.


I had tested Win8/64 on old desktops with it's new fastboot and on some machines it was impressive. From a competitive standpoint it is a little disappointing as I thought we were 'damn the torpedos - full speed ahead' with mir and phablet for the desktop in this cycle. However, if it's not working until 15.10 then I am satisfied with Trusty or Unity 7 on Utopic. It all works here :)lol

Regards..

---

### Post by craig10x on 2014-06-18
my bad..yes, re-reading the slide i see they are talking about having unity 8 and mir as default by 15.10...makes sense....LTS is always geared to stability and not introducing really radically new stuff ;)

---

### Post by zika on 2014-06-18
> **craig10x said:**
> my bad..yes, re-reading the slide i see they are talking about having unity 8 and mir as default by 15.10...makes sense....LTS is always geared to stability and not introducing really radically new stuff ;)That is why, as it seems to me, we have two parallel development processes and I was thinking about proposing two different forums for each of them...

---

### Post by Elfy on 2014-06-18
> **zika said:**
> ... I was thinking about proposing two different forums for each of them...

Ask - but unlikely, if we still closed dev forums it might have been worth doing. 

We could possibly add a prefix to this sub-forum.

---

### Post by ventrical on 2014-06-18
> **Elfy said:**
> Ask - but unlikely, if we still closed dev forums it might have been worth doing. 

We could possibly add a prefix to this sub-forum.


Well..  isn't unity8-next a development flavor after all, running parallel to Utopic?

---

### Post by philinux on 2014-06-19
Some progress.

[http://www.omgubuntu.co.uk/2014/06/ubuntu-devs-demo-gtk-apps-running-mir-unity-8?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29](http://www.omgubuntu.co.uk/2014/06/ubuntu-devs-demo-gtk-apps-running-mir-unity-8?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29)

---

### Post by grahammechanical on 2014-06-23
Gettting this thread back on topic. I have finally installed Ubuntu-Desktop-Next. I have been testing the Next ISO images every couple of days and the image 20140623 brings up the usual GUI Try - Install dialog. TRY just gets to the phablet home screen and freezes but that is another thread.

The install option brings up the familiar Ubiquity GUI installer which installs as it usually does. Booting brings up the familiar login screen and logging in brings up the phablet home page which freezes. So, it is progress of a sort.

I can use recovery mode to update/upgrade and will do so daily to see how things improve. Resume brings up the login screen but logging in causes bounce-back with the password panel blanked out. Resume = llvmpipe.
 
No failsafeX option in Recovery menu. Well there wouldn't be? Would there. So, someone is giving thought to what is needed.

Regards.

---

### Post by Mateusz Stachowski on 2014-06-24
> **grahammechanical said:**
> Gettting this thread back on topic. I have finally installed Ubuntu-Desktop-Next. I have been testing the Next ISO images every couple of days and the image 20140623 brings up the usual GUI Try - Install dialog. TRY just gets to the phablet home screen and freezes but that is another thread.

grahammechanical if I remember correctly you have an NVIDIA card so you are testing on Nouveau. If yes then you most likely hit the same bug as I am. You could check ~/.cache/upstart/unity8-mir.log and /var/crash directory for unity8 crashes. 

If you will see in unity8-mir.log this line:

> nouveau: kernel rejected pushbuf: Invalid argument

then it is the same thing I have and it is reported as [Bug #1298914]("https://bugs.launchpad.net/ubuntu/+source/unity8/+bug/1298914").

---

### Post by ventrical on 2014-06-24
My main install now only presents me with a large white arrow (from early Mir testing days) and the daily-live gives me the same thing. I am not going to trash my current install - just ride out the updates but I am working stricktly on Intel Graphics devices  so I have yet to try nVidia or my ATi box. So I am going to try different boxes .. time permitting.

Regards..

---

### Post by grahammechanical on 2014-06-24
I had heard that there was problems with Nouveau. I will put in another install with tomorrow's image (20140625) and will activate the Nvidia proprietary driver. Desktop-Next needs to be tracked on both open and closed source video drivers. By the way, today's update brought in an upgrade to Unity8 that left me with the same black screen and the mouse pointer that was used in the past to indicate we were running xmir/mir.

Regards.

---

### Post by Mateusz Stachowski on 2014-06-25
> **grahammechanical said:**
> I had heard that there was problems with Nouveau. I will put in another install with tomorrow's image (20140625) and will activate the Nvidia proprietary driver. Desktop-Next needs to be tracked on both open and closed source video drivers. By the way, today's update brought in an upgrade to Unity8 that left me with the same black screen and the mouse pointer that was used in the past to indicate we were running xmir/mir.

Regards.

I can already tell you it is not going to work.

You forgot that closed source drivers don't support Mir or Wayland.

---

### Post by grahammechanical on 2014-06-25
I had not forgotten. But something has to give or 16.04 is going to break every time someone installs 16.04 and ticks "Install third party software." Xmir worked with Nouveau but not with Nvidia but at present there is a mir/nouveau bug. So, we are not getting very far on Nvidia adapters. Such is life.

I see three ways that I can track the development of Ubuntu Desktop Next (Unity 8) over the next 12 - 18 months. I can have two installs, one on an open source video driver and one on a proprietary video driver and then update/upgrade every day or so to see how things are progressing. I can also, from time to time, run the live session.

Today's update changed login>black screen to login>bounce back. And so we live.

Update: Using Nvidia GT 220

desktop-next + Nouveau driver = login screen bounce with ability for repeated login attempts.
desktop-next + Nvidia driver = login screen bounce without ability for repeated login attempts.

Well, the Nvidia driver got further than I expected it to get.

> [COLOR=#333333][FONT=sans-serif]The first version of the iso is going to include Xorg still (needed for our current lightdm greeter and ubiquity)[/FONT][/COLOR]

[https://blueprints.launchpad.net/ubuntu/+spec/client-1410-unity8-desktop-iso](https://blueprints.launchpad.net/ubuntu/+spec/client-1410-unity8-desktop-iso)

Regards.

---

### Post by ventrical on 2014-06-25
Just got the White Mir Arrow here on Live sessions across Ati , nVidia and SandyBridge but I plan to install on SandyBridge ans see what happens.

---

### Post by mc4man on 2014-06-25
The current test iso remains useless here (other than creating some notes & waiting for inevitable freeze up.
To move to semi-useless I'd need file manager, network & terminal apps

---

### Post by ventrical on 2014-06-27
A full rack of mir and unity8 updates thismorning and all I get is bounce back to login screen.

---

### Post by cariboo on 2014-06-27
I installed in Virtualbox yesterday, and I can log in, but it doesn't get past the login screen. At least I can shut it down using the icon in the upper left. :-P

---

### Post by Mateusz Stachowski on 2014-06-27
> **cariboo907 said:**
> I installed in Virtualbox yesterday, and I can log in, but it doesn't get past the login screen. At least I can shut it down using the icon in the upper left. :-P

VirtualBox doesn't support Mir so this won't work regardless in what state the current Unity 8 preview is in at the moment.

If you want to test in virtual machine then use VMware Player because it supports Mir. I posted screenshot with Unity 8 running in VMware Player in the [other thread]("http://ubuntuforums.org/showthread.php?t=2228993&p=13049656#post13049656").

---

### Post by ventrical on 2014-07-07
after todays updates , unity8 w mir is working once again. The 'phablet' screen will come up and you can do some swiping but browser still does not work. You can shut down too from top left , though , it is a little touchy at first. You have to click gear then pull down menu with mouse .. etc..

Such is the state of unity8 :) lol

edit .. it looks like a gigantic iphone :)

---

### Post by ventrical on 2014-07-16
After todays updates/upgrade I am atctually typing this in from the phablet browser. Ubuntuforums is a whole new experience with the way the browser works. I'll try to get some screen shots.edit:Ok .. at the bottom of the page you have to choose 'full site' to get the standard ubuntuforums experience.

EDIT:

The ubuntuforums editor does not work as usual  on the phablet as it does on the normal ff Unity desktop. Also .. will not shut down and close other windows. More or less.. it's hit and miss atm.. Probably will be for a time.

---

### Post by bcschmerker on 2014-07-20
> **grahammechanical said:**
> I had not forgotten. But something has to give or 16.04 is going to break every time someone installs 16.04 and ticks "Install third party software." Xmir worked with Nouveau but not with Nvidia but at present there is a mir/nouveau bug. So, we are not getting very far on Nvidia adapters. Such is life.

I see three ways that I can track the development of Ubuntu Desktop Next (Unity 8) over the next 12 - 18 months. I can have two installs, one on an open source video driver and one on a proprietary video driver and then update/upgrade every day or so to see how things are progressing. I can also, from time to time, run the live session.

Today's update changed login>black screen to login>bounce back. And so we live.

Update: Using Nvidia GT 220

desktop-next + Nouveau driver = login screen bounce with ability for repeated login attempts.
desktop-next + Nvidia driver = login screen bounce without ability for repeated login attempts.

Well, the Nvidia driver got further than I expected it to get.



[https://blueprints.launchpad.net/ubuntu/+spec/client-1410-unity8-desktop-iso](https://blueprints.launchpad.net/ubuntu/+spec/client-1410-unity8-desktop-iso)

Regards.
Concerning Unity™ 8, are similar problems being encountered with the X.org Radeon drivers, as of 19 July 2014? the Advanced Micro Devices® FGLRX package?  I'm looking into building an upgrade LinUX box around an ASRock® Z68 Pro3-M and a still-undetermined video display adapter; if I've a decent chance of running the Radeon® HD™ 6850 in this build, it'll allow me to concentrate on requirements for a video card for a Win 9 box that, as of July 2014, is a concept formulation study.

---

### Post by rrnbtter on 2014-07-23
Greetings,

I installed the Unity Next DVD last night. I was able to get to desktop and login to the internet. I found it interesting that systemd was default. I installed firefox from terminal but didn't use it. Running sudo apt-get update from the terminal borked the system even though it downloaded and installed some updates.  Not much funtionality for a one gig download. I will try and keep up after I reinstall.

Oh! PS!  I zsynced my Ubuntuu 14.10 iso using the Unity- Next zsync and only had to download 37% of the iso.

---

### Post by grahammechanical on 2014-07-23
@rrnbtter

What video adapter? As of yesterday I am still not getting beyond the login screen on my Nvidia GT220. It might be useful to know what at present works with Desktop Next and what does not.

Regards

---

### Post by rrnbtter on 2014-07-23
Greetings,
@Grahammechanical
Sorry for the ommission. The Launchpad release that prompted me to give this a try did mention that mesa was supported which tipped the scale in favor taking time for the installation. All of my systems are integrated intel.

rrnbtter@Toshiba-Satellite-L305:~$ sudo lshw -C video
[sudo] password for rrnbtter: 
  *-display:0             
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:45 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:5110(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:d3500000-d35fffff
rrnbtter@Toshiba-Satellite-L305:~$

---

### Post by rrnbtter on 2014-07-23
Greetings,
In addition, I was for the first time with the new releases able to make a USB install disk.  For the noobie I suggest that the "persistence" not be used since any errors will be persistent and can create a no boot situation on the USB.  Also It used to be that we set a boot flag on the desired boot partition but that has now been moved to a boot partition selection dropdown box at the bottom of the partitioner. This is important since it will default to the USB and not the desired partition. Hence, choosing the desired boot drive is crucial to a successful. My USB installer is also borked since I added persistence and now it stalls with a screen having the Ubuntu 14.10 in the middle. It may take me a day or so to fix all of this due to my limited time.

---

### Post by ventrical on 2014-07-23
Intel video graphics seems to be the preferred graphic adapter to use. I got the browser working, video, gallery, successful logout etc. It will download apps but not install them on the apps screen. There is a Unity panel hide screen with the apps already on them.

The unity8 experiments I did with Mir  on raring and saucy were much more manageable running from the terminal.(at least I could take screenshots). Although there has been a lot of progress (using intel graphics) it still seems like  unity8 is connected to the unity-system-compositor on stilts.  What I am seeing as of today's updates is a pre-empted framework being laid for more stable things to come.

 Also the telltale 'Mir' arrow in the top left corner of the screen has been greatly downsized.

[s]*note*  I tried on ATi/nVidia boxes .. but no screen at all.[/s]

*edit*

In all fairness to the developers I must comment that there is a certain learning curve that has to be considered while working with unity8. Keeping in mind that it is trying to transpose keyboard/mouse strokes/movements into touch interperetation. So, at first, some things may seem not to work in a conventional sense but if you think touch-mentality.. then they might. For example to get the full logout screen you have to hold your mouse over the top right gear wheel,  hold down left click and then drag downwards and release. You will then see the full menu.

---

### Post by ventrical on 2014-07-23
> **rrnbtter said:**
> Greetings,
In addition, I was for the first time with the new releases able to make a USB install disk.  For the noobie I suggest that the "persistence" not be used since any errors will be persistent and can create a no boot situation on the USB.  Also It used to be that we set a boot flag on the desired boot partition but that has now been moved to a boot partition selection dropdown box at the bottom of the partitioner. This is important since it will default to the USB and not the desired partition. Hence, choosing the desired boot drive is crucial to a successful. My USB installer is also borked since I added persistence and now it stalls with a screen having the Ubuntu 14.10 in the middle. It may take me a day or so to fix all of this due to my limited time.


ditto!

In some cases , persistence can be very useful .. but not in devel.

---

### Post by rrnbtter on 2014-07-23
Greetings,
I have for quite some time believed that what works is based on the platform being used by the particular developer. He is getting compatibility on his own machine. As some backup for this idea, I was on a Launchpad link the other day and a dev maintainer said that he had released a "fix" for a particular module but could't try it out on the noted platform "only his own".  This could be why "everything" doesn't work until the release. Some of the required support is written but not integrated. Intel seems to be the basic platform since servers don't need much video plus a great deal of support from intel.

---

### Post by grahammechanical on 2014-07-23
> **rrnbtter said:**
> Greetings,
I have for quite some time believed that what works is based on the platform being used by the particular developer. He is getting compatibility on his own machine. As some backup for this idea, I was on a Launchpad link the other day and a dev maintainer said that he had released a "fix" for a particular module but could't try it out on the noted platform "only his own".  This could be why "everything" doesn't work until the release. Some of the required support is written but not integrated. Intel seems to be the basic platform since servers don't need much video plus a great deal of support from intel.

I agree with that. I have no problem with that. At least the code is being converged. From my eaves-dropping on Ubuntu On Air video chats I know that the main focus of development is to get Ubuntu phone/tablet ready for release to the manufacturers by the end of August. Once that deadline is met I expect more developers will switch to working on convergence and I am sure that some will work on getting Desktop Next running on the various video adapter hardware that is out there. And so we live.

Regards.

---

### Post by ventrical on 2014-07-23
> **rrnbtter said:**
> Greetings,
I have for quite some time believed that what works is based on the platform being used by the particular developer. He is getting compatibility on his own machine. As some backup for this idea, I was on a Launchpad link the other day and a dev maintainer said that he had released a "fix" for a particular module but could't try it out on the noted platform "only his own".  This could be why "everything" doesn't work until the release. Some of the required support is written but not integrated. Intel seems to be the basic platform since servers don't need much video plus a great deal of support from intel.

 I am currently doing two fresh installs with form factors that have the N210 and the HD 5450. I'll be back. I erroneously made the comment that I had tried these two form factors when in fact it was Sandy Bridge.

Regards..

---

### Post by ventrical on 2014-07-23
Working nominally so far on HD 5450. Posting this message from Next Browser.Regards..

```

ventrical@ventrical-P5QL-PRO:~$ lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:1a.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6
00:1d.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIB (ICH10) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cedar [Radeon HD 5000/6000/7350/8350 Series]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cedar HDMI Audio [Radeon HD 5400/6300 Series]
02:00.0 Ethernet controller: Qualcomm Atheros AR8121/AR8113/AR8114 Gigabit or Fast Ethernet (rev b0)
ventrical@ventrical-P5QL-PRO:~$ 

```

---

### Post by rrnbtter on 2014-07-23
Greetings, 
I just zsynced my Unity Next ISO and it's hard to believe that there is a 17% difference in one day. 
Read /home/rrnbtter/utopic-desktop-i386-u8.iso. Target 83.7% complete.

verifying download...checksum matches OK
used 878948352 local, fetched 172410641

---

### Post by rrnbtter on 2014-07-23
Greetings,
Well I installed my new U8 iso onto my USB and ran it in 'try' mode. Must say it is much nicer than yesterday. Makes me want to go out and buy a touch screen laptop. The app store works and everything. I am still going to the ctrl alt f2 terminal to shutdown. sudo shutdown -H now.  It seems like the mouse actions are working better today than yesterday.  I'm still finding my way around but it is working fine. 
PS     With Unity Next defaulting to systemd it now makes sense why it is an option in Utopic. It is part of the 67% that is common between the two releases. IMHO

---

### Post by ventrical on 2014-07-24
And actually some of the apps are actually working .. like Flappy Bird for instance. :)  I tried to guide the bird through the first set of poles and the bird banged into the pillars and it crashed :)

---

### Post by Mateusz Stachowski on 2014-07-24
> **rrnbtter said:**
> PS     With Unity Next defaulting to systemd it now makes sense why it is an option in Utopic. It is part of the 67% that is common between the two releases. IMHO

Unity Next does not default to systemd as init it still uses Upstart. If it would default to systemd as init you would have this line in grub entry:

[http://www.piware.de/2014/04/booting-ubuntu-with-systemd-test-packages-available/](http://www.piware.de/2014/04/booting-ubuntu-with-systemd-test-packages-available/)

> To actually boot with systemd, press Shift during boot to get the grub menu, edit the Ubuntu stanza, and append this to the linux line: init=/lib/systemd/systemd.

Also the whole Unity 8 is currently only a phone and tablet affair so far and systemd isn't used in Ubuntu phones.

[http://www.piware.de/2014/04/booting-ubuntu-with-systemd-now-in-utopic/](http://www.piware.de/2014/04/booting-ubuntu-with-systemd-now-in-utopic/)

> Also this hasn’t yet been tested on the phone at all. I’m sure that it’ll require quite some work (e. g. lxc-android-config has a lot of upstart jobs). To clarify, there is nofixed date/plan/deadline when this will be done, in particular it might well last more than one release cycle. So we’ll “release” (i. e. switch to it as a default) when it’s ready :-)

---

### Post by rrnbtter on 2014-07-24
Greetings,
The Terminal app is not installing. It goes through the process then the download fails. Anyone have a terminal in Unity8 desktop?

---

### Post by ventrical on 2014-07-25
> **rrnbtter said:**
> Greetings,
The Terminal app is not installing. It goes through the process then the download fails. Anyone have a terminal in Unity8 desktop?


atm it will not install. It shows all the pics and etc.. but I can't get that one running either.

---

### Post by rrnbtter on 2014-07-25
Greetings,
@ventrical, Thanks I was just fishing for a workaround. This desktop seems to be a "lock out" much like android. I can do a ctrl alt f2 and get to utopic root but not to Unity8 root. so there is clearly two things at work here, Unity8 and Utopic. Im interested to see where "terminal" puts me (probably Utopic).

---

### Post by grahammechanical on 2014-07-25
This kind of thing is what makes tracking convergence interesting. I would expect a phone/tablet OS to be very restrictive as to what the user can change. I also heard some talk about there being a developer mode so developers could install and test their apps. And then we have the desktop where users expect much more freedom.

Regards.

---

### Post by rrnbtter on 2014-07-25
Greetings,
@grahammechanical, Exactly! and couple of days ago I ran an apt-get update && apt-get upgrade from the root (ctl alt f2) and it borked my Unity8 but Unity8 has an Update app which should theoretically only update Unity 8 and not the underlying Utopic (at this time at least).

---

### Post by rrnbtter on 2014-07-25
Greetings,
In addition, when I go to root and shutdown my system using 'shutdown -H now'  I get considerable systemd service calls in the shutdown stream. Yet  proc/1 indicates that upstart is running. This causes me to think about the meaning of the appearance of the systemd-shim and complete systemd update that recently appeared in Utopic. I think that with the Unity Next system Utopic is using Upstart and the Unity8 desktop is using systemd. This sounds wierd but I know for a fact that systemd is being used without booting systemd (from default grub).

---

### Post by grahammechanical on 2014-07-25
The promise was that the change over would not be noticeable to the user. I see that as meaning gradual and tested. Can Ubuntu run Upstart and SystemD at the same time? Or is it an all or nothing choice? I can imagine, in my simplistic way of thinking, a process where Upstart scripts are re-written to work with either Upstart or SystemD and then when the switch is thrown and everything is playing nicely with everything else, those scripts being cleaned up to work only with SystemD.

Do not forget that Ubuntu has to sync with Debian. So, Debian has to make many changes before Ubuntu can pull them in.

Regards.

---

### Post by rrnbtter on 2014-07-25
Greetings,
@grahammechanical, So then! could it be possible that the systemd litter that I am seeing at root (display) is synthetic and that it is upstart masquerading as systemd? I can accept the possibility of that idea. Also, I think that Cannonical walks away from Debian on this one, unless you think that debian will be running apps also. There is questions in the spinoff segment, xubuntu, kubuntu, puppy, mint etc, as to their plight over this Unity Next convergence of Phone, Tablet and Desktop. In other words how do they continue as 'buntu's' with this new paradigm (not to change topics, just to follow your statements).

---

### Post by rrnbtter on 2014-07-26
Greetings, 
I updated my Ubuntu-desktop-next dvd last night and performed a complete reinstall.  Unity 8 seems to be the same but the partitioner in the installer has vastly improved. Now that the USB creator in Utopic is working I am burning the ISO to my USB stick instead of DVD-RW. From USB it is only a few minutes to install. The Unity 8 install takes less time than it does to create the USB Startup in the first place.  The Unity8 desktop seemed smoother but I don't have a way to benchmark the experience and I don't have a touch system so its click.

---

### Post by grahammechanical on 2014-07-26
> [COLOR=#000000]In other words how do they continue as 'buntu's' with this new paradigm (not to change topics, just to follow your statements).[/COLOR]

That is exactly what I am thinking. Debian chose SystemD and Ubuntu also chose it because Ubuntu is built on Debian. But what will the developers of the spin-offs do? Stop at 14.04?

Regards.

---

### Post by ventrical on 2014-08-04
Unity 8 desktop is changing fast. Still a lot of bugs but it is getting better and better.  The whole log-on style has changed now.  It interacts a lot faster also .. My only complaint is that I can't take screenshots or use programs like gnome-terminal.

---

