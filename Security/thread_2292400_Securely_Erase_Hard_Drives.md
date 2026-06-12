---
title: "Securely Erase Hard Drives"
date: 2015-08-27
forum: Security
---

### Post by lingpanda on 2015-08-27
Hello,

    Looking for suggestions on software that adheres to the NIST 800-88 standard. I've only seen DoD 5220.22-M software. I do not want to go with a commercial product if it can be avoided. If not I'm looking at this.

[http://www.jetico.com/products/enterprise-data-protection/bcwipe-totalwipeout-enterprise](http://www.jetico.com/products/enterprise-data-protection/bcwipe-totalwipeout-enterprise)

How does dban stack up against this commercial product? Thanks.

---

### Post by bashiergui on 2015-08-27
I don't think NIST has endorsed any specific product. DBAN is pretty much the standard in the industry. 

This link discusses a few reliable alternatives in relation to NIST.
[http://mobile.esecurityplanet.com/windows-security/how-to-securely-delete-data-from-hard-drives.html](http://mobile.esecurityplanet.com/windows-security/how-to-securely-delete-data-from-hard-drives.html)

---

### Post by ajgreeny on 2015-08-27
I know nothing about the NIST 800-88 standard of data destruction but I wonder if you are a bit paranoid.

I have seen many discussions on secure deletion and many of them are now suggesting that a single-pass overwrite of files on a spinning disk is quite suficient to make data non-recoverable.

See [http://www.nber.org/sys-admin/overwritten-data-guttman.html](http://www.nber.org/sys-admin/overwritten-data-guttman.html) for a long and interesting discussion of this which seems to dispel the urban myths about data being recoverable even after it has been overwritten.

---

### Post by TheFu on 2015-08-28
I don't know anything about these standards - I do not believe the US military ever releases any HDDs after use on secure networks. They physically destroy them.

For SSDs, there is no known way to remove all data. Ask any data forensics expert.
For spinning HDDs that you need to reuse or sell, DBAN with 3 passes should be enough.
* all ones
* all zeros
* random
For spinning HDDs that you don't want reused, drill 5-10 holes through them before sending them to a HDD shredder. Watch the destruction happen - may want to video this for later proof. There are industrial shredders.

---

### Post by HermanAB on 2015-08-29
Howdy,

The 'DOD erase' programs and things like 'shred' are a bit of a myth.  In general, a sure sign of a clueless security newbie, is someone who actually use these erase programs.  The trouble is that the modern day file systems on various OS's and the disk controllers on the actual disk drives, put a spanner in the works of these simplistic erase programs.

Every magnetic HDD controller actually has a secure erase function built in (for about the last 20 years or so), which can be activated by the 'hdparm' program.  This erase routine can erase everything, including the space between the tracks.  Read the hdparm man page for details.

Solid state drives work differently and a simple erase is sufficient.

If you really work with military stuff, then your government's IT people should tell you what to do and you better contact them immediately, if you don't want to end up in the clink by accident.  If you are working for your government's IT, then I think you have a much bigger problem...

---

### Post by lingpanda on 2015-09-01
Thanks for the suggestions. I work in the private sector. Due to regulations I have to have a process on hand on how hard drives will be re-purposed. Looking at Blancco it appears it adheres to the NIST standard. Again appreciate all the feedback.

---

### Post by a2339 on 2015-09-05
in a terminal type
```
man dd 
```
from there you should be able to set up a commandline similar to
```
dd if="/dev/random" of="sdb" bs=1048576 count=9000
```
```
dd if="/dev/zero" of="sdb" bs=1048576 count=9000
```
where the "blocksize" bs in this example is 1MiB, this example overwrites the second harddrive sdb to 9000MiB [change that number as required].  it gives you no progress updates so you probably want to time 1000MiB.  Even after doing that, if your drive contains anything as sensitive as other people's money details or current login info, drilling to permanently break it is probably the safest option.

---

### Post by ian-weisser on 2015-09-05
Smashing HDDs with a sledgehammer is *really* satisfying...for the first few. It does get old (and heavy) rapidly.

---

### Post by CharlesA on 2015-09-05
> **ian-weisser said:**
> Smashing HDDs with a sledgehammer is *really* satisfying...for the first few. It does get old (and heavy) rapidly.

Been there, done that and it is very satisfying, but also lets you get some exercise. :p

---

### Post by bashiergui on 2015-09-06
> **ian-weisser said:**
> Smashing HDDs with a sledgehammer is *really* satisfying...for the first few. It does get old (and heavy) rapidly.
The anount I can smash before it gets old is directly proportional to how much I'm irritated at the world. There are days when there aren't enough hard drives to smash ;)

---

### Post by fugu2 on 2015-09-07
> **ian-weisser said:**
> Smashing HDDs with a sledgehammer is *really* satisfying...for the first few. It does get old (and heavy) rapidly.

FYI, smashing  a hard drive with a hammer will not remove the bytes that are store on the magnetic material. To be certain that the data is actually destroyed, you need to raise the temperature of the magnetic storage material above the Curie temperature ([https://en.wikipedia.org/wiki/Curie_temperature](https://en.wikipedia.org/wiki/Curie_temperature), most likely when its red hot), then quench it in a bucket of water. A blow torch should supply enough heat for this to happen.

---

### Post by CharlesA on 2015-09-07
> **fugu2 said:**
> FYI, smashing  a hard drive with a hammer will not remove the bytes that are store on the magnetic material. To be certain that the data is actually destroyed, you need to raise the temperature of the magnetic storage material above the Curie temperature ([https://en.wikipedia.org/wiki/Curie_temperature](https://en.wikipedia.org/wiki/Curie_temperature), most likely when its red hot), then quench it in a bucket of water. A blow torch should supply enough heat for this to happen.

It would break the platters, wouldn't it?

---

### Post by QIII on 2015-09-07
It would bend the platters.

I've cut disks into small pieces with blow torches.  Not for security, mind you.  Just for the heck of it.

Would like to do it with a plasma cutter.   Or a light saber.

---

### Post by portalhavoc on 2015-09-07
Have you tried using CloneZilla to format the hard drives? 

[http://www.clonezilla.org/](http://www.clonezilla.org/)

In case if that doesn't work, You could try using another formatting program.

Or if you want to get destructive. You could drill holes in the drives. or take them to the shooting range and shoot it with a shotgun. or microwave it. :P

---

### Post by CharlesA on 2015-09-07
How is using clonezilla a way to format hard drives?

I'd feel more comfortable by taking old drives to a hard drive shredder like this one: [https://www.youtube.com/watch?v=sQYPCPB1g3o](https://www.youtube.com/watch?v=sQYPCPB1g3o)

All I can say is... "And it's gone."

---

### Post by brian-mccumber on 2015-09-08
I have driven many, many, many stakes in the ground with a sledge hammer for forming concrete, I could smash a whole lot of hdd's with one.

---

### Post by ventrical on 2015-09-09
Microwave antenna magnet. Just hold that dougnut close to spining drive and it will brick. A less destructive method is MaxBlast or WD Data Life Guard Tools that will give all zeros.

Actually MaxBlast4 Zero Fill Process. I got it from an image on a Maxtor site about 8 years ago (still works - can't believe it !). You can put the image on a floppy or CD. (I use a USB floppy drive).  It will hard detect any hdd. (Haven't tried ssd yet. Would be an interesting experiement.)

Regards..

---

### Post by Bucky Ball on 2015-09-09
DBan.

---

### Post by ventrical on 2015-09-09
> **Bucky Ball said:**
> DBan.

Can't put image to USB floppy or CD but I guess it could be run from 'live' USB. Thanks..

---

### Post by ventrical on 2015-09-09
> **CharlesA said:**
> How is using clonezilla a way to format hard drives?

I'd feel more comfortable by taking old drives to a hard drive shredder like this one: [https://www.youtube.com/watch?v=sQYPCPB1g3o](https://www.youtube.com/watch?v=sQYPCPB1g3o)

All I can say is... "And it's gone."

All that wasted platinum... and that thing can probably eat a whole person in a very short period of time...scary stuff..

---

### Post by ventrical on 2015-09-09
> **ventrical said:**
> Microwave antenna magnet. Just hold that dougnut close to spining drive and it will brick. A less destructive method is MaxBlast or WD Data Life Guard Tools that will give all zeros.

Actually MaxBlast4 Zero Fill Process. I got it from an image on a Maxtor site about 8 years ago (still works - can't believe it !). You can put the image on a floppy or CD. (I use a USB floppy drive).  It will hard detect any hdd. (Haven't tried ssd yet. Would be an interesting experiement.)

Regards..

Almost 9 hours and 91% complete with MaxBlast4 Zero Fill Process of Maxtor SATA 160GB hdd. I'll try Dban later.

Regards..

---

### Post by ventrical on 2015-09-10
Dban = nwipe = no GUI . for 15.10 .. kewl..

---

### Post by ventrical on 2015-09-10
Dban = no GUI for 14.04 either (yet advertised in USC).

---

### Post by fugu2 on 2015-09-12
> **Bucky Ball said:**
> DBan.Dban is great if the hard drive is still functional. If the hard drive has failed, but there is still data on it, its a no-go.

---

### Post by HermanAB on 2015-09-13
The problem is that if you are merely playing, fine, carry on.  

If you are really serious about deleting data in order to re-use the disk at the same or higher security level, then you need to use hdparm, which will activate the built-in erase routine in the drive controller.

If you need to use the drive at a lower security level - sorry - not allowed.

If you need to destroy all classified data on the drive forever, melt or shred it.

---

### Post by kurt18947 on 2015-09-13
For broken drives - so obviously no reuse - I take them apart. It does typically take a special screwdriver tip but I don't need to be careful. I harvest the magnets for various uses. There are several choices to make the exposed platters unreadable. Sandpaper, just removed magnets wiped over the surfaces, pliers to bend the crap out of them (metal platters), torch, [your sadistic pleasure here:p]. Older drives have stronger magnets but the newer ones ain't bad.

---

