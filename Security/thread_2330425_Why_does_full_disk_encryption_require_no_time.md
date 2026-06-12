---
title: "Why does full disk encryption require no time?"
date: 2016-07-11
forum: Security
---

### Post by nw9165-3201 on 2016-07-11
Hi,

as far as I understand, the ***"Encrypt the new Ubuntu installation for security"*** option in the Ubuntu installer is meant to provide full disk encryption.

However, when using that option, it seems like as if the encryption would finish instantly, it literally does not seem to take any time at all.

When using BitLocker on Windows to encrypt the entire disk, it can take hours to fully encrypt the disk, even on SSDs. With BitLocker and other encryption tools like DiskCryptor or TrueCrypt for example, there's also a progress indicator, which shows how much of the disk is encrypted already.

Why is that not the case with the ***"Encrypt the new Ubuntu installation for security"*** option in the Ubuntu installer?

Even on my 1 TB SSD the encryption seems to be set up instantly and there's no progress indicator whatsoever.

How's that possible?

Regards

---

### Post by TheFu on 2016-07-11
LVM is magic. No, seriously, it is. ;)

Data doesn't become encrypted until written and many CPUs have built-in AES encryption which makes that a non-event with imperceivable slowdowns.  If you want to randomly initialize the storage areas PRIOR to writing anything, that will take some. I seem to recall it being an optional checkbox for the installation.

In many ways, Linux is similar to other OSes like Window, but in some ways it is a completely different animal. This is one of those places where it is different.

---

### Post by nw9165-3201 on 2016-07-12
> **TheFu said:**
> Data doesn't become encrypted until written

What? Then the ***"Encrypt the new Ubuntu installation for security"*** option in the installer is not full disk encryption at all.

If you are correct, then it does not encrypt the entire disk then. It only encrypts used disk space. The empty space is not encrypted then.

At least with BitLocker you have the option to choose between encrypting used disk space only or encrypting the entire disk, see following screenshot for example:

[https://i-technet.sec.s-msft.com/en-us/windows/jj983729.bitlocker-screen(en-us,MSDN.10).jpg](https://i-technet.sec.s-msft.com/en-us/windows/jj983729.bitlocker-screen(en-us,MSDN.10).jpg)

 > **TheFu said:**
> If you want to randomly initialize the storage areas PRIOR to writing anything, that will take some. I seem to recall it being an optional checkbox for the installation.

Yes, there is a ***"For more security: Overwrite empty disk space (The installation might take much longer.)"*** option on the next screen after the screen which has the ***"Encrypt the new Ubuntu installation for security"*** option.

Now, the question is: If that option is checked, does it just overwrite the empty disk space? Or does it also encrypt it?

I was assuming that it only overwrites it with zeros before encrypting it. I was assuming that the entire disk would be encrypted anyway using the ***Encrypt the new Ubuntu installation for security"*** option, regardless of the ***"For more security: Overwrite empty disk space (The installation might take much longer.)"*** option.

---

### Post by nw9165-3201 on 2016-07-12
Reported:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1602155](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1602155)

Regards

---

### Post by TheFu on 2016-07-12
> **nw9165-3201 said:**
> Reported:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1602155](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1602155)

Regards

Does the installer claim "full disk encryption"?  Is there a documentation mistake somewhere official?

Canonical isn't the maintainer of the code doing the work - that is probably a mix of LUKS and dm-crypt. Manually, it is usually  accessed via  **cryptsetup** command. Upstream, ?debian?, is not likely to do anything. The most you can hope for is a tooltip explanation for the installer. Doubt that will happen.

Pointing out how some other non-Unix OS does something isn't relevant. 

The **cryptsetup** manpage has lots of helpful information in it. Could be worth reading to avoid wasting the time of the people who triage bugs. BTW, there is a manpage for 99% of all tools and usually each has important data which would answer most questions, if read. Referencing a way that the manpage and the code are different **is** a bug and will likely get an update.

