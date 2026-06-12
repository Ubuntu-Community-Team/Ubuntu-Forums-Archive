---
title: "Mouse problems in Windows XP under Virtualbox"
date: 2010-09-26
forum: Virtualisation
---

### Post by Daisho on 2010-09-26
Greetings, friends!
I recently managed to migrate my native Windows xp installation to VB under Ubuntu and even got the famous reactivation problem sorted out. However, I've been trying to solve some problems I have with my mouse for about a week now without success. The problem is that VB seems to interpret all mouse movements/scrolling as "scroll down" (I can still move the cursor, it seems to be taking dual action, both movement and scroll down at the same time).
Has anyone else experienced this? Any tips or ideas?
Also, when I deactivate mouse integration the cursor jumps to the right border of the screen and only moves up and down (and does a lot of automatic right-clicking) until mouse integration is activated again through hotkey.

I run Ubuntu 10.04 64-bit Lucid as host, Oracle Virtualbox 3.2.8 with Windows XP SP3 32-bit as guest. My mouse is a cordless Logitech S510, driver through Logitech SetPoint.

Thanks,
Daisho

---

### Post by ScottyD135 on 2010-12-03
> **Daisho said:**
> Greetings, friends!
I recently managed to migrate my native Windows xp installation to VB under Ubuntu and even got the famous reactivation problem sorted out. However, I've been trying to solve some problems I have with my mouse for about a week now without success. The problem is that VB seems to interpret all mouse movements/scrolling as "scroll down" (I can still move the cursor, it seems to be taking dual action, both movement and scroll down at the same time).
Has anyone else experienced this? Any tips or ideas?
Also, when I deactivate mouse integration the cursor jumps to the right border of the screen and only moves up and down (and does a lot of automatic right-clicking) until mouse integration is activated again through hotkey.

I run Ubuntu 10.04 64-bit Lucid as host, Oracle Virtualbox 3.2.8 with Windows XP SP3 32-bit as guest. My mouse is a cordless Logitech S510, driver through Logitech SetPoint.

Thanks,
Daisho

I'm having the same problem, but my host is ubuntu 9.10 Karmic 32-bit, Windows XP SP3 32-bit as guest.  I am also using a logitech cordless mouse but don't have the model number handy.  Just wanted to confirm that this isn't an isolated problem!

ScottyD

---

### Post by Groodles on 2010-12-05
Have you installed VirtualBox Guest Additions yet on the Windows VM?

---

### Post by ScottyD135 on 2010-12-05
> **Groodles said:**
> Have you installed VirtualBox Guest Additions yet on the Windows VM?

I can't say for certain, but I didn't notice it as a problem until AFTER I installed guest additions...  Although, I installed them pretty quickly after getting the VM set up.

S

---

### Post by Daisho on 2010-12-19
> **ScottyD135 said:**
> I can't say for certain, but I didn't notice it as a problem until AFTER I installed guest additions...  Although, I installed them pretty quickly after getting the VM set up.

S
Just as I did. Migrated XP, installed guest additions and then I realised that something was wrong. Anyway it's good to know I'm not the only one with this problem  :roll:

---

