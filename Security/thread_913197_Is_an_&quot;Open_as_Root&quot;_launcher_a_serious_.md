---
title: "Is an &quot;Open as Root&quot; launcher a serious hazard?"
date: 2008-09-07
forum: Security
---

### Post by TheMaxzilla on 2008-09-07
I was showing [this]("http://ubuntuforums.org/showthread.php?t=24008&page=1") page to a friend, and he said that it was a serious security hazard. Can someone tell me if it actually is or not, and why it would be?

---

### Post by lukjad on 2008-09-07
I haven't tried it but here is a (possible) reason why this is not good. ***If*** it doesn't require a password every time you drag 'n' drop something in it, then there is a potential security risk since anyone, or any program could then access the critical files in your computer. However, I think that there will be a password prompt for this launcher. If there is, I see not real security risk, especially since it was a well respected Ubuntu Member.

---

### Post by lukjad on 2008-09-07
I just tried it and it **does** ask for the root password. It still doesn't open anything, but I wouldn't worry about it too much. I just wouldn't install it, it isn't useful, at least to me.

---

### Post by mister_pink on 2008-09-07
There's no security risk at all as far as I can tell. Its exactly the same as going and typing something on the command line with "sudo", gnome-open is just a program that will automatically decide what program to use to open the file. It will ask for your password just as often as normal sudo-ing (ie will remember it for 15 minutes.)

---

### Post by Oldsoldier2003 on 2008-09-07
It's no more dangerous than using sudo. 

Random, unthinking use of sudo ( regardless of how you invoke it ) is the real hazard.

---

### Post by TheMaxzilla on 2008-09-08
Okay, thanks then.

---

### Post by lukjad on 2008-09-08
Does it work for anyone else? It doesn't seem to work for me.

---

