---
title: "Reboot after upgrading"
date: 2011-02-11
forum: Server Platforms
---

### Post by yvsong on 2011-02-11
How does one know if reboot is needed after upgrading packages with aptitude?

---

### Post by wormyblackburny on 2011-02-11
From command line, it won't tell you. I'd use update manager because it will prompt you if you are worried about it.

---

### Post by JRV on 2011-02-11
A re-boot is usually not necessary unless the kernel is updated.

But it can never hurt.

---

### Post by JohnYYC on 2011-02-11
Is it possible to find out if a reboot is needed via terminal? Specially if your running Ubuntu Server.

---

### Post by egpetrich on 2011-02-12
My server will usually tell me if a reboot is necessary the next time I log in.

- Eric Petrich

---

### Post by sammie12340 on 2011-02-13
> **yvsong said:**
> How does one know if reboot is needed after upgrading packages with aptitude?
Just reboot. not much work, if u dont know what stuff you got running. just type 
> ps aux then do a reboot. and just restart all your stuff. done 2 minutes. and u are sure it works.

---

### Post by CharlesA on 2011-02-13
Most of the time a reboot isn't required after updates, but there are certain ones that need to have the system rebooted to apply - kernel updates in particular, but there are other ones too.

> **JohnYYC said:**
> Is it possible to find out if a reboot is needed via terminal? Specially if your running Ubuntu Server.

It is possible to find out if a reboot is required without logging off and back on to the server - you need to see if this file exists: /var/run/reboot-required

---

### Post by yvsong on 2011-03-01
After updating to 2.6.35.27, I see no /var/run/reboot-required and no alert of reboot required upon the next log in.

---

### Post by theozzlives on 2011-03-01
> **yvsong said:**
> After updating to 2.6.35.27, I see no /var/run/reboot-required and no alert of reboot required upon the next log in.

If you upgraded your kernel, you need to reboot.

---

### Post by CharlesA on 2011-03-02
> **theozzlives said:**
> If you upgraded your kernel, you need to reboot.
Indeed.

I just updated to kernel 2.6.32-29 on both Ubuntu Desktop and Ubuntu Server and /var/run/reboot-requried was present on both.

That file is cleared after you reboot, of course.

---

### Post by yvsong on 2011-04-17
/var/run/reboot-requried is unavailable in Ubuntu 10.10 on Amazon EC2.

---

