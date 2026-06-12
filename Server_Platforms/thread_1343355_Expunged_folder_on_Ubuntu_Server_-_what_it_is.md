---
title: "Expunged folder on Ubuntu Server - what it is"
date: 2009-12-01
forum: Server Platforms
---

### Post by jocampo on 2009-12-01
Silly question ... but I'm kind of worried. My Server was down or rebooted (still investigating the reason) the other day and today, I just found a weird and new folder on my home directory. The folder name is "expunged".

Can someone explain the meaning of "expunged" folder to me and why it could be there or why or who created it?

Thanks in advance,

---

### Post by munky99999 on 2009-12-02
Hmm that's a bit unusual to me. I'm thinking perhaps what happened was a file(s) were deleted and the trash was being emptied and failed to complete due to perhaps the shutdown.

Might also be security related. You might want to verify what happened.

---

### Post by jocampo on 2009-12-02
Thanks for reply. 

Can I say, based on your comment than when a deletion process fails, Ubuntu server creates that folder... with that particular name?

---

### Post by munky99999 on 2009-12-02
> **jocampo said:**
> Thanks for reply. 

Can I say, based on your comment than when a deletion process fails, Ubuntu server creates that folder... with that particular name?

Barring the obvious security breach + remote user doing it.

I honestly dont know what could have done it. The only thing that comes to mind would be emptying trash. Which is called expunging. Nothing else really related.

---

### Post by cariboo on 2009-12-03
The "expunged" directory is created when you install BleachBit

---

### Post by jocampo on 2009-12-06
> **cariboo907 said:**
> The "expunged" directory is created when you install BleachBit

well, I have NOT installed such program and my server has a private IP. I run a Virtual Machine on it with public IP, but I doubt has been compromised; it is running UFW and is fully patched, I checked it frequently.

Still.. strange to me ...

---

### Post by bsautner on 2010-11-26
Any progress on this? I just found this thread since i found an Expunged folder on a drive i download torrents to. No crash, no failed trash empty. Up to date Ubuntu 10.10 workstation... weird.

---

