---
title: "First &quot;whoops&quot; in a long time - and a lesson in security..."
date: 2009-12-21
forum: Security
---

### Post by Ghost|BTFH on 2009-12-21
So it's 2am and I'm trying to clean up a mess in my drive from a "friend" who sent me a practical joke zip file (wound up with over 4,000 jpg files of smut in about 100 folders) and I was tired of having to manually delete all of them.  Basically, he inserted the files I DID need mixed in with all the junk.

So what's a BTFH to do?  Use a simple find command to take care of the issue!  HAH! I'm brilliant!  I'm a genius!  I...just ran it in the wrong directory!!! >_<

So, long story short, I managed to rm my entire jpg library - wallpapers, artwork, you name it.  Well, I've heard every story down the line about how secure Linux is, and the partitions make it very difficult to recover data, etc...I heard wrong.

Enter *testdisk* which you can download right from our repositories.  It has a secondary program called *photorec* that will systematically hunt down and restore lost files on almost any kind of partition - formatted or otherwise.  It can also scan empty areas as well as occupied areas for recoverable files.

Basically, my prayers were answered and I could keep on truckin' - except this thing is more powerful than I ever imagined!  It proceeded to recover somewhere in the neighborhood of well over 12,000 jpg files alone!!!

I knew it would be sizable because of the prank my friend tossed at me, but I was figuring, 4,050 or so.  It recovered every single jpg file that has been on my hard drive (it was still rockin' and rollin' when I realized it had gotten all the files I needed recovered and stopped it with 23 hours left to go on the recovery of just blank space) including cache files from the internet - EVERYTHING.

So, lessons learned:  

#1: Don't combine find with rm unless you're in the right directory.

#2: photorec and testdisk are life savers.

#3: Your deleted data is not as deleted as one might think!

I think I'll be looking into a freespace shredder or something of the ilk in the near future!

Cheers,
Ghost

---

### Post by Grenage on 2009-12-21
I've never seen or heard of any claims that Linux FS is more secure for deleted files, there's a boat load of tools out there for that very purpose (secure delete being the most popular).

For future reference, you can use the command *shred* or install secure-delete.

---

### Post by Ghost|BTFH on 2009-12-21
Yeah, I'm checking out secure-delete right now, it seems to be very effective and can work anywhere rm can just by using srm instead.

Cheers,
Ghost

---

### Post by Grenage on 2009-12-21
Yup! For the super paranoid, it also has tools for clearing or randomising data stored in memory.

---

### Post by cdenley on 2009-12-21
No filesystem overwrites data immediately upon deletion, as far as I know. This would be a huge waste of disk I/O. The only thing unique about ext3 (and I assume ext4) is it does erase (zero out) meta-data, making it basically impossible to retrieve files by path/name.

---

### Post by bodhi.zazen on 2009-12-21
You can simply overwrite your HD with 0's. Use and then delete a file if you want ot fill only the unused space :

[http://ubuntuforums.org/showpost.php?p=5645609&postcount=2](http://ubuntuforums.org/showpost.php?p=5645609&postcount=2)

---

### Post by lovinglinux on 2009-12-21
I had a similar experience with rm yesterday, but in my case the problem was in the way dolphin file manager integrates with the terminal. 

[http://ubuntuforums.org/showthread.php?t=1360604](http://ubuntuforums.org/showthread.php?t=1360604)

---

### Post by BkkBonanza on 2009-12-21
I use "sfill -lz /" every now and then to make sure stuff isn't lingering around too long. It helps to clean up junk and empty the trash first.

(sfill being part of the secure-delete pkg)

---

### Post by Sarmacid on 2009-12-22
Next time you're about to do a dangerous operation such as using rm and find in the same line, I suggest you try echo and the command, that will show you what the command will do before actually executing it. I use it every time I'll rm more than 1 file. Something like this > $ echo rm *.html
rm index.html

---

### Post by Ghost|BTFH on 2010-02-06
> **Sarmacid said:**
> Next time you're about to do a dangerous operation such as using rm and find in the same line, I suggest you try echo and the command, that will show you what the command will do before actually executing it. I use it every time I'll rm more than 1 file. Something like this

Fantastic tip! Thanks. :)

---

