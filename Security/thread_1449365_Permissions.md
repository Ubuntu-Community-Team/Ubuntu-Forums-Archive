---
title: "Permissions"
date: 2010-04-07
forum: Security
---

### Post by QuickFixUS on 2010-04-07
I am not putting lnux on my mac, so I don't think it goes in the Apple section and Security is the closest I could find regarding file permissions, so excuse me if I am in the wrong area for this question.
 
I need to back up my macbook (OSX) data. I do not have another mac nor do my friendsw.. I do have a PC running ubuntu 9 though. So i hook it up and can see it, but all the document are locked and I dont have permissions.... now with windows I know how ot take over permissions, I have looked onlin and the closest I found is using the temporary root user command to view all locked files but that gets me to about 25% my data.. Does anyone know how to truly replace all permissions for a Mac HD on Ubuntu?
 
Thanks in Advance

---

### Post by cariboo on 2010-04-07
I would suggest installing openssh-server on your Ubuntu system, and use ssh+rsync to backup your files. I'm lazy, so I use grsync to backup my files. There is a grsync version for mac available [here]("http://grsync-mac.tuxfamily.org/?lang=en").

For an openssh-server howto have a look [here]("https://help.ubuntu.com/7.04/server/C/openssh-server.html").

---

### Post by QuickFixUS on 2010-04-09
i gathered from what you said that my mac has to be networked for open ssh to work but 
The mac is not working at all and i have no access to other macs..., so i cant network it i have to do it straight from my ubuntu workstation.... 
 
 
am  i understanding you wrong
 
thank you cariboo....

---

### Post by SaintDanBert on 2010-04-09
> **QuickFixUS said:**
> 
...
all the document are locked and I dont have permissions.... now with windows I know how ot take over permissions, 
...


As the [highlight]root user[/highlight] you can "modify" almost all file and folder permissions. (While it is possible to prevent root intervention, a regular user would need to work at it.) If you are not the **owner** of a file or a member of the owner **group** your access is governed by the **other** entry in the permissions mask
... or by any access control list (ACL) but let's not go there.

NOTICE: While there are ways to do this with mouse droppings, I recommend use of a command shell prompt (console or xterm).

You can become the root user in several ways
1. login as root (deprecated)
2. use the **su** substitute-user command
3. use the **sudo** substitute-user-do command (preferred)

I prefer sudo because it keeps a log of every command. This log is useful in case you need to play back whatever you did to un-wind some mistake or even re-learn something useful.

Here is an example:
```

user@host:path/ $  sudo -i          #become root for several commands
... you are now working as if you had logged in as root user
user@host:path/ #  cd /media/MyUsbDrive/
user@host:path/ # 
user@host:path/ #  chown -Rv  myUID:myGID  *
... recursively change ownership for files
... print the name and path for each file you touch
... explain how file and folder attributes change on each file
user@host:path/ # 
user@host:path/ #  {CTRL-D}         # log out (literally end-of-file)
user@host:path/ $ 

```

At this point, all of the files on you USB drive will be owned by you.
You then get to use the left most (user) entry in the permissions mask
and the middle (group) entry in the permissions mask.

I hope this helps,
~~~ 0;-Dan

---

### Post by QuickFixUS on 2010-04-09
The files are not on a USB drive they are on a harddrive and are locked by the mac OS... will this still work?

---

### Post by SaintDanBert on 2010-04-09
> **QuickFixUS said:**
> The files are not on a USB drive they are on a harddrive and are locked by the mac OS... will this still work?

Can't speak for "MAC OS" however, [highlight]root[/highlight] user is not called "super user" because of tights and a cape. That login is supposed to be able to access and manipulate anything and everything
... unless someone takes the extra steps to specifically lock them out.

Any MAC OS folks out there who can keep me honest and teach us something?

~~~ 8d;-/ Dan

---

