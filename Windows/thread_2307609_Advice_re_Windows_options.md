---
title: "Advice re Windows options"
date: 2015-12-26
forum: Windows
---

### Post by echo59 on 2015-12-26
Hi,

I've had a dual-boot PC for many years, running both Windows 7 and 15.04.  For Christmas my wife (and brother-in-law) got me a bespoke PC which he is putting together.  The specs are as follows:
**CPU   **Core i5-4460 3.2GHz (6MB cache)**RAM  **16GB DDR3
**HD1**  SSD 250GB
**HD2**  3TB SATA 3Gb/s
**Graphics**  GeForce GTX 750 (2GB DDR5)
**Motherboard**  ASRock H97 Anniversary, ATX, (UEFI)

I plan to have my OSs on HD1, the SSD, and keep the other drive for data.  I'll be running Ubuntu but I also need to have Windows installed, for a few legacy applications.  Because the machine is custom-built it doesn't come with any pre-installed OS.  My old dual-boot system worked fine, but it was a pain having to reboot to change from one to the other.  Which leads to my questions:-

**ONE:**
Dual-boot or just boot into Ubuntu and run Windows as a virtual machine?  What are the pros or cons for each option and do they actually matter that much given the spec?

**TWO:**
Which version of Windows to use?  Windows 10 or Windows 7?  Again, what is the rationale behind the advice.

**THREE:**
In my old dual-boot system I'd a data partition which I had encrypted with TrueCrypt and that mounted on boot, after the password, in both OSs.  I will need to have an encrypted partition again.  Does this influence your advice for question one?  Also, what strategy for encrypting a partition would you use at this stage?  I will need access to this encrypted data partition from both the Linux and Windows environments.

Many thanks for the advice, and Happy Christmas!!!

---

### Post by howefield on 2015-12-27
Thread moved to the "*Windows*" forum.

---

### Post by echo59 on 2016-01-05
Any thoughts???

---

### Post by KnownSyntax on 2016-01-07
I would have the hard drive split into two (where the bigger size would be the location on which you tend to use the most) between Windows and Ubuntu. Personally I'd recommend using Windows 10 (not just because it's the last version of Windows and Microsoft states that for the life of your device you will be supported with the newest release) but for the fact that you can use old programs using the compatibility mode. Plus I've been using Windows 10 since the alpha stages and find that it is well stable if you are using it with a desktop (laptops are a tad iffy still due to driver issues even to this date). Then you can run Ubuntu alongside of it, which will allow for you to have the best of both worlds.

---

### Post by echo59 on 2016-01-10
Thanks, @KnownSyntax.  I was 1/2 leaning towards Windows 10 because of the lifespan issue.  

So, you think dual-boot as opposed to a virtual machine?

---

### Post by JayKay3OOO on 2016-01-10
Buy the full retail windows so you can move it around as you like. More secure to go with 10. 7 is 6 years old now even though it does work a little nicer. 

Unless gaming use w10 in a vm. It only needs 3 to 4GB to run smooth. I have a nas so moving data between the vm and native machine is easier although you can set certain folders and probably do a simple shared folder from linux. There is probably a true crypt version. I noticed a tar on the website, but not used it.

There are encryption options when installing linux.

Constant re-boots are a pain even on an ssd. Two security holes to your data and dang it if you true crypt your ntfs and you linux and the mess.

CPU hp is probably going to be 40 - 50% a lot of the time similar to RAM use. My last quad core machine could run four VMS and have them do intensive tasks without too much slow down and certainly the base OS still ran fine. Boot times on a vm on an SSD are pretty fun and guest additions makes the linux windows divide almost seamless.

Go native if you need fastest possible gaming hp or rendering speed otherwise you'll soon tire of dual, triple or quad booting to different os's.

---

### Post by echo59 on 2016-01-10
What's a game?????  Haven't played a game in years.......

That settles it.  I think VM of Win10 is the way to go so.

Thank.

---

