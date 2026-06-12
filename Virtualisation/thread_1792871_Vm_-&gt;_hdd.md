---
title: "Vm -&gt; hdd"
date: 2011-06-28
forum: Virtualisation
---

### Post by amr3 on 2011-06-28
Hi there,
I am having on a processor i7 Intel, 4Gb RAM and XP 64 bit as OS, runing a VM VMDK file.


After reading some posts found I could help improving the fact was too, way too slow by adjusting from 2 to 1 processor.

It did. It improved a bit.
it seems.


Though the reason I am raising this thread is to ask if there is a way of converting this VMDK file into an **ISO **o **GSH **in order for me to take the OS is running in it -WServer 2003...- *outside* the VM.

This VM has a database so there are **3 partitions **on it. 1 with the OS, 2nd with database and a 3rd one.

Any help is more than welcome :)

alex

---

### Post by ClientAlive on 2011-06-29
> **amr3 said:**
> Hi there,
I am having on a processor i7 Intel, 4Gb RAM and XP 64 bit as OS, runing a VM VMDK file.


After reading some posts found I could help improving the fact was too, way too slow by adjusting from 2 to 1 processor.

It did. It improved a bit.
it seems.


Though the reason I am raising this thread is to ask if there is a way of converting this VMDK file into an **ISO **o **GSH **in order for me to take the OS is running in it -WServer 2003...- *outside* the VM.

This VM has a database so there are **3 partitions **on it. 1 with the OS, 2nd with database and a 3rd one.

Any help is more than welcome :)

alex


I'm not sure I understand what you want to do but here are a couple ideas.

You can clone the vm itself so you have a duplicate vm. I've used cloneVDI with success and love it.

