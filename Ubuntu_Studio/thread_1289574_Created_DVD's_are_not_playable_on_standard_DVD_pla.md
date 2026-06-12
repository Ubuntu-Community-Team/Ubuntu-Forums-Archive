---
title: "Created DVD's are not playable on standard DVD player"
date: 2009-10-12
forum: Ubuntu Studio
---

### Post by redlinethecar on 2009-10-12
Hello all just a little about my computer.  I have a HP DVD740 dvd -+ r/rw DL drive.  I am using a software called DeVeDe to create an ISO file.  After right clicking the ISO and selecting burn to disk the DVD burns fine.  I can then place the DVD into the drive in my computer and it recognizes it as a DVD movie and plays it just fine.  When placing the DVD inside of a standard player (one that has worked fine with burned dvd's only difference is the platform the DVD was created on with is Windows) the player says disc is not readable.  Im guessing there is something that is supposed to go in like a boot sector on the disk or something but im not sure.  Can someone please assist me in this error or point me in the right direction.  I don't want to partition my drive and install windows just to burn video DVD's.  Thank you for your help.

---

### Post by rippin on 2009-10-12
> **redlinethecar said:**
> Hello all just a little about my computer.  I have a HP DVD740 dvd -+ r/rw DL drive.  I am using a software called DeVeDe to create an ISO file.  After right clicking the ISO and selecting burn to disk the DVD burns fine.  I can then place the DVD into the drive in my computer and it recognizes it as a DVD movie and plays it just fine.  When placing the DVD inside of a standard player (one that has worked fine with burned dvd's only difference is the platform the DVD was created on with is Windows) the player says disc is not readable.  Im guessing there is something that is supposed to go in like a boot sector on the disk or something but im not sure.  Can someone please assist me in this error or point me in the right direction.  I don't want to partition my drive and install windows just to burn video DVD's.  Thank you for your help.

File format and content is everything. If it's cooked to an AVI, or like, the computer can deal with it. In fact, with proper codecs, the computer can play any DVD. However, a TV-DVD player needs region to be correct and generally will play only DVD which contain AUDIO_TS & VIDEO_TS files.

BTW, good reading: [http://catb.org/~esr/faqs/smart-questions.html](http://catb.org/~esr/faqs/smart-questions.html)

Wishing you well,

---

### Post by redlinethecar on 2009-10-12
My dvd's created are in dvd format.  My dvd has the AUDIO_TS & VIDEO_TS files but thank you for your help.  As far as the good reading, I will keep that in mind if I plan on posting on a computer hacking board.

---

### Post by rippin on 2009-10-12
> **redlinethecar said:**
> My dvd's created are in dvd format.  My dvd has the AUDIO_TS & VIDEO_TS files but thank you for your help.  As far as the good reading, I will keep that in mind if I plan on posting on a computer hacking board.

And we *still have no idea *about many things concerning your problem: file system, region, player type, OS, kernel, machine, error messages, etc.

Evidently you overlooked this important information ... 

" **[SIZE=3][/SIZE]**
**[When you ask,] be precise and informative about your problem**


[LIST]
[*] Describe the symptoms of your problem or bug carefully and clearly.
[*] Describe the environment in which it occurs (machine, OS, application, whatever). Provide your vendor's distribution and release level (e.g.: “Fedora Core 7”, “Slackware 9.1”, etc.).
[*] Describe the research you did to try and understand the problem  before you asked the question.
[*] Describe the diagnostic steps you took to try and pin down the problem yourself before you asked the question.
[*] Describe any possibly relevant recent changes in your computer or software configuration.
[*] If at all possible, provide a way to *reproduce the problem in a controlled environment*.
[/LIST]
<snip>"

Bye!,

---

### Post by mc4man on 2009-10-12
you may want to post what app was used or how you  burned the disk.

> selecting burn to disk the DVD burns fine.


Incompatibility with a standalone could be from not having the right filesystems set (ISO9660, UDF (1.02) for DVD_VIDEO ) 
or the burning app not burning as DVD_VIDEO

I have tried the linux burning apps and while they *can* work ok prefer to use a full featured iso creator/burner (ImgBurn running in wine

---

### Post by redlinethecar on 2009-10-12
> **rippin said:**
> And we *still have no idea *about many things concerning your problem: file system, region, player type, OS, kernel, machine, error messages, etc.

Evidently you overlooked this important information ... 

" **[SIZE=3][/SIZE]**
**[When you ask,] be precise and informative about your problem**


[LIST]
[*] Describe the symptoms of your problem or bug carefully and clearly.
[*] Describe the environment in which it occurs (machine, OS, application, whatever). Provide your vendor's distribution and release level (e.g.: &#8220;Fedora Core 7&#8221;, &#8220;Slackware 9.1&#8221;, etc.).
[*] Describe the research you did to try and understand the problem  before you asked the question.
[*] Describe the diagnostic steps you took to try and pin down the problem yourself before you asked the question.
[*] Describe any possibly relevant recent changes in your computer or software configuration.
[*] If at all possible, provide a way to *reproduce the problem in a controlled environment*.
[/LIST]
<snip>"

Bye!,

2.6.28-15-generic (#52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009)
AMD Sempron(tm) Processor 3500+
ubuntu 9.04 jaunty
region 1
standalone player types 
1. Magnavox DVD Player DBP170MWX
2. Magnavox DVD Player DP100MW8B
error message output from standalone player: "Disc not playable."
PC: Compaq Presario 1720NX 3 gig RAM and 2 HD 1 both 160gb drives.

---

### Post by redlinethecar on 2009-10-12
> **mc4man said:**
> you may want to post what app was used or how you  burned the disk.



Incompatibility with a standalone could be from not having the right filesystems set (ISO9660, UDF (1.02) for DVD_VIDEO ) 
or the burning app not burning as DVD_VIDEO

I have tried the linux burning apps and while they *can* work ok prefer to use a full featured iso creator/burner (ImgBurn running in wine

Software using to Burn ISO file is Brasero.  But im using ImgBurn through Wine right now so ill see how that goes.

---

### Post by rippin on 2009-10-12
> **redlinethecar said:**
> 2.6.28-15-generic (#52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009)
AMD Sempron(tm) Processor 3500+
ubuntu 9.04 jaunty
region 1
standalone player types 
1. Magnavox DVD Player DBP170MWX

Couldn't find data on this player. ;(

> 2. Magnavox DVD Player DP100MW8B**DVD**

                    
[LIST]
[*]                     Media Type             CD, DVD, CD-R, CD-RW, DVD+R, DVD-R, DVD+RW, DVD-RW
[*]                     Media Load Type             Tray
[*]                     Supported Digital Video Standards             MPEG-2
[*]                     Supported Digital Audio Standards             MP3, PCM
[/LIST]
Try these types of encoding (MPEG-2, MP3), but...

> error message output from standalone player: "Disc not playable."... I think it's file system type which is the conflict. File system is not the same to file type. A file system can be ext3 and the file an MP3. The reader must know how to cope with both.

> PC: Compaq Presario 1720NX 3 gig RAM and 2 HD 1 both 160gb drives.

Thank you for the information. Gave me something to go on. *Really*, thank you!

---

### Post by redlinethecar on 2009-10-12
Sorry the error message is actually "The play feature is not available on this Disc."

---

### Post by rippin on 2009-10-12
> **redlinethecar said:**
> Sorry the error message is actually "The play feature is not available on this Disc."

  "It is possible you are trying to play a disc that is NOT supported by your specific DVD player - This error message usually occurs when you try to play a non DVD-Video complaint disc and the player cannot read it" 

- [http://www.fixya.com/support/t2795705-disc_error_playback_feature_may_not](http://www.fixya.com/support/t2795705-disc_error_playback_feature_may_not)


HTH,

---

### Post by redlinethecar on 2009-10-12
> **rippin said:**
> "It is possible you are trying to play a disc that is NOT supported by your specific DVD player - This error message usually occurs when you try to play a non DVD-Video complaint disc and the player cannot read it" 

- [http://www.fixya.com/support/t2795705-disc_error_playback_feature_may_not](http://www.fixya.com/support/t2795705-disc_error_playback_feature_may_not)


HTH,

I do understand that but what Im not understanding is there are dvd's created in windows that work perfectly fine on that player.  So I just figured it had to be something about Linux.  Maybe some sort of compatibility issue or something.  I don't know I'm almost to the point of partitioning my drive and putting XP and ubuntu on there and solve the problem like that.

---

### Post by rippin on 2009-10-12
> **redlinethecar said:**
> I do understand that but what Im not understanding is there are dvd's created in windows that work perfectly fine on that player.  So I just figured it had to be something about Linux.  Maybe some sort of compatibility issue or something.  I don't know I'm almost to the point of partitioning my drive and putting XP and ubuntu on there and solve the problem like that.

I'm with you on that. I've used Linux exclusively since 2000. Tried to make a DVD for my TV DVD player from an AVI file using the software and steps I read on a web page but only the computer could play it. I'll never get MS Windows, so I let it go for what is was, in my eyes anyway, as not *that *important.

Because I can't be any further help on this topic, I wish you well.

---

### Post by rotary12 on 2009-10-12
> **redlinethecar said:**
> Hello all just a little about my computer.  I have a HP DVD740 dvd -+ r/rw DL drive.  I am using a software called DeVeDe to create an ISO file.  After right clicking the ISO and selecting burn to disk the DVD burns fine.  I can then place the DVD into the drive in my computer and it recognizes it as a DVD movie and plays it just fine.  When placing the DVD inside of a standard player (one that has worked fine with burned dvd's only difference is the platform the DVD was created on with is Windows) the player says disc is not readable.  Im guessing there is something that is supposed to go in like a boot sector on the disk or something but im not sure.  Can someone please assist me in this error or point me in the right direction.  I don't want to partition my drive and install windows just to burn video DVD's.  Thank you for your help.

you said [I am using a software called DeVeDe to create an ISO file.]why are you using DeVeDe,is it an .avi file you downloaded or a dvd you are trying to copy. if its an .avi,you have to convert it to dvd,if its a dvd you are trying to copy,right click the disk and select copy disk or use K9copy
check you dvd player for the word  Divx,if it says Divx burn the .avi as data,and it works. i use on my dvd and PS3

---

### Post by kayosiii on 2009-10-13
I have had success using QDVDAuthor and K3B...
I use this combo to create videos for live shows. I did have a bug a while back that meant that the movie would not play back on a Windows or Mac based computer but it worked fine on standalone players.

I would suggest trying to burn it in K3B first (the files as a video project) and if that fails - try generating the files using QDVDAuthor.

---

### Post by mikechant on 2009-10-21
You shouldn't need to do any special setup etc. or pre-convert any videos when using DeVeDe. In my experience I throw any old videos at it and it produces an iso that when burned plays on any DVD player.
Are you using the exact same blank disc brand with the DeVeDe isos as you were in windows?

---

### Post by redlinethecar on 2010-01-23
Well unfortunately sometimes I can be somewhat of an idiot.  Figured out the problem and kinda embarrassed to say.  It was actually the format of the DVD.  As soon as I switched it from PAL to NTSC it appears all of my dvd discs work.  Sorry for the wasted thread but really do appreciate the help and support on this forum.  It's always helped me out.  Thank you.

---

### Post by chinneths on 2010-04-29
I made the same mistake burning in PAL, so this post is very useful, thanks all!:guitar:

---

### Post by chinneths on 2010-04-29
But I have encountered a problem:

Unable to mount DVDVIDEO
 Error mounting: mount exited with exit code 32: mount:
 block device /dev/sr0 is write-protected, mounted read-only
 mount: /dev/sr0: can't read superblock

---

### Post by chinneths on 2010-04-29
I have been using DeVeDe to make the iso file and then just right clicking iso file and writing it to disc? Can anyone help me out? When I used PAL it burnt the DVD, but when I changed to NTSC I received the above error mesage!

---

### Post by jeebustrain on 2010-05-10
> **mikechant said:**
> You shouldn't need to do any special setup etc. or pre-convert any videos when using DeVeDe. In my experience I throw any old videos at it and it produces an iso that when burned plays on any DVD player.
Are you using the exact same blank disc brand with the DeVeDe isos as you were in windows?



This - I have only used DeVeDe a few times, but have never had problems. I have had a LOT more problems dealing with disc inconsistencies when trying to play on hardware dvd players than I've had with software issues. As long as you are choosing the correct encoding setting (NTSC or PAL), and using non-crappy discs, it should just work.

---

