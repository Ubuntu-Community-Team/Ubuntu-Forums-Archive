---
title: "the weakest link: log in password and encryption passphrase"
date: 2017-01-17
forum: Security
---

### Post by parminides on 2017-01-17
Although I've taken measures to protect most of my computer files over the years, I did not encrypt my home folder during installation a few years back. (I've been upgrading since.) I'm thinking about encrypting the home folder now, post-installation; something like [https://trisquel.info/en/wiki/encrypt-home-directory-after-install](https://trisquel.info/en/wiki/encrypt-home-directory-after-install).

Assume someone has a weak Ubuntu log in password ("abcd", birthday, whatever), but he chooses (or is assigned) a strong passphrase for the encrypted home directory. Now suppose that someone steals his hard drive.

Is it possible for the thief to boot to the Ubuntu partition on the hard drive (or copy the partition somewhere and make it bootable)? If so, guessing the log in password would be a much smaller hurdle than cracking the encryption passphrase.

Wouldn't this be a much easier way to access the home folder files? In other words, just attack the weakest security link, completely negating the encrypted passphrase strength. What prevents this from being possible?

---

### Post by TheFu on 2017-01-17
If you care about security, use whole drive encryption.  There are many reasons and not just massive performance improvements over an encrypted HOME.  If you just want a private directory that gets decrypted occasionally, that can be added later.

Passwords less than 20, random, characters, are a weak link.  People are hacking 16 character random passphrases in 24 hours today.  If someone has physical access, pretty much nothing we do can prevent access, except whole disk encryption when powered off.  Standby and hibernation break this.  Plus, you'll want a boot device that never leaves your person to avoid the "evil maid" attack.

Look up some articles about travel security for computer. There isn't 1 answer. It is about multiple layers.  [http://blog.jdpfu.com/search/?q=travel+computers](http://blog.jdpfu.com/search/?q=travel+computers) has my take on this.

---

### Post by parminides on 2017-01-17
I am very interested in increasing security, so I will read those links, but you didn't answer my question. Could someone avoid needing the encryption passphrase if they knew the log in password and had possession of the drive (but not the original computer)?

---

### Post by TheFu on 2017-01-17
> **parminides said:**
> I am very interested in increasing security, so I will read those links, but you didn't answer my question. Could someone avoid needing the encryption passphrase if they knew the log in password and had possession of the drive (but not the original computer)?

I didn't answer the question because I do not know the answer 100%. 

There are a number of issues with only using HOME directory encryption, a little searching will find some. Mainly leaks of cached data and passwords in the unencrypted swap.  For me, it was problems doing backups.  Whenever encryption is involved, great, recoverable, backups are required.

Last time I used HOME directory encryption, the key for access was just the login password. That wouldn't be tied to any specific hardware, unless you take extra steps with an external device.  There are recovery methods outlined in how-to docs on help.ubuntu.com, which also implies that nothing is tied to the specific hardware used.  I would bet that cloning a disk with encryption on it would allow the cloner with effort to get into the encrypted files, eventually. Would just depend on the strength of the password.

Whole drive encryption, as used with Ubuntu, is not tied to the specific hardware.  This I know 100%.

---

### Post by parminides on 2017-01-18
Thank you for your response. I haven't read your links yet, but I have been doing some research.

