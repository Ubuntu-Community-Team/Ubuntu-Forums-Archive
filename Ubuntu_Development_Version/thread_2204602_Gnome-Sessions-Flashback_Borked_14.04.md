---
title: "Gnome-Sessions-Flashback Borked 14.04"
date: 2014-02-09
forum: Ubuntu Development Version
---

### Post by NM5TF on 2014-02-09
have been running Trusty just fine since it was released for testing..:p

so yesterday for some stooooopid reason I thot I would install gnome-
sessions-flashback just to try it out..;)

it seemed to install without any problems/errors and when I rebooted
I got to the Ubuntu log-in screen & was presented with 3 choices:

     1.) Gnome Fallback with Compiz
     2.) Gnome Fallback with METACITY
     3.) Ubuntu Classic

However no matter which choice I use it appears to log-in, leaves the 
log-in screen, but then loops right back to the log-in screen....appears
to not accept my password :confused:

never get any error messages, it just keeps looping back to log-in screen](*,)

I have tried going to recovery mode with no luck:-(

```
sudo service lightdm restart
``` has no effect either :cry:

am running out of ideas...

right now I would be happy just to get back to having Unity working....***NEVER***
thot I would say that !!!

any help to get back to working greatly appreciated !!!

tommy

luckily my Ubuntu 12.04.4 & Mint 16 distros still work :p

---

### Post by muktupavels on 2014-02-09
If you can not login in unity session too than I would not say that flashback session is borked.

Try remove .Xauthority file. Read more here - [http://ubuntuforums.org/showthread.php?t=1859272](http://ubuntuforums.org/showthread.php?t=1859272).

---

### Post by NM5TF on 2014-02-09
thanx for reply....

will try your suggestion & report back

tommy

---

### Post by NM5TF on 2014-02-09
big thanx @albersmuktupavels :guitar:

back to unity desktop like it was before I broke it...:p

tommy

---

### Post by muktupavels on 2014-02-09
Did you test flashback session? Does it work for you?

---

### Post by NM5TF on 2014-02-09
> **albertsmuktupavels said:**
> Did you test flashback session? Does it work for you?

have not tried it yet.....just glad to have OS working again....just may stay with Unity for now...

thanx for the help...

tommy

---

