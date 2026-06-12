---
title: "Boot up in prompt - How to??"
date: 2005-09-21
forum: Server Platforms
---

### Post by phpgeek on 2005-09-21
Hi,

I choosed the boot option "server" when I installed... everything worked fine.. and did get the prompt the first time...

Rebooted the server - and nothing happens It just hangs with the message "Starting periodic command scheduler... . kground" Anyway - I found out it have nothing to do the the periodic command scheduler - tried to disable it in the rc.d - and the "Initializing random number generator... . kground" was just the last message then...

I can fine access the server through SSH, FTP etc. but I really want to be able to login directly on the server - and I can't get it to work...

Anyone know how to make this happens? I can do it though recovery mode - but thats really are no good... wants to get the login prompt when i just boot up the server normally..

Hope someone have a solution to my problem - otherwise im getting crazy

FYI: Linux XXXX.XXX.XX 2.6.12-8-amd64-generic #1 Thu Sep 15 22:59:26 BST 2005 x86_64 GNU/Linux

(Dual Xeon Server... )
Add to phpgeek's Reputation   	Edit/Delete Message

---

### Post by generallimptoes on 2005-09-28
I have the same problem with a PII 400, 256 RAM.  I did the same process, and it hangs at the same spot.  Any one know what to do?

---

### Post by lao_V on 2005-09-28
What are you running? Warty/Hoary/Breezy?

---

### Post by JimmyJazz on 2005-10-04
try hitting ctrl+alt+f2 (or ctrl+alt+f1) and see what happens.

---

