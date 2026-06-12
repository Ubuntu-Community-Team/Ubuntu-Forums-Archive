---
title: "VMware network adapter not working"
date: 2009-05-10
forum: Virtualisation
---

### Post by scottr1 on 2009-05-10
Hello all, I have recently jumped in with both feet to Ubuntu Jaunty Jackalope from Windows XP. So far I am loving it but find there are some programs from windows that I would like to run, so I installed VirtualBox OSE and Installed TinyXP Ver. 9 in that. Everything went fine with the install, but the network adapter will not start according to the device manager.

I have read quite a few threads on this and other forums about similar issues. I have tried uninstalling and re-installing the device and drivers to no avail.

There is also another matter of sharing folders. Am I right in assuming that I need to enable file sharing in linux in order for the VM Windows install to see these folders? I installed the sharing packages but when I try, i'm informed that I do not have permission and to: "Ask the administrator to add the line "usershare owner only = false" to the [global] section of the smb.conf to allow this."

I have edited the smb.conf file and restarted following the change but I still cannot share.

Any help you can give would be appreciated.

Thanks, from a newb

---

### Post by bobince on 2009-05-10
[assuming you do mean VirtualBox-OSE and not VMware as in the title]

> **scottr1 said:**
> Installed TinyXP Ver. 9 in that. Everything went fine with the install, but the network adapter will not start

Maybe TinyXP has removed the driver for the network adapter that VirtualBox emulates by default (PCnet-FAST III). You could try to get a driver off a full XP disc, but probably best first try changing the emulated network card in VirtualBox (VM Settings->Network->Adapter Type->Intel PRO/1000) to see if TinyXP has a working driver for that one.

> Am I right in assuming that I need to enable file sharing in linux in order for the VM Windows install to see these folders?No, VirtualBox uses its own mechanism to share files; it's not dependent on SMB on either side. You don't need Samba on the host, nor the Windows file-sharing services running/bound on the guest side.

You *can* also share files through SMB manually by setting up your own SMB server on the host as you were trying, but if you're only trying to swap files with the virtual machine there's no need.

---

### Post by scottr1 on 2009-05-11
Bobince, thanks so much. I was not aware you could change network adapters but i did and it worked flawlessly.

Two more questions if I may:

You mentioned that I do not need to share folders in Ubuntu in order to see them in VirtualBox OSE but when I open My computer in VM Windows, I see only the C drive, A drive (Floppy) and D drive (DVD burner). Do I need to do something else to see my two remaining internal drives and USB connected WD MyBook?

I thought I read somewhere that VirtualBox OSE does not support USB but under the devices menu, "USB devices" are listed. I plugged in my Creative Zen and Linux sees it but VM Windows does not. 2.1.4_OSE is the version, would you know if it does support USB?

Thanks again. Scott

---

### Post by bobince on 2009-05-11
> **scottr1 said:**
> Do I need to do something else to see my two remaining internal drives and USB connected WD MyBook?

Yes, you have to tell VirtualBox to share the folder you want accessible on each device with the guest. (It might not be a good idea to completely share the entire Linux filesystem with the guest.) You can do this from the Settings or by right-clicking the folder icon in the VirtualBox window status area (bottom-right).

Then if you've given your shared folder the name ‘hostdocuments’, you can access it in the guest's Explorer by typing the UNC path “\\vboxsvr\hostdocuments” in the address bar. You can use a ‘net use’ or similar command to mount the path under a drive letter if you like.

> I thought I read somewhere that VirtualBox OSE does not support USB but under the devices menu, "USB devices" are listed.

Yeah, I'm not quite sure what that's for on OSE; maybe it's just a useless vestigial menu. Certainly you won't be able to give the Windows guest direct USB-level access to the device on OSE.

If you just want to use the device as a USB Mass Storage Device, you can mount it in the Linux host and share a folder on it to the guest. If it's not one of the USB-MSD-compliant Zens you'd need to use the Sun (closed-source) full-VirtualBox to get them connected. Though if you're just trying to put music on, some Linux audio tools do also have that capability natively (which ones depends on whether it's an MTP-supporting Zen or not).

---

### Post by scottr1 on 2009-05-11
Thanks again, it really is pretty cool that you can run an entire O/S inside another. Not that I want to, but how many Virtual machines could you have? Are you just limited by disk space?

