---
title: "Access USB drive without executing boot records"
date: 2009-11-21
forum: Security
---

### Post by Ulysses_ on 2009-11-21
According to the following [article](http://antivirus.about.com/cs/tutorials/a/bsvirus_2.htm):  "Even non-bootable disks can spread a boot sector infection when they are accessed"  Is it possible to access the data in a USB drive without executing the machine code in its boot records, which may be infected?  What if we have a rule that all our external drives are always partitioned with just one partition?  Then there's no need for boot machine code, is there?

---

### Post by scorp123 on 2009-11-21
> **Ulysses_ said:**
>  "Even non-bootable disks can spread a boot sector infection when they are accessed" Welcome to the wonderful world of FUD. They are anti-virus software makers ... so what did you expect them to write? :)

Besides: Why are you bothered by this?? Hanging around in this forum I'd assume you are a Linux user now. Relax ... and enjoy the stuff you can do with your computer without having to defrag every 5 minutes, without having to hunt for spywares, anti-this and anti-that ... :D

> **Ulysses_ said:**
>  Is it possible to access the data in a USB drive without executing the machine code in its boot records You do that all the time. Or else you'd be booting into a new OS every time you insert a USB stick :D

> **Ulysses_ said:**
>  which may be infected? And so? Let Windoze users sort out their problems ...

> **Ulysses_ said:**
>  Then there's no need for boot machine code, is there? First of all ... all this is mainly FUD in my opinion. And even if you don't have executable boot *code* installed on a stick ... technically every disk has a master boot record and thus a reserved area where boot loaders would go. The only way to avoid that would be to go back to pencil and paper blocks.

But then again us Linux users can sit back and relax. You'd have to be "root" and really do something incredibly stupid in order for a Linux virus --which don't exist except in a few labs and computer museums-- to have any chance of success.

As ordinary user you don't even have permission to read or write the boot block of any disk, so even if having boot viruses on Linux were an issue --which clearly is not the case-- it would be a non-issue because you as ordinary user would not even be able to access that block.

Don't believe me? Just try and read the boot block of your main disk. Chances are it's called /dev/sda ?

```
dd if=/dev/sda of=sda-MBR.backup bs=512 count=1
```

