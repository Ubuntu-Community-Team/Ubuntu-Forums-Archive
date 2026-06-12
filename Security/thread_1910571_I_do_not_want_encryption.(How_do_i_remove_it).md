---
title: "I do not want encryption.(How do i remove it?)"
date: 2012-01-17
forum: Security
---

### Post by Vik Vasilev on 2012-01-17
I installed a clean version of ubuntu 11.04 a few months ago,and i clicked "encrypt my home folder" not knowing that this is going to cause complications. Now I want it removed and there is NO OPTION FOR THAT. -.-
I do not want my hard disk to be encrypted - my swap isnt getting mounted for some reason (and i blame the encryption for that), and my hard disk is running slower.
How do I remove the encryption Without removing or changing anything to my system? 
I dont have where to backup my data.

---

### Post by gsgleason on 2012-01-17
Encryption is of course going to slow things down, but I don't see how that related to your swap not working.

Do you want to fix your swap, or remove encryption?

---

### Post by Vik Vasilev on 2012-01-18
I want to remove the encryption first, and i`ll see what I can do about it after that.

While the system boots i sometimes get a message saying "cryptswap not detected, missing, press S to skip waiting" or something like that, and thats why I blame the encryption for that.

---

### Post by sh4d0w808 on 2012-01-18
Theoretically, your home's encryption doesn't affect other parts of your system - nor your swap area.

Swap is absolutely a different part on your harddisk.

Quote from askubuntu:

"Not to bring up an old thread but in case anyone has errors trying to follow these instructions, here is what I did.

Backup the home directory while you are logged in sudo cp -rp /home/user /home/user.backup. Check that your home backup has everything!!!
reboot into root via grub
Delete your home directory rm -rf /home/user
Remove the packages apt-get remove ecryptfs-utils libecryptfs0
Restore your home directory mv /home/user.backup /home/user
reboot
Remove any of those .Private .ecryptfs folders rm -rf ~/.Private rm -rf ~/.ecryptfs
Yay!
This worked for me. Home folder file permissions stay intact and does not bugger up Dropbox or git repos. Some reason my fresh install on Ubuntu 9.10 would not do the first command. Just make sure you think the process through when using rm -rf.

Just wanted to post this not only for my record, but anyone else who encounters problems.

Some notes:

"reboot into root via grub" was a bit unclear to me; I didn't reboot, just switched to using root (another user account with sudo privileges would work equally well).
Before removing the packages ecryptfs-utils and libecryptfs0 would work, I needed to remove /home/.ecryptfs/<myusername>. (It complained that ecryptfs-utils was in use.)"

I think there is no other way, only with more pain in ***.

---

### Post by Vik Vasilev on 2012-01-19
Isnt there a way to decrypt it without having to backup it to another place?: ( I have an 80gb hard disk and my home contains 75gb of music and photos i have collected for like 5-6 years....
Whatever. I`ll try by moving it to an unencrypted user. Thanks anyway.

---

### Post by Dry Lips on 2012-01-19
I had the exact same problem as you some months ago. Removing you encryption isn't easy, but it is possible. (See post #2 in the thread below). I ended up backing up my data and deleting the encrypted partition. All in all that was the easiest solution for me, but if backup is not possible, try to follow the tutorials bodhizazen provided.

[http://ubuntuforums.org/showthread.php?t=1703551](http://ubuntuforums.org/showthread.php?t=1703551)

---

### Post by Vik Vasilev on 2012-01-20
Thank you all, I guess i`ll  have to wait untill I can by one more 80gb hard disk :popcorn:

---

### Post by Dave_L on 2012-01-21
> **Vik Vasilev said:**
> ...I have an 80gb hard disk and my home contains 75gb of music and photos i have collected for like 5-6 years...

You don't have a backup of data you been collecting for several years?

---

### Post by Vik Vasilev on 2012-01-25
Nope. I know its dumb, but I have only one computer and my disk drive doesnt write cds anymore -.-

---

