---
title: "update on 13.04 today"
date: 2013-02-25
forum: Ubuntu Development Version
---

### Post by IYII3r41n on 2013-02-25
I tried to update my system today and recieved an error. 
Here are my system specs
```
LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu Raring Ringtail (development branch)
Release:    13.04
Codename:    raring
```I ran sudo apt-get update. All went fine. I ran sudo apt-get upgrade and got this...
```

Reading package lists... Done Building dependency tree        Reading state information... Done Correcting dependencies... Done The following extra packages will be installed:   gtk2-engines-pixbuf The following packages will be upgraded:   gtk2-engines-pixbuf 1 upgraded, 0 newly installed, 0 to remove and 31 not upgraded. 3 not fully installed or removed. Need to get 0 B/131 kB of archives. After this operation, 742 kB disk space will be freed. Do you want to continue [Y/n]? y (Reading database ... 245392 files and directories currently installed.) Preparing to replace gtk2-engines-pixbuf:amd64 2.24.14-0ubuntu1 (using .../gtk2-engines-pixbuf_2.24.16-1ubuntu1_amd64.deb) ... Unpacking replacement gtk2-engines-pixbuf:amd64 ... dpkg: error processing /var/cache/apt/archives/gtk2-engines-pixbuf_2.24.16-1ubuntu1_amd64.deb (--unpack):  trying to overwrite shared '/usr/share/doc/gtk2-engines-pixbuf/README.gz', which is different from other instances of package gtk2-engines-pixbuf:amd64 No apport report written because MaxReports is reached already                                                               dpkg-deb: error: subprocess paste was killed by signal (Broken pipe) Errors were encountered while processing:  /var/cache/apt/archives/gtk2-engines-pixbuf_2.24.16-1ubuntu1_amd64.deb E: Sub-process /usr/bin/dpkg returned an error code (1)
```
Any suggestions?

---

### Post by howefield on 2013-02-25
Thread moved to the "*Ubuntu +1 (Raring Ringtail)*" forum.

---

### Post by ft_ on 2013-02-25
yep : update/upgrade now ! It works.
If you can't : sudo apt-get remove gtk2-engines-pixbuf
and the packages which need this one (audacious, for my case).

---

### Post by IYII3r41n on 2013-02-25
> **ft_ said:**
> yep : update/upgrade now ! It works.
If you can't : sudo apt-get remove gtk2-engines-pixbuf
and the packages which need this one (audacious, for my case).

I tried what you suggested. No luck. I got the same error as listed above. 

update/upgrade no luck, 

sudo apt-get remove gtk2-engines-pixbuf gives me same error as upgrade. 

any other suggestions?

---

### Post by mcellius on 2013-02-25
I'm having the exact same problem, after today's updates.  I updated and upgraded about seven hours ago, and haven't been able to fix the problem yet: I'm hoping that it'll get fixed in an upcoming update.

I also tried the fixes that were suggested to you, also without success.

---

### Post by IYII3r41n on 2013-02-25
I just tried to submit a bug report, and I got an error saying it can't be reported. I hope you're right and it gets fixed in a new update.

---

### Post by ft_ on 2013-02-25
I've got exactly the same problem, and I can guarantee you that it is solved for me.
I did a lot of commands, with not a lot of success. I did not remember the exact sequence...

Try (in any order) :
apt-get clean
apt-get remove -f gtk2-engines-pixbuf (+ packages depending on)
apt-get -f install
apt-get update/dist-upgrade

I did not perform any state-of-the-art command !

---

### Post by mcellius on 2013-02-25
I tried all those commands earlier without success, but I just ran them again.  No change.

I also can't report the error.

---

### Post by mc4man on 2013-02-25
was an issue - 
[https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/1132881](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/1132881)
& was fixed

---

### Post by mcellius on 2013-02-25
Cool!  I just ran updates & upgrades again, and it all worked!  Excellent; back to normal.  Thanks!

---

### Post by IYII3r41n on 2013-02-25
Beautiful. A quick -f install,  and back in business. Thanks for all the quick responses and suggestions.

---

