---
title: "How dangerous is to resize?"
date: 2005-07-04
forum: The Cafe
---

### Post by sonny on 2005-07-04
Hey... I got an other HD (a lap-top hd but I've got the adaptor), and I was wondering how dangerous is to resize a linux filesystem?, cus I've got my /home and my / on 2 different partitions but same HD. I want to move the / partition to the laptop HD, but i want to use the extra space for my /home, so I need to resize my /home partition to take the free space. But i've heard that resizing isn't so secure, any comments? should i resize or give some other use to the HD?

---

### Post by aysiu on 2005-07-04
Honestly, I'm not quite sure what you're trying to with your set-up. The answer I give is the same as I would give for NTFS or FAT32--it's *generally* safe, but you should *always* back up your files. What program are you using for resizing?

---

### Post by sonny on 2005-07-04
Well I was going to use qtparted with the live cd... do you recommend something else? by the way, I'm not gonna resize any fat nor ntfs partition, it's my / partition. I don't like having my / and my /home in the same partition; if i mess the OS i can re-intall without losing anything. So I will install the OS on the lap-top HD, and then mount my other HD as my home directory. but I don't want to waste 30 gb of space.

---

### Post by aysiu on 2005-07-05
Let me make sure I've got this straight.
So, you're copying your /home to the mounted hard drive. Your laptop's hard drive will be / only? So, you're going to delete the /home directory and resize (as in make larger) the / partition to take up the whole hard drive? Should be fine. Resizing is far more dangerous when you're reducing the partition size (as opposed to enlarging). Nevertheless, you should always back up your data.

---

### Post by sonny on 2005-07-05
well.. not quite but yes... I'm moving the / to the 40 gb laptop HD, and use my 200GB for my /home, right now I have a 30gb partition for my / so I'm going to resize my /home to make it bigger, I don't want to back-up cuz I've got 87 gb of stuff... so unless there's at least a 90% chance my data won't be deleted I'll resized.. if not then I've to use it for something else... what do you think about this?

---

### Post by aysiu on 2005-07-05
well.. not quite but yes... I'm moving the / to the 40 gb laptop HD, and use my 200GB for my /home, right now I have a 30gb partition for my / so I'm going to resize my /home to make it bigger, I don't want to back-up cuz I've got 87 gb of stuff... so unless there's at least a 90% chance my data won't be deleted I'll resized.. if not then I've to use it for something else... what do you think about this?

Once again, let me make sure I've got this straight. So, you have it currently set up like this now, right?

40 GB Laptop:
30 GB /
10 GB /home

200 GB Hard Drive:
200 GB nothing

Have I got that right?

And you want it to end up looking like this, right?

40 GB Laptop:
40 GB /

200 GB Hard drive:
200 GB /home

Am I getting this right? It's kind of hard for me to figure out what you want from your description. I'm also a bit confused about your files. You say you have 87 GB of files to back up, but your laptop is only 40 GB? Where is the 87 right now?

My inclination would be just to keep your current configuration as is (/ and /home on your laptop) and just automount the 200 GB hard drive on load and put all your files there. Nothing says you have to have your files in your /home directory. You can have them wherever you want.

My guess is that I'm probably still not fully understanding 1. what your current configuration is and 2. what you eventually want it to look like. Can others chime in? Maybe there's something I'm not seeing.

---

### Post by sonny on 2005-07-05
well this is a case of missinterpretation, my current setup is 

200GB (not quite cuz of the byte transformation)

/ 30gb
/home 169gb
swap 1gb

40 gb Lap-top (empty)

and I want

/ 40gb (laptop)
/home 199gb
swap 1 gb

---

### Post by aysiu on 2005-07-05
Well, if you have 87 GB of files, you might as well back up the most important 40 GB of it, right? That way, in case it doesn't work, you'll have lost only half your stuff. Do you have any friends with iPods or extra hard drives who can lend some backup space to you just so you can do this? Data is always important, and you don't want to lose that should anything go wrong.

I'll tell you, I've resized my partitions many a time in the last few months (at least eight times), and I've never run into a problem. Nevertheless, even if there's only a .01% chance something could go wrong, it would *really* suck for you to lose 47 GB of data.

Otherwise, just go for it.

---

### Post by notos on 2005-07-05
well i havent resized (im on it) any time my partitions but as i know there are two posible Easy Options

1.- Do it with Knoppix / Ubuntu-Live (Gparted/Qparter)

2.- With LVM i heared it its prety stable and you can do it online (no-restart mode :P)
but dont ask me i am on the level of reading manuals and forums-posts :P

---

### Post by sonny on 2005-07-05
Ok... so I'll better ask for some space on a friend's HD.... any way... it should go fine this weekend. Thanks for the posts.

---

