---
title: "Self-encrypting drive VS full disk encryption VS volume encryption"
date: 2018-02-20
forum: Security
---

### Post by fizikz on 2018-02-20
What is the current recommendation on using one or several of these methods? 

With **self-encrypting drives** (SED) I see the benefits of hardware acceleration, invisibility/seamlessness to the OS and users, and the ease of securely erasing the drive nearly instantly. On the downside, the encryption implementation is not open to public scrutiny possibly raising questions about its security, and it might lack flexibility: can such a drive be used in external enclosures or as a secondary drive? 

**Full disk encryption** (I think) does away with those cons and offers the transparency of software, at least in open source software cases, and allows more flexibility, but comes at the cost of more user involvement in its setup. 

**Volume encryption** seems to be the most flexible, leaving encryption only for chunks of data that warrant it and keeping the rest of the system simpler.

In addition, the methods could be combined: eg. enabling SED on a drive that supports it, and within it using volume encryption for sensitive data.

Is this summary accurate? What is recommended considering both security and usability perspectives?

---

### Post by TheFu on 2018-02-20
I consider SED in the same way I think of HW RAID.  In a business environment, being tied to specific hardware might be acceptable if the other gains warrant the lack of flexibility.

FDE is what I use ... well, as much as is easily possible with Ubuntu.  It is 1 checkbox during the install, so not really THAT much user effort. At least on a single disk system.  In the Ubuntu FDE setup, /boot/ is **Not** encrypted on 16.04 or earlier versions.  The rest of the OS is.  This is necessary for the disk to be unlocked using a boot shim.  It does leave the system open to an "evil maid" attack, if you allow boot from the HDD and don't use some external boot storage that is never out of your sight.  LUKS/dm-crypt are the typical method on Linux.  Performance is usually 3% less than native for the storage.

I'm not certain what "volume encryption" means based on your description.  That sounds more like an encrypted directory than an encrypted volume.  Normally, something like encryptFS and encfs are used for these needs. Performance characteristics are significantly lower than for FDE methods.  

dm-crypt/LUKS can be used at the full partition level or at the LVM LV level.  I use it at the partition level and setup PVs, VGs, and LVs inside the partition, which makes this very flexible.

dm-crypt allows 8 slots for a passphrase to be created, so that multiple users don't know each others' decryption information.  It is also possible to use 2FA with dm-crypt, in a way.

Regardless of the encryption method used, having great backups is mandatory.  Proper encryption makes data recovery nearly impossible, since the data appears to be random on the disk. Data recovery tools cannot handle physical or logical corruption of data, so backups are really the only solution.  If you are unable or unwilling to have automatic, versioned, backups, it is best to avoid encryption completely.  IMHO.

I tried to use the built-in Ubuntu HOME directory encryption a few years ago and found that my system-level backups didn't work.  Performance was definitely slower.  Plus having only a portion of the data encrypted means it was possible for an attacker to get a foothold in the OS and still gain access to the decrypted data once I logged in (causing the directory to decrypt).  Doing something similar with FDE is significantly harder.

With FDE, the swap for the OS is also encrypted.  Swap can be read by an elevated process to pull sensitive data using tools already on the system.  For fun, run a password manager, unlock the passwords, and use a memory tool to find some passwords.  The a quality password manager is locked, everything should be encrypted in RAM, but when it is unlocked ... well, then those are available.  Be very careful using a browser addon for password management.

Also, whenever using encryption, it is very important to not use hibernation or standby modes. Shut down the system completely. This makes the data at rest secure.

Anyway, those are my thoughts.

---

### Post by fizikz on 2018-02-22
Thanks, TheFu. I had to read up on a lot of what you mentioned. 

FDE using LUKS seems to be the preferred method for linux, but I dual boot, so it seems FDE is not an option.

The setup I had in mind was to dual boot Windows (NTFS) and Ubuntu (ext4) and also have a shared data partition (NTFS? comments?). Previously I've used Truecrypt for shared partitions which worked well in that it could be accessed from both OSes, so the default in my mind was to stick with its successor, Veracrypt. 

Which of these scenarios makes the most sense:

- Unencrypted Windows, unencrypted Ubuntu partitions, and Veracrypt encrypted shared partition (maybe simplest)
- same as above but with SED enabled
- LUKS on Ubuntu partition, Windows partition either encrypted or not, Veracrypt encrypted shared partition
- something else?

