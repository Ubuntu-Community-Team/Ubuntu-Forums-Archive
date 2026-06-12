---
title: "ulimit -n for non root users?"
date: 2008-05-01
forum: Security
---

### Post by chalk-t on 2008-05-01
I'm having problems with ULIMIT -n:

Once having stuffed eclipse with several plugins, it's keeping all those jars open, thus running out of file descriptors.

So I first naively tried 

    ulimit -n 4096 

and got:

    bash: ulimit: open files: cannot modify limit: Operation not permitted

Searching the web, I got serveral hints, all to no avail:

Hint one: configure /etc/security/limits.conf

I tried the following entries.

* soft nolimit 4096
* hard nolimit 65572

eclipseuser soft nolimit 4096
eclipseuser hard nolimit 65572

root soft nolimit 4096
root hard nolimit 65572

This did help for root, but had no effect for the other users,
even after reboot (asside: would a reboot have been necessary?)

Hints two to n: place ulimit -n 4096 in any of:
 /etc/profile
 /etc/.bashrc
 ~/.profile
 ...

where ever I tried that, I got 
bash: ulimit: open files: cannot modify limit: Operation not permitted

unless, I'm running as root!!

Well I'm feeling a bit quesy running eclipse as root with all that plugins. 

:confused:

So how do I *really* expand the filelimits for a non root user? Preferably without having to sudo?


Oh btw. I'm now running xubuntu HH on AMD64, but had the same problem on GG.

---

### Post by mikko.ohtamaa on 2008-07-06
This worked for me. No reboot needed, just relogin.

[http://ubuntuforums.org/archive/index.php/t-521287.html](http://ubuntuforums.org/archive/index.php/t-521287.html)

---

### Post by peterramesh on 2009-06-16
I also faced the same issue,

In my case, If I 'eclipseuser' user logged via ssh to the same host, then I able to set the ulimit (the value should be less than the value specified in limit.conf file)

---

