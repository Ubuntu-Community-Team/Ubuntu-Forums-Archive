---
title: "Using Virtual Box with Ubuntu 10.10"
date: 2010-11-09
forum: Virtualisation
---

### Post by Stormsy on 2010-11-09
Hi all,

I upgraded Ubuntu 10.04 to 10.10 and it's great!

However, for work I need to use some drawing packages that are only designed for Windows (I know there are Linux versions but the Windows version is better, so to say.)

Anyhow - someone suggested using Virtual Box and so that's why I'm here; I have a copy of Virtual Box on disc, but I read somewhere that if I need to install Windows I need to have the Windows Version of Virtual Box...?

By installing Virtual Box, would I be opening any ports (like SSH) and leaving my beloved Ubuntu open to hackers? 

Last question (I promise!) - knowing what windows is like, if I were to get a virus on the windows virtual drive, would just deleting the windows virtual drive eradicate the virus and all the data on the virutal drive, or would the virus be on the hard drive and I would need to reinstall Ubuntu?

Thanks for your help! :)
Stormsy.

---

### Post by ki4jgt on 2010-11-09
Yes, if you got a virus then deleting the Virtual disk will delete the virus. Also, Virtual box is more like a network if you will or adhoc between two computers. The host computer which provides network access to the guest OS is just a networked computer to the guest OS, in this way, any viruses you get on windows, unless you give specific access to the virtual system to share files and other things, stays on windows.

---

### Post by ki4jgt on 2010-11-09
But it does present the same hazards as normal computer networking.

---

### Post by timgood on 2010-11-09
It would be best (in my opinion) to install VirtualBox from [here]("http://www.virtualbox.org/wiki/Linux_Downloads") as you will get the most up-to-date and Meerkat friendly version. VirtualBox is an emulator, so you can install multiple OS's on the Linux version, including Windows, other Linux Distro's  etc. You will need a Windows installation disk or .iso image to install the OS, and then you can run it from within Linux. It will not use any ports on your machine other than the ones used already by Ubuntu, so it is quite safe to use. Some purists might suggest that you install the OSE (Open Source Edition) available in the repos, but I have always had more success with the non-ose version. There is lots of help available online, so check out the download page above.

Hope this helps.

---

### Post by CharlesA on 2010-11-09
Virtualization and emulation are two different things, however, the VM software "emulates" physical hardware, so I suppose that's partially correct.

Anyway, to install Windows inside VirtualBox, you need only install VirtualBox (see above) and then install Windows inside the VM.

---

### Post by Stormsy on 2010-11-09
Hi all,

Thanks for the quick replies!! :D

So, to condenstate what has been posted - 
1.) Use the non-OSE version the Virtual Box;
2.) There is no specific version of Virtual Box to use.  Since I'm using Linux it would not matter if I wanted to install Windows (that can be phrased better...)
3.) All I'm doing is installing Windows onto a "clean" hard drive and so there won't be any access between the Host and Guest OS files and so no viruses will be transmitted.
4.) Since the drive is "virtual" any data (or virsues) on the drive can be deleted permanently without affecting the Host OS.

That really helps everyone - thanks for the Link timgood, I will download the 10.10 version.
Thanks!
Stormsy.

---

### Post by timgood on 2010-11-09
> **CharlesA said:**
> Virtualization and emulation are two different things, however, the VM software "emulates" physical hardware, so I suppose that's partially correct.

Cheers Charles - I was perhaps oversimplifying, thanks for pointing out the (obvious) differences between the two.

Have Fun!

---

### Post by Verbeck on 2010-11-09
if you have your /home shared with the guest os with write permissions, then you might loose data because of malicious programs

---

### Post by coldraven on 2010-11-09
I agree with timgood, I always get the latest version direct from VirtualBox. They have .deb files for most Linux distros.

You might like to read my tip here and save some head scratching :)
[http://ubuntuforums.org/showthread.php?t=1604549](http://ubuntuforums.org/showthread.php?t=1604549)

I only know regarding Windows XP but if you only have a pre-installed version (SLP) you might have difficulties.
 Read [http://en.wikipedia.org/wiki/System_Locked_Preinstallation](http://en.wikipedia.org/wiki/System_Locked_Preinstallation)
Sorry I cannot find the link but the answer is on the VBox forum. Search for dmidecode.
If you have a disk with a serial number it is easy to create a Windows VM.

And regarding malware, if you are paranoid :)
[http://www.woodmann.com/forum/showthread.php?13168-Tips-for-thwarting-VM-detection](http://www.woodmann.com/forum/showthread.php?13168-Tips-for-thwarting-VM-detection)

---

### Post by Dr. C on 2010-11-09
I use the OSE edition of VitualBox from the repositories. The only reason to use the PUEL edition is if one needs any of the closed source features such as USB support. There is a comparison between the OSE and PUEL editions [here]("http://www.virtualbox.org/wiki/Editions") 

Once virtual box is installed install Microsoft Windows in the VM. One important consideration is to delay activating Windows until all the VM hardware settings are finalized and the guest additions are installed. 

The Windows VM does not have access to the GNU / Linux host unless permission is given to access directory through a share or the VirtualBox shared folders. The Windows VM, is a full Windows installation so the normal security considerations of running Microsoft Windows apply.

---

### Post by Stormsy on 2010-11-10
Right - I have installed VirtualBox (I downloaded the .run file from their website and placed it into my /home directory and installed it from there.)

I've set up my virtual drives, but when I go into full screen mode, I get a black border around the window - how can I get rid of this so that when I go into Full screen mode I just get a full screen of the guest OS?

Thanks,
Stormsy.

---

### Post by Verbeck on 2010-11-10
have you got the guest additions installed?

---

### Post by Stormsy on 2010-11-10
> **Verbeck said:**
> have you got the guest additions installed?

:confused: I assumed that they were with the .run file I downloaded from the VirtualBox website...

Where can i download them from?

---

### Post by CharlesA on 2010-11-10
> **Stormsy said:**
> :confused: I assumed that they were with the .run file I downloaded from the VirtualBox website...

Where can i download them from?

They would have been included in the install. If you have the VM open, go to Devices > Install Guest addons.

---

### Post by SeijiSensei on 2010-11-10
> **Stormsy said:**
> 4.) Since the drive is "virtual" any data (or virsues) on the drive can be deleted permanently without affecting the Host OS.

When you have the VM configured the way you want (and the copy of Windows has been activated), use the "[snapshot]("http://en.onsoftware.com/how-to-create-and-manage-snapshots-in-virtualbox/")" feature of VirtualBox to make a backup of the initial machine state.  That way, if you somehow corrupt the installation or it gets infected by malware, you can just delete the corrupted version and use the snapshot to start over.

---

