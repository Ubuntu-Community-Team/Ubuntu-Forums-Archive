---
title: "Wiping a drive securely"
date: 2009-05-20
forum: The Cafe
---

### Post by logos34 on 2009-05-20
ok, here's another story I saw while over at the Beeb site:
> 
Hitting delete
Selling a PC? How to delete all the data on it 

[http://news.bbc.co.uk/2/hi/technology/8056364.stm](http://news.bbc.co.uk/2/hi/technology/8056364.stm)

Folks, if you think formatting a drive erases it securely, think again.  And don't even think that simply deleting files (trash) is going to do it.

Even formatted drive partitions can easily be recovered using **[Testdisk]("http://www.cgsecurity.org/wiki/TestDisk") **(avail in the ubuntu repos).

If you want to securely wipe it, you don't even need DBan disk.  The dd command will do same thing:

> # dd if=/dev/urandom of=/dev/sdx

---

### Post by northwestuntu on 2009-05-20
i used a program called killdisk.  worked good and had a lot of options.

---

### Post by gnomeuser on 2009-05-20
[Darik's Burn and Nuke](http://www.dban.org/)

---

### Post by stmiller on 2009-05-20
dban!

---

### Post by starcannon on 2009-05-20
I just pull my hdd's out and put new ones in; its cheap, easy, and actually adds "value" to the computer, making it easier for me to sell. I then "archive" my hdd in a cardboard box in the basement lol; I may have to turn them into generic file storage space one of these days.

---

### Post by John.Michael.Kane on 2009-05-20
There is also HDDerase.

---

### Post by logos34 on 2009-05-20
But the dd command is just as good as the free version of DBan, killdisk or something like Shred--it's included on the ubuntu live install cd (and just about every other linux utility disk).  The point is you don't need any proprietary software app.

> Of course you could always deploy the basic dd command more associated with backing up Master Boot Records (MBR) and imaging partitions or whole disks. It really is as simple as dd if=/dev/zero of=/dev/hda to overwrite a drive with a series of zeros or dd if=/dev/urandom of=/dev/hda which overwrites a drive with random data (though some will claim it is only really pseudo-random). **However, if you think this is pretty basic and can&#8217;t compete with the relative granularity of Shred or Secure-delete there are those who disagree. The people at 16 Systems have issued the &#8220;Great Zero Challenge&#8221; to established recovery businesses to retrieve one file and one folder from a hard drive wiped with the dd command. So far the prize has remained unclaimed**.

---

### Post by dragos240 on 2009-05-20
also you could just delete the partition too. There's nothing left after that, and no way to recover it.

---

### Post by Mehall on 2009-05-20
Yeah, 16 Systems say that most data recovery companies will hang up as soon as you say the letters "dd", and the ones that don't will ask if it completed first. if the answer is yes, THAT'S when they hang up.

/dev/zero is more than enough (having said that, I DO have a couple copies of DBAN, but it's easier and quicker to boot than a Live Disc, and loads all of itself to ram. once it's running, you can take the disc out.)

---

### Post by logos34 on 2009-05-20
> **dragos240 said:**
> also you could just delete the partition too. There's nothing left after that, and no way to recover it.

Testdisk can.  It locates and restores deleted, lost and damaged partitions.

> **Mehall said:**
> Yeah, 16 Systems say that most data recovery companies will hang up as soon as you say the letters "dd", and the ones that don't will ask if it completed first. if the answer is yes, THAT'S when they hang up.
:lolflag:

---

### Post by Ceiber Boy on 2009-05-20
Kill Disk is a us department of defence program that they use to erase the data from their hardisks before they decommission them. it is a free download and the program is run from a cd from BIOS. it simply stamps zeros right the way across your hardisk. phically removing the data.

for the more secure random hex version you have to pay fore, but to retrive any data from a hardisk that has had zeroes stampt across it would take some excessively expensive equipemnt that is only within the price range of govenment agencies!

---

### Post by dragos240 on 2009-05-20
> **logos34 said:**
> Testdisk can.  It locates and restores deleted, lost and damaged partitions.

Dang...

---

### Post by logos34 on 2009-05-20
> **dragos240 said:**
> Dang...

what'd you do--sell a disk like that, just partitions deleted?

---

### Post by dragos240 on 2009-05-20
No. Just that my previous statements were proven false, nothing else. And that deleting partitions is not the safest way of wiping a disk.

---

### Post by Mehall on 2009-05-20
> **logos34 said:**
> 
:lolflag:

You think I'm kidding? they hate dd!

They can't make money off you when dd is used, because every sensible human being will only agree to pay if they recover the data you need, which they can't!!!

---

### Post by tylerspaska on 2009-05-20
i use the shred command

---

### Post by Ceiber Boy on 2009-05-20
> **tylerspaska said:**
> i use the shred command

the shred command?

---

### Post by dragos240 on 2009-05-20
> **tylerspaska said:**
> i use the shred command
Never heard of it. Sounds fun.

---

### Post by logos34 on 2009-05-20
> **dragos240 said:**
> No. Just that my previous statements were proven false, nothing else. And that deleting partitions is not the safest way of wiping a disk.

oh.  Personally, it still amazes how much data can be recovered with the right forensic tools.  I mean, if I was going to plan a crime, I'd definitely stay away from a computer (or burn the drive afterward!). 

The part in the new piece about how hard it is to delete files in windows (there's always a copy somewhere) is so true.  Microsoft is so insecure.  I mean the fact that you can access an NTFS partition without the user/admin password is a joke.

---

### Post by CJ Master on 2009-05-20
[self-advertisment][Article on how to completely format the hard drive.](http://www.ehow.com/how_4999811_completely-format-hard-drive.html)[/self-advertisment]

Regardless, It's true that it's easily recoverable even if you delete your partitions. The sad part is that people sell computers with only wiping out the trash...

---

### Post by schauerlich on 2009-05-20
A sledge hammer is really the only way you can be sure your data is unreadable.

---

### Post by FuturePilot on 2009-05-20
> **logos34 said:**
> 
I mean the fact that you can access an NTFS partition without the user/admin password is a joke.
You can access any file system without a username and password as long as the software can understand the file system. The only way to protect against any information getting pulled off the drive is to encrypt your files. Even at that point though, if someone has physical access to a machine, you're done anyway.

---

### Post by Ceiber Boy on 2009-05-20
> **logos34 said:**
> oh.  Personally, it still amazes how much data can be recovered with the right forensic tools.  I mean, if I was going to plan a crime, I'd definitely stay away from a computer (or burn the drive afterward!). 

The part in the new piece about how hard it is to delete files in windows (there's always a copy somewhere) is so true.  Microsoft is so insecure.  I mean the fact that you can access an NTFS partition without the user/admin password is a joke.

This is a bit off topic but what is the huge secret about NTFS, that MS claims intellectual property for!?
is the complete knowledge of its operation given somewhere on the net?

---

### Post by dragos240 on 2009-05-20
> **logos34 said:**
> oh.  Personally, it still amazes how much data can be recovered with the right forensic tools.  I mean, if I was going to plan a crime, I'd definitely stay away from a computer (or burn the drive afterward!). 

The part in the new piece about how hard it is to delete files in windows (there's always a copy somewhere) is so true.  Microsoft is so insecure.  I mean the fact that you can access an NTFS partition without the user/admin password is a joke.

I can access linux partitions from another drive with mount. It's easy as heck!

---

### Post by logos34 on 2009-05-20
> **Mehall said:**
> You think I'm kidding? they hate dd!

They can't make money off you when dd is used, because every sensible human being will only agree to pay if they recover the data you need, which they can't!!!

yeah, I'm sure they do hate dd.  

Personally, when I plan my next crime (murdering my mother) I intend to use dd to cover my tracks...

---

### Post by logos34 on 2009-05-20
> **FuturePilot said:**
> You can access any file system without a username and password as long as the software can understand the file system. The only way to protect against any information getting pulled off the drive is to encrypt your files. Even at that point though, if someone has physical access to a machine, you're done anyway.

yeah, all of you are right, you can access any fs, of course, what was I thinking, duh

(I think I'm getting 'brainfreeze' from all the ice cream I'm eating right now...)

Okay, but consider this: you CAN access an XP machine to reset the PASSWORD when you've forgotten it.  I've done it, using a hack with a floppy.  The only way to protect your files is to encrypt them, like you say)

---

### Post by FuturePilot on 2009-05-20
> **logos34 said:**
> 

Okay, but consider this: you CAN access an XP machine to reset the PASSWORD when you've forgotten it.  I've done it, using a hack with a floppy.  The only way to protect your files is to encrypt them, like you say)

You can also reset a user's password in Linux too from a live CD using a chroot.

Like I said before, malicious person + physical access = **very bad**
you can do just about anything if you have physical access.

---

### Post by t0p on 2009-05-20
If you want to talk intelligently about secure deletion, it's worth checking out [this site]("http://mirror.href.com/thestarman/asm/mbr/WIPE.html").  It goes into some detail about "wiping", "erasing", "deleting"... explains what these terms mean, and *what they don't mean*.  There's a lot of crap going around about what can and can't be recovered.  And there's the simple fact that **dban** and **dd** are pretty much the last word in effective erasure.

If you want to break out the electron microscopes then the DoD want nothing less than degaussing and/or physical destruction of the disk.  But, as the site says:

> Personally, from the information we've read about such procedures, I consider them to be ridiculous in their extreme measures; hostile forces will always look for the 'weakest link' in obtaining desired information, and we believe it's still easier and quicker to obtain it from open communications and vulnerable human sources than any adequately overwritten hard disk

So chill out peeps!  dd is good enough!

---

### Post by zurack on 2009-05-20
When we assist on an investigation to recover data (known as analysis in the trade) the very first thing is to make a mirror copy of the media (HDD CD USB...) so as not to alter the original media.
Deleting data from Windows is highly unlikely due to the way Windows and installed applications handle the data, the online programs like window washer and east-teck eraser are not going to save anyone as fragments will remain. 

I have seen Dban quoted many times and would agree that program if used correctly would securely prevent any recovery of data. However Dban does not overwrite bad sectors and although the chances of sensitive being written there is very unlikely it still remains a place I would anaylise.

---

### Post by meeples on 2009-05-20
ive heard of the shred command. as far as i know i scrambles the binaries or something like shredding paper so that its unreadable unless you get scientists at it with special magnets.

i think.

---

### Post by t0p on 2009-05-20
> **zurack said:**
> Dban does not overwrite bad sectors and although the chances of sensitive being written there is very unlikely it still remains a place I would anaylise.

According to the periodic disk check Ubuntu does on my machine, there's nothing wrong with my relatively old hard drive.  No bad sectors, no analyzing them!

The real problem with utilities like dban and dd is that they are slow.  So if the Man catches you by surprise, he's got you by the short and curlies!

---

### Post by haroldh7 on 2009-05-20
When I want to get rid of a drive and want to make sure no one gets any data on the hard drive, I use a hammer on the drive so that no one can use it.
Now that is the best way to secure a drive from the wrong hands..

---

### Post by t0p on 2009-05-20
> **haroldh7 said:**
> When I want to get rid of a drive and want to make sure no one gets any data on the hard drive, I use a hammer on the drive so that no one can use it.
Now that is the best way to secure a drive from the wrong hands..

Not if they're coming in through the windows to get you!  A hammer just can't do enough damage in a short space of time.

What you need is thermite charges pre-placed in the drive's casing.  Push a button and up it goes in a brilliant flash!  Best not press it by mistake though...

---

### Post by tylerspaska on 2009-05-21
type "man shred" in the terminal to read up on it, but essentially it overwrites your data 25 times in 1's and 0's and randomly. Then I always have it write with the '-z' option to hide the fact that you've erased or "shreded" the drive, file, or whatever.

Some people are joking that they are using a hammer to destroy the drive, but that really isn't the best way at all. if the platters are wrinkled or even torn in half and someone really wants the data, they can still get it.

You should drill holes in the drive casing, pour in sulfiric acid (you can get it at a hardware store sold as a very powerful drain cleaner, just read the labels) then burn the drive.

---

### Post by Rainstride on 2009-05-21
> **logos34 said:**
> ok, here's another story I saw while over at the Beeb site:


Folks, if you think formatting a drive erases it securely, think again.  And don't even think that simply deleting files (trash) is going to do it.

Even formatted drive partitions can easily be recovered using **[Testdisk]("http://www.cgsecurity.org/wiki/TestDisk") **(avail in the ubuntu repos).

If you want to securely wipe it, you don't even need DBan disk.  The dd command will do same thing:

i though most people knew this. i use webroot eraser, its a disk you can make with the windows program "windows washer". i use that to wipe out the drive completely then install with full disk encryption.(i use 35 wipe gutmann mode.)

---

### Post by monsterstack on 2009-05-21
There are some official US Department of Defense [guidelines]("http://csrc.nist.gov/publications/nistpubs/800-88/NISTSP800-88_rev1.pdf") [nist.gov] [[COLOR="Red"]pdf[/COLOR]] for purging a disk.

But according to [this article]("http://www.usenix.org/publications/library/proceedings/sec96/full_papers/gutmann/index.html") [usenix.org], you need to be a bit more extreme:

> We now have a set of 22 overwrite patterns which should erase everything, regardless of the raw encoding. The basic disk eraser can be improved slightly by adding random passes before and after the erase process, and by performing the deterministic passes in random order to make it more difficult to guess which of the known data passes were made at which point. To deal with all this in the overwrite process, we use the sequence of 35 consecutive writes shown below:

Basically, the only way to be safe is to do the following:

[LIST=1]
[*]Overwrite the disk thirty-five times with a series of different random data-generating algorithms.
[*]Degauss the entire disk using a powerful electromagnet.
[*]Crush the disk with a steamroller.
[*]Use thermite charges to blow it up.
[*]Put the remnants of the disintegrated disk into the heart of a volcano.
[*]Take the magma from the volcano and make it radioactive.
[*]Put the radioactive molten slag on a rocket and send it into the heart of the sun.
[*]Blow up the sun.
[/LIST]

---

### Post by Rainstride on 2009-05-21
> **monsterstack said:**
> There are some official US Department of Defense [guidelines]("http://csrc.nist.gov/publications/nistpubs/800-88/NISTSP800-88_rev1.pdf") [nist.gov] [[COLOR="Red"]pdf[/COLOR]] for purging a disk.

But according to [this article]("http://www.usenix.org/publications/library/proceedings/sec96/full_papers/gutmann/index.html") [usenix.org], you need to be a bit more extreme:



Basically, the only way to be safe is to do the following:

[LIST=1]
[*]Overwrite the disk thirty-five times with a series of different random data-generating algorithms.
[*]Degauss the entire disk using a powerful electromagnet.
[*]Crush the disk with a steamroller.
[*]Use thermite charges to blow it up.
[*]Put the remnants of the disintegrated disk into the heart of a volcano.
[*]Take the magma from the volcano and make it radioactive.
[*]Put the radioactive molten slag on a rocket and send it into the heart of the sun.
[*]Blow up the sun.
[/LIST]

gutmann mode. [http://en.wikipedia.org/wiki/Gutmann_method](http://en.wikipedia.org/wiki/Gutmann_method)

---

### Post by meganox on 2009-05-21
That's pure FUD.  Gutmann 35 pass is a complete waste of time.  Even Peter Gutmann admits this.  His assumptions simply *do not apply* to modern hardware.

[http://www.law.com/jsp/legaltechnology/pubArticleLT.jsp?id=1202429342339](http://www.law.com/jsp/legaltechnology/pubArticleLT.jsp?id=1202429342339)

I read a paper where they tried to read back data that had been overwritten with a single pass of zeros with an electron microscope, and even though they knew *exactly* where on the disk they had written the data they were unable to retrieve it.  Unfortunately I can't find the link.

dd with zeros is good enough.  The only problem is with bad sectors (G-List).  Apparently Secure Erase calls the self-destruct function in modern hard drives to deal with this, so it is the safest software solution.

But for simply wiping a drive in order to sell it, dd is good enough for anyone.

Seriously.

Edit: Gutmann's quote, from the wikipedia article you referenced.

[COLOR=Black]> In the time since this paper was published, some people have treated the 35-pass overwrite technique described in it more as a kind of voodoo incantation to banish evil spirits than the result of a technical analysis of drive encoding techniques. As a result, they advocate applying the voodoo to [PRML]("http://en.wikipedia.org/wiki/PRML") and [EPRML]("http://en.wikipedia.org/w/index.php?title=EPRML&action=edit&redlink=1") drives even though it will have no more effect than a simple scrubbing with random data. In fact performing the full 35-pass overwrite is pointless for any drive since it targets a blend of scenarios involving all types of (normally-used) encoding technology, which covers everything back to 30+-year-old [MFM]("http://en.wikipedia.org/wiki/Modified_Frequency_Modulation") methods (if you don't understand that statement, re-read the paper). If you're using a drive which uses encoding technology X, you only need to perform the passes specific to X, and you never need to perform all 35 passes. For any modern PRML/EPRML drive, a few passes of random scrubbing is the best you can do. As the paper says, "A good scrubbing with random data will do about as well as can be expected". This was true in 1996, and is still true now.[/COLOR]

---

### Post by monsterstack on 2009-05-21
> **meganox said:**
> That's pure FUD.  

I understand your criticism, but since when has FUD been synonymous with "superfluous and redundant"?

---

### Post by meganox on 2009-05-21
It's not.  Gutmann is superfluous and redundant.  Advocating it is FUD.

---

