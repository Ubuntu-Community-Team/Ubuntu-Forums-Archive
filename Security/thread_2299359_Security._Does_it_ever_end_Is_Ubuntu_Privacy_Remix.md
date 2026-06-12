---
title: "Security. Does it ever end? Is Ubuntu Privacy Remix next for me?"
date: 2015-10-17
forum: Security
---

### Post by mikodo on 2015-10-17
Here I am. Perpetual novice and casual user. Tinkering with limited knowledge, limited time, and old when I started with computers, and older now ...

I have in my "New Project" tasks, to use Ecryptfs for my "data", which is housed outside of ~ that symbolically links to it. So when I have the time to learn how to do this, I will be editing fstab to use mountall for /mnt/data as I do now, and I think mtab to mount and umount the Ecryptfs. Cool. That's better than how I do things now with Gnupg for sensitive data. I get to encrypt the whole folder of "data" rather than, just files with gpg.

I took a minute (only) to look at Ubuntu Privacy Remix. [https://www.privacy-cd.org/en/home-mainmenu-71/55-was-ist-ubuntu-privacy-remix](https://www.privacy-cd.org/en/home-mainmenu-71/55-was-ist-ubuntu-privacy-remix)

Oh dear. That looks really interesting. Is is next? Will I be suffering with Senile Dementia by the time I start to play with this?

Edit And, since it secures APT, I guess that rules out using it with my planned Ubuntu install's using Snappy Updates. Would I only use this for Debian and derivatives that uses APT?

Is there anyone here that uses this and may want to comment?

Thank you.

---

### Post by TheFu on 2015-10-17
Use whole drive encryption if you care about data security. Many reasons, including better performance. The Linux Foundation published their list of security tasks for their workstations. A link was posted in the security sub-forum. Good read.

Security never ends because the attackers don't stop.

Privacy is hard on the internet. There are no absolutes. A tiny mistake blows all privacy and even if we do everything correct, someone will have learned how to break the privacy. Using tor doesn't guaranty any privacy without extreme caution. It is non-trivial.

---

### Post by mikodo on 2015-10-17
Thank you, TheFu.

I was actually thinking of you, when I wrote that earlier post. I almost mentioned a quoted paraphrase from you. "Security is hard".

I'll be reading that stuff from the Linux Foundation. Thanks.

I also like what the Electronic Frontier Foundation is publishing for some topics too. I use their Privacy Badger extension for Firefox.

I'm trying to find ways to encrypt, but not the whole disk. Pity, I take your advice always as "Golden" and a privilege to be offered. I want to have my ~ unencrypted to allow for the commercial VPN I use. I understand I cannot encrypt where its' service is executing from. But, I can encrypt anything else and, I thought I would start with my "data" on a different partition.I need to keep thinking about this.

---

### Post by grahammechanical on 2015-10-17
It seems to me that we could achieve the same end using a Ubuntu live session from a DVD+R disc with all data stored on a removable USB memory stick and without having a connection to a router and with the WiFi adapter turned off.

And if you want to be true to paranoia you will not trust these people either. Oh, and don't forget to weld the case of the computer to prevent anyone putting a spy device inside the case.

Regards.

---

### Post by mikodo on 2015-10-17
Thank you, Graham.

I think my sentiments are the same.

It just struck me as, here is something else I have to think about. Not something at "first blush" I could see myself doing.

Yours and others comments are filed away for more thinking, "down the road".

---

### Post by TheFu on 2015-10-17
I find it hard to believe that any program would be aware when whole disk encryption happens.  Do it below LVM and the programs won't know.
You'll want to protect against the "evil mail" attack.

---

### Post by mikodo on 2015-10-17
> **TheFu said:**
> I find it hard to believe that any program would be aware when whole disk encryption happens.  Do it below LVM and the programs won't know.
You'll want to protect against the "evil mail" attack.

Oh, great!

I will search for reading to learn about that.

Thank you!

---

### Post by mikodo on 2015-10-18
Alright. I learned tonight. A lot. I knew nothing about the difference of encrypting a file system, like Ecryptfs does and encrypting Block devices that can encrypt a list of things I would not use (like software Raid) and for things I might use including, disks, partitions, and Logical Volume Management (LVM) physical volumes. 

So. A good starting point for full disk encryption for me *below the file-system data, I think is to use what Ubuntu supports for Block devices namely, Dm-crypt.

A couple of links to start my learning journey. I will be reading more later.

[https://wiki.archlinux.org/index.php/Disk_encryption#Block_device_encryption](https://wiki.archlinux.org/index.php/Disk_encryption#Block_device_encryption)

[https://wiki.archlinux.org/index.php/Dm-crypt/Device_encryption#Cryptsetup_usage](https://wiki.archlinux.org/index.php/Dm-crypt/Device_encryption#Cryptsetup_usage)

Linux Foundation, "Linux Workstation Security Checklist": [https://github.com/lfit/itpol/blob/master/linux-workstation-security.md](https://github.com/lfit/itpol/blob/master/linux-workstation-security.md)

I got it. Full disk encryption. I'm going to try to transition to LVM's for next install. Protect desktop from intruders, (Evil Maid) and use the recommendations of the Linux Foundation for no Firewire, etc, (think BIOS/UEFI cracking). *And, everything else they suggest. ("Anti-Evil Maid" is above me right now).

I was already talked out of using TOR. (Besides, what for, for me. And, it only invites people to try to figure out who/what is coming out of the 3rd exit node).

Thank you, so much.

---

### Post by Bucky Ball on 2015-10-18
*Thread moved to **Security**.*

---