> I was assuming that it only overwrites it with zeroes before encrypting it. 
Why assume that?  I wouldn't. Overwriting in that way wouldn't be useful at all. We (volunteers here) have to deal with non-technical people all day here and choosing the correct level with which to reply isn't easy. I assumed lots of things based on your low bean count. Sorry.  

I bet, but don't know, that the "overwriting" happens after the container is marked for encryption and opened.  Then it doesn't matter what is written to the storage, since even zeros will appear as 100% random data during the encryption process on the raw storage.  Plus, when doing an install, I'm usually in a hurry, so NOT allowing it to eat time unnecessarily **is** a feature.  Later, if I want, the free space can be filled with random data trivially: [https://unix.stackexchange.com/questions/72216/fast-way-to-randomize-hd](https://unix.stackexchange.com/questions/72216/fast-way-to-randomize-hd)  There are common ways to clean up old files in Unix which have been around for many decades.

If you need the highest level of security for the data at rest, you'll probably need to manually setup the encryption. That skill is beyond me. I can do it for non-boot storage/partitions/LVs, but for the OS, it has eluded my skills the multiple (30-50-ish?) attempts made. Fortunately, for most of my needs, using a cheap chromebook with a minimal Linux on it as a remote access device is sufficient. That way sensitive data never leaves the physically secured server(s) to be on any portable device. Just another option.

Lastly, Ubuntu doesn't support "*whole drive encryption*" with a checkbox.  /boot isn't encrypted, therefore it isn't *whole drive encryption*. I know people are working on a way to have signed boot programs (think it is working somewhere), but until that becomes easy to use for normal people, with a checkbox during install, the best security is to have the boot media with you all the time and only use that (not the /boot partition).  We all need to fight those [evil maids]("https://www.schneier.com/blog/archives/2009/10/evil_maid_attac.html").

Good discussion. Appreciate it.

---

### Post by nw9165-3201 on 2016-07-12
> **TheFu said:**
> Does the installer claim "full disk encryption"?  Is there a documentation mistake somewhere official?

Well, the installer itself does not, but various documentations and articles do, just to name a few examples, see:

