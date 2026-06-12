---
title: "Can GRUB affect my VMWare Guest OS?"
date: 2008-04-06
forum: Virtualisation
---

### Post by breezey on 2008-04-06
My PC (Intel Q6600) runs Windows Vista 64bit and I have VMWare Workstation running XP 64 as guest OS. I just installed Ubuntu 8.04 Beta (x86) running dual boot with the Vista. Installation was successful and everything was fine until when I was trying to boot my XP guest OS. It says that I am trying to run 64 application while my hardware does not support it.

My question: what's the odd that the GRUB caused this given that I installed 32bit Ubuntu? I just want to make sure that it is the case before I reinstall Ubuntu using 64bit.

Also, Ubuntu AMD64 version runs on Intel 64 bit, right? Thanks for your help.

---

### Post by fjgaude on 2008-04-06
GRUB shouldn't effect any VM installs in eiterh Vista or Ubuntu, but...

If you are using a two or more drive setup, for everything to work correctly and not have to use BIOS to point at one drive or another, you should install Windows, Vista, or what have you, and then install Ubuntu. That way you will be able to acces Windows from Ubuntu, etc.

---

### Post by breezey on 2008-04-06
> **fjgaude said:**
> ... you should install Windows, Vista, or what have you, and then install Ubuntu. That way you will be able to acces Windows from Ubuntu, etc.

That's what I did. I have already had Vista 64 bit as the only OS on my pc for a while... and I have XP 64bit only as guest OS on my Vista. Then I want to dual boot my vista with Ubuntu and it happened that I installed Ubuntu 32bit. Only then I found that I can't boot my XP 64bit eventhough my Vista doesn't seem to be affected.

---

### Post by fjgaude on 2008-04-06
> **breezey said:**
> That's what I did. I have already had Vista 64 bit as the only OS on my pc for a while... and I have XP 64bit only as guest OS on my Vista. Then I want to dual boot my vista with Ubuntu and it happened that I installed Ubuntu 32bit. Only then I found that I can't boot my XP 64bit eventhough my Vista doesn't seem to be affected.

I see, you have WinXP over a VM under Vista. Are you on two drives?

When you boot up, do you see the GRUB menu coming from the install of Ubuntu? You then click on Vista and when loaded you load up the VM running WinXP. That's the way I see it, at least for now.

When you remove the 32-bit Ubuntu and install a 64-bit version, the GRUB menu will be re-generated and all should be okay. If not, it is easy to fix by editing the menu.lst file in /boot/grub directory of Ubuntu.

Let us know how you ae doing.

---

### Post by breezey on 2008-04-06
That's correct... my XP runs as VM under Vista.

I have two SATA drives but I installed all Vista and Ubuntu on the same drive on different partition.

GRUB correctly gives me the boot list and I can boot up my Vista without problem.

So, do you think that the fact GRUB was created by Ubuntu 32bit then that's probably why I can't start my XP 64? Thanks.

---

### Post by fjgaude on 2008-04-06
You mean while in Vista you can't start the WinXP VM? That's strange. I don't think it would have anything to do with the 32-bit install of Ubuntu.

How did you normally access WinXP while in Vista? But you can't now?

---

### Post by breezey on 2008-04-06
Uhm... just found new fact. Just tried to login to my Ubuntu and it seems that it wasn't setup properly even though the installation was successful. I boots to BusyBox on my Ubuntu. But I guess this is a separate issue ... so I will create a new thread.

---

### Post by breezey on 2008-04-06
> **fjgaude said:**
> You mean while in Vista you can't start the WinXP VM? That's strange. I don't think it would have anything to do with the 32-bit install of Ubuntu.

How did you normally access WinXP while in Vista? But you can't now?

I run XP using VMWare Workstation. And yes, it was running withough problem.

---

### Post by fjgaude on 2008-04-06
And the problem started when you installed Ubuntu in one of the partitions on the same disk as Vista, got a GRUB menu, but now you can't start WinXP while running Vista.

I can't see how 32-bit Ubuntu would have caused this issue.

Maybe someone else here has an idea.

---

