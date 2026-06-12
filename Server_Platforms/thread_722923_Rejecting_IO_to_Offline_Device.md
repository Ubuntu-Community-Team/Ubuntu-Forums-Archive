---
title: "Rejecting I/O to Offline Device"
date: 2008-03-13
forum: Server Platforms
---

### Post by gtdaqua on 2008-03-13
We have a strange problem with our Dell PowerEdge 1950 server here. Its a brand new machine running Ubuntu 7.10 64 bit Gutsy server on it. In two weeks time we have seen this message twice now: "Rejecting I/O to Offline Device". 

The machine hosts only VMWare server. Whenever the error message pops up, we lose connectivity and only option is to restart the server (hard boot)! 

Its a brand new server we setup on first week of Feb and it has two 146GB 3.5" SAS 15K in RAID-1. The server also has Dell Remote Access Controller. 

Can anyone tell me why this is happening? Its critical because we have not found a solution so far; actually we are not quite sure where the problem is.

---

### Post by Petersonz on 2008-03-13
Yep.

I myself have a 2950 with an array on the Perc 5/i (onboard) with a RAID 5 and a Perc 6/e with an external MD1000 RAID 5.

The problem lies in the fact that the Ubuntu kernel includes an older module for the megaraid_sas driver version 03.00.10-rc5.

This version is in fact too old to reliably support both the Perc 5 and Perc 6 in the 9 series Power Edge servers from Dell. (Found this out when installing the Dell Openmanage Managed Node software and it complained that 03.00.13 was the minimum required version for both Perc 5 and Perc 6 controllers)

I wound up having to install Redhat Enterprise 5 in order to install the latest Dell/LSI Logic driver which is 03.00.16 in order to get the reliability back. 

Dell and LSI only release the dkms version of this driver in Redhat RPM or Suse format, thus leaving us freeware Linux folks out to dry.

I tried using the alien package converter to change it to debian and install it to no avail. I suspect because I didnt get the dkms package and try that.

In the end, it made sense to just bite the bullet and buy Redhat to use these Dell servers and move on.

Also, dont waste your time trying the Hardy 2.6.24-11-server kernel. It wont help. It still has the 03.00.10-rc5 old megaraid_sas driver in it.

Sorry for the bad news, Im not good enough to take apart the Redhat driver and make it work in Ubuntu.

Some happier news for you tho.

If you bought your Dell with the Quad port Intel PCIe card, you can compile Intel's latest drivers as a module against the Ubuntu kernel and life will be good. Both the PT and VT versions of the card work great for me complete with jumbo frames, LACP Bonding, and VLAN tags.

---

### Post by gtdaqua on 2008-03-13
hey thanks for the reply! thats a good research you have done! But my question now is that really causing Ubuntu to see devices go offline? Should the Ubuntu server be seeing the Dell's RAID because the OS should normally see only the virtual disk (VD) created out of Dell's RAID utility. 

Btw, that server has a quad-port. My another concern is that the case with all Dell servers? Then the matter has to be escalated guys! Come on, its getting serious now because I know there are several IT admins out there with Dell and Ubuntu boxes trying to run VMWare!!

---

### Post by Petersonz on 2008-03-13
In my case, so far, yes.

Even though the megaraid_sas driver shows the individual drives in the dmesg, only the virtual/lun drive created in the Perc Raid utility show up as /dev/sda (and /dev/sdb in my case as its a perc 6 with an MD1000 added).

The /dev/sda (on the internal Perc 5) never crashed with Offline Device errors, the /dev/sdb (external MD1000 attached to Perc 6/e) does crash randomly for me.

For 2 days now, been on Redhat Enterpise 5 with Dell's 03.00.16 driver and no problems so far. This is a record under heavy disk I/O for me.

---

### Post by Petersonz on 2008-03-13
Another note.

I have another client with a 1950 (1U high) and 2 SAS drives in a mirror using the onboard Perc 5/i and an MD3000 on a Perc 6/e with no reliability problems using the Hardy kernel.

But, the disk I/O load on the internal mirror array is much lower than my 2950 installation had on its RAID 5 internal array.

Maybe the new driver mitigates contention issues when multiple Perc/Megaraid controllers are used? 

I dunno. :confused:

---

### Post by gtdaqua on 2008-03-13
Dell Openmanage does say the firmware is too old and that it needs minimum 03.00.13. But I didnt bother because the system simply works. Only one particular Linux server throws up this error message once in a while and we lose connectivity.

---

### Post by gtdaqua on 2008-03-13
what do you think we should do? approach dell? approach canonical? or both?

---

### Post by Petersonz on 2008-03-13
Good question.

I say beat up Dell. Especially if you have Silver support from them. 

They are trying to score the desktop folks with Dell desktop machines with Gutsy installed on them, why be polarized to consumer desktops only and leave us loyal Dell server/Ubuntu Server folks in the cold?

If I had Michael Dell's phone number, Id love to tell him how I feel about their conformist practice of supporting Redhat and Suse only. Just like HP does. :lolflag:

Something like:

"Be different Mr Michael Dell. Tell your server team to pay attention to us Ubuntu server people and help us deploy Dell servers with Gutsy and Hardy on them."

Dell must be a majority stockholder of LSI Logic to be so loyal to them for their Perc cards. I gotta believe they can exert pressure on LSI's driver devs to produce GPL'ed driver source that can be compiled against Ubuntu kernels.

---

### Post by gtdaqua on 2008-03-13
right. will start then. All the dell servers we have here (plus switch, san box) are under gold support. 

but i cant understand why ubuntu wouldnt include the update? why supply a too old SAS drivers (03.00.10-rc5)? 

the only prob with dell is that  every issue goes on and on until u have an affair with them!

---

### Post by gtdaqua on 2008-03-14
I am asking in dell forums and they are asking to contact Ubuntu Forums for a faster solution. I am not happy with their answer. 

Here is the post in dell.

[Important Storage Driver Issue: Per6i/Integrated Drivers]("http://www.dellcommunity.com/supportforums/board/message?board.id=sw_linux&thread.id=13399")

Can Ubuntu tell me how do we go about this?

---

