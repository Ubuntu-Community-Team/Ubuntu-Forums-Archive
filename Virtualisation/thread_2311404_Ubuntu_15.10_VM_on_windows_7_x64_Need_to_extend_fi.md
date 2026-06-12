---
title: "Ubuntu 15.10 VM on windows 7 x64: Need to extend filesystem partition"
date: 2016-01-26
forum: Virtualisation
---

### Post by PancakeMaster on 2016-01-26
Hi, 
So I've read some posts about this online but I'm not really confident enough in my abilities to pull the trigger on anything I've read. 


Heres the problem: I installed ubuntu on virtualbox to a fixed 16gb partition. After dealing with some other issues I had with the installation, I by accident essentially discover that I have, like, 1gb free on the filesystem partition, which for some reason has only decided to use 8gb of the 16 I gave it. 


So, first question, why in the world is an essentially brand new Ubuntu installation using of order 8gb? 

Second, why is this installation not using the full 16gb allotted it? 

Third question, how can I get it to use the full 16gb? Or otherwise extend the filesystem partition? 


Looking at the ubuntu disk utility...thing... This is how the partitions are divided up: 


- Partition 1: Filesystem, 8.6gb Ext4
- Parition 2: Extended partition, 8.6gb 
- Partition 5: Swap, 8.6gb swap 


I don't really know how to interpret these partitions and I don't really know how to fix my problem without breaking anything. 

Tomorrow I can post pictures from gpart, or anything else you guys need. 


Please help, thanks.

---

### Post by Andy_Syrewicze on 2016-01-26
So, when you setup the VM in virtualbox did you actually choose the 16GB size, or was it the default?

I'm guessing you allowed the ubuntu installer to define the partition table for you? At any rate it looks like the swap partition automatically created consumed half of the overall 16GB virtual disk. Leaving you with roughly 8GB left. That should answer questions 1 and 2. 

If you come from the Microsoft world, think of the swap partition as kind of like a Windows Page File.

As for the third, you'll have to grow the volume, which is detailed [HERE]("http://askubuntu.com/questions/101715/resizing-virtual-drive"), or shrink your swap partition by using a tool like gparted to first shrink the swap partition and then have the root partition consume what you take away from the swap partition. 

Hope this helps!

__
A

---

### Post by MAFoElffen on 2016-01-27
<implied by the last post> 
And ... With the GParted LiveCD iso mounted in the virtual CD drive of that Virtual machine, boot the VM from that iso and do what you need to do with that VM's virtual disks.

At least, that is the easiest way I can think of, with the least amount of work.

---

### Post by PancakeMaster on 2016-01-27
Here's an issue. In the blog answer you sent me, they are extending the filesystem into unallocated space. I.e., gparted looks like this:  [http://1.bp.blogspot.com/_ev_jc-1kX-w/TUYqqiNy2-I/AAAAAAAAHfI/2YU019BwVsA/s1600/gparted.png](http://1.bp.blogspot.com/_ev_jc-1kX-w/TUYqqiNy2-I/AAAAAAAAHfI/2YU019BwVsA/s1600/gparted.png)

