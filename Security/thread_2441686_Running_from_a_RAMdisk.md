---
title: "Running from a RAMdisk"
date: 2020-04-25
forum: Security
---

### Post by Skaperen on 2020-04-25
the idea i have is to run my system with all the "system files" copied to a ramdisk, using the system on the mounted ramdisk.

in addition to running from a ramdisk, the origin files used to make these copies in the ramdisk will be unmounted. the disk and/or files holding the origin may also be encrypted. or the origin may be a read-only device.  or the origin may be accessed only over a network, possible after a network boot.

upgrades to the system would be carried out in a separately booted copy.

propagation of the upgrades to the origin master copy would be carried out manually or in isolation from any running copy.

consider that i am running an application i have installed which is suspected of have a backdoor or other means of upgrading its own version or installing or replacing other software or packages on my system(such as a video conferencing application that uses the developer's network). normal attempts to do this would usually happen with no errors but only the ramdisk would be modified. the next time the system is booted,a fresh copy of the unmodified system will be loaded. if this software is aware of the ramdisk technique,it may try to access the origin,which can easily be made to always fail if only a read-only device (an SD card) is available or restricted access (many options) over a network is used.

to safely upgrade an SD card in a laptop i would first switch it to read/write then boot it. an added init program would detect that it is in read/write mode and carry out the upgrade or suggest that i login to do that. it would not finish bringing up the system in the usual manner. even safer upgrades could use other boot media (USB memory stick) to modify the SD card.

---

### Post by EuclideanCoffee on 2020-04-26
So this is the reverse of a swap file. You place all disk space into RAM.

The problem is, I'm not sure what you're mitigating unless you want to destroy the session.

If you are compromised, there is no way to verify that your RAM data is secured unless each file is deterministic and can be verified via the network of other, hopefully non-compromised devices. Your best bet is simply to run only software and files you know are reproducible, which can be done following this system. It is like blockchain where multiple machines must verify a result. [URL="https://srukle.dreamwidth.org/19637.html"]https://srukle.dreamwidth.org/19637.html

[/URL]If you intend for this to be for privacy concerns, I want to note that _**security is NOT privacy**_.

---

### Post by Skaperen on 2020-04-26
i chose RAM because it's cheap enough these days and is the fastest storage around (besides CPU cache) that can hold the whole system with plenty to spare (on a typical new system these days) and can persist until time to reboot or shutdown.  i don't understand your reference to "destroy the session". do you mean "dismiss the system that has been loaded"?

if the system is compromised, and you have a reason to check if it really is, what does it matter.  a clever attack can either prevent you from checking or make it appear to be unchanged. if we used non-volatile storage (like a spare SSD device) to hold the running system, the process of booting a new system could do a reliable check.  would it still matter now that the reboot took place?

my concern is in regard to a "persistent compromise".  if only RAM can be compromised, then it's not persistent.  this, as long as best practices are followed, like your password management.

this is not a perfect solution ... nothing can be.  but, at least, it is going to complicate the lives of all but the very best attackers, who have more interesting targets than any of us.

---

### Post by EuclideanCoffee on 2020-04-26
> i chose RAM because it's cheap enough

Ok, so you're concerned about price? Why? You'd still need to build the system to go into RAM disk and do what I wrote above, which takes work if you want it to be sustainable.

> 
do you mean "dismiss the system that has been loaded"?


Rephasing what I wrote doesn't provide value to this conversation, and it's rude.

The engineering term is SIGKILL init, but we simply use the system call reboot.

> 
**_if the system is compromised_**, and you have a reason to check if it  really is, **_what does it matter._**  a _**clever attack**_ can either prevent you  from checking or **_make it appear to be unchanged_**. if we used non-volatile  storage (like a spare SSD device) to hold the running system, _**the  process of booting a new system could do a reliable check**_.  would it  still matter now that the reboot took place?


Oh, this checks the state of the system with fsck. We're not checking at this point if the system is compromised. We are checking if the system is sane. Can we rely that the files won't provide use output of garbage? The thing about this is that it's fairly simple. If the system cannot boot because the system files are corrupted and read as garbage, the system won't boot.

The kernel puts all that is the system into memory. The stored files provide space for the system, so when they are read to stdout which appears in tty (terminal).

>  my concern is in regard to a _**"persistent compromise"**_.  if only RAM can  be compromised, then it's not persistent.  this, as long as best  practices are followed, like your password management.

Ah, this is an APT.

You cannot defend yourself from an APT by placing everything into memory as the APT can read your memory. That is why it's feared.

It's impossible to have your entire system running as encrypted unless it's quite advanced technology (which is available but not open source).

> this is not a perfect solution ... nothing can be.  but, at least, it is  going to complicate the lives of all but the very best attackers, who  have more interesting targets than any of us.

Your solution already exists. This is an embedded device no doubt.

---

### Post by Skaperen on 2020-04-27
i don't understand what you wrote.  but there is enough semantics that i can guess possibilities.  if i am wrong then i must let you rephrase it.

a check could be added to my idea.  it would not be *fsck* because an ordinary attack would leave file system(s) in a normal state.  an ordinary attack might change files.  a checksum compare against a stored checksum reference stored where the attacker cannot change it would be a simple check.

a feature i would like to see added to all storage devices is a command to set a read-only mode that can only be unset by a full system hardware reset.  this storage would operate in an ordinary way after a reboot but after the system wants to exclude any possibility of compromise of its contents, it would set this read-only mode which would reject write or erase operations.  then the checksum can be stored on it and be sure that it cannot be changed by any malware.  the initial system that is first booted up can be on it, too.

> The kernel puts all that is the system into memory.

it does not put */usr* into memory.

i suspect you and i have different goals and are looking at this in different perspectives.  you want to prevent attacks that acquire data and i am looking at preventing attacks that change the system i am running (and, thus, can persistently acquire data, over time, even if entry of attacks becomes blocked in the future (bad CGI replaced on a web site, for example)).

> This is an embedded device no doubt.

i disagree.  this mimics an embedded device with a fast pre-loaded cache.  FYI, i have done system level development for a cable STB.

---

