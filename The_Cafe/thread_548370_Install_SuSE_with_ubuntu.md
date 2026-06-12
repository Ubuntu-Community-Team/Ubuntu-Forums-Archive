---
title: "Install SuSE with ubuntu"
date: 2007-09-11
forum: The Cafe
---

### Post by Eriksmits596 on 2007-09-11
Hi guys!
I was wonder if I just can install openSUSE so it uses ubuntu's bootloader? I mean: Currently I have Win XP + Ubuntu dualboot with grub. And now im wondering if there is anyway in the SuSE installation to select a option that uses the bootloader as alredy is installed?:)
Thanks/Erik

---

### Post by Castar on 2007-09-11
Are you afraid that it won't recognise Ubuntu+WinXP?

The bootloader in openSUSE is much nicer than Ubuntu's :)

---

### Post by igknighted on 2007-09-11
In the suse install (unlike the Ubuntu install sadly) you have an option to not install a bootloader or to add the bootloader to a partition instead of the MBR (the recommended method here).  Install the Suse bootloader to the partition Suse is on, then copy/paste the Windows entry in your /boot/grub/menu.lst file.  Change the title to something that will identify it as opensuse to you (can be whatever you want), and change the partition it points to from the windows partition to the suse partition.  Now, when it boots it will go to Ubuntu's grub, and if you select suse it will go to suse's grub.  This way you don't have to manually add kernels when they update or any other nonsense, each distro will update its grub as needed.

EDIT: I agree with castar though, Suse has a much better tool for configuring grub, plus it comes with a very pretty look to it.  But in the end the work required to install Suse's grub to the mbr and then put Ubuntu's back on its partition just isn't worth it... unless you want to do it to learn.

---

### Post by Incense on 2007-09-11
+1 for the openSUSE bootloader. It's pretty, and it does a great job of detecting your other OS. You could also consider running SUSE in Virtual Box for a while if you don't want to muck around with bootloaders.

---

### Post by Dragonbite on 2007-09-11
I have a similar but opposite situation:

I have WinXP and openSuse 10.2 installed on my computer and want to install Edubuntu as well but I want to preserve the openSuse bootloader and/or make sure the boot loader gives me the 3 options (even if I update).

Any ideas how to do that?  I'd rather not have to uninstall openSuse, install Edubuntu and then reinstall openSuse.

---

### Post by Incense on 2007-09-11
> **Dragonbite said:**
> I have a similar but opposite situation:

I have WinXP and openSuse 10.2 installed on my computer and want to install Edubuntu as well but I want to preserve the openSuse bootloader and/or make sure the boot loader gives me the 3 options (even if I update).

Any ideas how to do that?  I'd rather not have to uninstall openSuse, install Edubuntu and then reinstall openSuse.

Just use the live cd and allow ubuntu to take over, then load SUSE, open YaST-System-Bootloader, click the bootloader installation tab to reinstall SUSE grub (or LILO), and add Ubuntu under your section management list. I've never tried this, but I don't see why it wouldn't work. Good luck!

---

### Post by Eriksmits596 on 2007-09-11
Thx for all the help, I should try it in the next week:)

---

### Post by Dragonbite on 2007-09-11
When you say > **Incense said:**
> ... then load SUSE, open YaST-System-Bootloader, click the bootloader installation tab to reinstall SUSE grub (or LILO), and add Ubuntu under your section management list. !do you mean to load SuSE from the Grub menu choices Ubuntu creates or to use the CD1 of openSuse (like a recovery CD)?

I've got to get a copy of Clonezilla (copyzilla?) and make a clone of the partition first.  Dont' want to loose the changes I've made so far.

---

### Post by igknighted on 2007-09-11
> **Dragonbite said:**
> I have a similar but opposite situation:

I have WinXP and openSuse 10.2 installed on my computer and want to install Edubuntu as well but I want to preserve the openSuse bootloader and/or make sure the boot loader gives me the 3 options (even if I update).

