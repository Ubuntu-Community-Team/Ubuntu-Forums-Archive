---
title: "Physically destroying all data on a harddrive?"
date: 2009-06-21
forum: The Cafe
---

### Post by mamamia88 on 2009-06-21
i have 2 old computers i am going to donate to bestbuy to get rid of but they won't even display on the monitor so i assume the videocards are dead.  i removed the harddrive and i don't just want to throw the hd in the trash in case someone gets a hold of them.  anyone know of a sure fire way to fry a old ide drive?

---

### Post by Firestem4 on 2009-06-21
> **mamamia88 said:**
> i have 2 old computers i am going to donate to bestbuy to get rid of but they won't even display on the monitor so i assume the videocards are dead.  i removed the harddrive and i don't just want to throw the hd in the trash in case someone gets a hold of them.  anyone know of a sure fire way to fry a old ide drive?

Use DBAN and run it a 20+ times. Then give the hard-drive to an environmentally safe Electronics recycling company. Don't throw computers/parts in the trash as they are hazardous to the environment.

(The only way someone will be able to recover data on that hard-drive afterwards would be to use an electron-resonance microscope. Time-consuming, no chance of full recovery, and very expensive. Unless there is a real reason for someone to get data off of it, you won't have any issues.)

---

### Post by mamamia88 on 2009-06-21
how would i use it if i can't even display it on the monitor?

---

### Post by Muffinabus on 2009-06-21
Plug it in to the computer you're using now?

---

### Post by mamamia88 on 2009-06-21
the computer i use now is sata this is ide think i might just have fun with fireworks

---

### Post by HavocXphere on 2009-06-21
Sledgehammer

---

### Post by Firestem4 on 2009-06-21
> **mamamia88 said:**
> the computer i use now is sata this is ide think i might just have fun with fireworks

You can buy an IDE adapter for 5-15 dollars, external or internal.

---

### Post by The Real Dave on 2009-06-21
> **mamamia88 said:**
> the computer i use now is sata this is ide think i might just have fun with fireworks

Got a large building near by? Drop it off the top :D Just make real real real sure that no one's gonna end up below it, get a few friends to stand below and make sure no one gets in the way. A HDD on the head would kill pretty quick.


Or, you could try a sledgehammer :D

---

### Post by MaxIBoy on 2009-06-21
If you have no way to actually plug it into your computer, you could always borrow someone else's.


You could try tying it up in a thin blanket, and putting it in a clothes dryer along with a bunch of refrigerator magnets. (I recommend using low heat.)

Few more suggestions: Run it right next to a heavy duty unshielded electric motor. Unscrew the outer case of the hard drive, put in a bunch of sand, screw it back together, and then try to make it spin up again. (Don't actually do this inside a computer.)

NEVER, EVER use fire on electronics. The magic blue smoke is usually quite toxic.

---

### Post by WatchingThePain on 2009-06-21
Definately use a hammer.
I opened my HDD up to look inside.
The discs are made of glass, so nice to smash!.

No erm, fill with zeros.
That's about as close as you get to a low level format at home AFAIK.
There's a command to do that in a terminal but duh I forgot what it is.
Maybe "DD" has an option to fill with zeros.
Soz, I am still a n00b.

---

### Post by Dimitriid on 2009-06-21
open it up and use sandpaper on the plates.

---

### Post by starcraft.man on 2009-06-21
ACID! Weeeee. It'd have to be a fairly strong acid, but I bet you it'd be the most amusing thing you'd ever seen. You'd probably need access to a real lab like at a college or uni though. Just don't breathe any vapors. I guess I've spent too many hours in a chem lab....

---

### Post by Pogeymanz on 2009-06-21
I would like to recommend trying your best to get it to a computer where you can erase it with software, as someone has already recommended. It would be a waste to just smash it as somebody may be able to use it.

Just my two cents.

---

### Post by mamamia88 on 2009-06-21
ok thanks for all the suggestions guys

---

### Post by JordyD on 2009-06-21
Smash it.
Put it in a fire.
Smash it.
Put it in a fire.
Etc.

---

### Post by mamamia88 on 2009-06-21
ok so far i've stomped on it a few times dropped it from the ceiling a few times and put it under a blow dryer wonder if data is still recoverable

---

### Post by JordyD on 2009-06-21
> **mamamia88 said:**
> ok so far i've stomped on it a few times dropped it from the ceiling a few times and put it under a blow dryer wonder if data is still recoverable

See above post.

---

### Post by mamamia88 on 2009-06-21
ok thanks everyone anyone know if you can put old computers in good will drop off areas?

---

### Post by dragos240 on 2009-06-21
Perhaps just install it in your own computer, and run gparted, and erase all the partitions. That will fix it.

---

### Post by rookcifer on 2009-06-21
Just use a Linux LiveCD and run the following command:
```

shred -z -n 1 /dev/hdx
```

where "hdx" is your hard disk (it might be hda, hdb, sda, sdb, etc.)

This will write zeroes to the drive once and will make all data unrecoverable, even if one were to try to use MFM's (electron microscopes).  This notion you need multiple passes is a myth.  One pass will completely zap it.

---

### Post by solitaire on 2009-06-21
to physically remove all data....
1) Undo all screws
2) Take top cover off of drive
3) Grab a bottle of you're fave soft drink (I suggest Coca-cola or Irn-Bru) and a washing up basin or bucket
4) Pour the soft drink into a basin
5) Place main drive unit into the basin
6) Leave for 24 - 36 hours
7) Check condition of acid etched platters.... :D (no more usable data)

