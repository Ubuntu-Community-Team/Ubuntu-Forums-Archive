---
title: "Hi looking for something to completely wipe a HD..."
date: 2009-02-02
forum: The Cafe
---

### Post by cptrohn on 2009-02-02
Hi, I am looking for a good program/software to completely wipe a HD...

I am in the process of buying 2 used notebooks to give to my niece and nephew to use to start learing how to use computers early  (with a linux installation, they have all their lives to use windoze later)

But since the laptops I am looking to buy are inexepensive and don't have much in the way of resources (I'm not rich, by any means) I am planning on installing Puppy Linux on them in the HD..(I would let them boot from the CD, but with young kids the CD's will get screwed up without a doubt) These notebooks have windows on them but no recovery software with them....

Is there something that would wipe them completely just from a boot?  I would also like to be able to do this with other old notebooks that I could get for cheap and then donate them to local school systems for underpriveledged kids to use as well and get linux into more young users hands at the same time..

any ideas on something like this?

---

### Post by kevin11951 on 2009-02-02
> **cptrohn said:**
> Hi, I am looking for a good program/software to completely wipe a HD...

I am in the process of buying 2 used notebooks to give to my niece and nephew to use to start learing how to use computers early  (with a linux installation, they have all their lives to use windoze later)

But since the laptops I am looking to buy are inexepensive and don't have much in the way of resources (I'm not rich, by any means) I am planning on installing Puppy Linux on them in the HD..(I would let them boot from the CD, but with young kids the CD's will get screwed up without a doubt) These notebooks have windows on them but no recovery software with them....

Is there something that would wipe them completely just from a boot?  I would also like to be able to do this with other old notebooks that I could get for cheap and then donate them to local school systems for underpriveledged kids to use as well and get linux into more young users hands at the same time..

any ideas on something like this?

DBAN: [http://www.dban.org/](http://www.dban.org/)

You boot into it, follow on screen instructions, and it will wipe all the data off the hdd, permanently.

---

### Post by bash on 2009-02-02
I second [[COLOR="Black"]_kevin11951_[/COLOR]](http://ubuntuforums.org/member.php?u=278557) suggestions of DBAN. Used it on quite a few old machines myself and it's a simple and reliable tool that gets the job done.

---

### Post by cptrohn on 2009-02-02
GREAT.

Thank you very much Kevin, thats just what I was looking for.

Awesome...  The Linux community is great.  I just switched from windows a month or so ago and haven't looked back since.. thanks alot!

---

### Post by NewJack on 2009-02-02
> **kevin11951 said:**
> DBAN: [http://www.dban.org/](http://www.dban.org/)

You boot into it, follow on screen instructions, and it will wipe all the data off the hdd, permanently.

+1.  Used this quite a few times.  Works like a charm

---

### Post by MaxIBoy on 2009-02-02
First, unmount the hard drive. Then, run this:
```
dd if=/dev/urandom of=/dev/sda #or whatever the name of the hard drive is
```That will fill the hard drive with randomly generated binary data.

If you want to be sure that not even the FBI can get at your data, you can run this twice.

---

### Post by bash on 2009-02-02
> **MaxIBoy said:**
> First, unmount the hard drive. Then, run this:
```
dd if=/dev/urandom of=/dev/sda #or whatever the name of the hard drive is
```That will fill the hard drive with randomly generated binary data.

If you want to be sure that not even the FBI can get at your data, you can run this twice.

Actually urandom is not completly random. You would have to use /dev/random for that. And even then to be completly safe (paranoid tin hat style) you should wipe it a couple of times. Except this will take A LOT of time and if you want to do it for you whole harddrive you would have to run it from a Live CD which would create a lot of unneeded ressource usage. Instead you could just run DBAN which does all the same, but is a lot smaller and lighter.

---

### Post by boltz on 2009-02-07
When using dban, use the **PRNG stream** with 1 pass and not the quick option. 3 passes if you're paranoid but-

A single wipe will make drives impossible to read even with electonic microscope securityfocus.com/brief/888?ref=rss

also this is interesting

[http://16systems.com/zero/](http://16systems.com/zero/)

BTW the latest Dban will not work on some laptops, you just recieve a Non-fatal Error after a few minutes

so instead use the beta version on this page
[http://sourceforge.net/project/showfiles.php?group_id=61951](http://sourceforge.net/project/showfiles.php?group_id=61951)

---

### Post by Jags_FL on 2009-02-07
yes, I would say the same... DBAN 

Infact after using DBAN I noticed Win & Ubuntu were little more responsive than before :D

---

### Post by MaxIBoy on 2009-02-07
> **bash said:**
> Actually urandom is not completly random. You would have to use /dev/random for that. /dev/random is slower than /dev/urandom by a long shot. /dev/urandom is close enough. After all, you're not encrypting the garbage you're generating for your hard drive-- you're overwriting the non-garbage with garbage. Non-cryptographically-secure garbage is still garbage. > And even then to be completly safe (paranoid tin hat style) you should wipe it a couple of times. Except this will take A LOT of time and if you want to do it for you whole harddrive you would have to run it from a Live CD which would create a lot of unneeded ressource usage. Choose a distro like DSL that can run entirely from RAM. It will actually be faster than if you're running off a hard drive, even when only erasing a single partition, because that way, nothing is being read from anywhere on the hard drive, so more hard drive rotations are devoted to writing garbage.> Instead you could just run DBAN which does all the same, but is a lot smaller and lighter.
That looks cool, I hadn't heard of that before. Thanks!

---

### Post by |{urse on 2009-02-07
A friend of mine who works on special us govmt projects turned me on to dban, great tool! 
+10

---

### Post by jomiolto on 2009-02-08
You can also use shred:

```
shred -n xxx /dev/sd###
```

will overwrite the whole sd### partition/disk with random data for xxx times (the default is 25, which is more than a little paranoid and would take half an eternity on a large disk).

---

### Post by handy on 2009-02-08
Does anyone know of any software that enables low level formatting of HDD's?

You used to be able to do it from the BIOS of some machines in years gone by, some motherboard manufacturers used to supply a tool on their driver disk as well.

I've lost touch with how you can do a LLF in these modern times to modern drives? ;-)

By the way, a LLF is not going to make the data on the drive unrecoverable, this topic just bought the question to mind & I thought that perhaps some of the contributors may know.

---

### Post by DualBooterWhat on 2009-02-08
> **MaxIBoy said:**
> First, unmount the hard drive. Then, run this:
```
dd if=/dev/urandom of=/dev/sda #or whatever the name of the hard drive is
```That will fill the hard drive with randomly generated binary data.

If you want to be sure that not even the FBI can get at your data, you can run this twice.

... Why would you not want the FBI to get your data?

---

### Post by handy on 2009-02-08
> **DualBooterWhat said:**
> ... Why would you not want the FBI to get your data?

Why would a person want to make the deleted data on a drive unrecoverable?

---

### Post by jomiolto on 2009-02-08
> **DualBooterWhat said:**
> ... Why would you not want the FBI to get your data?

Because it's personal. I don't mind them looking at my lolcat collection (yes, that's what it's called these days :P ) or even at my programming projects (they are going to be open source anyway), but I would not want *anyone* looking at my more personal stuff.

Besides, it's not like they allow me to look at *their* stuff, so I guess it's only fair... ;)

---

### Post by MaxIBoy on 2009-02-08
> **DualBooterWhat said:**
> ... Why would you not want the FBI to get your data?
Why would you want to spend at least 10 hours (for a medium-big hard drive) while you make sure that all your captioned cat photos and bookmarks are well-hidden from the FBI? 

EDIT: dang, misunderstood you. 


My answer is, I don't care about any of the stuff on my hard drive right now. I don't keep private data on there anyway. But there's always the possibility that must be kept open.

---

### Post by boltz on 2009-02-08
Regarding law enforcement and where dban would of helped

I have read cases where a person has unknowingly and mistakenly clicked on a link that leads them to kiddy porn (CP), this person has then clicked away and thought nothing of it, and did not save the image or return but yet the browser left an incriminating thumbnail image on his HDD and he was charged and convicted (i think it was the U.S) and i also know of a case in France.

Whether or not it was right for them to be convicted along with the stigma attachment is a matter of opinion.

---

### Post by Stalker72 on 2009-02-08
I recommend Darik's Boot And Nuke. It owns.

Stalker72

---

### Post by Metallion on 2009-02-09
> **jomiolto said:**
> Because it's personal. I don't mind them looking at my lolcat collection (yes, that's what it's called these days :P ) or even at my programming projects (they are going to be open source anyway), but I would not want *anyone* looking at my more personal stuff.

C'mon... Just admit that you're talking about your porn collection. :)

---

### Post by Niksko on 2009-02-09
DBAN all the way. I'd just get the Ultimate Boot CD though. Really handy and has many uses, not just wiping hard drives.

Interestingly, I read somewhere that the DoD used to do something like 12 wipes and then would grind the hard drives into powder and pour it into concrete used for building foundations. Apparently now this technique is obsolete. The only current method for disposing of Secret or Top Secret digital data is now either physical destruction or degaussing. Degaussing completely removes the magnetic field of the disk platters, and also removes special data (that is not normally erased) that gives instructions to the disk head. This data can only be put on the disk in the factory, so without this the hard drive is essentially unusable.

-Nik

---

### Post by mips on 2009-02-09
> **handy said:**
> Does anyone know of any software that enables low level formatting of HDD's?

You used to be able to do it from the BIOS of some machines in years gone by, some motherboard manufacturers used to supply a tool on their driver disk as well.

I've lost touch with how you can do a LLF in these modern times to modern drives? ;-)

By the way, a LLF is not going to make the data on the drive unrecoverable, this topic just bought the question to mind & I thought that perhaps some of the contributors may know.


Drives have changed over the years and you cannot do a 'real' LLF anymore on modern hard drives. LLF is performed at the factory and the user has no access to that part/info of the drive. The LLF utils you get these days don't actually perform a LLF.

[http://en.wikipedia.org/wiki/Disk_formatting](http://en.wikipedia.org/wiki/Disk_formatting)
[http://www.ariolic.com/activesmart/low-level-format.html](http://www.ariolic.com/activesmart/low-level-format.html)
Google: HD low level format

---

### Post by kaldor on 2009-02-09
Gparted is what I use. It is a live CD partitioner running on Gnome.

---

### Post by billgoldberg on 2009-02-09
Just use dd with as source /dev/urandom or /dev/zero.

I've read /dev/urandom is better if you're wiping for security reasons.

--

A question.

Let's say I format my Windows 7 to an ext4 partition and install Ubuntu on it.

Would "people" still be possible to retrieve files from it that were on Windows? 

I don't think so. But I'm a data recovery newbie (actually, know nothing about it).

---

### Post by mips on 2009-02-09
> **billgoldberg said:**
> 
A question.

Let's say I format my Windows 7 to an ext4 partition and install Ubuntu on it.

Would "people" still be possible to retrieve files from it that were on Windows? 


Yes, but it depends on a few variables. Just because you format a drive or change the fs type does not mean the data is gone.

---

### Post by boltz on 2009-02-09
> **billgoldberg said:**
> Just use dd with as source /dev/urandom or /dev/zero.

I've read /dev/urandom is better if you're wiping for security reasons.

--

A question.

Let's say I format my Windows 7 to an ext4 partition and install Ubuntu on it.

Would "people" still be possible to retrieve files from it that were on Windows? 


Formatting is differnt from wiping so it could still be possible to recover data

---

### Post by handy on 2009-02-09
> **mips said:**
> Drives have changed over the years and you cannot do a 'real' LLF anymore on modern hard drives. LLF is performed at the factory and the user has no access to that part/info of the drive. The LLF utils you get these days don't actually perform a LLF.

[http://en.wikipedia.org/wiki/Disk_formatting](http://en.wikipedia.org/wiki/Disk_formatting)
[http://www.ariolic.com/activesmart/low-level-format.html](http://www.ariolic.com/activesmart/low-level-format.html)
Google: HD low level format

Thanks for the info' mips.

The reason I asked, is I have an 80Gb Deathstar that I thought I might try to resurrect with a LLF. :-)

---

### Post by aschwerin.moses on 2009-02-09
We can do a wipe out even using Windows 98 boot disk or win xp disk right... so whats the difference between DBAN and FDISK (in windows)...

---

### Post by LookTJ on 2009-02-09
> **aschwerin.moses said:**
> We can do a wipe out even using Windows 98 boot disk or win xp disk right... so whats the difference between DBAN and FDISK (in windows)...
Again, there is a difference between wiping/erasing and formatting a hard disk.

---

### Post by steveneddy on 2009-02-09
My favorite for many years:

[http://www.killdisk.com/](http://www.killdisk.com/)

---

### Post by mips on 2009-02-10
> **handy said:**
> 
The reason I asked, is I have an 80Gb Deathstar that I thought I might try to resurrect with a LLF. :-)

What's wrong with the drive? They suffered from about 4 different issues from bad pcb, corrupted nvram etc.

These guys use to have a tutorial but I cannot find it on their new site layout, [http://www.salvationdata.com/](http://www.salvationdata.com/)
[http://www.hitachigst.com/hdd/support/download.htm](http://www.hitachigst.com/hdd/support/download.htm)

---

### Post by handy on 2009-02-10
> **mips said:**
> What's wrong with the drive? They suffered from about 4 different issues from bad pcb, corrupted nvram etc.

These guys use to have a tutorial but I cannot find it on their new site layout, [http://www.salvationdata.com/](http://www.salvationdata.com/)
[http://www.hitachigst.com/hdd/support/download.htm](http://www.hitachigst.com/hdd/support/download.htm)

I don't know what's wrong with it? I haven't even gone to see if it is still here.  Every now & then I get ruthless & give or toss stuff out.  

I can't believe how much crap we accumulate, & I have been trying not to accumulate it for years. :-|

---