Concerns: I'd like to be able to access the drive when mounted in a hard drive dock or external enclosure, which is how I've migrate data in the past upon upgrades. The ability to mount one OS's filesystem from another (i.e. access Windows from Ubuntu) is rarely used but sometimes helpful to avoid having to reboot into Windows to fetch some file.

The problem of physical or logical data corruption with encryption is scary. How do the track records of the different methods (SED, LUKS, Veracrypt, etc) compare on this point?

I know I haven't been diligent enough with backups so far, only manually copying over the most important files to an external drive. :/ What's a recommended solution for automatic versioned backups?

I do shut down my laptop when moving it, but it's rare and 99.9% of the time, my system is running 24/7. It makes me wonder whether I should bother with fancy encryption setups.

---

### Post by TheFu on 2018-02-22
Lots of good questions.  Many have only opinion for an answer. That means there are lots and lots of different methods. Hopefully others will chime in with their opinions, since mine will be warped by my use and skills.

> **fizikz said:**
> Thanks, TheFu. I had to read up on a lot of what you mentioned. 

That is to be expected.  I'm constantly reading and learning.  Linux is huge.

> **fizikz said:**
> FDE using LUKS seems to be the preferred method for linux, but I dual boot, so it seems FDE is not an option.
 
I don't dual boot anymore.  Last time I did was around 2008-ish.  Since that time, virtual machines have completely changed my life.  The idea of having a mostly secure OS on the same platform as a completely insecure OS seems to defeat the purpose, to me.

> **fizikz said:**
> 
The setup I had in mind was to dual boot Windows (NTFS) and Ubuntu (ext4) and also have a shared data partition (NTFS? comments?). Previously I've used Truecrypt for shared partitions which worked well in that it could be accessed from both OSes, so the default in my mind was to stick with its successor, Veracrypt.  
See above.

> **fizikz said:**
> 
Which of these scenarios makes the most sense:

- Unencrypted Windows, unencrypted Ubuntu partitions, and Veracrypt encrypted shared partition (maybe simplest)
- same as above but with SED enabled
- LUKS on Ubuntu partition, Windows partition either encrypted or not, Veracrypt encrypted shared partition
- something else? 
Getting an entire Linux encrypted that doesn't use the default encryption settings from the installer is non-trivial.  It is HARD.  People do it.  I have have and I've tried.  I don't trust Veracrypt, but I don't trust Windows the last 2 yrs, since MSFT changed the license agreement.

> **fizikz said:**
> 
Concerns: I'd like to be able to access the drive when mounted in a hard drive dock or external enclosure, which is how I've migrate data in the past upon upgrades. The ability to mount one OS's filesystem from another (i.e. access Windows from Ubuntu) is rarely used but sometimes helpful to avoid having to reboot into Windows to fetch some file. 
I use network file sharing protocols for this.  My portable devices don't keep anything important. That's why servers exist.

> **fizikz said:**
> 
The problem of physical or logical data corruption with encryption is scary. How do the track records of the different methods (SED, LUKS, Veracrypt, etc) compare on this point? 
The built-in file system checks are it for logical issues.
Physical issues require monitoring SMART data periodically.  I run SMART tests weekly, automatic. If anything bad is happening, like relocated sector counts increase, then I start watching that more closely.  For example, the boot disk on my Plex/NFS/Calibra server sent this warning a few days ago ...
```
This message was generated by the smartd daemon running on:

   host name:  hadar
   DNS domain: example.com

The following warning/error was logged by the smartd daemon:

Device: /dev/sda [SAT], ATA error count increased from 108 to 112

Device info:
HGST HDN726040XXXXXX, S/N:K4J7VXXX, WWN:5-000cca-25ddfcXXX, FW:APGNWXXX, 4.00 TB

For details see host's SYSLOG.

You can also use the smartctl utility for further investigation.
The original message about this issue was sent at Thu Feb 15 22:41:36 2018 EST
Another message will be sent in 24 hours if the problem persists.
```
That was an email sent by the SMART testing subsystem.  All my Linux systems can send email to my mail server.  Logwatch is running on each system too, reporting in daily about changes.  The SMART data for that disk is only showing ATA errors. No other issues.  Probably a loose cable.  This Saturday morning, I'll reseat/replace the cable.


