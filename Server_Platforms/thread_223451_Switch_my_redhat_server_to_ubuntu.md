---
title: "Switch my redhat server to ubuntu?"
date: 2006-07-26
forum: Server Platforms
---

### Post by chadk on 2006-07-26
I have a dedicated server that I'm renting.  Would it be possible to install ubuntu on that server without actually being AT that server?  Can it be done over the network?  I have root access to the server but no physical access to the server.

---

### Post by cilynx on 2006-07-26
I would say that whether or not it is --possible-- is academic.  Whether or not it's a good idea is a better question.

How I would do it:
Start with a box with similar arch to your server.
Cut the hard drive 60/40.
Install Ubuntu on the 40% partition.
Boot the Ubuntu Live CD on the same system.
Make a tarball of the new Ubuntu system and save it on the 60% partition.
(Don't forget the options to maintain ownership and permissions)
scp the tarball to the remote server.
Connect to your remote server.
Use (g?)parted to make a new partition at least big enough to hold the full new Ubuntu install.
Format the new partition ext3
Untar the tarball to the ext3 partition
Update your menu.lst or lilo.conf or whatever to boot the new partition.
Pray.
Pray more.
Consider if I can afford to drive to wherever my remote server is at.
Pray.
Reboot.
Drive to wherever my remote server is and fix what I messed up.

Best of luck to you, but I wouldn't recommend it.

---

### Post by BakCompat on 2006-07-26
haha.

Pray.
Pray more.


I like that.

Yeah, i have a RH9 box that keeps getting s'kiddies in and would really like to migrate it over to Ubuntu 6.06 without having to export the massive amounts of customizations it has required. But, i don't think it will happen easily. The safer way is to move the necesary info piecemeal, but its a drawn out process. I'd love a standardized "upgrade any old linux box to <distro> cd" but there are just so many combinations out there in the FOSS world and so many iterations to choose from, i think i am better off doing a clean install of Ubuntu on a clean box and doing the slow migration. My data will like me better for it down the road.

---

### Post by mannheim on 2006-07-26
> **chadk said:**
>  Would it be possible to install ubuntu on that server without actually being AT that server? 

Would VMWare Server be a solution? You could install a virtual machine running Ubuntu, under the RH9 linux host. I think that VMware Server would allow the virtual ubuntu machine to serve to the internet.

You could then reconfigure ssh on the RH9 machine to listen on an alternative port, and have the Ubuntu virtual machine listen for ssh on port 22, and serve the web on port 80 and so on. Soon, you could forget that the original RH9 was there at all.

If you don't need every ounce of performance from the hardware, it might work.

---

### Post by chadk on 2006-07-27
:) Thanks guys... didn't think so. lol

---

