---
title: "How Windows Decided To Destroy My Linux Files"
date: 2007-02-18
forum: Windows
---

### Post by raldz on 2007-02-18
Yes, Windows just deleted my files in my external Linux drive... automatically! This is just another reason why _I_ shouldn't trust Windows anymore. See the video on how it looks like.  [click here for the full story plus video]("http://raldztech.blogspot.com/2007/02/how-windows-decided-to-destroy-my-linux.html")

---

### Post by 454redhawk on 2007-02-18
> **raldz said:**
> Yes, Windows just deleted my files in my external Linux drive... automatically! This is just another reason why _I_ shouldn't trust Windows anymore. See the video on how it looks like.  [click here for the full story plus video]("http://raldztech.blogspot.com/2007/02/how-windows-decided-to-destroy-my-linux.html")

I fail to see how this is a windows problem. Sounds lika a FS-Driver to me. There are a multitude of problems with FS-Driver and USB

Without that driver giving windows the ability to write nothing would have happened. You screwed the pooch.

Another windows bashing thread. Move on already.

---

### Post by some_random_noob on 2007-02-18
> **454redhawk said:**
> I fail to see how this is a windows problem. Sounds lika a FS-Driver to me. There are a multitude of problems with FS-Driver and USB

Without that driver giving windows the ability to write nothing would have happened. You screwed the pooch.

Another windows bashing thread. Move on already.
Windows bashing thread? I'd be pretty pissed off if Windows deleted all my Linux stuff. Probably was Windows. I have no idea what problems there'd be with FS-Driver and USB stuff, since Windows was scanning it I think it's obvious who to blame.

---

### Post by raldz on 2007-02-18
@454redhawk
I'm not bashing Windows.. I use it 10 percent of the time... I just don't trust it anymore (actually I don't have any important files stored in an NTFS or FAT partition, because I don't really trust it).. it seems that it has a brain of his own deleting files without my permission... not a big deal, I have 2 backups of all my files mirrored in different hard drives... I just find it funny when I realize that it is deleting my files.... this could be trouble to some people who doesn't have backups... especially if it contains critical files...

---

### Post by insane_alien on 2007-02-18
Umm, any OS that deleted files from a drive without consent is deserving of a bashing. Imagine that happened at a major bank or stock exchange, even though they probably have oodles of hourly backups or something it would cause chaos.

Its not a sign of a professional OS more like the hack and slash OS that MS origionally purchased way way back when 8-bit was cutting edge.

---

### Post by Trebuchet on 2007-02-18
Yes, I always videotape any action I take on my machine too. Never know when I might record another opportunity to bash Windows and finally convince those millions of benighted souls still using The Crap From Redmond.  ;)

---

### Post by highneko on 2007-02-18
I hear baby sound effects! Windoze is targeting children now!! :lolflag:

---

### Post by manmower on 2007-02-18
The driver for the file system is a likely culprit, not Windows. You're the one who's to blame for using software that comes with no warranty whatsoever and then trying to pin it on Windows.

---

### Post by yabbadabbadont on 2007-02-18
> **insane_alien said:**
> Umm, any OS that deleted files from a drive without consent is deserving of a bashing. Imagine that happened at a major bank or stock exchange, even though they probably have oodles of hourly backups or something it would cause chaos.

Its not a sign of a professional OS more like the hack and slash OS that MS origionally purchased way way back when 8-bit was cutting edge.