> **fizikz said:**
> 
I know I haven't been diligent enough with backups so far, only manually copying over the most important files to an external drive. :/ What's a recommended solution for automatic versioned backups? 
There are 100 different methods. Search these forums and the internet for methods that work for your needs.  I don't use image-based backups on Linux. Reinstalling the OS takes 15 minutes.  With a list of installed packages - takes about another 15 minutes to get those installed (worse case), and then customized settings and data are put back - usually 15 minutes.  So in 45 minutes, I can restore a system to a new HDD and it will look, act, almost 100% the same as it did when the backup was made.  I use rdiff-backup, but it is hardly the best for everyone.  It solves lots of issues that most other tools don't, however.  Plus, if a backup fails, it yells loudly, unlike some other tools.  These forums have lots of people using backup tools that can't actually be restored.  Sorta defeats the purpose for a backup.

> **fizikz said:**
> 
I do shut down my laptop when moving it, but it's rare and 99.9% of the time, my system is running 24/7. It makes me wonder whether I should bother with fancy encryption setups.

I encrypt all portable devices.  Had a smartphone stolen during an overseas trip a few years ago.  It was a pretty blatant theft.  The device wasn't encrypted and didn't have a passphrase.  All my contacts started being targeted by the gang responsible.  That same trip, a friend had his wallet and smartphone stolen too.  He worked for a huge telecom and was able to trace the locations for both our phones.  They were stolen in southern Europe. A week later his was in central Africa and mine was in Indonesia - places that don't honor the "reported stolen" IMEI database.

Since that time, I've changed to using a cheap netbook ($199 new worth about $75 now) and have a cheap smartphone ($20-$40) just for international travel.  Both are wiped before and after any trip.  Both are fully encrypted.  I use remote access back to my systems at home for any real computing needs.  ssh tunnels and VPN.  Not everyone can do this, but if there isn't much data local to the system, then having them stolen doesn't risk much either.

Virtual machines + remote access solves all sorts of security issues.

---

### Post by fizikz on 2018-02-26
That's a good point; securing your data in your own "personal cloud" and accessing remotely from nearly blank devices can be better from a management perspective, but it isn't always an option, especially for those who don't have a server set up at home or elsewhere.

I love VMs and actually that's what I've been using for most of my Windows needs, but it's not perfect and doesn't always work as well as a native installation. I think for now I'll still be dual booting, but can't wait to go all VM. Bit of an aside: I use Virtualbox; any other recommendations?

I'm still undecided as ever, and have more questions:

- Can LUKS be installed (easily) at installation on a partition, not whole drive? Preferably also working for a dual-boot setup.
- Can LUKS encrypted partitions/drives be accessed on external, non-boot drives?
- Can SED drives be accessed on external, non-boot drives?
- Why don't you trust Veracrypt? Alternatives?

---

### Post by TheFu on 2018-02-26
> **fizikz said:**
> That's a good point; securing your data in your own "personal cloud" and accessing remotely from nearly blank devices can be better from a management perspective, but it isn't always an option, especially for those who don't have a server set up at home or elsewhere.

I love VMs and actually that's what I've been using for most of my Windows needs, but it's not perfect and doesn't always work as well as a native installation. I think for now I'll still be dual booting, but can't wait to go all VM. Bit of an aside: I use Virtualbox; any other recommendations?


I don't have a "server" setup. It is a $150 desktop (it was $350 in 2010) with ssh allowed using ssh-keys from almost anywhere in the world. No password access.  I suppose that could be called "a server", but this isn't some $2500 machine.  For many people, a new $150 computer with a $50 CPU would be more than sufficient as a desktop.

I used virtualbox before Oracle bought SunMicro.  I used Xen for virtualization until 2011-ish. After that, I switched KVM and never regretted the switch.  But I'm not you.

> **fizikz said:**
> 
I'm still undecided as ever, and have more questions:

- Can LUKS be installed (easily) at installation on a partition, not whole drive? Preferably also working for a dual-boot setup.
 No. Not to my knowledge.

> **fizikz said:**
> 
- Can LUKS encrypted partitions/drives be accessed on external, non-boot drives?
 Yes.

> **fizikz said:**
> 
- Can SED drives be accessed on external, non-boot drives?
 I don't know. Probably.

> **fizikz said:**
> 
- Why don't you trust Veracrypt? Alternatives?
  I have suspicions for some situations.  Encryption is hard to do perfectly. Side-channel attacks are usually the first methods used.  The weakest part of most encryption solutions is the human.  I think using encryption on Windows is a waste of time, based on the EULA and ToS from MSFT.

