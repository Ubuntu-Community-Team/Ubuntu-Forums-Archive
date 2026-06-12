---
title: "synaptic cant load packages's changelog"
date: 2012-05-23
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by dino99 on 2012-05-23
Since a while when i want to view the updates changelog with synaptic, i only get a dialog box warning telling to view it via the source archive.
Do you get the same issue ?

[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1001872](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1001872)

---

### Post by ScislaC on 2012-05-23
Confirmed for you as I have experienced it as well

---

### Post by mc4man on 2012-06-01
This seems to be affecting more than 12.10, same thing is happening in 12.04, maybe others?
Both update-manager & synaptic can't display/get changelogs for packages that have recently updated

---

### Post by cariboo on 2012-06-01
It may be a problem with the automated build system, as there are quite a few change-logs missing on the quantal-changes mailing list too.

---

### Post by dino99 on 2012-06-01
> **cariboo907 said:**
> It may be a problem with the automated build system, as there are quite a few change-logs missing on the quantal-changes mailing list too.

its a wide issue

[https://bugs.launchpad.net/ubuntu/+bug/1001609](https://bugs.launchpad.net/ubuntu/+bug/1001609)

---

### Post by xebian on 2012-06-01
The title is misleading as it implies synaptic has a problem when in fact it's not.  The changelogs are simply not there so there is nothing synaptic can get and display.  But synaptic actually nice to even suggest an alternative way of looking at them.

```
Err Changelog for nautilus (http://changelogs.ubuntu.com/changelogs/pool/main/n/nautilus/nautilus_3.5.1-0ubuntu4/changelog)
  404  Not Found
Err Changelog for nautilus (http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus_3.5.1-0ubuntu4.changelog)
  404  Not Found [IP: 91.189.92.153 80]
E: changelog for this version is not (yet) available; try https://launchpad.net/ubuntu/+source/nautilus/+changelog

```

---

### Post by ventrical on 2012-06-01
It works good here. I just:

sudo apt-get update
sudo apt-get upgrade

run synaptic , item,  changelogs are there.

---

### Post by ventrical on 2012-06-01
Whopps! Reboot and:

---

### Post by mc4man on 2012-06-06
Seems to a continuing issue, quite unfortunate for all affected Ubuntu releases. 
Represents even a bit more of a pita now in 12.10, the 'new' Software Updater doesn't even get active links anymore. (The text updater version at least has  working right click options for the truncated changelogs

All in all a poor response from Canonical..

---

### Post by Yellow Pasque on 2012-06-09
I agree that it needs more attention, so I've raised the issue in #ubuntu-bugs. We're having a hard time figuring out who/where to assign it to so that it might get the attention it deserves.

---

### Post by balloons on 2012-06-11
I noticed this as well, and I subscribed to the bug. I will try and raise up more visibility to this. One of the changes requested @ UDS (which came from the U+1 team) was to have the update manager (software updater) give a nice changelog for all the changes at one glance and in general be more informative of what's happening. This is a step backwards from that :-(.

---

### Post by balloons on 2012-06-13
Thanks for noticing this guys, I followed up and updated the bug with the status :-)

---

### Post by mc4man on 2012-06-22
I'm now getting changelogs today, excellent..

---

### Post by dino99 on 2012-06-23
Got the latest Quantal updates and changelogs are viewable again directly from synaptic. Thats a good news, but have not seen comments about that fix.

---

### Post by balloons on 2012-06-25
> **dino99 said:**
> Got the latest Quantal updates and changelogs are viewable again directly from synaptic. Thats a good news, but have not seen comments about that fix.

The short end was it needed new hardware. After you brought up the issue, I pinged and checked on the status to keep things rolling :-) New hardware is in place and we get logs again :-)

---

