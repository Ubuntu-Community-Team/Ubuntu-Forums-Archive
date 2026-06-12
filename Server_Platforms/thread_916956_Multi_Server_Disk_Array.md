---
title: "Multi Server Disk Array?"
date: 2008-09-11
forum: Server Platforms
---

### Post by jamesb73 on 2008-09-11
Hi

Can anyone tell me if this is possible...

I have an Ubuntu 8.04 Server running mdadm and 6 x 1TB disks in a RAID-5 config.

At some point I am going to run out of space on the array and the motherboard will only support 6 disks on the main controller (the other has two ports but those are taken up by a system drive and a DVD-ROM).

The motherboard is a Gigabyte IP35-DS3R.

What i'd like to do is be able to either:

1) Add more drives to this machine but in an external case with own PSU/Coolers etc but need some way of getting cabline from case 1 to case 2.

2) Build another machine and somehow network the filesystems together so that they all appear as one mega large volume.

I'm doing this to encode all my DVD library (some 1000 disks) to online storage so I can watch anything back on demand on any of my media player devices around the house.

Is any of this possible?  I'd prefer not to have two machines with independent filesystems.

I've read some posts on iSCSI but i'm not sure this is the best way.  Is it possible to add an iSCSI device (eg /dev/md0 on remote pc) into the /dev/md0 array on the controller pc?

All help or pointers greatly received.

Thanks
James

---

### Post by windependence on 2008-09-11
For this kind of a task you should really start using server class hardware. You can buy cases that will handle more than 6 drives but you may also want to think about something like IcyDock to save space. Really what you are trying to do is build your own SAN, and SCSI would be better suited to that because you could just use an external RAID cabinet. I have a 12 drive unit sitting in my rack right now, but putting 300gig drives in it would require a re-mortgage. :)

If you want to use SATA, there are plenty of options available, but you will soon be limited by the number of drives your controller can manage. You might be able to get around that by using multiple controllers in one big LVM group but I'm not sure how performance would be.

-Tim

---

### Post by PilotJLR on 2008-09-11
I agree with Tim - this project really needs different hardware.

It is possible to take an additional machine, export a block device out via iSCSI, then just a "master" machine to make one big LVM logical volume with those block devices.

But now you're looking at complexity, LOTS of points of failure...  basically, you're just asking for an eventual data loss!

Direct-attached storage, like an eSATA enclosure, would be safer, but still a big possible point of failure.

---

### Post by trmentry on 2008-09-11
> **jamesb73 said:**
> Hi

Can anyone tell me if this is possible...

I have an Ubuntu 8.04 Server running mdadm and 6 x 1TB disks in a RAID-5 config.

At some point I am going to run out of space on the array and the motherboard will only support 6 disks on the main controller (the other has two ports but those are taken up by a system drive and a DVD-ROM).

The motherboard is a Gigabyte IP35-DS3R.

What i'd like to do is be able to either:

1) Add more drives to this machine but in an external case with own PSU/Coolers etc but need some way of getting cabline from case 1 to case 2.

2) Build another machine and somehow network the filesystems together so that they all appear as one mega large volume.

I'm doing this to encode all my DVD library (some 1000 disks) to online storage so I can watch anything back on demand on any of my media player devices around the house.

Is any of this possible?  I'd prefer not to have two machines with independent filesystems.

I've read some posts on iSCSI but i'm not sure this is the best way.  Is it possible to add an iSCSI device (eg /dev/md0 on remote pc) into the /dev/md0 array on the controller pc?

All help or pointers greatly received.

Thanks
James


You kinda sound like my first server. :)  

