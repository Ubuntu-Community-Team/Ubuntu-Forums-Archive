---
title: "rkhunter warnings on fresh hardy install"
date: 2008-11-06
forum: Security
---

### Post by PrettyNewAtThis on 2008-11-06
Hi all,

I recently installed kubuntu Hardy Heron on an older pc at home (all default settings) and had the machine connected to my DSL for a while before thinking more deeply about security.

Slow performance and nighttime hd spinning when I happened leave it on one night led me to think it had been hacked, so I unplugged DSL and got some security tools using another computer.  chkroot didn't find anything odd, but chkproc found dozens of processes hidden from ps.  rkhunter found no rootkits but warned that these 5 commands had been replaced by shell scripts: which, groups, ldd,  lwp-request and adduser.

I repartitioned the hd (which I wanted to do anyway to get rid of a Windows partition), reinstalled Hardy using a different password, read up on security, and enabled ufw to deny all incoming traffic before putting it back on the internet to do a full update, and then I unplugged the DSL again.  After reinstalling chkrootkit and rkhunter from the same usb drive I used the first time, I got exactly the same results from chkrootkit and rkhunter.

What's up?  :confused:

Thanks for any help!

---

### Post by brian_p on 2008-11-06
> **PrettyNewAtThis said:**
> 

What's up?  :confused:


Nothing. You made an incorrect assumption from the slow performance etc and have encountered features of chkrootkit and rkhunter reporting which cause worry. Ignore the warnings and/or search these forums for other similar experiences.

---

### Post by PrettyNewAtThis on 2008-11-06
> **brian_p said:**
>  Ignore the warnings and/or search these forums for other similar experiences.

Thanks, Brian - the one thing I haven't found mentioned before in these forums or googling the web is the warning on some of the commands being replaced.  Those are known with rkhunter and Hardy?

---

### Post by brian_p on 2008-11-06
> **PrettyNewAtThis said:**
> Thanks, Brian - the one thing I haven't found mentioned before in these forums or googling the web is the warning on some of the commands being replaced.  Those are known with rkhunter and Hardy?

[http://ubuntuforums.org/showthread.php?t=785332](http://ubuntuforums.org/showthread.php?t=785332)

---

### Post by PrettyNewAtThis on 2008-11-06
Wonderful, Brian, thanks.  Don't know why I didn't find these myself, but that's exactly what I needed.  Cheers!

---

