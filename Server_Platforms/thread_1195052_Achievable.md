---
title: "Achievable?"
date: 2009-06-23
forum: Server Platforms
---

### Post by zootoxin on 2009-06-23
Hi All, 

This question covers many topics so I have posted here, sorry if it causes any problems. 

OK, I am fairly new to Ubuntu I can do a couple of basic things but by no means am I an expert so I though what better way to move forward than to have a goal. 

I have 

1x Win7 PC - Gaming (Win7) - Wired
1x Ubuntu 9. PC - Living Room (UPC) - Wireless
1x WinXP Laptop - Mobile (WinLT) - Wireless
1x Ubuntu 9 Laptop - Bedroom (ULT) - Wireless

1x Router 

2x External HD (Containing Films/Music) 

I will now list several goals I wish to achieve and I would hope you guys can help me succeed hence learning alot about Ubuntu. 

1)I would like a fully functional network inplace making it possible for me to access shared files between the four machines. How? 
a)If not: how is this achieved with the 2 ubuntu machines? 

2)Is it possible to have a VPN type device that will allow me to control every device depending on where I am at the time? How?
a)a)If not: how is this achieved with the 2 ubuntu machines? 

3)I would like to use UPC as a media style device - what software would you recommend to make this possible.  (Can I make use of my cyberlink remote control?)

4)Is there anything for ubuntu like Gotomy PC, I would like to be able to access or control ULT from my work place or mobile phone. 

Ok, just reading that back I realise I have asked alot so I will leave it there for now.
Any help would be greatly appreciated.

Many thanks

Zoot

---

### Post by aeiah on 2009-06-23
for filesharing you'll want a mixture of NFS and SAMBA. samba will let your windows and linux computers share with eachother, but NFS is less of a headache, so you may wish to use that where you can. you can only use it for linux - linux sharing.

for remote access to machines within your network and from the outside world you'll want VNC. there are many VNC applications available for your operating systems. you'll also need a VNC server running on them too so they're connectable, of course. in the case of UltraVNC these are both in the same package.

there are other ways of accessing things in a windows only world or a linux only world. for windows, you've got remote desktop, and for linux you have ssh with x forwarding. i use ssh with x forwarding for displaying my livingroom desktop's music playing software on my netbooks screen, and it behaves just like a local application (but the sound goes through my livingroom speakers since that's where the program lives). 

as for number 3, providing you've got a compatible remote control and you can load up something like elisa or xbox media center onto your ubuntu machine and control it with the remote. i use my livingroom desktop as my multimedia machine but to be honest im quite happy just using a wireless keyboard and mouse since i also use it for general use

---

### Post by Paqman on 2009-06-23
> **zootoxin said:**
> 
3)I would like to use UPC as a media style device - what software would you recommend to make this possible.  (Can I make use of my cyberlink remote control?)


Depends what functionality you'd like it to have. There are quite a few media centre packages available such as Elisa/Moovida, Boxee and XBMC. At the top end you can go for a full-on system like MythTV where you can get into using your PC as a PVR (and even for home automation)

I've personally been using Elisa for a while. For streaming TV, video and music from a network share it's nice and straightforward, with minimal setup required, and has a lovely interface.

---

### Post by LowSky on 2009-06-23
1)just use SAMBA for sharing, its a headache, but it works.

Set static IP's for your computers, it makes sharing easier

2) there ar eplenty of VPN clients, openvpn being the best choice for linux/windows connectivity that will work over a multitude of Operating systems, Teamviewer is great option for windows use

3)Mythtv.org  ... otherwise use Windows 7 media center

4)GotomyPc? is a VPN client like TeamViewer, openvpn will work on any system

---

### Post by aeiah on 2009-06-23
VPN software isnt necessary unless you're dialing in from your office or something. VPN isnt the same as VNC.

---

### Post by zootoxin on 2009-06-23
Thanks for the replies so far guys, I am getting an idea of what is and is not possible. 

