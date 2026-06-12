---
title: "SSH users-admin"
date: 2011-03-21
forum: Security
---

### Post by ThePol1 on 2011-03-21
I am running Ubuntu 10.10 amd64 on a headless server and using x11 to forward the desktop for administration purposes. I can't seem to modify user rights using users-admin, however. I've tried 'gksudo users-admin' and 'sudo users-admin'. Those bring up the screen but it is blank (hour glass keeps spinning) and no user information is ever displayed. I've also tried just launching 'users-admin'. In this case it brings up the screen with my users but when I right-click and select user preferences or click the Advanced button nothing happens.

I've also tried launching gnome panel using 'ssh -X -C -c blowfish user@server gnome-panel'. When I select users-admin the password dialogue pops up (for my sudo password) but I still can't administer any user properties or click the Advanced button.

What am I doing wrong?

---

### Post by CharlesA on 2011-03-21
It think it's something to do with being connected remotely. I think it's a setting in policy-kit, but I am not sure.

I just know that I ran into the same thing a while back but now I just add new users via the command line.

---

### Post by ThePol1 on 2011-03-21
> **CharlesA said:**
> It think it's something to do with being connected remotely. I think it's a setting in policy-kit, but I am not sure.

I just know that I ran into the same thing a while back but now I just add new users via the command line.

Can you point me to a good guide on how to add specific user permissions via the command line? I would like to give a particular user the ability to Mount FUZE File Systems, for example. I can do it in 5 seconds via the GUI but can't seem to find a way to do it via command line.

---

### Post by ThePol1 on 2011-03-21
> **ThePol1 said:**
> Can you point me to a good guide on how to add specific user permissions via the command line? I would like to give a particular user the ability to Mount FUZE File Systems, for example. I can do it in 5 seconds via the GUI but can't seem to find a way to do it via command line.

I think I found the answer to my own question:
[http://ubuntuforums.org/showthread.php?t=866126](http://ubuntuforums.org/showthread.php?t=866126)

---

### Post by CharlesA on 2011-03-21
That sounds about right.

EDIT: found a couple of the threads I posted a while ago on it:

[http://ubuntuforums.org/showthread.php?t=1291617](http://ubuntuforums.org/showthread.php?t=1291617)
[http://ubuntuforums.org/showthread.php?t=1288021](http://ubuntuforums.org/showthread.php?t=1288021)

---

