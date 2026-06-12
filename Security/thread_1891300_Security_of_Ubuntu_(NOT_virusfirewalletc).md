---
title: "Security of Ubuntu (NOT virus/firewall/etc)"
date: 2011-12-05
forum: Security
---

### Post by drdjnicholls on 2011-12-05
Hi,
I have just started to use Ubuntu as I wanted to give Linux a try and I 
was getting very weary about reading about Windows security failings. This is not only the umpteen updates regularly supplied to 'plug a hole' but other things. For example Windows XP stores personal information in a swap file/page file and countless other logs are present. Therefore, whenever I sell a PC I am not satisfied with the various cleaning programs available but I do a secure wipe of everything on the hard disc.
I see there is discussion about ubuntu security in respect of viruses, malware and firewalls, but nothing (I can see anyway) about ubuntu and personal security, e.g., what ir logs about a user (programs used, passwords, etc) - is that because no such thing occurs or because no one has asked about this topic?
Thanks
David

---

### Post by Dangertux on 2011-12-05
> **drdjnicholls said:**
> Hi,
I have just started to use Ubuntu as I wanted to give Linux a try and I 
was getting very weary about reading about Windows security failings. This is not only the umpteen updates regularly supplied to 'plug a hole' but other things. For example Windows XP stores personal information in a swap file/page file and countless other logs are present. Therefore, whenever I sell a PC I am not satisfied with the various cleaning programs available but I do a secure wipe of everything on the hard disc.
I see there is discussion about ubuntu security in respect of viruses, malware and firewalls, but nothing (I can see anyway) about ubuntu and personal security, e.g., what ir logs about a user (programs used, passwords, etc) - is that because no such thing occurs or because no one has asked about this topic?
Thanks
David

Well it sounds like you're asking more about privacy than security. First off privacy and security are NOT the same thing. 

That being said - I'll answer the questions as you threw them out there.

> 
This is not only the umpteen updates regularly supplied to 'plug a hole' but other things.


Security updates are present and important in all major operating systems.


> 
For example Windows XP stores personal information in a swap file/page file and countless other logs are present.


Swap space is utilized much the same as in Windows. If personal information is swapped it may stay there until a reboot -- longer if forceable forensic techniques are used to extract it. This goes for memory too (the freezing technique).  Log files are present and very detailed in Linux (probably more so than Windows). There shouldn't be any outright logging of personal information from the OS itself. That being said, browser caches, stored credentials etc all apply. As far as storing passwords, depending on how you configure things like the keyring, your browser and anything else you put passwords in, they may be stored and may be able to be extracted. As far as your actual user password under Ubuntu it's hashed slightly stronger than Windows hashing (by default) though they can be made the same level of strength.

In most respects Windows and Ubuntu are similar in terms of both Security and Privacy -- they have to be in order to target the market they target. That being said the methods for securing either are slightly different in many respects.

I hope this was helpful.

---

### Post by drdjnicholls on 2011-12-05
*I hope this was helpful. *

Yes, it was. Thank you.

---

### Post by Megaptera on 2011-12-05
drdjmicholls,
Not sure what your needs are but you may be interested in:

Ubuntu Privacy Remix "The goal of Ubuntu Privacy Remix is to provide an isolated working environment where sensitive data can be dealt with safely. The system installed on the computer running UPR remains untouched, UPR is not intended for permanent installation on hard disk" [https://www.privacy-cd.org/en](https://www.privacy-cd.org/en)

or quantOS which "is a hardened Linux distribution, based on Linux Mint 11, for secure daily use as a desktop operating system.
quantOS leverages AppArmor application security profiles, Arkose Desktop Application Sandboxing and Vidalia for creating secure Tor connections to enhance online privacy." [http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/quantOS-70412.shtml](http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/quantOS-70412.shtml)

---

### Post by snowpine on 2011-12-05
The only three privacy tips you really need are: Don't give other people physical access, encrypt your hard drive, and when you sell a computer, wipe the drive with a utility such as dban.

Those are in addition to general online privacy/identity best practices, which are independent of operating system.

---

### Post by Paddy Landau on 2011-12-06
> **Dangertux said:**
> Swap space is utilized much the same as in Windows. If personal information is swapped it may stay there until a reboot -- longer if forceable forensic techniques are used to extract it.
However, as from 11.04, if you choose to encrypt your home folder when you install Ubuntu, it will also encrypt your swap space. Thus, you won't need to worry about the swap space.

---

### Post by Dangertux on 2011-12-06
> **Paddy Landau said:**
> However, as from 11.04, if you choose to encrypt your home folder when you install Ubuntu, it will also encrypt your swap space. Thus, you won't need to worry about the swap space.

This is true, however swap space like encrypted home folders are encrypted at mount. So for the entire duration you're swap space is in use during a single boot it will be accessible plain text.

Hope this helps

---

### Post by Paddy Landau on 2011-12-07
> **Dangertux said:**
> So for the entire duration you're swap space is in use during a single boot it will be accessible plain text.
Correct me if I'm wrong: as soon as you power off the computer, the swap space is not readable as it is encrypted.

---

### Post by Dangertux on 2011-12-07
> **Paddy Landau said:**
> Correct me if I'm wrong: as soon as you power off the computer, the swap space is not readable as it is encrypted.

This is correct however in the same applies in Windows Vista/7 using encryption as well. So I guess the point is if you're looking at it in terms of security on a desktop system. Think about the likely avenue of compromise, how is a typical desktop system going to be comrpomised?

Most likely through the browser or some other userland app right? Okay... For this to happen swap would be mounted as would the home filesystem, since you'd be logged in, thus essentially making encryption a moot point since the home filesystem and swap would both be readable plain text.

Hope this helps.

---

