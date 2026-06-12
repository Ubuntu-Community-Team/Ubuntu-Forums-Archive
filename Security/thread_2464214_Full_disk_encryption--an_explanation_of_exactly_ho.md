---
title: "Full disk encryption--an explanation of exactly how does it work from the user's end?"
date: 2021-06-26
forum: Security
---

### Post by StewartM on 2021-06-26
All,

I'm posting this because I've not been able to read how the full-disk encryption option actually works.   I don't want an explanation of how AES works, not an explanation of how to install it; there oodles of those.   I want to know how it works in practice and how secure it is (and what I meant by that is not "how AES is implemented" but what it does and does not do in practice).   I've been a Linux user for 13 years, I've been using Ecryptfs for most of that period, and I've used Scramdisk/TrueCrypt/Veracrypt, for my background.  Plus I've actually done an installation with the full-disk encryption option for someone else.  I just don't know how it "works".

And what do I mean by "how it works??

Is the same key used system-wide?  This is my biggest question.  That means:

1) If I log in as User1 on a full-disk encrypted system, and I have sudo privileges, can I "spy" into the contents of User2's and User3's account if I choose?  With Encryptfs, you can't--because those are encrypted with different keys.  Or do I have a separate key that can only decrypt my own /home folder + the filesystem and /boot folders?

2) If all user accounts are encrypted with separate keys, are these linked to the filesystem decryption key?  (Ergo, at the boot screen you can enter your /home user key, then again at the user login screen, as your home user key is linked to the filesystem key---it decrypts only the filesystem plus your own /home user directory, nothing else.  That would escape the need for multiple users having to share the master filesystem key for the whole system).

3) Is /swap encrypted with the same key as the filesystem? If it is a separate key, is it a permanent key? In Encryptfs the swap key is temporary, once the system is shut down the key is destroyed and another key is generated upon boot, which makes whatever was written to swap the previous session irretrievable.  

If /swap is encrypted with its own temporary, separate, key, is this true irregardless whether or not /swap is on a partition or is a swap file? (I've heard of people recommending using swapfiles as a workaround on Ubuntu's policies on auto-creating swap space on installs using full-disk encryption, which don't give you any partitioning options out of the box, and which generate ridiculously small swap spaces (on an install of Bodhi Linux, an Ubuntu derivative, i was doing on a friend's laptop that had only 2 GB of RAM, it only auto-created 1 GB of swap--and I'd think you'd need at least 2, better 4 for such a limited machine.  Ubuntu used to create 2:1 swap:RAM spaces by default, but not anymore). 

Thanks for any responses.

StewartM

---

### Post by CharlesA on 2021-06-26
> **StewartM said:**
> 
Is the same key used system-wide?  This is my biggest question.  That means:

1) If I log in as User1 on a full-disk encrypted system, and I have sudo privileges, can I "spy" into the contents of User2's and User3's account if I choose?  With Encryptfs, you can't--because those are encrypted with different keys.  Or do I have a separate key that can only decrypt my own /home folder + the filesystem and /boot folders?

It depends on the type of encryption used. I usually use LUKS to do full disk encryption and once the drive is unencrypted and mounted, any user with access can view whatever files they want to. This may be different from encrypfs or the other methods though. I speak of Full Disk Encryption from a server standpoint rather than a desktop or workstation standpoint, though.

> **StewartM said:**
> 
2) If all user accounts are encrypted with separate keys, are these linked to the filesystem decryption key?  (Ergo, at the boot screen you can enter your /home user key, then again at the user login screen, as your home user key is linked to the filesystem key---it decrypts only the filesystem plus your own /home user directory, nothing else.  That would escape the need for multiple users having to share the master filesystem key for the whole system).

I do not know the answer to the question at least in regards to LUKS, since it doesn't really have a "user" mode - it's all or nothing.

> **StewartM said:**
> 
3) Is /swap encrypted with the same key as the filesystem? If it is a separate key, is it a permanent key? In Encryptfs the swap key is temporary, once the system is shut down the key is destroyed and another key is generated upon boot, which makes whatever was written to swap the previous session irretrievable.  

If /swap is encrypted with its own temporary, separate, key, is this true irregardless whether or not /swap is on a partition or is a swap file? (I've heard of people recommending using swapfiles as a workaround on Ubuntu's policies on auto-creating swap space on installs using full-disk encryption, which don't give you any partitioning options out of the box, and which generate ridiculously small swap spaces (on an install of Bodhi Linux, an Ubuntu derivative, i was doing on a friend's laptop that had only 2 GB of RAM, it only auto-created 1 GB of swap--and I'd think you'd need at least 2, better 4 for such a limited machine.  Ubuntu used to create 2:1 swap:RAM spaces by default, but not anymore). 

Thanks for any responses.

StewartM

In my case with LUKS, The root device is encrypted with LUKS and then I've got LVM on top of it, so I'm technically using "encrypted swap" but my partition lives on the root device. It's using the same keys as the root device. Other implementations might be different as I've had this install running for quite a few years and I haven't felt like redoing everything.

Hopefully that helps, somehow.

---

### Post by StewartM on 2021-06-26
> I do not know the answer to the question at least in regards to LUKS, since it doesn't really have a "user" mode - it's all or nothing.

Why then is there a limitation on the number of user accounts with the default Ubuntu-based full-disk encryption?  (You can have up to 8).  

