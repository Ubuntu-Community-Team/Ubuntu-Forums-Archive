---
title: "Recover password if most of it is known"
date: 2013-04-22
forum: Security
---

### Post by proyt on 2013-04-22
Hi guys,

So, last week, I spilled soda on my computer and the keyboard stopped working. I attached an external keyboard and it was fine, including logging into Ubuntu. A day later, I went to log in, and it would not accept my password. Tried to reboot and computer had some sort of hardware failure. 

I have a new computer and transferred my old drive to an external enclosure. I'm trying to run ecryptfs-recover-private to recover the old encrypted home folder, but again, my password is not accepted. You would really help me out if you could take a look at these two possibilities:

1) What I'm thinking is that, even though I've entered the password a  thousand times, it's long and complicated, so maybe I'm off by a letter or two or the case.  Is there any program/strategy wherein I can enter what I might "think"  the password is and the program can use that as an algorithm? At best, limiting the length and possible characters? John the Ripper might be able to do this, but the instructions for doing so are highly inconsistent in Google searches.

2) Is it more likely that my file system became corrupted by the spill? If that's the case, I have no idea what that would do to my password file and thus would make recovery extremely difficult or impossible. When I plug in the old hard drive, it's directory structure looks fine and I'm able to read non-encrypted data, so not sure this is the case. I do have a shadow and passwd backup file from a fresh install on that system, if this helps.

Any advice would be greatly appreciated. I'd really like to get back some of the files I didn't have backed up.
Thanks!

---

### Post by Stonecold1995 on 2013-05-04
I think password cracking software such as HashCat has the ability to test permutations of a string.

I don't think password cracking is supported on this forum though.  You'll probably have a lot more luck asking at the HashCat forums or forums specific to this topic.

---

