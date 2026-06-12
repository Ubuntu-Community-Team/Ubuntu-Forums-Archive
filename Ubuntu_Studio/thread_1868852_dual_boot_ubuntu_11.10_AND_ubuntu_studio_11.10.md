---
title: "dual boot ubuntu 11.10 AND ubuntu studio 11.10"
date: 2011-10-24
forum: Ubuntu Studio
---

### Post by xianbei on 2011-10-24
Hello!

I know there are alternate / more efficient ways to do a DAW and PC workstation, but I'd like to proceed with the U/US dual boot, as I'm not sure my computer will be entirely stable with US.

Here's what I'd like to do:

1- keep my current configuration primary. I have Ubuntu 11.10 running well with a Vista dual boot (sucks, but at least I can watch Netflix). I want the standard install of Ubuntu 11.10 to be my primary Ubuntu, i.e. i want it to update and carry the boot loader.

I don't want to hose my U11.10 install, as I have it running swimmingly for work / VPN right now.

2- install Ubuntu Studio 11.10 on a separate partition called uStudio that I have already set up with gParted.

**It may be a n00b question, but I feel like I'm not the only one out there that would like this setup; could somebody provide a step by step to create this setup?

Thanks!

---

### Post by jejeman on 2011-10-25
Just install UbuntuStudio to the partition you have made for it. Make shure that you choose that one, and set it as "/" mountpoint.
You can use existing swap partition. Set it as swap.
Last thing you need to do is to NOT install grub, because you want Ubuntu to be the boot boss.

---

### Post by xianbei on 2011-10-25
Thanks jejeman; I'll give that a shot and post the results.

---

### Post by xianbei on 2011-10-30
Everything went swimmingly, with one minor exception:

all i had to do was run ```
sudo update-grub
```

and all is well with Ubuntu Studio.

Thanks for the help!

---

### Post by jejeman on 2011-10-31
Yes, that was expected that you needed to mannualy update grub.

---

### Post by taylorhagstrom on 2011-11-02
> **xianbei said:**
> Everything went swimmingly, with one minor exception:

all i had to do was run ```
sudo update-grub
```

and all is well with Ubuntu Studio.

Thanks for the help!

grub-customizer makes the process painless also.

---

### Post by bumbomaquides on 2012-07-30
If the mounting point for the ubuntu studio partition is "/" (root), then what's the mounting point for the ubuntu primary partition? 

Since it is not possible to mount different partitions in the same mounting point.

I'm trying to install ubuntu AND ubuntu studio (no windows in this computer), and still can't figure it out, considering the different kernel they use.

My intent is:

Primary partition (sda1), ext4: Ubuntu 12.04, mounting point??
Logical partition (sda5), ext4: Ubuntu Studio 12.04, mounting point??
Logical partition (sda6), ext4: My files, mounting point /home
Logical partition (sda7): swap.

I understand from posts in this thread that after the installation, I have to manually use the terminal in the ubuntu to run: sudo update-grub

And after that it will have to work.

So the only problem for me is knowing the mounting points.

---

### Post by jejeman on 2012-07-30
For both mounting point is / when it is system partition.
When you install Ubuntu sda1 is /, sda5 has no mount point. You don't really need to use this partition while in ubuntu.
When you install ubuntuStudio sda5 is /, sda1 has no mount point.

I don't know if it is wise to share home folder.

Well I guess you may need to update grub, but I doubt, because the last instalation would update grub. Unless you skip installation of grub.

---

### Post by bumbomaquides on 2012-07-30
Thank you!

I had to update the grub (sudo update-grub), and finally i chose not to share the home folder.

So now I have:

ubuntu partition (primary, mounting point "/")
ubuntu's home partition (logical, mounting point "/home")
swap partition (i hope both ubuntus share this) logical.
ubuntu studio partition  (logical, mounting point "/")
ubuntu studio's home partition  (logical, mounting point "/home")

looks like it's working!

thanks for your help!

---

### Post by mozgren on 2012-10-02
> **jejeman said:**
> Just install UbuntuStudio to the partition you have made for it. Make shure that you choose that one, and set it as "/" mountpoint.
You can use existing swap partition. Set it as swap.
Last thing you need to do is to NOT install grub, because you want Ubuntu to be the boot boss.

Excuse the noob question but... How does one avoid installing/overwriting grub?

---

### Post by jejeman on 2012-10-02
I just took a look at the installer, and actually you can't choose not to install grub.
This used to be an option.

---

### Post by Sylos on 2012-10-03
There should be an option when you go through the install process to NOT install GRUB (cant remember where - I normally just allow it to and then do my GRUBBING from whatever OS has it).

Cheers

EDIT: I stand corrected as above by Jejeman. That seems like a backwards step.

---

