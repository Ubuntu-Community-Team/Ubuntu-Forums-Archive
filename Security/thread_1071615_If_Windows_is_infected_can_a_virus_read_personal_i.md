---
title: "If Windows is infected can a virus read personal information on a Linux HDD?"
date: 2009-02-16
forum: Security
---

### Post by athealwashington on 2009-02-16
Hi, this is kind of an odd question so I will do my best to explain it.




My hard drive configuration is like this:


40GB Maxtor with Windows XP on it. NTFS.


320GB with Ubuntu on it. Ext2.



Now, if Windows XP gets infected can that virus read personal information on Ubuntu's HDD?


For example in /HOME/USER/DESKTOP I have a folder called Bank account and Pictures, now can that virus read those personal items?



The reason I ask is because I configured FS driver (allows you access Ext2 from windows) to allow me to view, delete, edit etc. from my windows box, and I can 100% access them.


So is my Linux documents safe from a Windows virus?




Also if Windows has a key logger logging keystrokes can it affect Linux?



Thanks in advance!!!:)


Sorry if I sound dumb!:)

---

### Post by madnak on 2009-02-16
I would say that if you have installed drivers that allow you to read/write ext2 from windows, then yes a virus would probably be able to read/write it as well. Its best to assume the worst.

I would say that if you had a key logger running in software (ie. not hardware attached to the computer) on windows that it would only work in windows and not under linux, since it's not a linux program.

Hope that helps.

---

### Post by Chayak on 2009-02-16
If you can read your linux partition from windows then the answer is yes.  If you can't then don't worry about it.

The same goes for a software keylogger.

---

### Post by athealwashington on 2009-02-16
OK, if I remove FS driver and I as a user can't access Linux throw windows, do viruses come equipped to access Linux via windows?



Also, say my windows 20 Trojans, Viruses, keyloggers, etc. and I log in to my bank account throw Linux, can the windows virus monitor me logging in?

---

### Post by madnak on 2009-02-17
Virus/malware are becoming more advanced every year and it is possible that a virus could install drivers to be able to read linux file systems, this is however unlikely. The only real way to protect your data is to have it encrypted, have a look at these links.

