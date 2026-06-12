---
title: "Need help! TrueCrypt volume is no longer bootable!"
date: 2010-07-16
forum: Security
---

### Post by Zhangcamilo on 2010-07-16
Hello every one at Ubuntu Forums,

I have a severe problem,

I installed TrueCrypt in Microsoft Windows XP SP3 (no Linux installations present) and I stopped the TrueCrypt service in the Windows enviroment, and then, I restarted, and all the sudden it seemed the PC can not see the Hard Disk at all at startup, nada... I believe I dismounted it by stopping the TrueCrypt service...

So the PC no longer understands there is a TrueCrypt volume in place, and I inserted the TrueCrypt recovery disk, and it can not do any thing, I restored the bootloaders, the true crypt loader, and once I finished this, I press ESC, and it says there are no bootable devices, so nothing. I even decrypted the disk, and it seemed that nothing happened with the restore disk...

Is there any way I can make this partition bootable again? because I have every thing in that partition, every single bit of life...

I have used TestDisk under Linux right now, but I am unsure of this, and I also further complicated the boot proccess, and now the PC states at startup about missing partition tables.

When I start truecrypt from this Kubuntu live CD, I am unable to see the encrypted hard disk even with root, there is no way to see this hard disk, only can be seen in the TestDisk app.

Can some please help? I really I am desperate, at least, if I can not make Windows Boot again, maybe just suck all the files out of the hard disk and put them some where for now, I really need to get back to work, and I cant seem to find a solution...

I know here at Ubuntu forums, some one may have the solution.
And I do know for sure all the files on this volume are there because of the TestDisk app, so they are there, they are just not reachable....

(I have posted this problem on a Linux forums instead of a Windows forum because the only way to try to recover the volume is with Linux Kubuntu Live CD, so I am very sorry if it seems a little out of the topic, but I need the help, thank you...)

---

### Post by WinstonChurchill on 2010-07-18
Your post is not very clear... If by "Installed TrueCrypt" you mean that you fully-encrypted your Windows system disk, then stopping the TrueCrypt system service would not cause the issues you're talking about - TrueCrypt functions through a kernel-mode driver. When you say that "the PC can not see the Hard Disk at all at startup", do you mean you're getting the INACCESSIBLE_BOOT_DEVICE 0x7B blue-screen-of-death error? Remember that with TrueCrypt, the entire disk is encrypted - if you're seeing any sort of Windows BSOD error at all, that means that the encryption/decryption is working, and TrueCrypt isn't the problem. 

If, as you say, you decrypted the system disk in-place with your rescue CD (this would take at least several hours, and even days depending on the size of your hard drive), you should be able to read the filesystem with a Ubuntu/Kubuntu live CD. Ubuntu is really more user-friendly; burn an Ubuntu Live CD and try that. Look at the disk with gparted and see whether or not it recognizes the filesystem.

You mention an "Invalid partition table" error, but if that was the case, I don't think TestDisk would be able to see any of your files. BIOS error messages are oftentimes stupidly unclear - that could be your BIOS way of saying it can't boot. If your MBR/partition table has actually been messed up (this part of the disk isn't encrypted by TrueCrypt), you just might be out of luck. Weigh the value of your data against the value of your time spent trying to recover it; it probably isn't worth it. If I was you, I'd nuke it, reinstall Windows (or better yet, Ubuntu!) and get on with life.

---

### Post by rookcifer on 2010-07-18
You would be better off posting this query to the Truecrypt forums since Truecrypt is not really something most Linux distros support (because of its wacky licensing).  [http://forums.truecrypt.org/](http://forums.truecrypt.org/)

---

