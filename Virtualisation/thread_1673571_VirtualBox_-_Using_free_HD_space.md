---
title: "VirtualBox - Using free HD space"
date: 2011-01-22
forum: Virtualisation
---

### Post by The Nutcrackin' Squirrel on 2011-01-22
Well yeah, it's me again. I just installed VirtualBox and wanted to use the 68GB, which I were using for Windows, as Boot Hard Disk. So I formated the partition with NTFS, but I still can't choose it when setting up a new Virtual OS. Is it even possible to use another partition for the VM?

---

### Post by migs73 on 2011-01-22
When I go through the set up procedure, I get the 'Create New Virtual Disk' which ask where I want the virtual disk and what size I want it.

If I click on the folder to the right of the text box, I can pick my other partition from this page. (see below)

Are you getting this far? Or are you not being allowed to put it on the partition?

I don't want to go any further on my machine as I don't want to overwrite the data in my partition (I was just giving it a go to see if I could help).

Mike

---

### Post by The Nutcrackin' Squirrel on 2011-01-22
Well, I come this far, but I can click on "Save" until I'm dead, nothing happens. :o

---

### Post by nick_goodfate on 2011-01-22
> **The Nutcrackin' Squirrel said:**
> Well, I come this far, but I can click on "Save" until I'm dead, nothing happens. :o

you have to type a name for that virtual hd at the top...

and i think vb uses just a .vdi file like virtual hd, it can't use a partition of your actual hd...

---

### Post by migs73 on 2011-01-22
You don't have a **file** in the partition!

The virtual HD is a **file**, so you will need to create one, and use that as the HD. If you select 'dynamically expanding' then it will grow and fill the partition as required.

Hope this solves your issues!!!

Mike

^^^^^^^EDIT and name it as Nick says!! In fact if you do that I think it creates a file anyway!

---

### Post by The Nutcrackin' Squirrel on 2011-01-22
Alright, I feel pretty stupid now. Thanks. :p

---

### Post by migs73 on 2011-01-22
No need to feel stupid, I like your idea of having a partition for the VM, I might try that in future. That is what got me looking at the thread.

To ask is but a moments shame, not to ask, and to remain ignorant, is a lifelong shame.
Chinese Proverb.(supposedly!)

---

### Post by nick_goodfate on 2011-01-22
if you want to use an entire partition for an other os, maybe you should try to install it at your real machine and not use a virtual machine by the way...

---

### Post by howefield on 2011-01-22
Thread moved to the Virtualisation forum.

---

### Post by migs73 on 2011-01-22
Then I can't run both at the same time!!!!!

---

### Post by nick_goodfate on 2011-01-22
> **migs73 said:**
> Then I can't run both at the same time!!!!!

:lol: you're right. So Nutcrackin' Squirrel if you want to run them both at the same time go for vb!

---

### Post by The Nutcrackin' Squirrel on 2011-01-22
I was using the partition for Windows before, but it's just a pain to restart every time I want to play a game for 20 minutes or something. 

So It created a .vdi file on the partition now. That means that it doesn't take any space from my Ubuntu partition, right?

---

### Post by migs73 on 2011-01-22
Yup, that should be it!!

Let us know if you hit any problems, as I said I might give this a go in a while (once I'm finished with 10.04, which is on my other partition).

---

### Post by The Nutcrackin' Squirrel on 2011-01-22
A question regarding the RAM size. If I give the VM 3GB is it reserved or does it share with the other OS?

---

### Post by howefield on 2011-01-22
> **The Nutcrackin' Squirrel said:**
> A question regarding the RAM size. If I give the VM 3GB is it reserved or does it share with the other OS?

Your total RAM needs to cover host plus any running VMs.

---

### Post by The Nutcrackin' Squirrel on 2011-01-22
Sorry, I don't really understand your answer. :o

In other words, is it a problem if I give the VM 3/4 of my RAM?

---

### Post by migs73 on 2011-01-22
> **The Nutcrackin' Squirrel said:**
> Sorry, I don't really understand your answer. :o

In other words, is it a problem if I give the VM 3/4 of my RAM?

Assuming the 3GB was 3/4 then it should be OK as Ubuntu (I am assuming it is your host OS) should run fine with the remaining 1GB.

In other words the two OS's don't share the RAM dynamically but use what is allocated by you.

---

### Post by The Nutcrackin' Squirrel on 2011-01-22
Alright, that's what I wanted to know. Man, that's the most helpful internet community I've ever seen, another big plus for Ubuntu. Thank you guys. ;)

E: I assume it's just using the 3GB while the VM is running, right? Silly question, but you never no.

---

### Post by howefield on 2011-01-22
> **The Nutcrackin' Squirrel said:**
> Sorry, I don't really understand your answer.

Sorry, I mean if you have eg, 4 gig of physical RAM in your machine and give the guest operating system 3 gigs, that will leave the host with 1 gig.

VirtualBox will let you do this, but give you a warning after you devote more than 50% of your RAM to the guest, you can ignore this if you like.

---

### Post by howefield on 2011-01-22
> **The Nutcrackin' Squirrel said:**
> I assume it's just using the 3GB while the VM is running,

Correct ;-)

---

### Post by JKyleOKC on 2011-01-22
Just in case you don't know, you will have to install Windows on that VM the first time you run it, just as you would with an actual machine. Once that is done, be sure to install the "Guest Additions" by using the Devices menu from vbox's frame around the VM screen. This will let you use "seamless mode" which gives you both systems at the same time on the same screen. I usually don't go to seamless mode, though; I prefer having the vbox frame around its window so that I have its menu choices that let me power the VM down or reset it when Windows decides to freeze...

---

### Post by Timmer1240 on 2011-01-22
on another note if the vdi was in another partition ntfs could you run it from there in virtualbox installed in linux partition?

---

### Post by howefield on 2011-01-22
> **Timmer1240 said:**
> on another note if the vdi was in another partition ntfs could you run it from there in virtualbox installed in linux partition?

Yes, you could run it from another partition, as long as the host system can see it.

Best for performance is putting the .vdi on another disk altogether.

---

### Post by Timmer1240 on 2011-01-22
Yes you can I just tred it sweet might be able to make some more room on my Ubuntu partition that way sweet!

---

### Post by The Nutcrackin' Squirrel on 2011-01-22
It works pretty well, except for the speed. Guess I'll buy two 4GB RAM bars to make it work properly.

---

### Post by Timmer1240 on 2011-01-22
I got 50 gigs of windows7 sitting unused might have to do a mint debian install over that never boot it up anymore anyhow right!

---

### Post by JKyleOKC on 2011-01-22
> **The Nutcrackin' Squirrel said:**
> It works pretty well, except for the speed. Guess I'll buy two 4GB RAM bars to make it work properly.Yes, you need plenty of RAM for virtualization to look good. It also helps if your processor is at least dual-core, since that leaves one core free to run the VM while the other runs the host. Still, RAM is the most critical part of the equation...

---

