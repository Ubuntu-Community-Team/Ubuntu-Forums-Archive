---
title: "Ubuntu UEFI Boot Entry Bug"
date: 2013-04-24
forum: Ubuntu Development Version
---

### Post by donniezazen on 2013-04-24
Hello,

efivars is unable to create a boot entry with the current kernel and the [bug]("https://bugzilla.redhat.com/show_bug.cgi?id=947142") seems to have been fixed upstream which I suppose will not end up in 13.04 ISO making it impossible to boot Ubuntu unless you make two installation media one with 13.04 and one with 12.10 to create boot entry. What do you guys think?

Thanks.

---

### Post by grahammechanical on 2013-04-24
People expect to install Ubuntu without any issues and they have had this expectation for a long time. But it is always been the case that Ubuntu is not easy to install on some hardware. That is why we have F6 options. The F6 options have been there for as long as I have been installing Ubuntu (coming up to six years). 

From the first day that Windows 8 machines were put on the market people expected to install Ubuntu without any issues. And when things did not work out correctly, they expected there to be ready made tutorials available on this forum. These are impossible expectations.

Do you have any evidence that that Redhat bug also applies in Ubuntu? Please provide the link to the Launchpad bug reference.

I can tell you this, in recent days there have been several kernel updates on Raring. Things have quietened down a lot over the last two days with hardly any updates at all. But we have had plenty of kernel updates since the end of March. Please download 13.04 and do a test install on a EFI system with secure boot enabled and report back.

Regards.

---

### Post by donniezazen on 2013-04-24
> **grahammechanical said:**
> People expect to install Ubuntu without any issues and they have had this expectation for a long time. But it is always been the case that Ubuntu is not easy to install on some hardware. That is why we have F6 options. The F6 options have been there for as long as I have been installing Ubuntu (coming up to six years). 

From the first day that Windows 8 machines were put on the market people expected to install Ubuntu without any issues. And when things did not work out correctly, they expected there to be ready made tutorials available on this forum. These are impossible expectations.

Do you have any evidence that that Redhat bug also applies in Ubuntu? Please provide the link to the Launchpad bug reference.

I can tell you this, in recent days there have been several kernel updates on Raring. Things have quietened down a lot over the last two days with hardly any updates at all. But we have had plenty of kernel updates since the end of March. Please download 13.04 and do a test install on a EFI system with secure boot enabled and report back.

Regards.

I am personally hit by this bug. Installation works fine but no boot entry is created. This bug has been discussed in Arch Linux forum ad nauseum as they are the first to get hit by such bugs. Other folks too have reported this issue on Ubuntu. [https://plus.google.com/100275307499530023476/posts/CXkbqf8i9YQ](https://plus.google.com/100275307499530023476/posts/CXkbqf8i9YQ) 

Thanks.

---

### Post by oldfred on 2013-04-24
Lets see some detail.
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

