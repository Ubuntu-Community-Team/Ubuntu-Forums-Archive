---
title: "How To Make Your Computer Catch People Stealing Your Porn =&gt; for linux?"
date: 2007-07-09
forum: The Cafe
---

### Post by ltk5 on 2007-07-09
link-> [Consumerist catches geeksquad]("http://consumerist.com/consumer/investigations/how-to-make-your-computer-catch-people-stealing-your-porns-272458.php"). This is the original article I found today.

Is a think like this possible for linux, theoretically. I know that some log files are under /var/log, but do they log everything?

---

### Post by KIAaze on 2007-07-09
It certainly is possible. I can't give you an exact howto, but all the necessary programs and capabilities do exist:
-video capturing software (I used one last year but don't remember the way. You'll certainly find a howto here [http://ubuntuclips.org/]("http://ubuntuclips.org/"))
-possibility to launch programs & scripts at startup (on KDE, just put them in ~/.kde/Autostart for example, in Ubuntu look for the startup services in the System menu)
-keylogging programs (that goes a bit further than just taking the videos since you can get passwords that way)

Admins shouldn't resort to such evil things... :/
Just lock down the system correctly and use internet filters or programs searching user accounts for certain files containing keywords.

Here's a link of several things evil admins (or anybody gaining access to the root account or your own) can do to you:
[http://www.hackinglinuxexposed.com/articles/20040608.html]("http://www.hackinglinuxexposed.com/articles/20040608.html")

---

### Post by lisati on 2007-07-09
> **ltk5 said:**
> link-> [Consumerist catches geeksquad]("http://consumerist.com/consumer/investigations/how-to-make-your-computer-catch-people-stealing-your-porns-272458.php"). This is the original article I found today.

Is a think like this possible for linux, theoretically. I know that some log files are under /var/log, but do they log everything?

I tried clicking the link but my wireless router's firewall blocked it!

EDIT (A few minutes later after tinkering with firewall settings): Interesting!

---

### Post by smoker on 2007-07-09
it wouldn't stop them removing the drive and slaving it to another computer and copying the lot!

---

### Post by ltk5 on 2007-07-09
Whoa, that's interesting. I'd never thought an admin has so much power at his hands.
Though linux is known for the permission-thingie, this is a bit new to me.

---

### Post by Polygon on 2007-07-09
if a normal guy tries to sit down in your computer and tries to brute force your pass, or tries to access your file through another account on the computer, they will have a hard time due to linux's permissions and security (like 3 second wait between password retries)

but.... if you take the hard drive out of the computer and stick it into another computer, the permissions are just all reset to the first user on that computer i think, or maybe root. Point is, unless your filesystem is encrypted, your files will not be safe if someone takes out the hard drive and plugs it into another computer

to protect yourself from this, use truecrypt (which has both windows and linux ports) to secure your important files... but im not even sure if the geek squad would know what to do with a borked linux computer anyway.... maybe i should try it sometime :D

---

### Post by cobrn1 on 2007-07-09
Yes, when giving someone physical access to the pc you are pretty well completely compromised. The last port of call is file encryption, which is pretty much a kill-all for your security issues. Make sure you dump all your porn, media and importand documents into a trucrypt volumes and you should be fine (aslong as you don't mount it for them...

lok up truecrypt - it's very cool. At the mo I don't think it has a GUI for the linux ver, but I believe they're working on that...

As for recording, I have no idea, but I'd guess that KIAaze has the right idea...

---

### Post by Wiebelhaus on 2007-07-09
> **ltk5 said:**
> link-> [Consumerist catches geeksquad]("http://consumerist.com/consumer/investigations/how-to-make-your-computer-catch-people-stealing-your-porns-272458.php"). This is the original article I found today.

Is a think like this possible for linux, theoretically. I know that some log files are under ***_/var/log_***, but do they log everything?


ok , so how do we perform a [Ccleaner]("http://www.ccleaner.com/") type function in linux?

---

### Post by Polygon on 2007-07-09
> **cobrn1 said:**
> Yes, when giving someone physical access to the pc you are pretty well completely compromised. The last port of call is file encryption, which is pretty much a kill-all for your security issues. Make sure you dump all your porn, media and importand documents into a trucrypt volumes and you should be fine (aslong as you don't mount it for them...

lok up truecrypt - it's very cool. At the mo I don't think it has a GUI for the linux ver, but I believe they're working on that...

As for recording, I have no idea, but I'd guess that KIAaze has the right idea...

there is "forcefield", which works as a GUI for truecrypt, but since there is no linux API for truecrypt right now, its having to do some weird stuff to make it work, like it has to parse the text messages that truecrypt sends and stuff

in other words, it doesnt work well, even when it does work. Its much easier to use it from the command line

truecrypt -u /path/to/volume /path/to/mountpoint    <-- to mount with read/write permissions

truecrypt -d   <-- dismount all truecrypt volumes

---

### Post by KIAaze on 2007-07-09
> **sx66gns said:**
> ok , so how do we perform a [Ccleaner]("http://www.ccleaner.com/") type function in linux?
[LIST]
[*][Kleansweep]("http://www.kde-apps.org/content/show.php?content=28631") (designed for KDE, don't know how good it works with Gnome)(never tried it myself anyway)
[*]Clear the command line history```
rm ~/.bash_history
history clear

```
[*]Firefox -> "Clear private data" in the menus
[*]Empty recycle bin... :rolleyes:
[*]Remove logfiles in /var/log (I don't know what can safely be removed)
[*]Remove files in /tmp (I don't know what can safely be removed)
[*]Maybe also ```
rm -r ~/*~
```.
[/LIST]
WARNING: This will remove all files ending with "~" in your home directory recursively.
Those files are usually backup files and can be quite useful. (mostly when editing text files for example)

Those are all the things I can think of right now.

Other programs to keep Ubuntu clean (not from you but from messy program installations/uninstallations) or free disk space:
-localepurge
-deborphan
-debfoster

---

