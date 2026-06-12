---
title: "VirtualBox Shared Folders"
date: 2008-07-20
forum: Virtualisation
---

### Post by xItachi on 2008-07-20
I'm using VirtualBox 1.6.2 and I have host as Ubuntu 8.04 and guest as Windows XP Professional.  I've set up the shared folder by going to the Windows XP VM window and Devices > Shared Folders.  I set the folder to be the home folder (/home/stephen) but I don't see it in Windows XP.  I went to Start > Run > explorer and I did not see the shared folder, nor in My Network Places.  Any ideas?  I've read somewhere that we could also use FTP or similar file transfer, but I'm not exactly sure how to do that.  Thanks!

---

### Post by coffeecat on 2008-07-20
Have you installed the Guest Additions in your Windows guest?

---

### Post by richiewrt on 2008-07-20
Map it as a network drive in your windows virtual box.  Open windows explorer (not internet explorer) Tools-->Map network drive. Go to browse and it should be there.

---

### Post by xItachi on 2008-07-20
Yes, I have installed Guest Additions, and I have tried mapping the network drive just now.. I clicked on browse and it didn't show up. =(

---

### Post by bren21 on 2008-07-20
I've been having the same problem on my virtualbox install. I go into windows explorer, network places, entire network,  virtual box shared folders, but there is no folder there. I have guest additions installed as well.

---

### Post by zd3nik on 2008-07-20
> **xItachi said:**
> Yes, I have installed Guest Additions, and I have tried mapping the network drive just now.. I clicked on browse and it didn't show up. =(

When you map the drive your best bet is to just put the shared folder path in yourself rather than jumping through all the hoops necessary to find it by browsing.

When you share the folder in VirtualBox, before closing the Shared Folders setup box, right-click on the folder you shared and click on what's this.  It will give you the path to type in when you map a drive to the folder in windows.

For example, if you named the folder "SharedFolder", then in the map network drive window you would put in \\vboxsvr\SharedFolder

Hope this helps.

---

### Post by hariprs on 2008-07-20
I am also having the same problem, Temporily i am using bridged network between Guest&host and doing FTP to share files.

---

### Post by xItachi on 2008-07-21
hariprs: Could you please explain how to do that?

zd3nik: I tried doing what you said by mapping the network drive directly instead of browsing, (\\vboxsrv\stephen) and it still cannot find the folder.

---

### Post by krsmit0 on 2008-07-21
xp has problems with older copies of the guest additions.

[http://forums.virtualbox.org/viewtopic.php?t=7273&sid=42ac265c3318de80ded22e7d2f83a9d7](http://forums.virtualbox.org/viewtopic.php?t=7273&sid=42ac265c3318de80ded22e7d2f83a9d7)

read this and there is a download link for the newest version.

try that.

---

### Post by xItachi on 2008-07-21
krsmit0: Thanks! Guest Additions 1.6.0 works with shared folders :)

---

### Post by bone2006 on 2008-07-21
I'm having a hardtime sharing as well.  Getting a little confused as their official website seems to indicate that the free open source edition you can't share between host and guest?

I downloaded the new iso for the guest additions, which I believe is VBoxGuestAdditions_1.6.2.iso and so far I haven't been able to share either.

---

