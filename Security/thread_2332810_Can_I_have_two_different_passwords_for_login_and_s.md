---
title: "Can I have two different passwords for login and sudo?"
date: 2016-08-04
forum: Security
---

### Post by mikey93898 on 2016-08-04
Hey all,

I have a huge long complicated password to login, so my home folder encryption is a bit stronger. However, this then means using sudo is a huge pain. I'd like to use a slightly easier sudo password... something a malicious script or snooping user couldn't crack without effort, but also something easier on my fingers when I issue many sudos in many terminal windows. Say for instance, my login password is 30 characters long, and I'd like my sudo password (or a second addon password) to be only 8.

Is this possible?

And before you say full system encryption... I hear you, and I agree. I just can't because I'm on a wireless keyboard and I couldn't figure out how to get its drivers loaded before the encryption password prompt (thus, my keyboard didn't work at all with full system encryption). Although, if anyone has an answer to that problem in particular, I might prefer it.

---

### Post by yoshii on 2016-08-04
One possible workaround is to use the Root Terminal carefully.  I think it's found in /usr/share/applications as a .desktop file after being installed.  It's the red coloured command line computer screen icon.  What it does is sets things to root use in that window so you don't have to keep typing sudo.  And then when you close that window, it's back to normal.  That's an oversimplification, but the general idea.  

I am not entirely certain how to get access to it.  I had some trouble getting to in on one distro, but it was installed readily on a different distro (both ubuntu systems).  


Here's where more info on this topic is:  

[http://bbb-solutions.blogspot.com/2014/11/how-to-become-root-in-ubuntu.html](http://bbb-solutions.blogspot.com/2014/11/how-to-become-root-in-ubuntu.html)
[http://tombuntu.com/index.php/2007/12/page/3/](http://tombuntu.com/index.php/2007/12/page/3/)

---

