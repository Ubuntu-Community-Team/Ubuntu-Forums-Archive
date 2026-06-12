---
title: "Can't Copy Files From Live DVD"
date: 2020-11-24
forum: Ubuntu/Debian BASED
---

### Post by ivan23m on 2020-11-24
Hello

I would like to copy files via Live DVD to my mobile device but it doesn't allow me to nor can I open them. The four with the x sign. With the last two on the right I have no problems with, these were made about ten days ago. 

I tried copy-paste but it said libmtp error. I also tried with the cp command and it said permission denied. 

```


zorin@zorin:~$ cd /media/zorin/1e630862-2660-4d7f-bbb7-595b502d2172/home/ivan23m/Desktop/
zorin@zorin:/media/zorin/1e630862-2660-4d7f-bbb7-595b502d2172/home/ivan23m/Desktop$ cp Dnevnik.odt /home/zorin/Desktop/
cp: cannot open 'Dnevnik.odt' for reading: Permission denied
zorin@zorin:/media/zorin/1e630862-2660-4d7f-bbb7-595b502d2172/home/ivan23m/Desktop$ 


```


But maybe I should ask is that necessary at all, I'm gonna do a system reinstall anyway, maybe I'll be able to open and copy them after?

---

### Post by DuckHook on 2020-11-24
Your difficultites are likely due to permissioning issues.

I have not used Zorin in years, so I cannot guide you with details, but you should be able to see who owns those files and see if they have the "read" bit set for "others". Note that when you run a LiveUSB/DVD session, the owner is set to some special version of root. Those files may be set to be only readable by the file owner, in which case the read bit must be set to allow others.

Here is a link to a simple explanation for file permissions: [https://www.linux.com/training-tutorials/understanding-linux-file-permissions/](https://www.linux.com/training-tutorials/understanding-linux-file-permissions/)

---

### Post by ivan23m on 2020-11-24
I'm gonna need further assistance on what exactly to write, Zorin is based on Ubuntu so I'm sure there wouldn't be any problems with more detailed advice. I understand permissions generally but I don't know what to do next. And by the way, I'm the only user of this PC.

---

### Post by CelticWarrior on 2020-11-24
> **ivan23m said:**
> And by the way, I'm the only user of this PC.

But you are not that user when running a live session and that's the problem.
I'm not sure you actually understand permissions.

---

### Post by ivan23m on 2020-11-24
Yes, that seems to be the case, I'm not particularly acquainted with how Linux works, I ask for advice here when I have some problem. So, can anything be done, is there a way to copy those files?

---

### Post by CelticWarrior on 2020-11-24
Yes, something can be done, but I just realized you're the same person from [this thread]("https://ubuntuforums.org/showthread.php?t=2444903") and I don't have the slightest desire of engaging in another round.
So, I'll leave you with the experts.

As a last note, the way to avoid the situation you're in now is to have proper backups. This is applicable to any OS and any usage scenario. Having that the system can break a be reinstalled or installed other anytime, your personal files are safely backed up.
Trying to retrieve files from an unbootable system with strict file ownership/permission is not for newbies. Again, I'll leave you with the experts. Sorry, @DuckHook

---

### Post by TheFu on 2020-11-24
Ubuntu has a Permissions tutorial.  All Unix-like OSes use this, so pretty much every popular OS in the world today uses Unix permissions, except 1.
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) is the Ubuntu permissions tutorial.

Also, never forget that all Unix-like OSes are multi-user, regardless of the number of human users.
By default, Ubuntu's first userid will be 1000.
By default, Ubuntu running in a Live-Boot-Install environment will have a userid of 999. That is not 1000 and it isn't in the same group as 1000, so the permissions must allow "other" to have at least read access if you want to copy files.  See the tutorial link for how to accomplish that.

Not learning permissions, but still running Unix OSes will lead to wasted hours, days, weeks, months until they are learned AND understood. I don't know of any shortcut to that knowledge, besides sitting down and going through all the permissions using multiple userids for about 45 minutes.  That's all it takes and you'll have 90% of what matters about permissions for all Unix-like operating systems.  There is a choice.  Be frustrated or learn this topic.

P.S. Zorin works the same.

---

### Post by DuckHook on 2020-11-24
As others have stated, there is a limit to how much help you can expect within the confines of this virtual environment. Both TheFu and I have linked you to tutorials that describe what to do. There's nothing more that I can add to that. You must now navigate into the directories you wish to work on and change those permissions. How to change permissions is explained in the tutorials.

BTW, your statement:> **ivan23m said:**
> Zorin is based on Ubuntu so I'm sure there wouldn't be any problems with more detailed advice.…is a misunderstanding: a common misunderstanding, but still a misunderstanding. Just because a distro is based on Ubuntu does not make instructions interchangeable. In your case, a good example is your LiveDVD session: I have no idea how Zorin implements their LiveDVD, how they've set up their version of root, whether they use Sudo and if so, what defaults they have decided on, etc. For Zorin, the LiveUSB root account might not be 999. You may have better luck on the Zorin forums.

Whichever forum you use, no helper can handhold you to the extent you seem to be expecting: instructing you in the use of a terminal, simple navigation commands, or inputting keystrokes. These are basic skills like turning a steering wheel or pressing on the accelerator. Driving instructions must assume that the basic mechanics have already been grasped. Likewise, Linux instruction assumes that its basic mechanics have already been grasped.

---

