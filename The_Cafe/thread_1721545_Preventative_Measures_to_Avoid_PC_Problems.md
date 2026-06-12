---
title: "Preventative Measures to Avoid PC Problems"
date: 2011-04-04
forum: The Cafe
---

### Post by billdotson on 2011-04-04
There are many problems that can occur on a modern computer.
Once they occur, they are often very difficult, or at least annoying, to repair. Sometimes the problems cannot be repaired adequately at all. This list is not exhaustive, but here are a few things you can do to as a precaution. Feel free to add to the list if there is anything missing.

1) Backup your files. This isn't that difficult to do, but many people do not do it in an effective way. Some people do back their files up, but only do so periodically. When something happens, such as a hard drive failure, recent files may not be backed up and may even be a cause for panic if they are very important. Standard practice is to backup new files as soon as you create them. If you have new files created daily, then you need to back them up daily. 
    You can use an external hard drive, a flash drive, or optical discs (DVD and CDs) for data backup. Hard drives are mechanical in nature and error prone but are cheap for the amount of storage space they offer. Optical discs are good because they are not mechanical, but they can degrade if they aren't treated well.

2) Backup your Master Boot Record (including partition table).
There are many things that can happen that can cause problems with the partition table or the master boot record. Boot sector viruses can wreak havoc. By backing up the MBR, repairing a boot sector virus can be as simple as restoring the MBR.

3) Make an image of you operating system partition. You can use ntfsclone, part of the ntfsprogs package for Windows installs. For *nix OSes, clonezilla, partimage, etc. can be used. This can make problems very easy to solve in some cases. If you are using Windows for example, and you start getting lots of errors and other strange things, you can simply restore your image and get it back to how it was working when you backed it up. For the Windows example, if you are still getting blue screens, etc. after a restore, then a hardware issue may be likely.

4) Keep your operating system and the programs you have installed separate from your data. You can do this by having your operating system installed on one partition, and having another partition used for data storage only. GParted is a partition editor for GNU/Linux that works really well. If your operating system partition gets messed up, then you won't have to pick through folders to find your data.

---

### Post by 3Miro on 2011-04-04
Loss of important date is the only irreversible problem. Everything else can be fixed with clean re-install and some time. I can get an Ubuntu machine up an running to 100% productivity in couple of hours (given a good internet connection). I can probably do that on Arch too.

I would go with backup of all vital data and don't bother with the rest.

---

### Post by sydbat on 2011-04-04
> **3Miro said:**
> I would go with backup of all vital data and don't bother with the rest. This. /thread

---

### Post by aysiu on 2011-04-04
> **3Miro said:**
> Loss of important date is the only irreversible problem. Everything else can be fixed with clean re-install and some time. I can get an Ubuntu machine up an running to 100% productivity in couple of hours (given a good internet connection). I can probably do that on Arch too.

I would go with backup of all vital data and don't bother with the rest.
For Linux, yes.

For Windows and Mac, a reinstallation takes too long.

---

### Post by dh04000 on 2011-04-04
To avoid hardware problems keep your system cool and clean. To reduce wear and tear, try turning your computer off when not in use. Saves a bundle of cash with a lower energy bill.

The more you know.

---

### Post by dnairb on 2011-04-04
I would also add (especially for new users): "Stop fiddling." I have seen a  number of posts here and other support forums (fora?) which begin: "I was just looking at blahblahblah, and did blahblah. Now my system doesn't work!"

---

### Post by aysiu on 2011-04-04
> **dh04000 said:**
> To reduce wear and tear, try turning your computer off when not in use. I have a laptop and netbook, so I just put them to sleep instead of turning them off.

---

### Post by youbuntu on 2011-04-04
Don't use computers = avoidance of PC problems :)

---

### Post by handy on 2011-04-04
> **dh04000 said:**
> To avoid hardware problems keep your system cool and clean. To reduce wear and tear, try turning your computer off when not in use. Saves a bundle of cash with a lower energy bill.

The more you know.

I agree with the above.

For desktop systems it is easy to disconnect the cables, remove the top/side cover & take the case outside for both the extra light & due to the dust that is about to fly. 

If you have your own air compressor (or can of compressed air) blow all of the dust out of the machine, paying particular attention to any heat-sinks & fans.

Always prevent the fans from being spun by the air as you can cause damage. 

Give the PSU a really good blast of air, again prevent the fan(s) from revolving.

