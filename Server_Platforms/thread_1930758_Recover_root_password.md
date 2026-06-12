---
title: "Recover root password"
date: 2012-02-24
forum: Server Platforms
---

### Post by Ataraxos on 2012-02-24
Hi all!
 
I am trying to access an old ubuntu server machine but I don't know the root pass.
I tried to hold shift while opening and then it gave me the Lilo boot console with no recovery options so I wrote "Linux single" but nothing happened. It opens but I don't have user/pass info.
Any clue what can I do? I don't have cd or any other info about ubuntu version etc. 
Physical access to machine is my only path.
 
Thanks in advance

---

### Post by agillator on 2012-02-24
[http://www.debianadmin.com/forgot-root-password-or-reset-root-password-in-debian.html](http://www.debianadmin.com/forgot-root-password-or-reset-root-password-in-debian.html) should work for you, I believe.

---

### Post by roelforg on 2012-02-24
I'm not gonna give hacking instructions, only use this when you really forgot your OWN root password.
I'm not responsible for any consequences.

Boot with in the grub cmdline
```

init=/bin/sh

```And use
```

passwd root

```to change the pass.

---

### Post by iponeverything on 2012-02-24
> **Ataraxos said:**
> Hi all!
 
I am trying to access an old ubuntu server machine but I don't know the root pass.[
I tried to hold shift while opening and then it gave me the Lilo boot console with no recovery options so I wrote "Linux single" but nothing happened. It opens but I don't have user/pass info.[
Any clue what can I do? I don't have cd or any other info about ubuntu version etc. 
Physical access to machine is my only path.
 
Thanks in advance

you can reset the password but not recover it. The encryption is one-way.

---

### Post by Ataraxos on 2012-02-28
@agillator
boot: Linux init=/bin/sh didn't work
It returns me not such an image
It boots only with "Linux" but this is a normal boot.
The machine runs Ubuntu and has LILO boot manager.
Any ideas how to reset the root password?

---

### Post by zeljkojagust on 2012-02-28
Which Ubuntu is it? You can try and boot with one of LiveCD distros, mount root partition and change hash in /etc/shadow file for root user.

---

### Post by Ataraxos on 2012-02-28
> **zeljkojagust said:**
> Which Ubuntu is it?
 
I don't know... How i can see this?
Surely must be a very old version.

---

### Post by Elfy on 2012-02-28
Run this from a terminal 

```
lsb_release -a
```

---

### Post by Ataraxos on 2012-02-29
> **forestpiskie said:**
> Run this from a terminal 
 
```
lsb_release -a
```
 
I don't have access on a terminal...
No user or root account on the machine

---

### Post by surfer on 2012-02-29
boot with a live cd and do what is described in the link posted by agillator.

---

### Post by ssam on 2012-02-29
> **iponeverything said:**
> you can reset the password but not recover it. The encryption is one-way.

john the ripper might be able to brute force the password, given the hashed password file. though if you had a good password, it could take a long time.

---

### Post by Iowan on 2012-02-29
If it's a standard Ubuntu install, there may not be a root password.

---

### Post by ablin1 on 2012-04-08
> **forestpiskie said:**
> Run this from a terminal 

```
lsb_release -a
```

i did this on my computer and it came up with:

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 11.10
Release:    11.10
Codename:    oneiric

please help - thanks in advance

---

### Post by N4RPS on 2012-06-09
> **agillator said:**
> [http://www.debianadmin.com/forgot-root-password-or-reset-root-password-in-debian.html](http://www.debianadmin.com/forgot-root-password-or-reset-root-password-in-debian.html) should work for you, I believe.

Hello!

Thanks, man. You ROCK!

:guitar:

This did the trick in helping me reset my PW and get around that bloody minimum PW length requirement that prevented it. Always figured if you could do it on install, you could do it at other times; this URL helped me figure out how.

73 DE N4RPS
Rob

---

