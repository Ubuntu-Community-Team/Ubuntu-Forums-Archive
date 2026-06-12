---
title: "Grayed out (unavailable) USB devices in Sun VirtualBox 3.0.10 with 9.10 Karmic  Host"
date: 2009-11-07
forum: Virtualisation
---

### Post by LarryJ2 on 2009-11-07
1.  IF USB device doesn't appear to the guest OS and is unavailable inside the guest  OS.

2.  and/or   IF In the Guest window, under Devices->USB Devices, your USB devices appear but are grayed out...

3.  Try this:
[LIST=1]
[*]
[*] In the host (Karmic 9.10 for example), System->Administration->Users and Groups  
[*]Click on the Keys Icon (to right of Help) and give your password.
[*]Select (highlight) your normal user line (the one with /home/xxx)
[*]Click Manage Groups.  
[*]In the Groups settings List Box, navigate down to vboxusers
[*]With vboxusers high lighted,  click properties
[*]Click the check box next to your normal user to indicate you want the normal user to be a member of the vboxusers group.
[*]reboot the host.
[/LIST]

Hopefully, your USB devices should be visible inside your guest OS.  For example, in XP,  my  USB flash drive  device appears in My Computer as KINGSTON (E:) inside XP.

Please note that you have to tell VirtualBox allow your USB device under Details -> USB/Device Filters, first.   Just click on the button Details Tab button USB,   check Enable USB controller then click the USB+ icon at the right and place a check by the USB device you want your guest to have access to.

Also note this applies to the Non-Open Source Version of virtual box (the one installed from the repository)  The version you can get directly from SUN allows USB devices to be ported through to the guest.  OSE version does not.

Another note: If you have your USB thumb drive mounted in the host (mine is Karmic) an Icon will appear on the desktop.   If you have successfully completed the steps above,  when you start the guest, the Karmic host desktop USB icon disaappears to later return when you shut down the guest! (That is so neat!  Bravo Ubuntu)

Yes, I can read your mind...  If I could run Quicken directly under Karmic,  I wouldn't need XP!!.  I'm totally Linux except for Quicken and Turbo Tax.

---

### Post by davec64 on 2009-11-07
Nice one Larry!

Just to add to your post, if you install Virtualbox Guest additions it will give you the ability to left click the USB icon in the status bar at the bottom and select which USB Devices are passed through to the guest OS.

To install:
Select "Install Guest Additions" from the Devices menu.
or if that doesn't work install the .EXE from the CD/DVD drive within the Guest OS.

The Guest additions also give you a lot more functionality which is certainly woth an investigate!

By the way the above applies to the non free version, I don't think you have the option on the OSE version.

:)

---

### Post by tylergannon on 2009-11-07
D'oh!!  Should have realized that reinstalling the O/S might have reset the group membership... I remember doing this in the past but I don't recall having to do it for recent versions of VB... did something change?  I son't know who to contact @ Sun but seems like getting that group membership ought to be scriptable, or maybe there should be a README that pops up to tell dummies like me what to do after installing.

Anyhow thanks for the fix, it's much needed!
-Tyler

---

### Post by LarryJ2 on 2009-11-07
davec64 and all:

That's my understanding also.  You have to agree to Sun's User License (PEUL) before you can [_download_]("http://www.virtualbox.org/wiki/Downloads") the non-free binary from Sun, which provides USB support.  From [http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)
> Closed-source features ¶

    * USB support 

    VirtualBox implements a virtual USB controller and supports passing through USB 1.1 and USB 2.0 devices to virtual machines.

Sun at some point may start charging us hobby users but it's such a nice program that I would be willing to pay.

LJ

---

### Post by FozzIT on 2009-11-12
Hi!  I am new to the forum so I apologise if I am going over old ground but I have read a lot on this over the last few days and I am none the wiser! I have had most experience (and that isnt much) with dual booting Ubuntu 9.04 with XP but recently rebuilt my PC with 9.10 with a view to go strictly Linux! Obviously there are still those Windows apps that I need to run and saw Virtualbox as an option.