My first task is going to be making all the machines visable to eachother so it looks like samba is the way forward.
Not sure yet how I view the Linuxs machines from the Windows ones but thats another story.

I also (forgot to mention) have a External Hard Drive which is connected to my Router, at the moment my Linux PC's can't see this device.

So what I basically need - Get all 4 computers linked.
Get the 2 Linux machines linked to the External Hard drive attached to the router. 

Anyone have a good tutorial for SAMBA?

---

### Post by LowSky on 2009-06-23
ubuntu documentation
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
nice 10 min video
[http://www.youtube.com/watch?v=Ad17kma8rNM](http://www.youtube.com/watch?v=Ad17kma8rNM)

---

### Post by ugm6hr on 2009-06-24
> **zootoxin said:**
> So what I basically need - Get all 4 computers linked.
Get the 2 Linux machines linked to the External Hard drive attached to the router. 

How is the networked HD recognized in Windows?  Presumably it is a specific networked HD device?

It must use some form of drive sharing, which is likely to be SMB (to allow easy sharing with Windows).

If so, you should be able to just type in the IP address into nautilus:
e.g. smb://192.168.1.250

---

### Post by zootoxin on 2009-06-24
Ok I had a look at things last night (shame I have to go to work! it gets in the way)

Firstly It looks like the main problem is linking XP to Win7 so I am going to ignore that for the time being. 

So, off the bat I my Ubuntu Laptop can see the shared drives on my Win7 PC no problem. 
Any idea how I make it a permanant link? 

I can connect to the Hard Drive attached to the Router by FTP again anyway I can make it perm? create a shortcut etc? 

I installed Elisa which looks really good but I can't find the folders from the network to link to. Any Ideas? 

This is turning out to be a head scratching but pretty cool exercise :D

---

### Post by ugm6hr on 2009-06-24
> **zootoxin said:**
> I can connect to the Hard Drive attached to the Router by FTP again anyway I can make it perm? create a shortcut etc? 

For SMB, the share is "permanent" - you just need to give the relevant program the correct network address.

You can add a shortcut in nautilus just be dragging the address to the bottom left pane.  However, this only really works with fixed IPs.

Not sure how Elisa / Moovida network shares work - I use XBMC myself.

---

### Post by zootoxin on 2009-06-24
OK So far so good guys, network up and running and working nicely. 

Thanks for the tip on XBMC it looks really cool. can you give me some pointers on getting the most out of it please. 
It looks like there is a lot of potential there.

Also, can someone tell me how to make a shortcut? (In noob detail)

I have the emerald theme manager and I have downloaded and imported the themes, I can see them in the list of themes but when I click on them nothing happens. 
How do I actually get the theme to change on my unbuntu? 

Thanks guys, I am loving this

---

### Post by windependence on 2009-06-24
> **aeiah said:**
> VPN software isnt necessary unless you're dialing in from your office or something. VPN isnt the same as VNC.

It certainly would be necessary for someone dialing in from outside their network as VNC is not secure. Zoot, I would recommend OpenVPN. It is free and has a GUI windows client to boot.

As suggested, teamviewer is also very good.

-Tim

---

### Post by ugm6hr on 2009-06-25
> **zootoxin said:**
> Also, can someone tell me how to make a shortcut? (In noob detail)

1. Open nautilus (file browser).
2. Type in the network address e.g. smb://192.168.1.250/freenas1/ in Location bar of nautilus
Where: smb = for Samba shares; 192.168.1.250 = IP address of the computer with the shared folder; freenas1 = share name
This should open the SMB share folder
3. In nautilus left hand pane, select Places from drop-down menu. 
4. Double-click the location bar entry to highlight the entire address.
5. Drag the hightlighted location bar to the bottom left pane in nautilus
6. You can then rename it to whatever you want with right-click.

> Thanks for the tip on XBMC it looks really cool. can you give me some pointers on getting the most out of it please. It looks like there is a lot of potential there.
Check the xbmc website.  There is an Ubuntu PPA for up-to-date releases too.  I would suggest just playing around with it.  But unless you are setting up a media centre, it is unlikely you will need most of its features.

---

### Post by zootoxin on 2009-06-30
OK Guys, here's what we have. 

I have the samba network in place. 
Ubuntu laptop in Bedroom + XBMC - linked to all other machines accessing films and music from windows network. 

Ubuntu PC in living room + XBMC - linked to all other machines accessing films and music from windows network.

The two Ubuntu devices can now control one another using the ubuntu remote desk top thingy. 

So its all working remarkably well up to this point. I have a couple of problems though.

A) I have an ExHD connected to the Ubuntu PC which I have shared but when I try and connect from one of the windows devices I get an error - you do not have permission etc. 
How do I fix this? 

