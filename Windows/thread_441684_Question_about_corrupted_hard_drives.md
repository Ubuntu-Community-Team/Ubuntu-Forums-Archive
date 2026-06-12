---
title: "Question about corrupted hard drives"
date: 2007-05-12
forum: Windows
---

### Post by brennydoogles on 2007-05-12
I set up a dual boot on my Mother in law's home computer several months ago with Edgy and Windows XP. A few weeks ago, her windows failed to boot, and it appears that the drive is corrupted. Today I found Two programs to help me recover files from her windows partition to her linux partition ([Testdisk]("http://www.cgsecurity.org/wiki/TestDisk") and [PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec")) . I am not sure how to use either program, but I am going to attempt to figure out tonight. If anyone is familiar, any help would be appreciated. My main question however, is what to do after I recover all of the data that I can. I will most likely end up formatting the drive, but it is old, and I fear that this corruption is a sign that it is dying. Is there a way to make an exact copy of that drive onto another drive, and have the computer boot with the new drive in the place of the old windows drive?? Any help would be greatly appreciated.

---

### Post by starcraft.man on 2007-05-12
> **brennydoogles said:**
> I set up a dual boot on my Mother in law's home computer several months ago with Edgy and Windows XP. A few weeks ago, her windows failed to boot, and it appears that the drive is corrupted. Today I found Two programs to help me recover files from her windows partition to her linux partition ([Testdisk]("http://www.cgsecurity.org/wiki/TestDisk") and [PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec")) . I am not sure how to use either program, but I am going to attempt to figure out tonight. If anyone is familiar, any help would be appreciated. My main question however, is what to do after I recover all of the data that I can. I will most likely end up formatting the drive, but it is old, and I fear that this corruption is a sign that it is dying. Is there a way to make an exact copy of that drive onto another drive, and have the computer boot with the new drive in the place of the old windows drive?? Any help would be greatly appreciated.

I haven't used either of those programs, but I do believe I know a program that is almost guaranteed to fix this problem. Its called Spinrite. I've actually used it twice when I had serious errors on my OS partition and it has fixed it both times. It works on any OS becauses it passes under everything and works right at the data level on the drive. More info is available [here.]("http://www.grc.com/sr/spinrite.htm") Now, I know your gonna ask me but its 89$ I think, well, there are ways to get it for free *cough*torrent *cough* and while I don't really want you to do that, there is no DRM on his product. In fact, people have actually used the copy without paying and then when it worked so perfectly they went out and bought a copy or two to support him. It's a marvellous program, and I keep a copy with me whenever I go anywhere :)

That said, choice is up to you what ya want. I vote spin rite though, whether ya want it or not is up to you (however you choose to get it >.>).

---

### Post by brennydoogles on 2007-05-12
> **starcraft.man said:**
> I haven't used either of those programs, but I do believe I know a program that is almost guaranteed to fix this problem. Its called Spinrite. I've actually used it twice when I had serious errors on my OS partition and it has fixed it both times. It works on any OS becauses it passes under everything and works right at the data level on the drive. More info is available [here.]("http://www.grc.com/sr/spinrite.htm") Now, I know your gonna ask me but its 89$ I think, well, there are ways to get it for free *cough*torrent *cough* and while I don't really want you to do that, there is no DRM on his product. In fact, people have actually used the copy without paying and then when it worked so perfectly they went out and bought a copy or two to support him. It's a marvellous program, and I keep a copy with me whenever I go anywhere :)

That said, choice is up to you what ya want. I vote spin rite though, whether ya want it or not is up to you (however you choose to get it >.>).

Do you know how large the program is, and if it will run from Ubuntu?? I need to try my best to get this HD recovered (at least partially) by tonight.

---

### Post by starcraft.man on 2007-05-12
> **brennydoogles said:**
> Do you know how large the program is, and if it will run from Ubuntu?? I need to try my best to get this HD recovered (at least partially) by tonight.

The program is tiny, its written is Assembler (yes, that ancient language). Its only about 160k, its actually coded to run in windows. What it does is generate an ISO for either a floppy or CD to boot to. You boot to the program and then you can choose what diagnostic you need.