---

### Post by H2SO_four on 2009-06-21
use Dban or truecrypt to write data over the whole disk about 35 times, whatever the DoD standard is.  Then get your hands on some thermite.  You may need to try hard for that one.  Light fuse, run.

---

### Post by Viranh on 2009-06-21
It took three pages for someone to recommend thermite? Really? That was the first thing that came to mind...

---

### Post by JordyD on 2009-06-21
> **dragos240 said:**
> Perhaps just install it in your own computer, and run gparted, and erase all the partitions. That will fix it.

Even if you erase the partitions, it can be recovered. You have to do something special.

---

### Post by JordyD on 2009-06-21
> **Viranh said:**
> It took three pages for someone to recommend thermite? Really? That was the first thing that came to mind...

I don't even know what it is.

---

### Post by RATM_Owns on 2009-06-21
> **WatchingThePain said:**
> Definately use a hammer.
Maybe "DD" has an option to fill with zeros.
Soz, I am still a n00b.
You mean like...
```
dd if=/dev/zero of=/dev/hdx
```

Better would be...
```
dd if=/dev/urandom of=/dev/hdx
```

Otherwise, use Dban.

---

### Post by WatchingThePain on 2009-06-21
> **RATM_Owns said:**
> You mean like...
```
dd if=/dev/zero of=/dev/hdx
```

Better would be...
```
dd if=/dev/urandom of=/dev/hdx
```

Otherwise, use Dban.

Yes, thank you for clarifying that for the OP.

---

### Post by solitaire on 2009-06-21
> **JordyD said:**
> I don't even know what it is.

Thermite  is just Iron Oxide and Powdered Aluminum..
Needs a VERY hot flame to ignite it though...

---

### Post by ghindo on 2009-06-21
I think a lot of this is probably overkill.  Just delete all the partitions with Gparted and then take it to your local dump/recycling plant and make sure it's properly recycled.

---

### Post by Dark Aspect on 2009-06-21
> **mamamia88 said:**
> i have 2 old computers i am going to donate to bestbuy to get rid of but they won't even display on the monitor so i assume the videocards are dead.  i removed the harddrive and i don't just want to throw the hd in the trash in case someone gets a hold of them.  anyone know of a sure fire way to fry a old ide drive?

> **HavocXphere said:**
> Sledgehammer

That would work, but why destroy an old hard drive? Even if its 2 or 3 GB you could experiment with it, install freebsd on it or something. I see no point in destroying a good piece of hardware. If anything you can use it for storage.

---

### Post by Firestem4 on 2009-06-21
To clarify as two people have recommmended this. If you are worried about data being recovered, Deleting the partitions does NOT delete any information, it just makes the hard drive File System unrecognizable to the host computer.

The best methods to make sure data is 100% unrecoverable are as following:

Phase transition (Ie: Liquification)
destruction (industrial shredders, smashed to oblivion)
Destabilize the magnetic structure of a hard disk (Powerful enough rare earth magnets will erase data)
&
overwriting data numerous and/or encryption and overwritting data again.

Special tools can be utilized to recover data from hard-drives that are low-level formatted (IE: Electron-resonance microscopes). As the name implies the microscope can detect resonance from what the magnetic field on a hard-disk IS and used to be. That is why overwriting a hard-disk with 30+/- passes with alternating values of 1's and 0's are recommended. Anything short of this type of equipment will not be able to recover data.

---

### Post by LookTJ on 2009-06-21
Use DBAN and run it over 3 times, or if you're paranoid, 15 times.

---

### Post by WatchingThePain on 2009-06-21
> **Firestem4 said:**
> To clarify as two people have recommmended this. If you are worried about data being recovered, Deleting the partitions does NOT delete any information, it just makes the hard drive File System unrecognizable to the host computer.

The best methods to make sure data is 100% unrecoverable are as following:

Phase transition (Ie: Liquification)
destruction (industrial shredders, smashed to oblivion)
Destabilize the magnetic structure of a hard disk (Powerful enough rare earth magnets will erase data)
&
overwriting data numerous and/or encryption and overwritting data again.

