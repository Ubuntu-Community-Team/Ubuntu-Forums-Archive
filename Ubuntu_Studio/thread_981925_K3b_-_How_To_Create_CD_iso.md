---
title: "K3b - How To Create CD iso?"
date: 2008-11-14
forum: Ubuntu Studio
---

### Post by mapes12 on 2008-11-14
I have just installed K3b as it seems a good CD burning application. I have a music CD that I want to make an iso image from as a backup for the original. I've been all over the options in K3b but can't find a way to do this?

Or, if I should be using a different application suggestions would be very welcome.

Mark

---

### Post by magump on 2008-11-14
If you are just trying to make a copy of your music CD, when you open K3b, under the Tools menu, click on Copy CD.  If you want to make an iso image, you  must have a .iso file to make an image of.  If you have an .iso image, the burn dvd iso image is also under the tools menu.  Hope this helps as I am trying to completely understand what it is you are doing with a music CD.

---

### Post by mapes12 on 2008-11-14
> I am trying to completely understand what it is you are doing with a music CD.

Sorry, perhaps I didn't explain it very well.

I'm trying to create an .iso image/file of my music CD so that I can keep it on my machine in case the CD becomes damaged and I can then just simply burn me another one from the .iso image in the future.

> click on Copy CDI tried that but half way thru it call for blank CD-R to write to. I don't want a duplicate CD, just the .iso in case I need to create a new CD in the future.

---

### Post by binbash on 2008-11-14
i dont have k3b installed, i am pretty sure k3b does this but i am using acetoneiso to do this (and also mounting cds etc).You can create iso image from cds or folders

---

### Post by magump on 2008-11-14
Have you thought about using K3b to "rip" your audio cd into a folder on your hard drive, then burn the audio tracks to a CD to make an audio CD?  That is what I have done in the past and also transfered the audio tracks to my mp3 player.

---

### Post by thorgal on 2008-11-14
select Copy CD and turn on option "Only create image" in the popped up window (settings frame).

---

### Post by mapes12 on 2008-11-14
> but i am using acetoneiso to do this Sounds good! I've Googled it but the links I've found are all dead. And I can't find it in the Ubuntu repo's.

> Have you thought about using K3b to "rip" your audio cd into a folder on your hard drive, then burn the audio tracks to a CD to make an audio CD? That is what I have done in the pastAgreed, and appears easy to do. But an .iso image would be just good for me. I've Googled for hours and got no where with this.

> select Copy CD and turn on option "Only create image" in the popped up window (settings frame). Tried this but it creates an .iso file and a .toc file. Neither of which are recognised by K3b to burn a blank CD.

There are loads of posts all over the web referring to a "dd" command line similar to this thread: [http://ubuntuforums.org/showthread.php?t=657648](http://ubuntuforums.org/showthread.php?t=657648) but it plain does not work.:confused:

BTW - I'm running 8.04 LTS.

---

### Post by thorgal on 2008-11-14
how do you mean it does not burn the created iso ? it should.
In any case, there's another option in the same setting window : the Copy Mode. Set it to clone.

---

### Post by binbash on 2008-11-14
[http://www.getdeb.net/app/AcetoneISO](http://www.getdeb.net/app/AcetoneISO)

---

### Post by mapes12 on 2008-11-15
Thanks Binbash. I've installed it. But when I run it, Conversion>Generate ISo from CD/DVD, a window pops up "Please note that this tool only works for normal DATA CD/DVD. It won't work with Audio CD and Game CopyProtected cd's".

> how do you mean it does not burn the created iso ? it should.Well it doesn't.> In any case, there's another option in the same setting window : the Copy Mode. Set it to clone.Tried that and it creates a file with the extension .img I've tried every variable in that window of K3b.

So I'm no further forward in my quest to generate an ISO from my music CD ](*,) 

Can anyone help please :confused:

---

### Post by rykel on 2009-12-23
Hi all,


I am also getting frustrated after more than an hour of trying to find out how in the world I can copy an audio CD into a .iso.

Brasero and k3b both do not seem to have the .iso option.

Has this got anything to do with the disc being an audio CD?

Thanks for further helping.

---

### Post by galactica48 on 2010-11-21
> **mapes12 said:**
> I have just installed K3b as it seems a good CD burning application. I have a music CD that I want to make an iso image from as a backup for the original. I've been all over the options in K3b but can't find a way to do this?

Or, if I should be using a different application suggestions would be very welcome.

Mark
This is how to create an iso image from any folder you wish:

Open K3b
Select NEW DATA PROJECT
Drag all folders that you wish to create iso image into the bottom left window
Select BURN
Thick ONLY CREATE IMAGE option
Choose destination directory for easy find
Click START
Thats all
Galactica48

---

### Post by RaumTrug on 2010-11-21
haven't had to do that myself yet, but...

but there's a kde prog called "kiso" in the repos, guess what it's good for ;)

also you could try to extract the cd data directly from the drive's block device to an iso file as an iso file is just like an 1:1 image of the data burned to the cd. you could do this with the shell command "dd", for example like this (not tested):

```

dd if=/dev/cdrom of=~/myimage.iso

```the "if=" part must be the device of the drive with the cd, the "of=" part the file you want to save into.

---

### Post by bulletxt on 2010-11-22
You can't and never will be able to create an ISO-9660 image of a CD-Audio.

You can however create a raw image and then burn it passing the TOC file.

You can use AcetoneISO to do your CD-Audio backup. 

[http://www.acetoneteam.org](http://www.acetoneteam.org)

---

### Post by SeijiSensei on 2010-11-22
KDE makes it easy to create a single file that contains an entire CD's content.  Insert the CD, then open it with dolphin.  You'll see a variety of folders appear.  These aren't really on the CD though; they are "virtual" folders created using KDE's kio-slave technology.  If you open the "Full CD" folder, you'll find multiple versions of the entire CD in different formats.  I generally use FLAC because it's smaller than WAV, yet still loss-less.  Just drag one of these CD images to your preferred archive location.

True, you won't get an ISO version, but you'll get a complete backup of the CD in a very convenient format.

---