---

### Post by fizikz on 2018-03-01
The more I read, the more I'm surprised at the lack of any simple solution for dual boot encryption on a single disk. It seems it is possible with some lengthy manual process: [https://askubuntu.com/questions/293028/how-can-i-install-ubuntu-encrypted-with-luks-with-dual-boot/293029](https://askubuntu.com/questions/293028/how-can-i-install-ubuntu-encrypted-with-luks-with-dual-boot/293029)

Complicated + encryption sounds like a good way to get into trouble..

Given my constraints of dual booting and having a shared partition accessible from both OSes, Veracrypt is the only option I'm aware of for the shared partition.

Veracrypt system/FDE encryption doesn't work for multi-boot setups, and I'm not using bitlocker, so I don't know if there's any option for encrypting Windows.

For the rest, I'm back to the scenarios I listed before:

- no OS encryption
- SED (if drive supports it)
- unencrypted Windows, complicated/manual LUKS encryption for Ubuntu (risky)

Is this really it?

I wanted to favor LUKS over Veracrypt, but given the constraints, it seems not possible. Actually, given the constraints maybe there's currently no solution...

---

### Post by fizikz on 2018-03-07
As a reference for myself and others, here are some additional resources with instructions on setting up encryption on dual-boot single disk systems.

Unencrypted Windows, encrypted linux:
[https://askubuntu.com/questions/721714/dual-boot-unencrypted-windows-10-encrypted-ubuntu-14-04](https://askubuntu.com/questions/721714/dual-boot-unencrypted-windows-10-encrypted-ubuntu-14-04)
[https://gist.github.com/Maddosaurus/90aa5ad6034f4d3e5468394d129a4ffa](https://gist.github.com/Maddosaurus/90aa5ad6034f4d3e5468394d129a4ffa)

Encrypted Windows, encrypted linux:
[https://aprescott.com/posts/dual-booting-windows-and-linux-with-encryption](https://aprescott.com/posts/dual-booting-windows-and-linux-with-encryption)
[https://forum.level1techs.com/t/guide-how-to-dual-boot-encrypted-instalations-of-linux-and-windows/115050](https://forum.level1techs.com/t/guide-how-to-dual-boot-encrypted-instalations-of-linux-and-windows/115050)

---

### Post by TheFu on 2018-03-07
And have you gotten any of these methods working?  

[https://ubuntuforums.org/showthread.php?t=2357627](https://ubuntuforums.org/showthread.php?t=2357627) is where Paddy worked through a how-to.
[https://help.ubuntu.com/community/ManualFullSystemEncryption](https://help.ubuntu.com/community/ManualFullSystemEncryption) is the result.

---

### Post by fizikz on 2018-03-09
I haven't tried any yet. Which worked or didn't work for you?

Thanks for the links. It looks nicely documented, works with UEFI, and has /boot encrypted too. I might that one first.

---

### Post by TheFu on 2018-03-09
> **fizikz said:**
> I haven't tried any yet. Which worked or didn't work for you?

Thanks for the links. It looks nicely documented, works with UEFI, and has /boot encrypted too. I might that one first.

I don't dual boot with Windows and won't allow Win8+ on my network or a currently patched Win7 (with the EULA modified to allow spyware).

For my needs, using virtualization was best. That removes the cross-platform requirement that you seek.

---

### Post by kevdog on 2018-03-11
Only my thoughts

Full disk encryption is great --- until something goes bad, then the data is usually unrecoverable.  I'm no hacking expert, however I had this problem before in the past.  I totally sucked. Although I see the theoretical benefit of Full disk encryption, I usually now work with volume or partition encryption.

---

### Post by fizikz on 2018-03-12
@kevdog Do you mean hardware or software full disk encryption? In any case, it seems FDE isn't even viable for dual boot single disk situations anyways.

As for the previous link on setting up encryption, kernel updates breaking grub is a pretty annoying bug: [https://help.ubuntu.com/community/ManualFullSystemEncryption/KnownBugs](https://help.ubuntu.com/community/ManualFullSystemEncryption/KnownBugs) Is there no solution for this yet?

Honestly, I'm surprised at how difficult it is to get encrypted dual boot set up. Surely this isn't an unusual use case.

---

