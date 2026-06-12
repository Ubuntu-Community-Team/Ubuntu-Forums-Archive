---
title: "The Command which wipes the HDD"
date: 2009-10-07
forum: The Cafe
---

### Post by GreenDance on 2009-10-07
Hi, I was reading another thread and noticed someone's signature, I won't repeat what it says, but basically it's the command which wipes the hard drive, what baffles me is why does this command exist?

---

### Post by Tristam Green on 2009-10-07
It exists to wipe the HDD with extreme prejudice.

---

### Post by RiceMonster on 2009-10-07
First of all, the command will not work by default.

Second of all, it exists because under *nix, everything is mounted under one directory, called /. The command rm exists, because people want to be able to delete files. So with that command, you can tell it to delete any directory, which includes /. Nobody made a concious decision, "Hey, let's make a command that deletes everything!".

---

### Post by GreenDance on 2009-10-07
> **RiceMonster said:**
> First of all, the command will not work by default.

Second of all, it exists because under *nix, everything is mounted under one directory, called /. The command rm exists, because people want to be able to delete files. So with that command, you can tell it to delete any directory, which includes /. Nobody made a concious decision, "Hey, let's make a command that deletes everything!".

I forgot to add to my question, why isn't the command blocked, but as long as it does not work by default thats a good thing :)

---

### Post by Tristam Green on 2009-10-07
It's not really a single command, either.  It's a command with certain switches turned on or off, that needs to be run under a set of conditions.

I have it aliased on my machine as "doomsday".

---

### Post by orngjce223 on 2009-10-07
Why isn't the command blocked?  Why, because one of the selling points of Linux is that it will do *exactly* what you tell it to do!  xD

I know there's a few examples on this very forum of hapless users who've managed to run the command and hose their systems.

---

### Post by GreenDance on 2009-10-07
thank you for all the replies :)

---

### Post by stwschool on 2009-10-07
It's the linux way to assume you know what you're doing. That's how I like it.

---

### Post by blur xc on 2009-10-07
> **GreenDance said:**
> Hi, I was reading another thread and noticed someone's signature, I won't repeat what it says, but basically it's the command which wipes the hard drive, what baffles me is why does this command exist?

The people who wrote that command into existence didn't sit down and say, "hey, lets make a command so people can wipe their HDD's!!!  That would be cool!".

They wrote a command to delete files.  In DOS, it's (or was) called del, in *nix it's called rm.  del *.* c:\ would do a lot of nasty things too.  I know, I biffed a batch file I was working on when I was a teenager in DOS 5 and did that.

so- rm removes files.  rm * removes all files from a directory.  rm -rf recursively deletes files and folders from the directory.  If you select / to be the directory to start deleting- well, in and of itself, nothing will happen.  Unless you are logged in as root (bad idea), running in a root terminal, or put a sudo in front of it.  

A much safer, albeit slow if you have a lot of sub-directories, is to rm * the files, and rmdir the directory.  rm w/o the -rf switch won't delete directories, and rmdir can't delete directories unless they are empty.

So, the moral of that story is be extra careful of what you do while logged in as root- or with what you put a sudo in front of.  There a user that has a sig line that says - "Linux always assumes you know what you are doing".  

BM

---

### Post by doas777 on 2009-10-07
btw, rm -rf / will not wipe your drive. it will delete a lot of files you need, but the system will crash before it is done, so don't think you can use it to actually wipe a drive with a system on it.

---

### Post by gnuvistawouldbecool on 2009-10-07
Anyway, why exactly would you want to wipe the HDD with rm, anyway?  You can still use the disc afterwards, other commands can write *bad sectors* to the disc, which would be much more fun if you want to destroy a system.

That particular command, using more sane parameters, tells you how fast your drive works.

---

### Post by Eisenwinter on 2009-10-07
A good thing to do is to always read the manual page for a command.

You can do this by typing "man <command>" in the terminal.

For example:

```
man rm
```

This will print out the manual page for the rm command, which you can then read and understand entirely.

The switches **r** and **f** are covered there, of course.

---

### Post by Simian Man on 2009-10-07
> **doas777 said:**
> btw, rm -rf / will not wipe your drive. it will delete a lot of files you need, but the system will crash before it is done, so don't think you can use it to actually wipe a drive with a system on it.

It will actually get pretty far since most all of what the system needs is loaded into RAM.  You can, for example, delete an executable program while that program is running without trouble.

Might be fun to try in a VM :).

---

### Post by Mehall on 2009-10-07
> **doas777 said:**
> btw, rm -rf / will not wipe your drive. it will delete a lot of files you need, but the system will crash before it is done, so don't think you can use it to actually wipe a drive with a system on it.

You have clearly never run "sudo rm -rf /", as you would know that it loads the rm function into RAM, meaning it WILL continue.

Yes, you won't be able to do much else, and if you try to do other things, the system may lock up instead of finishing, but left to it's own, it will wipe the entirety of the machine.

Also on the "Don't do if you like your data!!" list is the "dd if=/dev/urandom of/dev/hda1" which will overwrite the entirety of hda1 with pseudo-random data. (also usable is /dev/null  which writes null data, zeroes essentially, to every sector.)

EDIT: Simian Man beat me to it, but I have actually done that command to a machine.

---

### Post by doas777 on 2009-10-07
> **Simian Man said:**
> It will actually get pretty far since most all of what the system needs is loaded into RAM.  You can, for example, delete an executable program while that program is running without trouble.

Might be fun to try in a VM :).
indeed. last year someone made a video of it. check around the forums and you should find it.

have fun

