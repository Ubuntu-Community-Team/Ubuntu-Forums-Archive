---
title: "Need help to properly partition HD before install 12.04 LTS"
date: 2013-10-10
forum: Server Platforms
---

### Post by JohnyBeGood on 2013-10-10
[FONT=arial][SIZE=3]Hi all,

I have a dedicated server with 1TB HD and when I used hosts interface to install Ubuntu Desktop [COLOR=#262626]12.04 LTS 64bit I over looked default config and [/COLOR][COLOR=#262626]my [/COLOR][COLOR=#ff0000]**/**[/COLOR][COLOR=#262626] portion only got 20GB after using it for while in /var/www I've noticed I was running out of space.

Here's how default install template looks like [http://i.imgur.com/mGi4td2.jpg](http://i.imgur.com/mGi4td2.jpg)[/COLOR]
Now I would like to use pretty much all of HD for **[COLOR=#ff0000]/[/COLOR]** and this is how I would partition it [http://i.imgur.com/hiYupzu.jpg](http://i.imgur.com/hiYupzu.jpg)

My question is my way o.k.? or there's a reason why [COLOR=#ff0000]**/**[/COLOR] needs only 20GB?
I would like to do it right now instead to find later on if something installed in ie. /var/lib needs more space but I have it in say /home.

TIA

[/SIZE][/FONT]

---

### Post by oldfred on 2013-10-10
Moving to server sub-forum.

---

### Post by JohnyBeGood on 2013-10-11
Anyone?

---

### Post by nerdtron on 2013-10-11
I say, shrink your /home partition and use that space to mount as /var directory. You will need to enter single user mode when you do this.
On single user mode, transfer the content of the whole /var directory to another location, then mount the newly created partition as /var. Now transfer everything back to the /var directory.
Be sure to check out for the permissions and the fstab entry for the new partition.

---

### Post by joelgsf on 2013-10-12
I would suggest you to read this post [https://help.ubuntu.com/community/UEFI]("https://help.ubuntu.com/community/UEFI").
I have recently made a similar installation, on a 500 GB disk. My partition scheme was
> 
/boot -------- 1 GB
/ ------------ 16 GB
/var -------- 10 GB
/usr -------- 10 GB
/home - ~450 GB 
/swap ------- 4 GB

It is running nicely, with plenty of space available in all partitions, despite lots of apps already installed. I always define first 'swap' at the end of the disk, then all system partitions at the beginning of the disk, and what is left I asign to 'home'.

---

