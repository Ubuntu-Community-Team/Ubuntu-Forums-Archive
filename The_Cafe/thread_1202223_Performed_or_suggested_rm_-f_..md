---
title: "Performed or suggested rm -f *.* ?"
date: 2009-07-02
forum: The Cafe
---

### Post by papenpj on 2009-07-02
Has anyone ever done the command that I believe goes

cd /
rm -f *.*

IF you have no idea what it does, Im gonna be nice and tell you that you won't like the results so don't try it.  My friend was setting up his dad's mythbox again and was annoying me and since I was on ssh a recited the command and it took him a second to realize what I said when I told him all i need to do is press enter.... ah running as root is fun.


side note:
Is there a way I can prevent this???? I happen to have my my windows drive mounted and don't want to lose it if something like that happens.... once i really want to try it.

---

### Post by swoll1980 on 2009-07-02
From what I heard if your using Ubuntu it won't do anything.

---

### Post by papenpj on 2009-07-02
> **swoll1980 said:**
> From what I heard if your using Ubuntu it won't do anything.

I don't know if I want to fall for that or not.

---

### Post by .Maleficus. on 2009-07-02
All that would do is delete files within the / folder.

There are no files there to begin with.

There are folders, which would be skipped because you didn't use the -r (recursive) flag, but no actual files.  And as swoll said, you can't delete root anyways.  SELinux assumes the flag "--preserve-root" by default so it won't let you.

[Read this thread]("http://ubuntuforums.org/showthread.php?t=1087562").  I have seriously linked to this thread 3 times this week about this issue.  People, it is a non issue!  That thread really, really needs to be stickied.


Edit:  Not to mention the only files it would delete are those that have an extension.  IE, it would delete "super-importanty-sys-file.txt" but not "more-important-sys-file".

---

### Post by jelle_ on 2009-07-02
> **papenpj said:**
> Has anyone ever done the command that I believe goes

cd /
rm -f *.*



I had a directory ~ in my home directory and want to remove it. so i did a sudo rm -r ~. luckily, i could enter Ctrl+C in time

---

### Post by .Maleficus. on 2009-07-02
> **jelle_ said:**
> I had a directory ~ in my home directory and want to remove it. so i did a sudo rm -r ~. luckily, i could enter Ctrl+C in time
For the future, you own your home directory so you don't need to (and shouldn't) use sudo to be root.  You would have wanted something like this, "rm -r ~/~".  Or, you know, open Nautilus and delete it :D.

---

### Post by papenpj on 2009-07-03
Maleficus, Good to know that it won't completely delete everything.  Of course having a system intact won't be good once all the other important files are deleted, Im wondering is there a way to easily recover files deleted with rm?

---

### Post by MikeTheC on 2009-07-03
Oh, I do that like just all the time. Every day, and twice before breakfast.

Oh sh3@$)(*#$(*@#$

[font=courier][color=green][size=3]**NO CARRIER**[/size][/color][/font]

---

### Post by oldos2er on 2009-07-03
> **papenpj said:**
> 
cd /
rm -f *.*


 Wouldn't that only delete files with a dot "." in their name?

---

### Post by yabbadabbadont on 2009-07-03
> **oldos2er said:**
> Wouldn't that only delete files with a dot "." in their name?

Yep.  Although it would also wipe out any directories (and all their contents) that have a "." in their name.  It is obvious that the OP comes from a DOS/Win background.  Then again, most do.  :D


Back in the old DOS days, you could do stuff like
```
format /autotest c:
```
(Don't try that at home kids.   ;))


Edit: We used to also play mean tricks on each other like using a hex editor to swap the "md" and "cd" commands inside of command.com  Ah, the memories.  :lol:

---

### Post by fatality_uk on 2009-07-03
> **yabbadabbadont said:**
> 
Don't try that at home kids.   ;)

Wise words ObiWan

---

### Post by koleoptero on 2009-07-03
The ***sudo rm -fr **** would be more dangerous in the root folder. I've seen people advising others to do this in these forums. It's a pretty bad taste joke. Hence my signature.

---

### Post by yabbadabbadont on 2009-07-03
You must also be very careful when using the 'dd' command.  The reason that I am currently running Jaunty instead of Gentoo is that I made a typo late one night (actually very early the next morning) last week.  Hence my current user title.  :lol:

---

### Post by .Maleficus. on 2009-07-03
> **yabbadabbadont said:**
> Yep.  Although it would also wipe out any directories (and all their contents) that have a "." in their name.
"rm" will not delete a directory.  "rmdir" will delete an empty directory and "rm -r" will delete a filled directory, but just "rm" will not.

---

### Post by yabbadabbadont on 2009-07-03
> **.Maleficus. said:**
> "rm" will not delete a directory.  "rmdir" will delete an empty directory and "rm -r" will delete a filled directory, but just "rm" will not.

I misread the OP's subject as "rm -rf" not what it really was...  :oops:

---

### Post by Old Marcus on 2009-07-03
```
sudo rm -rf / --no-preserve-root
```

Would do the job.

---

### Post by sdlynx on 2009-07-03
just so you know the dangerous command is actually ```
sudo rm -fr /
``` lol ^^DON'T RUN THAT

---

### Post by .Maleficus. on 2009-07-03
> **yabbadabbadont said:**
> I misread the OP's subject as "rm -rf" not what it really was...  :oops:
With the amount of threads that pop up about "sudo rm -rf /" I'm not surprised at all :D.
> **Old Marcus said:**
> ```
sudo rm -rf / --no-preserve-root
```

Would do the job.
As well as:
```
sudo rm -rf /*
sudo rm -rf /bin /etc/ /usr /mnt /var <et al>
```
> **sdlynx said:**
> just so you know the dangerous command is actually ```
sudo rm -fr /
``` lol ^^DON'T RUN THAT
Now where'd I put my facepalm.jpg...

---

### Post by Jesus_Valdez on 2009-07-03
Youtube? 

[http://www.youtube.com/watch?v=D4fzInlyYQo](http://www.youtube.com/watch?v=D4fzInlyYQo)

---

