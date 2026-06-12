---
title: "Extra account 'dirmngr' appears on login screen (once)"
date: 2014-02-27
forum: Security
---

### Post by Adam's AI on 2014-02-27
I was logging into a machine today, and in addition to the usual options (my account, remote login) there was a third option called dirmngr.
I logged out and it was gone, and restarted the machine and it was still gone, but I found it strange that it was there as I had never seen it before.
Does this suggest a security problem?

Thanks

---

### Post by papibe on 2014-02-27
Hi Adam's AI.

Did you install dirmngr?

Could you open a terminal, run these commands, and post back its results? (you can copy/paste the text):
```
apt-cache policy dirmngr

grep -i dirmngr /etc/passwd
```
Regards.

---

### Post by Adam's AI on 2014-03-01
> **papibe said:**
> Hi Adam's AI.

Did you install dirmngr?

Could you open a terminal, run these commands, and post back its results? (you can copy/paste the text):
```
apt-cache policy dirmngr

grep -i dirmngr /etc/passwd
```
Regards.

Thanks for the reply!
I did not install dirmngr on its own -- I don't know if it somehow go installed with some other software, but on this comp I haven't installed too much other than stock ubuntu, a few common programs, and a few other DEs.

apt-cache policy dirmngr yields:
```

dirmngr:
  Installed:  1.1.1-1.1
  Candidate:  1.1.1-1.1 
  Version table:
 *** 1.1.1-1.1 0
        500 http://archive.ubuntu.com/ubuntu/ saucy/universe amd64 Packages
        100 /var/lib/dpkg/status

```

grep -i dirmngr /etc/passwd yields:
```
dirmngr:x:116:126::/var/cache/dirmngr:/bin/sh
```

---

### Post by papibe on 2014-03-03
Thanks.

It looks like the package is installed, and the user exists.

It looks like a minor bug. Since only users with id > 1000 should be displayed on the login screen. If it happens again, I would reported in [Launchpad]("https://bugs.launchpad.net/ubuntu").

Regards.

---

### Post by Adam's AI on 2014-03-05
> **papibe said:**
> Thanks.

It looks like the package is installed, and the user exists.

It looks like a minor bug. Since only users with id > 1000 should be displayed on the login screen. If it happens again, I would reported in [Launchpad]("https://bugs.launchpad.net/ubuntu").

Regards.

That is reassuring. Thanks alot for the help!

---

