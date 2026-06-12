---
title: "Ubuntu Won't Boot"
date: 2010-12-31
forum: Server Platforms
---

### Post by Captainnow on 2010-12-31
Here is the deal. 

I have a computer that will install and boot windows xp pro with no issues at all. I install ubuntu linux and it won't both. No errors nothing. It will just finish loading the bios and go to a black blank line. No C:\ prompt, no error. Nothing. Pressing enter doesn't do anything. 

I have even tried installing different versions of Ubuntu Server, 10.10, 10.04, even tried debian linux nothing will work, but it will install and run windows xp pro without a single problem.

A bit of backgroud. This computer before this did install and run Ubuntu 10.10 without a problem. Then something happened and the OS crashed. So I tried to reinstall it. This is when this problem started. And since this I have installed windows xp pro without problem. So hardware is working. If it wasn't windows shouldn't work. So what would allow Windowx XP Pro to work without problem, but also make it so linux won't boot and give no error?

No new hardware has been added or removed.

---

### Post by drs305 on 2010-12-31
I can't tell if your latest installation is a server edition or not, and whether you still have an Ubuntu installed but not working. 

For a normal installation, if you have a blinking cursor it could be a video problem. Try holding the SHIFT key during boot and see if the Grub2 menu appears.

If it does, highlight the first entry and press "e". Use your cursor buttons to move to the end of the "linux" line. Remove "quiet splash" and add "nomodeset". Press CTRL-x to boot. 

If it boots to the Ubuntu Desktop, go to System, Administration, Additional Hardware and install the video driver that is hopefully displayed.

---

### Post by Captainnow on 2010-12-31
It isn't a video problem. If I install windows, windows will install, and load all the way to the desktop and I can use windows no problem

When I install Ubuntu Server 10.10 it will go through the entire install successfully. It reboots. I see the bios splash screen. It goes through post test. It will stop at the last line of that. I will see all that still on the screen and it won't go no farther. 

Enter doesn't add lines. There is no error on the screen. It just doesn't do anything at all, but you are able to see text on the screen. 

Windows loads and works fine. Ubuntu will not boot after it installs.

I did try your suggestion about hold the shift key during boot. No change. It just sits there after the bios has finished. No error or anything. I currently have Ubuntu Server 10.04 installed.

---

### Post by James78 on 2011-01-01
> **Captainnow said:**
> It isn't a video problem. If I install windows, windows will install, and load all the way to the desktop and I can use windows no problem
Actually it could still be a video problem. Linux video drivers aren't Windows drivers, and thus are coded differently and work differently, and have different compatibility with different combinations of hardware and software.

Either way though, in this case, it's probably related to booting, and not video related. Are you using software RAID for Ubuntu?

---

### Post by Captainnow on 2011-01-01
> **James78 said:**
> Actually it could still be a video problem. Linux video drivers aren't Windows drivers, and thus are coded differently and work differently, and have different compatibility with different combinations of hardware and software.

Either way though, in this case, it's probably related to booting, and not video related. Are you using software RAID for Ubuntu?

No I have 3 hard drives in the computer. The computer is just a simple home server. Nothing high end. It has 3 sata drives. A 250 GB, and two 500 GBs. They aren't in any raid hardware or software. I'm installing the OS to the 250 GB. 

The most annoying part of this issue is I did have ubuntu server 10.10 working on this computer. Then something happen to when I rebooted the machine permissions were all screwed up and it couldn't boot no more. It would give permission denied errors all the way through bootup and wouldn't ever get to a log on screen. So I reformated and reinstalled the OS. Since then I can't get it to boot up to use it. I haven't changed any hardware in the system.

---

### Post by James78 on 2011-01-01
Hmm, you could try zero'ing out your drive first, then installing. Sometimes multiple installations mess something up for me for when I re-install, and it just doesn't work like it should. It could fix something, or nothing, but it's worth a try if the drive you're using for your installation is dedicated to Linux (you don't want to overwrite any other partitions or OS's on the same drive now!)

Make sure you have the proper drive letter (sda, sdb, etc) BEFORE continuing; you don't want to overwrite the wrong drive on accident.
```
dd if=/dev/zero of=/dev/sda
```