Whereas in my case, gparted looks like this: [http://imgur.com/o21lBZB](http://imgur.com/o21lBZB)


See, it's not unallocated space. How do I deal with this?

---

### Post by PancakeMaster on 2016-01-27
Welp, trying what the blog said broke the machine. Now it won't boot.

---

### Post by Andy_Syrewicze on 2016-01-27
Well that's no good...   :(

I take it by followed the blog, you chose the route in which you increase the virtualbox disk size?

Did you do any resizing with gparted?

if so, were the directions followed completely? Also, now that it won't boot, does it throw error messages? Boot Loop? Need more info.

---

### Post by PancakeMaster on 2016-01-27
Not really. It just kinda...wouldn't start. I ended up just reinstalling the VM entirely. The original problem I had, and why I was reluctant to reinstall the VM, was because I couldn't get 3d acceleration to work. I fixed that, so the better option was just remaking the VM. 

Also, it turns out the reason I had such a large swap space was because ubuntu matches the swap partition with the amount of RAM I give it. I don't know why it does this, but it allowed me to give make the FS partition larger (by supplying the VM with less RAM).

---

### Post by monkeybrain20122 on 2016-01-27
> **PancakeMaster said:**
> Here's an issue. In the blog answer you sent me, they are extending the filesystem into unallocated space. I.e., gparted looks like this:  [http://1.bp.blogspot.com/_ev_jc-1kX-w/TUYqqiNy2-I/AAAAAAAAHfI/2YU019BwVsA/s1600/gparted.png](http://1.bp.blogspot.com/_ev_jc-1kX-w/TUYqqiNy2-I/AAAAAAAAHfI/2YU019BwVsA/s1600/gparted.png)

Whereas in my case, gparted looks like this: [http://imgur.com/o21lBZB](http://imgur.com/o21lBZB)


See, it's not unallocated space. How do I deal with this?
  
In your case you don't really need to use the  "VBoxManage modifyhd .. --resize" command on the .vdi to create new empty space. If I were you I will just use gparted to delete the whole extended partion and swap inside and then extend /dev/sda1 to take the 8G. It makes no sense to have swap as big as your actual system and not sure what the extended partition is for. You don't need a swap partition in VM since you will never suspend or hibernate with the VM. Just allocate it more ram in VB's Settings (If you run the VBoxManage command there will be additional space after /dev/sda2. You can then delete the extended partition with swap inside and then extend extend sda1 to cover the whole space.)


Well to figure out why it won't boot you have to tell us exactly what you did in order. Conceptually it is very simple. The VBoxManage modifyhd command is like putting your system in a bigger hd, then use gparted to fill up the new space.

BTW resizing will not work if you created your original virtual drive with fixed size (instead of dynamic) in that case you have to clone it first and then resize the resulting dynamic virtual drive. Or. See second post [here ]("https://forums.virtualbox.org/viewtopic.php?f=35&t=50661")
But you probably don't need to clone first if you just use gparted to delete the extended + swap and just expand sda1 into this existing spacewith gparted.

---

### Post by MAFoElffen on 2016-01-28
No!!!! Argh!!! (LOL. Sorry for the explatives, but...)
> 
Quoted from last poster:
[COLOR=#000000] If I were you I will just use gparted to delete the whole extended partition and swap inside and then extend /dev/sda1 to take the 8G.[/COLOR]

The swap filesystem uuid is in the fstab of the installed system. If you delete it > extend the root volume > then add new swap... Then the newly created swap ha a different UUID, therefore on boot is not found. (you would have to update the fstab with the the UUID) Or if as he said, leave it deleted, same thing, it tries to mount it from fstab, but not found. (again would need to edit the fstab.)

*** But if you shrink the swap partition to the right (leaving free unllocated space before it) > Then you can extend the root partition to the right. On a desktop Linux System, you only need 1.5 times the allocated RAM. @ 1.5 GB, that would give you 6.5 GB back.

If you need more, then you could migrate always to a larger VM disk image...

---

### Post by monkeybrain20122 on 2016-01-28
> **MAFoElffen said:**
> No!!!! Argh!!! (LOL. Sorry for the explatives, but...)

The swap filesystem uuid is in the fstab of the installed system. If you delete it > extend the root volume > then add new swap... Then the newly created swap ha a different UUID, therefore on boot is not found. (you would have to update the fstab with the the UUID) Or if as he said, leave it deleted, same thing, it tries to mount it from fstab, but not found. (again would need to edit the fstab.)
.

It may flash an error message for a second or two but it will boot. You can fix fstab after you boot if you care, it will boot slightly faster if you fix it, but otherwise no difference. If you mess with uuid of /home (if you have a separate /home) then it won't boot but swap is fine. I have deleted and created swap many, many times on real hds instead of VM. I move my install around hd and the uuid of swap keeps changing since I can't clone it. There must be about 3 or 4 uuid's for swap in my fstab with all but one commented out. I have never had a problem booting,

> *** But if you shrink the swap partition to the right (leaving free  unllocated space before it) > Then you can extend the root partition  to the right. On a desktop Linux System, you only need 1.5 times the  allocated RAM. @ 1.5 GB, that would give you 6.5 GB back.


He doesn't need any swap. In most modern machines (at least 4 G of ram common place) you don't need swap unless you hibernate/suspend. Since this is a VM this need doesn't arise. If he wants to give the VM more ram he can just adjust it in Vbox's settings (assuming that of course the host has at least 4 G of ram to run VM smoothly

---

