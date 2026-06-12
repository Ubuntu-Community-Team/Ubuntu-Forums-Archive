---
title: "syslog questions"
date: 2009-02-08
forum: Server Platforms
---

### Post by inphektion on 2009-02-08
I'd like to setup a central syslog server.  Never really used it before but basic syslogd seems to be install in ubuntu server anyway.  
I see /var/log/syslog is filled with a bunch of local messages, If i start pointing other hosts to this server to use as a syslog server do their logs start showing up mixed into /var/log/syslog?

What I'd like to do is create a new dir entirely just for syslog messages and expose that to an apace virtual host so I can browse the logs over http.  I just want it to be easy to separate where the logs are coming from, does this happen automatically?

Also should I use syslog-ng or rsyslog instead?  
However if i try to install one of them aptitude complains that it would have to remove ubuntu-minimal which I'm not sure I should do...

---

### Post by inphektion on 2009-02-09
This is what i get:
> 
The following packages are BROKEN:
  ubuntu-minimal 
The following NEW packages will be automatically installed:
  dbconfig-common rsyslog 
The following packages will be automatically REMOVED:
  klogd sysklogd 
The following NEW packages will be installed:
  dbconfig-common rsyslog rsyslog-mysql 
The following packages will be REMOVED:
  klogd sysklogd 
0 packages upgraded, 3 newly installed, 2 to remove and 0 not upgraded.
Need to get 722kB of archives. After unpacking 2392kB will be used.
The following packages have unmet dependencies:
  ubuntu-minimal: Depends: sysklogd but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
ubuntu-minimal

Score is 115

Accept this solution? [Y/n/q/?] q


Doesn't seem safe to accept that... anyone?

---

### Post by inphektion on 2009-02-09
I found this:
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/42555](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/42555)

I don't like any of the solutions here as they are really just work arounds.... 

maybe I'll just compile rsyslog myself and manually stop syslogd?

---

### Post by inphektion on 2009-02-09
I think the only downside to removing ubuntu-minimal is I won't be able to upgrade to a new release easily.  So I might do that as I plan on being on hardy for a while.

---

### Post by inphektion on 2009-02-11
Well i installed from the repo's, got it all working then wanted to do some things with it that apparently only avail in newer versions.  Didn't realize the rsyslog in the repo was so old, 2-3 years.

So now I'll be installing from source again.  I'll post what I do to get it working cause it isn't straight forward.  Since this is a self conversation it'll be good for others to follow who may want latest syslog on 8.04+

---

### Post by peterhof on 2009-02-12
Kind of interested in the outcome of this.

My situation is that I want to set up a syslog server and have Windows servers write the systlog files to the Ubuntu server.

Using NTSyslog on the Windows machine, and LogCheck on the Ubuntu side to send me the alerts.

For some reason I do not receive any Windows alerts, but am getting all the Ubuntu ones.

---

### Post by inphektion on 2009-02-18
> **peterhof said:**
> Kind of interested in the outcome of this.

My situation is that I want to set up a syslog server and have Windows servers write the systlog files to the Ubuntu server.

Using NTSyslog on the Windows machine, and LogCheck on the Ubuntu side to send me the alerts.

For some reason I do not receive any Windows alerts, but am getting all the Ubuntu ones.

What outcome do you want to know?  i've made progress and there are a few ways to go about this... you have syslog on ubuntu and are looking into moving to rsyslog to hopefully get the windows alerts?  Is that it?

---

