---
title: "Article In The Making"
date: 2008-03-17
forum: The Cafe
---

### Post by CD27 on 2008-03-17
WARNING!!! ANY AND ALL COMMAND LINE CODES ARE TO BE IGNORED BY NEW USERS TO LINUX AS THEY MAY CAUSE POTENTIAL SEVERE DAMAGE TO YOUR SYSTEMS!!!!

All who wish to help: I am writing an article and need your help. I am writing on the topic of "What NOT To Do In Ubuntu Linux". I have been informed to make it VERY clear, this thread is a SERIOUS thread and is not meant to be taken lightly. As by the Announcement that you'll above, be noted, malicious suggestions or attacks will NOT be tolerated and according to the announcement, you WILL be banned permanently from this site if you attempt it.

If you wish to offer information (along the guided lines of the rules below), I would prefer you to contact me via instant messenger: Yahoo-"Christian_dude_27" and "Bluedragon_k27"; MSN-"Psinetic@gmail.com"; AOL-"bluedragonk27" or via private message on this site. If you feel, however, you may post here on this thread, but I'd rather it be by private or instant message.

With that, here are the rules of the thread:

1. It's not just a "code" thread, ANYTHING that will cause damage to your Ubuntu Linux can be posted here, whether it be in terminal or something else.

2. YOU MUST EXPLAIN what this will do in its entirety, and also give a solution IN CASE it occurs.

3. All dangerous codes are to be labels with a WARNING!!!!

4. No joking around, this is serious. I'm writing this to help new users to know what to watch out for, and if by some chance they find themselves in a bind, how to fix it quick and easy without much hassle.

5. Solutions containing "reinstall" will be labeled as the most critical because reinstalling suggests that the incident is too severe to fix via terminal.

6. Please give references and experiences, DETAILED experiences and references to help explain WHY something is bad or dangerous and HOW TO FIX IT.

If your postings do not meet these criteria they WILL be deleted upon my request to the moderators and admin of the site. Please be careful, but be willing to help.

---

### Post by CD27 on 2008-03-17
I'll go ahead and post the first one.

WARNING, THIS **WILL** CAUSE YOUR SYSTE TO CRASH

As I learned the hard way, DO NOT give admin privileges to your /etc directory.

You can do this by right clicking the folder, going to permissions, and changing all three categories to "read and write" and then clicking "Apply to all subfolders" (I think).

If you do this it will cause your system to lock up because you've just given every user in your computer admin rights, which means ANYONE can do whatever they want to your computer, creating a serious security risk. The system failsafe's this by locking itself up. Thus you can't run ANY terminal commands. Your system is still functional however.

Do NOT overwrite your /etc directory on your hard drive with the /etc directory from your live cd, because your rules and users will be all jacked up, which will in turn cause your entire system to crash, resulting in your system being unable to boot AT ALL. You can correct these, but in my case, I had to reinstall because the drive STILL wouldn't mount (I suppose that because I copied over the /etc on my drive with a cd's /etc the drive thought it was a cd and was looking for a cd to mount as the hard drive, when it wasn't, but I really don't know).

This incident is labeled **[COLOR="Red"]CRITICAL[/COLOR]**.

---

### Post by CD27 on 2008-03-17
This is a forum I am creating to assist in my topic. [http://ubuntugeeks.aimoo.com/](http://ubuntugeeks.aimoo.com/)

---

### Post by CD27 on 2008-03-17
Fantastic! Looks like everyone REALLY wants to help each other out here, good job everyone!

---

### Post by CD27 on 2009-10-11
well over a year and still nothing. I honestly think that the transition for new linux users should be made alot easier. Everyone here knows that the majority of the problems with linux is simply because people don't know how to use it. Yes it is it's own operating system, completely and uniquely different from every other, but the amount of knowledge and experience required to properly run the darned thing gives everyone a head ache. I just made the permanent switch to ubuntu linux and I tell you, I've never had so many problems with an operating system in my entire career as a military IT professional, even with nasty windows viruses. It's literally, by the very definition, insane. However, I still find linux to be the best out of the three leading operating systems (Windows, Apple, Linux) and want to stick with it. But there are alot of mistakes people make when they first come to linux and the reading up they need to do isn't centralized and organized and it's WAY too much. I really would like to push for the possibility to make the transition easier for newer members of the community to be able to use the operating system. I'm starting to get the hang of it, but only because I've been troubleshooting the system literally since the day I installed it (about two to four weeks ago).

Just my humble opinion :)

---

### Post by kevdog on 2009-10-11
Lot of grandstanding here, but I don't see the point.  Only command I can think of not to do is:

sudo -rf rm /

---

### Post by Bachstelze on 2009-10-11
> **kevdog said:**
> Lot of grandstanding here, but I don't see the point.  Only command I can think of not to do is:

sudo -rf rm /

```
firas@iori ~ % sudo -rf rm /
usage: sudo -h | -K | -k | -L | -V
usage: sudo -v [-AknS] [-p prompt]
usage: sudo -l[l] [-AknS] [-g groupname|#gid] [-p prompt] [-U username] [-u username|#uid] [-g groupname|#gid] [command]
usage: sudo [-AbEHknPS] [-C fd] [-g groupname|#gid] [-p prompt] [-u username|#uid] [-g groupname|#gid] [VAR=value]
            [-i|-s] [<command>]
usage: sudo -e [-AknS] [-C fd] [-g groupname|#gid] [-p prompt] [-u username|#uid] file ...

```

:confused:

---

### Post by CD27 on 2009-10-11
lol epic

---

### Post by kevdog on 2009-10-11
oops

sudo rm -rf /

---

### Post by Bachstelze on 2009-10-11
> **kevdog said:**
> oops

sudo rm -rf /

```
firas@iori ~ % sudo rm -rf /
rm: cannot remove root directory `/'
```

Try again. ;)

---

### Post by lukjad on 2009-10-11
> **Bachstelze said:**
> ```
firas@iori ~ % sudo rm -rf /
rm: cannot remove root directory `/'
```

Try again. ;)
Lol, I'm tempted to try now.

---

### Post by kevdog on 2009-10-11
Hmm 

Im using intrepid so I don't get the nice warnings like you guys.

Is there really a point to this thread anyway??  I think you guys have proved this point by refuting my commands.  

Do not give admin priviledges to /etc?  What does this mean?  You mean root instead of admin?  I'm really confused about this one!

---

