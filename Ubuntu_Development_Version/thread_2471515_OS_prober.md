---
title: "OS prober"
date: 2022-02-01
forum: Ubuntu Development Version
---

### Post by MyMurry on 2022-02-01
Hello,

I think they can't deactivate it for the LTS. 

Regrads

---

### Post by guiverc on 2022-02-01
Sorry I don't know your issue, or what you're asking. You've not provided any OS & release specifics, though the area in which you've posted likely means you're using Ubuntu *jammy*.

Likely your issue is this one -

- [https://lists.ubuntu.com/archives/ubuntu-devel/2021-December/041769.html](https://lists.ubuntu.com/archives/ubuntu-devel/2021-December/041769.html)

this issue doesn't impact all boxes; but it impacts many, with the bug report here

- [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1955109](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1955109)

With Lubuntu we're tracking it [here]("https://discourse.lubuntu.me/t/lubuntu-jammy-issue-tracker-os-prober-grub-2-06/2952/") (*along with normal QA-tracker of course*), but you'll note the work around in the aforementioned bug report works for all users I've spoken too who help QA-test, and has always worked for me too.

---

### Post by MyMurry on 2022-02-18
I think the normal user can't handle this. After a Ubtuntu install he can't start Windows any more. I remember the time as Windows kills the Ubuntu boot loader and I couldn't start Ubuntu any more. It needs at least a option or package to restore the boot menu.

regards

---

### Post by #&amp;thj^% on 2022-02-18
If I understand correctly, the OP might have seen:
```
Warning: os-prober will not be executed to detect other bootable partitions.
Systems on them will not be added to the GRUB boot configuration.
Check GRUB_DISABLE_OS_PROBER documentation entry.
Adding boot menu entry for UEFI Firmware Settings ...
done

```
Some distros have now disabled "os-prober" for security.
Nothing stops anyone from changing it back to:
```
GRUB_DISABLE_OS_PROBER=false
```
in "**_/etc/default/grub_**"

---

### Post by mIk3_08 on 2022-02-18
> **MyMurry said:**
> I think the normal user can't handle this. After a Ubtuntu install he can't start Windows any more. I remember the time as Windows kills the Ubuntu boot loader and I couldn't start Ubuntu any more. It needs at least a option or package to restore the boot menu.
regards This is always at your own risk. When you decide to do a dual boot you should know first the consequences and risk. Now the best way to do is to contact your administrator for this technical issues. But if you can still handle the situation then the community is always willing to help you. Now where are we going to start now? I think we should start from scratch now. So good luck and cheers

---

### Post by MyMurry on 2022-02-19
The latest update solve the problem:

> grub2 (2.06-2ubuntu5) jammy; urgency=medium

  [ Julian Andres Klode ]
  * Free correct size when freeing params, rather than 16 Ki (LP: #1958623)
  * Build with FUSE3 (LP: #1935659)
  * Only run os-prober on first run and if it previously found other OS
    (LP: #1955109)

---

### Post by mIk3_08 on 2022-02-19
> **MyMurry said:**
> The latest update solve the problem:
Good to hear this thing. So good luck and cheers..

---

