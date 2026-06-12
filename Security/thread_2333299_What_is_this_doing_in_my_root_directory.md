---
title: "What is this doing in my /root directory?"
date: 2016-08-09
forum: Security
---

### Post by chopra on 2016-08-09
I seem to have found a .mozilla/ directory inside root's home directory,  timestamped august 2, around midnight, as are all of the files. All of  the same stuff that's in the directory for my ordinary home dir:  extensions, firefox/Crash Reports  firefox/profiles.ini   firefox/rf2xu4hs.default and the like.

There was also an empty /root/Desktop directory, dated aug 2.

What's  more, there's a /root/.config/google-googletalkplugin directory, a   /root/.cache/mozilla directory,  a  /root/.cache/webkit/icondatabase/WebpageIcons.db file, and a  /root/.cache/dconf/user file that all seem to be timestamped around aug 2  quarter past midnight. Also a  /root/.dbus/sessionbus/1af0aa44a925d3fd81bac27d54dda4fb-0 file with that  same date.

I don't go into the /root directory that often, so I  don't know what's supposed to be there, but I know the chromium browser  has a SUID binary, /usr/lib/chromium-browser/chrome-sandbox (and I  recall a second SUID binary with that title, though I can't find it now)  which seems like the most likely way these things could get there. I  also know that /root is not supposed to have a Desktop or a .mozilla  directory.  I never log on as root, or perform any commands with  elevated priveledges unless I need to.

Is there a legitimate reason why these files and directories are here, and should I worry? 

Chopra

---

### Post by ajgreeny on 2016-08-09
Have you ever run firefox as root?

It is certainly not a safe thing to do, but you probably would not be the first to do so for whatever reason.

If you have it would explain why there is a hidden configuration folder for FF in /root.

---

### Post by Habitual on 2016-08-09
Vncviewer, teamviewer on the system at all?

Does  ```
sudo last root
``` show anything obvious?

---

### Post by chopra on 2016-08-09
Thanks for the replies guys.

> **Habitual said:**
> 
Vncviewer, teamviewer on the system at all?

Does  ```
sudo last root
``` show anything obvious?

sudo last root gives the same output as last root without the sudo, which is just the following:
wtmp begins Mon Aug  1 10:28:36 2016

No activity since aug 1, whereas this stuff was from aug 2. I've never heard of vncviewer or teamviewer before, and a check with the software updater shows that vncviewer is in Ubuntu's software repository, but it is not installed on my system.

[QUOTE=ajgreeny]
Have you ever run firefox as root?

It is certainly not a safe thing to do, but you probably would not be the first to do so for whatever reason.

If you have it would explain why there is a hidden configuration folder for FF in /root. 		 [/QUOTE]

Certianly not.  I never perform any command as the super user that involves connecting to the outside world through ssh, web browsers, or the like.  sudo apt-get is an exception, I suppose.

---

### Post by ajgreeny on 2016-08-09
>  [Quote] Originally Posted by ajgreeny
Have you ever run firefox as root?

It is certainly not a safe thing to do, but you probably would not be the first to do so for whatever reason.

If you have it would explain why there is a hidden configuration folder for FF in /root.
Certianly not. I never perform any command as the super user that involves connecting to the outside world through ssh, web browsers, or the like. sudo apt-get is an exception, I suppose. [/QUOTE]I'm very glad to hear that but it had to asked just in case.

---

### Post by Habitual on 2016-08-09
You have a router? Maybe needs an update or at the very least a review/inspection of the logs and access controls?
Wireless networks?
"Mates" that would have physical access to the system?

---

### Post by chopra on 2016-08-10
> **Habitual said:**
> You have a router? Maybe needs an update or at the very least a review/inspection of the logs and access controls?
Wireless networks?
"Mates" that would have physical access to the system?

I am the only person who accesses my machine. I live alone, so no one else has physical access.  This is a laptop, and I don't recall giving a router or wireless networks priveledged access to my machine. The one thing I did around the same time as the time stamps was install, play briefly, and uninstall the supertux game from the ubuntu software repository.

Interestingly, there were a couple of .png files in the mozilla folder, and I copied them into an area accessable through my main account and gave my normal self permission to view the copies.

The png files show images from a firefox session I was connected to around the time I had started the process of upgrading to version 16 LTS.  I don't recall exaclty what happened, but there's a window that has been popping up every time I sign on, informing me of the new 2016 LTS release.  A few days ago, I clicked on it to upgrade, and was going to but at some point later put it off and cancelled, because I wasn't sure how long it would take.  There were two firefox tabs open during this, and each now has its image captured in a .png file.  Maybe something related.

Chopra

---

### Post by mc4man on 2016-08-10
I would just get rid of the .mozilla folder & everything in it. No good reason for it to exist.

To note: running sudo firefox would not write to /root , it would write to /home/username who ran the command.
If one was to go sudo -H firefox or similar that would indeed  write to /root

---

### Post by chopra on 2016-08-11
Okay.  What about following that were either updated or created by whatever happened? If they don't serve any purpose, then deleting them would also seem like a good idea.
 
/root/.cache/dconf/user
/root/.dbus/sessionbus/1af0aa44a925d3fd81bac27d54dda4fb-0

BTW, I don't generally open firefox via the command line anyway, I use the GUI.  So a firefox session somehow accessed my /root directory, via some fluke, I'm assuming. 
If I enter my password to authenticate, and then click on a web link, could that cause this?  I know it shouldn't.

---

### Post by mc4man on 2016-08-12
> **chopra said:**
> Okay.  What about following that were either updated or created by whatever happened? If they don't serve any purpose, then deleting them would also seem like a good idea.
 
/root/.cache/dconf/user
/root/.dbus/sessionbus/1af0aa44a925d3fd81bac27d54dda4fb-0

Just leave them, they belong (and will come back anyway

---

### Post by chopra on 2016-08-15
I found the cause.  At least, I found what triggers it.
After signing on, I get the offer to upgrade to ubuntu 16.  A bubble comes up titled "Release Notes".  Clicking on the links 
 [URL="https://wiki.ubuntu.com/XenialXerus/ReleaseNotes"]https://wiki.ubuntu.com/XenialXerus/ReleaseNotes

or 
 [/URL][http://www.ubuntu.com/community/participate/](http://www.ubuntu.com/community/participate/)

creates a Desktop/ directory in the /root directory, as well as the .mozilla/ directory. Even if I have another instance of firefox running, 
clicking on any of these links opens up a new window, and clicking on further links opens up more tabs in that window.

One of the links even takes me to this board, and altough I'm signed on as Chopra, it says I'm not signed on in the mysterious window.

Surely, this is something that other people can duplicate, I hope?  It seems like the "Release Notes" bubble belongs to root, and so it thinks 
root is opening the window.  It might be wise to warn people not to go surfing on the web from this window.

Chopra

---

### Post by Habitual on 2016-08-15
Good work!

---