I used this:  [http://www.cooldrives.com/multilane-adapter-kit.html](http://www.cooldrives.com/multilane-adapter-kit.html)

To get sata controller ports out of the box to an external case.  I just used 4 port promise cards.  I had 2 of them in my computer to get 8 drives externally.

The case I used was.  [http://www.censuspc.com/product.php?productid=644&cat=71&page=1](http://www.censuspc.com/product.php?productid=644&cat=71&page=1)


Anyway... what I did was leave my drives that internal to the server (your 6 1tb drives) as 1 array.  then the i took the drives in the external box as the 2nd array.  I left it like this as if I had a psu fail, then 1 array would go down.  Not x# of drives in an array and it go south then.


Currently my setup is using 1 large case with 3x2 sata backplane cages (3 drives to 2 5.25 bays).  So I have 19 drives in my case.  15 in the front, 4 internal.  

I'm using [http://www.supermicro.com/products/accessories/addon/AoC-SAT2-MV8.cfm](http://www.supermicro.com/products/accessories/addon/AoC-SAT2-MV8.cfm)  controllers.... but they are pci-x but work in normal pci.  I just haven't had the money to get a good mobo that supports mci-x yet.  Working on that for next one. :)  I do see a performance hit but it's not bad as I just server files to my lan with it.

---

### Post by jamesb73 on 2008-09-12
Thank you all for your advice on this.

Yes, I was trying to build a SATA SAN for my home and so that I could gain the experience to properly advise my clients (i'd rather my home kit fail than their office kit).  I work with a lot of small to medium enterprises that don't have vast cash resources for these things but still need a good solution.

I toyed with the idea of building a seperate machine with the same config and just store other data on it but I know i'm going to get the question of building a very large single partition.

I'm not too keen on putting all the drives in one case for cooling reasons and load on a single PSU.

So, I like the idea of extra controllers, an external cabinet and multi-lane cables between them.  For my purposes, I would need to find a cabinet that was rack mountable.

I understand that if I build an external cabinet with its own power supply and that fails then X disks will disappear from the array simultaneously which would definitely be a problem.

So the ideal solution there would be to have a cabinet with a redundant PSU right?

So the question I have now which i'm sure is easy is how simple is it to add an extra controller and add the disks to my existing array.

The 6 current disks are on an ICH9R chipset in AHCI mode and appear to ubuntu as sda through sdf in /dev

The array was built with mdadm, starting with 3 disks and then I did an add and grow to add the other 3 as I wanted to know how to do that right from the start.

So, if I put in a promise card will the drives appear as sdg, sdh etc which I can then add or will I need to do something else to do this.  

Also, does the controller hardware affect the physical data mapping on the drive, in other words, if a controller fails or I want to upscale, do I have to use a promise card or can I replace later with, say, a 3-Ware 24 port?

Thanks in advance.
James

---

### Post by Robstarusa on 2008-09-12
Would lustre work?  It is not for the faint of heart....  How much linux experience do you have?

---

### Post by Multi-Medea on 2008-09-12
The answer to your problem is really [www.addonics.com](www.addonics.com).  What you need is:
 - An eSATA controller that supports their port multiplier (they make them for both PCI-e and PCI-X buses; if all you have is old PCI you're out of luck).
 - Their port multiplier
 - If you want to save physical space on the external enclosure, addonics also make a fit-five-drives-in-the-space-of-three nifty little box.  
 
Now, connect every five drives using short sata cables to the port multiplier, and use an eSATA cable to connect that to the eSATA controller on your motherboard.

There is additional material on the addonics site, read it!

/ji

PS: I don't have stock in addonics, I'm just a *very* satisfied customer.

---

### Post by HermanAB on 2008-09-12
...or, you can use the latest version of NFS which allows spanning virtual disks over ethernet.

---

### Post by windependence on 2008-09-13
For power supplies take a look at this one:

[IMG]http://www.istarusa.com/images/server_power/mini_redundant/tc500r8am001.jpg[/IMG]


[http://www.istarusa.com/server_power/mini_redundant/passive_pfc/](http://www.istarusa.com/server_power/mini_redundant/passive_pfc/)

These fit where a normal ATX power supply would go, and are hot swappable.

-Tim

---

### Post by jamesb73 on 2008-09-13
Thanks to everyone so far who's helped me with this.

I had a good look at the addonics site and there's a whole bunch of stuff on there that will definitely help me out.  I just need to find a UK distributor.

One of the things they have is a really cool server case with 5.25" bays mounted the other way around and I love the configuration of the 5x3.5 in 3x5.25 bay thing although hot-swappable in this particular project isn't an issue.

Plus, most of the multilane connectors to go on the external box all seem to fit a 50-way SCSI hole so getting the right case the for job.

So the only issue left to solve is how will Ubuntu see these extra drives - in other words, will mdadm care that they're on different controllers?

- James

---

### Post by fjgaude on 2008-09-13
> So the only issue left to solve is how will Ubuntu see these extra drives - in other words, will mdadm care that they're on different controllers?


Some years back I had drives on two controllers and created an array using **mdadm** without incident, all worked as expected.

I believe as long as the OS sees the drives it doesn't concern mdadm, it will create!

---

### Post by windependence on 2008-09-13
I agree, I think it will work fine.

-Tim

---

### Post by trmentry on 2008-09-13
> **Multi-Medea said:**
> The answer to your problem is really [www.addonics.com](www.addonics.com).  What you need is:
 - An eSATA controller that supports their port multiplier (they make them for both PCI-e and PCI-X buses; if all you have is old PCI you're out of luck).
 - Their port multiplier
 - If you want to save physical space on the external enclosure, addonics also make a fit-five-drives-in-the-space-of-three nifty little box.  
 
Now, connect every five drives using short sata cables to the port multiplier, and use an eSATA cable to connect that to the eSATA controller on your motherboard.

There is additional material on the addonics site, read it!

/ji

PS: I don't have stock in addonics, I'm just a *very* satisfied customer.


I've heard the port multipliers dont' play with well with linux.  btu that was a while back... is that not the case now?  are the multipliers realiable in linux?

---

### Post by jamesb73 on 2008-09-13
Thanks again.

I have a 2-port SATA controller I stuck in a windoze box a bit back, it's a fairly generic chipset so I might just stick it in the server and attach a drive just to see how ubuntu handles it before I go any further.  I'm not planning on adding it to my array at this point I just want to see how what device mapping it gives to it.

It'll be a month or so before I need to add an external cabinet to my system but I think that a multilane card, port multiplier and 5-disk caddy system in an external enclosure with a redundant PSU is the way to go.

- James

---

### Post by fjgaude on 2008-09-14
Sounds good to me... do it as you will. <smile>

---

