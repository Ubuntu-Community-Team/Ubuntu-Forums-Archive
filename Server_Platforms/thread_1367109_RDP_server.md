---
title: "RDP server?"
date: 2009-12-29
forum: Server Platforms
---

### Post by pcal on 2009-12-29
Hi folks,

I have 2 diskless thin client machines with win ce in firmware that I would like to retask as remote desktops on an ubuntu machine.

The firmware is looking for a win terminal services server to connect to via rdp, possibly with citrix as well.

Is there an option somewhere out there on the multiverse for me to add a server function in an ubuntu desktop to allow connections from these win ce thin clients? I guess I could build a specific machine to act as a server if necessary, but it would be far better if I could just hang them off an existing desktop. All I am really looking for is a cheap option to provide net access in a couple of bedrooms, so 90% of my requirement is just browser access...

Any clues welcome!

Regards,

pcal

---

### Post by CharlesA on 2009-12-29
I do not believe you can use remote desktop (RDP) with Ubuntu. However you can use VNC, but I am not sure how it would work with 2 or more users.

---

### Post by Lars Noodén on 2009-12-29
> **CharlesA said:**
> I **do not believe**...

If you can forgive me for poking fun at faith-based computing long enough for us to look together at the description for [krdc](http://docs.kde.org/stable/en/kdenetwork/krdc/), we can see that RDP is in fact supported.  It may not be a very good protocol, it may not be a secure protocol, but it is supported.  ;)  krdc is part of the regular [kubuntu-desktop](apt://kubuntu-desktop/) package.  

Unfortunately, there does not seem to be any corresponding documentation for the matching server, krfb.  So, for the server, it is sure that the [xrdp](apt://xrdp/) package supports RDP.  

@pcal : If the Wince clients can handle VNC, then CharleA's suggestion of using VNC will give you a lot of options including krfb and tightvncserver.

---

### Post by Lars Noodén on 2009-12-29
What brand and model are the thin clients?  It might be quite possible to put an embedded linux distro on them either as a thin-client station or as a dedicated web browser kiosk.

*Edit: retroactively +1 for @ lykwydchykyn 's suggestion below to try LTSP if the units can do pxe boot*

---

### Post by CharlesA on 2009-12-29
Ah KDE, that explains why I didn't see anything for Gnome.

---

### Post by lykwydchykyn on 2009-12-29
Do they have PXE boot capability?  I'd be surprised if they didn't.

I was in a similar situation a few years ago, and found that booting via PXE to an LTSP server gave by far the most satisfying performance and user experience.

If you want to go with rdp, xrdp should do it.

---

### Post by spikyjt on 2009-12-29
I can also recommend LTSP. Use the PXE (network) boot function which, as the previous poster says, your thin clients will almost certainly have. LTSP is very easy to setup and maintain and very efficient. I have network running 27 thin clients on one server.

---

### Post by pcal on 2009-12-30
:) Thanks guys for some useful suggestions!

The bios doesn't seem to provide the ability to intervene before loading the Win CE image - at least, none of the usual key combinations I can think of provide access to a bios screen.

Once loaded, there is a menu of hardware choices designed to locate and connect to the RDP server, but I've not found any option that relates to any form of network boot. Again, I can't say it's not there, but just that I haven't been able to find it if it is.

The machines themselves are Axus Microsystems - WinClient TC-300N series version 1.1f6, and the firmware contains Win CE v2.11

Yes, they are old! :) I got them at auction, and while they doubtless spent many moons on someone's spare parts shelf, they came to me unused - still in original packaging with all accessories and manuals. (The manual by the way, is little more than a step through for connecting to RDP)

The thought of replacing the firmware is even more tempting than running them off another machine. I have attempted to get them to boot a v9.10 netbook remix on a usb memory stick without success. Couldn't find any boot option other than default... (the usb image works fine on other machines) So, if there is a replacement bios I can buy somewhere (assuming I need a new chip, as flashing an upgrade seems unlikely), I'd love to hear about it.

In the mean time, I'll explore LTSP in the hope someone can point out where I've missed a PXE boot option.

Regards, and thanks for suggestions to date...

Pcal

---

### Post by lykwydchykyn on 2009-12-30
Can't say for that model, but one model of thin client I worked with had no BIOS screen, but it tried to boot PXE by default.  If it failed, it went on into Windows CE.

---

### Post by pcal on 2009-12-31
Hi again folks...

Found [this link]("ftp://ftp.atcomp.cz/terminaly/axus/Firmware%20Upgrade%20Procedure.PDF"), which seems to offer hope that the thin clients may be flash upgradable after all.

Is there a distro (preferably ubuntu) that would be small enough to fit, or alternately a boot loader that could be flashed into these machines to allow loading an os from usb?

Sorry to be asking so many questions, but this is a little above my pay scale in terms of technicalities...

Thanks in anticipation,

Pcal

---

### Post by Lars Noodén on 2009-12-31
> **pcal said:**
> Hi again folks...
Found [this link]("ftp://ftp.atcomp.cz/terminaly/axus/Firmware%20Upgrade%20Procedure.PDF"), which seems to offer hope that the thin clients may be flash upgradable after all.


```

220 Microsoft FTP Service
...
550 Firmware%20Upgrade%20Procedure.PDF: The system cannot find the file specified. 

```