[https://superuser.com/questions/1593900/multi-user-full-disk-encryption-larger-than-8-user-threshold-i-e-not-luks](https://superuser.com/questions/1593900/multi-user-full-disk-encryption-larger-than-8-user-threshold-i-e-not-luks)

If you say is true (and this is the default installation) then this limitation makes no sense other than avoid having to implement a system of password sharing.  For if any sudo user can view/modfiy the other accounts just using sudo privileges, if a intruder can access just one of the user passwords combinations (the LUKS and the user account password) and if that user has sudo privileges then that intrusion compromises every user on the system, not just the hacked user.  Maybe I'm overlooking something or I'm misreading something, but that doesn't seem good. 

> In my case with LUKS, The root device is encrypted with LUKS and then I've got LVM on top of it, so I'm technically using "encrypted swap" but my partition lives on the root device. It's using the same keys as the root device

So with your system (is it the default installation?) the swap area is simply encrypted with the filesystem password, and thus access to the filesystem gives one the rights to examine swap.  If that's the default, it's not optimal; there is no reason to keep anything written in swap around, period, after a reboot.  

I think I recall looking at some of the installation options where it was possible to have the swap key regenerated anew on boot, which is the most desirable option, but I do not know if that is the default installation or not.

Thanks for the reply!

---

### Post by CharlesA on 2021-06-27
> **StewartM said:**
> Why then is there a limitation on the number of user accounts with the default Ubuntu-based full-disk encryption?  (You can have up to 8).  

[https://superuser.com/questions/1593900/multi-user-full-disk-encryption-larger-than-8-user-threshold-i-e-not-luks](https://superuser.com/questions/1593900/multi-user-full-disk-encryption-larger-than-8-user-threshold-i-e-not-luks)

If you say is true (and this is the default installation) then this limitation makes no sense other than avoid having to implement a system of password sharing.  For if any sudo user can view/modfiy the other accounts just using sudo privileges, if a intruder can access just one of the user passwords combinations (the LUKS and the user account password) and if that user has sudo privileges then that intrusion compromises every user on the system, not just the hacked user.  Maybe I'm overlooking something or I'm misreading something, but that doesn't seem good. 

What you call "users" here is not actual users - LUKS has a limit of 8 "key slots", which can contain anything from a key file, to a passphrase. This is the limitation the link you posted is referring to. It isn't a limit in the actual number of users on the system, but a limit on the number of passwords or keys you can use to unlock the encrypted drive. You can also remove and add other keys in the event one of the keys is compromised or needs to be rotated for whatever reason.

This might give you some more info on how that works: [https://www.thegeekstuff.com/2016/03/cryptsetup-lukskey/](https://www.thegeekstuff.com/2016/03/cryptsetup-lukskey/)


> **StewartM said:**
> 
So with your system (is it the default installation?) the swap area is simply encrypted with the filesystem password, and thus access to the filesystem gives one the rights to examine swap.  If that's the default, it's not optimal; there is no reason to keep anything written in swap around, period, after a reboot.  

I think I recall looking at some of the installation options where it was possible to have the swap key regenerated anew on boot, which is the most desirable option, but I do not know if that is the default installation or not.

Thanks for the reply!

I'm not really sure tbh. I checked and it looks like my root file system was created back in 2019 and I'm assuming that was when I reinstalled after my OS got hosed up.

I seem to remember setting this up manually because the default install set only 1GB for /boot and that only let me have one or two kernels installed before it ran out of space.

I also wanted the root LVM device and swap device to have better names than sda_whatever. My /boot/ partition is living on a USB flash drive, if that matters.

Have a read here:
[https://help.ubuntu.com/community/ManualFullSystemEncryption](https://help.ubuntu.com/community/ManualFullSystemEncryption)
[https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019](https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019)

---

### Post by TheFu on 2021-06-27
I'll take a stab at this ... again.  Had a system lock up just before submitting my prior post and I don't have the desire to re-write it all, but I drew a diagram to show partitions --> LUKS Containers --> LVM objects.  Hope this helps.

[ATTACH=CONFIG]288738[/ATTACH]

Often, an LV can be thought about as a smart partition, but that's an understatement.  LVs can be modified while the system is being used and while the file system is active.  That's huge.

---

### Post by CharlesA on 2021-06-27
> **TheFu said:**
> I'll take a stab at this ... again.  Had a system lock up just before submitting my prior post and I don't have the desire to re-write it all, but I drew a diagram to show partitions --> LUKS Containers --> LVM objects.  Hope this helps.


I just wanted to say that that is a great example image of how everything is nested.

As an aside, the forum software does so an auto saved in different intervals and if you've got text that was saved, there should be a "Restore Auto-Saved Content" button above the post icons section in the full editor.

Don't know if it helps or if you already knew about it, but I figured I would throw it out there any way.

---

### Post by StewartM on 2021-06-28
Charles A and The Fu,

What's I'm seeing and reading is:

1) Yes, you can have up to eight encryption keys (I knew already these were not necessarily tied to users; that's a feature I'd like, but it not provided).  It seems you can use these multiple keys to:

a) give users (to avoid passphrase sharing);
b) encrypt different partions (including swap, I suppose?)
c) you can add, reovke, and replace encryption keys

2) However, I don't see anyway that you can have each user have their own separate keys that *only* encrypt/decrypt their user directories.  You can have the entire /home directory on its own partition, but (unlike Encryptfs) all users who have accounts will use either one keys or separate keys that encrypt/decrypt all of /home, which would include not only the contents of their own user directories, but those of other users. This is something I regard as intrinsically inferior to the Encryptfs system, which does give users separate keys that only encrypt/decrypt their own /home user folders and not the accounts of others. 