So my XP VM is running fine but still cannot view a usb device within my VM. I do not appear to have a vmusers group within Ubuntu when Virtualbox was installed so I cannot make myself a member of that. There does not appear to be any reference to usb devices in the VirtualBox console other than on the device menu of the VM itself. The usb option is not greyed out but when you select it the sub menu is empty and in fact greyed out.

I installed Virtualbox 3.0.10 from the software repository within Ubuntu rather than download it from the Virtualbox website (which is what I have done in the past when I first took a look at virtualbox). Does anyone feel that could make a difference?

I would appreciate any ideas that anyone may have? By the way I am planning a new build on another (hopefully slightly more butch PC) and am thinking of reverting back to 9.04 as I have performance reservations with 9.10!! Not sure what people make of that?

---

### Post by FozzIT on 2009-11-12
I am not sure but I think my problem could lie with intalling the OSE version of Virtualbox rather than the full one?

---

### Post by LarryJ2 on 2009-11-12
FozzIT:

Yes, I think you arrived at the correct deduction. As I understand it, there is no USB support in the  OSE / Repository version of VirtualBox.  However, USB support is available in the currently free but licensed version you can download from Sun.  LJ

---

### Post by FozzIT on 2009-11-13
Thanks again! I will be hopefully performing the new install over the weekend so I will let you know! It's all a learning curve but it keeps things interesting!

---

### Post by FozzIT on 2009-11-13
Oh and does anyone feel that 9.10 is tad more hungry than 9.04? Or is it just me?

---

### Post by ben2talk on 2009-11-16
> **FozzIT said:**
> Oh and does anyone feel that 9.10 is tad more hungry than 9.04? Or is it just me?

I didn't find that - but on first install, it was slower because of the wrong nVidia driver being installed, I had to manually check the recommended 18x driver - after that it seemed lighter and faster. Nautilus is still a pig.

---

### Post by zeefreak on 2009-11-16
i am having similar problems with 9.10 and virtualbox 3.0.10. i have installed the version from sun and added myself to the vboxusers group. when i go into virtualbox all the usb devices are present and i can create rules for them. when i start virtualbox, the usb devices i've told to go to the virtual machine disappear from my desktop, but they never show up in the virtual machine. as soon as i shut down the virtual machine, they appear again on my ubuntu desktop.

devices in question are a usb hard drive and an ipod nano. both work fine under ubuntu and on other windows systems. i've also checked in the windows disk manager, and they are definitely not showing up at all to the windows os.

---

### Post by zeefreak on 2009-11-16
aha. i figured it out. in the virtualbox settings configuration, if i check the box 'Enable USB 2.0 (EHCI) Controller' it breaks. unchecking this box, and all the usb devices work as expected. anyone have any clue why that might be? perhaps this checkbox does not do what i think it does, namely enabling 2.0 support instead of just 1.1.

---

### Post by mustali on 2009-11-16
Thank you.

---

### Post by WedgeHG on 2009-11-17
Thanks, LarryJ2, that was exactly what I needed. 

It should be noted that rebooting the host shouldn't be necessary. Logging out and then back in did the trick for me.

:grin:

---

### Post by FozzIT on 2009-11-19
Well I did a fresh install with 9.04 instead and downloaded the full version of virtualbox and after adding to the virtualbox users group am able to recognise the ipod without problem. Although I believe that the sycronisation within iTunes leaves a lot to be desired? Example being that I removed songs from the iPod and when disconnected, they were still there!

So I am assuming that 9.10 would be okay too although I still have performance reservations with it, so have decided to stick with 9.04 for the time being. Coupled with the hit and miss issues with iTunes I have decided to keep a separate Windows enviroment (as a server) for the few Windows apps I need to run (including iTunes) whilst keeping Ubuntu as my main desktop client.

