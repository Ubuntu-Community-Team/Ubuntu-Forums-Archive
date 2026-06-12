---
title: "Store bought computer"
date: 2006-11-25
forum: The Cafe
---

### Post by Kristy on 2006-11-25
Im in the market for a new computer.  The one I have is slow and quite outdated.  I always said I would build another one, but you know the nicely packaged bundles walmart has  .... well, they are very tempting.  

So onto my question.  Can you take a store bought computer and format all the crap that comes with it off.  In other words, can I take my WinXP cd and format over the multitude of software that comes with the computer, then install ubuntu (dual boot).  Instead of having to mess with their "recovery disk" ](*,)  everytime I want to re-do something.  I would just like to be able to pick and choose what I install and not use their "recovery disk".

I hope I put this in the right section .. if not please move.

Thanks:D

---

### Post by kdawg on 2006-11-25
You don't need to use the windows disk, just use the ubuntu alternate install disk and wipe the drives when you install from that.  When it comes to partitioning, there is a selection that will erase the entire drive and do a default partition scheme and install.  One thing you want to look for however is if there are hidden partitions on the drive.  My Acer laptop had one.  Basically, the machine had a 30gb drive but 10gb was a hidden recovery partition where a certain key combination at boot would recover windoze from that partition.  It was a waste of space so I used fdisk to get rid of it.  So just check and make sure you are getting the full amount of space!

---

### Post by aysiu on 2006-11-25
Yes, you can resize the Windows partition and install Ubuntu on the other newly created partition. Ubuntu's boot loader will automatically add Windows to the boot menu, and you can choose which one you want to boot into at startup.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by kdawg on 2006-11-25
Oops sorry, just realized you wanted to do a dual boot.  In that case, you need to install windoze first in most cases so it will play nicely with linux.  The problem is that most machines prebuilt come with a OEM copy that is vender specific, like dell machines come with dell versions of windows that have all that crap on it.  So I guess you would need to buy from a place that will give you a straight up windows disk!  Sorry for the long winded response, hope this helps and I'm not confusing at all!

---

### Post by po0f on 2006-11-25
Kristy,

Be very careful to **not** wipe out the backup (usually hidden to Windows) partition that OEMs usually use to restore Windows from if you ever have to reinstall Windows.

---

### Post by Kristy on 2006-11-25
Ok.
 .... seeing that juicy 19" widescreen and brand new box for 699 tonight made me think of buying a store bought.

So its a compaq ..  I once had a HP and it had a recovery disk.  Everytime I had to reinstall something (due to my goofing up) I had to use that damn disk and redo everything.  With my computer now, I have my copy of xp ( as well as 98 ) and my ubuntu disk.  

Now hypothetically speaking .. I get this computer.  I put in my xp cd and reboot ... install xp.  then get that configured, and later install ubuntu.

That is what I want to do.  I want to be able to reinstall windows or anything else I want, without having to use that recovery disk.

Is this possible?  

Sorry for the long post.  This is the one thing that has kept me from buying store bought since my first computer.

---

### Post by Kristy on 2006-11-25
> **po0f said:**
> Kristy,

Be very careful to **not** wipe out the backup (usually hidden to Windows) partition that OEMs usually use to restore Windows from if you ever have to reinstall Windows.


Should I be worried about this if I dont plan on ever using the restore/recovery disk?  And if I do restore/reinstall/repair windows I will be using my own disk.

---

### Post by 3rdalbum on 2006-11-25
It is possible. Very possible.

But you'd have to find out what hardware is in your computer, then search the web and manually install drivers for all of it.

---

### Post by mips on 2006-11-25
> **Kristy said:**
> Ok.
 .... seeing that juicy 19" widescreen and brand new box for 699 tonight made me think of buying a store bought.

So its a compaq ..  I once had a HP and it had a recovery disk.  Everytime I had to reinstall something (due to my goofing up) I had to use that damn disk and redo everything.  With my computer now, I have my copy of xp ( as well as 98 ) and my ubuntu disk.  

Now hypothetically speaking .. I get this computer.  I put in my xp cd and reboot ... install xp.  then get that configured, and later install ubuntu.

That is what I want to do.  I want to be able to reinstall windows or anything else I want, without having to use that recovery disk.

Is this possible?


Yes, it is possible.

Go to the compaq/hp website and download the software drivers for that PC onto a memory stick/cd.

Insert the Ubuntu cd and wipe the hard drive, repartition the drive as you would like it, apply the changes. Do NOT install Ubuntu at htis stage.

Reboot with the Windows CD and install windows on the first partition you created. Next install all your drivers you downloaded. install any additional stuff like Office, antivirus, firewall.

Once you are done pop in the Ubuntu Cd an simply install it to the other partitions you created.

Look at the link provided by Aysiu.

---

### Post by gumbald on 2006-11-25
All I'll say is be careful... I had to spend 30 mins on the phone to Acer before I was eventually told that I couldn't install a retail/volume copy of Windows (working in a school). Somebody else had already wiped the hard drive, but luckily we had more than one of the PCs so I could clone the entire hard drive back. Else it would have had to go back to Acer.

---

### Post by Gargamella on 2006-11-25
> **mips said:**
> Yes, it is possible.

**Go to the compaq/hp website and download the software drivers for that PC** onto a memory stick/cd.

Insert the Ubuntu cd and wipe the hard drive, repartition the drive as you would like it, apply the changes. Do NOT install Ubuntu at htis stage.

Reboot with the Windows CD and install windows on the first partition you created. Next install all your drivers you downloaded. install any additional stuff like Office, antivirus, firewall.

Once you are done pop in the Ubuntu Cd an simply install it to the other partitions you created.

