---
title: "You can help out Coreboot!"
date: 2008-10-28
forum: The Cafe
---

### Post by uid313 on 2008-10-28
[Coreboot](http://en.wikipedia.org/wiki/Coreboot) is a free software project aimed at replacing the standard BIOS firmware found in most computers with a lightweight firmware system designed to perform only the minimum of tasks necessary to load and run a modern 32-bit or 64-bit operating system.

You can help out the Coreboot project, it doesn't require any programming skills.
```

$ sudo apt-get install subversion
$ svn co svn://coreboot.org/repos/trunk/coreboot-v2

```
```

$ cd coreboot-v2/util/getpir/
$ make
$ sudo ./getpir

```
getpir will generate a file called "irq_tables.c", you should send this to Coreboot.
```

$ cd coreboot-v2/util/mptable/
$ make
$ sudo ./mptable > mptable.txt

```
This generate a file called "mptable.txt", you should send this to Coreboot.
```

$ sudo apt-get install superiotool
$ sudo superiotool -dV > superiotool-dV.txt
$ sudo dmidecode > dmidecode.txt
$ sudo dmidecode --dump > dmidecode-dump.txt
$ lspci -tvnn > lspci-tvnn.txt
$ sudo lshw > lshw.txt

```
Now send an email to the Coreboot project mailing list.
[http://www.coreboot.org/mailman/listinfo/coreboot](http://www.coreboot.org/mailman/listinfo/coreboot)
E-mail address: coreboot at coreboot dot org
Attach the files irq_tables.c, mptable.txt, superiotool-dV.txt, dmidecode.txt, dmidecode-dump.txt, lspci-tvnn.txt, and lshw.txt.

---

### Post by uid313 on 2008-10-28
Anyone helped out?

---

### Post by VeeDubb on 2008-10-28
I may be willing to help out, but an awful lot more information might be helpful.

Just for starters...

What EXACTLY do those commands and programs do?

---

### Post by Sef on 2008-10-28
Moved to community cafe.

---

### Post by zmjjmz on 2008-10-29
While I'm all for coreboot, I'd also like to know exactly what these scripts do.

---

### Post by uid313 on 2008-10-29
**$ sudo apt-get install subversion**
This command installs subversion (svn), a tool that is needed to download the latest development version of Coreboot from svn source code repository.

**$ svn co svn://coreboot.org/repos/trunk/coreboot-v2**
This command makes just recently installed subversion (svn) connect to subversion repository at coreboot.org, and download the latest coreboot-v2.

**$ cd coreboot-v2/util/getpir/**
This changes directory into the coreboot that you just downloaded.

**$ make**
This compiles the 'getpir' utility that come with coreboot from source code into a executable binary that you can run.

**$ sudo ./getpir**
This runs the 'getpir' utility that you just compiled.
This generates a file called 'irq_tables.c' in the same directory, which is a text file with C source code.
It needs to be run with the 'sudo' command which runs it with administrator privileges, because it needs to access the memory to grab the [IRQ](http://en.wikipedia.org/wiki/Interrupt_request) routing tables.
This is motherboard hardware information.

**$ cd coreboot-v2/util/mptable/**
This changes the directory into 'mptable' utility of the coreboot.

**$ make**
This compiles the 'mptable' utility that come with coreboot from source code into a executable binary that you can run.

**$ sudo ./mptable > mptable.txt**
This runs the 'mptable' utility and saves the output it prints out into a file called mptable.txt
Sudo makes it run with administrator privileges, which it needs in order to access the memory and get the MP table from the motherboard. It is just motherboard hardware information.

**$ sudo apt-get install superiotool**
This command installs the 'superiotool' from the Ubuntu repository. It is a tool that figures out what kind of [Super I/O](http://en.wikipedia.org/wiki/Super_I/O) chip you have no your motherboard. Brand and model.

**$ sudo superiotool -dV > superiotool-dV.txt**
This runs the superiotool with administrator privileges, using the "d" and "V" parameters. The "d" parameter gets the Super I/O register contents, and "V" makes it verbose.

**$ sudo dmidecode > dmidecode.txt**
This runs the dmidecode utility with administator privileges. It fetches some DMI ([Desktop Media Interface](http://en.wikipedia.org/wiki/Desktop_Management_Interface)) information from the SMBIOS. It outputs it into the dmidecode.txt file.

**$ sudo dmidecode --dump > dmidecode-dump.txt**
This is the same as the command above, but it dumps it into the dmidecode-dump.txt file, without first decoding it.

**$ lspci -tvnn > lspci-tvnn.txt**
This runs the 'lspci' command which **l**i**s**ts the **PCI** bus, and saves the output into a file called 'lspci-tvnn.txt'.

**$ sudo lshw > lshw.txt**
This runs 'lshw' with administrator privileges. It **l**i**s**ts **h**ard**w**are, and saves them into a file called 'lshw.txt'.

---

### Post by uid313 on 2008-10-29
After you're done, and have ran all the commands, and e-mailed Coreboot the files, you can remove the coreboot-v2/ directory.

You can also remove 'svn' (subversion) and 'superiotool' if you wish, since you no longer need them.
$ sudo apt-get remove subversion
$ sudo apt-get remove superiotool

---

### Post by uid313 on 2008-10-29
Anyone helping out?

Were the descriptions of the commands suitable?
Anymore questions?

---

### Post by zmjjmz on 2008-10-29
I intend on doing it, I just wanted to know what those programs were.
I don't like running stuff with sudo that I don't know about.


Anyways, you'll be able to get more info from me because I have two computers (that I can use for this. I actually have 14 computers) and will be running these tests on both

---

### Post by Polygon on 2008-10-29
besides for OSS purists, why would a normal user wnat to use coreboot instead of the bios included on their motherboard?

I myself am EXTREMELY skeptical. This seems like the thing that one doesn't really want to mess with, as if you do something wrong, you have yourself a nice big doorstop.

---

### Post by medic2000 on 2008-10-29
i shall help.

---

### Post by Vadi on 2008-10-29
Well, since it only gives info, I'll do this. Why not

---

### Post by Vadi on 2008-10-29
> **Polygon said:**
> besides for OSS purists, why would a normal user wnat to use coreboot instead of the bios included on their motherboard?

Same reason someone would want to get an Android phone instead of a normal one? 

@OP: It didn't work: [http://pastebin.com/m4ae3dad5](http://pastebin.com/m4ae3dad5)

---

### Post by zmjjmz on 2008-10-29
This is from my Thinkpad T20.

---

### Post by zmjjmz on 2008-10-29
2 more files, there's a max of 5 attachments/post.

---

### Post by uid313 on 2008-10-30
> **Polygon said:**
> besides for OSS purists, why would a normal user wnat to use coreboot instead of the bios included on their motherboard?
There are many reasons.
For one, its open, you can be sure its no trojans or backdoors.
Two, BIOS is a legacy piece-of-poop, with Coreboot you can either make it it load a legacy BIOS firmware like SeaBIOS, or you could load OpenFirmware IEEE 1275-1994, or you could load GNUFI which is an EFI implementation.
Coreboot is modern and uses 32-bit mode, not like some old 16-bit mode like BIOS.
Also, coreboot can boot in 2 seconds.
[http://www.youtube.com/watch?v=nuzRsXKm_NQ](http://www.youtube.com/watch?v=nuzRsXKm_NQ) 

> **Polygon said:**
> I myself am EXTREMELY skeptical. This seems like the thing that one doesn't really want to mess with, as if you do something wrong, you have yourself a nice big doorstop.
Yes, flashing the BIOS with Coreboot is not something you should do, this could go wrong and it could brick your motherboard.
The above mentioned commands however, does not install/flash Coreboot, it just downloads Coreboot, and runs some some utilities to obtain information from the hardware.

---

### Post by Vadi on 2008-10-30
It doesn't work for me :\

---

### Post by uid313 on 2008-10-30
> **Vadi said:**
> It doesn't work for me :\
That is not a very informative explanation.
What *exactly* does not work?

---

### Post by artir on 2008-10-30
I helped :)

---

### Post by saulgoode on 2008-10-30
What should the subject of the email be?

---

### Post by artir on 2008-10-30
I wrote "Useful data for the project"

---

### Post by uid313 on 2008-10-30
> **artir said:**
> I helped :)
Great! :)

> **saulgoode said:**
> What should the subject of the email be?
I don't know. The name of your motherboard would probably be a good subject line.

---

### Post by Vadi on 2008-10-31
> **Vadi said:**
> @OP: It didn't work: [http://pastebin.com/m4ae3dad5](http://pastebin.com/m4ae3dad5)

See above

---

### Post by uid313 on 2008-10-31
> **zmjjmz said:**
> This is from my Thinkpad T20.
Please e-mail them to the coreboot mailing list.

---

### Post by uid313 on 2008-11-02
[http://www.youtube.com/watch?v=X72LgcMpM9k](http://www.youtube.com/watch?v=X72LgcMpM9k)

Coreboot just held a talk at Google.
It is available on YouTube.
It explains coreboot for those who are interested.

---

### Post by mdancer on 2008-11-05
I will do this thing. But I want more. If I want help you to bring support of coreboot on my gigabyte GA-965P-S3 can I do something more?

---

### Post by john_spiral on 2008-11-05
This Coreboot stuff looks interesting. Besides Tetris what's the most impressive application that's been built?

Is there any chance of frying my hardware with the commands on the first post?

thanks

John

---

### Post by askyourpc.com on 2008-11-05
Is there a motherboard that allows you to write your own BIOS?

---

### Post by eternalnewbee on 2008-11-05
I'd love to replace my BIOS with Coreboot, if that's possible, but as I'm not so deep in to Linux, I'll just patiently wait for reactions from Power users, like Caljohn, or staff members.
In the meantime I've subscribed to this Thread to stay in touch.
Keep up the good work.

---

### Post by Lord Xeb on 2008-11-05
Ummm... I am not going to even attempt this. I am not going to fudge my lappy by doing any of this becuase it is my only computer. Can you role back to the origional bios if you **** up

---

### Post by zmjjmz on 2008-11-05
> **Lord Xeb said:**
> Ummm... I am not going to even attempt this. I am not going to fudge my lappy by doing any of this becuase it is my only computer. Can you role back to the origional bios if you **** up

No, you're just screwed.
I'd test it on a machine where you can easily swap out the mobo.

---

### Post by RaZoR1394 on 2008-11-11
Developers on the Coreboot mailing list have clearly stated that this information is spamming the list. Unless you want to try a patch or make your own patch and you are fully ready to test Coreboot on your system there is no point in posting your information to the list,

---

