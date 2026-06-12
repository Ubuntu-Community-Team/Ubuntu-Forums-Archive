---
title: "Remote Backup - RSync?"
date: 2011-08-13
forum: Server Platforms
---

### Post by geudrik on 2011-08-13
I have two servers in two different locations, that do several different things.  One of their primary functions is providing remote storage for a few classmates on Server A.  Part of a project that I'm doing is setting up redundancy between two Ubuntu servers - Server A (where we use Hamachi to store school work), and Server B.

What I need to now do is once a night, start a mirror of the data on Server A -> Server B.  The stipulations are as follows
[LIST]
[*]Must only copy NEW or CHANGED files.
[*]If a file is deleted, that change must also be reflected in the data on Server B after the push
[*]Must be auto(cron)matable - No passwords, or user interaction, on a nightly basis
[*]Nodes must be able to be added on-demand - that is, if we get a third server, we must be able to essentially drop it in to the grid and have it work (don't worry about port-forwarding or any of the basic networking stuff - we've got that covered)
[/LIST]

I have been doing some reading and I feel like RSync could be my ticket - probably by using SSH and keys to handle authentication / maybe rsync into an sshfs mounted dir?

What are your takes / thoughts / ideas / oppinions of this?  I am very much learning so anything insight is greatly welcomed! :P

-Pat

---

### Post by kgatan on 2011-08-14
Rsync with ssh keys will work great but i would not recommend to just have a mirror backup. 
If your main server gets hacked or the data gets deleted for some reason you will lose the backup since it will mirror nothing. 

In that aspect i also suggest you let the backup server log into the main server, not the other way around. 
Backup server should only be backing things up, everything else should be locked down as much as possible. 

Id suggest you to use rsnapshots which is based on rsync and store atleast a few snapshots. this will also give you the possibility to restore previous versions of files. 

Rsnapshots is easy to setup and its also easy to add "nodes" as long as they are linux machines.

---

### Post by geudrik on 2011-08-17
Alright, after much further deliberation, we've not hit a wall of issues.  Allow me to cover the bases...

We have set up passwordless SSH between the redundant server and the primary server, which will allow rsync to synchronize data.

The issues that we are now facing are as follows
[LIST]
[*]Given that each user needs a user account on the primary server for organizational purposes, how do we ensure that their data is encrypted?  Using --encrypt-home seems logical, however, using rsync nightly to back up said data is going to be a problem because their home dismounts as soon as they log out
[*]Could we potentially have a single folder that is encrypted, but permanently mounted, with their homes as sub-directories?
[/LIST]
The encryption unfortunately is critical here.  We aren't all too worried about people stealing data by logging in remotely, but rather, in the event that someone steals a drive.  

Lay it on me... :)

---

### Post by hawk2010 on 2011-08-17
Why not use Duplicity ? [http://wiki.kartbuilding.net/index.php/Duplicity_-_secure_incremental_backup](http://wiki.kartbuilding.net/index.php/Duplicity_-_secure_incremental_backup)

---

