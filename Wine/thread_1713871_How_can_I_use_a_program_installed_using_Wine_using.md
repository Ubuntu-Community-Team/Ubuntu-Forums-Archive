---
title: "How can I use a program installed using Wine using multiple users?"
date: 2011-03-24
forum: Wine
---

### Post by Aeonis on 2011-03-24
I have Ubuntu 10.10.  I'm a rather new user, but a fast learner.  I looked at this post:  [http://ubuntuforums.org/showthread.php?t=917422&page=1](http://ubuntuforums.org/showthread.php?t=917422&page=1)

I want to do this to more than just StarCraft...  It's my play toy to try to figure something out.  Basically, when my brother uses his account to try to play SC, he can't because his Wine directory doesn't have SC installed on it.  I was thinking about other WIndows only games/programs and I followed that thread and mine isn't working properly.

I know that I should probably stick to that thread, but what I was trying to figure out was if this could work:

Have a generic account that would host the Wine folder, then use that account to install anything that will be used by multiple users and then have multiple users use that wine directory as a home folder.  If not, then can we use a launcher or something to use a file from My account to Generic account to run a Wine program and then I can log off and brother can do the same program?

---

### Post by cogadh on 2011-03-25
You don't need to create a separate account just to install the games. Just put the Wine prefix in a directory that both users have access to, install under one account, copy the shortcuts to the other, then both of you can use the software.

---

### Post by cwwilson721 on 2011-03-26
To give an example:

My son and I both like playing World of Warcraft. And since it has grown to over 16GB installed, I'll be danged if I'll have 2 separate installs.

So I moved the '.wine/drive_c/Program Files/World of Warcraft' folder (only) that has the WoW install in it to /home/public (I already used 'sudo chmod -R 777 /home/public', so both accounts have read/write access to the folder.)

I only moved the WoW folder, because any other installs for wine I want to keep as a per-user thing.

I then created a shortcut in place of the copied folder pointing to that folder, in both my wine and in my son's wine folder.

Seems to work fine for my install.

---

### Post by Aeonis on 2011-03-31
> **cwwilson721 said:**
> To give an example:

My son and I both like playing World of Warcraft. And since it has grown to over 16GB installed, I'll be danged if I'll have 2 separate installs.

So I moved the '.wine/drive_c/Program Files/World of Warcraft' folder (only) that has the WoW install in it to /home/public (I already used 'sudo chmod -R 777 /home/public', so both accounts have read/write access to the folder.)

I only moved the WoW folder, because any other installs for wine I want to keep as a per-user thing.

I then created a shortcut in place of the copied folder pointing to that folder, in both my wine and in my son's wine folder.

Seems to work fine for my install.

I'm new to the commands within Ubuntu . How do I move those properly?  Is there a walkthrough you followed?

Edit:  I just looked and I can't navigate to a /home/public folder.  It says it doesn't exist.

---

### Post by cogadh on 2011-03-31
You need to create it.

---

