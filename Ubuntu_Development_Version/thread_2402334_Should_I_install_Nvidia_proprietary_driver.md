---
title: "Should I install Nvidia proprietary driver?"
date: 2018-09-28
forum: Ubuntu Development Version
---

### Post by Hewjr100 on 2018-09-28
Currently running Ubuntu 18.10.  Nouveau-Nvidia does not work with my Nvidia GTX 1050 gpu.  To resolve this issue I blacklisted Nouveau and system is running via Intel HD 630 gpu.  All is working well, but I am wondering if installing Nvidia proprietary driver would be better.  Any thoughts on this?

Henry

---

### Post by Bashing-om on 2018-09-28
Hewjr100; Hello -

If performance is a factor, the proprietary driver wins hands down.
If it is Wayland as the DE - then nvidia is a wok in progress.

Thoughts: you may find this call of interest: 
See: [http://albertomilone.com/blog/?p=670](http://albertomilone.com/blog/?p=670)

[INDENT]we work to make it better for all
[/INDENT]

---

### Post by Hewjr100 on 2018-09-28
No Wayland for me.  Sticking with Xorg.  The reason I ask is purely a question of ram.  I upped my ram to 16 gb and want to see which gpu will utilize it the most.

Henry

---

### Post by Bashing-om on 2018-09-29
Hewjr100; Well -

lunux is going to use it all .. unused memory is wasted memory :)
have a look at:
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by Hewjr100 on 2018-09-29
Thank you for your reply.  I just hope blacklisting nouveau, and installing proprietary driver does not conflict.

Henry

---

### Post by Bashing-om on 2018-09-29
Hewjr100; Uh huh ..

Installing the correct nvidia proprietary driver is "supposed" to blacklist the nouveau driver automagically.
but,
[INDENT][INDENT]all things are not perfect
[/INDENT][/INDENT]

---

### Post by Hewjr100 on 2018-09-29
Guess I found out the hard way.  System froze after I blacklisted nouveau and then installed proprietary driver.  Gonna reinstall later.

Henry

---

### Post by Hewjr100 on 2018-09-29
Back to 18.04  Proprietary driver works without issue.

Henry

---

### Post by Bashing-om on 2018-09-29
Hewjr100; Great !

> 
18.04 Proprietary driver works without issue.

If this matter is now concluded to your satisfaction:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)


[INDENT]Happy trails to you
[/INDENT]

---

