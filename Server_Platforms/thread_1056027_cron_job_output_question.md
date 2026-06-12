---
title: "cron job output question"
date: 2009-01-31
forum: Server Platforms
---

### Post by inphektion on 2009-01-31
I have a script that runs that kicks off a backup of VM's on ESXi server.  As it outputs it writes the percentage done like:
Clone: 0% done. Clone: 1% done. 
But it writes it over itself.
So that at the end if I run the script and > to output the file looks like this:

```
################ Taking backup snapshot for Nostalgia ... ################
Destination disk format: VMFS thick
Cloning disk '/vmfs/volumes/datastore2/Nostalgia/Nostalgia.vmdk'...
Clone: 100% done.
Removing snapshot from Nostalgia ...
#################### Completed backup for Nostalgia! ####################


Start time: Sat Jan 31 11:00:07 UTC 2009
End   time: Sat Jan 31 11:00:56 UTC 2009
Duration  : 49 Seconds

Completed backing up specified Virtual Machines!

```

However when I add to the script to mail me the output from the cron job i get this:
```

################ Taking backup snapshot for Nostalgia ... ################
Destination disk format: VMFS thick
Cloning disk '/vmfs/volumes/datastore2/Nostalgia/Nostalgia.vmdk'...
 Clone: 0% done. Clone: 1% done. Clone: 2% done. Clone: 3% done. Clone: 4% done. Clone: 5% done. Clone: 6% done. Clone: 7% done. Clone: 8% done. Clone: 9% done. Clone: 10% done. Clone: 11% done. Clone: 12% done. Clone: 13% done. Clone: 14% done. Clone: 15% done. Clone: 16% done. Clone: 17% done. Clone: 18% done. Clone: 19% done. Clone: 20% done. Clone: 21% done. Clone: 22% done. Clone: 23% done. Clone: 24% done. Clone: 25% done. Clone: 26% done. Clone: 27% done. Clone: 28% done. Clone: 29% done. Clone: 30% done. Clone: 31% done. Clone: 32% done. Clone: 33% done. Clone: 34% done. Clone: 35% done. Clone: 36% done. Clone: 37% done. Clone: 38% done. Clone: 39% done. Clone: 40% done. Clone: 41% done. Clone: 42% done. Clone: 43% done. Clone: 44% done. Clone: 45% done. Clone: 46% done. Clone: 47% done. Clone: 48% done. Clone: 49% done. Clone: 50% done. Clone: 51% done. Clone: 52% done. Clone: 53% done. Clone: 54% done. Clone: 55% done. Clone: 56% done. Clone: 57% done. Clone: 58% do
 ne. Clone: 59% done. Clone: 60% done. Clone: 61% done. Clone: 62% done. Clone: 63% done. Clone: 64% done. Clone: 65% done. Clone: 66% done. Clone: 67% done. Clone: 68% done. Clone: 69% done. Clone: 70% done. Clone: 71% done. Clone: 72% done. Clone: 73% done. Clone: 74% done. Clone: 75% done. Clone: 76% done. Clone: 77% done. Clone: 78% done. Clone: 79% done. Clone: 80% done. Clone: 81% done. Clone: 82% done. Clone: 83% done. Clone: 84% done. Clone: 85% done. Clone: 86% done. Clone: 87% done. Clone: 88% done. Clone: 89% done. Clone: 90% done. Clone: 91% done. Clone: 92% done. Clone: 93% done. Clone: 94% done. Clone: 95% done. Clone: 96% done. Clone: 97% done. Clone: 98% done. Clone: 99% done. Clone: 100% done.
Removing snapshot from Nostalgia ...
#################### Completed backup for Nostalgia! ####################


Start time: Sat Jan 31 11:00:07 UTC 2009
End   time: Sat Jan 31 11:00:56 UTC 2009
Duration  : 49 Seconds

Completed backing up specified Virtual Machines!


```

How can i get the output to be like the first one in my mail?  I assume there is something I can change in the script.  My cron job simply runs a script called backupesx.sh that contains this:
```

#!/bin/bash

ssh root@10.1.18.25 "/vmfs/volumes/NFS-VMClones/scripts/ghettoVCB-enhance.sh /vmfs/volumes/NFS-VMClones/scripts/esx_backup_servers" > /root/ESXi/ghetto.out

mail -s "ESXi backup of MYVM3" "it@mydomain.com" < /root/ESXi/ghetto.out

```

thanks for any feedback.

---

### Post by inphektion on 2009-02-01
just weird the file i get mailed has all the percentages, the file on the filesystem at the end doesn't... 
maybe if I > to tmp.out then mv tmp.out to ghetto.out and mail myself that?

---

### Post by unutbu on 2009-02-01
Maybe try this:
```
ssh root@10.1.18.25 "/vmfs/volumes/NFS-VMClones/scripts/ghettoVCB-enhance.sh /vmfs/volumes/NFS-VMClones/scripts/esx_backup_servers" 1>/root/ESXi/ghetto.out 2>&1
```

It will redirect both stdout and stderr to ghetto.out.

---

### Post by inphektion on 2009-02-01
nope...
this is weird.  basically I'm seeing what is outputted to the screen.  when what I want is what that final file looks like.  That final file just has the last percentage (100%).  if I were to watch the output on my screen I'd see every percent counting as I'm getting...

There has to be a way I can just get that final file without another cron job that somehow runs after this one completes...

---

### Post by inphektion on 2009-02-01
ok when i just see "Clone: 100%" on one line that is when I was cat'ing the file out.  if I vi the file I do see all the percentages with a ^M in front of them all... 
so i'd need to strip out all the ^M's but the last one.....

---

### Post by unutbu on 2009-02-01
```
sed -i 's/^M$//g' file
```
will script out all the ^M characters. Be sure to type Ctrl-v Ctrl-m to produce the ^M character.

Also, it might be the case that the script is using special terminal control characters like backspace. If these control characters are in the output file, then maybe
```

cat ghetto.out | col -b
```
will show you the output you desire.

---

### Post by inphektion on 2009-02-01
yes thanks for that.
if you can help with looping through and getting rid of all the "Clone" lines but the last now please let me know.
[http://ubuntuforums.org/showthread.php?t=1056986](http://ubuntuforums.org/showthread.php?t=1056986)

---

