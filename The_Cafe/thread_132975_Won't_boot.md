---
title: "Won't boot"
date: 2006-02-19
forum: The Cafe
---

### Post by kruzzin on 2006-02-19
I have 4 HD's. My primary are 2 80gb Sata drives. I have Windows installed on the first one.
I also have 2 40gb IDE HD that run on a promise card. I installed Ubuntu for PC from the install CD and everything appeared to go fine, until, it said to take out the CD and reboot and then finish the install.
When it reboots it just goes to Windows...Nothing about the Linux install.
Any Suggestions...
Or do you need more info...
Thanks

---

### Post by mstlyevil on 2006-02-19
[QUOTE=kruzzin]I have 4 HD's. My primary are 2 80gb Sata drives. I have Windows installed on the first one.
I also have 2 40gb IDE HD that run on a promise card. I installed Ubuntu for PC from the install CD and everything appeared to go fine, until, it said to take out the CD and reboot and then finish the install.
When it reboots it just goes to Windows...Nothing about the Linux install.
Any Suggestions...
Or do you need more info...
Thanks[/QUOTE]

It sounds to me like you told it no on installing Grub to the MBR. You have to select yes when it ask you to install the Grub or else the MBR will only see Windows. Try reinstalling it and this time let it rewrite Grub to the MBR and it should work.

---

