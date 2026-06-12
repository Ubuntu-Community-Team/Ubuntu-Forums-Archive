---
title: "Putting limitation on a program"
date: 2011-06-05
forum: Security
---

### Post by grofff on 2011-06-05
I must run a program for which no sourcecode is available, so I would like to know what is the easier way in ubuntu to force limitations on it, for example not allowing it to access hard disk, or only allow access to its own directory. 

I've scanned quickly the net for similar questions, and usually the replies either suggested apparmor or urged not to run an untrusted program under any circumstances. The latter option isn't available to me, because I need this program and will never be 100% sure of what's inside it. As for apparmor, I understand that it is only for programs that you already trust, but fear they could be hijacked through some bug (I've tried to follow a howto, but the profile generator needs the program to be run in the first place).

---

### Post by FuturePilot on 2011-06-05
> **grofff said:**
> As for apparmor, I understand that it is only for programs that you already trust

Not true. It's for any program, trusted or not. Some people apparmor Adobe Reader, Flash, and Skype. If you get to know apparmor a little you can create some kind of simple base profile and then tweak it from there.

---

### Post by grofff on 2011-06-06
> **FuturePilot said:**
> Not true. It's for any program, trusted or not. Some people apparmor Adobe Reader, Flash, and Skype. If you get to know apparmor a little you can create some kind of simple base profile and then tweak it from there.

Could you point me to a howto that explains how to do this? (the more simple and specific the better... probably this will be the only situation in which I need apparmor). The ones I found were usually centred about using the profile generator, that requires the program to be run in the first place).

---

### Post by Lars Noodén on 2011-06-06
[http://wiki.apparmor.net/index.php/Documentation#How-to_and_Tutorials](http://wiki.apparmor.net/index.php/Documentation#How-to_and_Tutorials)

[http://wiki.apparmor.net/index.php/Profiling_with_tools](http://wiki.apparmor.net/index.php/Profiling_with_tools)

[http://wiki.apparmor.net/index.php/Profiling_by_hand](http://wiki.apparmor.net/index.php/Profiling_by_hand)

[http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

---

### Post by ohadcn on 2011-06-06
in the worst case you can run it in chrooted enviroment

---

### Post by bodhi.zazen on 2011-06-06
> **ohadcn said:**
> in the worst case you can run it in chrooted enviroment

chroots are sort of out of favor as they are relatively easy to break out of and take some time to configure.

apparmor and selinux are both much better options then a chroot.

---

