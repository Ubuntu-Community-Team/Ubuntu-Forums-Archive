---
title: "No USB Devices in VBox After System Updates (Tried ALL The Usual Suspects!) in 16.04"
date: 2018-07-11
forum: Virtualisation
---

### Post by OzzyFrank on 2018-07-11
Hi. I have had all sorts of fun & games over the years with either getting VirtualBox to work again after an Ubuntu system update, or re-enabling USB support to use my printer in WinXP, but this time - after HOURS of Googling - I admit defeat. In short, before proceeding with the system update, I allowed it to remove a bunch of old kernels and related packages (this was the only difference with the other times), and all was fine, and my VMs loaded, but the printer - or any USB device - was no longer recognised. As I've said, I've been through all this before, and tried all the usual things (will list in detail below), including installing the latest version via Oracle's download page (which often does the trick), and of course the appropriate Extension Pack, DKMS, virtualbox-guest-dkms, adding my user to **vboxusers**, making sure all packages installed are the same version, etc... then even doing something I've never had to so, which is purge it, and install the officially-supported one from the Ubuntu repos... but NOTHING is getting VirtualBox to recognise ANY USB device.

Now, I can rule out some obvious things, as the printer worked absolutely fine in WinXP minutes before the system update, and works fine now in Ubuntu (so it's not the connection or cable or printer). It is not a driver issue in WinXP, as it worked fine minutes before, and no USB devices are recognised in any other VM. In **Settings > USB**, the controller is enabled, filters are all there, and when trying to create a new filter there is only **<no devices available>**. So, USB and printer are fine in the Ubuntu host, but not in any guest. I'll try to remember everything I've tried today, and list below (including troubleshooting commands and their output) - and you can also rule out that I didn't reboot when I should have, as I rebooted pretty much after trying everything!

[note: "Oracle VBox" will mean the one downloaded from their page, and "Ubuntu VBox" will refer to the one from Ubuntu's repos]:

* After the updates, and checking USB as outlined above, it was apparent Oracle VBox (not sure which version, but from earlier this year) had been replaced by Ubuntu VBox 5.1.34, so tried to upgrade to latest Oracle VBox 5.2.14 r123301 (Qt5.6.1) via downloaded .deb, but could not proceed due to ***"Error: Breaks existing package 'virtualbox' that conflict: 'virtualbox'.***.." - so did a **sudo apt-get purge virtualbox** and successfully installed it after that. Then installed Extension Pack, DKMS, virtualbox-guest-dkms, added my user to **vboxusers**, etc.

* Checking DKMS with **dpkg -l | grep virtualbox-dkms** returned:
[COLOR="#800080"]ii  virtualbox-dkms                                 5.1.34-dfsg-0ubuntu1.16.04.2                             all          x86 virtualization solution - kernel module sources for dkms[/COLOR]

* Since that was the earlier version, ran: **sudo apt-get purge virtualbox-dkms**, then **sudo apt-get install virtualbox-dkms**, and also installed **virtualbox-guest-dkms** after that, but that just installed the same version. So:

* Added Oracle repo, ran **apt-get update**, then to make sure of version that would be installed, ran **apt-cache policy virtualbox-guest-dkms**, which showed that the newest candidate was still only 5.1.34.

* Decided that since this version mis-match could be the culprit, I had no choice but purge Oracle VBox and just install "virtualbox", as in Ubuntu VBox 5.1.34... installed the Extension Pack, virtualbox-guest-dkms, etc, made sure my user was added to **vboxusers**, ran Guest Additions, checked USB was enabled for the guest in **Settings > USB**... but still no USB devices recognised... which was confirmed by running **VBoxManage list usbfilters**:
[COLOR="#800080"]Global USB Device Filters:

<none>[/COLOR]

* Even though I knew USB & printer were fine in the host, I ran **lsusb**:
[COLOR="#800080"]Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 1a2c:2d43 China Resource Semico Co., Ltd 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 04a9:10dc Canon, Inc. 
Bus 001 Device 004: ID 18f8:0f99 [Maxxter] Optical gaming mouse
Bus 001 Device 003: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/COLOR]

* Decided to purge **virtualbox**, and install the package **virtualbox-5.1** instead (slightly newer 5.1.38), and dependencies, DKMS, Ext. Pack, and all the other things listed above. Once again, VMs load OK, but cannot recognise any USB devices, even though the controllers are enabled, and everything else should be fine.

* Also ran **sudo /sbin/vboxconfig**, and it did its job without issue, but did nothing to fix the USB

Also worth mentioning, to save you asking, that besides the ridiculous amount of reboots:

* I made sure the VMs were not just off, but fully powered down
* I even exited the VirtualBox Manager, though it shouldn't have made a difference
* As suggested in a forum, ran **sudo usermod -a -G vboxsf myusername**
* And **sudo update-usbids** didn't help
* Ran **VBoxManage list usbhost**, but unsurprisingly only came up with:
[COLOR="#800080"]Host USB Devices:

<none>[/COLOR]
* Even tried suggestions of powering up VMs with USB/printer disconnected, then plugging them in once the guest was loaded, to no avail.
* Tried **sudo dpkg-reconfigure virtualbox-5.1**
* The **id** command gives the following output:
[COLOR="#800080"]uid=1000(myusername) gid=1000(myusername) groups=1000(myusername)[/COLOR]
... which, according to other forum posts, shows I am not a member of vboxusers, though have (apparently) successfully added myself (I had no errors come up, and I even installed **gnome-system-tools**, ran **users-admin**, and in **Manage Groups > vboxusers** I am listed in **Group Members**, with a tick, and the **Group ID** is **129** - and, of course, *vboxusers* is listed when I run **groups myusername**). Also, as per another post, there is a group called **wheel**, which VBox apparently uses, and it was adding the user to that which fixed the USB issue - so if you agree, please help me do this correctly (however, looking this up, it seems it is a legacy thing from the early days, specifying who has sudo access, so I'm guessing this is no longer really used).

As you can see, I really have tried a lot of things, and spent hours looking up more info, and uninstalling/reinstalling, before coming here and asking for your help. And previously I would have already fixed it by now, and all I can say is that while I could be wrong, the one difference is that I allowed the removal of a bunch of old kernels, which otherwise had no adverse effect on my system. So, I really hope someone can help, as I am at my wit's end, and I really need to be able to use my printer in WinXP again! (In Ubuntu, the Canon driver is useless, and only good for printing low-res pages, not hi-def DVD printing like I can in XP). Many thanks in advance!

**[COLOR="#FF0000"]UPDATE[/COLOR]**: **[COLOR="#800080"]USB/Printer WORKS as ROOT[/COLOR]**: OK, I thought I'd try something I've never seen suggested, being to run VirtualBox as root. So, after first exporting the WinXP guest (since it's the only one I really need USB for), I closed the VirtualBox Manager, then opened it as superuser via the terminal, which of course listed no VMs, so imported the WinXP VM, checked the settings to see if any USB devices were listed when going to add a new filter, and there was the printer and other USB devices. So running the VM that way at least enables me to print again, though this is just a workaround, so I will not mark it as [SOLVED] (since it isn't). I just thought I'd add this info so you experts have more to work with. Being, in short, USB is fine in Ubuntu (host), and works in guests running as root, but not when running VirtualBox the usual way... and this all happened after allowing removal of old kernels/headers/etc (which might not have anything to do with it, but I'm guessing it does).

---

### Post by LHammonds on 2018-07-11
Is your machines BIOS at the latest firmware revision?

---

### Post by OzzyFrank on 2018-07-11
> **LHammonds said:**
> Is your machines BIOS at the latest firmware revision?

Not sure, but I only built this PC a year ago. And not sure if that would be an issue, since USB was fine in VBox until this update, and is perfectly fine in the host (Ubuntu 16.04) - so this is not a global (host/guest) failure of USB. (EDIT: see my update above - USB is fine when running the VM as root)

---

### Post by slith76-9 on 2018-07-16
Hi, I have exactly the same problems. Thanks for your article.

---

### Post by OzzyFrank on 2018-07-16
> **slith76-9 said:**
> Hi, I have exactly the same problems. Thanks for your article.

Well, sorry I couldn't offer an actual fix, but at least that workaround gets your USB/printer back in VMs until the issue is (hopefully) fixed in a future update.

---

### Post by slith76-9 on 2018-07-25
**the solution:**

"These Ubuntu package was updated yesterday, libpam-kwallet4:amd64 (4:5.5.5-0ubuntu1.2, 4:5.5.5-0ubuntu1.3), libpam-kwallet5:amd64 (4:5.5.5-0ubuntu1.2, 4:5.5.5-0ubuntu1.3)and this must have caused the trouble. I just commented out the following lines in /etc/pam.d/lightdm
auth    optional        pam_kwallet.so
auth    optional        pam_kwallet5.so
and a reboot saved my day"

see [https://unix.stackexchange.com/questions/454593/groups-not-registering-in-x](https://unix.stackexchange.com/questions/454593/groups-not-registering-in-x)

---

### Post by OzzyFrank on 2018-07-26
> **slith76-9 said:**
> I just commented out the following lines in /etc/pam.d/lightdm
auth    optional        pam_kwallet.so
auth    optional        pam_kwallet5.so
and a reboot saved my day"

Nice find! Especially since, from what I can see looking around, the main issue people were having before this workaround was **lightdm**/login issues, and a couple of people found they were no longer members of certain groups (not sure if that was an issue with me, but I was still listed as belonging to *vboxusers*). But that little workaround certainly worked, and now I no longer have to run my VMs as root to get access to the USB devices.

Do you (or anyone else reading this) know if there is any downside to commenting those lines out? The only thing I could find mentioned was the minor annoyance of having to enter the password for KDE Wallet upon each boot (which wasn't an issue here).

---

### Post by redshoerider2 on 2018-09-23
I'll second this solution: commenting out the two kwallet lines brought the USB devices back. 

I did some digging too....and other than having to enter the password for KDE Wallet, I can't find a downside of the removal of those lines. Why, exactly, the KDE wallet causes this error is for someone far smarter than me. 

Thanks!

---

