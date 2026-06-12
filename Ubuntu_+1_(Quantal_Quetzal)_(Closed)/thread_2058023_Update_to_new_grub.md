---
title: "Update to new grub"
date: 2012-09-14
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Chelidze on 2012-09-14
I upgraded to ubuntu 12.10 to see what does the new internet connectivity brings
 so now i started update and it wants to update grub and i am at a loss what do i select here can any one help me :)

[http://i.imgur.com/zZDgd.png](http://i.imgur.com/zZDgd.png)

no netter what i select it tells me 

[http://i.imgur.com/QOYFV.png](http://i.imgur.com/QOYFV.png)

---

### Post by cariboo on 2012-09-14
You didn't mark where you wanted grub installed, highlighting the choice, doesn't mark it. You have to press the space bar to do so.

---

### Post by Chelidze on 2012-09-14
> **cariboo907 said:**
> You didn't mark where you wanted grub installed, highlighting the choice, doesn't mark it. You have to press the space bar to do so.

aha sorry for posting a question like this ,,space" button and i was pressing enter 

I think they should have cleared this for me to use space button 

I do not think any windows user will use space button


eh !!!
as expected it did not boot grub can not be found or something

---

### Post by cariboo on 2012-09-14
Using the space bar for marking a selection in a text based menu has been a standard since before Windows 3.0.

I suggest you check what drive is the boot drive in your BIOS, then boot from the Live CD, and chroot the / partition and run:

```
grub-install /dev/sd[x]
```

where /dev/sd[x] is your boot drive, then run:

```
update-grub
```

To chroot the / partition use the following commands:

[LIST=1]
[*]sudo mount /dev/sd[x] /mnt
[*]sudo mount -o bind /dev /mnt/dev
[*]sudo mount -o bind /sys /mnt/sys
[*]sudo mount -o bind /proc /mnt/proc
[*]sudo chroot /mnt
[/LIST]

In this case /dev/sd[x] = where your / partion is located eg: /dev/sda1

I'm sure the others will come up with other ways to do the chroot. :)

---

### Post by Chelidze on 2012-09-14
> **cariboo907 said:**
> Using the space bar for marking a selection in a text based menu has been a standard since before Windows 3.0.

I suggest you check what drive is the boot drive in your BIOS, then boot from the Live CD, and chroot the / partition and run:

```
grub-install /dev/sd[x]
```

where /dev/sd[x] is your boot drive, then run:

```
update-grub
```

To chroot the / partition use the following commands:

[LIST=1]
[*]sudo mount /dev/sd[x] /mnt
[*]sudo mount -o bind /dev /mnt/dev
[*]sudo mount -o bind /sys /mnt/sys
[*]sudo mount -o bind /proc /mnt/proc
[*]sudo chroot /mnt
[/LIST]

In this case /dev/sd[x] = where your / partion is located eg: /dev/sda1

I'm sure the others will come up with other ways to do the chroot. :)


 I do not know if i did the right thing which i doubt but i tryed to fix this issue before you posted and i addressed this issue with [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) app
yes the os are booting now but grub is so messed up , i see duplicates and should i just delete them ??

on windows my boot partition was 200 mb system partition did ubuntu used the same partition ??

---

### Post by cariboo on 2012-09-14
> **Chelidze said:**
> I do not know if i did the right thing which i doubt but i tryed to fix this issue before you posted and i addressed this issue with [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) app
yes the os are booting now but grub is so messed up , i see duplicates and should i just delete them ??

on windows my boot partition was 200 mb system partition did ubuntu used the same partition ??

Grub gets installed on the MBR of usually the first hard drive, it doesn't touch your Windows partitions.

It sounds like you are using the previous version of Grub, as I've seen a couple of comments where it gets {i]messed[/i] up after installing the latest grub version. 

I haven't seen a fix yet though.

---

### Post by Chelidze on 2012-09-15
> **cariboo907 said:**
> Grub gets installed on the MBR of usually the first hard drive, it doesn't touch your Windows partitions.

It sounds like you are using the previous version of Grub, as I've seen a couple of comments where it gets {i]messed[/i] up after installing the latest grub version. 

I haven't seen a fix yet though.

thank you for the information

---

### Post by YannBuntu on 2012-09-17
> **Chelidze said:**
> I do not know if i did the right thing which i doubt but i tryed to fix this issue before you posted and i addressed this issue with [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) app
yes the os are booting now but grub is so messed up , i see duplicates and should i just delete them ??

on windows my boot partition was 200 mb system partition did ubuntu used the same partition ??

Please indicate the URL provided by Boot-Repair. THis will give us the answers.

---

### Post by dino99 on 2012-09-17
@yann
[http://ubuntuforums.org/showthread.php?t=2058884](http://ubuntuforums.org/showthread.php?t=2058884)

mine is: paste.ubuntu.com/1202088

---

### Post by YannBuntu on 2012-09-17
( **@dino99:** next time please send me a private message. The current thread is Chelidze's one. )

---

### Post by Chelidze on 2012-09-22
> **YannBuntu said:**
> ( **@dino99:** next time please send me a private message. The current thread is Chelidze's one. )

I am sorry that i have not replayed to this thread I did not knew that some one posted in it 

 I think this grub menu is too messed up to change, so will just ignore it till ubuntu 12.10 release then i am going to do a clean install 

 any way thank you for helping me :)

---

