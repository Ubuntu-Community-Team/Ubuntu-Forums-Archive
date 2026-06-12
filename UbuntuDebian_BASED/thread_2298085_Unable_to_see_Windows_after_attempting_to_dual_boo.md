---
title: "Unable to see Windows after attempting to dual boot with Elementary OS"
date: 2015-10-08
forum: Ubuntu/Debian BASED
---

### Post by newguyjo on 2015-10-08
Ok, so i'm super new and don't really have any business doing this but i wanted to try out elementary OS after stumbling across it somewhere. 

My work laptop is a Lenovo Thinkpad Carbon X1 that had Windows 7 running on it. I made a bootable thumbdrive with elementary os, changed the BIOS so it would boot from the flash drive, chose to try elementary OS without installing. Everything seemed to work fine so i tried to install it. 

The only options i was given were to either erase everything and install EOS or do the 'something else' option which seemed to be to manually pick partitions and such. In that option it appeared that the drive was one really small partition and one really large one taking up the rest of the drive. Also, they were both marked as "unknown"....as in it didn't seem to recognize the exhisting OS as windows. I have no idea why this is.
 
Anyway, I left the installation process and got out of the thumbdrive and back into the windows installation already present and still working quite well despite the fact the linux OS didn't recognize it as such. In Windows i used the disk utility to shrink the windows partition down so there was some free space. Then i went back into the flash drive and tried installing agian. This time it still didn't recognize the windows partition but did see there was existing free space. I broke this into a root, swap and home chunks based on some instructions found on "it's F.O.S.S." and then installed. 

This seemed to work great as next thing i know i'm booting intio EOS without trouble and everything is working great. The problem came when i went to restart and see if Windows was still ok....but i ended up right back in EOS. It's like windows isn't even there. Using the 'fdisk -l' command seemed to show the partition where windows is/was as still present so i suspect it actually is still there. But I don't get any option on reboot to choose EOS vs. windows. 

I tried Boot Repair and ran the "recommended repair". Upon reboot this presented me with the option menu to choose what to boot into but the only options were to boot into elementary OS or elementary OS with special options, or something like that.  I'm afraid to go into any "advanced options" in Boot Repair because i don't want to screw anything up worse. If i can't get this figured out i'm likely going to be in trouble with the IT dude at work. I'm hoping someone here will be able to help me out.

Do i need to do the thing where i make a small /boot partition at the beginning of the disk? Is there a way to repair the windows bootloader if that's the problem? Why doesn't linux/elementary OS recognize the windows partition as windows?

Any help would be GREATLY appreciated!!!

Also, here's the Boot Repair output website thing:
[http://paste2.org/k2nL6fsO](http://paste2.org/k2nL6fsO)

Thanks in advance!!
jake

---

### Post by QIII on 2015-10-08
*Moved to **Ubuntu/Debian BASED***

---

