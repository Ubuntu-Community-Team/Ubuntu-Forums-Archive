---
title: "Broken Upgrade"
date: 2012-09-27
forum: Server Platforms
---

### Post by Twinkie on 2012-09-27
I had a power loss to a Ubuntu 10.04 server during sudo apt-get upgrade.  Restored power to the system and now get the following error during upgrade:
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

I'm not exactly a Linux guru so I ran the command and a wonderful prompt ">"... Now what?  I tried the magic of google and could not find a solution.  This is a remote school site and I really don't want to charge them for me to re-install.  Any help would be great.

Thanks in advance,
Todd

---

### Post by Twinkie on 2012-09-27
Should have searched here first.  Already found the solution...

sudo dpkg --configure -a
sudo apt-get install -f

as posted by sikander3786 in "http://ubuntuforums.org/showthread.php?t=1803582&highlight=dpkg+interrupted"

Sorry to bother all of you.
-Todd

---

