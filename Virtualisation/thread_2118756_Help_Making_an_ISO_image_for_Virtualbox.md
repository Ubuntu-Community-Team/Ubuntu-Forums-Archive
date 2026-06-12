---
title: "Help Making an ISO image for Virtualbox"
date: 2013-02-21
forum: Virtualisation
---

### Post by Joeyxc on 2013-02-21
I have a problem, I wanna use the recovery disks I purchased for my my laptop before I switched to Ubuntu to boot XP with virtual box... How do I do this since it boots straight to a recovery screen not windows?

---

### Post by Cheesemill on 2013-02-22
You can't use recovery discs to install Windows into a VM, you need to purchase a full retail or OEM version of Windows.

---

### Post by lisati on 2013-02-22
> **Joeyxc said:**
> I have a problem, I wanna use the recovery disks I purchased for my my laptop before I switched to Ubuntu to boot XP with virtual box... How do I do this since it boots straight to a recovery screen not windows?

I've moved your question to its own thread: a lot can change in 5+ years.

---

### Post by haqking on 2013-02-22
> **Joeyxc said:**
> I have a problem, I wanna use the recovery disks I purchased for my my laptop before I switched to Ubuntu to boot XP with virtual box... How do I do this since it boots straight to a recovery screen not windows?

Take a clone of your existing Ubuntu Install using clonezilla.

Then use your system restore disk to put your Windows XP back and then take a clone of that.

Clone your Ubuntu back to your laptop.

Then using clonezilla put your XP clone into a VM.

Peace

---

