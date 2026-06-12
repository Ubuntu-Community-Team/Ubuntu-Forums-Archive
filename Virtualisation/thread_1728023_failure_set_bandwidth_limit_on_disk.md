---
title: "failure: set bandwidth limit on disk"
date: 2011-04-13
forum: Virtualisation
---

### Post by yangguo1220 on 2011-04-13
i there,

I am trying to test the "limit disk bandwidth" function. I followed the instructions in the user manual to first create a bandwidth group, then attach the disk image to the bandwidth group. However, i got the following error when I try to re-start the VM.

Failed to open a session for the virtual machine guest1.
Unknown error creating VM (VERR_GENERAL_FAILURE).

Result Code:  NS_ERROR_FAILURE (0x80004005)
Component:  Console
Interface: IConsole {515e8e8d-f932-4d8e-9f32-79a52aead882}


I detach the disk image first, then attach it with bandwidth group, then fails as above. Also, I tried not to detach the disk image and directly add it into the bandwidth group, it also fails.

Did I do something wrong ?

Thanks,

Ning

---