[https://help.ubuntu.com/community/FullDiskEncryptionHowto](https://help.ubuntu.com/community/FullDiskEncryptionHowto)
[https://www.eff.org/deeplinks/2012/11/privacy-ubuntu-1210-full-disk-encryption](https://www.eff.org/deeplinks/2012/11/privacy-ubuntu-1210-full-disk-encryption)
[http://thesimplecomputer.info/full-disk-encryption-with-ubuntu](http://thesimplecomputer.info/full-disk-encryption-with-ubuntu)
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1404_encryption&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1404_encryption&num=1)

> **TheFu said:**
> I bet, but don't know

That does not necessarily sound reassuring. So, me having submitted a bug report probably was a good idea, so that we can hopefully get an official confirmation instead of having to guess...

> **TheFu said:**
> that the "overwriting" happens after the container is marked for encryption and opened.  Then it doesn't matter what is written to the storage, since even zeros will appear as 100% random data during the encryption process on the raw storage.

Then the installer options should be renamed the way it's done for BitLocker where it offers to select between "Encrypt used space only" and "Encrypt entire drive", see:

[https://i-technet.sec.s-msft.com/en-us/windows/jj983729.bitlocker-screen(en-us,MSDN.10).jpg](https://i-technet.sec.s-msft.com/en-us/windows/jj983729.bitlocker-screen(en-us,MSDN.10).jpg)

That woule be a lot more straight forward and easier to understand.

> **TheFu said:**
> If you need the highest level of security for the data at rest, you'll probably need to manually setup the encryption.

Why?

Why not let the installer do it? If the installer currently does not provide the highest level of security, I'd consider that a bug which should be fixed.

 > **TheFu said:**
> That skill is beyond me.

One more reason to let the installer do it.

> **TheFu said:**
> Lastly, Ubuntu doesn't support "*whole drive encryption*" with a checkbox.  /boot isn't encrypted, therefore it isn't *whole drive encryption*. I know people are working on a way to have signed boot programs (think it is working somewhere), but until that becomes easy to use for normal people, with a checkbox during install, the best security is to have the boot media with you all the time and only use that (not the /boot partition).

Looks like it's possible to encrypt /boot as well and then "simply" have GRUB decrypt and mount the disk upon booting the machine for example, see:

[http://www.pavelkogan.com/2014/05/23/luks-full-disk-encryption/](http://www.pavelkogan.com/2014/05/23/luks-full-disk-encryption/)

> **TheFu said:**
> Plus, when doing an install, I'm usually in a  hurry, so NOT allowing it to eat time unnecessarily **is** a feature.   Later, if I want, the free space can be filled with random data  trivially: [https://unix.stackexchange.com/questions/72216/fast-way-to-randomize-hd](https://unix.stackexchange.com/questions/72216/fast-way-to-randomize-hd)  There are common ways to clean up old files in Unix which have been around for many decades.

If the entire disk is not being encrypted by the Ubuntu installer option, then that could pose a security risk on SSDs due to wear leveling, right?

Regards

---

### Post by nw9165-3201 on 2016-07-16
Anyone?

---

### Post by Skaperen on 2016-07-19
sorry ... too much to read

this is my understanding ...

the encryption is merely enabled.  encryption is integrated with write operations, so it happens when writes happen.   resident data is not encrypted,  read it and write it back to be encrypted. you can change the key instantly, too (for entirely different reasons).

---

### Post by nw9165-3201 on 2016-07-19
Then it is not full disk encryption at all and wear levelling of SSDs could pose a security risk... :confused: :-k :shock: :(

---

### Post by frostschutz on 2016-07-19
> **nw9165-3201 said:**
> Then it is not full disk encryption at all and wear levelling of SSDs could pose a security risk... :confused: :-k :shock: :(

Let me show you a hexdump of my encrypted & trimmed SSD (random data segments shortened with --, visible free space zeroes *): [https://bpaste.net/raw/505157](https://bpaste.net/raw/505157) 

What can you do with it?

Encrypting just your data is enough for most people, but there are different ideas here...

1) overwrite the entire device with random data to get rid of old unencrypted data

2) overwrite the entire device with random data so you can't see where free space is / how much encrypted data you have and where

3) special case SSD: whether or not to use TRIM/discard or not which would make 1) and 2) superfluous as with TRIM, old data is always discarded and free space is always visible anyways (as shown in paste above)

There is no security risk with visible free space. You see people ranting about this everywhere but it's very far down in the list of things that actually matter. Visible free space is entirely normal. It's part of the concept for file based encryption (ecryptfs, encfs, new builtin ext4 encryption, ...), it's normal for SSD because everyone uses TRIM anyways, there's nothing whatsoever wrong with it.

Most setups have glaring weak points elsewhere. If your simple passphrase can be logged with a $1 keyboard dongle or simply by tampering with your initramfs or using the $5 decryption wrench [https://xkcd.com/538/](https://xkcd.com/538/) then visible free space is very far down on the list of things you should worry about.

---

### Post by Skaperen on 2016-07-24
> **nw9165-3201 said:**
> Then it is not full disk encryption at all and wear levelling of SSDs could pose a security risk... :confused: :-k :shock: :(

if you had encryption enabled when you first wrote the data, then that data is encrypted (with the old key).  if you want all the data to now be encrypted with the new key, read and rewrite all the data.  there are cases where less than this is desired and secure, so it won't just do it automatically.  wear levelling of SSDs has its own security issues when you no longer have block layer access to residual data (wiping the device won't get rid of all residual data).

---

### Post by SamInside on 2016-09-26
This is a _**very bad security-related bug**_, and it's being misunderstood by everyone.
The original poster should have focused on the ***"Overwrite empty disk space"*** option, maybe that would have made it clearer, but still I'm astonished that no one is getting this right.
I hope to do some clarification.

Encrypting a drive or a partition with Ubiquity, after choosing either the *"Encrypt the new Ubuntu installation for security"* option or the *"Something else"* one followed by manual encryption using the default partitioning software, you will be given this _*checkbox*_ at some point:
[SIZE=4]***"For more security: Overwrite empty disk space (The installation might take much longer.)"***[/SIZE]
This has one and only one obvious meaning:
_**the entire selected drive or partition will be wiped out / hard-formatted / overwrited with random data**_. This is how it works with every encryption software.
The reason to choose this option is to delete residual data on the disk/partition in case the disk is not new and "clear data" has been written on it in the past. You can of course do this before manually with various tools (*dd*, *shred*, etc.), but that's not the point.
The bug is that if you check the checkbox, **_this user choice will be completely ignored_**, i.e. the partition/disk will not be wiped and it will only be "set" for encryption of following writings (e.g. the following installation of Ubuntu and the first things the user will do with it).

I post again the bug report in hope of further discussion and fixing:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1602155](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1602155)

---

### Post by SamInside on 2016-09-27
Related unsolved old bug report: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1285247?comments=all](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1285247?comments=all)

---

### Post by frostschutz on 2016-09-30
The option should work. Indeed it doesn't. The bug report is confusing since it does not lead with this issue and does not provide steps to reproduce... probably won't be fixed this way unless a super motivated developer stumbles across it. ;)

