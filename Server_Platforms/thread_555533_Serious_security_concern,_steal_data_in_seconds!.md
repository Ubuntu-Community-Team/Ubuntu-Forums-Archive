---
title: "Serious security concern, steal data in seconds!"
date: 2007-09-20
forum: Server Platforms
---

### Post by TitanKing on 2007-09-20
I have noted, I never realized this before in my life, how easy someone can boot into your machine as root, steal your data and break your system.

The user will need physical access, which is not that hard!

By using this simple guide he can boot in as root, change the password and bootup stealing and breaking data:

Here is how:

1. Turn your computer on.
2. Press ESC at the grub prompt.
3. Press e for edit.
4. Highlight the line that begins kernel ........., press e
5. Go to the very end of the line, add "rw init=/bin/bash"
6. press enter, then press b to boot your system.
7. Your system will boot up to a passwordless root shell.

Is there no way to prevent this from happening? This is really serious, I know people who carry around notebooks with Ubuntu on it with very sensitive data, and I assured them that there data is protected, which is obviously not the case at all!

Regards.

---

### Post by buzzmandt on 2007-09-20
this might help
[http://ubuntuforums.org/showthread.php?t=7353&highlight=password+grub](http://ubuntuforums.org/showthread.php?t=7353&highlight=password+grub)

---

### Post by fnjordy on 2007-09-20
> **TitanKing said:**
> 
Is there no way to prevent this from happening? This is really serious, I know people who carry around notebooks with Ubuntu on it with very sensitive data, and I assured them that there data is protected, which is obviously not the case at all!

This is the same with every operating system, you can also use a Ubuntu live CD to gain access.

The only solution is to encrypt everything, there's a starter in the wiki, note the warning though:

[https://help.ubuntu.com/community/FullDiskEncryptionHowto](https://help.ubuntu.com/community/FullDiskEncryptionHowto)

---

### Post by zekica on 2007-09-20
You can always run any Linux Live CD with ntfs-3g installed and access data in Windows partitions. Or you can insert Mac OS X install DVD and access data from the installed system.

You can't protect data on your HDD if it is not encrypted. I hope that other answers are going to help you.

---

### Post by TitanKing on 2007-09-20
Thanks for the reply guys, I will look into a encryption solution...

---

### Post by joewilliams on 2007-09-20
Isn't there a boot password option in bios on most laptops? Doesn't this password "happen" before grub gets going?


....me going to check bios on my laptop....

---

### Post by MJN on 2007-09-20
Most BIOS passwords are useless against all but the most casual crackers (Google 'reset bios password' for a multitude of methods). As already mentioned by fnjordy if there's physical access then the game is over in the majority of cases - encryption is the way out.
 
Mathew

---

### Post by bodhi.zazen on 2007-09-20
Physical access = bad news. Encryption is helpful BUT it is by no means foolproof and can be cracked as well.

With this said, encryption can be helpful.

Check out this link : [http://www.hermann-uwe.de/blog/towards-a-moderately-paranoid-debian-laptop-setup--part-1-base-system](http://www.hermann-uwe.de/blog/towards-a-moderately-paranoid-debian-laptop-setup--part-1-base-system)

---

### Post by Xbehave on 2007-09-20
if you configure your bios to only boot of your HD then password protect your bios this covers most attacks, 
For more security encrypt your HD (however this can be abit of a pain as it prompts you for your password on boot)


and for remote security you may wont to look at 
pax ( 60% safer)
selinux ( not sure but 99% safe IMO)

---

### Post by lisati on 2007-09-20
The only sure-fire method I know of to keep a computer secure is one which works with all hardware platforms and all OSes. 

The basic idea is to completely disconnect it from the real world (including disconnecting power supplies, routers, modems, wifi cards), putting in a deep hole in the back yard, and filling the hole with concrete.

The downside to this kind of approach, however, is that it makes it difficult for legitimate users to access the machine's capabilities.

---

