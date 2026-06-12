---
title: "More VMWare/WinXp networking problems!"
date: 2008-04-09
forum: Virtualisation
---

### Post by drsox1899 on 2008-04-09
I'm another Ubuntu 7.10 user who has a problem with VMWare networking to/from a WinXp virtual install.  I've searched the forum for "vmware networking" and there are lots of great how-to's for sharing between Ubuntu and WinXp but my problem at the moment isn't that.

With the Xp install on the NAT setting I can access the internet, but not my local network.  The data shows that a DHCP server at 172.16.176.254 has given it an address of 172.16.176.128 with a Gateway at 172.16.176.2.  The Xp will connect to the host through a Workgroup of Mshome - the host is also on the same Workgroup, but asks me for a password if I try to connect.

All my other PCs etc are on a network of 192.168.123.*. with the Workgroup name Pussycat. I can ping the host's external address (192.168.123.26) from inside the Xp, as well as all the other networked devices on 192.168.123.*.

If I change the NAT setting to Bridge, then nothing is connectible.  No DHCP assigned address is given.  Setting a fixed address in the 192.168.123.* range does nothing, neither does a fixed address as 172.16.176.128.  Bridge just seems to be going nowhere.

For the moment I just want to be able to connect to my other networked devices !:confused:

Thanks.

---

### Post by drdrewdown on 2008-04-09
IF this is on a wireless LAN bridge function thru vmware will not work at all

there is a rule in the 802.11 something that says you cannot spoof a mac address on a wireless NIC

in this scenario of a wireless lan you're only option will be NAT networking inside the VM.. if you hardwire, Bridge ought to work without issues.

basically with the NAT scenario its putting you on a different LAN from the rest of your pc's other then the host, which is using a vmnet to associate with the NAT lan.

please verify you're on a wireless connection before i go too much further..

cheers

---

### Post by drsox1899 on 2008-04-09
Hi there.  No, there is no Wireless stuff involved at all.  All connections are by Wired Ethernet.

---

### Post by fjgaude on 2008-04-09
Go back to the NAT type of LAN connection. Make sure you have setup Samba for the Shares you wish to connect to. Make sure you have your samba password entered:

```
sudo smbpasswd -a <name>
```

Enter your password twice, or is it three times, and then you should be at to where you wish to be.

Let us know how you are doing.

---

### Post by drsox1899 on 2008-04-09
Well that might be it.  Another unknown unknown.

I have not configured any Samba in Ubuntu.  My Unix RAID boxes already have Samba shares that I can access from Ubuntu.  Where should I start in configuring Samba to be able to access the WinXp VMWare installation ?  :-k

---

### Post by drsox1899 on 2008-04-09
Well, I've got part of the way there.

I reset the WinXp VMWare to NAT and then read the instructions in this Samba guide : [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605).

Thank goodness that I now know that I have to do something to configure Samba.  The instructions above are good but not without problems for the literally minded Ubuntu-ite..

OK, so I can get out of my WinXp prison and also access my Ubuntu box from my other "real" WinXp box.  I can't access the NAS's, but that can wait till tomorrow.

Thanks so far.

---

### Post by fjgaude on 2008-04-09
If you are runniing other than the beta Hardy, go to **System/Administration/Shared Folders** in the gnome panel menu, and setup the Shares you wish. It's real easy once you know what to do. <smile>

Set everything as a Share and then in WinXP you will have the run of all your Ubuntu files and drives.

---

### Post by drsox1899 on 2008-04-10
There now seems to be some duplicate info in my Samba config files.  When I look at Places>Network I see Icons for individual Pcs AND an icon for Windows Network.  Selecting Windows Network shows an icon for the Workgroup (Pussycat).  Selecting Pussycat shows more icons for the individual PCs !

Where would I look to try to correct this ?

I also cannot see an icon for the VMWare XpPro in Places>Network.

Plus - when I look in the VMWare XpPro in Network Places - I only see one of the PCs on the network - the UNIX RAID NAS.  When I try to open it, I get a "XXX is not accessible etc notice"  Usually in Win this means that Win hasn't waited long enough and eventually a login screen appears - not in this case.

What should I do here ?

:confused:

---

### Post by drsox1899 on 2008-04-12
Latest news :

Switched back to VirtualBox.  Quicker for WinXp and may be more functional for USB support etc.  I'm also updating to 8.04.

My networking problems were solved on VB with 7.10 ! 
But not USB - hence the update.

I'm abandoning VMWare.  Doesn't seem to be right for what I want - namely to run some Win apps and Games for which  I can't find alternatives.

---

