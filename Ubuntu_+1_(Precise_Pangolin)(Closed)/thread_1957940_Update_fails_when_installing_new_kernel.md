---
title: "Update fails when installing new kernel"
date: 2012-04-13
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by PatrickD-52761 on 2012-04-13
Hello everyone,

Let me start by saying that I had this issue on 11.10, when I tried to compile my own kernel.  Ultimately I did a clean installation to 12.04 and have been happy up until now. Now this happens with the update to the linux-3.2.0-23-generic kernel that was offered to me via apt-get/update notifier.

Here are the results that I get when I run apt-get (or in this case dpkg --configure )
```
patrickdickey@dcky-ubuntu64:~$sudo dpkg --configure linux-image-3.2.0-23-generic 
Setting up linux-image-3.2.0-23-generic (3.2.0-23.36) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-23-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic


```

The update/dpkg --configure hangs at this stage, until I kill it with CTRL+C. Then it comes back with errors in processing, and says it didn't process linux-3.2.0-23-generic.

Originally I started this update on Wednesday evening, and it was hung until Thursday afternoon (when I killed it the first time).

So my questions are how do I get this to finish, or how do I clear it from the queue, so I can update other things/install other applications?

Right now, if I try apt-get <anything> it says that I have to run dpkg --configure -a. Which puts me right back where I'm at.

How do I submit a bug about this (and which package should I submit it against)?

Thanks, and have a great weekend.:)
Patrick.

---

### Post by dino99 on 2012-04-13
if it hang while trying to update-grub, then im thinking about dkms, is it installed ?

but start some cleanings : clean/autoclean/autoremove, maybe bleachbit as root too.

then purging & reinstalling grub-pc (supposed there is no more grub legacy & menu.lst around, right ?)
maybe some packages conflict ; check the sources.list (only Precise archives) and ppa in case.

update
sudo dpkg-reconfigure -phigh -a
(can take a while, dont stop it)

note: i've no clue about compiling kernel, im too lazy and use kernel-ppa instead, but i suppose you are used to do it.

---

### Post by PatrickD-52761 on 2012-04-13
> **dino99 said:**
> if it hang while trying to update-grub, then im thinking about dkms, is it installed ?

but start some cleanings : clean/autoclean/autoremove, maybe bleachbit as root too.

then purging & reinstalling grub-pc (supposed there is no more grub legacy & menu.lst around, right ?)
maybe some packages conflict ; check the sources.list (only Precise archives) and ppa in case.

update
sudo dpkg-reconfigure -phigh -a
(can take a while, dont stop it)

note: i've no clue about compiling kernel, im too lazy and use kernel-ppa instead, but i suppose you are used to do it.

[EDIT] A quick clarification. I put the information about my experience with the 11.10 and compiling my own kernel in to show that this problem isn't confined to 12.04. In this situation (on Ubuntu 12.04) it was just a normal series of updates through the Update Manager (which is set to install development updates along with everything else).

Yes, dkms is installed (as I have virtualbox installed). As for grub, all I *should* have is what comes with Precise. And as for the compiling the kernel, I tried it on 11.10, and it failed miserably (in fact, I think it was the 3.2.x series also). So everything that I'm getting now is coming from ubuntu's PPA's.

I don't think I have bleachbit installed, so that's out (since I can't install it until I fix this).  I'll try the autoclan/clean and then your update and dpkg commands to see what happens.  And I'll report back with whatever results I get.

Thanks, and have a great day:)
Patrick.

P.S. running sudo apt-get autoremove puts me right back into the loop--as it tries to finish the installation for me.

---

### Post by PatrickD-52761 on 2012-04-13
> **dino99 said:**
> if it hang while trying to update-grub, then im thinking about dkms, is it installed ?

but start some cleanings : clean/autoclean/autoremove, maybe bleachbit as root too.

then purging & reinstalling grub-pc (supposed there is no more grub legacy & menu.lst around, right ?)
maybe some packages conflict ; check the sources.list (only Precise archives) and ppa in case.

update
sudo dpkg-reconfigure -phigh -a
(can take a while, dont stop it)

note: i've no clue about compiling kernel, im too lazy and use kernel-ppa instead, but i suppose you are used to do it.

Ok, I tried the sudo dpkg-reconfigure command.  Here are the results:

```

patrickdickey@dcky-ubuntu64:~$sudo dpkg-reconfigure -phigh -a
Package `gtk2-engines-oxygen' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: gtk2-engines-oxygen is not installed
patrickdickey@dcky-ubuntu64:~$

```

So, unless there's a better way of cleaning this up, I'm worried that I'll have to do another reinstall (or at the very least an "upgrade" from 12.04 to 12.04.  I'll have to leave for work in about 2 hours, so tomorrow I'll spend the day moving everything off of the computer, and tomorrow night or Sunday, I'll do the reinstallation (unless we can find something else to fix this).

Have a great day:)
Patrick.

---

### Post by PatrickD-52761 on 2012-04-14
Finally an update that shows progress...

I tried using Bleachbit from source (without having to install it), and it cleaned up a lot -- but still had the same errors. So, I started playing around with dpkg, and found in the help this gem:

```

sudo dkpg --purge --pending

```

I ran that, and then ran sudo apt-get update && sudo apt-get upgrade (no more dist-upgrade for me).  Right now, I'm in the middle of 309 updates.  So, it worked (as long as I don't run into the same issue during this round).

I wish someone had documented this feature better in the blogosphere, as it would have saved me a lot of heartache back when I was on 11.10.

If the updates complete successfully, I'll be back to mark this thread as solved.  If not, I'll still be looking for advice.

Have a great day, and thanks for the assistance. :)
Patrick.

---