Just to pick nits :)  Most major banks (minor ones too) only do nightly backups.  They generally rely on different types of hardware raid to preserve things during the day.  (Actually, they *should* do nightly backups...  you wouldn't believe the stuff that goes on at even very large banks :roll:)

---

### Post by raldz on 2007-02-18
> **manmower said:**
> The driver for the file system is a likely culprit, not Windows. You're the one who's to blame for using software that comes with no warranty whatsoever and then trying to pin it on Windows.

yup.. probably.. but you can't blame people to use this software because Windows doesn't know how to read Linux file systems... while in Linux, we could read-write into Windows file systems without so much problem...  so, it's either Windows is doing some things wrong, or Linux is doing some things right... or both...

---

### Post by raldz on 2007-02-18
> **insane_alien said:**
> Umm, any OS that deleted files from a drive without consent is deserving of a bashing. Imagine that happened at a major bank or stock exchange, even though they probably have oodles of hourly backups or something it would cause chaos.

Its not a sign of a professional OS more like the hack and slash OS that MS origionally purchased way way back when 8-bit was cutting edge.

exactly my point... Windows didn't asked my permission... it thinks that the files are corrupt, therefore deleting it automatically...

---

### Post by 454redhawk on 2007-02-18
> **raldz said:**
> yup.. probably.. but you can't blame people to use this software because Windows doesn't know how to read Linux file systems... while in Linux, we could read-write into Windows file systems without so much problem...  so, it's either Windows is doing some things wrong, or Linux is doing some things right... or both...

Linux only recently (like in the last few months) has the ability to reliably write to NTFS via NTFS3G. Even now its STILL experimental.

I think you are confused.

---

### Post by raldz on 2007-02-18
> **454redhawk said:**
> Linux only recently (like in the last few months) has the ability to reliably write to NTFS via NTFS3G. Even now its STILL experimental.

I think you are confused.

I'm not confused, I know NTFS-3G is experimental... but it doesn't give me problems... I've been using FAT32 mounted on Linux without any problem... but EXT3 mounted on Windows is a problem... it's your call which is better on reading different file systems...

---

### Post by erlyrisa on 2007-02-18
thanks for the Info about Fs-driver ! - I never thought anyone would ever bother trying to tie Msoft soft to linux, can't wait to see it work on my machine.

-strange though how Vista was able to recognize the USB volume upon boot, Fs-driver must become a core component of Windows then in order for windows to actually be able to presume it knows what it's accessing and presume the volume is corrupt. - a great achievement by the Fs-driver programmers.

---

### Post by 454redhawk on 2007-02-18
> **raldz said:**
> I'm not confused, I know NTFS-3G is experimental... but it doesn't give me problems... I've been using FAT32 mounted on Linux without any problem... but EXT3 mounted on Windows is a problem... it's your call which is better on reading different file systems...


Make up your mind. You are comparing apples and oranges. Windows handles FAT32 just fine also.

 If you wanted to reliably write to a Windows/Linux system you should have picked FAT32. You made a poor choice and used experimental software.

---

### Post by raldz on 2007-02-18
> **454redhawk said:**
> Make up your mind. You are comparing apples and oranges. Windows handles FAT32 just fine also.

 If you wanted to reliably write to a Windows/Linux system you should have picked FAT32. You made a poor choice and used experimental software.

FAT32 doesn't support 4GB single files... I have lots of DVD ISOs... that's why I used EXT3 because I use Linux most of the time... does that enlighten you?  Before you assume things and assume my needs, be sure to ask first...  I'm not asking for your advice, I'm just sharing my experience.. so stop giving unsolicited advice because I'm not asking it... I will not use FS driver if I'm not sure what I'm doing... that's why I have lots of backups.. I use lots of beta software, I know the risks.. I don't need your advice...

---

### Post by erlyrisa on 2007-02-18
Doesn't fat32 also have a 32Gb limit? - it maybe readable under 2000 and higher but I dunno about linux's ability to read above the 32Gig? (never tried to tell ya the truth, I don't have anything over 20gig with fat32)

---

### Post by Dr. C on 2007-02-19
From the video it appears that the fs-driver was installed on Vista which is definatly experimental at best since the diriver was designed for earlier versions of Windows XP, 2003, 2000 etc. Just because something works on XP it does not mean it will work in Vista especially a filesystem driver

---

### Post by 454redhawk on 2007-02-19
> **raldz said:**
> FAT32 doesn't support 4GB single files... I have lots of DVD ISOs... that's why I used EXT3 because I use Linux most of the time... does that enlighten you?  Before you assume things and assume my needs, be sure to ask first...  I'm not asking for your advice, I'm just sharing my experience.. so stop giving unsolicited advice because I'm not asking it... I will not use FS driver if I'm not sure what I'm doing... that's why I have lots of backups.. I use lots of beta software, I know the risks.. I don't need your advice...

Ok Slick, I will refrain from any further advice if you stop saying windows deleted your files.
Windows DID NOT delete your files.

---

### Post by insane_alien on 2007-02-19
> **454redhawk said:**
> Ok Slick, I will refrain from any further advice if you stop saying windows deleted your files.
Windows DID NOT delete your files.

Did you watch the video? Yo clearly see a vista screen with a bunch of filenames flying by and i trust raldz is capable of finding out if the files really are gone. either way, it should NOT be happening. I also assume that it worked fine with XP.

---

### Post by raldz on 2007-02-19
> **insane_alien said:**
> Did you watch the video? Yo clearly see a vista screen with a bunch of filenames flying by and i trust raldz is capable of finding out if the files really are gone. either way, it should NOT be happening. I also assume that it worked fine with XP.

I was about to ask the same question..

---

### Post by 454redhawk on 2007-02-19
> **insane_alien said:**
> Did you watch the video? Yo clearly see a vista screen with a bunch of filenames flying by and i trust raldz is capable of finding out if the files really are gone. either way, it should NOT be happening. I also assume that it worked fine with XP.


I bet you think that guns that are used in suicide are at fault also. :lolflag:  (thats actually a pretty good analology because it is pretty much what he did, experimental software , unsupported OS...etc..)

I can see you now giving the police the report.

"You can CLEARLY see the gun in the video and the trigger was pulled.

THE GUN KILLED THAT POOR MAN!!! It jumped right up onto his head and went off!!!!"

Get a grip! :lolflag:

---

### Post by raldz on 2007-02-19
ok.. just to make 454redhawk happy, here is my statement...

"FS-Driver deleted my Linux Files"


---but who ever reads this, don't believe me instantly.. watch the video and be the judge.. I'm out of here... this thread is going no where.. I have no time for this conversation... I have better things to do than to have an argument with a person I don't even know or trust... I repeat.. I'm not asking any advice from anyone, I just shared my experience.. period!

---

### Post by Trebuchet on 2007-02-19
Most people would consider an OS that does what an application tells it to do is only doing what it's supposed to. Unless, of course, it's some version of Windows, then any problem at all is Bill Gates' fault. Any unbiased observer would realize that the only reasonable thing to blame here is the experimental software; which was already iffy just because Linux has known problems with reading and writing NTFS; never mind whether the software in question was even intended to run in Vista in the first place. Far more important is to get in the obligatory Microsoft bash.

---

### Post by chipsburner on 2007-02-21
> **raldz said:**
> @454redhawk
I'm not bashing Windows.. I use it 10 percent of the time... I just don't trust it anymore (actually I don't have any important files stored in an NTFS or FAT partition, because I don't really trust it).. it seems that it has a brain of his own deleting files without my permission... not a big deal, I have 2 backups of all my files mirrored in different hard drives... I just find it funny when I realize that it is deleting my files.... this could be trouble to some people who doesn't have backups... especially if it contains critical files...

hehe.  U are being too nice to M$.  They have a history of destroying other OS'es on other partitions or hard drives on bootup.  I used to use system commander, the their printed manual was a wealth of information on that.  

Windows, use to be the only game in town, so to speak.  M$ still thinks it is, and I think Ubuntu forums, perhaps has not figured out who the enemy is yet.  We are here because we do not like being slaves of M$.  Simple.  

Hope all is well in San Diego,  see you on the Mepis site.  Another good linux (ubuntu based) site.

---

### Post by raldz on 2007-02-21
> **chipsburner said:**
> hehe.  U are being too nice to M$.  They have a history of destroying other OS'es on other partitions or hard drives on bootup.  I used to use system commander, the their printed manual was a wealth of information on that.  

Windows, use to be the only game in town, so to speak.  M$ still thinks it is, and I think Ubuntu forums, perhaps has not figured out who the enemy is yet.  We are here because we do not like being slaves of M$.  Simple.  

Hope all is well in San Diego,  see you on the Mepis site.  Another good linux (ubuntu based) site.

nice to see you here chipsburner... I know you from the mepislovers.org forum... this is the fun thing about using Linux... lots of choices... I'm using MEPIS on my desktops and Kubuntu on my laptop.. have a good one...

---

### Post by AnRkey on 2007-11-16
I agree with raldz and insane_alien, any OS that deletes files without consent is not trustworthy! Just because the filesystem driver is not handling things properly according to the OS is not a good enough reason to wipe data... A simple (Yes/Yes to all/No/No to all) prompt would have solved this problem. Instead M$ makes the wrong choice! (again) Corrupt files is understandable but deleting them? [-X

Ubuntu also comes with no warranty, just like FS-Driver....

Whenever you log in to an Ubuntu box via ssh this pops up:
[I]
The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.[/I]

I trust Ubuntu completly, it's the reason my job is so much easier than it used to be. I don't trust Windows because I have no say as to how my systems work (or don't work)

It's because of this untrustworthiness  that I have made it my mission to move one box at a time to Linux!  So far it's 11 and counting \\:D/

Nuf sed!

AnRkey

---

