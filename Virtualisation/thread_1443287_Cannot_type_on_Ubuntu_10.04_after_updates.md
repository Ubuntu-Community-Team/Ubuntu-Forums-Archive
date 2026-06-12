---
title: "Cannot type on Ubuntu 10.04 after updates"
date: 2010-03-30
forum: Virtualisation
---

### Post by The Patriot on 2010-03-30
I am using VMare Fusion on Mac. After updating and restart, I can no longer type with my keyboard.

---

### Post by mkvnmtr on 2010-03-31
Check the known bugs on the 10.04 forum. If you do not find one maybe you should make one.
If you are lucky tomorrow the update might fix it.

---

### Post by The Patriot on 2010-03-31
> **mkvnmtr said:**
> Check the known bugs on the 10.04 forum. If you do not find one maybe you should make one.
If you are lucky tomorrow the update might fix it.

Where's the 10.04 thread?

---

### Post by The Patriot on 2010-03-31
> **The Patriot said:**
> Where's the 10.04 thread?

I reinstall it but I won't be updating it as the update contain bug that disable the keyboard. Which update should I avoid?

---

### Post by codfather on 2010-03-31
Try turning off the advanced graphics mode, as I had a similar issue with Ubuntu 10.04 VM with VirtualBox.

This assumes you can still use the mouse, click on the System -> preferences -> Apperance menu item, and select the Visual effects tab and then select none.

Have you installed the VMware tools for your virtual machine as they will have changed if you have upgraded your version of Fusion.

hth

Nick

---

### Post by mkvnmtr on 2010-03-31
In the development section you will find the forum for 10.04. There you can see what problems others a re havind and encounter the link to the launchpad site.
I have installed 10.04 in virtual box about 10 times and always seem to lose it on an update. Feedback from others will probably not help me because I use a very stripped down minimal install. Right now the problem seems to be getting thenmoduals loaded to install guest additions. Runs fine until I run the guest additions and after a restart I get a pretty green screen that does not let me do anything. I will keep trying about once a week until it works. I really like it  when it works and think I will install it on my computer after the release.

---

### Post by The Patriot on 2010-03-31
> **codfather said:**
> Try turning off the advanced graphics mode, as I had a similar issue with Ubuntu 10.04 VM with VirtualBox.

This assumes you can still use the mouse, click on the System -> preferences -> Apperance menu item, and select the Visual effects tab and then select none.

Have you installed the VMware tools for your virtual machine as they will have changed if you have upgraded your version of Fusion.

hth

Nick

I cannot login, I am at the login screen unable to do anything because I cannot type my password.

---

### Post by codfather on 2010-04-01
Does your mouse still work? If it does then you can use the Assistive technologies keyboard to enter your password. It is at the bootom of the login screen. If you haven't got the mouse, then look at the VM BIOS in the virtual machine and see if you can change settings there.

It might be worth having a look on the VMware forums to see if anyone has had a similar issue with Fusion. I only use VMware Workstation,Virtualbox and KVM on Linux, and I have never seen this issue. 

hth

Nick

---

### Post by Stoneface on 2010-04-18
I have the same problem. I cannot type either using 10.04 LTS (Stable now). I run Ubuntu in VMWare Fusion on by Macbook Pro as well. I still have to use the assitive keybaord. After logging on I can type without any problems. So it is not like I cannot do anything. But I just would like to enter the password directly withouth the assistive keyboard...

---

### Post by Stoneface on 2010-04-18
Just saw somebody using VmWare and Ubuntu 10.04 has the same problem and reported a bug @ [https://bugs.launchpad.net/ubuntu/+source/console-setup/+bug/548891](https://bugs.launchpad.net/ubuntu/+source/console-setup/+bug/548891) I have added myself to the list of affected people.

---

### Post by Stoneface on 2010-04-18
In the earlier mentioned bug report there was an excellent tip that worked for me. Open a terminal and add ```
sudo dpkg-reconfigure console-setup
``` Than choose Mac Book Pro (or computer of choice). It was MacBook Pro Intel in my case and US keyboard  with support for some alfabets and UTF8 worked. NB I did a reboot to activate this reconfiguration.. et voila!

---

### Post by The Patriot on 2010-04-29
Thanks, finally works.

---

