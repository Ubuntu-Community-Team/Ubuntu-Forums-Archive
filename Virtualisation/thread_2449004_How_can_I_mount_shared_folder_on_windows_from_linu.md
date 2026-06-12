---
title: "How can I mount shared folder on windows from linux inside virtualbox?"
date: 2020-08-18
forum: Virtualisation
---

### Post by colau on 2020-08-18
I tried with the following command to mount shared folder on windows 10.
```
mount -t vboxsf shared /home/user1/windows/
/sbin/mount.vboxsf: mounting failed with the error: No such device

```
How can I mount shared folder on windows from linux inside virtualbox?

---

### Post by HermanAB on 2020-08-18
Install the Virtualbox Guest Extensions on the Windows host, then use Virtualbox to add a share.

---

### Post by slickymaster on 2020-08-18
*Thread moved to **Virtualisation**.*

---

### Post by colau on 2020-08-18
Solved. I have installed kernel headers.

---

### Post by ajgreeny on 2020-08-18
Great news!

Jus so you understand the reasons behind this, the kernel-headers are required by the guest OS in order for it to build the kernel modules needed for sharing folders and several other of the guest-additions facilities.

Please now mark as SOLVED from the Thread Tools menu up-top if this is solved to your satisfaction. It is a great help to other users searching the forum.

---

### Post by TheFu on 2020-08-18
There are security and file locking considerations when using the *vboxsf* mount method.
May wish to consider treating each system like they are physical and use network-based file sharing protocols, which have a well understood security, file locking, and mitigations for most issues.

---

