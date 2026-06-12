---
title: "Can anyone else reproduce this?"
date: 2012-03-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Naddiseo on 2012-03-15
I accidently found a bug yesterday where gnome-terminal crashes if you try to fork a process in a path that is too long. I can reproduce it on my precise machine, I was wondering if anyone else can, and if so, obtain some more info on it. I can't seem to get a backtrace.

Steps to reproduce:
```

mkdir ~/123456789012345678901234567890  # Make the path long
cd ~/123456789012345678901234567890
a& # try to spawn an unknown process

```

I have a bug report, but until I can get more information, it's invalid:

[https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/955546](https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/955546)

---

### Post by meborc on 2012-03-15
nope, your example works fine and no crashes. I am on 64bit with latest updates

---

### Post by flemur13013 on 2012-03-15
I tried your mkdir, etc, and all I got was 

```
a: command not found
[1]+  Exit 127                a
```[FONT=monospace]
[/FONT]
and gnome-terminal  kept working fine.

---

### Post by tekstr1der on 2012-03-15
> **Naddiseo said:**
> I accidently found a bug yesterday where gnome-terminal crashes if you try to fork a process in a path that is too long.

FYI, your path is nowhere near "too long". Ext4 has no defined limit for pathname lengths and the linux kernel defines 4096 chars, so path length is not the cause of your issue.

---

### Post by matt_symes on 2012-03-16
Hi

It's fine on my machine as well.

```

matthew@matthew-Aspire-7540:~$ /usr/lib/command-not-found --version
0.2.44
matthew@matthew-Aspire-7540:~$ uname -a
Linux matthew-Aspire-7540 3.2.0-15-generic #24-Ubuntu SMP Tue Feb 7 22:32:19 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
matthew@matthew-Aspire-7540:~$ 
```

Kind regards

---

