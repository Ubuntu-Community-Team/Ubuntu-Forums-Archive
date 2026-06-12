---
title: "Mounting Virus-infected HDD Safe?"
date: 2013-07-11
forum: Security
---

### Post by JonasDeMoor on 2013-07-11
Hi all,

I'm running Ubuntu 12.04 at the moment on a single hard drive. Now, I want to add a second drive from an old PC: I intend to use this drive for backups from CloneZilla.

The computer where the drive is in to, for the moment, is running Windows XP and isn't connected to the internet, but it can't boot anymore.

I'm a little bit worried about possible viruses that may reside on the hard drive. Can you safely mount the drive into Ubuntu/Linux and format it without having to worry about viruses?
I know Windows viruses won't work on Linux, but I'm just a little bit concerned.


I was thinking about using GParted Live to format the drive first and afterwards boot into Ubuntu. 

What do you think is the best solution?


Thank you in advance.

P.S. Sorry for bad English

---

### Post by deadflowr on 2013-07-11
Go the livecd method.
At least then you won't have to worry about cross pollution into your existing Ubuntu drive as it won't be mounted.
And for the super paranoid, unplug the Ubuntu drive to make doubly sure.

Also, look into running S.M.A.R.T to see if the XP drive has actual drive problems, aside from nefarious code.
I think smart is included in the 'disks' program. (formerly disk utility).

---

### Post by ikt on 2013-07-11
> **JonasDeMoor said:**
> I'm a little bit worried about possible viruses that may reside on the hard drive. Can you safely mount the drive into Ubuntu/Linux and format it without having to worry about viruses?

Yes. The likelihood of anything happening is very tiny. You can do what was recommended above, but anecdotally my father runs a computer repair business, he plugs hard drives into an ubuntu machine to make sure the files are there (not a dead hard drive), then backs them up using clonezilla and we haven't had any issues regarding malware.

---

### Post by JonasDeMoor on 2013-07-11
Hello,

Thank you very much for the fast replies: I will go for the Gparted Live method :)

---

### Post by HermanAB on 2013-07-11
Yeah, don't worry, using Linux, you are safe from Windows malware and if you use the official repositories only, then you don't have to worry about Linux malware.

---

### Post by SeijiSensei on 2013-07-11
If you mount the drive into a Linux box, Linux itself will pay no attention to the device whatsoever other than to observe its existence during boot.  It will not mount any partitions on the drive unless you request that it do so with a "mount" command or the GUI equivalent.  That command will require root privileges as well.

---

### Post by Hungry Man on 2013-07-12
Even if you mount the drive it won't matter. The application can't start itself without exploiting some type of 'autorun' vulnerability or something, which would be very surprising. I suggest using one of those antivirus bootcds to scan it, and then do whatever it is you need to do.

---

### Post by Tom_ZeCat on 2013-07-16
> **Hungry Man said:**
> Even if you mount the drive it won't matter. The application can't start itself without exploiting some type of 'autorun' vulnerability or something, which would be very surprising. I suggest using one of those antivirus bootcds to scan it, and then do whatever it is you need to do.

I was about to suggest that.  The Kaspersky Rescue Disk is actually a specialized Debian-based Linux distro with utilities and Kaspersky Antivirus added to it.  It's a free download as an ISO file (that you can make into a CD).  You can boot to it while wired to the Internet (easier than wireless usually) and then let it update its definitions and then scan an entire infected PC.   I've fixed up many Windows PCs with it.

---

