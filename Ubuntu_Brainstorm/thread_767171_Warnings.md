---
title: "Warnings"
date: 2008-04-25
forum: Ubuntu Brainstorm
---

### Post by oasmar1 on 2008-04-25
Many people new to linux can be convinced to use malicious commands (seen [http://ubuntuforums.org/announcement.php?f=73](http://ubuntuforums.org/announcement.php?f=73)). Why not make it so that the most destructive commands provide a warning.
When a command like "rm -rf /" is run a message should appear in the terminal saying "The command entered will delete all files. If you are sure you want to complete this command please type the word agree"

As the commands are not used that frequently by anyone i don't think that it would be too much of a problem for people and would reduce the risk of new linux users corrupting their system.

If this has already been implemented/posted then I apologize.

---

### Post by nhandler on 2008-04-25
The issue with this idea is that it would be impossible to prevent the user from executing all of the dangerous commands. For example, malicious users could start posting commands that move all of the files on a user's computer to /dev/null, which would also delete them. There is no way to prevent users from executing dangerous commands. All we can do is try to educate them about what the commands do.

---

### Post by bruce89 on 2008-04-25
Mollycoddling users like this is silly. Maybe we should get the command *sudo* banned.

There are many ways to wreck a system. *rm -fr /*, *mv*ing stuff to */dev/null* and *dd*ing the hard disk with junk are examples. In other words, loads of things would need patched, and experienced users would make a fuss.

---

### Post by ssam on 2008-04-27
if ubuntu can reach a point where 99% of people never **need** to use the command line then the the problem pretty much goes away.

i think it is pretty close.

one thing that would help is if people giving help in the forums gave GUI methods to achieve a task instead of command line ones. it can be a bit more effort, but i think it is worth it.

---

### Post by ronacc on 2008-04-27
I agree with ssam , I always run the latest developement version (waitng for intreped right now:) ) and I find I rarely "have" to use the terminal ' trying to protect people completly would rapidly render a distro almost unuseable , witness the absolute debacle that is Vista . Or if you are in the US just read the warning stickers that are on everything ,

---

### Post by qamelian on 2008-04-27
> **ssam said:**
> if ubuntu can reach a point where 99% of people never **need** to use the command line then the the problem pretty much goes away.

i think it is pretty close.

one thing that would help is if people giving help in the forums gave GUI methods to achieve a task instead of command line ones. it can be a bit more effort, but i think it is worth it.
A gui method is impractical because it assumes that all users are using the same desktop environment which will not always be the case. GUI instructions on how to resolve a problem in Ubuntu (Gnome) may not apply for users of Kubuntu, Xubuntu or any or *buntu off-shoots.

---

### Post by Mr.Macdonald on 2008-04-27
Learning terminal is trivial and takes about half a day to learn. Personally i feel that GUI has many flaws and that command line execution is very simple.

Even when i am doing basic work that could be done on GUI i many times use command line for simplicity

If you don't know BASH i suggest that you learn it.


Annoying GUI Problems:

deleting files justs puts them into the trashcan (very annoying). While
sudo rm -rf $FILES gets rid of them forever.

Using gedit creates lock files (or whatever these are "test.txt~") and oh so they make me angry.

---

### Post by ssam on 2008-04-28
> **Mr.Macdonald said:**
> Learning terminal is trivial and takes about half a day to learn. Personally i feel that GUI has many flaws and that command line execution is very simple.

Even when i am doing basic work that could be done on GUI i many times use command line for simplicity

If you don't know BASH i suggest that you learn it.


I use bash daily. when i am working i typically have laptop and a desktop, each with several terminals on sevral virtual desktops, and logged into many remote machines.

> **Mr.Macdonald said:**
> 
Annoying GUI Problems:

deleting files justs puts them into the trashcan (very annoying). While
sudo rm -rf $FILES gets rid of them forever.


in the behaviour tab in the nautilus prefs, tick the 'include delete command that bypasses deleted items folder'

> **Mr.Macdonald said:**
> 
Using gedit creates lock files (or whatever these are "test.txt~") and oh so they make me angry.

backup files. each time you save, the previous version is put in the ~ file.

---

### Post by scradock on 2008-04-29
> **ssam said:**
> 


in the behaviour tab in the nautilus prefs, tick the 'include delete command that bypasses deleted items folder'




or maybe for people who don't mess with preferences everyday and know what you mean:

System Tools | Configuration Editor | apps | nautilus | preferences - 

tick "enable_delete" which adds a delete command that bypasses the deleted items folder............

---

