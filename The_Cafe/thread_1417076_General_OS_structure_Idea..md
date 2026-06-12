---
title: "General OS structure Idea."
date: 2010-02-26
forum: The Cafe
---

### Post by MasterNetra on 2010-02-26
[COLOR="Red"]N[/COLOR]ow I don't know if there is a OS using something like this or not. And I don't have anywhere near the required programming skill to do this myself, but I would like to put this out anyway in case someone who does might be in the least bit interested.

  [COLOR="Red"]I[/COLOR] was thinking why not employ a OS structure that separates base system from regular system wide apps and use different admin levels for it. The base system with the core files, drivers and such could be solely controlled by root itself. Any kernel and driver updates would require root a prompt. And what would separate the root prompt from your normal sudo one is that the root prompt would disable (or block all traffic) from your Internet connection while your typing as well as freeze all other non-essential programs while you type the root password. The access of course would be granted solely for that installation program instance or command with no grace period like there is with sudo. Yes it would be annoying to have to enter a password for each base system related command but if your going to so much may as well log into root. Additionally remote login should not be a option with root/the base system, at least not with the desktop/laptop/notebook version. Server could be made do-able but disabled by default. (For those mass installations and upgrades, otherwise it might take a while to login into 100+ servers and update them each individually.)
  [COLOR="Red"]A[/COLOR]s for managing apps and games that could continue using a sudo-like prompt but would be associated with a lesser admin level that can't mod the base system. So that in the event someone breaks into lesser admin account and trashes it and all your system wide apps and games. At least they can't touch the main system files (unless you did something retarded like put the root password in a txt file and your lesser account can use the root prompt. Only solution to prevent that is to not have a root access from the lesser admin account. And prevent duel logging of course.) Addtionally it could be made to where if this happens and root is still untouch you could clear rest of the system from root with prehaps one command or use a restore utility to clear eveything out and setup everything to near vanilla. (All kernal, driver, and other base system upgrades would of course still be there so it would not be completely like a fresh install nor would it take as long as one. (Base could keep compressed versions of the startup apps and restore them when "Refresh" is ran. [A good and appropriated name I think])
   [COLOR="Blue"]Linux system in general could no doubt be modded to do this as its not a giant a leap from it, but a lot of programming to be done still I would think.[/COLOR]

lol I hope this made sense.

---

### Post by NightwishFan on 2010-02-26
I am sure developers tackle ideas such as these. Did you ever hear of a Microkernel?

---

### Post by falconindy on 2010-02-26
Read up on sandboxes and chroot jails. They're very similar to what you're describing in terms of limiting access. They're already employed today by a number of applications.

---

### Post by MasterNetra on 2010-02-26
Any of them actually employ a restore system like "refresh"  as well as preforming what I'm suggesting?

---

### Post by MasterNetra on 2010-02-26
I guess I might of not been completely clear on what I meant by Base System I was including system files as part of it as well.

---

### Post by falconindy on 2010-02-26
Oh, must have missed that part. Add union mounts and filesystems to your reading list. I use a union mount for my backups.

---

### Post by PhoHammer on 2010-02-26
I do believe Chrome OS will sport one of your ideas, in that 
the main file system for the OS will be read-only: [_http://chrometecha.blogspot.com/2009/11/chrome-os-and-security.html_]("http://chrometecha.blogspot.com/2009/11/chrome-os-and-security.html")

---