Special tools can be utilized to recover data from hard-drives that are low-level formatted (IE: Electron-resonance microscopes). As the name implies the microscope can detect resonance from what the magnetic field on a hard-disk IS and used to be. That is why overwriting a hard-disk with 30+/- passes with alternating values of 1's and 0's are recommended. Anything short of this type of equipment will not be able to recover data.


Yeah,
Cos not many dudes have an electron Microsocope at home.

---

### Post by Firestem4 on 2009-06-21
> **WatchingThePain said:**
> Yeah,
Cos not many dudes have an electron Microsocope at home.

Thats precisely the point lol. Unless the said destructee of data was liable for treason and had to get rid of sensitive data, no one would even go that far.

---

### Post by k2t0f12d on 2009-06-21
> **RATM_Owns said:**
> You mean like...
```
dd if=/dev/zero of=/dev/hdx
```

Better would be...
```
dd if=/dev/urandom of=/dev/hdx
```

Otherwise, use Dban.

Best would be random fill *then* zero fill.
Of course thats what the *shred* command does...

---

### Post by SerenityKill3r on 2009-06-21
Place under a big magnet, then place in a bucket of concentrated acid for a few hours.

---

### Post by handy on 2009-06-22
Pull the lid off it, if you don't have a torque driver small enough, drill or grind the heads off the screws, brake the disks & remove the magnets which are so incredibly strong that they are useful.

A couple of HDD magnets hold a reasonable sized & not too thin white board on our fridge door. ;)

---

### Post by rookcifer on 2009-06-22
> **Firestem4 said:**
> 
Special tools can be utilized to recover data from hard-drives that are low-level formatted (IE: Electron-resonance microscopes). As the name implies the microscope can detect resonance from what the magnetic field on a hard-disk IS and used to be. That is why overwriting a hard-disk with 30+/- passes with alternating values of 1's and 0's are recommended. Anything short of this type of equipment will not be able to recover data.

[Wrong.]("http://sansforensics.wordpress.com/2009/01/15/overwriting-hard-drive-data/") MFM's cannot be used to recover data that has been overwritten one time.  It has been tried, it doesn't work.  Those who say it does don't understand how hard drives work.

[Here]("http://www.springerlink.com/content/408263ql11460147/") is the abstract of a technical paper where researchers tried to use MFM's to recover data.

---

### Post by ugm6hr on 2009-06-22
> **mamamia88 said:**
> ok thanks everyone anyone know if you can put old computers in good will drop off areas?

Advertise it (for free) on your local freecycle group.

Unless it is totally worthless, someone will pick it up; I had someone collect a redundant PC for its PSU before.

---

### Post by Jestersage on 2009-06-22
If it's larger than 20Gb, I think most of the FreeGeek will take it.

here's how we do it:
a) check if the HD is >20Gb. If it is, we wipe it (forgot algorithm), and also check if disk is reusable.
b) if not reusable, we first remove the control board (that's the valuable part). Then we actually crush it with a dedicate hole-puncher (way better than sledge hammer as it a 2nd-class lever). We crush it until we see one of the platter is destroyed.

Sidenote: there's a freegeek if you live in:
# Portland, OR
# Fayetteville, AK
# Central FL
# Chicago, IL
# Columbus, OH
# South Bend, IN 
# Vancouver, BC (Canada)
# Murfreesboro, TN 
# Minneapolis-Saint Paul
# Toronto, ON (Canada)
# Providence, RI
Bworks in St Louis also does this stuff.

---

### Post by JohnFH on 2009-06-22
> **rookcifer said:**
> [Wrong.]("http://sansforensics.wordpress.com/2009/01/15/overwriting-hard-drive-data/") MFM's cannot be used to recover data that has been overwritten one time.  It has been tried, it doesn't work.  Those who say it does don't understand how hard drives work.

[Here]("http://www.springerlink.com/content/408263ql11460147/") is the abstract of a technical paper where researchers tried to use MFM's to recover data.

At last.  Some sense has come to this thread.  There's far too much FUD about the need to repeatedly wipe a hard drive to get rid of the data.  One pass is enough.

I think it's a waste of resources to physically destroy a hard drive when all that's needed is a simple dd command.

---

### Post by handy on 2009-06-22
> **JohnFH said:**
> At last.  Some sense has come to this thread.  There's far too much FUD about the need to repeatedly wipe a hard drive to get rid of the data.  One pass is enough.

I think it's a waste of resources to physically destroy a hard drive when all that's needed is a simple dd command.

I agree. 

Though when a drive has failed it is worth pulling it apart, as the disks make good coasters, or bird deterrents when hanging in your fruit trees, & as previously stated the magnets are awesome, so strong they are dangerous.  I'm sure I'm not the only one that has received a blood blister when the things snap together! lol

You can't pull them apart, you have to slide them off each other & with quite some effort. :)

---