[http://ubuntuforums.org/showthread.php?t=998526&highlight=truecrypt](http://ubuntuforums.org/showthread.php?t=998526&highlight=truecrypt) 
[https://wiki.ubuntu.com/EncryptedPrivateDirectory](https://wiki.ubuntu.com/EncryptedPrivateDirectory)

> Also, say my windows 20 Trojans, Viruses, keyloggers, etc. and I log in to my bank account throw Linux, can the windows virus monitor me logging in? No not if you login from linux.

---

### Post by Chayak on 2009-02-17
> **athealwashington said:**
> OK, if I remove FS driver and I as a user can't access Linux throw windows, do viruses come equipped to access Linux via windows?



Also, say my windows 20 Trojans, Viruses, keyloggers, etc. and I log in to my bank account throw Linux, can the windows virus monitor me logging in?

No

and no.  I'm a malware analyst for a living.  I haven't seen a sample yet than can magically run itself from an unbooted windows install.

---

### Post by Slim Odds on 2009-02-18
> **madnak said:**
> Virus/malware are becoming more advanced every year and it is possible that a virus could install drivers to be able to read linux file systems, this is however unlikely. The only real way to protect your data is to have it encrypted, have a look at these links.

I wouldn't say that it's unlikely.

If a virus on windows can take control of your machine with "root" access. I could do just about anything. And it does not have to be all that "advanced".

If you have a full time, high speed internet connection, it's easy for it to download whatever it wants. If it has "root" access, it can easily install itself as a service that always starts up automatically. Therefore, it can install drivers and reboot and still be in charge.

---

### Post by cariboo on 2009-02-18
There is no way the malware can transfer it self if the os isn't running, in most cases if you dual boot, you are only running one os. There isn't any way for the malware to write to a Linux directory unless it is world read/writeable, and then it wouldn't run unless it was granted root permisiions as the op said.

If your windows installation is setup properly, this would never happen, as the malware would be detected and removed before it could do any harm.

Jim

---

### Post by Slim Odds on 2009-02-18
> **cariboo907 said:**
> There is no way the malware can transfer it self if the os isn't running, in most cases if you dual boot, you are only running one os. There isn't any way for the malware to write to a Linux directory unless it is world read/writeable, and then it wouldn't run unless it was granted root permisiions as the op said.

If your windows installation is setup properly, this would never happen, as the malware would be detected and removed before it could do any harm.

Jim

When an application gets control of the hardware, it can do **whatever **it wants. If you think that the ext2/3 attributes will stop an application that can directly read and write to the harddrive, then you don't understand how computers work.

 BTW, it's the linux kernel that enforces those attributes. If the kernel is not running, no enforcement.

Try accessing an NTFS partition in linux using ntfs-3g. You can do **anything** you want. The files attributes do not protect anything.

I found that Windows NTFS "encryption" does **NOT** actually encrypt the data. I could read it **without** any problems from linux.

---

### Post by fsando on 2009-02-20
> **cariboo907 said:**
> There is no way the malware can transfer it self if the os isn't running, in most cases if you dual boot, you are only running one os. There isn't any way for the malware to write to a Linux directory unless it is world read/writeable, and then it wouldn't run unless it was granted root permisiions as the op said.

If your windows installation is setup properly, this would never happen, as the malware would be detected and removed before it could do any harm.

Jim

> **Chayak said:**
> No

and no.  I'm a malware analyst for a living.  I haven't seen a sample yet than can magically run itself from an unbooted windows install.

I have been thinking about this a lot as well. Why wouldn't it be possible for some kind of malware, if it gets access to your windows, then to install the ext2 driver (it's freely available) and then silently gain access to you linux. In my (uneducated) view this is even worse than an infected linux as the malware would have full access to ALL of your linux not just your home folder. It could easily write anything anywhere like alter any startup script etc. And perhaps even worse: this (hypothetical) malware may not have any effect on your windows which would lower the chances of detection and reduce the chances that anti virus programs would protect against it.

I don't see why this would not be possible.

As for being likely I'd say, in the coming year (if this scenario is possible) we may see it in the wild. This is simply a very low hanging fruit (albeit not that big yet).

---

### Post by cariboo on 2009-02-20
THe first question would be, why would someone bother when WIndows itself is a much easier target. Most crackers are after bigger fish than a home user.

It is possible to crack a Linux installation and use it as part of a botnet, but that usually depends on the user creating a weak root password.

To get malware to run on Linux, you the user must intervene, as the only place it would run is in your home directory, unless you run it as root, then it can affect the rest of the system.

Jim

---

### Post by Slim Odds on 2009-02-20
> **cariboo907 said:**
> THe first question would be, why would someone bother when WIndows itself is a much easier target. Most crackers are after bigger fish than a home user.

You can ask that question if you want, but it's meaningless regarding the question whether it can be done or not.

> **cariboo907 said:**
>  It is possible to crack a Linux installation and use it as part of a botnet, but that usually depends on the user creating a weak root password.

To get malware to run on Linux, you the user must intervene, as the only place it would run is in your home directory, unless you run it as root, then it can affect the rest of the system.

Jim

Jim, you really need to go back and carefully read my previous post.

Once a virus gets control of your hardware in Windows, it can write **anything** it wants to your linux partitions. This means that it can install code that **runs as root** the next time you boot into linux.

It's just a simple fact.

---

### Post by fsando on 2009-02-20
> **Slim Odds said:**
> You can ask that question if you want, but it's meaningless regarding the question whether it can be done or not.



Jim, you really need to go back and carefully read my previous post.

Once a virus gets control of your hardware in Windows, it can write **anything** it wants to your linux partitions. This means that it can install code that **runs as root** the next time you boot into linux.

It's just a simple fact.

My reasoning comes to the same result.

So from what you are saying the only protection is a fully encrypted system.

If so, how does that affect performance?

---

### Post by Slim Odds on 2009-02-20
> **fsando said:**
> My reasoning comes to the same result.

So from what you are saying the only protection is a fully encrypted system.

If so, how does that affect performance?

That would be one way.

The other option is not to dual boot a linux system with a windows system.

Running a linux system is pretty secure because it's difficult to compromise in the first place.

Since windows is much more easily compromised, you have to keep it away from your linux data somehow.

Apart from gaming, etc. it would be much better to run windows in a VM on the linux machine. There are many advantages to that.

---

### Post by athealwashington on 2009-02-22
> **fsando said:**
> I have been thinking about this a lot as well. Why wouldn't it be possible for some kind of malware, if it gets access to your windows, then to install the ext2 driver (it's freely available) and then silently gain access to you linux. In my (uneducated) view this is even worse than an infected linux as the malware would have full access to ALL of your linux not just your home folder. It could easily write anything anywhere like alter any startup script etc. And perhaps even worse: this (hypothetical) malware may not have any effect on your windows which would lower the chances of detection and reduce the chances that anti virus programs would protect against it.

