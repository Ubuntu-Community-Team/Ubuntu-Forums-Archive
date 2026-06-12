---
title: "Ubuntu Server 21.04 Stuck Loading Installer"
date: 2021-05-16
forum: Server Platforms
---

### Post by norsemangrey on 2021-05-16
[COLOR=#1A1A1B][FONT=&amp]I am trying to install Ubuntu Server (downloaded from [/FONT][/COLOR][here]("https://ubuntu.com/download/server")[COLOR=#1A1A1B][FONT=&amp]) on my server, but after selecting "Ubuntu Server" from the GRUB menu the process seem to get stuck on "Reached target Cloud-init target." before reaching the installer. Does anyone have any idea what might be going on?

[/FONT][/COLOR][IMG]https://preview.redd.it/housdyuv1cz61.png?width=987&format=png&auto=webp&58a9d74b[/IMG][ATTACH=CONFIG]288478[/ATTACH][COLOR=#1A1A1B][FONT=&amp]
[/FONT][/COLOR][IMG]https://preview.redd.it/housdyuv1cz61.png?width=987&format=png&auto=webp&58a9d74b[/IMG]

---

### Post by TheFu on 2021-05-16
Did you switch to a different tty and login?

Or .... just hit <enter> for a login prompt.

BTW, I just installed 21.04 Server in the last 10 minutes.

---

### Post by norsemangrey on 2021-05-16
Thanks for the reply. I am not familiar with what tty means or how I switch this. The only thing I did after starting the computer was selecting the ISO image location from device boot menu and then selecting 'Ubuntu Server' from the GRUB menu. Hitting 'Enter' or anything else does not do anything at the stage where the installer stops.

---

### Post by TheFu on 2021-05-16
You're still in the installer?  I didn't have issues with that besides forgetting to remove the flash drive.

Are you in a virtual machine?  If so, post the hypervisor used.  I used all the defaults for the VM install, except I forced using a bridge for the LAN connection and virtio for both the HDD and NIC.

Perhaps the screen isn't tall enough to see the "Close" or "Reboot" button?

/var/log/installer/ is where the installation logs are located.

---

### Post by norsemangrey on 2021-05-16
I am not installing on a virtual machine. This is on bare metal on a Supermicro X11 board. Maybe 'installer' is not correct to use here because I have not really gotten to the installer yet. As mentioned previously the _only_ thing I have done after booting from the Ubuntu Server ISO is selecting Ubuntu Server from the GRUB menu. I have have not even been presented with any install options yet.

I am stuck somewhere between here:
[ATTACH=CONFIG]288481[/ATTACH]

and here:
[ATTACH=CONFIG]288482[/ATTACH]

---

### Post by TheFu on 2021-05-16
<enter> doesn't work?
Check the keyboard. May need to ensure "legacy usb support" in the bios.

---

### Post by norsemangrey on 2021-05-16
There is no issue with the keyboard. I can of course hit the enter key, but it does not do anything other than moving the cursor to the next line. Are the snapshots I am adding to the post not showing?

---

### Post by ajgreeny on 2021-05-16
*Thread moved to **Server Platforms**.* which is more appropriate and a better fit.

---

### Post by norsemangrey on 2021-05-16
Thanks. I do not know whether or not this issue is server related or not though.

---

### Post by norsemangrey on 2021-05-18
I hope I am not the first ever to experience this issue :-k

---

### Post by TheFu on 2021-05-18
> **norsemangrey said:**
> I hope I am not the first ever to experience this issue :-k

Think I started a reply twice before, but ended up deleting it each time.  If you aren't a "server" person already, then there is little reason to use 21.04 "server" over 20.04.  6 months of patch support really isn't worth the effort. The 21.04 is more for developers and testers, not for production.  Production systems deserve LTS releases.  People new to Linux should stick with desktop installs. We can still install all the server programs into a base desktop system. There's no special limit on which programs can be installed between desktop and server ISOs.

The new installer is VERY different.  To check whether it is a HW problem, install 20.04 Server. How does that work for you?  20.04 has 5 yrs (4 yrs left) of no-hassle patch support. and perhaps 9 yrs of sign-up, hassle, patch support, remaining.

The 21.04 server installer was hiding some buttons way at the bottom of the screen during my install test. They were the normal "Done", "Back", "Cancel" options.  Use a {tab} to cycle through fields.  

I pulled the server ISO file down the week it was released. I just checked using zsync and there aren't any updates. 4/22 is the ISO date.

---

### Post by norsemangrey on 2021-05-18
The 20.04 version seems to work fine. The reason I want to use 21.04 is because it has a newer version of ZFS. That said I am not new to Linux and have always used the server versions of Ubuntu as I am more comfortable with CLI. It is probably best to stick with the LTS in general, but I do not have any special hardware and it really irritates me that this is not working. I mean I am not even getting to the install so something weird is going on here.

---

### Post by TheFu on 2021-05-18
And the installation logs on a working vs non-working install?  What's different?

---

### Post by norsemangrey on 2021-05-19
How could I possibly see any installation logs when I not even get to the installer? :)

---

### Post by TheFu on 2021-05-19
> **norsemangrey said:**
> How could I possibly see any installation logs when I not even get to the installer? :)

Because you said: 
> The 20.04 version seems to work fine.
That means somehow booting into Linux off some boot media, choose "try ubuntu", mount the place with the prior, failed, 21.04 logs, and being able to review them.  Any Linux distro with a "try ubuntu" option should work.  I'm partial to Ubuntu-Mate, but anything from TinyCore to a full Ubuntu Desktop will probably work.

Or maybe just use the 20.04 install with a PPA to get a newer version of ZFS?

I don't use ZFS on Linux.  Played with it on 20.04 and it did some funky things I didn't like and the system was crazy slow. Went back to LVM+ext4 and all was fast again.  That's from about 10 months ago, so my memory is a little fuzzy and it wasn't with 20.04 server.  I haven't moved to it yet. 

The "Try Ubuntu" method is core to troubleshooting many issues - even just to see whether an incompatible driver was introduced to the kernel later.

---

### Post by rsteinmetz70112 on 2021-05-19
Could the iso be corrupt? Have you tried a different iso or checked the installation iso you are using?

---

### Post by TheFu on 2021-05-19
> **rsteinmetz70112 said:**
> Could the iso be corrupt? Have you tried a different iso or checked the installation iso you are using?

zsync will quickly validate a current .ISO file, if the sha256sum file cannot be found.
Steps:
[LIST=1]
[*] get the zsync file from the same place as the ISO file
[*] place both into the same directory - they are from 4/22
[*] Run 
```
$ zsync ubuntu-21.04-live-server-amd64.iso.zsync
```
[/LIST]

Perhaps in the Advanced option of the grub menu, there is a checksum validation option. I honestly haven't looked.

---