I learned today that apparently one can change user passwords in Ubuntu even if the current password is unknown/fogotten! I find this astounding, but that's exactly what's claimed at [http://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password](http://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password).

I hope one of you can reassure me that the Linux/Ubuntu programmers took some measures to prevent access to encrypted data in the account whose password is changed in this manner.

If not, what is the point of encryption?

(Of course, this highlights my original point/question, which was whether computer security was only as good as the weakest link.)

---

### Post by TheFu on 2017-01-19
The best way to uncover the answer to something like this that I know is to bring up a virtual machine and try what you suppose.  

I'm tight on storage or I'd do it now. It only takes 15 min to install a base OS.

With all Unix systems (and Windows), if you have physical access to the machine, then security can be bypassed for system logins with a little effort ... except if there is whole disk encryption.  There are documented techniques for how to recover encrypted data depending on which type of encryption has been used.  If you are trying to keep a sibling out of your stuff, then HOME directory encryption is probably sufficient. I wouldn't trust it for corporate data, mainly because it has lots of gaps on the OS and if the OS is compromised, everything is lost.  BTW, that is a concern for whole disk encryption too, but the attack vectors for access are much smaller.

If someone can gain root on a Unix machine (really not THAT hard thanks to design decisions and bugs), they can change anything. Some distros have SELinux enabled by default, which can prevent root from having this sort of access.  But they shouldn't be able to access sufficiently encrypted storage. They can attack that encryption.  If it is trivial enough, it can be broken.  Long, random, passphrases are the best defense plus 2FA or 3FA for access to encrypted storage.

Every OS has similar issues. Privilege escalation is a problem for all of them. That is how "jailbreaking" an iphone works.  That is how gaining root on Android works. That is why Windows can be hacked.  It isn't hard to find methods and techniques to do this on every OS out there.

---

### Post by ian-weisser on 2017-01-19
> **parminides said:**
> I hope one of you can reassure me that the Linux/Ubuntu programmers took some measures to prevent access to encrypted data in the account whose password is changed in this manner.

Of course they did.
Your passphrase to mount and decrypt is not related to login...except for convenience
When you change your login password, but forget to change your ecryptfs mount password, you will find your system crashing upon login to your account (can't mount /home).

TheFu is right - test it yourself. If you find a hole, please file a bug to close it.

---

### Post by parminides on 2017-01-19
> **TheFu said:**
> The best way to uncover the answer to something like this that I know is to bring up a virtual machine and try what you suppose. 

The method requires GRUB, so I wouldn't know how to do it with a virtual machine. I don't know if I have the nerve to attempt it with a physical machine. It might deny subsequent access to my files if something goes wrong.

> With all Unix systems (and Windows), if you have physical access to the machine, then security can be bypassed for system logins with a little effort ... except if there is whole disk encryption. [...] If you are trying to keep a sibling out of your stuff, then HOME directory encryption is probably sufficient. 

If this is true, then why bother with home folder encryption at all on a computer only used by one person? If the computer is shut down, the bad guy would have to have physical access to the machine to get to the files. And if the machine is running (logged in by user with encrypted home folder), then the files are unencrypted anyway! So what's the point?

I'm trying to understand security and privacy issues better in this golden age of hacking, but it looks like home folder encryption isn't all that it's cracked up to be. Would someone correct me if I'm wrong? I'm trying to make my files more secure.

BTW, does whole disk encryption mean the whole disk is encrypted or just the partition containing the OS? I recently did a fresh install of Ubuntu 16.04 (dual boot with Windows), and the whole disk encryption option was grayed out. I assumed that it was because other things were on parts of the "whole disk." So is whole disk encryption not available if the disk has multiple partitions with multiple operating systems?

P.S. I read somewhere that Ubuntu did not allow whole disk encryption, but since this option was given (although grayed out), I assume that they have changed their policy.

---

### Post by TheFu on 2017-01-19
A proper VM still uses grub.  You can test most things in this sort of VM, just not really fast graphics, but pretty much everything else.

On 16.04, Ubuntu has a form of full disk encryption - it leaves the 500M boot partition unencrypted, but everything else IS encrypted.  The installer doesn't handle dual-boot for this choice. Other Linux OSes should, since their installers are much more feature rich with more complex storage situations.  It is frustrating to me too.

You can encrypt all the storage connected to the system, if you like. I use dm-crypt/LUKS on an external SSD with LVM. There isn't a GUI for this.

For the types of questions you are asking, you really need to start using VMs and testing yourself. It is easy for someone to misunderstand your true meaning and provide an incorrect answer for your specific question.

---

### Post by ian-weisser on 2017-01-19
> **parminides said:**
> If this is true, then why bother with home folder encryption at all on a computer only used by one person? If the computer is shut down, the bad guy would have to have physical access to the machine to get to the files. And if the machine is running (logged in by user with encrypted home folder), then the files are unencrypted anyway! So what's the point?

Two complimentary answers:
1) This is precisely why single-directory encryption went out of fashion around 2010-2012 in favor of whole-disk encryption.
2) Encryption of any type protects only data at rest. Data while you are logged in must be protected by other means.