As a side issue to this (my apologies as it is nothing to do with this topic) I have an HP printer that I wished to share on my home network (a mixture of Ubuntu & Windows clients) and with a library full of useless Windows software that came with the printer, I had little or no success of sharing this on a Windows platform due to multiple HP software errors that would occurr on the clients and the Windows print server itself.

Have now published the HP printer on my main Ubuntu client instead (easily) and the rest of the household can print merrily without incident (from either Windows or Linux)!

Just a massive Ubuntu success story (for me) that I had to share! :D

---

### Post by nulall on 2010-01-07
Thanks for this simple fix. It has (almost) all my USB devices showing up now.
Any idea why my printer is still grayed out or what I can do to fix/troubleshoot this?

---

### Post by psmccormick on 2010-01-09
> **nulall said:**
> Thanks for this simple fix. It has (almost) all my USB devices showing up now.
Any idea why my printer is still grayed out or what I can do to fix/troubleshoot this?

I am also having this problem with a printer. I am using 9.10 and VirtualBox 3.1.2 PUEL. I am a member of the vboxusers group. However, my printer is still grayed out in VirtualBox.

Any help would be greatly appreciated.

---

### Post by MisterBill on 2010-01-11
OMIGOD. I spent THREE DAYS trying to debug getting an iPod Nano to (a) be recognized in VirtualBox under Karmic and then (b) sync properly with Apple's disgracefully DRM'ed iTunes crapware (in XP as a VirtualBox guest OS).

And the answer was right here all the time -- "disable EHCI USB 2.0 support in your VirtualBox setup".

You guys are ubuntu.gods. I worship at your feet. 

May your lottery tickets all be winners,

Mister Bill

---

### Post by dukebytes on 2010-01-21
Thanks for all the info!!  I have been told that VB only works with USB if you "buy" the full version.  I have tried the group mgmt stuff and several other things, can't find half of it and no USB.

Hey I need to download the full version and then do the geeky stuff woohoo.

Have used my Ipod without changing a song since I loaded 8.04 and trashed windows a while back :)

Oh and just a side note - I run an older version of Quicken (95) in wine - works great!!

9.10 & 3.1.2 and Itunes here we come :)  Now just need to find that Lamb of God CD....

Thanks guys,
Duke

---

### Post by 68pontiac on 2010-01-28
> **nulall said:**
> Thanks for this simple fix. It has (almost) all my USB devices showing up now.
Any idea why my printer is still grayed out or what I can do to fix/troubleshoot this?

Found the solution for this sorta by accident but mostly by trial-and-error. Just like you add yourself to the vboxusers group add yourself to the lp group. Log out and back in and you should have usb printing capability. If not, ask somebody smarter than me. ;)

---

### Post by dvigue on 2010-02-02
> **LarryJ2 said:**
> 1.  IF USB device doesn't appear to the guest OS and is unavailable inside the guest  OS.

2.  and/or   IF In the Guest window, under Devices->USB Devices, your USB devices appear but are grayed out...

3.  Try this:
[LIST=1]
[*]
[*] In the host (Karmic 9.10 for example), System->Administration->Users and Groups  
[*]Click on the Keys Icon (to right of Help) and give your password.
[*]Select (highlight) your normal user line (the one with /home/xxx)
[*]Click Manage Groups.  
[*]In the Groups settings List Box, navigate down to vboxusers
[*]With vboxusers high lighted,  click properties
[*]Click the check box next to your normal user to indicate you want the normal user to be a member of the vboxusers group.
[*]reboot the host.
[/LIST]

Hopefully, your USB devices should be visible inside your guest OS.  For example, in XP,  my  USB flash drive  device appears in My Computer as KINGSTON (E:) inside XP.

Please note that you have to tell VirtualBox allow your USB device under Details -> USB/Device Filters, first.   Just click on the button Details Tab button USB,   check Enable USB controller then click the USB+ icon at the right and place a check by the USB device you want your guest to have access to.

