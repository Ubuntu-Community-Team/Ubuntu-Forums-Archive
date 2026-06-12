---
title: "Shared folder with VMware and Ubuntu 22.04"
date: 2022-05-12
forum: Virtualisation
---

### Post by Complete on 2022-05-12
I am using Ubuntu 22.04 as a Virtual machine using VMWare Workstation 16 Pro hosted on a Windows 10 Pro computer.

There is an issue with having shared folder between the virtual machine and the host.  It is documented with VMware and the solution involved adding a line to /etc/fstab

When I try to edit this file, I find it is read only.

I tried to change the read and write settings for the file and the directory it is in.  

[IMG]https://i.stack.imgur.com/BfMbD.png[/IMG]

But this did not work and when I opened the file with gedit, it still displayed the file in read-only mode.

Please advise.

---

### Post by TheFu on 2022-05-12
Don't use gedit.

Use **sudoedit** to edit the /etc/fstab file. This has been the safest way to edit system files for years now. Older and out-of-date guides often show other commands. Not all are bad, but using sudo with most GUI programs is a bad idea, sometimes with terrible outcomes.

I find the chmod commands above scary.  It is very important NOT to change the permissions on system files.

---

### Post by Complete on 2022-05-13
> **TheFu said:**
> Don't use gedit.

Use **sudoedit** to edit the /etc/fstab file. This has been the safest way to edit system files for years now. Older and out-of-date guides often show other commands. Not all are bad, but using sudo with most GUI programs is a bad idea, sometimes with terrible outcomes.

I find the chmod commands above scary.  It is very important NOT to change the permissions on system files.

Excellent advice.
Thanks much !!

---

### Post by slickymaster on 2022-05-13
*Thread moved to **Virtualisation**.*

---

### Post by Complete on 2022-05-13
> **slickymaster said:**
> *Thread moved to **Virtualisation**.*

Ok.
Thanks.
Done.

---