---

### Post by parminides on 2017-01-19
I will test the password change method and see if it allows access to encrypted home folder. I use vmplayer for virtual machines. I've never seen a grub menu in any of my virtual machines. If I can't figure out how to do it, I'll try the change password method on a physical machine.

If home folder encryption went out of fashion circa 2012, what is the current opinion about installing the home folder on a separate partition? That used to be a popular choice in the past, but I'm not seeing much discussion about it any more.

Thanks for all your help. I'm sincerely trying to figure out the most secure way to do things. I spent half a day yesterday convincing myself that the warnings in chkrootkit and rkhunter were false positives!

---

### Post by ian-weisser on 2017-01-19
> **parminides said:**
> what is the current opinion about installing the home folder on a separate partition? That used to be a popular choice in the past, but I'm not seeing much discussion about it any more.

'Not much discussion' usually means 'out of fashion'.
Fashions change. That's why they are called fashions.

A separate home partition is a very wise choice...for certain types of users. It's an unwise choice for some others. It's neither wise nor unwise for many, a matter of personal preference.

---

### Post by parminides on 2017-01-19
> **ian-weisser said:**
> A separate home partition is a very wise choice...for certain types of users. It's an unwise choice for some others. It's neither wise nor unwise for many, a matter of personal preference.

It always sounded like a great idea to me, but I was afraid something would go wrong. There were plenty of horror stories of people who bricked their machine and/or data, so I never tried it.

In the Golden Age of Hacking, though, I'm more inclined to explore things like that.

EDIT: It appears that separate home partition is more for convenience when doing a fresh install than it is for security. For instance, the user doesn't have to restore files after new installation. If the home partition were encrypted, then it would seem that all users would have to have the passphrase! That's not cool. If each user had his/her own separately encrypted home folder, then it seems no better a situation (with respect to security) than users encrypting their home folder on the OS partition.

---

### Post by TheFu on 2017-01-19
> If the home partition were encrypted, then it would seem that all users would have to have the passphrase! That's not cool.
This is not true. There are 8 slots for passphrases in dm-crypt/LUKS.  The cryptsetup manpage explains that.

I don't use a different HOME partition on most of my systems, but my HOME directories tend to be very small. No real data or media is kept there. I have network storage for that stuff.

The #1 security thing people can do is have daily, automatic, versioned, backups. I keep at least 30 days, but on higher risk systems, have 60, 90, even 120 days. With an efficient backup tool, this really isn't that much extra storage for configs, system settings, ... basically, everything except large media files.

The #2 security thing is to be patched and run a supported Linux OS.

This is sufficient for nearly all end users running desktops. Everything else is striving for that last 2% of more security. If you are doing high-risk activities, use a VM, take a snapshot and replace that as needed - daily, weekly, whatever.

For portable devices, whole disk encryption makes sense, so when they are stolen or lost, the data and access to your other accounts from the machine aren't at risk. This also helps when a storage device needs warranty service/replacement. Nice to be able to send a failed disk to the vendor without concern of photos showing up anywhere.

If one of the 6 virtualization tools from VMware doens't do what you need, perhaps using the solution that google, redhat, NASA, rackspace and thousands of huge VM providers around the world choose would make sense?  That is KVM + QEMU.

---

### Post by parminides on 2017-01-20
I tried the password change technique described at [http://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password](http://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password). I tried the main one in the article and a similar method described in one of the comments ("The Drastic Measures"). Both involved booting to recovery mode in the grub menu. (I skipped other methods in the comments that were based on booting to live medium.)

The good news is that when I changed the password by either method, it did not allow me to access my encrypted home folder. In fact, the login accepted my password, made the characteristic Ubuntu sound, and then looped back to asking for my password again. After I used the grub menu recovery mode technique to change back to the original password, all was well.

More good news is that both grub menu recovery mode techniques can be disabled by issuing a "sudo passwd" command to set a root password. Do this when logged in normally. Then the grub menu won't allow the root prompt without the root password.

I suspect that the live media methods cannot be disabled this way. My guess is that they will nonetheless lead to the same endless login loop I encountered. One of them involves making changes to /etc/shadow (same as "The Drastic Measures" above).

---