This is the first time I tried to debug the Ubuntu installer and damn it's confusing... tons of stuff in the debug log, just not what you're looking for.

Edit:

The file """skip_erase""" exists even with the option checked, and such the erasing functions (crypto_wipe, crypto_do_wipe) are never called. I'm too lazy to track down what is supposed to be creating/removing the """skip_erase"""

---

### Post by SamInside on 2016-09-30
> **frostschutz said:**
> The bug report is confusing since it does not lead with this issue and does not provide steps to reproduce... probably won't be fixed this way unless a super motivated developer stumbles across it.
Have you checked the other older bug report that I've linked?
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1285247?comments=all](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1285247?comments=all)
It refers to the exact issue.

---

### Post by T2uiYKb7 on 2016-10-05
> **nw9165-3201 said:**
> What? Then the ***"Encrypt the new Ubuntu installation for security"*** option in the installer is not full disk encryption at all.

If you are correct, then it does not encrypt the entire disk then. It only encrypts used disk space. The empty space is not encrypted then.

At least with BitLocker you have the option to choose between encrypting used disk space only or encrypting the entire disk, see following screenshot for example:

[https://i-technet.sec.s-msft.com/en-us/windows/jj983729.bitlocker-screen(en-us,MSDN.10).jpg](https://i-technet.sec.s-msft.com/en-us/windows/jj983729.bitlocker-screen(en-us,MSDN.10).jpg)

 

Yes, there is a ***"For more security: Overwrite empty disk space (The installation might take much longer.)"*** option on the next screen after the screen which has the ***"Encrypt the new Ubuntu installation for security"*** option.

Now, the question is: If that option is checked, does it just overwrite the empty disk space? Or does it also encrypt it?

I was assuming that it only overwrites it with zeros before encrypting it. I was assuming that the entire disk would be encrypted anyway using the ***Encrypt the new Ubuntu installation for security"*** option, regardless of the ***"For more security: Overwrite empty disk space (The installation might take much longer.)"*** option.


There's lots of ways to write random data over your entire disk, you can do it with the live DVD/USB and "dd" command if you interested.

I never considered encrypting deleted files but I can see how it would be important to some. 

Edit: Sorry to clarify do you want those deleted files to be wiped or do you want them encrypted so you can possibly restore them in the future? I can't see why anyone would want to encrypted deleted files.

---

### Post by SamInside on 2016-10-11
> **andrew.nz said:**
> to clarify do you want those deleted files to be wiped or do you want them encrypted so you can possibly restore them in the future? I can't see why anyone would want to encrypted deleted files.
Obviously "wiped". Please see my post to understand the issue: [https://ubuntuforums.org/showthread.php?t=2330425&page=2&p=13549951#post13549951](https://ubuntuforums.org/showthread.php?t=2330425&page=2&p=13549951#post13549951)

---