Look at the link provided by Aysiu.

Also Lenovo/IBM website has a great drivers section.

---

### Post by mips on 2006-11-25
> **Gargamella said:**
> Also Lenovo/IBM website has a great drivers section.

Thats won't help him, he's buying a Compaq(HP) PC. unless i misunderstand you.

---

### Post by Kristy on 2006-11-25
Thanks for all yalls help.  I havent bought the computer YET.  I just wanted to see if what I wanted to do was possible.

I just hate the idea of not being able to just pop in the windows disk when I mess up something (and that does happen from time to time) .  

Here is another question.  Say it has a 160gig HD, and you partition it with 3 sections.  Using the restore/recovery disk, when you pop it in, does it automatically ONLY copy to C: .  My other partitions wont be touched ... will they?
Im just full of questions.  I dont know anything about store bought computers.  I had one ... and it ended up being a throw away.

:)

---

### Post by mips on 2006-11-25
> **Kristy said:**
> 
Here is another question.  Say it has a 160gig HD, and you partition it with 3 sections.  Using the restore/recovery disk, when you pop it in, does it automatically ONLY copy to C: .  My other partitions wont be touched ... will they?


Usually the ENTIRE drive gets wiped but it might differ between vendors. All i know is that if you use a restore cd you might as well kiss your entire HD goodbye.

What you could do is simply image the existing windows partition, this will allow you to restore the image at a later stage without affecting other partitions. You have to resize the existing partition before you image it though, this depends on the imaging software to a large degree.

---

### Post by Spano on 2006-11-25
Maybe your best bet is to buy a new computer and add a second hard drive for your Ubuntu install.  Storage is cheap and two drives will make your dual boot easier and more flexible.

---

### Post by ZylGadis on 2006-11-25
Here is another thought: if you don't want to use the Windows that comes preinstalled on the computer, **you should be able to get a refund for it**. Google for additional information, but essentially people have managed to get as much as $200 back [B]in the case they do not accept the EULA they are presented with when they first boot[B].
To do that, usually you'd have to go to small claims court and sue the manufacturer of your machine. A much easier option is to buy the machine with a credit card, then tell your cc company that so-and-so of that price is due a refund and you want to dispute it (they will temporarily give you the so-and-so back). Your cc company will ask you for an explanation letter, which you can write and send back (i.e. I am due a refund if I don't accept the EULA, and I did not accept it, etc). Then just sit back and leave your cc company to battle the machine manufacturer for the actual refund. The manufacturer cannot decline the refund (it can threaten you, etc, but as long as you know your rights you are fine), and cannot state the exact costs of the software installed because of the non-disclosure agreement it has with MS, so you should be able to get the retail price of Windows, as that is your only reference point (and the court would agree).
Of course, people who do this generally don't want Windows at all, but that should work in case you want to install a copy of Windows that you obtained by other means, too. The important thing is not to accept the EULA at first boot.

---

### Post by aysiu on 2006-11-25
You don't need to sue the manufacturer. You just need to document things correctly and ask nicely.

More details here:
[User refund for no Windows option](http://news.bbc.co.uk/2/hi/technology/6144782.stm)

There are also a number of retailers who sell Linux preloaded or with no operating system installed. The most talked-about one on these forums is [System 76](http://system76.com/index.php/cPath/2_52?osCsid=7d181d61890d9ebf5de4b8b1e750ec2b), but you can find a complete list of these vendors [here](http://lxer.com/module/forums/t/23168/).

---

### Post by ZylGadis on 2006-11-25
Of course, I'm assuming the manufacturer will decline at first, or at least will try to inundate you with legal mumbo-jumbo and essentially confuse you so much that you accept much less than what you should. I don't think asking nicely will do :) That is always the first step, of course, but it won't work - so I've outlined the next steps.

Edit: Scratch the first edit. It is always good to check one's numbers before writing.

---

### Post by wdo_will on 2006-11-25
> **gumbald said:**
> All I'll say is be careful... I had to spend 30 mins on the phone to Acer before I was eventually told that I couldn't install a retail/volume copy of Windows (working in a school). Somebody else had already wiped the hard drive, but luckily we had more than one of the PCs so I could clone the entire hard drive back. Else it would have had to go back to Acer.

I won't be buying a PC from them anytime soon, then...:rolleyes:
They're worse than Micro$oft!

---

### Post by teet on 2006-11-25
> **Kristy said:**
> Im in the market for a new computer.  The one I have is slow and quite outdated.  I always said I would build another one, but you know the nicely packaged bundles walmart has  .... well, they are very tempting.  

So onto my question.  Can you take a store bought computer and format all the crap that comes with it off.  In other words, can I take my WinXP cd and format over the multitude of software that comes with the computer, then install ubuntu (dual boot).  Instead of having to mess with their "recovery disk" ](*,)  everytime I want to re-do something.  I would just like to be able to pick and choose what I install and not use their "recovery disk".

I hope I put this in the right section .. if not please move.

Thanks:D

As others have mentioned, if you don't use the install disks/partition that came with your machine, you will run into a few problems with windows activation (i.e. it won't activate without calling microsoft).

As long as you have a legit windows key and a legit Windows XP cd you should be okay.  I've done it before several times.  I didn't want to use the recovery disks that came with my laptop b/c they install so much extra crap so I borrowed an OEM copy of XP Home w/SP2 to reinstall.  It, of course, wouldn't activate after I got it installed so I called up microsoft.  Some guy named "Bob" with a thick accent asked me a few questions.  A couple of them were:

Have you ever reinstalled windows before?

How many computers do you currently have this copy of windows installed on?

Where did you buy your computer?

Then he went ahead and activated it for me.  

-teet

---

