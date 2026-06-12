---
title: "Black Screen / No USB with VirtualBox (Windows XP)"
date: 2008-05-06
forum: Virtualisation
---

### Post by Bennett2005 on 2008-05-06
Hi everybody,

Backstory:  I'm working on getting a nice transitional setup for my parents to get them switched over to Ubuntu.  They're running Windows XP right now, and I'm planning on switching them over during the coming weekend when my wife and I visit.

I'm looking to VirtualBox for a simple solution to handle a couple applications, mostly Quicken and iTunes.  I'm having a couple problems with getting the setup figured out and I'm wondering if anyone has any suggestions.

I'm running Hardy Heron (reg) with 2g RAM and an ATI 9700 128mb video card with proprietary drivers enabled.

1:  Cannot get USB support functioning properly
    I've been banging my head against the wall over this one for the better part of a couple of hours.  I'm running the non-OSE version of VirtualBox just to get the USB support, but I can't get past an error message in the settings.  It has to be familiar, because I've found a lot of history about it.  The error reads:

Error message: " Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.

"Result Code: 0x80004005 Component: Host Interface: IHost {81729c26-1aec-46f5-b7c0-cc7364738fdb} Callee: IMachine {31f7169f-14da-4c55-8cb6-a3665186e35e} "

I've followed the suggestions from the actual [VirtualBox]("http://www.virtualbox.org/ticket/747") website and I've found the same problem listed in [their forum]("http://forums.virtualbox.org/viewtopic.php?t=5622"), but I still cannot get rid of the above error.

2:  Black Screen in Seamless Mode
    When I fire up the Windows XP install and go into seamless mode, the screen behaves poorly.  Clicking on the windows xp taskbar rights the display, but clicking in numerous other places will black out the background or cause slow performance.  I've allocated 32mb of video memory in the VirtualBox settings.

Any help here would be huge.  Especially with the USB problem.  I'm not as concerned about the seamless mode, because I can still run XP in a smaller window.  Seamless would be much nicer but I'm more concerned about the lack of USB functionality.

Thanks!  :)

---

### Post by Bennett2005 on 2008-05-06
USB is now working!!! Very Happy, big thanks to the Sasquatch from the VirtualBox forums for helping me out.

I followed the first option in the guide in this post:

[http://forums.virtualbox.org/viewtopic.php?p=21294#21294](http://forums.virtualbox.org/viewtopic.php?p=21294#21294)

Works very well, and will help keep my folks hooked on their iTunes addiction for a little while longer until I can set up a proper intervention. It's a serious issue. Rolling Eyes

Now the only Virtualization related problem is the black screen.

---

### Post by Lord_Phoenix on 2008-05-07
You'll have to disable special effects (compiz) to get Seamless working properly, there's a few compatibility issues between this two.

I did it by going to System / Preferences / Appearance the I think it's the first option on the last tab (the rightmost one). After that I got it working a bit better. It works even better if you remove XP's background image, you're going to see it anyway.

If you want to take a step forward and make it feel more integrated, try applying a Ubuntu Human theme to Windows XP.

---

