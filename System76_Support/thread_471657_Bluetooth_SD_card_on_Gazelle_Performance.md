---
title: "Bluetooth SD card on Gazelle Performance"
date: 2007-06-12
forum: System76 Support
---

### Post by cward002 on 2007-06-12
Hi everybody.

I did a very silly thing last night, although I di not know it was silly at the time. I inserted a Bluetooth SD card that I had for my old computer into my Gazelle Performance and I rebooted to see if it would allow me to have bluetooth. Well, the computer didn't like the card!!! it allowed me to log in under gnome but hen everything locked up. So here is what I tried:

1) re-booted the computer normally(Gnome) with SD card inserted - same result as above
2) re-booted the computer normally (Gnome) without SD card - got a Hal Failed to load error and none of the applets on the top bar loaded. No mouse response either.
3) re-booted again and this time I had a mouse so I tried to do a system restore but no luck. The internet was obviously working, so I tried to do an update through update manager but that showed nothing to update.
3)tried to boot into a Failsafe Gnome session which was successful but there was no prompt in the terminal so I couldn't do anything there.
4)Finally I booted into Rescue Mode but I didn't know any commands to try to restore my system.

So right now I can boot in to my system but it is incredibly slow to boot. and now when I boot up I get a white square like the terminal in the top left of the screen but there is no prompt or anything. and I cant tyoe anything in the box.

I hope this is enough information.

Thanks for any suggestions

Colin

---

### Post by cward002 on 2007-06-13
bump

---

### Post by cward002 on 2007-06-13
sorry I bumped too soon

---

### Post by thomasaaron on 2007-06-13
I guess the place to start would be with your kernel log. But getting that to us might be difficult.
You could try mounting a USB drive (and hoping it auto-mounts) and then entering the following from recovery mode:
cat /var/log/messages > ~/messages.log
cp ~/messages.log /media/disk
umount /media/disk

Then you can take the USB disk to another computer and retrieve the log off of it and post it here.


But, as much as I hate to say it, it would probably take less time to restore your system than figure out how your bluetooth card hosed it. Especially considering you have no mouse, keyboard, etc...

Instructions for restoring are here:
[http://knowledge76.com/index.php/Restoring_Your_System](http://knowledge76.com/index.php/Restoring_Your_System)

Do you have your important files backed up?

---

### Post by cward002 on 2007-06-13
Hi Thomasaaron

thanks for the reply. I don't really have any crucial files on this computer yet, but I do a nightly back up anyway so I should be  OK. I will try these instructions and let you know.

Thanks again

Colin

---

### Post by cward002 on 2007-06-13
Hi Thomasaaron.

I just looked at the instructions and they look like exactly what I need. I knew I could restore my system with a Ubuntu CD but I wasn't sure how to get the system76 stuff re-installed. I knew it would probably be a repository but I didn't know the link

Thanks a lot

I will let you know how it goes after I try this tonight.

Colin

---

### Post by cward002 on 2007-06-14
Hey Thomasaaron.

well I am back up and running!!! 

I followed the directions in the link you gave me and it worked fine. The only sticky bit was remebering to disable desktop effects so that I could get a working terminal so I culd fix the Desktop Effects!!! But it's all good now. The only thing now is that boot-up is much slower but I think that is a problem for a lot of people and not specifically related to this issue. I am going to do some research.


Thanks again Thomasaaron

Colin

---

### Post by thomasaaron on 2007-06-14
Colin,

First:
OK, I give! Why are there no Scottish bullfighters?

Second:
For your slow booting, let's check something out.
Go to a terminal and type: sudo gedit /etc/network/interfaces  (and hit enter...)

The only lines in that file that should NOT have a comment (#) beside them are:

auto lo
iface lo inet loopback

If this is not the case, put comments in front of all other lines and see if you boot faster.

Best,
Tom

---

### Post by cward002 on 2007-06-14
Hi Tom.

That is exactly what I am going to do when I get home tonight. 

I will let you know how it goes.

Secondly, I will give you a hint: red Kilts!!!!ROFL

---

### Post by cward002 on 2007-06-14
Sorry I posted the answers out of order!!!!! LOL

---

### Post by thomasaaron on 2007-06-14
> Secondly, I will give you a hint: red Kilts!!!!ROFL

:lolflag:

---

### Post by cward002 on 2007-06-14
well I tried your suggestion on the internet connection but I lost all internet connectivity!! I ran PPPOECONF and got my wired connection back.

however it added a bunch of stuff to my interfaces file(attached)

---

### Post by cward002 on 2007-06-14
sorry my first attempt at attaching my interfaces file didn't work. Here it is

---

