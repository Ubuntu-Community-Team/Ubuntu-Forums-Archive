---
title: "Unable to boot from Windows XP Installation disks"
date: 2007-06-07
forum: The Cafe
---

### Post by Eric_ on 2007-06-07
Okay; here's the issue
I installed Ubuntu, after formatting my entire drive, I figured I would make a partition for windows later, or even put another drive in for it, anyway. I install ubuntu, everything on ubuntu works great, however, When i try to boot from the windows xp installation disk (tried 2 retails and one burned) they all get to where it says "starting windows" (from the installation screen, where it would then walk you through installation/partitioning) and then results in the blue screen of death, basically saying it has stopped to prevent hardware damage, But I can boot from ubuntu, mandrivia, ect, all just fine.


Solutions? :popcorn:

---

### Post by KiwiNZ on 2007-06-07
Are your drives sata?
 
XP does not support sata natively. Check the MS site

---

### Post by nonewmsgs on 2007-06-07
if you have ANY kind of ide/sata card windows is often quite bitter about that.  i have an ide card beause new motherboards beleive one ide port is enough and i had to pull it out before i could get it to work although that might have also been because my dvdram was on that card.  ubuntu installation is infinitely better.

---

### Post by DeafDog on 2007-06-07
> **KiwiNZ said:**
> Are your drives sata?
 
XP does not support sata natively. Check the MS site
Depends. Some motherboards/chipsets (like my nForce 4 for example) will run the SATA controllers in a compatability mode where they appear like regular IDE drives, so XP will detect them when installing. After you've got Window installer however, you're suppose to install the proper drivers so Windows starts using them in full SATA mode, which is faster and less taxing on the CPU.

---

### Post by Eric_ on 2007-06-08
Yeah, my drives are all SATA (all of them; dvd/cd drives, hdd's, ect) Is there a solution?

---

### Post by tim1980 on 2007-06-08
check your BIOS settings, sometimes its possible to change the mode of SATA to Emulation or something so it pretends to be IDE drive but just slower but will install this way

---

### Post by steven8 on 2007-06-08
I say you consider yourself d**n lucky.  Take the discs out in your backyard, hang them on wires, and shoot them with bb guns until there is nothing left.

Just my 2 cents.

---

### Post by Eric_ on 2007-06-08
> **steven8 said:**
> I say you consider yourself d**n lucky.  Take the discs out in your backyard, hang them on wires, and shoot them with bb guns until there is nothing left.

Just my 2 cents.

My home is constantly subject to search to make sure I have no weapons :-P. And I just got my ankle monitor cut off today, so i'd rather not get tinto trouble so quickly. and I like to have windows dual booted for gaming, vent, ect.

---

### Post by woodsmoke on 2007-06-08
Hi
I'm the new person on the block....I DETEST the term "newbie"....it implies that somehow you are less intelligent than myself..... and the folks who have been around Linux for a while know that I'm just older than dirt...and not very intelligent....

However, there is a way "around this".... Windblows DOES NOT....like to go in "after" linux......

But...there is a disc called "linux console"...it floats around on the web....and....surprisingly.....

Norton Partition Magic 8 will partition the hard drive .... unfortunately, since Norton is now bound at the hip with Microsith, only Partition Magic 9/10- will work with Vista....

But anyway...... either of these proggys.....I don't recommend the console if you are "new" to computers...it is command line and .... not necessarily easy to understand....but anyway....Norton is more "graphical"...

It shows you a "line" that describes what is on a HD..... and you can "move it back and forth"....

use one of the proggys to change the partition "size" of the present partition.... 

HOWEVER......you CANNOT....just "let it go at that..".....you ALSO have to reformat,,at the same time.... the "other" part of the drive...as FAT....File Allocation Table....

Norton will kind of walk you through it.....yeech...I detest anything attached to Norton....but it is better than console....which is command line....yeech even MORE...

but anyway... you can resize the partition and AT THE SAME TIME.... format the "left over" amount as a FAT partition....

THen.....when Ubuntu....or actually any Linux Distro that is worthwhile..... "looks' at the drive it says....

Hey..... I see two thingys here....one of them is...."reiser/whatever/don't knwo"....and..."FAT"....what do you want me to do...?

Ubuntu....or any other distro will then patiently follow your instructions to "dual boot".... take over the FAT partition.... and leave the other one alone....

it will then put a "boot loader" in "front" of the whole mess.....

so....when you boot up...you "should"....."should".... see....the bios and stuff of the board... you know....wher you can hit F2 or "esc" and get to bios....

and then see a "boot loader"....Ubuntu will be on top and Windblows....will be in it's PROPER place.... after ... things like "safe mode" and "command line"...etc....

well.....long post...but cut to the chase.... borrow a copy of Norton BEFORE 9 and let it work its magic for you...

HOWEVER.....it will install itself on the HD.... but that's ok..... for the peace of mind it affords....

even though I detest the piece of drek

woodsmoke

---

### Post by Eric_ on 2007-06-08
> **woodsmoke said:**
> text

woodsmoke


Thanks, i'll give that a shot in a few mins.;)

---

### Post by woodsmoke on 2007-06-08
Hi

please remember that you do it at your own risk....

wellll.....naawwww.....

I've done it with my old MADBOOT disk that you can't get anymore.... a 3.5 floppy.... it's now a CD....

JUST BE CAREFUL.....to follow all the "prompts"......

Actually you can get into the admin console and repartition from within Ubuntu....although I haven't done it yet , I'm a new person here....but Linux will let you resize the partition from within itself...problem is that it's within itself...

Actually..... you could also use Kanotix.... the live cd....it will ask what you want to do and youkind of work through it....

but....anway...I've got the old Norton 8....YEEECCHHH.... I did NOT know that it was gonna put some stuff on the HD.... and reparttiojned.... to install XP after another linux...

and by the by....if you are going to get a cheapo laptop or whatever that has VISTA on it.... only PM 9 is "liscenced" to resize the partition in Vista so you can install a linux on the FAT...

have fun!
woodsmoke

---

