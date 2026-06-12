---
title: "virtual box"
date: 2019-02-26
forum: Virtualisation
---

### Post by j3984 on 2019-02-26
Do you think using ubuntu in Virtual Box is truly secure??? I mean its an Oracle product and its used on Macs and PCs so it seems that it might be possible for someone to backdoor
their way into your data  or something..?? But its sure nice to not have to dual boot which is never without some complication.What do you think?

---

### Post by TheFu on 2019-02-26
All software has risks.  Only trivial programs are likely to be completely secure and maybe not even those are secure if the libraries used to build the program(s) have issues.

The virtualbox installed from the Ubuntu Repos is a F/LOSS version. You can check all the code yourself, if you like, or pay someone to check the code for issues. Up to you.

But, in the world where I live, there are shades of white, black and gray.  Nothing is perfectly secure. Mitigations for each known issue are needed or the risks need to be documented and the people in charge (CxOs) need to physically sign off on those risks. The host isn't perfectly secure, so any guest inherits both the good and bad from that. VirtualBox is far from perfect, but it can be the best choice for many needs.  There are other choices, each with pros and cons of their own.  

I haven't used virtualbox in about 8 yrs.  For my needs, there are better options.

---

### Post by bitsnpcs on 2019-02-26
Hello j3984,

with Virtualbox, if enabled, you can set  it to share files with the host and guest, if not enabled you shouldn't be able to share them.
Another option is you can set your virtual machine for "Host only adapter" and use it offline, even whilst the OS it is installed on (Host) still has internet access. 

There is also a software called "Gnome Boxes", I heard it mentioned in the last 3 weeks, it was getting a positive statement about it. I haven't tried it myself, if you have not made a final decision yet it is worth looking at both GnomeBoxes & VirtualBox, such as which host OS you use, and the each of the software's requirements to see which will work best for you.

---

### Post by QIII on 2019-02-26
Moved to Virtualisation for a better fit.

---

### Post by jdeca57 on 2019-02-27
I may be wrong, but I consider Virtualbox as an ideal environment to test a new version of Linux or to try out some new software or combinations of software. There are other solutions once you will use said versions or software for real. The performance of Virtualbox is good enough to test a;most anything if your hardware is up to the task. And if it amounts to testing, security is a lesser issue. I'd recommend the use of it.

---

### Post by lammert-nijhof on 2019-03-05
I consider Virtualbox virtual machines very secure. I download the deb files directly from the Oracle site to get the latest version, but also the Ubuntu repositories will be safe, but it has a somewhat older version of Virtualbox. I use shared folders to share and exchange data between VMs. I have the Firewall active and I block all incoming traffic to the host and all VMs. There are no open ports, that could be used by hackers. 

[LIST]
[*]I have one dedicated VM for Banking and Paypall and that one is only "powered on" and on line when needed, say a few minutes per day. The VM is NOT used for anything else, no browsing, no emails or any other potential way it could get a virus.
[*]I have another VM for testing new Apps or settings and I take a snapshot each week and for each risky change. If needed I can roll back that VM to the last working state.
[*]I have a VM for all other normal usage like email, browsing, whatsapp, torrents, libre-office etc, but you also could use the host for that.
[*]And I use Windows XP to play the old wma copies of my LPs and CDs with True Bass and WOW effects, just to remember the good old times
[/LIST]
I run all that on a 2008 HP dc5850 with a 4-core Phenom II (3.2 GHz)and  8 GB of DDR2. I use mainly Xubuntu and Ubuntu Mate, both 18.04 LTS, because they are efficient with memory usage. I give XP 1 GB, most Linux distros 1½ GB, Ubuntu 18.04 itself 2 GB and Windows 7 and 10 each 2 - 2½ GB. That is sufficient for most applications, but I have an old habit of closing applications and web sites, that I do not use anymore.

---