It will take a very long time to finish, maybe ~8-10 hours, maybe longer or shorter.

---

### Post by Captainnow on 2011-01-01
> **James78 said:**
> Hmm, you could try zero'ing out your drive first, then installing. Sometimes multiple installations mess something up for me for when I re-install, and it just doesn't work like it should. It could fix something, or nothing, but it's worth a try if the drive you're using for your installation is dedicated to Linux (you don't want to overwrite any other partitions or OS's on the same drive now!)

Make sure you have the proper drive letter (sda, sdb, etc) BEFORE continuing; you don't want to overwrite the wrong drive on accident.
```
dd if=/dev/zero of=/dev/sda
```

It will take a very long time to finish, maybe ~8-10 hours, maybe longer or shorter.

Ok I could try that, but how would you recommend I do that when I can't get to a command prompt to type anything. I can boot CDs, and install windows xp pro without a problem. I have also had the windows xp CD do a full format. I have nothing on any drive to worry about losing.

---

### Post by James78 on 2011-01-01
Boot to rescue mode on your server install CD, then go to a root shell prompt.

---

### Post by Captainnow on 2011-01-02
So far still no change on the system. It will not load linux.

I have attached a pic of what the screen looks like when the computer finally stops loading. Everything on the screen is from the bios. You will see all that even if I have windows XP installed. It listed the two Boot from CD lines since there are two CD Roms installed.

After this screen is when you would see the windows splash come up as it first starts to load windows (if windows was installed).

Currently Ubuntu Server 10.04 is installed and isn't loading. As you can see after the last boot cd line there is nothing. Just a blinking _ that won't move if you press enter, and doesn't allow you to type anything. 

This is a dedicated linux machine. No other OSs are installed except Ubuntu Server 10.04. 

I'm hoping the pic will help get this solved. I would like to get this back running linux again.

Thanks for all the help.

---

### Post by James78 on 2011-01-02
Hmm, it looks like it might be trying to boot from the CD. Is the CD still in the drive?

If that's not the case, I would have no idea, because if it's a grub issue, usually the whole screen goes black and displays some type of text (or blinking cursor). That screenshot might help whoever else identify the problem though.

---