I didn't quite understand how to access the folder once it was shared but I finally found it under my network which makes sense now that I think about it.

It's weird, I can access my Zen through Ubuntu and transfer files to/from but the Zen doesn't see them on the device. I thought at first it was because of messed up MP3 tags so I tried editing them,but that was no help. It seems the Zen only sees the items that I put on originally with Windows. If I remove a file from the Zen with linux and then put it back on, the player no longer recognizes it even though I can see it with nautilus.

Since the Zen doesn't read filenames, only ID3 tags, could Ubuntu be altering the tags somehow making them unreadable to the player or am I just talking out my behind?

---

### Post by bobince on 2009-05-12
> **scottr1 said:**
> how many Virtual machines could you have? Are you just limited by disk space?

Yes, and by RAM if you're running more than one at the same time.

> Since the Zen doesn't read filenames, only ID3 tags, could Ubuntu be altering the tags somehow making them unreadableUnlikely. What'll probably be happening is some sort of confusion between the type of connection the computer has with the device. Depending on what player you have (there are many completely different players all still called “Zen”), this could be:

* USB Mass Storage (simplest: computer accesses and controls the filesystem on the device as if it were an external hard disc);

* Media Transfer Protocol (originally Windows Media Player-specific, now partially standardised. The device controls the filesystem and provides limited access to files to the computer);

* A Creative-proprietary protocol known as PDE.

Extra fun is generated when more than one is supported. For example USB Mass Storage might be supported as a way of using the device to transfer files between machines, but not for loading music.

Check which way you are accessing the device on both platforms. If you are using Windows Media Player on Windows, you're using MTP. If you have to use special Creative software on Windows, it's probably PDE. If you are browsing the device like a hard disc on Linux, it's probably USB Mass Storage. But if it's a ‘gphoto’ URL, it's MTP.

To access PDE devices under Linux you will need gnomad. MTP devices can be synchronised using this or a variety of music player apps. See [http://en.wikipedia.org/wiki/Creative_ZEN#Alternative_software](http://en.wikipedia.org/wiki/Creative_ZEN#Alternative_software). Some Zens are PDE by default but can have their firmware upgraded to support MTP, which gives them a better chance of working with more software on any platform.

This is all a horrible mess. I wish the branded MP3 player manufacturers had just stuck with good old USB Mass Storage, which has always worked everywhere with the simplest interface possible. Curiously, many of the cheap no-brand players still work this way, making them a better deal for many users.

---

### Post by scottr1 on 2009-05-12
> Check which way you are accessing the device on both platforms. If you are using Windows Media Player on Windows, you're using MTP. If you have to use special Creative software on Windows, it's probably PDE. If you are browsing the device like a hard disc on Linux, it's probably USB Mass Storage. But if it's a ‘gphoto’ URL, it's MTP.I'm pretty sure it is MTP. I have always used drag and drop in Windows. I did have to install WMP11 for windows to be able to see the device, but once plugged in to USB it came up as another drive.

In Linux, it has been much the same, once I installed LIBMTP, upon plugging the unit into USB, a nautilus window comes up and I can drag and drop. I can see all of the content I put on the drive actually go there but the player does not recognize it.

You mentioned a gphoto URL; I'm not sure where I would see that but funnily enough, on occasion when I plug the unit in I will get an error message that Linux cannot access the camera. When this happens, I have to do a "cleanup" in the device before it is recognized again.

> 
To access PDE devices under Linux you will need gnomad. MTP devices can be synchronised using this or a variety of music player apps. See [http://en.wikipedia.org/wiki/Creative_ZEN#Alternative_software](http://en.wikipedia.org/wiki/Creative_ZEN#Alternative_software). Some Zens are PDE by default but can have their firmware upgraded to support MTP, which gives them a better chance of working with more software on any platform.Could the version of LIBMTP have something to do with it? I do have Gnomad 2 and I just tried transferring files to the ZEN through it. Once again, according to the program the transfer happened and nautilus sees them, but the player doen't recognize anything. I will give the software you recommended a try next.

---

### Post by scottr1 on 2009-05-12
I uninstalled VirtualBox OSE and installed the latest full version from Sun. I thought I would need to reinstall Windows but it kept my existing intallation. Once I figured out how to enable USB support, I was able to sync using WMP. I am also able to drag and drop just as I used to and the player recognizes everything.

---

