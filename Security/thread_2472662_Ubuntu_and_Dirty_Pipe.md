---
title: "Ubuntu and Dirty Pipe"
date: 2022-03-08
forum: Security
---

### Post by spattent on 2022-03-08
So, you probably have heard about the latest privilege escalation vulnerability in the Linux kernel:
[https://dirtypipe.cm4all.com/](https://dirtypipe.cm4all.com/)

Vulnerability was first introduced in Linux 4.9, got more easy to exploit in Linux 5.8, and was fixed in Linux  5.16.11, 5.15.25, 5.10.102.

Ubuntu 20.04.4 LTS uses Linux 5.4.0 :o

Since I can't seem to find an Ubuntu security advisory about this, is Ubuntu 20.04.4 LTS effected? I think with kernel 5.4.0 we have to assume it *is* effected. Has it already been patched before the public announcement? If so, what exact package version contains the fix?

(Apparently, 5.4.0.100.104 seems to be the latest kernel image available on Ubuntu 20.04.4 LTS at this time)

Thank you and regards.

---

### Post by oldos2er on 2022-03-08
> **spattent said:**
> I can't seem to find an Ubuntu security advisory about this

[https://ubuntu.com/security/CVE-2022-0847](https://ubuntu.com/security/CVE-2022-0847)

---

### Post by spattent on 2022-03-08
> **oldos2er said:**
> [https://ubuntu.com/security/CVE-2022-0847](https://ubuntu.com/security/CVE-2022-0847)

Can you explain a little more? What exactly does status "Needs triage" mean? And where can we see which *exact* [FONT=courier new]linux-image-generic[/FONT] package version contains the fix for the vulnerability?

Thank you and regards.

---

### Post by TheFu on 2022-03-08
> **spattent said:**
> So, you probably have heard about the latest privilege escalation vulnerability in the Linux kernel:
[https://dirtypipe.cm4all.com/](https://dirtypipe.cm4all.com/)

Vulnerability was first introduced in Linux 4.9, got more easy to exploit in Linux 5.8, and was fixed in Linux  5.16.11, 5.15.25, 5.10.102.


That appears to be incorrect. Even the link provided says v5.8 is where it was introduced, no v4.x kernels are listed as critical.

According to Ars Technica:

> The vulnerability [COLOR="#FF0000"]_first appeared in Linux kernel version 5.8_[/COLOR], which was released in August 2020. The vulnerability persisted until last month, when it was fixed with the release of versions 5.16.11, 5.15.25, and 5.10.102.

So, 20.04 not running the HWE stack isn't impacted.  5.4 is before the problem started.

Newer isn't better. **New** is the enemy of **stable**.

---

### Post by alexmurray on 2022-03-08
Updates to fix this in the affected kernels (Ubuntu 21.10 and Ubuntu 20.04 LTS running the HWE stack) have been published - [https://ubuntu.com/security/notices/USN-5317-1](https://ubuntu.com/security/notices/USN-5317-1)

---

### Post by spattent on 2022-03-09
Thank you all for the clarification!

BTW: I think the original publication says the underlying problem was first introduced in 4.9, but became "critical" (in the sense of the currently known exploit) in 5.8.
So it wasn't clear whether there *might* be other exploits that work with 4.9+ too. As I understand it now, the experts believe versions < 5.8 are safe, at the moment.

---

### Post by TheFu on 2022-03-09
> **spattent said:**
> Thank you all for the clarification!

BTW: I think the original publication says the underlying problem was first introduced in 4.9, but became "critical" (in the sense of the currently known exploit) in 5.8.
So it wasn't clear whether there *might* be other exploits that work with 4.9+ too. As I understand it now, the experts believe versions < 5.8 are safe, at the moment.

If you are patching your Ubuntu systems weekly and have stayed on supported releases, then you won't have this issue.[s] It was handled last month.  [/s]This is typically how all Linux security issues are handled.

Plus, if your servers systems don't have any local users - and most shouldn't - then it doesn't really matter. It isn't a remote attack. Someone needs to be on the system already.  Of my 20-ish systems, only 3 have regular humans on them. The rest provide services, not local user accounts.

This attack is really about companies providing local accounts onto shared systems and shared infrastructure.  You're reasonably secure webserver is fine, provided it isn't on a shared hosting system with 3000 other users.  And if it is on a shared hosting system, perhaps saving $5 a month really isn't worth it?

**Update: Appears I was wrong in thinking these were patched last month in Ubuntu.  Mar 9, 2022 is when the patches were released (today).**

---

### Post by oldos2er on 2022-03-09
As alexmurray says, there were kernel updates (for me) this morning.

---

### Post by lsutiger on 2022-03-15
I am running xubuntu 20.04.1 and my uname -r 5.11.0-46-generic. Is my system in the clear?
Output of find /boot/vmli*
/boot/vmlinuz
/boot/vmlinuz-5.11.0-46-generic
/boot/vmlinuz-5.13.0-30-generic
/boot/vmlinuz-5.13.0-35-generic
/boot/vmlinuz.old

---

