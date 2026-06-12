---
title: "Windows at its best"
date: 2008-07-21
forum: The Cafe
---

### Post by Separ on 2008-07-21
[IMG]http://img152.imageshack.us/img152/1153/wtfmg7.png[/IMG]
This happened on my friend's computer who had reinstalled Windows a few days ago and has Virus protection.
:lolflag:

---

### Post by songshu on 2008-07-21
i don't think its funny at all, it just proves that Microsoft is taking its responsibility when it comes to protecting its customers and provide a healthy commercially supported product.

I'm just surprised that it doesn't recommend Wubi as a critical security update.

---

### Post by Daveski on 2008-07-21
> **Separ said:**
> This happened on my friend's computer who had reinstalled Windows a few days ago and has Virus protection.

This is fairly common. I have seen DEP kill Windows Explorer loads of times on loads of machines. Doesn't really give the user a warm feeling does it?

---

### Post by keiichidono on 2008-07-21
I'm actually fixing a Windows laptop that keeps on trying to kill explorer right now. I'll make sure to install Ubuntu on this machine though. :D

---

### Post by wrtpeeps on 2008-07-21
It's not always to do with a virus.

Windows has closed explorer on me a few times. It does it sometimes on my laptop if I start clicking desktop items too quickly after boot. :(

---

### Post by Joeb454 on 2008-07-21
> **wrtpeeps said:**
> It's not always to do with a virus.

Windows has closed explorer on me a few times. It does it sometimes on my laptop if I start clicking desktop items too quickly after boot. :(

I nearly edited your post! (It's right next to the quote button)

Thats because Windows requires you to wait a further 10 minutes before you can begin

---

### Post by Dark Aspect on 2008-07-21
What version of windows was he using?I've never actually seen this error before.The only time Windows crashed completely on me was a time when I left my 2k computer for about a hour and when I came back it had the fatal blue screen of death.I rebooted and I had the same error at boot up :(

I became a Ubuntu user after that,

---

### Post by Polygon on 2008-07-21
means windows tried to write in an area that is most likely reserved for the kernel, and windows by default kills any process that tries to write there to protect it from malware and such

---

### Post by zmjjmz on 2008-07-21
> **Polygon said:**
> means windows tried to write in an area that is most likely reserved for the kernel, and windows by default kills any process that tries to write there to protect it from malware and such

Couldn't it just say, oh I dunno, "Permission Denied"?

---

### Post by Polygon on 2008-07-22
most likely not cause ususally the program tried to write there without your knowledge or consent so it just kills the program and says "oh yeah..btw.."

---

### Post by cdekter on 2008-07-22
> **Polygon said:**
> most likely not cause ususally the program tried to write there without your knowledge or consent so it just kills the program and says "oh yeah..btw.."

Actually, DEP is designed to stop execution of the contents of regions of memory that are supposed to be storing data. How did executable code get into the data regions you ask? Buffer overflow...

---

### Post by kamaboko on 2008-07-22
I have conservatively installed Windows on 500 computers (desktops, laptops, and servers) and have never had that problem.  I'd chalk this one up to user error.

---

### Post by songshu on 2008-07-22
> **kamaboko said:**
> I have conservatively installed Windows on 500 computers (desktops, laptops, and servers) and have never had that problem.  I'd chalk this one up to user error.

i've seen it on a laptop before when installing SP2 after installation.

still no clue why it happens but we re-installed several times and SP2 did the trick every time, you can turn it of somewhere making an exception or disable DEP (don't remember where it was)
its been a few years ago already and my friend is running 6.0.6 ever since.

---

### Post by Polygon on 2008-07-22
> **kamaboko said:**
> I have conservatively installed Windows on 500 computers (desktops, laptops, and servers) and have never had that problem.  I'd chalk this one up to user error.

again its not user error, as how would the user tell windows explorer to write to memory that its not supposed to...hmm?

---

### Post by rickyjones on 2008-07-22
I got that error when I was using a questionable copy of Alcohol 120%. Reinstalled Windows without that software and it worked fine. Tested again by doing a clean install with Alcohol 120% and the same thing happened. I'm guessing that the user installed a piece of software that integrated with Explorer.

-Richard

---

### Post by Daveski on 2008-07-22
> **kamaboko said:**
> I have conservatively installed Windows on 500 computers (desktops, laptops, and servers) and have never had that problem.  I'd chalk this one up to user error.

I suspect it is the fact the every application and it's dog installs some explorer add-on such as adding a new menu to the right-click context etc.

---

### Post by Separ on 2008-07-22
> What version of windows was he using?I've never actually seen this error before.The only time Windows crashed completely on me was a time when I left my 2k computer for about a hour and when I came back it had the fatal blue screen of death.I rebooted and I had the same error at boot up

I became a Ubuntu user after that,

He is using Windows XP and outright refuses to use linux because he thinks M$ is the best.

However having said that, I made my own custom distro and he says he will run it in virtualbox to help test it.

One step at a time........

---

### Post by phrostbyte on 2008-07-22
> **songshu said:**
> i don't think its funny at all, it just proves that Microsoft is taking its responsibility when it comes to protecting its customers and provide a healthy commercially supported product.

I'm just surprised that it doesn't recommend Wubi as a critical security update.

That's exactly what I was thinking.

Error: Windows is a terrible operating system
Windows recommends you install Ubuntu.

---

### Post by poofyhairguy on 2008-07-22
killall -9 windows-explorer

---

### Post by Separ on 2008-07-22
> **poofyhairguy said:**
> killall -9 windows-explorer
C:\> killall -9 windows-explorer
'killall' is not recognised as an internal or external command, operable program or batch file.
C:\>

---

### Post by FyreBrand on 2008-07-22
This happens because SP2 is installed (which includes the support for DEP) and the CPU/Mobo combo doesn't support DEP.  This usually happens in older systems.  The answer here is to set DEP appropriately or turn it off.  Here is a Microsoft KB if you're really interested: [http://support.microsoft.com/kb/875351](http://support.microsoft.com/kb/875351)

edit: I've only seen this once or twice.  Typically if DEP isn't supported it doesn't seem to turn itself on.  Maybe it was on by default in this instance.

---

