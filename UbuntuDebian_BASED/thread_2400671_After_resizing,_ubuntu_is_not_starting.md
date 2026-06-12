---
title: "After resizing, ubuntu is not starting"
date: 2018-09-08
forum: Ubuntu/Debian BASED
---

### Post by caneraydinbey on 2018-09-08
I had 8 gb swap. THen i increased it to 16 gb on live usb ubuntu.


It did not give any warning while i was doing. Because i used the space from end of the root, not from the beginning.


But after that, ubuntu is not starting. It stays at ubuntu logo.


I went again to live usb and tried a lot of things.  One example is that
[https://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/](https://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/)


    sudo grub-install --boot-directory=/mnt/ubuntu/boot /dev/sdX


i was trying to write this.


it says


> warning: File system `ext2' doesn't support embedding. 
warning: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their  use is discouraged.. 
error: will not proceed with blocklists.


i dont know what to do.


also i tried this:


[https://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](https://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd)




    grub-install error can not open directory . boot/grub/i386-pc no such file or directory




also trried this


[https://askubuntu.com/a/229453/542960](https://askubuntu.com/a/229453/542960)


for this part


    sudo chroot /mnt
    Install grub:
    
    grub-install --boot-directory=/boot/ --recheck /dev/sda


i get this:


grub-install error can not find efi directory


what happened to my system ? i have only ubuntu, not dual

---

### Post by jdeiros on 2018-09-08
Hello,

I am having trouble following this from what I read, correct me  if I am wrong:
 
You already had a working PC w/ 8gb swap NOT running  off a live USB, and you wanted to increase your PCs swap to 16gb? And to do this,  you used a live ubuntu USB, resized swap? Then BLAM, random information about boot issues and grub-install, which I have absolutely no idea how to decipher because I  have no idea what you did between plugging in the live usb and then finding yourself using grub-install.

You could have honestly changed all your swap information locally without the use of a live usb.

[https://askubuntu.com/questions/178712/how-to-increase-swap-space](https://askubuntu.com/questions/178712/how-to-increase-swap-space)

---

### Post by caneraydinbey on 2018-09-08
Hello.

I had 8 gb yes. BUt hibernation was not working. So, i read about it and i decided to increase my swap.

It completed without error. But now i cant login to my ubuntu.

I could not change my swap because there was no free area so i should have decreased the size of linux.

It is ubuntu 16.04

i tried lots of things but still cant login.

---

### Post by jdeiros on 2018-09-08
Do you have any idea what you did when you resized the swap? You still haven&#8217;t told us how you went about doing that.

What completed without error ?

---

### Post by caneraydinbey on 2018-09-08
> **jdeiros said:**
> Do you have any idea what you did when you resized the swap? You still haven’t told us how you went about doing that.

What completed without error ?


I went to live usb. Opened gparted.

Clicked swap and "swapoff"

Then deleted.

THen for dev sda2 (my ubuntu is there), i resized. from 230 to 222 gb. I chose from the end so even it did not show a warning after i  click "apply all operations". I meant this. It did not say "it can cause an error if you resize main partition."

then created a new swap.

partion name linux-swap
file system linux swap

and restarted after apply all operations.

And i chose "ubuntu".

But it stays at ubuntu logo. dots are changing.

I dont know how i broke the grub or another thing.

---

### Post by ajgreeny on 2018-09-08
As you deleted your original swap then created another you will need to edit /etc/fstab to point to that new swap, if not a delay will occur in the boot sequence as the old missing swap is searched for.  I would expect it to either eventually boot or perhaps show an error about a missing partition and ask you to press "S" to skip that partition's mount.

Using the live system please show us the fstab of your installed system and also the output of ```
sudo blkid -c /dev/null
``` which will show all the UUIDs of the current partitions.
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by caneraydinbey on 2018-09-08
> **ajgreeny said:**
> As you deleted your original swap then created another you will need to edit /etc/fstab to point to that new swap, if not a delay will occur in the boot sequence as the old missing swap is searched for.  I would expect it to either eventually boot or perhaps show an error about a missing partition and ask you to press "S" to skip that partition's mount.

Using the live system please show us the fstab of your installed system and also the output of ```
sudo blkid -c /dev/null
``` which will show all the UUIDs of the current partitions.
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**


```
sudo blkid -c /dev/null
``` 

for that, i am attaching picture. Because it is different computer.

[ATTACH=CONFIG]281019[/ATTACH]




edit: i noticed that i did not add flag after creating swap. So now i added esp and boot flag to linux swap then restarted but still cant login.

---

### Post by caneraydinbey on 2018-09-09
This is boot info

[http://paste.ubuntu.com/p/kdt3NFdhgh/](http://paste.ubuntu.com/p/kdt3NFdhgh/)


after i use boot-repair, it became this


[http://paste.ubuntu.com/p/2n5K7K8xCK/](http://paste.ubuntu.com/p/2n5K7K8xCK/)

---

### Post by caneraydinbey on 2018-09-09
[COLOR=#242729][FONT=Arial]I am on upstart mode. When i write ",top" it shows 8 gb as swap. I increased swap to 11 gb . When i go to live usb, i see 11 gb swap file. Why is that?[/FONT][/COLOR][COLOR=#242729][FONT=Arial] &#8211; [/FONT][/COLOR]

---

### Post by caneraydinbey on 2018-09-09
Now again did something and restarted. Black screen after i choose ubuntu on boot. And after 1-2 minutes, i can login. How can i be sure it will work forever if i restart?

---

