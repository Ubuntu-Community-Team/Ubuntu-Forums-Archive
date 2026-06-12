---
title: "cable connected but no internet in Virtualbox"
date: 2010-09-19
forum: Virtualisation
---

### Post by Pyrohyper on 2010-09-19
Hi there.
I am using for the host Ubuntu 10.04 and for the guest i am using Windows XP pro.
My network adapter is set to NAT.
It says that cable is connected but i don't have internet on guest.
Shared folder works well.
Help me please :cheers:

---

### Post by CharlesA on 2010-09-19
*Moved to **Virtualization**.*

Anyway, what does ipconfig /all return?

---

### Post by Pyrohyper on 2010-09-19
How to see that?
I am 100% noob

i went to Windows XP (Start, All Programs, Accessories, Command Prompt) and there was no return
Windows IP Configuration was writen and nothing else

---

### Post by CharlesA on 2010-09-19
That usually means that no network card was detected. You can check device manager to see if a network card was detected or not.

This is probably a better question to ask on a Windows forum.

---

### Post by Pyrohyper on 2010-09-19
Thanks for info. But it should recognize virtual box card for internet

---

### Post by CharlesA on 2010-09-19
Which card do you have listed under "network" in virtualbox?

Mine's using "AMD PCNet-FAST III network card"

---

### Post by Pyrohyper on 2010-09-19
Intel PRO/1000 MT Desktop (NAT)

---

### Post by CharlesA on 2010-09-19
Was it listed in device manager?

If not, try using a different card.

---

### Post by Pyrohyper on 2010-09-19
it's not listed :(

---

### Post by CharlesA on 2010-09-19
Try a different card. Windows XP is very picky about what it has drivers for.

If you installed it in virtualbox, it should have found the card regardless of which one you were using.

---

### Post by Pyrohyper on 2010-09-19
You are the MAN! ! !
I changed card to PCNet-FAST III and now it's working!
Now comes the question, how to delete this Thread? :)

---

### Post by CharlesA on 2010-09-19
Mark it as solved from the thread tools menu.

---

