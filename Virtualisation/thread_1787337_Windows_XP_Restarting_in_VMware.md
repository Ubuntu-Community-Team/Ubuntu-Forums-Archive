---
title: "Windows XP Restarting in VMware"
date: 2011-06-21
forum: Virtualisation
---

### Post by derekreilly on 2011-06-21
Hi guys,

I am using Kubuntu 11.04 and installed Windows XP in VMware player 3.1.4.I installed VMware tools so I could get full-screen. This worked, however when I restart the virtual Windows, it doesn't get past the Windows XP logo, it just keeps restarting over and over again.

I have also tried this in Vbox and the same thing happens there too. 

Any ideas?

---

### Post by Jake.Debord on 2011-06-21
Is it restarting on its own or are you restarting it?

---

### Post by derekreilly on 2011-06-21
It keeps restarting on it's own. It's like it's on a loop.

---

### Post by Jake.Debord on 2011-06-21
I would suggest firstly, running through your settings and making sure you have everything set satisfactory simple things too like RAM, video ram etc etc... If you can, check your ISO file make sure it's not corrupt... You may need to try a new ISO with a fresh install.

---

### Post by fjgaude on 2011-06-23
This happens in both VMware and VBox? Wow! You have two different VMs, one for VBox and one for VMware?

---

### Post by derekreilly on 2011-06-23
> **fjgaude said:**
> This happens in both VMware and VBox? Wow! You have two different VMs, one for VBox and one for VMware?


I've been trying to run WXP on each of them but have the same issue.

---

### Post by derekreilly on 2011-06-23
> **Jake.Debord said:**
> I would suggest firstly, running through your settings and making sure you have everything set satisfactory simple things too like RAM, video ram etc etc... If you can, check your ISO file make sure it's not corrupt... You may need to try a new ISO with a fresh install.

Everything is set as default.

---

### Post by fjgaude on 2011-06-24
That's what I use, WinXP; works great in VMware Player.

Maybe you need to re-install Player or WinXP.

---

### Post by Dedoimedo on 2011-06-25
What kind of bus are you using for disk?
Dedoimedo

---

### Post by zero244 on 2011-06-25
I agree it could be a setting for that paticular V-Machine.
If youve never had that VM working you may have to recreate it.
If you move a VM from one computer to another different computer you may have to adjust the settings.

I have used both VMware Player and V-Box and I have found VMware player less likely to crash.

If you select more than one core for windows xp in vmwares settings, that could break windows.
I dont think windows xp supported dual core cpu's till sp2.

---

