---
title: "Ubuntu 20.04 Installer"
date: 2020-04-25
forum: The Cafe
---

### Post by pinus20 on 2020-04-25
**Ubuntu 20.04 Installer**

I just made a note in my calendar that the update was successfull and I don't need to reinstall. First the good part, if you have a very simple configuration it works fast and with only a few clicks. But if your setup is more complicate like you have two disks and want encryption or have an existing Windows you easily end with a broken installation or a destroyed windows.

Start with a two disk system, this works only if you don’t want encryption on one disk. The installer can’t set up a system with two encrypted drives! There are solutions to do that but not with the installer, see appendix. This isn’t appropriate these days, unencrypted disks should be an exception these days. I wonder what’s so complicated to use the same password for multiple disks? 
Painful details. The installer allows you to create a physical volume for encryption. After you’re done with it it tells you that you need an unencrypted boot partition. Simply annoying. And than it did not tell you how big this partition needs to be. Month later you get bitten, the update fails because the boot partition is to small for the number of kernels the update system installs into your system. Another point is that the installer allows you to configure multiple encrypted drives, leaving your system unbootable. 
If you change the files system you can easily end up with a broken system. If you choose BTRFS for your root mount point and don’t create a swap partition your swap is broken because the installer creates the swap file the wrong way. There are also solutions to do that, see appendix. I haven’t tried all the other file systems but doubt that they work better. Don’t get me wrong BTRFS is a great file system that has the features you want on the desktop, e.g. compression and snapshots. If Ubuntu is not able to create the swap files with the proper attributes they should at least warn if you select them for the root partition.

Creating a dual boot system with Windows it’s a challenge by itself. If you’re able to reinstall Windows on a smaller partition you save yourself the day. Make sure you know about Bitlocker, BIOS date and fast start. There are some articles on the net that describe how to set up such a system. But don’t expect it to be easy. The installer doesn’t care much on the challenge.

The installer didn’t develop for years. If you go for the something else option you have a great chance to mess up your system. What bugs me most is that the installer lets you walk straight into the trap in so many ways. The much I like the work on the desktop Ubuntu did, the much I dislike the installer.  
[B]
Appendix[/B]
[LIST]
[*]Use multiple encrypted disks 
[/LIST]
[INDENT]The details are beyond this text. The basic idea is to let the installer create an encrypted root and mount the other drives during boot using keys on the root partition. Since LUKS supports multiple keys it makes sense to use two keys, the human readable key and a random file on the disk.
[/INDENT]

[LIST]
[*]Create swap file on BTRFS 
[/LIST]
[INDENT]touch swapfile
chattr +C swapfile 
fallocate --length 32GiB swapfile
sudo chown root swapfile 
sudo chmod 600 swapfile 
sudo mkswap swapfile 
sudo swapon swapfile
[/INDENT]

---

### Post by grahammechanical on 2020-04-25
> 
Creating a dual boot system with Windows it&#8217;s a challenge by itself. If  you&#8217;re able to reinstall Windows on a smaller partition you save  yourself the day. Make sure you know about Bitlocker, BIOS date and fast  start. There are some articles on the net that describe how to set up  such a system. But don&#8217;t expect it to be easy. The installer doesn&#8217;t  care much on the challenge.

You are forgetting something. It is called Microsoft. There is a reason for long term Linux developers calling that company the Evil Empire. I have no desire to stir up best forgotten hatreds but Microsoft has got as big as has and as rich has it has by doing everything it can to be a monopoly. Today Microsoft is playing a lot nicer with Linux developers but do not think that the people running that company will make it easy to dual boot with Linux. Or for retailers to offer Linux as an alternative OS. This is business after all.

Regards

---

