---
title: "Questions about ClamAV"
date: 2019-09-10
forum: Security
---

### Post by dagmann on 2019-09-10
I installed ClamAV per this webiste, [https://kifarunix.com/how-to-install-and-use-clamav-antivirus-on-ubuntu-18-04/](https://kifarunix.com/how-to-install-and-use-clamav-antivirus-on-ubuntu-18-04/)
No problems where encountered.

However I don't understand how to verify that ClamAV is actually running?
Nor how to check for any viruses/etc that is might have found?
If a virus/etc was found does this product popup a message?

I assume there are no graphical interfaces for this product?

Linus/Ubuntu noob here.

Thanks in advance.


Also I don't understand the following commands:
nice -n 15 clamscan && clamscan -ir /
cpulimit -z -e clamscan -l 50 & clamscan -ir /

---

### Post by deadflowr on 2019-09-10
There is a gui, clamtk.
It's in the repositories.

---

### Post by dagmann on 2019-09-10
thanks deadflowr

---

### Post by SeijiSensei on 2019-09-10
If you're expecting an always-on virus monitoring program like you find in Windows, there is no such thing for ClamAV.  Instead you should run the [command]("https://linux.die.net/man/1/clamscan")

```
sudo clamscan -r /
```

and it will scan all the directories starting at the root ("/").

Running clamscan with the "-ir" switches will print only infected files.

The commands you list are designed to run clamscan without it taking over the entire machine.  See the manual page for [nice]("https://linux.die.net/man/1/nice") for more details.  Nice allows you to control how much attention the scheduler pays to a particular program and whether to give it priority over the other (hundreds of) programs running on your system.

---

### Post by dagmann on 2019-09-10
Thanks SeijiSensei

maybe I will try some other antivirus software

---

### Post by TheFu on 2019-09-10
> **dagmann said:**
> Thanks SeijiSensei

maybe I will try some other antivirus software

Why?  Might be worth reviewing the sticky threads at the top of the security sub-forum first.

---

### Post by Rubi1200 on 2019-09-11
I tried clamAV once upon a time, many moons ago.

Conclusions:

1. there is no real need for antivirus on Linux unless you are sharing files with/between Windows users and machines

2. you need to change your mindset; Linux is not Windows. Are there exploits for Linux? Yes of course. But the system as a whole is secure and not exposed the way a Windows machine would be

3. security comes in layers; antivirus is not a one size fits all solution

I have been using Linux for over 15 years now and have never once seen a virus or other exploit that would even make me think I need "antivirus"

Read the stickies at the top of this forum, inform yourself with online research.

Good luck!

---

### Post by (kyT%0) on 2019-09-11
> **dagmann said:**
> maybe I will try some other antivirus software

please do tell if you find >>>some other antivirus software?<<< other than clam(+1) or sophos(-1).

---

### Post by TheFu on 2019-09-11
There are commercial vendors of Linux AV/AM software.  Many also sell Android AV/AM software. 
[https://www.eset.com/int/business/endpoint-antivirus-linux/](https://www.eset.com/int/business/endpoint-antivirus-linux/) is one. They have a personal license and a multiple-device personal license which isn't on their website. Was talking with a guy in their sales a few weeks ago. I don't recall the exact name of the 3-5 device license version. Sorry.   My company had E&O insurance which required that we ran current AV with current signatures.

My email gateway server runs clamav on every inbound email. I can't remember the last time it quarantined anything. It blocks all sorts of things besides positive virus discoveries.

But most AV is only about 50% effective.   To effectively handle viruses/malware, run high risk programs in a container that cannot write to the computer's storage. That is what Canonical's snap packages are about or if you don't have RAM to burn, check out sandboxing tools like firejail.  There are other options.

---

### Post by dagmann on 2019-09-11
I found this [https://www.eset.com/us/home/antivirus-linux/](https://www.eset.com/us/home/antivirus-linux/).

---

### Post by (kyT%0) on 2019-09-11
40 bucks for an antivirus for an operating system which is free...naaah.

thanks for the share & please do share if you find any more.

---

### Post by dagmann on 2019-09-12
Well Clamtk always show that there is an update available. What update, clamav or clamtk?  Also when I run Clamav in the Terminal a message states that it is not current.
They both installed from the repository so why wouldn't they be up to date?

Anyway how can I get and install the most current version of ClamAV and ClamTK?

---

### Post by (kyT%0) on 2019-09-12
> **dagmann said:**
> What update, clamav or clamtk?

clamav. but be rest assured your virus definitions should be up-to-date.

> **dagmann said:**
> Anyway how can I get and install the most current version of ClamAV and ClamTK?

[https://www.clamav.net/documents/upgrading-clamav](https://www.clamav.net/documents/upgrading-clamav)

---

### Post by dagmann on 2019-09-12
Okay, I reinstalled Clamav.  When trying to update the signatures with 'sudo clamav' command I get the message:   'Problem with internal logger (UpdateLogFile = /var/log/clamav/freshclam.log).'
Anyone know what that message means?

---

### Post by (kyT%0) on 2019-09-12
clamscan -V : check version 

sudo freshclam : update

---

### Post by dagmann on 2019-09-23
Solved

---

### Post by mcyber4 on 2019-09-26
> **TheFu said:**
> 
But most AV is only about 50% effective.   To effectively handle viruses/malware, run high risk programs in a container that cannot write to the computer's storage. That is what Canonical's snap packages are about

Interesting, didn't know that. So using a firefox snap should increase security a lot? I was hacked a year ago with a UEFI rootkit and have the impression via a Firefox bug. (excecuting malicious code in a simple email reading online only)

Since I only boot Win10 with Eset as it also scans the UEFI bootsector. Oh well I have used Linux for about 20 years without a antivirus. Now suddenly I have a different view...

---

### Post by dagmann on 2019-09-26
What is a 'Canonical's snap package' ?

---

### Post by deadflowr on 2019-09-26
> **dagmann said:**
> What is a 'Canonical's snap package' ?

snaps are a new package architecture Ubuntu's parent company/sponsor (Canonical) has developed.
They're restricted apps by default, in terms of what access they have to the rest of the system.
[https://en.wikipedia.org/wiki/Snappy_(package_manager)]("https://en.wikipedia.org/wiki/Snappy_(package_manager)")
[https://snapcraft.io/]("https://snapcraft.io/")

One of the benefits of the restricted setup is it allows developers to publish their apps quickly.
(since if the app breaks only the app should break, so the rigorous testing a normal package may require isn't needed)
This is couple with snaps have a revisioning system in-place which always keeps the last version in case said failure of an update happens.
That allows you to rollback to that last version with ease.
(Unfortunately that ease is still limited to command line only, afaik)

---

