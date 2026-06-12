---
title: "windows/dos and linux systems"
date: 2008-06-13
forum: The Cafe
---

### Post by mo.reina on 2008-06-13
was having a discussion with a friend about linux in general, and though we both are die-hard linux users (have been for a few years), we couldn't figure out what made linux so much more stable than windows/dos.  or to rephrase that, what makes windows/dos so unstable when compared to any linux/unix system.  i mean, macs are stable as hell, but i heard that's because they use a modified FreeBsd system.  so it all harks back to a unix-derived system.

anyone feel like giving a short explanation?

---

### Post by kerry_s on 2008-06-14
i don't think 1 is really more stable than another, they all have there problems, most people would say windows is unstable but if you factor the number of people using it of course it's a large number. if you do the same for linux you'll get a equal amount of instability compared to the number of people who use it. of course in the linux world we shrug it off, then fix it. apple has the same ups and downs as any other os.

you'll find people all over using different os's who have never ever seen a crash.

---

### Post by jrusso2 on 2008-06-14
Well Windows has not been dos based since Windows ME, its based on the NT kernel which some say is derived from VAX VMS.

Anyways somethings that can make Windows unstable are that the drivers are allowed direct access to the kernel. So I poorly written driver can cause all kinds of havoc.

Also the registry can become corrupt and cause issues as poorly written software leaves the registry with all kinds of dead ends scraps.

Best advice to keep a Windows system stable is use good software.  Don't install and uninstall a lot of junk and use WDM certified drivers and good quality hardware.

---

### Post by Victormd on 2008-06-14
I was a hardcore windows user (NT4.0 and XP) and had it setup where it almost never crashed, only when I was running extensive 3D modeling+rendering and a few years ago + not enough RAM = crash... Now, after transitioning to ubuntu, I feel just as safe (like it a lot more though) and the crash frequency might be slightly less than in windows... but, like kerry_s said, we shrug it off...

---

### Post by anjilslaire on 2008-06-14
Well, there's also the argument that while X may crash, the kernel is still up & running, hence the OS hasn't crashed, even though the GUI has dumped, and is effectively crashed for many end-users.

Windows on the other hand (with the exception of Win2K8 now) has the GUI system wrapped up in the OS itself. If Explorer.exe (the GUI shell, basically) crashes, then the OS itself is likely hosed, and must be rebooted. Linux, on the other hand, merely needs X restarted in many cases to continue on.

Enter Windows Server 2008, however. This latest OS from Microsoft actually has a separate GUI subsystem. You are even given the option of installing the OS in Core Server Mode, with no GUI at all. Yes, that's right: Windows without any Windows (ironic, eh?). Microsoft hs finally separated the OS from the GUI, so potentially the argument can be made of Windows in th future as well: The system *really* hasn't crashed, just the GUI.

---

### Post by mo.reina on 2008-06-14
ok but how about the difference between the linux OS/kernel and the one that windows/microsoft uses?  i mean there must be an advantage in terms of stability and/or security in using linux since all the big servers, ISPs, etc. are running linux/UNIX.

---

### Post by LaRoza on 2008-06-14
> **mo.reina said:**
> was having a discussion with a friend about linux in general, and though we both are die-hard linux users (have been for a few years), we couldn't figure out what made linux so much more stable than windows/dos.  or to rephrase that, what makes windows/dos so unstable when compared to any linux/unix system.  i mean, macs are stable as hell, but i heard that's because they use a modified FreeBsd system.  so it all harks back to a unix-derived system.

anyone feel like giving a short explanation?

Its all in the source. The Linux source is built by developers trying to make a good kernel, and the Windows kernel is built trying to meet deadlines.

The development models of Linux ensure a good kernel, the development model of Windows ensures good marketting.

Linux isn't a cheap copy of anything, like DOS. CP/M was the OS DOS is copying (actually, it was named QDOS (quick and dirty operating system) and bought by MS for $50000).

Microsoft isn't concerned with making good software. If they could get away with selling dirt, they'd do it.

---

### Post by zmjjmz on 2008-06-15
I've noted that crashes don't happen at all on Linux/UNIX if you run stable software.
If you run unstable software, you might crash X.
But luckily, Linux (and most Unices) can run without X.
Windows kinda depends on its GUI for everything except Server 2008, as pointed out above, and so if you run an unstable app that would crash the GUI on anything else, on Windows you crash the whole system :D

---

### Post by mo.reina on 2008-06-15
right but microsoft's gui wasn't integrated until windows 95, before that they had DOS.  and yet it wasn't DOS that people were running on their big servers but linux/UNIX.  so what are the main differences in kernel design and code that make the *IX systems superior in terms of stability?

---