The link and the server seem broken.  Even when logging in and rummaging for the file, it can be found but not read.  Kind of makes one wonder if anyone has ever, ever, ever actually tried to **used** Microsoft software instead of just re-selling or doing hit-and-run installs before seeking new employment.  

Looking at the Axus website....oh my...requires enough discression to stop writing or thinking about it now...

The documents may not have enough info to safely or conveniently work on replacing the firmware.  

> **pcal said:**
> Hi again folks...
Is there a distro (preferably ubuntu) that would be small enough to fit, or alternately a boot loader that could be flashed into these machines to allow loading an os from usb?


It sounded earlier like the BIOS on those units don't support usb booting.  Older systems often don't.  If they do support PXE booting, then that will probably figure into the solution.  

I'd bet there isn't space for a proper distro, even one like [Puppy Linux](http://puppylinux.org/).  

The way it is often done with embedded devices and linux is to use BusyBox.  You've probably seen the name flash by when installing Ubuntu.  It's the same tool.  You take a program and then busybox wraps enough around it that it can run in a ram disk.  Then the ramdisk gets booted and everything runs from that.  Works great for other appliances, like ADSL modems, too.

BusyBox is part of Ubuntu and you can find the LTSP client pieces you want and try wrapping them.  I would suggest using a spare machine, one that you are already familiar, for testing booting with that over pxe served from your normal computer.  Once you have it booting fine, then try porting over to the thin client machines.  The reason for that is it will take many tries and you can do more tries per hour with the regular machine.  A second reason is that the number of new things or changes to be made at the same time and you have several new things: pxe boot, busybox, ltsp, diskless clients.  Break the task into little pieces first.

One possible sequence, out of many choices:

1) on a spare machine get a ltsp client going
2) on that spare roll your own busybox image with the above client
3) figure out how to get that image onto the diskless machines

Did you get it to pxe boot?  You can use dnsmasq and the netboot tarball to test it:

[http://archive.ubuntu.com/ubuntu/dists/karmic/main/installer-i386/current/images/netboot/netboot.tar.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/main/installer-i386/current/images/netboot/netboot.tar.gz)

[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

It won't install but if you see the installation startup screen you know pxe boot works.

---

### Post by vmemmanuel on 2010-02-07
Hi,
I do have diskeless thin clients and they work fine with ubuntu 9.10.
But there are things to do before you network them using XRDP.
These are the steps I followed:-
PART-I. Updating and Installing Components.
1. sudo apt-get update ( give the su password, same as the one used while installing ubuntu)(Time taken - < 1 min)
2. sudo apt-get upgrade (Time taken 3 to 4 hours depending on internet connection speed, for the first time. Later it will take only minutes)
3. RESTART COMPUTER
4. sudo apt-get install build-essential
5. sudo apt-get install libpam0g-dev
6. sudo apt-get install libssl-dev
7. sudo apt-get install tightvncserver
Part - II
Download  the xrdp-0.4.1.tar.gz file.(Pl mail me if you need this)
1. cd ~/Desktop (Note the Tilde before /. It is not a hyphen)
2. tar xvzf xrdp-0.4.1.tar.gz
3. cd xrdp-0.4.1
4. make
5. sudo make install
Part - III
1. On terminal type the command gconf-editor
2. Go to apps -> gnome_settings_daemon -> plugins -> keyboard
3. under Name = Active, Untick the value check box.(Disable). 
   close Conf-editor window.
4. Goto system -> Administration -> Users and Groups
5. Unlock - give password - add new user - allot password 
6. logout. login as new user and do step 1,2,3 of Part III to new user, or any number of users you may later add. 
Part - IV
1. Logout and login as the user who installed ubuntu.
2. Start xrdp by the command  sudo /usr/local/xrdp/xrdp_control.sh start
Part - V
1. Right click the network icon on right of top menu bar.
2. Click Edit Connection.
3. Select Auto eth1 (or eth0 if you have only one nic card) . Click Edit. select IPV4 settings. put method to manual. click add. input Address as 192.168.1.1, Netmask as 255.255.255.0, DNS as 0.0.0.0. ensure "connect automatically" and "available to all users" are enabled. Click Apply.
4. Close network connections window.
Part VI
1. Connect the thin client and switch it on.
2.Select Set a Static IP address. 
Or connect 192.168.1.1
Or
Local IP - 192.168.1.2
Gateway  - 192.1.1.1 ( Same as Host)
Sub Mask - 255.255.255.0
Input IP - 192.168.1.1 (Same as Host)
Type the user name.
Type the user password.
Restart the thin Client and you should LOG in to Linux. Enjoy the experience.

If you want to browse the internet you will need two NICs. I dont know what type of Diskless clients you use but this worked for me in my mine which are also win ce machines. They work very well.
If you need to buy a Thin Client please visit [www.neosisone.com]("http://www.neosisone.com").
You may contact me at [EMAIL="vmemmanuel@hotmail.com"]vmemmanuel@hotmail.com[/EMAIL]
Regards and best of luck.
Emmanuel

---

### Post by pcal on 2010-02-08
WOW. Thanks for such a detailed blow by blow description!

Real life has temporarily intervened in the project, but as soon as I can get back to it I will post results here...

Thanks again,

Pcal

---