My advice is if you need this fixed right away, go get a torrent of it (if I'm gonna tell ya to do that I guess I better send ya to isohunt and tell ya to search for "spinrite"). It will contain both ISOs, so you can just burn it (if you buy from gibson, I don't think he gives you ISOs just the generator that only works with Windows). Then just put it on a floppy or cd (i prefer CD as floppies are almost dead now) and boot to it. You can find a guide to how to use it in the torrent.

Then, assuming it fixes your problem, I would advise you to buy it from him (a license, since you already have a copy). It's his only source of revenue and it is a great program, feel free to write him a note explaining why you needed his program in the testimonials, and don't worry about telling him you pirated a copy, he actually DOESN'T mind, imagine that :D

Also, listen to security now if you can, good podcast :)

Hope that fixes it for ya.

---

### Post by brennydoogles on 2007-05-12
> **starcraft.man said:**
> The program is tiny, its written is Assembler (yes, that ancient language). Its only about 160k, its actually coded to run in windows. What it does is generate an ISO for either a floppy or CD to boot to. You boot to the program and then you can choose what diagnostic you need.

My advice is if you need this fixed right away, go get a torrent of it (if I'm gonna tell ya to do that I guess I better send ya to isohunt and tell ya to search for "spinrite"). It will contain both ISOs, so you can just burn it (if you buy from gibson, I don't think he gives you ISOs just the generator that only works with Windows). Then just put it on a floppy or cd (i prefer CD as floppies are almost dead now) and boot to it. You can find a guide to how to use it in the torrent.

Then, assuming it fixes your problem, I would advise you to buy it from him (a license, since you already have a copy). It's his only source of revenue and it is a great program, feel free to write him a note explaining why you needed his program in the testimonials, and don't worry about telling him you pirated a copy, he actually DOESN'T mind, imagine that :D

Also, listen to security now if you can, good podcast :)

Hope that fixes it for ya.

Sweet, I am downloading it now (with the full intent of buying it, because this guy is saving my life :o) ) but I was wondering... how could I make a bootable floppy of it?? I don't have any CDr's handy, but I have a slew of handy Floppies that I could use if possible.

---

### Post by brennydoogles on 2007-05-13
ok, so spinrite looked promising, but didn't fix anything. I am trying PhotoRec right now, so i will post back in 8-10 hours when it finishes.

---

### Post by smoker on 2007-05-13
> Is there a way to make an exact copy of that drive onto another drive, and have the computer boot with the new drive in the place of the old windows drive?? Any help would be greatly appreciated.
Reply With Quote

there is a great free app called 'driveimagexml' which can make an exact copy of your windows partition, and restore this on another drive, please read the instructions on the use of the app, it is available here:
[http://www.runtime.org/dixml.htm](http://www.runtime.org/dixml.htm)

if you suspect it is the drive that is falling (other than os corruption), the best thing you can do is remove it as soon as possible, and slave it to another machine, everytime you try to boot that drive may make the file system and data more unreadable and recoverable. once you have done this, there are apps available from most hard drive manufacturers that can copy the data, bit by bit, to a new drive of the same size or larger. if you check out the support page on the hard drive that is faulty, and/or the make of hard drive you want the data transferred to, you should be able to download and make a bootable floppy or cd or such an app.

once you have the data safely off the failing drive, then you can check the drive's integrity with the proper diagnostic tool that most manufacturers also have available to freely download for this purpose. there is also a great rescue cd called the 'ultimate boot disk' which includes a wide range of hard drive diagnostic apps, it is available here: [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

best of luck

---

### Post by hobieone on 2007-05-13
is the drive making a consistant taping noise? usaually when a drive is failing it will make a loud tapping noise. and normally you wouldn't be able to aceess any of the partitions.

only reason i asked is i had experienced a similar problem on one of my compter. it turned out the drive was fine. and my win xp  had just been updated and it some how mess up the mbr on the hard drive and resulted in booting to ubuntu only and botting to windows causeing an error.  only way to fix it was to install windows completely then fix grub  to access linux.

---

