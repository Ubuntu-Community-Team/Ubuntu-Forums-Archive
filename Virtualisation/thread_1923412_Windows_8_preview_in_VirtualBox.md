---
title: "Windows 8 preview in VirtualBox"
date: 2012-02-10
forum: Virtualisation
---

### Post by Rebelli0us on 2012-02-10
I'm playing around with Windows 8 Developer Preview, but Guest Additions video driver is NOT loading.  My monitor is 1920x1080 but Win8 screen resolution is only 1280x1024, the rest of the screen is blank. Any ideas?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=212448&stc=1&d=1328901980[/IMG]

---

### Post by japzone on 2012-02-11
VirtualBox's Guest Additions are not yet compatible with Windows 8. A Workaround for the Screen Resolution problem can be found here:
[**http://www.windows7hacker.com/index.php/2011/09/running-windows-8-on-virtualbox-with-additional-wide-screen-resolution/**]("http://www.windows7hacker.com/index.php/2011/09/running-windows-8-on-virtualbox-with-additional-wide-screen-resolution/")

I used this trick and I've now got a Perfect Widescreen Windows 8 running in VB.

---

### Post by Rebelli0us on 2012-02-11
> **japzone said:**
> VirtualBox's Guest Additions are not yet compatible with Windows 8. A Workaround for the Screen Resolution problem can be found here:
[**http://www.windows7hacker.com/index.php/2011/09/running-windows-8-on-virtualbox-with-additional-wide-screen-resolution/**]("http://www.windows7hacker.com/index.php/2011/09/running-windows-8-on-virtualbox-with-additional-wide-screen-resolution/")

I used this trick and I've now got a Perfect Widescreen Windows 8 running in VB.

ThaNk you, that worked, you're golden.

The path "C:\Program Files\Oracle\VirtualBox\VBoxManage.exe" does NOT exist on my system. So the command must be run on the **HOST**. In my case from the linux Terminal:

```
VBoxManage setextradata "w8-preview" CustomVideoMode1 1920x1080x32
```

Device Manager in the Guest Win8 still shows that "VirtualBox Graphics Adapter" is not loading, "Windows cannot initialize the device driver for this hardware. (Code 37)".

BTW, Microsoft Visual Studio is a shadow of its former days, even their own examples crash as they load in the IDE. I doubt that many developers will invest the time to learn all this "new" stuff.

---

### Post by japzone on 2012-02-11
> **Rebelli0us said:**
> ThaNk you, that worked, you're golden.

The path "C:\Program Files\Oracle\VirtualBox\VBoxManage.exe" does NOT exist on my system. So the command must be run on the **HOST**. In my case from the linux Terminal:

```
VBoxManage setextradata "w8-preview" CustomVideoMode1 1920x1080x32
```

Device Manager in the Guest Win8 still shows that "VirtualBox Graphics Adapter" is not loading, "Windows cannot initialize the device driver for this hardware. (Code 37)".

BTW, Microsoft Visual Studio is a shadow of its former days, even their own examples crash as they load in the IDE. I doubt that many developers will invest the time to learn all this "new" stuff.
Yeah the command has to be run on host because obviously the Guest doesn't have anything VirtualBox installed since GE isn't currently compatible.

PS:Windows 8 Dev Preview is as it's name states a Preview for Devs. It's not a fully functioning copy of Windows 8. It's just to show people what the New Metro UI looks like and how it works. The Customer Preview(aka Beta version) of Windows 8 is set to come out at the end of this Month and should be much more Stable and Feature filled(ie An App Store will be Available).

---

### Post by Greg J Preece on 2012-02-19
Just reinstalled the developer preview in VirtualBox on my laptop to get into VS11, found this thread, and had a bit of a play with the VM. I've managed to get hardware accelerated graphics working (mostly) correctly, along with some other stuff. Performance on the VM is much improved, and it was relatively easy to get going.

First of all, using the instructions found in the VirtualBox additions ISO under the 64Bit/ folder, extract the driver package using this command:

VBoxWindowsAdditions-amd64 /extract /D=C:\Drivers

(I'm assuming here that you're running 64 bit. Adjust as necessary for 32 bit.)

Next, open up device manager, if you can figure out how. (I just love how Metro has made this a convoluted process. It's the future.) If you haven't done any fiddling yourself since install, you'll notice that the component jumping out at you with warning signs is a base system device. Right click, hit "Update driver software", and in the wizard, select "Browse my computer for driver software." Aim the wizard at C:\Drivers and let rip. You should see some new system devices spring into life in the device manager. Marvellous.

Now it's on to the graphics drivers. These are installed the same way - the device you're updating drivers for is the Microsoft standard doodad under "Display Adaptors" in the device manager. My trick here was to install both bundled drivers, one after the other. The standard driver installed but couldn't initialise after restart, so then I installed the WDDM driver over the top - bam, accelerated 3D, and no errors during install.

[s]The part that doesn't work yet is the screen resolution. The monitor still shows up in device manager as a generic non-PnP monitor, so none of the usual VirtualBox screen resolution trickery works yet. I'm still working on this, but for now the resolution VboxManage tweak detailed earlier in the thread suffices.[/s]

Edit - scratch that. After a reboot or two I resized the VM's window and Win8 followed suit. Screen res now working perfectly. :)

I'm also having some issues with disk I/O lagging the VM quite badly, but that might be because I'm currently the Win8 VM in Win7, with the VDI running from my Linux partition, (on a MacBook, hehe) so it's not what you would call a standard setup!

Edit - This was in VirtualBox 4.1.8, **not** 4.1.2 as is currently in the 11.10 repositories.

Hope that helps. :)

---

### Post by japzone on 2012-02-23
> **Greg J Preece said:**
> Just reinstalled the developer preview in VirtualBox on my laptop to get into VS11, found this thread, and had a bit of a play with the VM. I've managed to get hardware accelerated graphics working (mostly) correctly, along with some other stuff. Performance on the VM is much improved, and it was relatively easy to get going.

First of all, using the instructions found in the VirtualBox additions ISO under the 64Bit/ folder, extract the driver package using this command:

VBoxWindowsAdditions-amd64 /extract /D=C:\Drivers

(I'm assuming here that you're running 64 bit. Adjust as necessary for 32 bit.)

Next, open up device manager, if you can figure out how. (I just love how Metro has made this a convoluted process. It's the future.) If you haven't done any fiddling yourself since install, you'll notice that the component jumping out at you with warning signs is a base system device. Right click, hit "Update driver software", and in the wizard, select "Browse my computer for driver software." Aim the wizard at C:\Drivers and let rip. You should see some new system devices spring into life in the device manager. Marvellous.

Now it's on to the graphics drivers. These are installed the same way - the device you're updating drivers for is the Microsoft standard doodad under "Display Adaptors" in the device manager. My trick here was to install both bundled drivers, one after the other. The standard driver installed but couldn't initialise after restart, so then I installed the WDDM driver over the top - bam, accelerated 3D, and no errors during install.

[s]The part that doesn't work yet is the screen resolution. The monitor still shows up in device manager as a generic non-PnP monitor, so none of the usual VirtualBox screen resolution trickery works yet. I'm still working on this, but for now the resolution VboxManage tweak detailed earlier in the thread suffices.[/s]

Edit - scratch that. After a reboot or two I resized the VM's window and Win8 followed suit. Screen res now working perfectly. :)

I'm also having some issues with disk I/O lagging the VM quite badly, but that might be because I'm currently the Win8 VM in Win7, with the VDI running from my Linux partition, (on a MacBook, hehe) so it's not what you would call a standard setup!

Edit - This was in VirtualBox 4.1.8, **not** 4.1.2 as is currently in the 11.10 repositories.

Hope that helps. :)

Should be useful when Win 8 Customer PReview comes out and I'll really want to start messing around with it :)

---

### Post by lovinglinux on 2012-03-02
> **Rebelli0us said:**
> ThaNk you, that worked, you're golden.

The path "C:\Program Files\Oracle\VirtualBox\VBoxManage.exe" does NOT exist on my system. So the command must be run on the **HOST**. In my case from the linux Terminal:

```
VBoxManage setextradata "w8-preview" CustomVideoMode1 1920x1080x32
```

Device Manager in the Guest Win8 still shows that "VirtualBox Graphics Adapter" is not loading, "Windows cannot initialize the device driver for this hardware. (Code 37)".

BTW, Microsoft Visual Studio is a shadow of its former days, even their own examples crash as they load in the IDE. I doubt that many developers will invest the time to learn all this "new" stuff.

Thanks. This works for Consumer Preview as well.

---

### Post by Rebelli0us on 2012-05-19
> **lovinglinux said:**
> Thanks. This works for Consumer Preview as well.

Yes confirmed, resolution fix works. But after installing Guest Additions the OS will no longer boot! And where is the Start Menu?

---

