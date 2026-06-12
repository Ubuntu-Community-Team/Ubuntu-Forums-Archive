---
title: "Windows 8, kali, boot-repair -&gt; bzzzzz"
date: 2014-04-25
forum: Windows
---

### Post by xbit2 on 2014-04-25
Hi, i did funny things today.

 i tried out to install "kali" on my laptop, where "Windows 8.1" uefi already was installed.

 1. i disabled "secure boot option" in bios to be able to boot an install kali via CD.
 2. installed kali whithout grub.
 3. than enabled "secure boot option" and checked if Windows will boot -> yes it did.
 4. booted the live version of ubuntu and started "boot-repair tool" with "recommended repair option" in hope that it will install grub2

 ... but ... 
 all what i now have is a "Gnu grub Version 2.00-19ubuntu2" "Minimal BASH-like line editing ...." grub> command prompt.
 there is no boot choise option, nothing..
 booting from my windows partition fails...

 the link i got from the repair-tool is this: [http://paste.ubuntu.com/7328744/](http://paste.ubuntu.com/7328744/)

 can someone please help me to get a grub boot loader where i can choose between kali and windows ?

 thank you very much.

---

### Post by WoodenWalker on 2014-04-25
If you don't mind me asking, is there any particular reason you installed Kali without Grub?

---

### Post by xbit2 on 2014-04-25
:-\" i thought that i will not need it. and ... there was a 50% change that i was right ;)

---

### Post by WoodenWalker on 2014-04-25
Had you turned off fast-boot prior to install and boot repair?

---

### Post by oldfred on 2014-04-25
Moved to OtherOS since not Ubuntu.

Grub2 is both a boot manager and a boot loader. 

You cannot boot Linux without a boot loader and grub is about the only one that works with UEFI.
Since you have Windows your want Linux in UEFI mode if at all possible. A very few UEFI system will only boot Linux in BIOS mode. And then you can only select which to boot from UEFI menu. UEFI is also a boot manager.

I do not know for sure with Kali, but it does not look like you have secure boot versions of kernels. So you need to have UEFI on, BIOS/CSM off and secure boot off.

Can you boot debian entry in UEFI menu?
It looks like you ran the buggy UEFI in Boot-Repair. With that rename booting Windows in UEFI menu leads to grub menu and you can only boot the renamed Windows from grub menu.
 
Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)

To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

Not sure with newer versions, but grub often did not install correctly with those systems with Intel SRT. That is seen as RAID and then grub wants to install to RAID not normally.

---