Try and execute that as ordinary user. You will **_NOT succeed_** and this is the answer you will get:
```
dd: opening `/dev/sda': **[COLOR="Red"]_Permission denied_[/COLOR]**
```

Ordinary users have no business reading boot blocks on Linux. As I said: Even if this whole story were an issue here ... it's in fact not an issue. Not even remotely.

Besides: I am using Linux since 1996 ... Every year I hear the BS "One day Linux will have viruses too ... "  Riiiiight. I am still waiting. Show me one. Just one .... No luck so far. So I will just relax and sit back and do something else instead and let the Windoze users hunt for their latest viruses they've been infected with ...

---

### Post by Ulysses_ on 2009-11-21
I used to think along the same lines but was shocked to discover that the machine code in the master boot record is not only for booting up!  It also implements the partitioning scheme in any way it wants, without having to follow any standard format!  And that's for normal usage, not booting!  For example with BootIt the executable that goes in the MBR supports more than the usual maximum of 4 partitions (3 primaries and 1 extended with the possibility of many logicals inside the extended partition), but it supports up to 200 primaries, of 1-2 TeraBytes each.  

You don't have to boot off a BootIt disk in order to access it in windows. In linux I'm sure you can access a BootIt disk too.  But does linux do so out of knowledge of the format, ie where BootIt stores the numbers that say what sector each partition begins and ends at, or does it execute the real-mode machine code in order to construct a table for its own future use?

If linux knows the format of BootIt, and the standard format with the 4 partitions/standard partition table, then what does linux do with a format it does not know?

---

### Post by Ulysses_ on 2009-11-21
> **scorp123 said:**
> I am using Linux since 1996 ... Every year I hear the BS "One day Linux will have viruses too ... "  Riiiiight. I am still waiting. Show me one. Just one

Wikipedia: "In 1997, when a virus for Linux was released – known as Bliss"

[http://en.wikipedia.org/wiki/Computer_virus](http://en.wikipedia.org/wiki/Computer_virus)

---

### Post by scorp123 on 2009-11-21
> **Ulysses_ said:**
> Wikipedia: "In 1997, when a virus for Linux was released &#8211; known as Bliss"

[http://en.wikipedia.org/wiki/Computer_virus](http://en.wikipedia.org/wiki/Computer_virus) Yeah riiiight. How about reading the full text instead of quoting out of context??

>  ... Bliss requires that the user run it explicitly (so it is a trojan), and it can only infect programs that the user has the access to modify .... **The Bliss virus never became widespread, [B][COLOR="Red"]and remains chiefly a research curiosity.[/COLOR]**[/B] 

Right. Big deal. So what's the difference between "Bliss" and any potentially harmfull shell code you find here in this very forum? None. **[COLOR="Red"]You have to run it first before it can cause damage.[/COLOR]** I could just as well hex-encode a potentially harmful shell command and write a header that would extract the command ... it would still not be a real virus, and it would still have to be executed by the users themselves.

This is not even remotely close to a self-spreading + self-propagating + self-reproducing + system-wide-infecting virus as we know it from the Windoze world.

So again ... I am still waiting for a serious virus threat. Not lab experiments and BS I have to execute myself for it to work.

If you want to discuss security threats on Linux ... fine: let's talk about badly patched servers, super-lazy and stupid admins and human hackers who found a way into a server. Those threats are real, yes.

But viruses on Linux belong into the Sci-Fi department.

---

### Post by scorp123 on 2009-11-21
> **Ulysses_ said:**
> or does it execute the real-mode machine code in order to construct a table for its own future use? Partition tables are **read** ... not *executed*. Again: This is FUD, FUD, FUD.

> **Ulysses_ said:**
>  then what does linux do with a format it does not know? Throw an error that it cannot read the disk. What else??

---

### Post by Ulysses_ on 2009-11-21
> **scorp123 said:**
> it would still not be a real virus

Instead of defocusing into what is or is not a virus which does not really matter, let's concentrate on the title. When a BootIt disk is hotplugged, how do you believe linux knows where the 200 supported partitions are?

---

### Post by scorp123 on 2009-11-21
This article here shows why Linux/Unix viruses won't work for too long:

[http://en.wikipedia.org/wiki/Staog](http://en.wikipedia.org/wiki/Staog)

> " ... It was discovered in the fall of 1996, and the vulnerabilities that it exploited were shored up soon after. It has not been detected in the wild since its initial outbreak. .... It worked by exploiting some kernel vulnerabilities to stay resident. Then, it would infect executed binaries.

Since it relied on fundamental bugs, software upgrades made systems immune to Staog. This, combined with its shot in the dark method of transmitting itself, ensured that it died off rather quickly ... "

That's exactly what Linux users are being told again and again: Keep your systems updated + and only install stuff from the official repositories. Don't work as "root". Never ever. Unless it's really really needed for administrative stuff. Don't enable the root account. Leave it off. Use "sudo" instead.

Voila. That's why viruses don't work here.

---

### Post by scorp123 on 2009-11-21
> **Ulysses_ said:**
> how do you believe linux knows where the 200 supported partitions are? Linux knows partition types because there are kernel modules for each of the supported partition types. Remove the "ntfs" kernel module and Linux will no longer know NTFS (Fedora and Red Hat do that).

Can you please show me the part in the kernel sources where they added support for that "BootIt" stuff? Because if it's not in the kernel .... then Linux will not support it. Unknown filesystem, unknown partition type.

---

### Post by Ulysses_ on 2009-11-21
And I have just set up a virtual vmware hard disk with BootIt.  It mounts happily to a linux virtual machine.  

Now how does linux know how many partitions I have set up BootIt with, where they start and where they finish, if there is no standard partition table?

---

### Post by Ulysses_ on 2009-11-21
> **scorp123 said:**
> Linux knows partition types because there are kernel modules for each of the supported partition types.

You are confusing partition types (NTFS, etc) with partitioning schemes in the master boot record (standard, BootIt, PCDOS, etc).  There is no standard partition table in the master boot record of PCDOS, neither is there in BootIt. 

Yet BootIt mounts.  How does linux get the sector numbers of the start and end of each partition, if there is no standard partition table?

---

### Post by scorp123 on 2009-11-21
> **Ulysses_ said:**
> And I have just set up a virtual vmware hard disk with BootIt.  It mounts happily to a linux virtual machine.   I just googled around and "BootIt" is as the name implies a boot manager? So it's the other way round: it boots other OS'es. Just like other free and/or commercial boot loaders do as well. So the big deal here is ... what?? That a boot manager can support 200 partitions (like you're ever gonna have that??) and Linux happens to be one of the supported partition types?

> **Ulysses_ said:**
>  Now how does linux know how many partitions I have set up BootIt with, where they start and where they finish, if there is no standard partition table? Honestly ... I don't care. You want to panick. Fine ... so go ahead and panick. Don't let the Linux viruses bite you. ):P

LOL

:lolflag:

---

### Post by Ulysses_ on 2009-11-21
Haha. No I do not want to panic. Just want to mount vmware disks to a linux host, and have been told this should not be done but raw data should be read without mounting, as mounting will transmit any infection.

---

### Post by Ulysses_ on 2009-11-21
> **scorp123 said:**
> So the big deal here is ... what?? That a boot manager can support 200 partitions and Linux happens to be one of the supported partition types?

The big deal is it's substantially different from the standard contents of the MBR, enough that someone has to know where BootIt stores its proprietary partition table to access the disk.  Or execute parts of or all the machine code that is provided in it.

---

### Post by scorp123 on 2009-11-21
> **Ulysses_ said:**
> this should not be done but raw data should be read without mounting, as mounting will transmit any infection. ... to Windows machines. Yes. See above. On Linux this is a total non-issue. OK?

---

### Post by Ulysses_ on 2009-11-21
> **scorp123 said:**
> ... to Windows machines. Yes. See above. On Linux this is a total non-issue. OK?

Thanks for the contributions.  It would have been nicer if it was solidly substantiated rather than just the opinion of someone on the internet.  We don't know if you're a malware expert related to Black Hat projects, or just a tekkie teenager with an interest in computers.  So your words, as are anybody's words here, are as good as the substantiation that comes with them.

---

### Post by scorp123 on 2009-11-21
> **Ulysses_ said:**
>  We don't know if you're a malware expert related to Black Hat projects, or just a tekkie teenager with an interest in computers.   Do a Google search on my nick. ~2100 postings here on Ubuntu forums, ~2200 postings on Linux Mint forums ...  I dare say I know WTF I'm talking and writing about. Good enough for you?? Besides: I don't need to prove anything to you. ;)

> **Ulysses_ said:**
>  So your words, as are anybody's words here, are as good as the substantiation that comes with them. There are no known Linux boot viruses that would spread in a way that you suggest. And what you are doing is panicking. Substantiated enough for you? 

If you're *that* paranoid you probably shouldn't use computers at all. Sorry to say so.

---

### Post by cariboo on 2009-11-21
I'm closing this thread, as it is going nowhere. I would suggest you put each other on your ignore lists.

---

