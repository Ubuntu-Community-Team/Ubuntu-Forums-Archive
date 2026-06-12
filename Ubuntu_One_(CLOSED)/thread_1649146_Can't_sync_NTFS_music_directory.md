---
title: "Can't sync NTFS music directory"
date: 2010-12-19
forum: Ubuntu One (CLOSED)
---

### Post by someonehour on 2010-12-19
Problem with Ubuntu One and NTFS drives.

I have all my music on an NTFS partition. 
I'm able to see this partition in Ubuntu no problem. Can play music using Rhythmbox.

But when I want to sync this, the option to syncronize the folder is greyed out.

I'm able to syncronize an ext4 directory such as Documents.   So I know my Ubuntu One account appears to be correct and connected.

I added the parition to /etc/fstab so its mounted on boot up.

Why is the option greyed out?

---

### Post by duanedesign on 2010-12-20
Ubuntu One can only sync directories in your $HOME.

---

### Post by Morbius1 on 2010-12-20
@duanedesign, I have no idea what Ubuntu One is but if it can only sync directories in his home directory can't he change the mount point in fstab to something in his home directory?

---

### Post by someonehour on 2010-12-20
thanks. that did it.
I mounted it under /home/me/Music and now it says it can sync.

I don't understand why that is though.
What's the difference where its mounted?

---

### Post by someonehour on 2010-12-21
new problem.
I bought the annual music sync ubuntu mobile.
I have my music mounted on /home/me/Music.
I checked to sync this directory.
Only I see the directories of music, but nothing inside them.
Why don't I see any mp3 files inside the directories?

---

### Post by Morbius1 on 2010-12-21
Why not post the output of the following command so we can all see what ownership / permissions you have set up on this directory:
```
ls -al /home/me/Music
```

---

### Post by duanedesign on 2010-12-23
> **someonehour said:**
> new problem.
I bought the annual music sync ubuntu mobile.
I have my music mounted on /home/me/Music.
I checked to sync this directory.
Only I see the directories of music, but nothing inside them.
Why don't I see any mp3 files inside the directories?

Ubuntu One syncs the metadata(folders) before the content. So sometimes you see the folders before the content. You can keep track of the number of items in each queue with the following commands:

```
u1sdtool --waiting-metadata | wc -l
```


```
u1sdtool --waiting-content | wc -l
```

---

### Post by someonehour on 2010-12-26
ls -al /home/l/Music

drwxrwx---  1 root plugdev   4096 2010-03-07 18:00 Yngwie Malmsteen - Alchemy
drwxrwx---  1 root plugdev   4096 2010-03-07 18:03 Yngwie Malmsteen - Facing The Animal
drwxrwx---  1 root plugdev   4096 2010-03-07 18:02 Yngwie Malmsteen - Fire & Ice
drwxrwx---  1 root plugdev   4096 2010-03-07 18:00 Yngwie Malmsteen - Inspiration
drwxrwx---  1 root plugdev   4096 2010-03-07 18:02 Yngwie Malmsteen - The Seventh Sign
drwxrwx---  1 root plugdev   4096 2010-03-07 18:01 Yngwie Malmsteen - War To End All Wars


u1sdtool --waiting-content | wc -l
18284

u1sdtool --waiting-metadata | wc -l
0


I don't know why its not syncing.  This is hard to troubleshoot

---

### Post by Morbius1 on 2010-12-27
This would be a lot easier if I knew what Ubuntu One was but if I reverse engineer your ls -al output it looks like your line in fstab is sometheng like this:

> /dev/sdxy /home/me/Music ntfs defaults,nls=utf8,umask=007,gid=46 0 0That's fine for user "me" as he is a member of the plugdev (46) group but Ubuntu One is probably not a member of that group or it's designed to only work for one user - "me".

What I would try is either make yourself the owner of the mount point:
> /dev/sdxy /home/me/Music ntfs defaults,nls=utf8,umask=007,[COLOR=Blue]uid=1000[/COLOR],gid=46 0 0OR make it so everyone can access the mount point:
>  /dev/sdxy /home/me/Music ntfs defaults,nls=utf8,[COLOR=Blue]umask=000[/COLOR],[COLOR=Blue]uid=1000[/COLOR] 0 0

---

### Post by someonehour on 2010-12-28
Ok it did sync some files not all.  I bought the annual Music sync. I have about 50GB of music, but it didn't sync all of it.  And my account it says 2GB 100% used.

What's wrong with this Ubuntu One.  
Does it mean it sync's one file? ;)
Ridiculous how difficult this is.  I thought Ubuntu was trying to make the Linux experience easy for people.

---

### Post by someonehour on 2011-01-06
I still can't get this to work.
The music sync'ed to my cloud space (2GB) instead of the unlimited music account.

Did I misunderstand how the Ubuntu One Music is supposed to work?

---