Any ideas how to do that?  I'd rather not have to uninstall openSuse, install Edubuntu and then reinstall openSuse.

Hmm, upon further review you can click the "advanced" tab on the last step of Ubuntu's live install and grub will, by default, install to (hd0).  This is the MBR of the first drive.  You can change it to (hd0,#) - assuming only one HD - where # is the partition number that Ubuntu is to be installed on.  Bear in mind that grub uses a zero index counting scheme, so partition sda1 would be (hd0,0) and sda2 would be (hd0,1), etc.  Then use the same procedure as above, except do it in Suse and add Ubuntu.

---

### Post by Andrewie on 2007-09-11
I suggest you hold off installing Opensuse for awhile. The next version is going to have an option during the install that will auto detch all your distro. But if you still want to install make sure that you install Opensuse last, it has the better tools then ubuntu and should detech your current ubuntu install.

---

### Post by Eriksmits596 on 2007-09-11
Souds great! I think I wait until openSuSE 10.3 have been released in stable version then:)

---

### Post by Castar on 2007-09-11
> **Eriksmits596 said:**
> Souds great! I think I wait until openSuSE 10.3 have been released in stable version then:)

Less than a month away! :guitar:

---

### Post by Eriksmits596 on 2007-09-12
Good!;)

---

### Post by thisllub on 2007-09-12
10.3 looks very good.

I will be giving it serious consideration, especially now the install is less bloated.

It is worthwhile learning how to install grub manually. I have saved a few systems by understanding how to fix  bootloaders and  damaged raid partitions.
I'll bet nearly everyone has seen 
GRUB error 5

at least once.

---

### Post by Eriksmits596 on 2007-09-12
Hehe no i haven't seen GRUB error 5... yet;)

---

### Post by Dragonbite on 2007-09-13
I just ran the openSuse backup utility (very easy ... I like it) and burned it onto a DVD.

What do I need (from openSuse) to restore from a backup?  Can I do a minimial openSuse installation (even without a GUI, just Yast) and restore from the backup I have on the DVD and get the GUI, settings and files working the way they did? Is there a way I can restore  on a blank partition via LiveCD without having even a minimal openSuse installation?

I am :oops: kinda new to backups and I see the restore option in Yast (should try it first to make sure it works I suppose).  

If this works this will be incredibly easy (compressed my backup is 1.2 GB) I could get a few backups on a DVD, burn them and have my parents hold it (to protect from catastrophic events like a fire or flood)!!

On a side-note, does Ubuntu have a backup utility? I haven't looked.

---

### Post by ExSuSEusr on 2007-09-13
SuSE (Novell) pays *protection* money to Microsfot :(  :(  :(

I know, I know... but hey... just sayin!!!!

---

### Post by igknighted on 2007-09-13
> **ExSuSEusr said:**
> SuSE (Novell) pays *protection* money to Microsfot :(  :(  :(

I know, I know... but hey... just sayin!!!!

wow, you know nothing about the deal.

Novell pays microsoft a small fee to license certain things it wants to distribute with SLED.  MS pays Novell a lot more for the right to distribute SLED, which it needs to do in order to avoid  anti-trust suits.  They also signed a deal not to sue each other.  Sure you can look at it as a microsoft divide and conquer, but it is just as likely that MS is concerned by Novell's patent portfolio.  It is more an aknowledgment (sp) from both sides that a patent war is bad for both of them, and an agreement to not do that and move on in a productive manner.  Absolutely nothing wrong with that.

In short, post FACTUAL information to support your "pay for protection" claim (not some blog-spam), or else go do your research before distributing FUD against one of linux's strongest corporate backers.

---

### Post by Dragonbite on 2007-09-13
> **ExSuSEusr said:**
> SuSE (Novell) pays *protection* money to Microsfot :(  :(  :(

I know, I know... but hey... just sayin!!!!Somebody came here looking for information and it was all going nicely until SOMEBODY had to try and stir things up (really, the only purpose for such a post)! Yeesh!

---