I don't see why this would not be possible.

As for being likely I'd say, in the coming year (if this scenario is possible) we may see it in the wild. This is simply a very low hanging fruit (albeit not that big yet).


That was my exact same worry.

---

### Post by fsando on 2009-02-22
> **Slim Odds said:**
> 
<snip>
it would be much better to run windows in a VM on the linux machine. There are many advantages to that.

I've been fighting with windows in a VM many times and it never really worked I eventually gave up. I need to share data between Linux and windows which I do via a ntfs partition. It means that my apps must be able to work fluently with data that live outside of the VM.

Another problem is that when I buy a laptop I also buy some windows which only runs on that laptop - I don't think it will run in a VM. I would then have to pay twice for windows :(

---

### Post by Slim Odds on 2009-02-22
> **fsando said:**
> I've been fighting with windows in a VM many times and it never really worked I eventually gave up. I need to share data between Linux and windows which I do via a ntfs partition. It means that my apps must be able to work fluently with data that live outside of the VM.

Another problem is that when I buy a laptop I also buy some windows which only runs on that laptop - I don't think it will run in a VM. I would then have to pay twice for windows :(

Not sure what the "fighting" is about. Lots of people run Windows in a VM without much problem. I use VirtualBox and it runs fine.

Sharing data in VirtualBox is quite easy. You just make a shared folder. Windows can work with it without issue. I'm not even sure what Windows thinks the file system is, but it just works.

I can't be sure, but I'll bet that your existing Windows install could be used (if you have a CD or DVD version). Many things don't change in a VM, like your BIOS type, etc.

VM's are easy to backup and restore. If your Windows VM gets a virus, you can just go back to a previous snapshot.

---

### Post by fsando on 2009-02-25
> **Slim Odds said:**
> Not sure what the "fighting" is about. Lots of people run Windows in a VM without much problem. I use VirtualBox and it runs fine.

Sharing data in VirtualBox is quite easy. You just make a shared folder. Windows can work with it without issue. I'm not even sure what Windows thinks the file system is, but it just works.

I can't be sure, but I'll bet that your existing Windows install could be used (if you have a CD or DVD version). Many things don't change in a VM, like your BIOS type, etc.

VM's are easy to backup and restore. If your Windows VM gets a virus, you can just go back to a previous snapshot.

My fighting was primarily in edgy and feisty where my apps crashed and virtualbox also crashed when running data outside of the vm. Filenames with certain character combinations would not be visible inside VB and also Danish letters was a big problem.

I didn't know it could be possible to run the windows that comes with the laptop in a vm. I'll definitely look into it.
Thanks

---

### Post by The Cog on 2009-02-26
The VirtualBox manual has a section on lifting a real windows image into a VM. Some tweaking may be required because of the apparent hardware change, but it can be done. Windows is written specifically to make doing it difficult, to prevent unauthorised copying via disk images.

---

### Post by fsando on 2009-02-26
> **The Cog said:**
> The VirtualBox manual has a section on lifting a real windows image into a VM. Some tweaking may be required because of the apparent hardware change, but it can be done. Windows is written specifically to make doing it difficult, to prevent unauthorised copying via disk images.

Nice! The benefit of Sun buying VirtualBox?

---

### Post by The Cog on 2009-02-26
> **fsando said:**
> Nice! The benefit of Sun buying VirtualBox?

The manual is in the downloads web page. I'm sure the info is in that manual. Either there or their FAQ.

---