I say this as although my computers are mostly single-user (me) systems, at times I have created accounts for others.  These people typically use weaker passphrases and even if I require them to use a strong, one, they will end up writing it down to remember it.  To my mind, this creates a security weakness that need not exist. 

3) I recall there was one install where the swap key was generated on boot but I can't find it. I suppose from what you gave me is that you could manually revoke and replace the swap partition key periodically to mimic this. 

What generated my asking these questions is that have received a new computer from a Linux vendor that has the full-disk encryption (with /home on a different physical drive).  I did this because Ubuntu deprecated Encryptfs and no longer offered it on installation (though one can always install it post-install).  However, other Linux distros, such as Linux Mint, still offer Encryptfs as an option on install (plus full-disk encryption). 

But I forgot to tell the vendor I wanted ext3 file system instead of ext4 because file wipers still largely work with the default mode of ext3. So I got ext4 which I want to get rid of (except for the boot drive; which is a SSD, where no file wiping works insofar as I understand it, so ext 4 is ok).  So I was thinking of reformatting the disk with my /home directory to get ext3.  Now I'm thinking about just going back to Ecryptfs, as it's still offered on Mint installs and I see it's a superior solution superior for /home and /swap to the full-disk encryption.  Thanks for both of your replies.

---

### Post by TheFu on 2021-06-28
>  b) encrypt different partions (including swap, I suppose?)
Each LUKS container will have different slots and methods used by those slots for decryption.  LUKS has a 2-phase encryption method.
There's the data part which is always encrypted and there's the LUKS header part which is what holds the decryption keys for the data.  By limiting access to the header to 8-slots, LUKS makes it so
1) excellent, random, encryption keys and salt us used for all the data, regardless of user input.
2) modifying a slot in the header access doesn't mandate re-re-re-encryption for all the data.
Smart, right?

As for 2) each user have their own separate keys, just setup different LUKS containers for each user.  Want to keep 5000 users with 5000 separate containers?  Go for it.  Always remember that with Unix systems, everything is just a file. That includes whole HDDs, partitions, or files.  We could make a 10G "file", then treat it like a partition, make it into a LUKS container and put a file system inside it or ZFS or LVM, if we prefer.

Trading a "feature" for poor security is something I prefer to avoid.  Encfs and EncryptFS have well documented security problems.

LUKS can use 2FA. I do it that way with a yubikey in challenge-response mode.

If you want to wipe empty space on a disk, just fill it up daily with random data.  That's a 3-4 line script.  The pros for ext4 are so many, IMHO, ext3 doesn't have much use anymore.  Heck, I use ext2 for /boot sometimes for small partitions and mostly read-only data (anywhere performance and journaling isn't needed).

Swap should be encrypted all the time.  I suspect something was lost in my attempt to convey LVM's power.

---

### Post by StewartM on 2021-06-28
> Encfs and EncryptFS have well documented security problems.

Like what? The only one I'm aware of is that Encryptfs doesn't always unmount the encrypted /home user directory after logout--it's best to do a reboot after logging out.  You could also point out that Encryptfs files will differ in size, that an adversary can differentiate encrypted files by size, something is probably a small text file vs a large media file, though the file names are ecrypted.  That part of the data will "leak".

> As for 2) each user have their own separate keys, just setup different LUKS containers for each user. 

And using LUKS I have to what? Re-partition the LVMS to accommodate a new user?  Or resize a LVM if one user runs out of space while another user has plenty of space?  And how exactly do you give different users different LVMs when everything is supposed to be under /home?  I have looked at a good many tutorials and 'how-tos' to do full-disk encryption, and none of them I recall showing this. 

> If you want to wipe empty space on a disk, just fill it up daily with random data. That's a 3-4 line script. The pros for ext4 are so many, IMHO, ext3 doesn't have much use anymore. 

I've used ext3 on all my systems for the past 14 years, since migrating to Linux from Windows, and I've never lost data, despite doing file wipes routinely.  The only hard drives I've had fail was a new one from Dell that was so new that it couldn't have possibly been to disk wear (it was replaced under warranty a few months after I bought the computer) and a backup external one where the firmware, not the disk itself, failed.  Wiping files on ext3 should mostly work, and plus I do it routinely for mostly everything, not just for sensitive files.  I believe that no security system is perfect, but I also think that putting all your eggs into one basket (say, full-disk encryption with no ability to wipe individual files) is also a mistake.  

Since I've never lost data to file corruption using ext3, plus I can wipe files, I don't see the advantage of ext4.

---

### Post by TheFu on 2021-06-28
I've provided leads for more research. It is up to others to research those leads and decide for themselves if there is any merit. Sorry that I've failed.

Creating a new LV is 5 seconds and ZERO downtime. A VG can have hundreds of physical disks and thousands of LVs.  Or use the "everything is a file method."

---

### Post by CharlesA on 2021-06-28
> **StewartM said:**
> 
And using LUKS I have to what? Re-partition the LVMS to accommodate a new user?  Or resize a LVM if one user runs out of space while another user has plenty of space?  And how exactly do you give different users different LVMs when everything is supposed to be under /home?  I have looked at a good many tutorials and 'how-tos' to do full-disk encryption, and none of them I recall showing this. 

As TheFu mentioned everything is a file on Linux. You can create a 10GB file with dd and then turn it into a LUKS container via cryptsetup. It's not going to be as flexible as LVM but it's still possible.

After you create the dd file, you can mount the luks container, format it as ext3/ext4 and then mount the file system as /home/$USERNAME.

