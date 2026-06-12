---
title: "Backups: what and when?"
date: 2005-05-05
forum: Server Platforms
---

### Post by mwnovak on 2005-05-05
Thought I'd try posting this here before turning to more generic Debian lists...

As a "learning project," I've installed Ubuntu 5.04 on a Mac G4 Cube with the intention of running the box as a web server (publicly) and file server (for my LAN).  In addition to my websites, the server will eventually host the "learning projects" of several friends and students (they're learning basic web development, I'm learning basic server administration: everyone wins).

From what I've found out, many people recommend three "tiers" for backing up a Linux server: 1) monthly full-system backups for "bare metal" recovery, 2) intermediate/weekly backups, and 3) daily backups.  

Although I'm still sorting out my "bare metal" recovery options, I get the general idea (backup everything and have a plan for returning a wiped drive to its pre-crash condition).

That said, I'm trying to figure out which files/directories I should target for the intermediate/weekly and daily backups.  

For example, I believe that [FONT=Courier New][COLOR=Sienna]/home[/COLOR][/FONT] and [FONT=Courier New][COLOR=Sienna]/root[/COLOR][/FONT] should be included in daily backups because user files change on a regular basis and are not recoverable from other sources.  But, what about [FONT=Courier New][COLOR=Sienna]/opt[/COLOR][/FONT] (home to MySQL databases, I believe) and [FONT=Courier New][COLOR=Sienna]/var[/COLOR][/FONT] (home to the system logs, no?)?

And, for weekly backups, [FONT=Courier New][COLOR=Sienna]/etc[/COLOR][/FONT] seems like a good candidate (integral to the system, but not changing daily), as does [FONT=Courier New][COLOR=Sienna]/srv[/COLOR][/FONT] (for similar reasons).  But, what else?

Unfortunately, I haven't been using Linux long enough to have any intuitive sense about Ubuntu's directory structure.  Hence, my overall questions is simply, "Which directories should I be including at each 'tier' of the backup strategy, and why?"  

Can anyone advise me or at least point to a Debian-specific resource that'll help answer my question? 

Thanks in advance for your help,

--MW

---

### Post by mendicant on 2005-05-05
You could also say, for any but the full backup: backup anything that has changed since the previous backup.  tar and rsync both support this kind of thing, I believe.

---

### Post by mwnovak on 2005-05-06
That's probably the thing to do... it hadn't occurred to me that tar would let me specify something like "include all files added/changed in the past [x] days."  

I'm pretty new to *nix, and it's moments like this that make me stop and say, "D@mn, Linux is cool!"  Thanks for the tip, mendicant.

For other newbies who might find this thread, an example tar line that does this "past [x] days" operation might looks like:

> [COLOR=Sienna]tar -c -p -N "7 days ago" -X excludeDirs.lst -f $backupWeekly.tar / [/COLOR]

The relevent part is: [FONT=Courier New][COLOR=Sienna]-N "7 days ago"[/COLOR][/FONT]

Also, there's a quick overview of tar's relative date syntax at: [http://www.gnu.org/software/tar/manual/html_chapter/tar_7.html#SEC115](http://www.gnu.org/software/tar/manual/html_chapter/tar_7.html#SEC115)

Thanks again,

--MW

---

### Post by SNo0py on 2005-05-22
I would use rsync - it compares the files and backs up only changed files.

Personally I'm only backing up /home, /root, /etc as well as MySQL and the Apache-Root using rsync. In case the harddisk has a crash I'm reinstalling the Distro from CD and restoring all configuration using the backed-up /etc-directory.
Yeah, that approach does not allow me to restore everything within 5 minutes, but it is a good compromise between backup space and restore-speed.

---

### Post by LordHunter317 on 2005-05-22
[QUOTE=mwnovak]  But, what about [font=Courier New][color=Sienna]/opt[/color][/font] (home to MySQL databases, I believe)[/quote]Ubuntu usually stores MySQL database in /var/lib/mysql.  /opt is for programs, not data.  

>  and [font=Courier New][color=Sienna]/var[/color][/font] (home to the system logs, no?)?/var contains lots of things, some of which don't need to be backed up.

I should point out it's not as simple as backing up files, either.  For MySQL for example, you have to actually run a program to dump the database; you will not get a consistent backup simply backing up the data area unless the server is stopped.

---

### Post by dannysauer on 2005-05-25
I personally am a big fan of rsync-based snapshots.  While I rolled my own program several years back, there's a system called "dirvish" that uses the same concepts and is more suitable for general use.  You don't waste a bunch of space, and you have complete daily snapshots that are easy to restore from.  Dirvish is pretty nifty (and free).  Check it out.

---

