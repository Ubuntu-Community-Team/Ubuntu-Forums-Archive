---
title: "firefox 2 crashing on ubuntu 7.10 (gutsy) sparc"
date: 2007-11-27
forum: Sun Sparc Users
---

### Post by mheise on 2007-11-27
[SIZE="4"]
Hello,

yesterday i resurrected an old Ultra 10 workstation with an ubuntu 7.10 server installation.

The install went quite smoothly. Then I proceeded to update and upgrade with
$ sudo apt-get update && sudo apt-get upgrade

After the server install completed, Ii went on to install x11.
$ sudo apt-get install xubuntu-desktop

Then I restarted the Ultra 10. Graphic login appears and I can login to a nice Xfce Desktop. Great-I just love ubuntu. 

BUT:

firefox 2 crashes reproduceably whenever I start it with a bus error
$ firefox &

I then started firefox in safe mode with
$ firefox -safe-mode &
-> now firefox starts up and I can browser websites on the local network, but when I try to set the proxy under
Edit->Preferences->Advanced, firefox crashes again with a bus error

Has anyone solved this ? Any ideas, pointers ?

I've seen posts on ubuntuforums.org suggesting to use Epiphany as a web browser, but AFAIK Epiphany is for the GNOME desktop and not for just Xfce 

Thanks

Max


[/SIZE]

---

### Post by jcastill on 2007-11-27
Hello Max, Iceape browser works also.

I tried your idea of running firefox in safe-mode ([http://ubuntuforums.org/showthread.php?t=393961](http://ubuntuforums.org/showthread.php?t=393961) that is my post) and it did work. I don't use a proxy (direct gateway) so I can access and use it without problems.

So it seems the problem is related to an addon or something else. I will try to move around and report.

Good luck and thanks for the suggestion.

Jose

---

### Post by switlikbob on 2007-12-17
Has anyone figured this out yet, or does firefox just sinply not work on the sparc platform?

---

### Post by mips on 2007-12-18
What is the full version number of firefox you are using?

---

### Post by switlikbob on 2008-01-08
Same problem here...any ideas?  I am running the latest version of Firefox on Gutsy.

---

### Post by kirsche on 2008-01-09
Seeing the same issue here on xubuntu running on VIA C7 1.2 GHz processor.
Iceape and Netscape working fine.
Still looking into it..

---

### Post by kirsche on 2008-01-09
just found this post:
[http://ubuntuforums.org/showthread.php?t=641027](http://ubuntuforums.org/showthread.php?t=641027)

not sure if its the same issue, but at least i'm using xfs here.

---

