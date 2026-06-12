---
title: "Automatic install to pure LVM system"
date: 2012-01-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by sgifford on 2012-01-16
Hello,

I'm using preseeding to automatically install Precise onto a pure LVM system, with root and /boot on LVM.  LVM booting is officially supported by Grub 2, and works fine as far as I can tell.

When I'm installing, I get one warning about having /boot on LVM.  I also get two warnings about not being able to stat the /dev/mapper devices, but they work when I select "Retry", so I think it's just a timing thing.

Despite these warnings, the system installs fine, and boots fine after installation.

I am wondering if there is a preseed option to suppress the warning about /boot on LVM, and if anybody has any advice for avoiding the other two warnings?

I am also wondering if /boot on LVM will be a supported configuration for Precise, since the required tools all support it?

I will attach screenshots of the errors I'm seeing, and a copy of my preseed file.

Thanks for any advice!

-----Scott.

---

### Post by kevpan815 on 2012-01-16
I thought that there was a Bug Report of some kind about how LVM installs are not working right now (Some how i got my self subscribed to the E-mail) and occasionally receive updates about the Bug Report to my E-mail Address.

---

### Post by sgifford on 2012-01-17
> **kevpan815 said:**
> I thought that there was a Bug Report of some kind about how LVM installs are not working right now (Some how i got my self subscribed to the E-mail) and occasionally receive updates about the Bug Report to my E-mail Address.

Thanks for your response kevpan815!

I searched around in the bug reports, and while I found some reports of LVM not working in some circumstances (like with a large snapshot or when installing on top of an existing LVM drive), I didn't get the impression it never works at all.  I may have missed the bug you're talking about; if you can point me towards it I'll take a look.

It works fine for me though, except for these warnings from the installer that stop my automatic installation from being automatic.  Once I select "OK" and "Retry" for those, the installation completes successfully, and everything works.

Mainly I'm looking for a way to get rid of those warnings so the installation is completely automatic, and also to hear about it if anybody thinks that running the entire system from LVM (including /boot) is a terrible idea.

Thanks,

-----Scott.

---

