---
title: "Is there a GUI for setting access to Extn drives for other users?"
date: 2016-05-30
forum: Ubuntu Studio
---

### Post by javierdl on 2016-05-30
Otherwise I suppose I should be "TAKING THE [SIZE=4]**TIME**[/SIZE] TO LEARN [THIS]("http://askubuntu.com/questions/694111/help-allow-another-user-to-access-partitioned-drives-on-ubuntu-15") ALIENATING COMMANDS METHOD THAT I'LL USE EVERY 3 YEARS OR SO". 

Sorry about the ranting....

JDL

---

### Post by TheFu on 2016-05-31
Sorry, don't understand the question as asked.  

If Unix file systems are used, making storage accessible to other users is a simple file-directory permissions and possibly group management question. File and directory permissions are the core of Unix security and part of any multi-user OS. There isn't any way around that - well - there isn't if security is **any** consideration at all.

Is there a GUI for this?  Yep, but it is different tools for the different aspects.  The shell is much, much, much, much easier to use for this stuff.   BTW, the same steps are necessary on Windows in a multi-user environment too.  You have a link that explains the mechanics.

---

### Post by javierdl on 2016-05-31
Thanks for replying TheFu.
Don't get me wrong, I do appreciate and value "security". But I value it more "when it's needed". My point is: I'm not in a work environment running a company, protecting highly valuable intelligence assets. I just want my girlfriend to have access to the ext drive where we keep the photos directory. But I guess that's too much to ask.
As for Windows, as much as I don't enjoy this aspect of Linux, I do like Ubuntu more than Windows, way more! However, my girlfriend never had ANY trouble accessing the ext drives with it. Steps? What steps? 
As for the shell method being much much easier, you can say that, and you look at it that way because you already know it.
Anyway, I guess I'll have to halt my life just to share the photos directory. Most likely I'll just share my Ubuntu password with my girlfriend.

---

### Post by TheFu on 2016-05-31
Well ... there are many different answers depending on how the system is setup, what type of external drive is being used and which file systems it has.

So ....
a) what type of external drive is it?
b) which file system does it have?
c) how does it get mounted?
d) where does it get mounted?

Since you´ve been a member here since 2009, I assumed you understood file and directory permissions. No? Didn´t want to talk down to you. Tutorial: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

But the link you already provided has the answers too.  Which is sorta why I didn´t understand the question - since it appeared that you had already found an answer.

Of course, if you don´t care about security at all, you can chmod -R 777 /path/to/the/photos ... but that will make everyone who is able to connect to the machine be able to delete everything in the directories with those permissions. Probably not what you really want, but feel free to do that. It is your box.

BTW - I´m taking your tone as sarcastic; trying to be funny.  If that isn´t the intent, please explain so I can match that tone.

---

### Post by javierdl on 2016-05-31
First off, please accept my most sincere apologies for being sarcastic, and venting in the process. I shouldn't have done that, as it's not your fault that I'm going through this.
Yes, it's been a few years since I first used Ubuntu, and have learned a few things since then. But it hasn't been a non stop learning journey. I skipped a few years. And "[COLOR=#000000]file and directory permissions[/COLOR]" as you can see, I'm still struggling with. I do like geeky things, I know some simple web coding, but I never meant to be a network administrator, an IT manager, etc (not that I mind, I just don't have the time. Not too sure I'm cut out for that though). So it's quite frustrating for me to come to the realization that I have to have almost the same level of technical skill JUST TO SHARE MY PHOTOS DIRECTORY. 
I can't blame you for being confused. On the one hand I ask for an answer, but on the other hand, I present the answer to the same question. The answer to this confusion is not in the link I provided, but the subject title. In another words: I would MUCH prefer a GUI for the same shell method explained in the link. 

Answering your questions:
[COLOR=#000000]a) What type of external drive is it? 

[/COLOR][IMG]https://images-na.ssl-images-amazon.com/images/I/31FBYG+JrLL._AC_US160_.jpg[/IMG]
[COLOR=#000000][Source]("https://www.amazon.ca/1TB-Canvio-Basic-USB-3-0/dp/B00N2S6ZUQ/ref=sr_1_1?s=electronics&ie=UTF8&qid=1464707532&sr=1-1&keywords=external+hard+drive+toshiba")
Mine is 2 years older. But is the same type.
[/COLOR]
[COLOR=#000000]b) Which file system does it have? 
NTFS
[/COLOR]
[COLOR=#000000]c) How does it get mounted?
Automatically, I just turn the pc on. 
[/COLOR]
[COLOR=#000000]d) Where does it get mounted?
On the desktop (?)

Btw, I never interpreted your tone as talking down to me. I do appreciate your putting up with me :)

JDL


[/COLOR]

---

### Post by TheFu on 2016-05-31
NTFS is an issue.  File permissions are controlled by mount options. No other way for you to solve this.

Storage being mounted to the desktop means it is using a ¨fake¨ mount - gvfs.  You need to use the /etc/fstab to mount it in order to control the mount options ... as far as I know.  You can check this by typing ´df´ (use a terminal) and seeing if the location for the storage shows up or not.  I don´t allow automatic mounts - it is a huge security issue in my mind.  There are subtle things that can be done with mounts which I find highly undesirable.

Everything you need to know is in those previously provided links.

---

### Post by javierdl on 2016-06-01
Thanks a bunch for the info TheFu :)

J

---

