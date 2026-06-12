---
title: "Adjusting policies for ASLR/DEP?"
date: 2012-03-11
forum: Security
---

### Post by Hungry Man on 2012-03-11
I'm new to Ubuntu from Windows and I'm interested in playing around with the security features. I currently have apparmor profiles set up for Chromium (renderer/ browser) and pidgin as well as other processes.

On Windows I know you can change the policies regarding SEHOP, DEP, and ASLR. SEHOP doesn't apply to Linux, so I'm curious about whether I can change it for DEP/ ASLR.

Windows has DEP set to Opt-Out and ASLR set to Opt-In. Is this similar to how Linux does this? Any way to force an application to use DEP/ASLR?

---

### Post by Ms. Daisy on 2012-03-12
DEP appears to be called "Userspace Hardening" and includes ASLR in this link:

[https://wiki.ubuntu.com/Security/Features](https://wiki.ubuntu.com/Security/Features)

That link indicates that they are included by default in all recent versions.

---

### Post by Hungry Man on 2012-03-12
Right, they're supported by the kernel (and hardware) but that doesn't necessarily mean that applications are using them. The OS can force applications to use them but I can say with confidence that it's not forcing ASLR system wide - otherwise my OS would not boot.

So I'm wondering what the policies are and if they can be modified.

---

### Post by bpny on 2012-03-13
You can use this tool [http://www.trapkit.de/tools/checksec.html](http://www.trapkit.de/tools/checksec.html) to check security features on Ubuntu.

---

### Post by Hungry Man on 2012-03-13
That looks helpful, thank you.

---

