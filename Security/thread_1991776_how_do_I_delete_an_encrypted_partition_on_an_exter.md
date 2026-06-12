---
title: "how do I delete an encrypted partition on an external harddrive?"
date: 2012-05-30
forum: Security
---

### Post by captainIDK on 2012-05-30
I wanted to encrypt my external hard drive to protect my information in the event it was seized. I'm a nub so I used disk utility to add an encryption to my external hdd. It worked, but when I tried to open the encrypted hdd on my windows 7 laptop there were incompatibility issues. I didn't know what was going to happen I just went for it and wanted to see what would happen. At first I thought the reason my PC couldn't open the hdd was because I used a file type that wasn't compatible with windows. Which encouraged me to post in this forum. 

I think I have some misconceptions about what I was trying to do.

Here are my questions:

1) Is ubuntu encryption even compatible with windows? say I plug in an external hard drive that was encrypted using ubuntu 12.04 to a windows 7 PC will I get a nice little dialog box that lets my type in my password?

2) Say I created an encrypted partition not knowing that I couldn't remove it and then wanted to change the file type so I added another partition with the file type I thought would work with windows 7. So I have a encrypted partition within an encrypted partition and then an NTFS file type on my external Hard drive. Is it possible to remove the encrypted partitions-leaving a blank unformatted external hdd- and create a new partition with an encryption that is compatible with windows 7?

3) say I get the chance to go back to square one and create a new encrypted partition on my external hdd. what would be the best procedure to follow to make it an encrypted hdd that can go back and forth between ubuntu 12.04 and windows 7?

---

### Post by wilee-nilee on 2012-05-30
Gparted in Ubuntu will delete it, as far a dual OS use I think you can set-up truecrypt to do it, you will have to look though.

Per the commonly asked questions.

> Can I mount my TrueCrypt volume  under Windows, Mac OS X, and Linux? 

> Yes, TrueCrypt volumes are fully cross-platform.

---

### Post by captainIDK on 2012-05-31
I reformatted my external hard drive using my windows computer. It was easy and from what I can tell it worked.

---