You can sometimes (if it hasn't already been done) create a cooler internal environment in desktop/tower cases by using nylon ties to group & route cables in such a way as to be less of on an obstruction to the air flow. 

For Notebooks/compacts, you have to go to the trouble of removing the keyboard so you can access the gizzards. Once inside, use the compressed air routine previously mentioned.

If you have a noisy fan removing it & soaking it overnight in light oil (sewing machine oil is good) will rejuvenate it. I have found automatic transmission oil is too heavy, but diesel fuel works a treat, so it is probably the cheapest solution.

After soaking I suspend the fan in the container above the oil to drip (over-night is good), then dry it as best I can before re-installation.

If you replace a heat-sink, be sure to remove the remnants of the original thermal paste on the CPU/GPU or other chip, before applying an even thin coat of new paste & then of course the heat-sink assembly.

---

### Post by Irihapeti on 2011-04-04
> **dnairb said:**
> I would also add (especially for new users): "Stop fiddling." I have seen a  number of posts here and other support forums (fora?) which begin: "I was just looking at blahblahblah, and did blahblah. Now my system doesn't work!"

Really? But you haven't lived until you've borked your system at least once. :)

---

### Post by handy on 2011-04-04
> **Irihapeti said:**
> Really? But you haven't lived until you've borked your system at least once. :)

You do the most in depth learning when you are forced to. :)

---

### Post by msandoy on 2011-04-04
For new systems, backups are the most important. But as time ticks bye, fans and thermal paste suffers. Handy has a lengthy post about the importance of cleaning heatsinks and fans, but I'd like to add, cheap computers very often have "very" cheap thermal paste on the cpu and gpu. Replacing it might save you hours of fan noise torture and burnt fingertips on laptops. 
I have an old HP laptop, I need to remove 64 screws to access the cpu heatsink. But it was worth it. Temperature sank by 10-15°C on average.
In combination with handy's fan soaking, you can have trouble free computing for years.

---

### Post by sammiev on 2011-04-04
I do a full backup once a week to a usb hdd. Takes me less than 30 min to be up and running where I was before the ooppppss I made. LOL :popcorn:

---

### Post by handy on 2011-04-04
I use a ReadyNAS Duo to store my backup data, it also allows my wife to access vids from the computer in her office.

Any essential data is also backed up onto optical media, usually more than once.

As far as a system backup I don't bother. If my drive fails I'll replace it, re-install Arch, use the various how-to I have written to refresh my memory on certain aspects of setting Arch up to be just how I like it. I also have copies of configuration files backed up which will make the re-installation that much quicker/easier.

With my IPCop headless firewall/router, I have screen shots of every configuration page from the client browser interface, I've had to use it once when the 2GB drive died. It made the job of setting it up again so easy.

As far as the topic of this thread is concerned, you can't prevent hardware failures. You can keep your machine internally clean & as cool as possible to help it last longer, but you can't stop the inevitable HDD failure or the mains spike that destroys your UPS & most of your computer.

Taking measures to make it as easy as possible to recover from the worst case scenario is the best we can do.

I don't store data off-site. If our house is destroyed by fire my data will be the least of my concerns for sometime.

---

### Post by CharlesA on 2011-04-04
> **3Miro said:**
> Loss of important date is the only irreversible problem. Everything else can be fixed with clean re-install and some time. I can get an Ubuntu machine up an running to 100% productivity in couple of hours (given a good internet connection). I can probably do that on Arch too.

I would go with backup of all vital data and don't bother with the rest.

+1 to the backup vital data and don't bother with the rest. The rest can usually be reinstalled fairly easily and isn't worth backing up.

I backup my Steam folder, even tho that can be "easily" replaced, since I don't want to download 200 GB of data again. :lol:

> **aysiu said:**
> For Linux, yes.

For Windows and Mac, a reinstallation takes too long.

That's true. I have been using Clonezilla to clone a machine after I get it all set up, so if something happens to the drive or the machine, I can restore the programs and whatnot without having to spent a few hours reinstalling junk.

> **aysiu said:**
> I have a laptop and netbook, so I just put them to sleep instead of turning them off.

I do that with my desktop, when I am done using it, I put it to sleep. My netbook gets turned off since I use it maybe twice a week.

---

### Post by Zerocool Djx on 2011-04-05
I have to semi disagree with number 4. Reason being, I agree with your concept, but I have always had my data on 2 separate drives rather then 2 partitions. It's common for most of my custom builds  to have a primary and secondary drive. Secondary drive is for user data.

---

### Post by sydbat on 2011-04-05
> **handy said:**
> For desktop systems it is easy to disconnect the cables, remove the top/side cover & take the case outside for both the extra light & due to the dust that is about to fly. 

If you have your own air compressor (or can of compressed air) blow all of the dust out of the machine, paying particular attention to any heat-sinks & fans.I use a vacuum with the crevice tool. Never had a problem and it reduces the dust by 99%.

> Always prevent the fans from being spun by the air as you can cause damage. 

Give the PSU a really good blast of air, again prevent the fan(s) from revolving.When I vacuum out the interior, I make sure to give the fans a nice fast run to spin the caked on dust off the backside. Again, never had a problem.

