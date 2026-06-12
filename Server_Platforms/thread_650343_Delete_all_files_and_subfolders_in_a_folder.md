---
title: "Delete all files and subfolders in a folder"
date: 2007-12-26
forum: Server Platforms
---

### Post by frodemt on 2007-12-26
Hi

How do I delete all files and folders in lets say /home/user/testfolder/ from a text based command?

---

### Post by icheyne on 2007-12-26
rm -fr /home/user/testfolder/*

to try it out before you pull the trigger, try:

echo rm -fr /home/user/testfolder/*

---

### Post by psusi on 2007-12-26
Leave off the /* on the end to delete testfolder, and ALL of its contents.  Adding the /* will only delete the non hidden files and directories ( and their contents ) in testfolder, leaving the folder there with any hidden files and directories still intact.

---

### Post by frodemt on 2007-12-26
> **psusi said:**
> Leave off the /* on the end to delete testfolder, and ALL of its contents.  Adding the /* will only delete the non hidden files and directories ( and their contents ) in testfolder, leaving the folder there with any hidden files and directories still intact.

But if I dont use "/*", the rm-command will delete testfolder too. I want to just delete its content.

---

### Post by pgjensen on 2007-12-26
do * and .*

---

### Post by psusi on 2007-12-26
> **pgjensen said:**
> do * and .*

NO do NOT.  ".*" includes "." and ".." which will end up causing rm to delete the entire contents of the directory that testfolder is IN.

---

### Post by xdice on 2007-12-26
> **frodemt said:**
> Hi

How do I delete all files and folders in lets say /home/user/testfolder/ from a text based command?

Just to add in another way to accomplish the task:

First, verify ownership of the directory.  Since it's in your homedir, 99% sure it's owned by you, but verification never hurts:

ls -l /home/user | grep testfolder

Now for the delete:

rm -rf testfolder && mkdir testfolder

(What that does, is removes the folder, and if that command is successful, then it will create a new directory called testfolder).

If you have to set specific user:group ownership info, do that like this:
chown user:group testfolder

(Again, 99% sure you won't have to do that last step).

This way, you can be sure that all of the content, hidden directories and files are removed from testfolder, but when you're done, testfolder still exists. 

 I find that it's a little easier this way, than to remember which combination of *'s and /*'s will work (safer, too - wildcards combined with rm -rf can be a recipe for disaster.).

---

### Post by frodemt on 2007-12-26
just * worked well enough. None of the directories has hidden files, so I think it will be good enough.

It would be perfect if someone find a solution to my first question though.

---

### Post by frodemt on 2007-12-26
> **xdice said:**
> Just to add in another way to accomplish the task:

First, verify ownership of the directory.  Since it's in your homedir, 99% sure it's owned by you, but verification never hurts:

ls -l /home/user | grep testfolder

Now for the delete:

rm -rf testfolder && mkdir testfolder

(What that does, is removes the folder, and if that command is successful, then it will create a new directory called testfolder).

If you have to set specific user:group ownership info, do that like this:
chown user:group testfolder

(Again, 99% sure you won't have to do that last step).

This way, you can be sure that all of the content, hidden directories and files are removed from testfolder, but when you're done, testfolder still exists. 

 I find that it's a little easier this way, than to remember which combination of *'s and /*'s will work (safer, too - wildcards combined with rm -rf can be a recipe for disaster.).

I am making a program that uses commands to do stuff. I will try your command.

---

### Post by psusi on 2007-12-27
> **xdice said:**
> 
ls -l /home/user | grep testfolder


ls -ld ~/testfolder is shorter to type and runs faster ;)

---

### Post by xdice on 2007-12-27
> **psusi said:**
> ls -ld ~/testfolder is shorter to type and runs faster ;)

True enough, but I like to type out everything when explaining a topic (just think of it as my verbosity switch is stuck in the on position) ;)

---

