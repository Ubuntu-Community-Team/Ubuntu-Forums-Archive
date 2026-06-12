---
title: "Moving Files"
date: 2010-03-23
forum: The Cafe
---

### Post by PhilMize on 2010-03-23
So you need to backup a windows based computer's data (in a work related environment) in order to wipe it and drop a new image. Sometimes this data can be MASSIVE. What methods do you guys' use? 

My rant/opinion, Windows fails at large file transfers(esp XP). It never seems to work if you just select all and paste onto an external drive of some sort. Even if you move data in sections and not all at once. I always get some sort of error from windows. My method is too usually boot to a live ubuntu environment and do all my file moving there. I usually get the best results that way. But even sometimes then I get errors. So what else do you guys' do? There's gotta be a more efficient way.:o

---

### Post by undecim on 2010-03-23
When I need to move files off a computer, I usually use a laptop and a crossover ethernet cable. With gigabit ethernet controllers , the transfer is so fast that the hard drive becomes the bottleneck rather than the actual transfer.

---

### Post by PhilMize on 2010-03-23
Wow really? I never thought about doing that! Duh! Seems like a great option. I'm going try this next time I need to move some files. LOL, feels like its been forever since I've used a crossover cable, let alone made one. *googles color order*

---

### Post by kelt65 on 2010-03-23
For that I would use "dd" in linux to create an image of the Windows partition(s). Just copying things over in linux could result in very messed up permissions.

---

### Post by rottentree on 2010-03-23
Install Powershell?

Edit: I think I have misunderstood the question :|

---

### Post by ssam on 2010-03-23
don't all ethernet card auto switch now, so there is no need for a cross-over. actually you just need 1 end to be able to autoswitch.

if its old enough to not autoswitch, then its probably old enough to not be gigabit.

---

### Post by Paqman on 2010-03-23
> **ssam said:**
> 
if its old enough to not autoswitch, then its probably old enough to not be gigabit.

And/or run on coal.

---

### Post by Dragonbite on 2010-03-23
Clonezilla (LiveCD)
dd (from LiveCD)
rsync (from LiveCD)
xcopy (from Windows)

---

### Post by PhilMize on 2010-03-23
> **Dragonbite said:**
> Clonezilla (LiveCD)
dd (from LiveCD)
rsync (from LiveCD)
xcopy (from Windows)

I'm pretty sure all those copy the contents of the hard drive entirely. (Only have experience with clonzilla)

I'm talking about saving a profile's, my docs, favorites, desktop etc that is all, then wiping the computer and reinstalling. Then recreating the profile and pasting all the data back.

---

### Post by Dragonbite on 2010-03-23
> **PhilMize said:**
> I'm pretty sure all those copy the contents of the hard drive entirely. (Only have experience with clonzilla)

I'm talking about saving a profile's, my docs, favorites, desktop etc that is all, then wiping the computer and reinstalling. Then recreating the profile and pasting all the data back.

Clonezilla and dd copies whole partitions, the others can pick and choose files and folders. Rsync also has a GUI to make things easier, called "Grsync"

At work (Windows XP) I use xcopy to routinely backup my Documents & Settings/<username> folder onto my server drive in case the laptop dies or is stolen.  It only copies the changed or new files.

More specifically, I run something like this ```
rem
rem SET THE SOURCE AND DESTINATION
rem

set DST=\\server\destination\folder\
set SRC=C:\"Documents and Settings"\<username>\backups\

rem
rem RUN THE XCOPY FOR EACH FOLDER, SET AS THE %FLD% VARIABLE
rem

set FLD="My Documents\"
XCOPY %SRC%%FLD%* %DST%%FLD% /y /s /k /h /d /q 

set FLD="Application Data\"
XCOPY %SRC%%FLD%* %DST%%FLD% /y /s /k /h /d /q 
```

I use rsync (actually Grsync) on my Linux box to backup my /home directory and a list of all of the applications I have installed via synaptic. After re-installing Ubuntu and setting up my same username, I rsync things back and use the list file to select all of the application installed previously and install them. Once that's done just log out and back in and I'm back where I was before but with a new installation.

I'll be doing this with Linux when 10.04 LTS comes out :)

---

### Post by koenn on 2010-03-23
+1 for XCOPY

I usually give it the /C (continue on errors) to avoid having 1 faulty file stop the entire copy operation. If the file can't be read by xcopy, it's probably useless anywway, unless there are other factors to take into account : open databases, system files, permission issues, (or someone left a spreadsheet open in Excel). Those should be dealt with before you even start thinking about copying.

---

### Post by koenn on 2010-03-23
> **PhilMize said:**
> So you need to backup a windows based computer's data (in a work related environment) in order to wipe it and drop a new image. Sometimes this data can be MASSIVE.  ... 

You can avoid this problem altoghether by not having data on your PC's 
Work belongs on the fileservers, and you can do the same with user profiles, so there doesn't really need to be any data locally on the PC, and you can just overwrite the thing with your new image. If a user happens to have to have his own private photo/music/.... collection on that disk, that's not really your problem. 

maybe that's an approach worth looking in ti for the future.

---

### Post by PhilMize on 2010-04-08
> **koenn said:**
> You can avoid this problem altoghether by not having data on your PC's 
Work belongs on the fileservers, and you can do the same with user profiles, so there doesn't really need to be any data locally on the PC, and you can just overwrite the thing with your new image. If a user happens to have to have his own private photo/music/.... collection on that disk, that's not really your problem. 

maybe that's an approach worth looking in ti for the future.

I WISH I COULD HAVE THAT SETUP! Sadly, the school district I work for, we have multiple buildings all over 100 square miles and don't have a all fiber backbone to support all that bandwidth. Mostly between buildings we have T1's and VPN's going. Sad I know :(. They are also a education system that has around 900 employee's and feels they only need one full time administrator and one part-time.

---

