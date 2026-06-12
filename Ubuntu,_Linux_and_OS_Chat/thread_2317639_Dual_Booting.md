---
title: "Dual Booting"
date: 2016-03-18
forum: Ubuntu, Linux and OS Chat
---

### Post by Dixie_Lou on 2016-03-18
Is there a writ here for Dual Booting anywhere?   Is Dual Booting considered Visualization? Is Dual Booting TABOO here?

---

### Post by v3.xx on 2016-03-18
We have Wiki's on the subject, guess you should ask your questions.

---

### Post by v3.xx on 2016-03-18
What do you wish to dual boot?

---

### Post by Dixie_Lou on 2016-03-18
I was just looking for a specific Thread on Dual Booting, the subject seems to be scattered all over the place.
I just graduated the ten year school of HARD KNOCKS on Dual Booting.
Toward the end, I googled things like,,,,, Is Dual Booting Reliable?

---

### Post by Dixie_Lou on 2016-03-18
Is Dual Booting reliable, compared to say VM Box? I hear a lot of people don&#8217;t like Dual Booting.
I am Dual Booting Windows 7 Ultimate along side Ubuntu 14.04 LTS.                         
 I just want it to work
I got a lot of useful info here, so I figured "Give back", so I am here.

---

### Post by v3.xx on 2016-03-18
>  I hear a lot of people don&#8217;t like Dual Booting.
I have not heard this.

I find dual boot reliable, been doing it since 2008.  I also find VirtualBox reliable; nice to have two systems running at the same time.  I do both.

A place to start is the link below.  "D" for dual boot and "V" for virtual.

---

### Post by howefield on 2016-03-18
Thread moved to the "*Ubuntu, Linux and OS Chat*" forum.

Welcome to the forums Dixie_Lou,

Hard to see if this is a discussion thread or a support thread so moved here, if you have specific questions regarding dual booting, please feel free to post them, probably *General Help*  or the * Installation & Upgrades* forums would be best, Virtualisation which is running various operating systems suimultaneously is some else altogether.

---

### Post by kansasnoob on 2016-03-18
> **Dixie_Lou said:**
> Is there a writ here for Dual Booting anywhere?   Is Dual Booting considered Visualization? Is Dual Booting TABOO here?

Dual booting is not the same as using a VM. It's hardly taboo since Ubuntu's main download link points to this installation guide:

[http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

You can see it's a simple dual-boot with Win 7 :D

I have bare metal booting as many as 16 Ubuntu OS's for various testing purposes. There is a learning curve to dual/multi-booting just as there is to anything. The use of UEFI BIOS and GPT partition tables both made multi-booting easier since there is no longer a 4 primary partition limit, but also harder because configuring /boot/efi can be tricky.

If you plan on dual-booting you should ask a more direct question like "How would I go about dual-booting with *whatever OS*".

A knowledgeable response would be to ask you to post the output of some commands using a live Ubuntu DVD/USB, beginning with "sudo parted -l", or in more complex circumstances requesting a boot info summary.

There used to be a lot of guides for dual-booting but few have been updated to account for grub 2 and UEFI booting.

---

### Post by grahammechanical on 2016-03-18
What we have not provided are things like these:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)

Regards.

---

### Post by mikodo on 2016-03-19
> **grahammechanical said:**
>  - snippet - [http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)

Thanks. I hadn't seen this.

---

### Post by pfeiffep on 2016-03-19
> **Dixie_Lou said:**
> Is there a writ here for Dual Booting anywhere?   Is Dual Booting considered Visualization? Is Dual Booting TABOO here?Certainly dual / multiple booting is not taboo. Many folks employ dual / multiple booting. There are at least 2 options for dual booting:[INDENT]1 - a single hard drive with more than one operating system - [GRUB]("https://www.gnu.org/software/grub/") will enable you to choose which OS to boot
2 - multiple hard drives each with at least one OS
[/INDENT]

In my case I have Windows 7 installed on a SSD and choose to boot this by engaging the startup boot option - depressing the escape key during power up (I chose not to install grub on my SSD.
 I have a second internal HDD with 2 different Ubuntu versions installed; grub enables me to choose (I have bios set to default boot the HDD where grub is installed).

The primary disadvantage of dual boot is one must "reboot" to engage another OS. This disadvantage is overcome by installing a virtualization program such VirtualBox (there's no free lunch as this might be a bit slower)

---

