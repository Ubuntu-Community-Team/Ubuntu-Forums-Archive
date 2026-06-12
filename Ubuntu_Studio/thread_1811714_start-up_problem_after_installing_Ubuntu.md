---
title: "start-up problem after installing Ubuntu"
date: 2011-07-25
forum: Ubuntu Studio
---

### Post by kimia_95 on 2011-07-25
I had windows 7 on my laptop until i installed Ubuntu, when i restart it in order to complete my installation it just started Ubuntu and it seemed that windows 7 is disappeared. but i later understood that my windows 7 has a start-up problem which i don't know and i can't fix it.Do you think uninstalling Ubuntu would help or you suggest a better way?please help me.:(

---

### Post by rickytikki on 2011-07-25
how did you insttall through wubi like inside windows7? do you see a grub laoder with windows 7 on it? what might have happend is that the MBR for windows is messed up for some reason MBR(master boot record) but ansewr these questions to make sure thats what it is.

---

### Post by alberto2172 on 2011-07-25
Your GRUB Loader got messed up because it hates Ubuntu. Well Windows hates Ubuntu and wants to be the only OS thats running. All you have to do is go to your GRUB menu and click on the one with 'recovery' mode. That scroll down to 'Fix GRUB' and that should fix it. If you cant login to GRUB use the Ubuntu Live CD and use the Terminal to fix the problem. 

I dual boot my Windows 7 and Ubuntu OS and every time that Windows Updates its has a tendency to mess up the GRUB Loader.

Or is it that you have this same problem as the link below..:

[http://ubuntuforums.org/showthread.php?t=1794285&highlight=GRUB](http://ubuntuforums.org/showthread.php?t=1794285&highlight=GRUB)

---

