---
title: "Built in autonuke? For the parinoid"
date: 2011-06-09
forum: Security
---

### Post by SlagTheDrive on 2011-06-09
I've got 11.04 running on my machine with LVM/Full disk encryption.  Even still, I want to have have a way to quickly being a nuke of my machine.  Basically, I'd love some command(s) I could run or build into GRUB that would act similarly to DBAN's autonuke.  I know it is probably overkill with encryption, but encryption can be broken, if the machine get low level'd, it's gonna require a LOT more resources to recover (and then try and decrypt).  

I can even go the route of USB/CD bootable media, but only if it'll boot directly into destruction mode.

Thanks!

PS. Yes, I realise that building any of this into the system is dangerous, that's what offsite backups are for!

---

### Post by tubbygweilo on 2011-06-10
Just forget to remember your big, long, hard and varied pass phrase you need to enter system. Now if your data is as valuable as you suggest then physical security is top of your list as speedy destruction of data (mounted or not) is hard to manage unless helped along by a gushot to the hard disk or something of that ilk.

It is not quite as easy to throughly erase data as some stories, films or TV plots would suggest.

You might spend sometime searching slashdot.org as I expect that this question has been asked and answered on many occasions.

Good luck with your search.

---

### Post by HermanAB on 2011-06-10
Dude, your machine is encrypted.  All you need to do is hit yourself upside the head with a brick to forget the passphrase...

---

### Post by Thewhistlingwind on 2011-06-10
> **tubbygweilo said:**
> 

It is not quite as easy to throughly erase data as some stories, films or TV plots would suggest.


Well, it kinda is but it kinda isn't.

The main problem in the OP's case would be speed. A proper (At least as proper as software gets.) DBAN style wipe takes far longer then you have if your in a hurry.

It's not important though, your already using full disk encryption.

---

### Post by ehode on 2011-06-10
Buy a Degausser

---

### Post by collisionystm on 2011-06-10
Anyone seen the movie, The Core? The Hacker kid just punches a key combination onto his computers and it loads a big screen that says PURGING DATA and wipes out his machines... if only it were that simple!

---

### Post by CharlesA on 2011-06-10
> **ehode said:**
> Buy a Degausser

 ^ That.

---

### Post by walt.smith1960 on 2011-06-10
> **HermanAB said:**
> Dude, your machine is encrypted.  All you need to do is hit yourself upside the head with a brick to forget the passphrase...

Not sure I'd want to work in YOUR IT department. Resigning could be painful in more ways than one. 



:D

---

### Post by SlagTheDrive on 2011-06-10
I don't need "super ultra fast destruction" like they show in the movies (I'm running DBAN currently on another machine with DoD Short, taking at least 4-6 hours - I know it isn't fast).  If I wanted that, I'd put some thermite over my hard drive and tie it to an Arduino trigger - unfortunately I have a laptop and that isn't a viable option.  

Sure, I'd love an instant solution, but I need something portable and "hard" solutions are not (Can't carry a Barrett M82A1 with me everywhere, but it does "fix" hard drives very well)

I'm trying for something that is "safe"+1 like N+1 redundancy on servers.  Encryption is "safe" as long as my password is compromised.  Add the +1 of hard drive getting a 5220.22-M or similar, I figure I'm about as safe as I can reasonably get.

So besides this "hitting myself upside the head with a brick".  Is there something I can "build in"?  Can I tell grub to fire off something like dd and scrub the drive?

Thanks...

---

### Post by hellz99 on 2011-06-17
Key locked removable drive bay and a hammer within reach. 
Just cause I want to be sure the job gets done right.

---

### Post by ziekfiguur on 2011-06-17
something like
```
sudo dd if=/dev/urandom of=/dev/sda
```
would probably work, although it just overwrites the disk once instead of 3 times like dban,

---

### Post by SlagTheDrive on 2011-06-18
> **hellz99 said:**
> Key locked removable drive bay and a hammer within reach. 
Just cause I want to be sure the job gets done right.

I'm on a laptop.  That would require hauling around a screw driver and a hammer where ever I go.  Impractical.

---

### Post by SlagTheDrive on 2011-06-18
> **ziekfiguur said:**
> something like
```
sudo dd if=/dev/urandom of=/dev/sda
```would probably work, although it just overwrites the disk once instead of 3 times like dban,

Is there anyway to do anything like that from grub?

---

### Post by wolfgangmcq on 2011-06-18
What for? If you accidentally hit it, that could be a problem... and if you have a backup anyways, can't whoever it is you're afraid of just look at that?

---

### Post by tubbygweilo on 2011-06-19
The best I can think of is to install another full disk encryption via alt cd, the resulting palimpsest should make all previous data quite secure from prying eyes.

---

### Post by crispy_420 on 2011-06-22
Hardwired switch to thermite in case is quick solution and can't be stopped fast enough to preserve data. Sorry just had to say it.

Or you could have a clean OS as a host and use VMs stored in encrypted volumes. Pull the plug and volumes go back to previous states of being stored in secure state of encryption. If you keep them on an encrypted partition they usually get seen as RAW drives so people are likely to write over unless they know.

---

### Post by DZ* on 2011-06-23
> **SlagTheDrive said:**
> Is there anyway to do anything like that from grub?

I don't know, but you only need to overwrite key slots and LUKS header for the rest of the disk to become unrecoverable. That is less than 10Mb at the beginning of the disk ([http://code.google.com/p/cryptsetup/wiki/FrequentlyAskedQuestions](http://code.google.com/p/cryptsetup/wiki/FrequentlyAskedQuestions))

---