It isn't as easy to deal with, but it is still possible. If a user needs more space, you can either resize the image after unmounting it and then resize the file system after remounting it or do some lvm magic.

There are other ways to accomplish the same thing with different encryption tools, but the only one I've really used is LUKS for block level encryption.

Have a read through this page if you want more info on what is out there:
[https://wiki.archlinux.org/title/Data-at-rest_encryption#Comparison_table](https://wiki.archlinux.org/title/Data-at-rest_encryption#Comparison_table)

> I've used ext3 on all my systems for the past 14 years, since migrating to Linux from Windows, and I've never lost data, despite doing file wipes routinely.  The only hard drives I've had fail was a new one from Dell that was so new that it couldn't have possibly been to disk wear (it was replaced under warranty a few months after I bought the computer) and a backup external one where the firmware, not the disk itself, failed.  Wiping files on ext3 should mostly work, and plus I do it routinely for mostly everything, not just for sensitive files.  I believe that no security system is perfect, but I also think that putting all your eggs into one basket (say, full-disk encryption with no ability to wipe individual files) is also a mistake.  

Since I've never lost data to file corruption using ext3, plus I can wipe files, I don't see the advantage of ext4.

I was using ext3 for years up until I tried out ext4 and stuck with it.

You can see some of the differences in the link below:
[https://www.thegeekstuff.com/2011/05/ext2-ext3-ext4/](https://www.thegeekstuff.com/2011/05/ext2-ext3-ext4/)

FWIW, I only really use ext4 for my /boot and root partitons nowadays. Everything else is running off ZFS, but I know that isn't for everyone as it is more complicated to set up and use.

---

### Post by StewartM on 2021-06-29
TheFu,

You've not failed.  You'd made me aware of the possibilities with LUKS. However, there is no specific tutorial on how to proceed, You've spoken of a great many possibilities, and I don't doubt you at all, but the examples are sparse---Say, I've not seen a /home directory subdivided into multiple user partitions out of the box.  What I got from the Linux vendor (which I've not set up yet, hence this post) is probably the generic full-disk encryption installation plus /home on a separate physical drive.

So, what I'm thinking is the easiest and quickest way to get what and to get the new computer up and running is:

1) Reformat the LUKS partition on the drive containing /home that they provided from ext4 to ext3.  Ext3 is still a journaling system, but only journals the metadata by default, not the file contents, so file wiping is still an option.  This should be doable using GParted, so it seems (maybe from a bootable DVD?) so this should be fairly straightforward and I can do this first. If what you say is correct, I don't need to change the filesystem of the physical drive containing home itself from ext4 to ext3, just the LUKS container, which you say is doable on the fly.

The LUKS partition on the filesystem drive ( / ) can stay ext4 as that is a SSD M2 drive and wiping won't work anyway on an SSD.

2) Install Encryptfs to produce the encrypted /home directory, save that now /home resides inside the LUKS /home partition.  Using Encryptfs inside of/in addition to LUKS on the same system appears to be quite possible:

