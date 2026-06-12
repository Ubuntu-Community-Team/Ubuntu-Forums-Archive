---
title: "How can I edit a grub file?"
date: 2012-04-01
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by gosling1 on 2012-04-01
Sorry, should have typed 'grub'.

I currently have Ubuntu 12.04 LTS and another variant (not completely certain which) and, due to the sequence of installation the default boot is the one that isn't Ubuntu. 

I'd like to remove the second one so that Ubuntu boots when I turn on the computer. I think that there is a configuration file that I'll need to edit to remove references to the second variant but don't know which file and exactly how to do it.

If someone can provide information about this process, I'd be very appreciative.

Cheers,

Mike Robinson

---

### Post by howefield on 2012-04-01
Thread moved to the "*Ubuntu +1 (Precise Pangolin)*" forum.

---

### Post by lucazade on 2012-04-01
to edit the grub file:

```
sudo gedit /etc/default/grub

```
and then finalize the process with:

```
sudo update-grub
```

---

### Post by oldfred on 2012-04-01
lucazade's suggestions will let you modify grub2 boot parameters, but it sounds like you have the wrong boot loader in the MBR and want the other one.

Can you boot into the system you want to boot directly into.

#reinstall from working (not liveCD) system - first find Ubuntu drive (example is drive sda but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
sudo update-grub

But grub2 remembers which drive to reinstall to. So if you are using another system with grub2 you may want to prevent that system from reinstalling to the MBR on a major grub2 update.

#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions If you unchoose all drives it will not reinstall to the MBR and may not update fully. Or you can install to another location like a PBR which normally is not recommended.

---

### Post by ranch hand on 2012-04-01
Let me get this straight.

You have 2 installed OS's.  We will call these A and B.

You are using A to supply the the grub menu.

You want to use B to supply the screen menu.

Is this correct?

Can you boot to B?

There are no files to edit to change grub duties from one install to the other if the above is all true.

Grub from B just needs to be installed on the MBR of your HDD to do this.

If you can boot to B this is easy.  Run;
```

sudo update-grub

```
This will make sure that all OS's are included in the screen menu.
```

sudo grub-install /dev/sdx

```
where x is the drive your bios looks at to boot from.  If you have a single drive system this would be sda.

If you can't boot to B then you will have to boot to the live CD and follow the directions here;
[https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2)

---

### Post by gosling1 on 2012-04-01
> **ranch hand said:**
> Let me get this straight.

You have 2 installed OS's.  We will call these A and B.

You are using A to supply the the grub menu.

You want to use B to supply the screen menu.

Is this correct?

Can you boot to B?

There are no files to edit to change grub duties from one install to the other if the above is all true.

Grub from B just needs to be installed on the MBR of your HDD to do this.

If you can boot to B this is easy.  Run;
```

sudo update-grub

```This will make sure that all OS's are included in the screen menu.
```

sudo grub-install /dev/sdx

```where x is the drive your bios looks at to boot from.  If you have a single drive system this would be sda.

If you can't boot to B then you will have to boot to the live CD and follow the directions here;
[https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2)

OK, I have two OS installed. Kubuntu and Ubuntu both installed from .iso disks. When system boots, there is a text screen shown, (I think that it's the grub?) which lists several options. The first one and the one which will boot into is Kubuntu. The alternative is Ubuntu. There are a bunch of other options like memory check and the like but the screen only is visible for 10 seconds or so.

I can boot into either of these but would prefer for the system to boot into Ubuntu instead of Kubuntu.

That's my quest, to revise the program that performs the loading.

Hope this is clear and I thank everyone for assisting with this.

Cheers,

Mike Robinson

---

### Post by xebian on 2012-04-01
> **gosling1 said:**
> OK, I have two OS installed. Kubuntu and Ubuntu both installed from .iso disks. When system boots, there is a text screen shown, (I think that it's the grub?) which lists several options. The first one and the one which will boot into is Kubuntu. The alternative is Ubuntu. There are a bunch of other options like memory check and the like but the screen only is visible for 10 seconds or so.

I can boot into either of these but would prefer for the system to boot into Ubuntu instead of Kubuntu.

That's my quest, to revise the program that performs the loading.

Hope this is clear and I thank everyone for assisting with this.

Cheers,

Mike Robinson

There are 2 ways to do this.  One is to edit the file /etc/default/grub and change the GRUB_DEFAULT=0  <--- 0 is the first on the menu, 1 is the second..,etc.

The other one is to boot to your preferred OS, then

on a terminal

sudo update-grub
sudo grub-install  /dev/sda

---

### Post by gosling1 on 2012-04-02
Thanks to all. Now I boot right into Ubuntu without having to worry about selecting from the grub menu.

What a great place!

Cheers,

Mike Robinson

---

