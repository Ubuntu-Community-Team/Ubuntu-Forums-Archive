---
title: "A different kind of failed upgrade"
date: 2011-10-14
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2011-10-14
Normally people get stuck with no GUI session because they lack proper VGA drivers setup. Others are stuck at purple screen, but in the end it's the same problem with a touch of plymouth. Wubi dudes get stuck at no grub or grub rescue.

Yet, there seems to be a growing number of cases like this:
[http://ubuntuforums.org/showthread.php?t=1860359](http://ubuntuforums.org/showthread.php?t=1860359)

I have no idea what happened in this cases. Some apparently have no way of using their NIC. Others just don't have fixed/dhcp IP and DNS set. Either way, they seem to not have have all 11.10 packages installed. Those with Internet can't run apt-get update/upgrade, dist-upgrade, do-release-upgrade, etc.  Some have lsb_release pointing to 11.04, other 11.10.

Do you have any clue?

---

### Post by cariboo on 2011-10-14
Have a look at this bug report:

[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/864174](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/864174)

Post #6 seems to be a workable solution

---

### Post by effenberg0x0 on 2011-10-14
Thanks, I'll see if it fits these guys situation. 

Btw, nice beard.

EDIT: I'll report back, just waiting for some word for them. Hope you're right. It only tricks me why they have broken dependencies, inability to update/upgrade, etc.

---

### Post by ventrical on 2011-10-15
My first question  to those who are having probs with install would be "Did you use a torrent to do your download".  I mean , really , how many check the integrity of their downloads?

  During Maveric and beta testing of natty I had some wicked problems with Unity and wireless drivers. One long_time user commented that "the devs are just having some fun with you". I did not buy it then and I don't buy it now.

  I do know that if I do a download from , lets say, The University of Waterloo in Canada that I am going to get a valid download 99.9 % of the time .. but, as time has proven, if I use a torrent then I am always setting myself up for a re-mixed mirror and that install can be hacked  till the cows come home .. so then I'm just *issing against the wind if I start bellyaching about a failed install.

---

### Post by dino99 on 2011-10-15
used "main" server (as usual)

---

### Post by vasa1 on 2011-10-15
> **ventrical said:**
> My first question  to those who are having probs with install would be "Did you use a torrent to do your download".  I mean , really , how many check the integrity of their downloads?
...

I used a torrent to get 11.10 and then only did a **md5sum** before I made a live USB which worked as it should.

I've used torrents three times so far and all of them gave me satisfactory results (matching md5sums and functional live USBs.)

I did not check the integrity.

---

### Post by ventrical on 2011-10-15
> **vasa1 said:**
> I used a torrent to get 11.10 and then only did a **md5sum** before I made a live USB which worked as it should.

I've used torrents three times so far and all of them gave me satisfactory results (matching md5sums and functional live USBs.)

I did not check the integrity.

Well thats a great plug for torrents. They have a come a long way. Perhaps I can only point at my own personal experience and re-specify that when I used torrents I was operating under the Windows xP system.   I am not saying that chances for a corrupt .iso copy are likley while using Windows XP. I'm just pointing to my own experience from my locale.

 And just a side note. I have always been willing to download from an alternate site just to eliminate the chance (or greatly reduce it) of a bad copy.  Less downtime really , IMHO.

---

### Post by el_koraco on 2011-10-15
> **ventrical said:**
> Well thats a great plug for torrents. They have a come a long way. Perhaps I can only point at my own personal experience and re-specify that when I used torrents I was operating under the Windows xP system.   I am not saying that chances for a corrupt .iso copy are likley while using Windows XP. I'm just pointing to my own experience from my locale.

 And just a side note. I have always been willing to download from an alternate site just to eliminate the chance (or greatly reduce it) of a bad copy.  Less downtime really , IMHO.

out of all the distros I've used, I think I've used the download link from websites only two or three times, the others were torrents. Never had a problem with a torrent download, though I didget a corrupt Maverick iso from ubuntu.com.

---

### Post by ventrical on 2011-10-15
Then there must be some real hard-core compatability problems with lots of pcs out there, obsoleted hardware and the likes.  So if ya don't got the 3D graphics - forget Unity then!

sort of reminds me of that Pink Floyd line -"If ya don't eat your meat ya can't have any pudding -- how can ya have any pudding if ya don't eat your meat?"  lol  :)

---

