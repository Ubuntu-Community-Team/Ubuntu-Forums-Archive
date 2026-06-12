---
title: "ubuntu Software Center wiped out system, can't boot."
date: 2013-09-28
forum: System76 Support
---

### Post by rpjohns on 2013-09-28
Just got a new system 76 desktop with ubuntu 13.04. I had tried to install Teamviewer on it but the install failed. I then went into Software Center which informed me that I could not do anything till the failed package stuff was  resolved and asked if I wanted to resolve it now. I said yes. The next thing I know all the software was removed from the system. 

I then tried rebooting and now the machine will not boot. It just churns away on the splash screen where U B U N T U letters flash in sequence. So I'm screwed. To make matters worse the box doesn't have a cd drive -- I got this machine for my mother and was just setting up a simple system for browsing the internet and reading email.

So what can I do? Install from flash drive via USB? If so, how to get an install image on a flash drive? How to get the machine to boot from a flash drive?

---

### Post by SuperFreak on 2013-09-28
This link may get you started
[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu")
You will have to do this on a separate machine from the affected 76 PC.
Once you have made your USB up go into the BIOS on the 76 machine and change BIOS Boot order so USB is the first item to boot. Then start up the 76 PC with the USB stick and follow the instructions for install

see next post for making ISO in Windows

Pressing F2 when you start the machine but before Ubuntu starts may get you to BIOS screen

---

### Post by SuperFreak on 2013-09-28
Sorry the instructions I gave are for making USB Iso in Ubuntu. Here are the directions for a Windows machine
[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows")

---

### Post by rpjohns on 2013-09-28
Thanks for the reply. I have a laptop running ubuntu 12.04 and I am currently downloading the iso for ubuntu 13.04. I am sorley tempted to download the iso for 12.04 and use that but I've already started the 13.04 download. At any rate, on the system 76 box I get into the bios and there doesn't seem to be a way to specify the boot order. I just have choices like 'fast boot' with a few sub choices, one of which is usb, but all I can change about the usb is whether it 'partial' or 'full' or 'never' wrt to the POST. I assume that means booting? So I was going to change it to 'full' which seems to indicate that the usbs are available all the time during startup as opposed to only after the OS boots. I'm guessing here. 

The other question I have is which usb port to use? There are usb 3.0 and 2.0 and about 4 of each. I guess I'll try 3.0 first since it's presumably faster. Not sure if a specific usb port would be designated as the one to read during boot sequence. I'm hoping that whichever is holding the flash drive is the one it will read.

Thanks again. The iso download is taking some time and the download feedback says about an hour. I have a 10.04 iso handy already I used in a VM. Could that work? I'm worried about it having the drivers needed for the 'very' new hardware.

Thanks again, I really appreciate the help here. I'm obviously got a lot to learn.

---

### Post by SuperFreak on 2013-09-28
I have USB 3 ports on my computer as well as USB 2 but I know with my PC the computer will not boot to USB 3 ports only 2. I don't own a system 76 computer though so yours may differ.
Ubuntu 10.04 is no longer supported and will not receive any updates so I recommend against that.

---

### Post by SuperFreak on 2013-09-28
This may help you set the boot order
[http://knowledge76.com/index.php/Restoring_Your_System]("http://knowledge76.com/index.php/Restoring_Your_System")

---

### Post by rpjohns on 2013-09-29
Ok Solved this thing with help from super freak -- thanks!  

So by 'Solved' I mean I got myself into a fix and got out of it, but there still seems like a bug somewhere.

Heres's how it happended:

- I bought a system76 ratel desktop with ubuntu 13.04. (nice machine and a solid outfit)
- I wanted to install TeamViewer, the installation failed due to some missing 32 bit libs.
- I now have a failed package lodged in the works
- I go into the Software Center and the app tells me I have an unresolved install and I will need to resolve before I can install|remove any software and asks 'resolve now?'
==> this is the place I should have done a little research before leaping....but, I just wanted to get down the road and got careless/lazy and said yes, just wanting the problem to go away.
- Software Center apparently resolved it by undoing the teamviewer install wreckage, but also aggressively (and savagely)  removed the  ubuntu13.04 installation. Nice.
- Everything disappears and I'm praying a reboot will restore everything some how.... but, it would not boot. 
- after wallowing in disbelief and a brief stint of victimhood, I decide to fix it.
- I go to my ubuntu 12.04 laptop and down load the iso for ubuntu 13.04, and use the 'create startup disk' tool to create an install image on a usb flash drive.
- now, to get the system76 box to look in the flash drive for the boot image I need to change bios
- I put the flash drive in a usb 2.0 in the back of ratel and reststart and hit F2 to get into BIOS
- In the BIOS utilty program I navigate to the 'Boot' tab. After some head scratching and a fair bit of trial and error I learn that I have to change 'fast boot' to 'normal boot' which reveals a choice where you can choose the usb  for first attention in the boot sequence. It's not obvious -- from memory, it's the last choice on that menu and you'll change from the disk to the usb. Note too, the usb flash drive needs to be in.
- then I save and exit from BIOS utility and the system76 sees the install image in the usb and I install ubuntu 13.04. Easy at this point.
- I then rebooted, got back into the BIOS utility and changed the boot properties back to 'fast boot' and choosing the disk as frst boot device.

Happy ending, although, it sucks that the Software Center lured me down this pathologic path. My fault for not being smarter, but nonetheless, the ubuntu guys aught to look for a possible bug, or at least take the sharp edges off that baby. I'm used to Synaptic Package Manager I guess, but I got burned.

---

### Post by SuperFreak on 2013-09-29
Good news

you can mark the thread as SOLVED by going to your first post>Edit>Advanced> change prefix from OTHER  at title to SOLVED

---

### Post by GeneSalamin on 2013-09-29
I noticed that TeamViewer is not listed in Ubuntu Software Center.  It's risky to install software from an untrustworthy source.  It corrupted your system.

---

### Post by houstonbofh on 2013-10-01
> **SuperFreak said:**
> Ubuntu 10.04 is no longer supported and will not receive any updates so I recommend against that.
This is incorrect.  The "Desktop" distribution is not supported, but "Server" is.  And since they use the same repositories, you will still get updates.  I just updated a kernel to 2.6.32-52 right now.

---

### Post by SuperFreak on 2013-10-01
This was published last May [HERE]("http://fridge.ubuntu.com/2013/05/10/ubuntu-10-04-lucid-lynx-desktop-end-of-life-reached-on-may-9-2013/")
> Ubuntu announced its 10.04 (Lucid Lynx) release almost 3 years ago,
on April 29, 2010. As with the earlier LTS releases, Ubuntu committed
to ongoing security and critical fixes for a period of 3 years on the
desktop. The support period is now nearing its end and Ubuntu 10.04
Desktop will reach end of life on Thursday, May 9th. At that time,
Ubuntu Security Notices will no longer include information or updated
packages for Ubuntu 10.04 Desktop. Ubuntu 10.04 Server continues to
be supported for another 2 years.

Prudence dictates having an install with appropriate security updates

---

### Post by houstonbofh on 2013-10-03
> **SuperFreak said:**
> This was published last May [HERE]("http://fridge.ubuntu.com/2013/05/10/ubuntu-10-04-lucid-lynx-desktop-end-of-life-reached-on-may-9-2013/")


Prudence dictates having an install with appropriate security updates

And observation shows that I am getting them, even after May 9th.  I do not know if they actually dropped anything.  After all, what is a server, and what is a desktop?  I can install ubuntu-desktop on a server install...

The point is that the repositories are still up (unlike 10.10) and I can still receive updates and install new software.

---

### Post by isantop on 2013-10-03
The desktop related packages (dependencies of the ubuntu-desktop metapackage) won't receive any more updates. These include things like gksudo and policykit, where you *really* don't want a security bug.

I'd definitely recommend being on 12.04 at the earliest. 13.04 (or 13.10 later this month) would be your best bet.

---

### Post by houstonbofh on 2013-10-03
> **isantop said:**
> The desktop related packages (dependencies of the ubuntu-desktop metapackage) won't receive any more updates. These include things like gksudo and policykit, where you *really* don't want a security bug.
Good catch. :)  However, I went and looked and the latest version of gksu was quite a while before support ended.  There is a later version for Precise and one, but it is also Gnome 3 while Lucid is Gnome 2...  So it could be that there is no more recient version that works on Gnome 2.  Not worried enough to check.  I am slowly migrating the last of my 10.04 systems to 12.04, so it will be a non-issue soon enough.

But you are correct in that some things are no longer being patched.  And I still can't figure out how they decided what was "server" and what was not.  It seems somewhat random.

> **isantop said:**
> I'd definitely recommend being on 12.04 at the earliest. 13.04 (or 13.10 later this month) would be your best bet.

I think we can agree that we will never agree on the merits of LTS vs current. :)  But I do recommend 12.04 over 10.04 as soon as convenient.  But I do not consider that upgrade critical yet.

---

### Post by isantop on 2013-10-03
The server question is simple. Ubuntu Server is a standard Ubuntu image minus the ubuntu-desktop bits. Ubuntu desktop is the Ubuntu Server image plus ubuntu-desktop.

---

### Post by houstonbofh on 2013-10-16
Actually, ubuntu-server defaults to a different kernel in some versions.  And there are some GUI tools that are still being updated...  Tools which depend on gnome.  It would have thought they would have dumped everything gtk, but they did not.

---

### Post by Ubun2to on 2013-10-17
> **GeneSalamin said:**
> I noticed that TeamViewer is not listed in Ubuntu Software Center.  It's risky to install software from an untrustworthy source.  It corrupted your system.
Teamviewer is actually a really good service. I use it because I am too lazy to walk upstairs and downstairs between computers.
I dislike them, however, as they dropped the ability to allow unattended access in version 8, which means the primary reason for me using it has been removed on Linux.

---

