---
title: "Today's build."
date: 2016-10-12
forum: Ubuntu Development Version
---

### Post by Hewjr100 on 2016-10-12
Does anyone think that ubuntu 16.10 daily build, dated 12 Oct. will be the same as official release on the 13th.

Henry

---

### Post by #&amp;thj^% on 2016-10-12
Just keep updating and you will arrive at 16.10 Final.
Cheers

---

### Post by sudodus on 2016-10-12
At least Lubuntu Alternate needs a respin ...

---

### Post by howefield on 2016-10-12
> **Hewjr100 said:**
> Does anyone think that ubuntu 16.10 daily build, dated 12 Oct. will be the same as official release on the 13th.

Probably not, there have been plenty updates coming through since then, just compare the checksums for the isos - if they are different zsync your copy to the released image :)

Or as 1fallen said, updating will take you there anyway.

---

### Post by Hewjr100 on 2016-10-12
First thanks for all your replies.  The reason I ask is that I know updating will get me to final, but I am concerned about leftover files from the daily builds.  howefield, how do I zsync?  

Henry

---

### Post by acheronuk on 2016-10-12
> **Hewjr100 said:**
> Does anyone think that ubuntu 16.10 daily build, dated 12 Oct. will be the same as official release on the 13th.

Henry

At least one more re-spin is required it seems.

---

### Post by ventrical on 2016-10-12
> **Hewjr100 said:**
> First thanks for all your replies.  The reason I ask is that I know updating will get me to final, but I am concerned about leftover files from the daily builds.  howefield, how do I zsync?  

Henry

You have to install zsync first.

```

sudo apt-get install zsync

```

then

   ctrl+alt+t for terminal

     then go to directory where iso is, usually Dowloads
cd Downloads

then
```

$zsync -i ./ yakkety-desktop-amd64.iso http://cdimage.ubuntu.com/daily-live/current/yakkety-desktop-amd64.iso.zsync


```

regards..

---

### Post by howefield on 2016-10-12
> **Hewjr100 said:**
> ...  howefield, how do I zsync? 

What I'll do (for a 64 bit iso) is. rename the most recent yakkety daily iso file that I have to ubuntu-16.10-desktop-amd64.iso. and then use the terminal command.. (after "cd'ing" to where the iso file is stored)

```
zsync http://releases.ubuntu.com/yakkety/ubuntu-16.10-desktop-amd64.iso.zsync
```

You would need to have zsync installed, so if you haven't..

```
sudo apt install zsync
```

Handily zsync will also verify the integrity of the file so no need to checksum it. Also I am guessing at the names and the paths but they should be correct going by previous experience. If you have a yakkety iso, give it a practice go, obviously using the daily build URLs and file names as appropriate :)

Also you will end up with a copy of the original iso that you started with that has an .old extension. I'll remove the .old from the filename and rename that iso to whatever the "Z" code name is and zsync from there to the first spin of that cycle.

Not sure if the example below will help, but I had an iso zsynced early on the 8th and have just zsynced it to show you an example, it has obviously been respun since I zynced it as it came up 85% complete.. 

```
hugh@yakkety-laptop:~$ cd /Data/Yakkety/
hugh@yakkety-laptop:/Data/Yakkety$ zsync [http://cdimage.ubuntu.com/daily-live/pending/yakkety-desktop-amd64.iso.zsync](http://cdimage.ubuntu.com/daily-live/pending/yakkety-desktop-amd64.iso.zsync)
cdimage.ubuntu.com: No route to host
#################### 100.0% 874.5 kBps DONE      

reading seed file yakkety-desktop-amd64.iso: *******************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************Read yakkety-desktop-amd64.iso. Target 85.3% complete.      **************************************
downloading from [http://cdimage.ubuntu.com/daily-live/pending/yakkety-desktop-amd64.iso:](http://cdimage.ubuntu.com/daily-live/pending/yakkety-desktop-amd64.iso:)
#################### 100.0% 3050.2 kBps DONE      

verifying download...checksum matches OK
used 1353449472 local, fetched 233466313
hugh@yakkety-laptop:/Data/Yakkety$ 
```

---

### Post by Hewjr100 on 2016-10-12
Thanks howefiled and ventrical.  I will add the thread to my ubuntu favorites folder, for future reference.

Henry

---

### Post by howefield on 2016-10-13
Just to complete, this is my workflow to zsync from yakkety 64 bit daily build to final 64 bit release.

Move to folder containg yakkety .iso file. Take care, if zsync doesn't find an appropriate .iso file it will start downloading a full fresh copy so keep an eye on the terminal output. Ctrl+C will stop the process.

```
hugh@yakkety-laptop:~$ cd /Data/Yakkety/
hugh@yakkety-laptop:/Data/Yakkety$ ls
yakkety-desktop-amd64.iso  yakkety-desktop-amd64.iso.zs-old
```

Rename yakkety iso to the final release
```
hugh@yakkety-laptop:/Data/Yakkety$ mv yakkety-desktop-amd64.iso ubuntu-16.10-desktop-amd64.iso
```

zsync (removed a lot of asterisks for brevity and had already zsynced hence the 100% it updated by 15% last night and further 9% today)
```
hugh@yakkety-laptop:/Data/Yakkety$ zsync http://releases.ubuntu.com/16.10/ubuntu-16.10-desktop-amd64.iso.zsync
#################### 100.0% 1031.8 kBps DONE     

reading seed file ubuntu-16.10-desktop-amd64.iso: *************************************************************************************************************************************
Read ubuntu-16.10-desktop-amd64.iso. Target 100.0% complete.      *************************************
verifying download...checksum matches OK
used 1593835520 local, fetched 0
hugh@yakkety-laptop:/Data/Yakkety$
```

Copy to destination folder
```
hugh@yakkety-laptop:/Data/Yakkety$ mv ubuntu-16.10-desktop-amd64.iso /Data/Linux/Linux\ Isos/
```
  
Remove .iso.old yakkety file
```
hugh@yakkety-laptop:/Data/Yakkety$ rm yakkety-desktop-amd64.iso.zs-old
```      

Rename ubuntu iso to ZZ cycle ready for first daily build... (obviously won't be zany :) )
```
hugh@yakkety-laptop:/Data/Yakkety$ mv ubuntu-16.10-desktop-amd64.iso.zs-old zany-desktop-amd64-iso
```

Rename Folder (when the name is known)
```
hugh@yakkety-laptop:/Data/Yakkety$ mv /Data/Yakkety/ /Data/Zany
```

Update alias in .bashrc so typing zany (or whatever the name will be) cd's to the folder and zsyncs (I use "pending" rahter than "current").

```
alias zany='cd /Data/Zany && zsync http://cdimage.ubuntu.com/daily-live/pending/zany-desktop-amd64.iso.zsync'
```

---