### Post by SeijiSensei on 2019-03-06
VirtualBox began as an open-source project under the auspices of Sun Microsystems and continues to be one.  Oracle bought Sun and thus acquired VirtualBox as well. All the VB code is open except for the Extension Pack which includes proprietary software to enable functions like USB that are [encumbered]("https://www.usb.org/about") with intellectual property rights.  The complete source code can be downloaded from [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads).  If you want a completely open-source implementation, don't install the Extension Pack, though you'll be giving up useful added functionality for probably no increase in security.

---

### Post by moahiah51n32 on 2019-05-11
> **lammert-nijhof said:**
> I consider Virtualbox virtual machines very secure. I download the deb files directly from the Oracle site to get the latest version, but also the Ubuntu repositories will be safe, but it has a somewhat older version of Virtualbox. I use shared folders to share and exchange data between VMs. I have the Firewall active and I block all incoming traffic to the host and all VMs. There are no open ports, that could be used by hackers. 

[LIST]
[*]I have one dedicated VM for Banking and Paypall and that one is only "powered on" and on line when needed, say a few minutes per day. The VM is NOT used for anything else, no browsing, no emails or any other potential way it could get a virus. 
[*]I have another VM for testing new Apps or settings and I take a snapshot each week and for each risky change. If needed I can roll back that VM to the last working state. 
[*]I have a VM for all other normal usage like email, browsing, whatsapp, torrents, libre-office etc, but you also could use the host for that. 
[*]And I use Windows XP to play the old wma copies of my LPs and CDs with True Bass and WOW effects, just to remember the good old times 
[/LIST]
I run all that on a 2008 HP dc5850 with a 4-core Phenom II (3.2 GHz)and  8 GB of DDR2. I use mainly Xubuntu and Ubuntu Mate, both 18.04 LTS, because they are efficient with memory usage. I give XP 1 GB, most Linux distros 1½ GB, Ubuntu 18.04 itself 2 GB and Windows 7 and 10 each 2 - 2½ GB. That is sufficient for most applications, but I have an old habit of closing applications and web sites, that I do not use anymore.

Hello  				 				 					 						 	[URL="https://ubuntuforums.org/member.php?u=1949495"][B][COLOR=#000000]lammert-nijhof,
[/COLOR][/B][U][COLOR=#000000]Can you tell me more about firewall setting running VirtualBox please.
[/COLOR][/U][COLOR=#000000]
_I'm a newbie ):P_[/COLOR][B][COLOR=#000000]
[/COLOR][/B][COLOR=#000000][/COLOR][COLOR=#000000][/COLOR][COLOR=#000000][/COLOR][/URL]

---

### Post by SeijiSensei on 2019-05-11
A VirtualBox VM by default runs in "NAT" mode. That means the VM is not visible from outside the host machine. If you choose "bridged" networking, the guest will receive an address on the same network as the host. In that case it's as vulnerable as any other machine on your network.

---

### Post by lammert-nijhof on 2019-05-21
The firewall settings are the same as with any other installation. I use the bridged network setting, because it is saves CPU load on my old brick. If you are more worried about security or have a faster CPU you could use the NAT network setting for all guests blocking inbound access. I use Gufw firewall and I have denied inbound access on both host and most guests. Only one Guest has the ports open for KDE Connect. To share data between host and guests and between the guests, I use the shared folders function of Virtualbox. I do not allow access from any other computer to the host nor to the Guests.

I have a backup server, that is powered on, only during the backup and that backup server will allow inbound traffic from Samba (Windows Networking). The backup server is an old Pentium 4 with all my reasonable sized IDE disks (250 and 320 GB) with BTRFS and LZO compression, it will accept ~1 TB of data. I use the same trick to keep my laptop up-to-date, my laptop Ethernet allows inbound traffic for Samba. The laptop WiFi blocks all inbound traffic. The nice thing is that I can use one cable to transfer data at 1 Gbps, by selecting the laptop as DHCP server in its Ethernet settings.

---

