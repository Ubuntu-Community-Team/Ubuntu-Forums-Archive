---
title: "A newbie is tired of dual-booting"
date: 2008-09-20
forum: Virtualisation
---

### Post by Zdravko on 2008-09-20
Hi there!
I have already Vista running on my laptop. I left some few GBs at the end for a future Linux installation. However, I am not quite sure whether this dual-boot is very efficient. Is there a way to install Ubuntu on top of Vista and run both OS'es simultaneously? I just hate it to switch back and forth between each OS just because I want to check something.
Explain me what are the possible configurations with such a virtualization.
Thanks in advance!

---

### Post by mike1234 on 2008-09-20
> **Zdravko said:**
> Hi there!
I have already Vista running on my laptop. I left some few GBs at the end for a future Linux installation. However, I am not quite sure whether this dual-boot is very efficient. Is there a way to install Ubuntu on top of Vista and run both OS'es simultaneously? I just hate it to switch back and forth between each OS just because I want to check something.
Explain me what are the possible configurations with such a virtualization.
Thanks in advance!

 Maybe try Wubi? VM isn't all it's cracked up to be. I have it installed and it works okay. Never tried MS virtual machine.

[http://wubi-installer.org/](http://wubi-installer.org/)

M.

---

### Post by Zdravko on 2008-09-20
What is Wubi? And how will it help me run Ubuntu and Vista in the same time?

---

### Post by mike1234 on 2008-09-20
> **Zdravko said:**
> What is Wubi? And how will it help me run Ubuntu and Vista in the same time?

 From your post I gathered you only have Vista installed as of now, correct? You can install wubi and still keep Vista plus have Ubuntu also. And if you don't like wubi you can simply uninstall it.  I think I would give it a try. 

M.

---

### Post by Zdravko on 2008-09-20
Ah, yes - I just read this. But I still have to reboot my laptop to start the other OS, right?

---

### Post by mike1234 on 2008-09-20
> **Zdravko said:**
> Ah, yes - I just read this. But I still have to reboot my laptop to start the other OS, right?

 Yes, nothings perfect. Even VM requires "rebooting" of sorts. I have XP on VM, and it has to be started, stopped. Wubi is just for people to get a feel for Ubuntu before installing or converting over to Linux.

M.

---

### Post by howefield on 2008-09-20
> **Zdravko said:**
> Ah, yes - I just read this. But I still have to reboot my laptop to start the other OS, right?

Correct, you would be no further forward given your criteria of not rebooting from one os to another.

You could download Virtualbox for Windows and install Ubuntu into a virtual machine, that way you can run both operating systems simultaneously. There is also a free program available from Microsoft, I think it is called Virtual PC.

Running a virtual machine needs a decent amount of ram to run well, as you will allocate some of your system memory to the guest operating system, I wouldn't want to run Vista and a guest system on less than 2 gig, bare minimum.

---

### Post by Zdravko on 2008-09-20
Aha. I will install Ubuntu in the usual way, then - in the spare room in a separate partition. I will have to live with the restart.

---

### Post by smo0th on 2008-09-20
wubi makes you restart and you don't wanna restart, you could use vmware on top of vista and install ubuntu in a virtual machine

although for me is better using vmware to virtualize the wind0ze os ;)

---

### Post by Zdravko on 2008-09-20
> **howefield said:**
> Correct, you would be no further forward given your criteria of not rebooting from one os to another.

You could download Virtualbox for Windows and install Ubuntu into a virtual machine, that way you can run both operating systems simultaneously.

Running a virtual machine needs a decent amount of ram to run well, as you will allocate some of your system memory to the guest operating system, I wouldn't want to run Vista and a guest system on less than 2 gig, bare minimum.
Okay, I will stick to dual-boot then! Thanks for the explanation.

---

### Post by ajhunt on 2008-09-20
Just seen this thread and like you was tired of rebooting. I've gone down the VM route but with Linux as the main OS with Vista as the VM. For me, the performance is a bit better that way plus most of the day to day stuff I do in Linux. I do have a fairly good spec laptop with 2gb memory though which helps!

---

### Post by michaelkahl on 2008-09-20
I haven't dual-booted in a long time...but I've used alternatives to help when I needed Windows for something.
I'd tried virtualization before and wasn't pleased...but I tried it in windows, on a 32bit OS, and with 2GB memory.  Now I'm running Ubuntu 64 with 4GB memory, and running 2 VM's is extremely smooth.
I use Virtual Box OSE with Guest Options installed.
As for WUBI, well it has it's place...but thats somewhere between using a live CD and doing a dual-boot. I don't think it's a good permanent install method.  I used it to help configure and document my Ubuntu install till I got everything working.  Then I uninstalled XP and went strait Linux.
To each there own..if it works stick with it.  At least WUBI doesn't leave you open to that accidental "O CRAP!" moment when you realize you killed your windows partition.

---

