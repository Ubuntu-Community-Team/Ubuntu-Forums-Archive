---
title: "4Hours to kill"
date: 2016-04-08
forum: The Cafe
---

### Post by izznogooood on 2016-04-08
So, its Friday after work. Had my first beer, tssssst ahhhh... Thinking i would prepare my desktop for installing some other OS's for testing purposes. This would involve shrinking my 500GB win partition to 200gb (I never use it anyway....) Had a USB stick with Ubuntu Daily build lying a round, Ill use that i said...
Boot the development system, enter Gparted... Make my shrinking choices... 
Then I notice a 512mb free space at the very beginning of my 2TB media/backup drive thinking, hmmm thats odd... Oh, well lets expand my EXT4 partition to the left, completely unnecessary. Mostly to satisfy my OCD i think...
Push Check, here we go...

[ATTACH=CONFIG]268244[/ATTACH]

So, tonight there will be no movies with plexconnect, no testing new OS's, No nothing.... Im stuck in this Environment for the next 4Hours!

Cheers :D

---

### Post by Bucky Ball on 2016-04-08
Well, it's nearly 2Tb and it looks like it's moving the whole lot to the left rather than expanding the partition. It's growing from 1.8 to 1.8. :-k

Got a good book? You can always cancel the process by hitting the big button.

---

### Post by izznogooood on 2016-04-08
Yep, god knows why it did that. Anyway, I'm not going to chance it, it will run its course...

---

### Post by grahammechanical on 2016-04-08
That is why I apply one action at a time. I do not queue them up. In case I want to call off the action for some reason. I have never had a move/size break an OS on the drive but there is always that anxiety that it might.

It is always the case that whenever I am doing something that cannot be interrupted my wife will want me to find some web site or play some song.

---

### Post by oldfred on 2016-04-08
Moving left always is a copy and if a lot of data slow.
And space on drive may have been for a future ESP - efi system partition or something similar. 
I really do not like moving left. Expanding right usually is very quick.

And do not move NTFS partitions. They have essential boot info & partition info in the partition, so moving often requires major repairs. Use only Windows tools to resize NTFS. But do not use Windows for anything else. Use gparted.

---

### Post by izznogooood on 2016-04-09
The process went fine, but it took 8 hours :(. And I belive it was and old EFI from when I used that disk for ubuntu 15.10....

> **oldfred said:**
> And do not move NTFS partitions.........

I did not know that thanks....

---

### Post by gameboy9309 on 2016-04-29
4 hours.... Wow.

---

### Post by yetimon_64 on 2016-04-30
> **gameboy9309 said:**
> 4 hours.... Wow.

That's nothing, try cloning a 2 TB HDD to an external dock (a usb2 device) from a live dvd boot; 4 full DAYS later before it finished ... ](*,). I was terrified of a power outage or surge the whole time taking out the external docks power, but it finally completed; it was lovely to get back to a normal boot and off the live one. I have since upgraded to a usb3 external dock which can do the same job in about 7 to 8 hours :P.

Edit: just realized that I am on a live boot right now shredding that very drive (clearing it out for a total linux only rebuild). The shred command has been running about 4 hours now and is only at the 65% mark. Only one pass of zeros though; big drives sure chew up the time for such tasks :-). That 4 day back up of the Windows set up, mentioned above, was done many months ago.

---

