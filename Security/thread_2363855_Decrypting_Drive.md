---
title: "Decrypting Drive"
date: 2017-06-15
forum: Security
---

### Post by mark.constant on 2017-06-15
We have setup an enterprise application on Ubuntu 16.04. When I was told to build the server I was asked to encrypt the Hard-Drive. Now I have been asked to permanently unencrypt it. It is a VM. I know I basically need to add a new VDMK and then copy the content over and a bunch of other items need to change. Is there a step by step direction for this that somebody has found? I know it would normally be easier to reinstall but there already a lot of customizations on this server and it really isn't an option.

---

### Post by TheFu on 2017-06-15
Welcome to the forums.

Do your normal backup, then restore to a fresh install to a new VM. Just remove the crypttab and grub settings for encryption.  Since it is a VM, you can test this over and over and over without any risks.

I wouldn't try to do this in-place. I'd do it into a new VM.

A server that has too many functions on it is a liability. There are often inter-dependencies that break things over time.

BTW, if you didn't keep sufficient notes to recreate the server, I think the IT methods used could use improving.  Servers need "run books" or just use devops methods to build the server.  All my servers aren't perfect and I'd have trouble recreating some myself. Plenty of room for improvement here.

As for encryption, I find it easier to handle at the hostOS level, not inside each VM. If the hypervisor can't handle that out of the box for $0, perhaps a better hypervisor should be considered?

Or not.

---