### Post by jbaerbock on 2008-06-15
My problem has always been that while it is only the GUI that crashes in Linux, how does one restart X without it? CTRL-ALT-Backspace is usualy frozen along with any other keyboard command along with it.

---

### Post by LaRoza on 2008-06-15
> **jbaerbock said:**
> My problem has always been that while it is only the GUI that crashes in Linux, how does one restart X without it? CTRL-ALT-Backspace is usualy frozen along with any other keyboard command along with it.

[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

---

### Post by Mazza558 on 2008-06-15
> **LaRoza said:**
> Its all in the source. The Linux source is built by developers trying to make a good kernel, and the Windows kernel is built trying to meet deadlines.

The development models of Linux ensure a good kernel, the development model of Windows ensures good marketting.

Linux isn't a cheap copy of anything, like DOS. CP/M was the OS DOS is copying (actually, it was named QDOS (quick and dirty operating system) and bought by MS for $50000).

Microsoft isn't concerned with making good software. If they could get away with selling dirt, they'd do it.

To be fair, when Microsoft was a very small company, I'm sure they cared about the quality of what they were producing, as they needed to prove themselves at first. I agree that the only thing on their agenda now (and ever since 1990 or so) is money.

---

### Post by zmjjmz on 2008-06-15
Didn't MS buy DOS though?
As far as I know, they've only improved on it.

---

### Post by LaRoza on 2008-06-15
> **Mazza558 said:**
> To be fair, when Microsoft was a very small company, I'm sure they cared about the quality of what they were producing, as they needed to prove themselves at first. I agree that the only thing on their agenda now (and ever since 1990 or so) is money.

Well, barring one piece of quality software they wrote, all of their work has been acquired and renamed. 

MS-DOS is an interesting story. It goes (in short) like this:

IBM was commissioned to build a PC, but they didn't have an OS, but they accepted it anyway. They went to find an OS to buy, they went to the creator of CP/M, but he wasn't in the office that day and the company didn't want to sign anything without him. So IBM went to Microsoft a small company at the time and asked them. Microsoft accepted the offer, but they didn't have an OS either (they didn't say that at the beginning!). Microsoft went out shopping and found QDOS, written by a single person. They bought it for $50000 and renamed it. Sold it to IBM, IBM put it on the PC and it was popular.

Microsoft exists because of a fluke.

---

### Post by jomiolto on 2008-06-15
> **LaRoza said:**
> [http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

Thanks, that's an interesting bit of information. And no, I did not accidentally shutdown my laptop when testing that and pressing a wrong key combination... :-\"

---

### Post by Ioky on 2008-06-15
well, in fact, even DOS is come from UNIX, I mean it is not a modify version of UNIX, but DOS is try to make itself run like Unix.

anyway, but to be fair as I personally experiences, Xp are fairly stable, I did crash once with Linux, after like a years of using it, and I still don't know why it crash that day. haha anyway, although xp do crash more, but what crash in front of me is Mac OS X. And don't ask me why it just did. I have a pretty up to date Mac book pro. I only use it to do school work, but it crash like about 4 time a week. It just kind of freeze, you can't use the mouse. (well you can move it around but that is about it.) It is kind of annoying with Mac crash.

---

### Post by zmjjmz on 2008-06-15
Nope, not at all.
That's NT.

---

### Post by jespdj on 2008-06-16
> **mo.reina said:**
> right but microsoft's gui wasn't integrated until windows 95, before that they had DOS.  and yet it wasn't DOS that people were running on their big servers but linux/UNIX.  so what are the main differences in kernel design and code that make the *IX systems superior in terms of stability?
DOS is a very simple, single user / single tasking operating system, which is totally unsuited for a server which needs to multitask heavily to serve all the clients that connect to it. So DOS is absolutely useless for any kind of use on a server, and it was never meant to be used like that.

Windows 3.1 (which ran on top of DOS) had a simple kind of multi-tasking: [cooperative multitasking](http://en.wikipedia.org/wiki/Computer_multitasking). That means that control lies with the program, not the operating system: the OS gives the control to a program, and then the program is supposed to give the control back to the OS after a short while, so that other programs can run. This is opposed to preemptive multitasking, in which the OS decides when to switch to the next program. With cooperative multitasking, if one program behaves badly and doesn't return control to the OS in time, the whole computer will hang. That makes it very unstable. Also, DOS and Windows 3.1 did not have proper memory protection, which means that any program can read and write into the memory of any other program. This makes the whole system very unstable and insecure.

> **Ioky said:**
> well, in fact, even DOS is come from UNIX, I mean it is not a modify version of UNIX, but DOS is try to make itself run like Unix.
Huh? No, DOS did not come from UNIX and does not try to run like UNIX. It was never made to compete with UNIX; it was made because IBM needed an OS for their personal computer.

---

