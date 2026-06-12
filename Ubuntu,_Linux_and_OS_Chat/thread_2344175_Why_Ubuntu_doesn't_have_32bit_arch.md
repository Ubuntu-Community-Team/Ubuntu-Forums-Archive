---
title: "Why Ubuntu doesn't have 32bit arch?"
date: 2016-11-23
forum: Ubuntu, Linux and OS Chat
---

### Post by mintmag on 2016-11-23
Can someone please tell me why Ubuntu 64bit doesn't come with 32bit architecture? I know you can install it manualy but why is it set up this way. I've always had trouble installing 32bit in Ubuntu.

---

### Post by mintmag on 2016-11-23
Hello is anyone there? Maybe someone from Canonical could tell me.

---

### Post by QIII on 2016-11-23
Please do not demand an answer.  If you do not receive answers to your queries within 12 hours, it is appropriate to respond to your own thread with the word "bump" to bring it back to the top.

If you are interested in hearing from someone at Canonical for their explanation, you are welcome to contact them.  I suggest starting with [email]ubuntu-devel-discuss@lists.ubuntu.com[/email]

This is a strictly volunteer user forum.  Canonical developers and employees generally do not come here.

---

### Post by 1clue on 2016-11-23
32-bit hardware can't run 64-bit code.

64-bit hardware can run either 32 or 64-bit code.

It's a hardware limitation.

---

### Post by Dennis N on 2016-11-23
You don't need to install anything - just enable it with a single terminal command. Then you are good to go. Not having a ton of 32-bit libraries on the default install saves space.

---

### Post by mintmag on 2016-11-24
> **Dennis N said:**
> You don't need to install anything - just enable it with a single terminal command. Then you are good to go. Not having a ton of 32-bit libraries on the default install saves space.

If you're referring to ```
dpkg add-architecture i386
``` it didn't work for my 32Bit GOG games.

---

### Post by mc4man on 2016-11-24
> **mintmag said:**
> If you're referring to ```
dpkg add-architecture i386
``` it didn't work for my 32Bit GOG games.
If you need i386 packages on a 64bit install you'd need to install them manually unless your game(s) were packaged properly for multi-arch.

---

### Post by Dennis N on 2016-11-25
> **mintmag said:**
> If you're referring to ```
dpkg add-architecture i386
``` it didn't work for my 32Bit GOG games.

If you need help, start a thread on a help forum such as General Help. I've installed 5 or 6 32-bit games on my 64-bit Xubuntu systems. These were not packaged as .deb files.

As you said, Linux Mint includes a lot of the 32-bit libraries on their 64-bit systems by default, so it is easier there.

---

### Post by mintmag on 2016-11-25
> **Dennis N said:**
> If you need help, start a thread on a help forum such as General Help. I've installed 5 or 6 32-bit games on my 64-bit Xubuntu systems. These were not packaged as .deb files.

As you said, Linux Mint includes a lot of the 32-bit libraries on their 64-bit systems by default, so it is easier there.

I don't recall mentioning Mint, but should GOG package their games with 32bir packages?

---

### Post by Dennis N on 2016-11-25
> I don't recall mentioning Mint, but should GOG package their games with 32bir packages?
I must be seeing things. I know what GOG is, but I'm not familiar with their packages. I got all my Linux games through Humble Bundle, mostly several years ago. Quite a few were created only in 32-bit versions. Otherwise, I wouldn't bother with 32-bit.

---

### Post by mintmag on 2016-11-25
> **Dennis N said:**
> I must be seeing things. I know what GOG is, but I'm not familiar with their packages. I got all my Linux games through Humble Bundle, mostly several years ago. Quite a few were created only in 32-bit versions. Otherwise, I wouldn't bother with 32-bit.

It is true they work betting with Mint, though I think it's silly not to include 32bit lib files for 64Bit. If you want tiny just use 32Bit?

---

### Post by vasa1 on 2016-11-25
> **mintmag said:**
> I don't recall mentioning Mint, ...
You have been recommending Mint to people in this forum :)
[https://ubuntuforums.org/showthread.php?t=2343199&p=13573261#post13573261](https://ubuntuforums.org/showthread.php?t=2343199&p=13573261#post13573261)
[https://ubuntuforums.org/showthread.php?t=2342827&p=13571417#post13571417](https://ubuntuforums.org/showthread.php?t=2342827&p=13571417#post13571417)
And in [https://ubuntuforums.org/showthread.php?t=2339400&p=13554943#post13554943](https://ubuntuforums.org/showthread.php?t=2339400&p=13554943#post13554943) you implied you're asking here because "the Mint forums are kind of empty" :???:

---

### Post by mintmag on 2016-11-25
> **vasa1 said:**
> You have been recommending Mint to people in this forum :)
[https://ubuntuforums.org/showthread.php?t=2343199&p=13573261#post13573261](https://ubuntuforums.org/showthread.php?t=2343199&p=13573261#post13573261)
[https://ubuntuforums.org/showthread.php?t=2342827&p=13571417#post13571417](https://ubuntuforums.org/showthread.php?t=2342827&p=13571417#post13571417)
And in [https://ubuntuforums.org/showthread.php?t=2339400&p=13554943#post13554943](https://ubuntuforums.org/showthread.php?t=2339400&p=13554943#post13554943) you implied you're asking here because "the Mint forums are kind of empty" :???:

In the forums yes but not on this thread.

---

### Post by vasa1 on 2016-11-25
> **mintmag said:**
> In the forums yes but not on this thread.

So?

---

### Post by mintmag on 2016-11-26
> **vasa1 said:**
> So?

I don't understand, is there a point to this?

---

### Post by mintmag on 2016-12-15
So does anyone know why there is no 32bit arch included with Ubuntu. Are there version of Ubuntu that do have it?

---

### Post by 1clue on 2016-12-16
Exactly what sort of answer are you looking for?

Reading the responses to this thread I see all sorts of helpful information from multiple interpretations of your question.

1. 32-bit architecture is not automatically installed on the 64-bit installer because 32-bit is a waste of space for anyone who doesn't specifically need 32-bit software support.
2. Adding multiple architectures automatically increases code complexity which means there are a correspondingly larger number of bugs and vulnerabilities which apply to your system.

Either of those reasons would be good enough to not include 32-bit automatically on a 64-bit installer. I'm sure I could think of other reasons to leave it out, but this is enough.

You could install 32-bit Ubuntu, and then everything would be 32-bit. Some people with 64-bit hardware still do this, although that choice makes no sense to me.

---

### Post by mintmag on 2016-12-17
> **1clue said:**
> Exactly what sort of answer are you looking for?

Reading the responses to this thread I see all sorts of helpful information from multiple interpretations of your question.

1. 32-bit architecture is not automatically installed on the 64-bit installer because 32-bit is a waste of space for anyone who doesn't specifically need 32-bit software support.
2. Adding multiple architectures automatically increases code complexity which means there are a correspondingly larger number of bugs and vulnerabilities which apply to your system.

Either of those reasons would be good enough to not include 32-bit automatically on a 64-bit installer. I'm sure I could think of other reasons to leave it out, but this is enough.

You could install 32-bit Ubuntu, and then everything would be 32-bit. Some people with 64-bit hardware still do this, although that choice makes no sense to me.

How much space does it take. Also are there official versions of ubuntu that come with 32bit arch?

---

### Post by QIII on 2016-12-17
Your question has been asked and answered to the best ability of the volunteers who populate these forums.  Please direct further inquiry to Canonical, LTD.

Closed.

---

