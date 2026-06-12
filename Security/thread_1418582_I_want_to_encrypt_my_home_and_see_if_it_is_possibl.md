---
title: "I want to encrypt my /home and see if it is possible to encrypt the whole hdd"
date: 2010-02-28
forum: Security
---

### Post by lmicu on 2010-02-28
I am looking at a possibility to encrypt my home director on Karmic. I am not sure how this is done on an existing installation and I did not find any relevant guides to do it.

Did anybody do this in the past, is it working, any prompts for passwords, any lack in speed or boot?

Thanks,

---

### Post by bodhi.zazen on 2010-02-28
I would simply use LUKS post install for an encrypted data partition.

The default for home is ecryptfs

[http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/)

see the link above for instructions on how to do this post install.

---

### Post by cham93086 on 2010-03-01
There are two options I can think of:

1) The standard live CD comes with an option to encrypt your home directory.  This is the option I currently use.  This option requires you log in as normal; it's completely seamless, with no noticeable speed reduction (for me.)
[INDENT]1) Back up your home directory, including hidden files
2) Do a fresh install, and select the encrypted folder option
3) Restore your old settings and documents by just recopying your backup into your home directory.[/INDENT]
I've found this method to be the easiest and least painful, and also what I currently use. It provides an excelent barrier against accidental or "accidental" snooping, and some hooligan that steals your laptop; someone very very motivated AND very well equipped can still get to your data.

2)The alternate install CD comes with an option for a fully encrypted install. This requires you enter 2 passwords, once pre-boot, and again to login.  There is an increase in boot time (it took me an extra 30 seconds?) But once loaded, there is no noticeable speed change.  It's my understanding a fresh install is also required. When I changed over, (I've subsequently changed to option 1 listed above) I backed up my ENTIRE home directory, used the alternate install CD, then restored all my settings and data from my backup.  Be forewarned: I tried to upgrade from Jaunty to Karmic, while using a fully encrypted HD and it got VERY ugly, I had to wipe and start over.  The disclaimer here is the same.  This gives excellent protection from neighborhood hooligans, and people at the coffee shop, however, if the government wants to throw their weight around, they are going to be able to look at it. It will just take a while.  

The question to ask is what are you trying to protect and from whom? If your looking for total protection of your data, don't let your computer onto the Internet, and don't take it out of your house.  More realistically, the first option is probably more than sufficient, so long as you are religious about locking your system when you walk away from it at the coffee shop.  Remember in either case, once your computer is booted, and not locked, any data is accessible. When it's shut down its relatively safe.

---

### Post by tubbygweilo on 2010-03-01
> **cham93086 said:**
> ...The question to ask is what are you trying to protect and from whom? If your looking for total protection of your data, don't let your computer onto the Internet, and don't take it out of your house.  More realistically, the first option is probably more than sufficient, so long as you are religious about locking your system when you walk away from it at the coffee shop.  Remember in either case, once your computer is booted, and not locked, any data is accessible. When it's shut down its relatively safe.

And standing answer [538]("http://xkcd.com/538/");)

---

### Post by Krovas on 2010-03-01
The XKCD take is amusing, but I still think total hard drive encryption is worth doing. This may help you:

[http://kuparinen.org/martti/comp/ubuntu/en/cryptolvm.html]("http://kuparinen.org/martti/comp/ubuntu/en/cryptolvm.html")

I looked into encrypting an existing install, and it's hideous. Just back up want you want, blank your drive, wipe it down, do a new encrypted install per the above instructions, put your stuff back and destroy the unencrypted backups. Piece of cake.

---

