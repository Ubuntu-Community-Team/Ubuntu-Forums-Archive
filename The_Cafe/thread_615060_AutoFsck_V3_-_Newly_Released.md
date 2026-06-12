---
title: "AutoFsck V3 - Newly Released"
date: 2007-11-16
forum: The Cafe
---

### Post by musther on 2007-11-16
AutoFsck V3 has just been released over at:
[http://wiki.ubuntu.com/AutoFsck](http://wiki.ubuntu.com/AutoFsck)

The list of new features looks something like this:
KDM Support (for kubuntu etc)
A configuration GUI - allows configuration of:
   Audio prompt (can be disabled/enabled)
   Check can be done on shutdown or after a quick reboot (machine is then halted)
      The reboot method is default as it is more reliable.
   Frequency of checks (max_mount_count) can be changed from the GUI
   A test can be run (checks are set up on user command)
Some more under-the-hood changes.

There's also now an AutoFsck announcements list so you can keep track of new releases:
[http://www.flamingfatherland.org/software/autofsck/subscribe.php?action=signup](http://www.flamingfatherland.org/software/autofsck/subscribe.php?action=signup)

---

### Post by Tundro Walker on 2007-11-17
Awesome!

I love this program.  I'm all for anything that can delay maintenance tasks till AFTER I'm done using the computer.

Wish someone would go a step further and make  system updates do the same thing.  You know, instead of nagging you to run them in manually or behind the scenes while you're trying to use the computer, instead just wait until log-off / shutdown to run in the updates.

I personally am the type that shuts down my computer after I use it to save power and noise, so maybe I'm in the minority here.

Anyways, love this script.

---

### Post by musther on 2007-11-17
It would be pretty easy to write a script which would do what you want with the updates, email me and I'll write you one:
[email]jmusther@gmail.com[/email]

---

### Post by BigSilly on 2008-01-01
Just started using this, and I'd like to say a big thank you to the author. Very useful tool, and it's nice to have proper visible control over what fsck gets up to. It's especially useful to me at the moment as my fsck is playing up on Ubuntu, but even regardless of that it's a tool I would always hope to use on Ubuntu.

Thanks, and a Happy New Year.

---

### Post by henriquemaia on 2008-01-06
Thanks for posting the link to this app. I was just looking for this, after having to wait almost 10 minutes for my laptop to start because of fsck disk checking.

---

### Post by houstonbofh on 2008-02-29
Vote for this app at [http://brainstorm.ubuntu.com/idea/1031/](http://brainstorm.ubuntu.com/idea/1031/) if you like it.

---

### Post by RAV TUX on 2008-02-29
> **musther said:**
> AutoFsck V3 has just been released over at:
[http://wiki.ubuntu.com/AutoFsck](http://wiki.ubuntu.com/AutoFsck)

The list of new features looks something like this:
KDM Support (for kubuntu etc)
A configuration GUI - allows configuration of:
   Audio prompt (can be disabled/enabled)
   Check can be done on shutdown or after a quick reboot (machine is then halted)
      The reboot method is default as it is more reliable.
   Frequency of checks (max_mount_count) can be changed from the GUI
   A test can be run (checks are set up on user command)
Some more under-the-hood changes.

There's also now an AutoFsck announcements list so you can keep track of new releases:
[http://www.flamingfatherland.org/software/autofsck/subscribe.php?action=signup](http://www.flamingfatherland.org/software/autofsck/subscribe.php?action=signup)


Nice work, Thanks for the announcement. ;)

---

### Post by bubieyehyeh on 2008-03-02
> **musther said:**
> 
There's also now an AutoFsck announcements list so you can keep track of new releases:
[http://www.flamingfatherland.org/software/autofsck/subscribe.php?action=signup](http://www.flamingfatherland.org/software/autofsck/subscribe.php?action=signup)

I'm getting the following error messages on that url

Warning: require_once() [function.require-once]: URL file-access is disabled in the server configuration in /home/djp/public_html/ffl/software/autofsck/subscribe.php on line 4

Warning: require_once([http://www.flamingfatherland.org/head.html](http://www.flamingfatherland.org/head.html)) [function.require-once]: failed to open stream: no suitable wrapper could be found in /home/djp/public_html/ffl/software/autofsck/subscribe.php on line 4

Fatal error: require_once() [function.require]: Failed opening required 'http://www.flamingfatherland.org/head.html' (include_path='.:/usr/lib/php:/usr/local/lib/php') in /home/djp/public_html/ffl/software/autofsck/subscribe.php on line 4

---

### Post by musther on 2008-03-02
Sorry about that, I'll take a look at it when I get chance, very busy at the moment, but I'll do it ASAP.

---