[https://unix.stackexchange.com/questions/581106/is-it-good-to-have-both-luks-and-ecryptfs-encryptions-at-the-same-time](https://unix.stackexchange.com/questions/581106/is-it-good-to-have-both-luks-and-ecryptfs-encryptions-at-the-same-time)

This means that each user has separate encrypted folders without having to create additional LUKS partitions within the /home LUKS directory.

This would also install encryptfs-swap.  The documentation says "it detects any swap partitions or swap files" so hopefully that would work. That gives me another thing I want, an encrypted swap with a temporary key that is destroyed on shutdown and regenerated on boot (it will also be encrypted with the LUKS key of that partition but that is less relevant).   As encryptfs-swap detects swap files, as well as swap partitions, this (hopefully) means on future installs I can jettison the arbitrary swap partitions created by the default Ubuntu distributions, which are hard to resize, and just create swap files. 

I next want to upgrade this laptop, so maybe I can try out that combo. But first, I have to get the new desktop up and running.

---

### Post by kurt18947 on 2021-06-29
> As encryptfs-swap detects swap files, as well as swap partitions, this  (hopefully) means on future installs I can jettison the arbitrary swap  partitions created by the default Ubuntu distributions, which are hard  to resize, and just create swap files.

As far as I know, Ubuntu hasn't created swap partitions at install for some time, it creates swap files. I used one of the 'easy to use' encryption methods, I think it was encfs but I'm not certain. I became aware of a REALLY easy to exploit security issue - typing the letter "p" unlocked the encryption so stopped using it. Too bad, it was really easy to use. I don't know why the flaw couldn't be fixed. I'm a basic/casual user so not versed in the ins and outs of advanced topics like partition or disk encryption.

---

### Post by StewartM on 2021-07-14
> I used one of the 'easy to use' encryption methods, I think it was encfs but I'm not certain. I became aware of a REALLY easy to exploit security issue - typing the letter "p" unlocked the encryption so stopped using it. 

I've used ecrypt-swap-setup for years with no problems (and yes, I checked periodically). 

[http://manpages.ubuntu.com/manpages/bionic/man1/ecryptfs-setup-swap.1.html](http://manpages.ubuntu.com/manpages/bionic/man1/ecryptfs-setup-swap.1.html)

[https://superuser.com/questions/576097/is-ecryptfs-setup-swap-persistent](https://superuser.com/questions/576097/is-ecryptfs-setup-swap-persistent)

> Running ecryptfs-setup-swap makes permanent changes to /etc/fstab and /etc/crypttab that ensure your swap space is encrypted at every boot.

A random key is generated and used to encrypt swap at each boot.

The only exception to the above occurs if you add new swap files or swap partitions after you've run ecryptfs-setup-swap, as it only operates on the swap space present at that time.

On my new desktop I set up over the past weekend, I also was able to run ecryptfs-setup-swap on my LUKS encrypted volume that held an encrypted swap (with a permanent, fixed, key, the same as used for the rest of the volume) and it replaced that with the random key generated at boot and destroyed on shutdown.  Ecryptfs-setup-swap to me is clearly the superior solution.  Some have reported bugs with ecryptfs-setup-swap, but I've never seen it and I suspect that at least some of these were related to hibernate/suspend usage.  To me, for a desktop (or even a laptop) these are not important.  I've used encryption long enough and was warned by almost all encryption programs to "disable hibernate/suspend!" so that not having these isn't an expectation nor a big deal.

I was also able to run ecryptfs inside the LUKS LVM as well for my user accounts, which is also preferable as it provides an easier way to separate the encryption of user accounts from the system-wide encryption provided by the LUKS LVM (i.e., you don't have to block off various parts of the /home directory partition for various users and set up keys for each one; which can be a problem as various users' disk space requirements can vary drastically). 

And, I also found out it's trivial now to use GParted or other partition managers to open up LUKS containers and to change the filesystem type from there. I was able to change it from ext4 to ext3 for /home, as I had wanted.  As I stated above, the loss of wiping abilities for ext4 (without the need to wipe the drive freespace periodically, which is time-consuming for large drives) plus the fact that I've never lost data to corruption with ext3 filesystems (and trust me, the power has gone out lots of times here!) doesn't justify ext4.  Whatever gain in filesystem robustness with ext4 is minute compared to the loss of the ability to wipe data.

---

### Post by TheFu on 2021-07-14
Glad you found a solution which makes you happy enough.

I've used LUKS on laptops that suspend nightly since 2016. My rule is suspend at home/work when only trusted people have access, but shutdown whenever I leave the building or the laptop is moving outside the building.  If I'm walking on campus between buildings, I shutdown.  My laptop is still suspended from last night, so I can't show the "uptime" it reports, but it has probably been 2 weeks, perhaps longer. LUKS and suspend are stable, at least on Intel CPUs that I've used.

For disk space limitations, I'd use quotas.

I have an automatic free-space weekly wipe job. It file system independent. It runs after daily backups, but before the automatic pm-standby, so I don't have to be involved or inconvenienced.

How do you backup the encrypted files for users who aren't logged in?  I ask because that was the main reason I stopped using directory-level encryption methods. Backups are more important to me than encryption.  With LUKS, I can get all the data for all the users in the system backups whether they are logged in or not.  I'm probably just displaying my ignorance.

---

### Post by StewartM on 2021-07-16
> I've used LUKS on laptops that suspend nightly since 2016.

This is for a desktop, so suspends/hibernate isn't really as applicable.  The technology may well have improved, I don't doubt that, but as someone who has been doing encryption since the 1990s the boilerplate warning was always "don't trust hibernate/suspend".  So I'm just accustomed to disabling those up front. 

> For disk space limitations, I'd use quotas.

Hmm, as in % of the disk? I thought that block encryption by definition required setting up a fixed allocation per device (I know that LUKS containers can be expanded, and even shrunk, but what I've read in the tutorials was that there was always risk in that).

> How do you backup the encrypted files for users who aren't logged in?

As most of the users who would be using this desktop would be in the category of "infrequent but recurrent" users, I leave the backups to them.  I back up my own accounts to encrypted (Veracrypt) external hard drives.  The users who would occasionally use my system would be a) not users who would require a lot of storage (for one in particular, the internet is mostly Facebook and Youtube); b) not security-conscious (they would ask for weak passphrases, and if enforced a stronger LUKS passphrase, they'd just write it down). I know I could create different LUKS keys for them, put they'd have weak passphrases for them, else I'd be constantly enabling and disabling LUKS keys for them so it would not be walk-up access. At least given the LUKS encryption system installation I was given.  

I don't doubt that, as you say, that you could get a LUKS system I would be happy with, it's just I've not seen any examples on the web. I had held on to Ubuntu 16.04 for a long time after seeing no options with the encrypted LUKS install of 18.04, thinking "in 20.04 they'll have options" but nope, none yet.  You can't even do the simple things, like change the default swap space size nor put /home on a different drive/partition with the installation defaults.  From my perspective, encrypted installs should be the default (there's really no reason why not, and especially for laptops--both Microsoft and Apple make encryption the default option) and thus as it is the default option it should have all the options in the GUI that a non-encrypted installation has.


If you wanted to back up a directly-level Ecryptfs encryption for someone, you could simply copy-and-paste their entire encrypted directly--and their keys are in /home/.ecryptfs--though that would not be a backup that could be opened independently of a running Linux system. (Me, I don't back up my entire directory, just the user data; as if I do a complete install instead of an upgrade sometimes the configuration files in /home/user are incompatible with the new version of Linux and break things, so it's best to start out with new configuration files).

---

### Post by TheFu on 2021-07-16
Cough - way to bury the lead!!!  16 posts in and we are finally told this is a temporary purpose setup?  Thanks.

If it were me, I would encrypt and put the LUKS decryption key on the network for automatic boot.  [https://withblue.ink/2020/01/19/auto-mounting-encrypted-drives-with-a-remote-key-on-linux.html](https://withblue.ink/2020/01/19/auto-mounting-encrypted-drives-with-a-remote-key-on-linux.html) explains how. I've not done this. Basically, any disk on the correct network could be unlocked automatically, but off that network and it is fully encrypted.  I have seen this implemented with RHEL and FreeIPA, but didn't dig into the implementation.

Per-user quotas don't have anything to do with partition sizes, except setting a quota for a user larger than the partition wouldn't magically create storage. 

Is comparing $420B annual revenue Apple and $140B annual revenue MSFT to $0.120B annual revenue Canonical fair?  
Anyway, you've found a solution. Enjoy.

---

### Post by CharlesA on 2021-07-16
> **StewartM said:**
> 
I don't doubt that, as you say, that you could get a LUKS system I would be happy with, it's just I've not seen any examples on the web. I had held on to Ubuntu 16.04 for a long time after seeing no options with the encrypted LUKS install of 18.04, thinking "in 20.04 they'll have options" but nope, none yet.  You can't even do the simple things, like change the default swap space size nor put /home on a different drive/partition with the installation defaults.  From my perspective, encrypted installs should be the default (there's really no reason why not, and especially for laptops--both Microsoft and Apple make encryption the default option) and thus as it is the default option it should have all the options in the GUI that a non-encrypted installation has.


What are you going on about? You can do an encrypted root from the setup GUI if you really want to.

If you want to do it automatically, you just need to select the "Advanced features" button under "Erase disk and install Ubuntu" and check the boxes for use LVM and encrypt the new installation for security. That stuffs everything for / on a single partition.

[ATTACH=CONFIG]288823[/ATTACH]

If you want something more complicated, do it manually by selecting "Something else" instead of "Erase disk and install Ubuntu" and set up the efi, /boot and encrypted root partition from there by selecting the option for "physical volume for encryption" listed in the wizard.

That option will create your LUKS container. You still need to create the ext4 file system and set it up as / and swap or /home or /tmp or however many partitions you want to have.

[ATTACH=CONFIG]288824[/ATTACH]

FWIW, Windows 10 doesn't do encryption by default during install. You have to enable Bitlocker after install and create your recovery key in order to enable it.

I haven't used a Mac, so I can't comment on how they handle full disk encryption.

---

### Post by StewartM on 2021-07-22
> If you want something more complicated, do it manually by selecting "Something else" instead of "Erase disk and install Ubuntu" and set up the efi, /boot and encrypted root partition from there by selecting the option for "physical volume for encryption" listed in the wizard.

That option will create your LUKS container. You still need to create the ext4 file system and set it up as / and swap or /home or /tmp or however many partitions you want to have.

Hmm, I didn't do an Ubuntu install, but I did do a Bodhi install of the LTS release equivalent of 20.04 (which would be a downstream release) for a friend and tried the hard drive encryption and didn't see these options.  Moreover, after a lot of searching I never saw any resource that described what you just posted (several things that had long pages of command line stuff, and I'm old school enough to follow the adage ([which has been posted on the Ubuntu forums]("https://ubuntuforums.org/announcement.php?f=326")) is that "never copy and paste and execute command line commands you don't understand, due to the potential of executing malicious code").   And even these pages didn't have every option I wanted. 

What I did see while doing this install and searching for solutions (my friend's laptop had only 2 GB of RAM, which was why I was installing Bodhi and not Ubuntu, as it was below the recommended specs) was the people struggling with the default swap partition/file size issue.  The default install gave me only 1 GB of swap for a laptop having 2 GB RAM, which seemed to me inadequate for a machine so limited; I would have voted for 4 GB swap, Lots of other people too thought it was inadequate, but from what you showed, it should be trivial to set up.  But no one mentioned it or seemed to be aware of it.

So the GUI options surely aren't advertised.

Another thing that I find frustrating and backward (and is disappointing) is that the Linux distros I've tried still keep showing the users " ****** "s for their passphrases.  All the standalone encryption software I've used of good repute (Scramdisk, TrueCrypt, Veracrypt, etc) now give the "show passphrase" option because they understand that showing the passphrase encourages users to create stronger passphrases while strings of ****'s lead them to use weaker passphrases.  Now Windows 10 allows one to peek at what one typed in to encourage stronger passphrases; I don't know about Mac.  But Linux still enforces the "*****"s.  The reason I mention this is an IT friend of mine (who's a Linux user) says the "****"s are "the industry standard" but that can't be as Windows 10 now allows users to view their passphrases.

IMHO, the history of ****s dates from terminal/mainframe days, when encryption wasn't used, and people used their girlfriend's or dog's name or whatnot to login, passphrases so weak that someone peeking over their shoulder might spot and use to hack the account.  With encryption, passphrases that are generally equal to at least a 128-bit key that would resist a dictionary attack someone could not spot and memorize in a 3-second peak, unlike "Rover",  so whatever security one would lose by this option would be more than offset by users generating and using stronger passphrases.  I know that someone could set up a hidden camera to capture passphrases but someone with that kind of access would just install a keylogger on the machine to be compromised.  So to me, there's no good reason not to allow them.

---

### Post by StewartM on 2021-07-22
> If you want something more complicated, do it manually by selecting "Something else" instead of "Erase disk and install Ubuntu" and set up the efi, /boot and encrypted root partition from there by selecting the option for "physical volume for encryption" listed in the wizard.

That option will create your LUKS container. You still need to create the ext4 file system and set it up as / and swap or /home or /tmp or however many partitions you want to have.

Hmm, I didn't do an Ubuntu install, but I did do a Bodhi install of the LTS release equivalent of 20.04 (which would be a downstream release) for a friend and tried the hard drive encryption and didn't see these options.  Moreover, after a lot of searching I never saw any resource that described what you just posted (several things that had long pages of command line stuff, and I'm old school enough to follow the adage ([which has been posted on the Ubuntu forums]("https://ubuntuforums.org/announcement.php?f=326")) is that "never copy and paste and execute command line commands you don't understand, due to the potential of executing malicious code").   And even these pages didn't have every option I wanted. 

What I did see while doing this install and searching for solutions (my friend's laptop had only 2 GB of RAM, which was why I was installing Bodhi and not Ubuntu, as it was below the recommended specs) was the people struggling with the default swap partition/file size issue.  The default install gave me only 1 GB of swap for a laptop having 2 GB RAM, which seemed to me inadequate for a machine so limited; I would have voted for 4 GB swap, Lots of other people too thought it was inadequate, but from what you showed, it should be trivial to set up.  But no one mentioned it or seemed to be aware of it.

So the GUI options surely aren't advertised.

Another thing that I find frustrating and backward (and is disappointing) is that the Linux distros I've tried still keep showing the users " ****** "s for their passphrases.  All the standalone encryption software I've used of good repute (Scramdisk, TrueCrypt, Veracrypt, etc) now give the "show passphrase" option because they understand that showing the passphrase encourages users to create stronger passphrases while strings of ****'s lead them to use weaker passphrases.  Now Windows 10 allows one to peek at what one typed in to encourage stronger passphrases; I don't know about Mac.  But Linux still enforces the "*****"s.  The reason I mention this is an IT friend of mine (who's a Linux user) says the "****"s are "the industry standard" but that can't be as Windows 10 now allows users to view their passphrases.

IMHO, the history of ****s dates from terminal/mainframe days, when encryption wasn't used, and people used their girlfriend's or dog's name or whatnot to login, passphrases so weak that someone peeking over their shoulder might spot and use to hack the account.  With encryption, passphrases that are generally equal to at least a 128-bit key that would resist a dictionary attack someone could not spot and memorize in a 3-second peak, unlike "Rover",  so whatever security one would lose by this option would be more than offset by users generating and using stronger passphrases.  I know that someone could set up a hidden camera to capture passphrases but someone with that kind of access would just install a keylogger on the machine to be compromised.  So to me, there's no good reason not to allow them.

---

### Post by CharlesA on 2021-07-22
> **StewartM said:**
> Hmm, I didn't do an Ubuntu install, but I did do a Bodhi install of the LTS release equivalent of 20.04 (which would be a downstream release) for a friend and tried the hard drive encryption and didn't see these options.  Moreover, after a lot of searching I never saw any resource that described what you just posted (several things that had long pages of command line stuff, and I'm old school enough to follow the adage ([which has been posted on the Ubuntu forums]("https://ubuntuforums.org/announcement.php?f=326")) is that "never copy and paste and execute command line commands you don't understand, due to the potential of executing malicious code").   And even these pages didn't have every option I wanted.

I've used this guide to set up one of my boxes with full disk encryption of the OS drive. My /boot is running of a 32GB USB stick. You can make it so /boot is on it's own partition, but it complicates things.

[https://www.linux.com/training-tutorials/how-full-encrypt-your-linux-system-lvm-luks/](https://www.linux.com/training-tutorials/how-full-encrypt-your-linux-system-lvm-luks/)

There is also a pretty good guide on the Arch Wiki - the commands are generic Linux commands, not specific to Arch.

[https://wiki.archlinux.org/title/Dm-crypt/Encrypting_an_entire_system#LVM_on_LUKS](https://wiki.archlinux.org/title/Dm-crypt/Encrypting_an_entire_system#LVM_on_LUKS)

> What I did see while doing this install and searching for solutions (my friend's laptop had only 2 GB of RAM, which was why I was installing Bodhi and not Ubuntu, as it was below the recommended specs) was the people struggling with the default swap partition/file size issue.  The default install gave me only 1 GB of swap for a laptop having 2 GB RAM, which seemed to me inadequate for a machine so limited; I would have voted for 4 GB swap, Lots of other people too thought it was inadequate, but from what you showed, it should be trivial to set up.  But no one mentioned it or seemed to be aware of it.

The default behavior was changed quite a while ago because machines normally have more memory on them nowadays and it would be dumb to use 32GB of space for swap when a machine is running with 16GB of RAM. Some stuff I read mentioned a swap file by default, but that hasn't been my experience (granted, I'm only running 18.04 as a VM currently with Debian for everything else).

On my 18.04 box, I've got a swap partition.

```
cat /proc/swaps
Filename                                Type            Size    Used    Priority
/dev/dm-1                               partition       4190204 6716    -2

```

> 
Another thing that I find frustrating and backward (and is disappointing) is that the Linux distros I've tried still keep showing the users " ****** "s for their passphrases.  All the standalone encryption software I've used of good repute (Scramdisk, TrueCrypt, Veracrypt, etc) now give the "show passphrase" option because they understand that showing the passphrase encourages users to create stronger passphrases while strings of ****'s lead them to use weaker passphrases.  Now Windows 10 allows one to peek at what one typed in to encourage stronger passphrases; I don't know about Mac.  But Linux still enforces the "*****"s.  The reason I mention this is an IT friend of mine (who's a Linux user) says the "****"s are "the industry standard" but that can't be as Windows 10 now allows users to view their passphrases.

IMHO, the history of ****s dates from terminal/mainframe days, when encryption wasn't used, and people used their girlfriend's or dog's name or whatnot to login, passphrases so weak that someone peeking over their shoulder might spot and use to hack the account.  With encryption, passphrases that are generally equal to at least a 128-bit key that would resist a dictionary attack someone could not spot and memorize in a 3-second peak, unlike "Rover",  so whatever security one would lose by this option would be more than offset by users generating and using stronger passphrases.  I know that someone could set up a hidden camera to capture passphrases but someone with that kind of access would just install a keylogger on the machine to be compromised.  So to me, there's no good reason not to allow them.

The whole "don't echo the password to the screen" thing was a Linux thing for a long time. Windows has always showed your masked password, but now they give you the option to see it since typos happen.

I can't tell if you are supporting this behavior or if you think it's bad. The user experience where you don't get anything echoed to the screen while typing on the keyboard is confusing, especially for someone who is used to Windows.

I haven't seen any cases where cryptsetup will echo your password to the screen. If you are concerned that displaying the masked password makes users pick poor passwords, use a password generator so you don't have to think about it.

---

### Post by StewartM on 2021-07-26
Charles,

I was complaining that not being able to see your passwords (which Truecrypt, Veracrypt, Scramdisk and other noteworthy encryption programs *do allow*) does drive weak passphrase creation.  It's much easier to type in correctly a passphrase equivalent to a 256-bit key when you can see what you're typing; very difficult when you don't.

But I have another question--have you had any problems with encrypted swap being disabled on kernel upgrades?  

> cryptsetup: WARNING: Option 'size' missing in crypttab for plain dm-crypt 
    mapping cryptswap1. Please read 
    /usr/share/doc/cryptsetup-initramfs/README.initramfs.gz and add the correct 
    'size' option to your crypttab(5).
cryptsetup: WARNING: Resume target cryptswap1 uses a key file


I had this, and the fix is to 1) update in /etc the crypttab file and append "size=256" at the end.  Then you also have to update initramfs:

> 
swapoff -a

sudo update-initramfs -c -k all

swapon -a


This has bitten a number of people, just wanted to know if it was your experience too.

---

### Post by CharlesA on 2021-07-26
> **StewartM said:**
> Charles,

I was complaining that not being able to see your passwords (which Truecrypt, Veracrypt, Scramdisk and other noteworthy encryption programs *do allow*) does drive weak passphrase creation.  It's much easier to type in correctly a passphrase equivalent to a 256-bit key when you can see what you're typing; very difficult when you don't.

That makes sense. I've lost count of the number of times I've made a typo when trying to punch in my encryption key and having to retype it in. It's a minor inconvenience through, since there isn't a mechanism for wiping the drives if you put the wrong passphrase in.

As for the swap file issue - I haven't run into that, but my installs are older (and I'm also running Debian) instead of Ubuntu, so I don't know if that explains the difference.

I do know, I had a hell of a time with getting the post upgrade scripts to add cryptsetup to the initramfs images.

---

### Post by StewartM on 2021-07-27
Well, two things happened to my new desktop (ordered from a Linux vendor with Mint--their preference--and wit the LUKS encryption setup).

1) I mistakenly downloaded and install Hplip from HP to run what I thought was a All-in-one device (but wasn't).  Doing that and replacing the Linux hplip broke several things in the Cinnamon desktop.  I was able to revert the Hplip back to the Linux version, but several things in Cinnamon remained broken (after doing multiple searches on what others had found and done, I tried these and either they didn't work or they didn't apply to me).  Finally I tried removing and re-installing the broken components, and that resulted in a system that I can boot but after I log in I get a blank screen.

So...I'm going to first try completely removing Cinnamon (purging) and then re-installing it at the recovery command prompt. If not, I'll have to learn how to set things back up myself. I suspect that will be relatively easy, as /home is on a separate disk I will just take what I see already set up Gparted during the installation.  I may first try just doing the installation without erasing the filesystem partition; if that doesn't work I'll do it with erasing/formatting the filesystem (but not home). 

2) But I have yet another thing to do before that.  I still had the old hard drive mounted in the desktop with an Ubuntu 16.04 install, so still I had a usable system to use before doing the above.  But last night, the new computer's power supply apparently croaked. I have a 750 W spare, that is relatively new (only like 2 years old), so I have something I can plug in.

Oh and according to what I'm seeing looking in my crypttab, the default LUKS encryption for /swap does use a randomly generated key. 

[https://wiki.archlinux.org/title/Dm-crypt/Swap_encryption](https://wiki.archlinux.org/title/Dm-crypt/Swap_encryption)
> 
In systems where suspend-to-disk (hibernation) is not a desired feature, /etc/crypttab can be set up to decrypt the swap partition with a random password with plain dm-crypt at boot-time. The random password is discarded on shutdown, leaving behind only encrypted, inaccessible data in the swap device.

To enable this feature, simply uncomment the line beginning with swap in /etc/crypttab. Change the <device> parameter to the name of your swap device. For example, it will look something like this:

/etc/crypttab

# <name>  <device>     <password>     <options>
swap      /dev/sdX#    /dev/urandom   swap,cipher=aes-xts-plain64,size=256

In fact, you have to modify the install with a fixed LUKS key to do hiberation

[https://help.ubuntu.com/community/EnableHibernateWithEncryptedSwap](https://help.ubuntu.com/community/EnableHibernateWithEncryptedSwap)

---