Also note this applies to the Non-Open Source Version of virtual box (the one installed from the repository)  The version you can get directly from SUN allows USB devices to be ported through to the guest.  OSE version does not.

Another note: If you have your USB thumb drive mounted in the host (mine is Karmic) an Icon will appear on the desktop.   If you have successfully completed the steps above,  when you start the guest, the Karmic host desktop USB icon disaappears to later return when you shut down the guest! (That is so neat!  Bravo Ubuntu)

Yes, I can read your mind...  If I could run Quicken directly under Karmic,  I wouldn't need XP!!.  I'm totally Linux except for Quicken and Turbo Tax.

Thank you so much. I Freaking LOVE this forum. i have been trying for DAYS to get my External to work...I am so happy/ 

I LOVE UBUNTU!

Thanks guys!!!

---

### Post by rajush on 2010-02-10
> **LarryJ2 said:**
> 1.  IF USB device doesn't appear to the guest OS and is unavailable inside the guest  OS.

2.  and/or   IF In the Guest window, under Devices->USB Devices, your USB devices appear but are grayed out...

3.  Try this:
[LIST=1]
[*]
[*] In the host (Karmic 9.10 for example), System->Administration->Users and Groups  
[*]Click on the Keys Icon (to right of Help) and give your password.
[*]Select (highlight) your normal user line (the one with /home/xxx)
[*]Click Manage Groups.  
[*]In the Groups settings List Box, navigate down to vboxusers
[*]With vboxusers high lighted,  click properties
[*]Click the check box next to your normal user to indicate you want the normal user to be a member of the vboxusers group.
[*]reboot the host.
[/LIST]

Hopefully, your USB devices should be visible inside your guest OS.  For example, in XP,  my  USB flash drive  device appears in My Computer as KINGSTON (E:) inside XP.

Please note that you have to tell VirtualBox allow your USB device under Details -> USB/Device Filters, first.   Just click on the button Details Tab button USB,   check Enable USB controller then click the USB+ icon at the right and place a check by the USB device you want your guest to have access to.

Also note this applies to the Non-Open Source Version of virtual box (the one installed from the repository)  The version you can get directly from SUN allows USB devices to be ported through to the guest.  OSE version does not.

Another note: If you have your USB thumb drive mounted in the host (mine is Karmic) an Icon will appear on the desktop.   If you have successfully completed the steps above,  when you start the guest, the Karmic host desktop USB icon disaappears to later return when you shut down the guest! (That is so neat!  Bravo Ubuntu)

Yes, I can read your mind...  If I could run Quicken directly under Karmic,  I wouldn't need XP!!.  I'm totally Linux except for Quicken and Turbo Tax.

I did all possible things like "disable EHCI USB 2.0", re-installing Vbox from "http://www.virtualbox.org/wiki/Linux_Downloads", and every possible things that i could do, but it still shows me Grayed out (unavailable) USB devices for my Windows 7 guest. Is there anything that I might be doing wrong???!!!
Please somebody help !!!

Rajush

---

### Post by giovannilenzi on 2010-02-13
I had the same problem. Thanks for the solution!

---

### Post by ljmjr on 2010-12-06
Thanks for the information.  All went according to plan except I couldn't see the USB thumb drive in explorer.  After some looking around I found the version of XP that I loaded, for whatever reason, didn't load the USB drivers correctly.  
So if you and see the USB drives in the guest session's Devices>USB Devices and they are checked but you don't see them in windows explorer;  Go to Control Panel>Systems>Hardware>Device Manager and look at the USB section to ensure you don't see a yellow ?. If so click on it and reload the drivers.
Thanks again

---

### Post by ThomasNovin on 2011-06-02
Don't forget to install the Extension pack. You will need it if you have enabled USB 2.0 EHCI.

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

I had working USB but just now I noticed that it stopped working. When I installed 4.0.8 over my previous 4.0.4 + also upgraded the extension pack and the guest additions it started to work again!

---