---

### Post by orlox on 2009-10-07
> **doas777 said:**
> btw, rm -rf / will not wipe your drive. it will delete a lot of files you need, but the system will crash before it is done, so don't think you can use it to actually wipe a drive with a system on it.

Does it actually crash?? I can imagine a gui becoming unresponsive, like gnome dying while you do it, but I'm not sure if the process would stop doing it's thing.

Of course, you would eventually erase the kernel, and the rm command itself, but the related processes are all stored in ram and rm wont affect that, so I don't see it that obvious that it will die before ending.

By the way, wasn't there a warning when you tried to run rm with those arguments?? Just like when you try stupid things with apt like "sudo apt-get remove libc6" it will warn you that you may probably bring doom to your OS.

---

### Post by Exodist on 2009-10-07
> **GreenDance said:**
> Hi, I was reading another thread and noticed someone's signature, I won't repeat what it says, but basically it's the command which wipes the hard drive, what baffles me is why does this command exist?

GNU/Linux is not designed to protect its users from them selfs. The only thing that command does is remove all the files and directories from the drive for you. Sometimes you may need that; Like cleaning up a old drive quickly or when guys in black suites have a warrant to search you home and you need your home folder to go bye bye. :(

---

### Post by Mr. Picklesworth on 2009-10-07
Same reason you can use dd to fill a disk with 1s :)

---

### Post by renkinjutsu on 2009-10-07
> **Exodist said:**
> GNU/Linux is not designed to protect its users from them selfs. The only thing that command does is remove all the files and directories from the drive for you. Sometimes you may need that; Like cleaning up a old drive quickly or when guys in black suites have a warrant to search you home and you need your home folder to go bye bye. :(

if only the guys from [Hackers]("http://en.wikipedia.org/wiki/Hackers_(film)") used *nix .... sigh. I guess nobody's THAT elite.

---

### Post by Tristam Green on 2009-10-07
> **Exodist said:**
> GNU/Linux is not designed to protect its users from them selfs. The only thing that command does is remove all the files and directories from the drive for you. Sometimes you may need that; Like cleaning up a old drive quickly or when guys in black suites have a warrant to search you home and you need your home folder to go bye bye. :(

If you have suits chasing you, a rm -rf ~ won't save you from data collection.

Just sayin'.

---

### Post by Exodist on 2009-10-07
> **Tristam Green said:**
> If you have suits chasing you, a rm -rf ~ won't save you from data collection.

Just sayin'. it will if you remove your home folder then use dd to spread null data back across the drive where no fills are at. Yes rm -rf actualy only removes the directory information from the FAT allowing that area of the disk to be used and written over. Thats why its a two step process. 1 remove Dir from FAT, 2 spread null data bits to prevent them from seeing files that were removed from FAT that where still there.


Other option is a large homemade electro magnet hooked to an extention cord stuck to your hard drive. Youll prob need a new drive if you ever use this tho. I used to work for the military and we used this to demilitarize old HDDs.

---

### Post by Tristam Green on 2009-10-07
> **Exodist said:**
> it will if you remove your home folder then use dd to spread null data back across the drive where no fills are at. Yes rm -rf actualy only removes the directory information from the FAT allowing that area of the disk to be used and written over. Thats why its a two step process. 1 remove Dir from FAT, 2 spread null data bits to prevent them from seeing files that were removed from FAT that where still there.


Other option is a large homemade electro magnet hooked to an extention cord stuck to your hard drive. Youll prob need a new drive if you ever use this tho. I used to work for the military and we used this to demilitarize old HDDs.

Ahh, degaussing.  Works on everything.

See, you failed to mention anything about writing and rewriting zeroes over the sectors.  That's where it's at, and if memory serves me, eight to ten swipes does the trick?

---

### Post by &#32 Greg on 2009-10-07
cat /dev/urandom > /dev/sdasomething works to overwrite drives...

---

### Post by schauerlich on 2009-10-07
> **Tristam Green said:**
> Ahh, degaussing.  Works on everything.

See, you failed to mention anything about writing and rewriting zeroes over the sectors.  That's where it's at, and if memory serves me, eight to ten swipes does the trick?

Sounds like you have experience in this field. Got something you want to tell us, Tristam?

---

### Post by Exodist on 2009-10-07
> **Tristam Green said:**
> Ahh, degaussing.  Works on everything.

See, you failed to mention anything about writing and rewriting zeroes over the sectors.  That's where it's at, and if memory serves me, eight to ten swipes does the trick?

Yea I got ahead of my self. :)

---

### Post by orngjce223 on 2009-10-07
It was on Slashdot recently, IIRC.

---

### Post by hoppipolla on 2009-10-07
I think an administrator in a shell as powerful as BASH will always have the ability to wipe the hard drive in one command....... right?

---

### Post by schauerlich on 2009-10-07
> **hoppipolla said:**
> I think an administrator in a shell as powerful as BASH will always have the ability to wipe the hard drive in one command....... right?

Bash itself actually provides very few tools. Most of the stuff that can do any damage lives in /bin.

---

### Post by Firestem4 on 2009-10-07
> **Tristam Green said:**
> It's not really a single command, either.  It's a command with certain switches turned on or off, that needs to be run under a set of conditions.

_I have it aliased on my machine as "doomsday"_.

Can I steal that? :P

---

### Post by carniola on 2009-10-07
> **doas777 said:**
> indeed. last year someone made a video of it. check around the forums and you should find it.

[_Here's one_]("http://www.youtube.com/watch?v=D4fzInlyYQo") for the morbidly curious.

---

