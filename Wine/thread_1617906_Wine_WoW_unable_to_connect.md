---
title: "Wine WoW unable to connect"
date: 2010-11-09
forum: Wine
---

### Post by dardack on 2010-11-09
Since Tonite I am no longer able to connect to WoW with wine.  My windows computer connects/logs in fine.  If I run WoW.exe with sudo wine, I can connect.  

But i don't want to run wine as sudo and would like to figure this out.  Anyhelp woudl be appreciated.

---

### Post by dardack on 2010-11-09
OK it hangs on the submitting non personal data, guess a user can submit what type of OS/GPU?

---

### Post by Mobidoy on 2010-11-09
I have just tried and it worked for me. I have seen that non personal data message which is new.... 

Are you behing a router ?

---

### Post by dardack on 2010-11-10
> **Mobidoy said:**
> I have just tried and it worked for me. I have seen that non personal data message which is new.... 

Are you behing a router ?


Yea but didn't matter.  On windows behind router worked fine.  Running sudo wine wow.exe worked fine.

It has randomly started to work.  However:

If I change WINEPREFIX to anything but what I run out of, even a fresh one, I don't even get to the point of asking for my authenticator #.  So made 3 backups of that directory just incase. 
 But would still love to know about this issue, what happens if I loose the good working .winewow profile folder, am I SOL?

---

### Post by Mobidoy on 2010-11-10
What are your Ubuntu and wine versions ?

---

### Post by dardack on 2010-11-10
> **Mobidoy said:**
> What are your Ubuntu and wine versions ?

10.10 and 1.3.6.

Also, have determined the folder causing the issues.  .winedir/drive_c/users/Public/Application Data/Blizzard Entertainment/Battle.net/Cache, if i copy the Cache folder from my windows machine that can successfuly log in from Doc & settings/All Users/Application data/Blizzard Entertainment/Battle.net/Cache to wine's dir, I now can successfully log in.

It's like this cache folder isn't successfully being created when it's missing or missing certain folders underneath it.

---

### Post by Mobidoy on 2010-11-10
Check the permissions on the directory, or to parent directories, That could be the problem.... Maybe you have at some point used sudo during installation and the game was installed for root and now it is acting on you.

If that is the case, giving full permissions will solve it.

---

### Post by dardack on 2010-11-10
> **Mobidoy said:**
> Check the permissions on the directory, or to parent directories, That could be the problem.... Maybe you have at some point used sudo during installation and the game was installed for root and now it is acting on you.

If that is the case, giving full permissions will solve it.

Nope my user has access to write.  If I delete the Cache folder, when I rerun wow and try to Login, it successfully creates the Cache Folder and temp download folders under cache, but it can't seem to create the 10-15 2 digit/letter folders blizz needs (ie 69, 1f, 99, etc).  There are wierd type of files under these folders, no idea what they are for.

---

### Post by dardack on 2010-11-15
Just incase someone has same issue.  Creating a new user name in ubuntu allows me to connect and such.  So i copied over stuff from old folder that i really wanted.  No idea why that profile was borked like that.

---

