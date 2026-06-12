---
title: "Security Concern over WSL"
date: 2024-08-14
forum: Security
---

### Post by werewulf75 on 2024-08-14
I sometimes have to dual-boot a small Windows 10 partition for a few specialist apps and sp. hardware, which has the Windows Sub-system for Linux. Since this was installed, I noticed that Windows now reads ext partitions in the Storage Devices control panel, and even in a file manager. I am rather concerned that any access of Windows to my Ubuntu partitions presents a security risk or at the very least a privacy one.

Can anybody shed any light on this?

---

### Post by currentshaft on 2024-08-14
,

---

### Post by werewulf75 on 2024-08-14
> **currentshaft said:**
> You don't even need WSL to do this.

Use full volume encryption with LUKS if you value privacy.
It's my Linux system drives that so far I'd been reluctant to encrypt on account of there being 3 Ubuntu systems and a Fedora one. I keep data inc. backups on fully encrypted USB drives and sticks, with one small unencrypted stick for quick data for the day etc. Also, I use Veracrypt for encryption, which won't encrypt Linux system disks. 

Thanks for the suggestion, think I'll give it a go with LUKS. Don't want Windows to have the slightest access, don't trust it at all even after removing most of the spying stuff.

---

### Post by currentshaft on 2024-08-14
/

---

### Post by werewulf75 on 2024-08-14
> **currentshaft said:**
> Keep in mind, malicious software on Windows can still affect the unencrypted parts of all those Linux operating systems, including the ability to keylog passwords to encrypted containers to decrypt later.
That seems to require that Windows - not running when a Linux system is booted of course - somehow could pass on malicious software that could run on Linux, surely.

Also, Windows system has a load of privacy/security apps inc. a very secure VPN running that among them intercept just about anything malicious or privacy infringing before it could get onto the system. (I have much the same apps on my Linux systems as well.)

---

### Post by currentshaft on 2024-08-14
hoo

---

