---
title: "File Server Build"
date: 2011-02-11
forum: Server Platforms
---

### Post by vaf on 2011-02-11
Hi all

I have been trying to find some recommendations for a file server build. I am looking at the following setup for a small office running Windows 7 desktops, pretty much just needing file sharing.

I have built a few (about 4) Ubuntu Server 9.04 boxes that work well, but I'd like to try to use 10.04 (or 10.10 if you think I should!)

CPU:  Intel G6950
MB:   Intel DQ57TM
RAM:  Corsair 2GB DDR3
HDD:  4 x WD RE4 1TBin RAID 10 (or would RAID 5 be better?)
CASE: Fractal Design R3
PSU:  ANTEC EA-650W

Main focus is stability and reliability.

Any comment/advice is welcome.

Thanks

---

### Post by YesWeCan on 2011-02-11
Hi,
I am running a similar server. Like you, stability and reliability are my priorities. That is why I also bought an Intel mobo, the DH55HC, on which I am running 10.04.1 server 64-bit.
I cannot comment on 10.10 as I have not used it but 10.04 is a long term support version so I have no incentive to upgrade.

I think 2GB is the minimum RAM I would use. I think 10.04 is a little more demanding than 9.04 but if you find 9.04 plenty fast then no more RAM is needed.

I am also using a four 1TB disk RAID10 (WD Caviar Black). I am using mdadm software RAID. With my priorities I would never use RAID5 for anything. With only 4 disks RAID6 is ok (not for larger arrays though) and by my own statistical analysis you are a little more likely to recover your array in the event of a disk failure (both over 90%), but you still only get 50% capacity efficiency. I prefer RAID10 because it is simpler and in the event of an array failure I think I am more likely to get my data back some other way. RAID10 is faster on writing and much faster to rebuild. My feeling is that a good quality hardware RAID controller would be more reliable than software RAID.

Hope that helps.

---

### Post by elico on 2011-02-11
a 650W PSU is not something you need. 400W will be more than you need.
in this kind of system size and disk almost any hardware raid card will be better.
it might will cost money but you will be more that satisfied in any case that you will have any problem with the array.
raid 10 has far more reliability but it depend on the sensitivity of the data for the client.
1 TB if information for small server is very big.

---

### Post by aeiah on 2011-02-11
> **YesWeCan said:**
> Hi,
My feeling is that a good quality hardware RAID controller would be more reliable than software RAID.



im no expert in the matter, but i was always under the impression that the advantage of software raid is that its easy to rescueue when things go wrong. with hardware raid, you have to make sure the computer you're using to rescue things with has the same hardware raid controller as your fileserver. if you use software raid you could just plug in two of the disks (even via external usb enclosures) and grab the data off them.

hardware raid does perform better, but if we're talking about a small office i dont think you need to worry too much.

you'd want to investigate this properly though like i said.

---

### Post by aeiah on 2011-02-11
but yes, your specs are fine. you're only serving data anyway. just go with ubuntu server 10.04 (since its a long term support release) and you should have the option at install time to set it as a samba server.

you might want to consider a 5th hard drive just for the OS (just a small 80GB HDD), then put the 4x1TB in a raid 10. when finished, take a copy of the entire operating system hard drive image (should only be a few gigs). id actually put an image of the os hard drive on a new hdd and just keep it handy. others would perhaps use 2x80GB for the OS in a raid 1.

---

### Post by iissmart on 2011-02-11
If you plan on slowly adding more hard drives to the RAID, do RAID5 because you can add one drive at a time. In RAID10 you have to add two at a time. At only four drives performance will be the same between RAID5 and RAID10. If you're thinking long term, I would recommend RAID6.

---

### Post by YesWeCan on 2011-02-11
> **aeiah said:**
> im no expert in the matter, but i was always under the impression that the advantage of software raid is that its easy to rescueue when things go wrong. with hardware raid, you have to make sure the computer you're using to rescue things with has the same hardware raid controller as your fileserver. if you use software raid you could just plug in two of the disks (even via external usb enclosures) and grab the data off them.
I agree with you. Or at least, I believe, you have to use the same type of RAID card. And software RAID is much cheaper. I am not yet familiar enough with how mdadm performs in various error conditions. I am trying to learn more about it. I haven't found a manual yet. ;)

---

### Post by KeLa on 2011-02-11
I have used this kind of setup_
2 disks raid1 for os
5 or more disks in raid5 for file share (it's fast enough for file share)
That way you have fast and mirrored os partitions and reliable file share partitions.

---

### Post by arrrghhh on 2011-02-11
> **YesWeCan said:**
> I haven't found a manual yet. ;)

[mdadm MAN page](http://www.linuxmanpages.com/man8/mdadm.8.php)

---

### Post by YesWeCan on 2011-02-11
> **arrrghhh said:**
> [mdadm MAN page](http://www.linuxmanpages.com/man8/mdadm.8.php)
Ya, right. :P

---

### Post by Butterfly_Monk on 2011-02-12
I'm trying to do the same thing., set up a server with 4 2TB drives just for music, movies & pics but when I install Lucid server edtion it comes up with a dos like screen. I'm sick of windows & I've spent hours reading about this stuff but none of it is straight forward. I try to set up a RAID system but there are so many options.

I just wanna secure my data if the OS fails.

---

### Post by YesWeCan on 2011-02-12
The server version of Ubuntu has no GUI. You can add it using 'sudo apt-get install ubuntu-desktop'.
There isn't really much different between server and desktop versions: [https://help.ubuntu.com/10.04/serverguide/C/preparing-to-install.html](https://help.ubuntu.com/10.04/serverguide/C/preparing-to-install.html)

I would like to see proper documentation of linux in general. Canonical have made a good start and the Community pages are good. The "man pages" are pretty much command syntax references for those who already know how to use the commands; and their presentation seems to be stuck in the 1970s.

---

