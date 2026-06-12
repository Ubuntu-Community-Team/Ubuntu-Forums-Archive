---
title: "Permissions Preventing Apps From Opening"
date: 2009-03-22
forum: Security
---

### Post by Taggart.BBS on 2009-03-22
After playing around with permissions in my home folder, I am no longer able to open KATE. (a restart and an uninstall/re-install of the program was what led me to suspect a permissions problem.) Opening the program from the terminal gives me:

trying to create local folder /home/username/.kde/etc: Permission denied

&

kdeinit4: Aborting. bind() failed: : Permission denied
Could not bind to socket '/home/username/.kde/socket-station1/kdeinit4__0'

I am able to open the program by 'sudo kate' from the terminal.


Unrelated, but interesting:
All of my files are backed up on an external drive, as I had just yesterday gone through a clean install of the OS, therefore, I was fearless, and started playing around more with the permissions. One of my "solutions" involved chown the entire home folder to root owner. (Don't try this at home!) After the immediate problems this caused (including not being able to open anything) I did a system restart, and to my amazement, found that this state was unacceptable to the OS, which re-applied my username ownership of my username folder under /home. While this a great feature, alas, it did not solve the problem.

Anyway:
I assume the problem is in the permissions, in that the system doesn't have write access to my home folder, which is required for KATE to start up. Any help in solving this problem is appreciated. Thanks!

P.S.:
If more info is required, I'll happily provide it.

P.P.S.:
I'd typed this up in KATE (after sudo opening it) and was getting ready to post this, and Firefox no longer opens as well. From the terminal, I get:
(firefox:5854): GnomeUI-WARNING **: While connecting to session manager:
None of the authentication protocols specified are supported.
As with Kate, sudo firefox opened it right up, so while the language is different, I suspect it is a related problem.

---

### Post by Taggart.BBS on 2009-03-22
I solved this mostly myself using [http://ubuntuforums.org/showthread.php?t=371052#8]("http://ubuntuforums.org/showthread.php?t=371052#8")

One last lingering problem I suspect may be related is firefox being unable to write new cookies (thus forcing me to log in every time) but I'll work on it.

Thanks anyway, though.


edit: Above problem was unrelated

---

### Post by umechanism on 2009-03-28
I'm having the same problem.  I changed some folder and file permissions (never select "recusrive" when changing permissions!!!) and now Firefox will NOT launch and a video capture program (captures video from my video camera and saves the files to my hard drive) is having trouble writing to my Videos folder.

Did you get Firefox to work again?

---

### Post by lensman3 on 2009-03-28
Use the "chmod -R 700 *" and "chmod -R 700 .*"(note dot) to change the permissions.  If you can't change a files permission become super-user (sudo) to force the change.  The -R flag can really screw things up because it will recursively move through directories.  It can move up directory trees by following the .. files.  Recall that the files (and directories) with a leading dot are hidden files in Linux and have to be handled separately.

You also might have to  run the chown and the chgrp commands  also to get everything back to normal.

Hope this helps.

---

### Post by umechanism on 2009-04-04
> **umechanism said:**
> I'm having the same problem.  I changed some folder and file permissions (never select "recusrive" when changing permissions!!!) and now Firefox will NOT launch and a video capture program (captures video from my video camera and saves the files to my hard drive) is having trouble writing to my Videos folder.

Did you get Firefox to work again?

I got Firfox working again by doing this:
[LIST=1]
[*]Uninstalling Firefox completely.
[*]Deleted the ".mozilla" folder (this is a hidden folder in your home directory).
[*]Rebooted my machine
[*]Re-installed Firefox
[*]Bam!  Working again.
[/LIST]

---

