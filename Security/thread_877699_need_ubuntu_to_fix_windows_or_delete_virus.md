---
title: "need ubuntu to fix windows or delete virus"
date: 2008-08-02
forum: Security
---

### Post by pintree3 on 2008-08-02
Using Windows XP home SP3 I think I got a virus. PC won't boot. Can't even get to "use last configuration" screen, on DOS prompt I am told something is wrong with the boot sector and am told to insert the system disk--assuming this system disk is the Windows original installation disk (the only one I have--OEM) I do so, click enter and PC reboots only to find myself with the same screen--My PC can't even recognize the Windows CD. Am now using the Ubuntu CD (but it takes about 5 boot attempts for it to be recognized.)
What I am asking for is to possibly use Ubuntu to do a virus scan and repair within windows -or anything else to help me solve this problem.
many free online scanner pages seem to only accept IE and not firefox.
Any suggestions?

Thanks in advance

---

### Post by Titan8990 on 2008-08-02
It sounds more like you need to run ms chkdisk from the recovery console or Bart's PE. From other OSes you will have problems cleaning viruses because you can't access the Windows registry where many viruses make dumps.

---

### Post by SunnyRabbiera on 2008-08-02
Yeh in this area there is not a lot ubuntu can do, just offer a way to get files off the windows drive until its possible to install windows again.
Windows and linux can only interact on certain levels as long a MS hates linux.

---

### Post by dentaku65 on 2008-08-02
You can install clamav anti-virus on the linux partition, update the patterns and scan the xp partition

---

### Post by sdowney717 on 2008-08-02
Yes, if you can mount the drive.

install fresh clam to update the definitions
run clamav and scan it.
I just dealt with this for someone. 
I took his drive out, put it in my PC, booted windows and ran a checkdisk on it.
I then booted linux and scanned it.
If the NTFS partition has errors, then I think you got to fix that with windows.

you can also install avast4linux. They have a deb file now.

---

### Post by pintree3 on 2008-08-02
thanks to all
-ist I can't run chkdsk since I can't get to where normally one would do such a thing.
in ubuntu I tried a search by  ";/" and a ":/media" to see my root directory but nothing showed there--is this an old command that no longer works?
I'm very new to ubuntu I've tried it for about 2 days only about 3 times in the last 3 years and left it because it is too complicated for me (too many permissions and console stuff for my old brain)
In windows I have 2 physical hard drives divided into 7 partitions (I think 4 are NTFS). In the ubuntu file browser I only see the G and H (which I had actually given names to ('Personl_drive' and 'music_drive') I also see my CD drive and DVD drive. I do not see anything else.
I did a search for "desktop", "windows", "Prog*files" and "Mich" in the hope that I can find what is/was on my windows desktop and the other partitons but got nothing. Where are my other partitions and my windows desktop files?
basically if I can get to them and then move the files in them to the other drives I don't mind formatting the C; drive where windows sits. But They either aren't there or I don't know how to find them
what

my ubunto version (as live cd) 8.04

P.S. my newbie-ism will show now: What is "mount a drive"? To me the word 'mount' is either a sexual word or something you do with a bike or horse.

---

### Post by sdowney717 on 2008-08-02
if you click
places - computer you should see them

And if you go to places - computer - filesystem - media - disk you should also see some windows partitions

---

### Post by pintree3 on 2008-08-02
HI
unfortunately I don't see them --hence my worry. Is this telling me that something seriously wrong is with my HDD (Evry single partition)? Or is Ubuntu Live CD not seeing them for another reason?

---

### Post by sdowney717 on 2008-08-02
mount just means setup the drive so linux can see it.

post the output of

sudo fdisk -l

open a terminal from app - access - terminal

I dont know if a live cd will show the window drives mounted

this thread will show you how to mount a partition if linux is installed to the drive
[http://ubuntuforums.org/showpost.php?p=4803348&postcount=18](http://ubuntuforums.org/showpost.php?p=4803348&postcount=18)

here is a guide on how to backup files from a dead windows system with a live cd
[http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/](http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/)

according to that site, hard drives with errors will not be shown and will have to be force mounted. And it looks like you should be able to get your files.
This does not mean your files are toasted. You will likely be able to get to them.

---

### Post by dentaku65 on 2008-08-02
With live cd you can try:
```
sudo apt-get install ntfsprogs
```
Then:
```
sudo ntfsfix /dev/sda1
```

---

### Post by pintree3 on 2008-08-05
Hi once again thank to you all. I sent it to the shop where I bought it and they weren't able to do anything with it. It seems as if the HD may be shot after all. They are now sending it to the HD manufacturer to see what it can do about it -but it doesn't look promising. I told them to make sure that nothing is done to the HD that could possibly delete my files for good.
I asked them that should the HD be shot what can be done to save my files and they told me that in such cases it could be sent to a place that specializes in retrieval of files with damaged hard drives but that it is an expensive process--very expensive.
SO I was wondering if there was any way I can do it myself or is such a thing only possible with special hardfware? Does anyone know?

---

### Post by /////// on 2008-08-06
Umm to save most of your files, I suggest you remove the hard drive and plug it into another computer. Then go to google and search for a program to "undelete files" or recover files. Use this and try to retrieve as much data as possible. If this doesn't work (If windows also can't see or mount the drive) then I suggest you format the drive (Make sure its a quick format) then run the undelete program. The first method is recommended because if you use the second method, when you re-install windows it'll write over some of the files in your hdd. Hopefully, it won't write over anything important and you can retrieve most of your files.

Good Luck

---

### Post by pintree3 on 2008-08-06
hi
the HD drive did go into another computer, that of the shop and they couldn't read it either. In reading your info I first thought hey that sounds good--and then I thought if both windows and linux can't mount it, therefore can't read it, then as far as the computer is concerned, it doesn't exist. and if it doesn't exist then it can't be formatted. I mean since it isn't mounted then there is no drive (it's icon) that one could go to and do the right-hand click and choose 'format'

OR
Is there another way that you know of that one can format a drive that "isn't there"?

---