> You can sometimes (if it hasn't already been done) create a cooler internal environment in desktop/tower cases by using nylon ties to group & route cables in such a way as to be less of on an obstruction to the air flow.Excellent advice. More airflow = cooler interior.

> For Notebooks/compacts, you have to go to the trouble of removing the keyboard so you can access the gizzards. Once inside, use the compressed air routine previously mentioned.Vacuum. It is a little different and you have to make sure that any smaller bits don't get sucked up.

> If you have a noisy fan removing it & soaking it overnight in light oil (sewing machine oil is good) will rejuvenate it. I have found automatic transmission oil is too heavy, but diesel fuel works a treat, so it is probably the cheapest solution.

After soaking I suspend the fan in the container above the oil to drip (over-night is good), then dry it as best I can before re-installation.Too much messy work. Good ol WD40 is easier. All you have to do is peel off the sticker that covers the top of the fan, pop out any "cover" for the bearing area, spray the WD40 with the included "spot straw" (I have no idea what it is really called, but it is always red), put it all back together and you're good to go. Wipe off any excess before re-installing.

> If you replace a heat-sink, be sure to remove the remnants of the original thermal paste on the CPU/GPU or other chip, before applying an even thin coat of new paste & then of course the heat-sink assembly.With pre-built machines, this is great advice. If you build your own, you will already have put good quality thermal paste onto your chip / heat sink surfaces. However, it is always good to check / replace every few years regardless.

---

### Post by Darth Penguin on 2011-04-05
Hardening the OS with Bastille helps mitigate the possibility of hackers and Internet threats causing damage. Fail2Ban as well.

---

### Post by handy on 2011-04-05
> **sydbat said:**
> 
I use a vacuum with the crevice tool. Never had a problem and it reduces the dust by 99%. 

I used to use such a vacuum technique when I was in business. These days now that I own a compressor I prefer to release the dust to the outside outside world. :)

> **sydbat said:**
> 
Too much messy work. Good ol WD40 is easier. All you have to do is peel off the sticker that covers the top of the fan, pop out any "cover" for the bearing area, spray the WD40 with the included "spot straw" (I have no idea what it is really called, but it is always red), put it all back together and you're good to go. Wipe off any excess before re-installing. 

I'd never use a penetrating oil for lubrication, but if it works for you, that's great. :)

---

### Post by fela on 2011-04-05
> **glossywhite said:**
> Don't use computers = avoidance of PC problems :)

Best advice ever there mate! :)

---

### Post by 3Miro on 2011-04-05
This has gone into hardware issues now. Those are different from software.

I don't blow out the dust form my machine, I use wet-wipes. Turn it off, open it up and then go over the entire surface of the interior, gently over the blades of the fans, even dismount the video card to clean that one. I used to disassemble the heat sync cover of the GPU as well. I do the general wiping every month or two, bigger disassembly happens every 3 - 4 months. Note that this depends on the conditions in which you run your system.

Laptops are harder to clean, although it is even more important that you clean them.

---

### Post by fela on 2011-04-05
BTW, about backing up / not losing data, this is my setup:

I have a server running 24/7, runs quite a few different things, but what I'll mention here is that it has 2TB of space in it. 1TB is used for its own data, and the other for backups. It's set to backup everything using rsync incremental backups (using hardlinks to avoid duplication), every 2 nights, to the backup drive.

So, if I have any important data on any other PC, such as photos, I just transfer it to some place on the server, and know that it will be stored in 3 places come the next turn on the cron wheel.

---

### Post by CharlesA on 2011-04-05
> **fela said:**
> BTW, about backing up / not losing data, this is my setup:

I have a server running 24/7, runs quite a few different things, but what I'll mention here is that it has 2TB of space in it. 1TB is used for its own data, and the other for backups. It's set to backup everything using rsync incremental backups (using hardlinks to avoid duplication), every 2 nights, to the backup drive.

So, if I have any important data on any other PC, such as photos, I just transfer it to some place on the server, and know that it will be stored in 3 places come the next turn on the cron wheel.

That sounds pretty close to the way I do my backups.

I've got each desktop set to run a script to sync the local documents folder to my server, and the server does incremental backups daily. I also do monthly backups to two different drives, one incremental of just documents and not media and one of everything.

I think the only thing I don't do is have offsite storage, which would be a good idea, but I haven't decided how to do yet.

---

### Post by 3Miro on 2011-04-05
I have a work computer, home computer and an external HDD. Every day at the end of the work day I rsync my important folders with the external HDD, then I go home and rsync with the home machine. Effectively I get three copies of everything, I can access all my data simultaneously at home, work or somewhere else if I have to travel and I don't have to bother maintaining a separate server (BTW, I do have a separate server, I just don't use it for backups).

---

