---
title: "Final help before install"
date: 2005-05-01
forum: Repositories &amp; Backports
---

### Post by necorium on 2005-05-01
ok at the end of the week i'm formatting my pc and installing linux for the first time.  \\:D/  i want to install windows and linux (need to install xpee for family). what would be the best way to do this? i was thinking i should install windows first onto a c:\ partition of 100gigs. after installing windows i'll install ubuntu onto d:\ partition of 20 gigs. would this be the best way to do this? i don't want to have problems. 

also at the end of the linux install will it give me some option to add a dual boot at the start of my computer? i don't want any one operating system take over.

please if u can think of any pointers for me while while doing this that would be great. I've reformatted and installed windows a zillion times but i've never even used linux. looking foward to your replies.

(oh yeah i'm gonna totally reformat my pc before and with windows i'll make two partitions. then i'll boot up linux install and reformat the d:\ is that gonna work or how should i handle the initital reformatting)

sorry if this is in the wrong thread but i couldn't figure out which one to post in.

---

### Post by Bob D. on 2005-05-01
> ok at the end of the week i'm formatting my pc and installing linux for the first time. \\[img]images/smilies/icon_biggrin.gif[/img]/ i want to install windows and linux (need to install xpee for family). what would be the best way to do this? i was thinking i should install windows first onto a c:\ partition of 100gigs. after installing windows i'll install ubuntu onto d:\ partition of 20 gigs. would this be the best way to do this? i don't want to have problems Yes, install Windows first, then Ubuntu. You don't need to create a second partition at this time for Ubuntu. Just install Windows into the size of partition you desire. When you go to install Ubuntu, at the partition formatting step you'll have an option to just use all the unallocated space to install Ubuntu. select that chioce and the remainder of your HD space will be used by Ubuntu.

> also at the end of the linux install will it give me some option to add a dual boot at the start of my computer? i don't want any one operating system take over. Yes, you will be presented an option for a dual-boot. If you install Windows first, Ubuntu will detect it and offer to install the boot loader (Grub) into the MBR (Master Boot Record). Accept this choice and you'll be good. When you boot, the Grub screen will appear at a point and you have (default) 10 seconds to pick another OS. If you use the arrow keys on the keyboard, you can arrow down to Windows, press Enter, and Windows will boot.

> (oh yeah i'm gonna totally reformat my pc before and with windows i'll make two partitions. then i'll boot up linux install and reformat the d:\ is that gonna work or how should i handle the initital reformatting) Really not necessary, as noted above. Just make your Windows partition and leave the rest unallocated. Ubuntu's installer will take care of the rest.

I'm assuming you have only one hard drive. I prefer to place the /home directory onto a separate drive from the '/'. It's just a preference I have...I do the same thing on XP. All my photos, documents, etc. are separate from the OS. That's about the only tip I've got. Other, more knowledgeable users may have some other advice.

Good luck! Of course post back if anything doesn't work quite right and let us know how it goes.

Bob

---

### Post by necorium on 2005-05-01
i need a lot of space for windows - couldn't that make my windows partition too small

---

### Post by Bob D. on 2005-05-01
Not following your question.

You stated you were going to make your Windows partition 100GB. You stated you were going to make your Ubuntu partition 20GB. I assumed (since you didn't say) that your hard drive is 120GB.

Ubuntu doesn't _install_ into the Windows file system (FAT32, NTFS, etc.) or use the Windows partition naming convention (C:/, D:/, etc.). Ubuntu doesn't use a 'D:' partition; Ubuntu will by default install into a partition named '/' (root) formatted to the ext3 file system. Windows cannot see nor use any of this space. Ubuntu can read Windows NTFS and read/write to Windows FAT32 partitions.

If your drive is larger than 120GB, make your 100GB Windows partition. When you install Ubuntu, you'll need to go to the manual partitioning section and manually make your Ubuntu 20GB partition. You can then leave the rest unallocated.

OR

You can make your Windows partition as big as you like, make as many Windows partitions as you wish, and in what ever unallocated space is left over install Ubuntu into that. Just do the Windows stuff first, then install Ubuntu.

The choice, as they say, is up to you! :)

Bob

---

### Post by necorium on 2005-05-01
thanks  ;-)  will let you know how it goes

---

