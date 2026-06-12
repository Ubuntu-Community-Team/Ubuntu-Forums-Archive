---
title: "The question of a good backup"
date: 2019-01-14
forum: Ubuntu, Linux and OS Chat
---

### Post by jdeca57 on 2019-01-14
In my opinion there is an empty space in actual Ubuntu distributions and that is a recommendation how to safeguard your data. Some of us use cloud and that is perfect but I guess not everybody does that and then the question is how to backup and with what? An external usb drive is enough, a NAS is better but then prices rise so perhaps we should stick with the usb.

Ubuntu has a backup program and it gives notifications asking you to use it. However, when one accepts then one should install duplicity. It makes a backup and the files get stored in a folder on that external drive and are named like: duplicity-full.20190114T135031Z.vol1.difftar.gz and there is little or no way to access them. I think this is a lost opportunity.

There is another solution available in the snap store and that is ‘back in time’. It has the big advantage of storing said data in a readable format so that restoring a single file is easy. I know, some people have a more advanced use of Ubuntu and prefer CLI and rsync solutions in a script. I’ve done that myself. 

The basic solution of backing up your system should be on the measure of a first time user and that implies a GUI and an easy default. Perhaps ‘Back in time’ is even difficult. But at least it shows you your files and lets an access to individual files without going through commands.

So my point is: shouldn’t backup be more transparent?

---

### Post by Tadaen_Sylvermane on 2019-01-14
I used to use rsync scripts with hard links so that it only backed up changes with each run. But it was far to difficult or annoying if I wanted to restore something as I had to check each backup to find what I wanted. The backups utility Ubuntu comes with is dead simple and all GUI driven. Takes nothing to restore files in a minute. I backup to my server over ssh. Just because you can't browse the actual files themselves is meaningless as it isn't meant to be used that way. You will find that many apps or utilities in any OS use their own naming scheme for files, many times not even remotely descriptive of what it actually contains. The built in encryption lets me store my backups on google drive without fear as well, another nice feature.

About the only problem I have with the Ubuntu backups utility is that it prompts me to install more software. One would think it would work out of the box, not need more installed.

---

### Post by jdeca57 on 2019-01-14
> **Tadaen_Sylvermane said:**
> 
About the only problem I have with the Ubuntu backups utility is that it prompts me to install more software. One would think it would work out of the box, not need more installed.
OK, that's one strange part and also confusing for a first time user but even if you get a nice
GUI saying backup Y/n then some filter saying what file one wants to restore must be a plus.

---

### Post by suzukawa on 2019-01-15
For system backup I found Clonezilla to be a reliable solution. It makes images of harddrives or partitions. Only thing it does not like is restoring bigger saved partition on a smaller one, even if there would be enough space. But it is still possible. You need about half the space of all data stored in a partition for the backup files. Means the backup of a lets say 100 GB partition with 10 GB on it needs about 5 GB free space on the backup medium.
For backup of simple data I can recommend FreeFileSync. Really flexible and reliable and you always see what's going on in its very good GUI.
My experiences with Deja Dup and duplicity were mediocre.

---

### Post by jdeca57 on 2019-01-15
> **suzukawa said:**
> 
For backup of simple data I can recommend FreeFileSync. Really flexible and reliable and you always see what's going on in its very good GUI.
My experiences with Deja Dup and duplicity were mediocre.
I tested FreeFileSync and it is indeed a very neat software. Open source, even. Thank you for bringing it to my attention Of course you can't find it in Ubuntu software and that's a shame. My feelings about the standard backup software in Ubuntu (based on duplicity) match yours.

It's a curse of open software that there will always be multiple alternatives and that the choice is one any user must make for himself. 

Also, any backup is better than no backup. Still, the Ubuntu default seems... less than optimal.

---

### Post by MartyBuntu on 2019-01-15
I just don't feel comfortable making backups from within a running system.
I do regular full drive imaging with an Acronis boot CD. Yes, it's very "involved", but it hasn't failed me in over 10 years.
I've tried other backup boot cd's to various results.

---

### Post by mastablasta on 2019-01-16
i use Areca. you can easily restore particular file from certain time from the file manager. 
but there is also Duplicati

I wasn't lucky with Luckybackup but it works for some, though it looks a bit abandoned.

KDE also has Kup.

---

