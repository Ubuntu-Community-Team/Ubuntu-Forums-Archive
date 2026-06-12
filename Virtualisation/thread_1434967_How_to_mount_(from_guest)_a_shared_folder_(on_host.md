---
title: "How to mount (from guest) a shared folder (on host). Both op sys are Ubuntu 9.1 Deskt"
date: 2010-03-20
forum: Virtualisation
---

### Post by charleswb on 2010-03-20
I have an Ubuntu 9.1 Desktop that I'm using for a host computer in a VMware Player virtualization. I have various Windows Guest op systems, and an Ubuntu 9.1 Desktop Guest op system.

I want to share a folder on the host op sys so that all the guest op systems can access the folder.

VMware automatically took care of this for me with the Windows Guests. All I had to do (in VMware virtual machine settings) was select the sharing option and give the path on the host. That was easy, and worked flawlessly with the Windows guest, but not with the Ubuntu guest.

On the Ubuntu guest, VMware did take care of the file sharing part automatically (on host), such that shared file (on host) can be seen by the Ubuntu Guest, but the Ubuntu Guest does not mount the shared folder. 

The Ubuntu Guest sees part of the path for the shared folder on the Ubuntu Host, but not the last part that would let me see the folder and mount it.

**I have tried (in the Guest) to manually mount the shared folder (on the Host), but I don't know how to do this, or don't know why I can't.**

Please advise. Thank you for your help.

---

