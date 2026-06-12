---
title: "VMware - The guest operating system has locked the CD-ROM"
date: 2020-04-15
forum: Virtualisation
---

### Post by mubeenkh on 2020-04-15
I've been struggling with the following problem.

I need to install vmware tool in a virtual xubuntu OS, and it's not letting me do that. I'd appreciate if anyone here could help me with this.

> 
The guest operating system has locked the CD-ROM door  and is probably using the CD-ROM, which can prevent the guest from  recognizing media changes. If possible, eject the CD-ROM from inside the  guest before disconnecting.

Disconnect anyway and override the lock?


Thanks.

---

### Post by TheFu on 2020-04-15
Have you tried ejecting the virtual optical disk? Use the umount command, if needed.  It is possible the install ISO is still connected to the VM in the VM settings. Check that too.

---

### Post by mubeenkh on 2020-04-15
I don't see any virtual disk connected. And the ISO which I used to install the OS, I've changed that ISO to the physical CD-ROM. So, it's not mounted as well.

---

### Post by jnguyen-m on 2020-04-16
> **mubeenkh said:**
> I've been struggling with the following problem.

I need to install vmware tool in a virtual xubuntu OS, and it's not letting me do that. I'd appreciate if anyone here could help me with this.



Thanks.

Hi [**[COLOR=#000000]mubeenkh[/COLOR]**]("https://ubuntuforums.org/member.php?u=2143394"),

It should always be locked because it is a CDROM. Just copy the content to your hard drive and execute from there.

jn

---