B) How do I connect to my network from the outside world (i.e. over the internet?) 

C) How can I make XBMC launch on Start up? 

Thanks for the advise 

Zoot

---

### Post by windependence on 2009-06-30
Your problem with the external is probably an ownership issue rather than a permissions issue. If you are using SAMBA, there are several options that you could configure to make the drive available only to your internal users. Don't let anyone tell you to set permissions to 777 as this is a serious security issue. Try to do it the correct way, you'll be glad you did. 

For web access, I would use ssh or sftp on port 22 (or any other port you want to run it on). You don't need to run an FTP server for either on of these, which is much more secure.

Not sure what XBMC is so I can't help you there but maybe someone else here can.

-Tim

---

### Post by zootoxin on 2009-07-02
> **windependence said:**
> Your problem with the external is probably an ownership issue rather than a permissions issue. If you are using SAMBA, there are several options that you could configure to make the drive available only to your internal users. Don't let anyone tell you to set permissions to 777 as this is a serious security issue. Try to do it the correct way, you'll be glad you did. 

For web access, I would use ssh or sftp on port 22 (or any other port you want to run it on). You don't need to run an FTP server for either on of these, which is much more secure.

Not sure what XBMC is so I can't help you there but maybe someone else here can.

-Tim

Hi Tim, thanks for the reply. 

Please could you explain to me the correct way to get the share for the external harddrive working.

I get two error messages

1. Permissions
2. Could not Mount

I have shared a normal folder and that works just fine.

Also, what is and how do I set up - ssh or sftp on port 22

Thanks 

Zoot

---

### Post by zootoxin on 2009-07-15
> **zootoxin said:**
> Hi Tim, thanks for the reply. 

Please could you explain to me the correct way to get the share for the external harddrive working.

I get two error messages

1. Permissions
2. Could not Mount

I have shared a normal folder and that works just fine.

Also, what is and how do I set up - ssh or sftp on port 22

Thanks 

Zoot


BUmp :)

---

### Post by windependence on 2009-07-15
Sorry, been crazy busy. Will reply shortly. :-)

-Tim

---

### Post by zootoxin on 2009-07-15
> **windependence said:**
> Sorry, been crazy busy. Will reply shortly. :-)

-Tim

Thanks mate :)

---

### Post by windependence on 2009-07-16
> **zootoxin said:**
> BUmp :)

Are you trying to share the external drive attached to a Linux box? Are you sharing it via SAMBA?

First, show me the output of:

```
sudo fdisk -l
```

-Tim

---

### Post by zootoxin on 2009-07-27
Sorry for the late reply.

Here is the output

Does it mean anything to you? 

Disk /dev/sda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1b6a1b69

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4685    37632231   83  Linux
/dev/sda2            4686        4870     1486012+   5  Extended
/dev/sda5            4686        4870     1485981   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb4fa5315

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    c  W95 FAT32 (LBA)

---

### Post by windependence on 2009-07-28
Looks like /dev/sdb1 is your USB drive. It doesn't look mounted. We need to mount the drive before you can share it.

-Tim

---

### Post by zootoxin on 2009-07-28
> **windependence said:**
> Looks like /dev/sdb1 is your USB drive. It doesn't look mounted. We need to mount the drive before you can share it.

-Tim


I can access the files on it. Is that different?

---

