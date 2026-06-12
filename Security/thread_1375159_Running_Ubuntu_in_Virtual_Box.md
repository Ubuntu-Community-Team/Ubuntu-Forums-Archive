---
title: "Running Ubuntu in Virtual Box"
date: 2010-01-07
forum: Security
---

### Post by alvin4 on 2010-01-07
Hi, I have a security question. I use vista as my operating system, and I will admit I have sort of abused it security wise, (not running scans very often, not installing updates, etc) and I would not at all be surprised if it has a virus or something. So I was wondering if I installed VirtualBox and ran Ubuntu inside it, moved all of my important confidential stuff to Ubuntu could a windows virus affect the stuff inside of VirtualBox?

Thanks,
Alvin:D

---

### Post by Sarmacid on 2010-01-07
It would be very very difficult for that to happen. The most likely scenario where your files could be harmed would be if any malware corrupted or erased the Ubuntu's VBox files.

---

### Post by alvin4 on 2010-01-07
> **Sarmacid said:**
> It would be very very difficult for that to happen. The most likely scenario where your files could be harmed would be if any malware corrupted or erased the Ubuntu's VBox files.So, I am safe?

---

### Post by running_rabbit07 on 2010-01-07
> **alvin4 said:**
> So, I am safe?

The Ubuntu would be safe. Though the VBox system files which are run by Windows will still be vulnerable.

---

### Post by alvin4 on 2010-01-07
> **running_rabbit07 said:**
> The Ubuntu would be safe. Though the VBox system files which are run by Windows will still be vulnerable.But could a windows virus have access to the files?

---

### Post by scrooge_74 on 2010-01-07
The moment they cross into the virtual machine and that machine is running linux is the same as a windows virus trying to sneak into a real linux machine: it wont happen, it wont have privileges, the linux security wont let it, the virus program wont run on linux, etc, etc

---

### Post by running_rabbit07 on 2010-01-07
But it could crash the VBox in a way that destroys the .vdi file in a way that makes it useless to the Virtual machine. Ubuntu is strong, but in that situation it is like building a brick house on a sandy foundation, one good rain (or virus) could sweep th foundation away and render it useless.

---

### Post by FuturePilot on 2010-01-07
> **running_rabbit07 said:**
> But it could crash the VBox in a way that destroys the .vdi file in a way that makes it useless to the Virtual machine. Ubuntu is strong, but in that situation it is like building a brick house on a sandy foundation, one good rain (or virus) could sweep th foundation away and render it useless.

I agree. The virtual machine would be absolutely useless if something would render Windows unbootable.

---

### Post by Project PWNED on 2010-01-08
I've ran Ubuntu in Virtual Box - it's nicer having it boot as your operating system. VBox doesn't do Ubuntu much justice at all, or if you have a spare computer around, install it on there. You'll be more pleased.

---

### Post by alvin4 on 2010-01-08
Say vista has a keylogger, when I enter a password in ubuntu, could the vista keylogger steal the password?

---

### Post by BkkBonanza on 2010-01-08
That would be close to impossible on a software level but very possible if a hardware keylogger were installed between or in your keyboard.

But as Sarah Connor likes to say, "No one is ever safe".

---

### Post by Project PWNED on 2010-01-08
If you're that paranoid, just enclose you system in a "safe room" that is shielded so Tempest technology, which can read a CRT monitor, is thwarted and run a LiveCD so nothing is stored, then make sure the fin foil hat is working for you.

---

### Post by running_rabbit07 on 2010-01-08
> **Project PWNED said:**
> ...

There is no reason for harassing the OP. If you read the original post, he doesn't keep his AV and such up to date, so he just wants a simple alternative to safely store his files. He is/was hoping that a virtual install would be the cure.

---

### Post by alvin4 on 2010-01-08
Would using Wubi be a safe alternative? Also how is the performance compared to VirtualBox?

---

### Post by The Cog on 2010-01-10
> **alvin4 said:**
> Say vista has a keylogger, when I enter a password in ubuntu, could the vista keylogger steal the password?

Yes it could. Itmay not even realise that you are typing into another OS inside virtualbox - virtualbox is just another windows application.

---