[http://forums.virtualbox.org/viewtopic.php?f=6&t=22422&hilit=clonevdi](http://forums.virtualbox.org/viewtopic.php?f=6&t=22422&hilit=clonevdi)

It's a small link at the bottom of post #1


I think you can just run some kind of cloneing software or backup tool in the virtual machine itself to make a copy of the os that's inside the vm. I've used clonezilla with linux before but I think it works with Windows software too.

[http://clonezilla.org/downloads.php](http://clonezilla.org/downloads.php)

If you want to use clonzilla inside the vm: First you go into settings (for that vm) > System - and make sure everything in the "boot from" field is unchecked except "CD/DVD ROM". Then you put the clonezilla live cd you burned into the drive and start the vm. The vm will then boot clonezilla inside it and you can use it to copy/ clone the os that's inside.

The only problem with this is I"m not sure if Virtual Box modifies anything about the os when it's installed in it. If not, you should be ok.

You can tell clonezilla where to save the image file (best not to store it on the same drive as the thing it's cloning - put it on an external). When you want to restore it somewhere else you just run clonezilla live on what you want to restore it on and have it restore the image from where you saved it.

Hope that helps. Let us know if you have other questions or if this is not it.
--------------------------

Linux has something called

```

dd

```

dd is an old program that, I think, came from IBM or something. It might be on Windows too. For Linux it's something that's already standard in the os and it makes a raw iso image and can do it of the entire drive. If it is in WServer 2003 then it could be used to make an iso by running it in the os in the vm - I think. This might be difficult though. Just thought I'd mention it because I used that before too and it did great for me.
----------------------

Edit:

Sorry, guess it's only in Unix/ Linux

[http://en.wikipedia.org/wiki/Dd_(Unix](http://en.wikipedia.org/wiki/Dd_(Unix)) Just found that out.

If you ever do use dd though be really really careful. If you make a mistake how you run the command it can wipe you out.

---

### Post by amr3 on 2011-06-29
> **ClientAlive said:**
> I'm not sure I understand what you want to do but here are a couple ideas.

You can clone the vm itself so you have a duplicate vm. I've used cloneVDI with success and love it.

[http://forums.virtualbox.org/viewtopic.php?f=6&t=22422&hilit=clonevdi](http://forums.virtualbox.org/viewtopic.php?f=6&t=22422&hilit=clonevdi)

It's a small link at the bottom of post #1


I think you can just run some kind of cloneing software or backup tool in the virtual machine itself to make a copy of the os that's inside the vm. I've used clonezilla with linux before but I think it works with Windows software too.

[http://clonezilla.org/downloads.php](http://clonezilla.org/downloads.php)

If you want to use clonzilla inside the vm: First you go into settings (for that vm) > System - and make sure everything in the "boot from" field is unchecked except "CD/DVD ROM". Then you put the clonezilla live cd you burned into the drive and start the vm. The vm will then boot clonezilla inside it and you can use it to copy/ clone the os that's inside.

The only problem with this is I"m not sure if Virtual Box modifies anything about the os when it's installed in it. If not, you should be ok.

You can tell clonezilla where to save the image file (best not to store it on the same drive as the thing it's cloning - put it on an external). When you want to restore it somewhere else you just run clonezilla live on what you want to restore it on and have it restore the image from where you saved it.

Hope that helps. Let us know if you have other questions or if this is not it.
--------------------------

Linux has something called

```

dd

```dd is an old program that, I think, came from IBM or something. It might be on Windows too. For Linux it's something that's already standard in the os and it makes a raw iso image and can do it of the entire drive. If it is in WServer 2003 then it could be used to make an iso by running it in the os in the vm - I think. This might be difficult though. Just thought I'd mention it because I used that before too and it did great for me.
----------------------

Edit:

Sorry, guess it's only in Unix/ Linux

[http://en.wikipedia.org/wiki/Dd_(Unix]("http://en.wikipedia.org/wiki/Dd_%28Unix")) Just found that out.

If you ever do use dd though be really really careful. If you make a mistake how you run the command it can wipe you out.


Thank you ClientAlive for your suggestion.
Sorry, might not have been too precise.
What i am trying to achieve here is what you refer in point 2.

"Extract" the OS and its partitions are in VM Ware so that i can "burn" it into a HDD and just ran it form there.

And yes, I believe creating an image of the whole OS is within the VM Ware would be the solution.
I wonder though If would give me any issues as inside the VM file there are a couple of partitions.

Anyway. Would keep you posted on my attempt this weekend to create a cloned image form within the VM Ware file.

thks,

Alex

---

### Post by ClientAlive on 2011-06-30
> **amr3 said:**
> Thank you ClientAlive for your suggestion.
Sorry, might not have been too precise.
What i am trying to achieve here is what you refer in point 2.

"Extract" the OS and its partitions are in VM Ware so that i can "burn" it into a HDD and just ran it form there.

And yes, I believe creating an image of the whole OS is within the VM Ware would be the solution.
I wonder though If would give me any issues as inside the VM file there are a couple of partitions.

Anyway. Would keep you posted on my attempt this weekend to create a cloned image form within the VM Ware file.

thks,

Alex



II don't know if the partition structure is copied over in an iso image or not. I don't think dd creates a partition table when copying but I could be wrong. I'm sure it depend on what tool you use to make the copy. Clonezilla is a pretty nifty little tool. It will not only clone but restore as well. I'm pretty new to the whole 'cloning/ imaging' thing - it's just what came to mind when I read your initial post.

When I p2v'd my o/s into virtual box is when I discovered that clonezilla can be run and used inside a vm. In my case I didn't get the result I was after but it wasn't because of clonezilla. It was a configuration issue that stemmed from on oversight on my part. Ultimately I used dd and this app I found in combination with one another.

Anyhoo . . .

As far as the idea of imaging os though - some virtualization software actually makes changes to the kernel of the o/s when you install it in the vm. Xen does this. I'm not sure if VMware does it or not. Point being though; that, if it has made changes, those changes will come along with the image. An attempt to install that image as a regular install may be problematic because of it. It's something I would try to look into.

---