### Post by drs305 on 2011-01-02
I don't know what the specific issue is but doing a search of the last message you get before the system stops booting revealed some possible clues. Here are a just a couple of results (verifying DMI pool data):
[http://www.computerhope.com/issues/ch000474.htm]("http://www.computerhope.com/issues/ch000474.htm")

[http://www.techsupportforum.com/hardware-support/motherboards-bios-cpu/150171-resolved-verifying-dmi-pool-data-bios.html](http://www.techsupportforum.com/hardware-support/motherboards-bios-cpu/150171-resolved-verifying-dmi-pool-data-bios.html)

---

### Post by Captainnow on 2011-01-02
> **James78 said:**
> Hmm, it looks like it might be trying to boot from the CD. Is the CD still in the drive?

If that's not the case, I would have no idea, because if it's a grub issue, usually the whole screen goes black and displays some type of text (or blinking cursor). That screenshot might help whoever else identify the problem though.

There is no CD in either drive. If I have a CD in the computer detects it just fine and loads the CD. If I put my Windows XP Pro CD in it will load the setup and complete successfully. I remove the CD. It will reboot to where you see it. Stop there for a quick moment. It will show the two Boot from CD lines just like it does in the screenshot and then start loading windows.

If I put the Ubuntu CD in it will load the CD, and I can run through the setup. It will also complete successfully. I remove the CD and reboot. It then reboots and stops right where you see it in the screenshot. 

So in short. All CDs load successfully. Both windows and linux will both say they install successfully. Only Windows will boot when installed. Linux doesn't load. 

I'm so confused on this. I do appreciate the help from these forums. I hope a solution can be found. Thanks.

---

### Post by Captainnow on 2011-01-02
> **drs305 said:**
> I don't know what the specific issue is but doing a search of the last message you get before the system stops booting revealed some possible clues. Here are a just a couple of results (verifying DMI pool data):
[http://www.computerhope.com/issues/ch000474.htm]("http://www.computerhope.com/issues/ch000474.htm")

[http://www.techsupportforum.com/hardware-support/motherboards-bios-cpu/150171-resolved-verifying-dmi-pool-data-bios.html](http://www.techsupportforum.com/hardware-support/motherboards-bios-cpu/150171-resolved-verifying-dmi-pool-data-bios.html)

The computer will always display "verifying DMI pool data" then list the two boot from CD lines when it loads windows. 
It also when Ubuntu Server did work on this machine it would also list that. 
I've doubled checked all settings in the BIOS and so far I haven't been able to find anything that is incorrect. I have even loaded default bios settings. No change.

---

### Post by oldfred on 2011-01-02
Is this an older BIOS that only supports IDE drives? You may then only be able to boot primary master drive. 

Older computers let you choose floppy or hard drive and hard drive had to be jumpered to be primary master. They then added CDs and other devices and most newer computers that support SATA drives also let you choose which hard drive is the  boot drive in BIOS rather than with jumpers (or cable select) on hard drive.

If you can only boot primary master and can boot windows then you do not have grub installed to the primary master. If you have newer BIOS you should be able to change drive boot order to drive with grub installed.

If you have server install, it is not liveCD. Download liveCD and run this:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by Captainnow on 2011-01-02
> **oldfred said:**
> Is this an older BIOS that only supports IDE drives? You may then only be able to boot primary master drive. 

Older computers let you choose floppy or hard drive and hard drive had to be jumpered to be primary master. They then added CDs and other devices and most newer computers that support SATA drives also let you choose which hard drive is the  boot drive in BIOS rather than with jumpers (or cable select) on hard drive.

If you can only boot primary master and can boot windows then you do not have grub installed to the primary master. If you have newer BIOS you should be able to change drive boot order to drive with grub installed.

If you have server install, it is not liveCD. Download liveCD and run this:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

I will double check and make sure the correct drive is listed for the first hard drive to boot. I'm pretty sure it is, but I will double check that.

Just to make sure this is clear. Windows isn't currently installed. I just have Ubuntu Server 10.04 installed right now. When I have installed windows it as as a sole windows machine and it does work as a sole windows machine. 

I know at the end of the server install it installs Grub.

---

### Post by oldfred on 2011-01-02
Grub likes to install to sda, but if you are booting from another drive then the system will halt after not being able to boot from the CD. Did you choose which drive to install grub to and then in BIOS make that the default boot drive?

---

### Post by Captainnow on 2011-01-03
> **oldfred said:**
> Grub likes to install to sda, but if you are booting from another drive then the system will halt after not being able to boot from the CD. Did you choose which drive to install grub to and then in BIOS make that the default boot drive?

Thanks to this information this allowed me to solve the problem. Here is what happened. 

I have 3 hard drives installed.
One 500 GB comes up as /dev/sda
The 250 GB comes up as /dev/sdb
Other 500 GB comes up as /dev/sdc

Now I'm not sure why the 250 GB is on /dev/sdb when it is plugged in to the number 1 sata port on the motherboard.

I'm installing the OS to the 250 GB (/dev/sdb) and the at the end of the installation it installs grub but it doesn't ask or say which drive it is installing grub too. 
So I just unhooked the 500 GBs drives. Installed the OS without those drives being detected. 
The Ubuntu server now boots. It would appear that Grub was going on /dev/sda and since I put the OS on /dev/sdb it wasn't able to find it to load the operating system.

Is there anyway to change what drive is assigned /dev/sda, /dev/sdb/, and /dev/sdc?

---

### Post by oldfred on 2011-01-03
On my system I have the drives in connectors 1,3, & 5 and they are in that order. Note that even then the boot drive in grub is always hd0 as my USB flash drive is still hd0 when it is seen as sdf. Note sure why it skips sde & sdd?

But I have seen others with drives not in port order. And those with mixed IDE & SATA will sometimes very by boot. May have to do with when drive wakes/powers up and BIOS first finds it.

---

### Post by Captainnow on 2011-01-03
Ok. I will check the boot order on them. At least now though the system boots and is working. 

Thank you all for all your help.

---

