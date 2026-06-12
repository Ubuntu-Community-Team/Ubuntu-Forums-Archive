---
title: "[SOLVED] RKHunter questions"
date: 2008-01-02
forum: Server Platforms
---

### Post by Ertai87 on 2008-01-02
So I set up rkhunter yesterday and did a scan.  It found no rootkits or other infections, but it gave me a bunch of warnings. I'm not sure if I set it up properly (I set it up using the default thingy), and I want to know what these warnings mean and if I should be concerned. Here they are:

1) One warning said I needed to run --propupd to set the base case for rkhunter. The problem is that (and keep in mind I'm a Windows user who recently switched, so I'm still in the Windows mindset) I'm not sure if I have the right files and stuff to start with. I haven't added any sources except medibuntu and the Wine base, so I should be OK, but, again, Windows mindset.

2) The other warnings I got said something about "[filename] has been replaced with [same filename]: [some modifier]" where the modifiers are POSIX shellscript executable, Bourne-again shellscript executable, or perlscript executable. What does this mean, should I care, and how do I get rid of this warning?

Thanks.

---

### Post by (((X))) on 2008-01-02
[http://ubuntuforums.org/archive/index.php/t-604068.html](http://ubuntuforums.org/archive/index.php/t-604068.html)

[http://ohioloco.ubuntuforums.org/showthread.php?p=3816644](http://ohioloco.ubuntuforums.org/showthread.php?p=3816644)

I recomend you to check your system with chkrootkit.

---

### Post by Ertai87 on 2008-01-02
OK I installed chkrootkit.  It returned all OK, except it said there were a bunch of scripts it couldn't execute.  Is this normal?

---

### Post by (((X))) on 2008-01-05
what else it it saying?

---

### Post by Ertai87 on 2008-01-05
Nevermind...it didn't compile properly...I made it compile better now, but I got some other problems.  I've continued the discussion here:

[http://ubuntuforums.org/showthread.php?t=657156](http://ubuntuforums.org/showthread.php?t=657156)

and here:

[http://ubuntuforums.org/showthread.php?t=658744](http://ubuntuforums.org/showthread.php?t=658744)

Thanks!

---

