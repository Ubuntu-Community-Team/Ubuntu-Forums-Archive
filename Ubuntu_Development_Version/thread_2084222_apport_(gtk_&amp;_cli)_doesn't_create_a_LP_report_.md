---
title: "apport (gtk &amp; cli) doesn't create a LP report on crashes"
date: 2012-11-14
forum: Ubuntu Development Version
---

### Post by mc4man on 2012-11-14
Atm a crash will produce an apport popup & if pursued create a .upload & .uploaded but no LP report
The .uploaded file is owned by whoopsie so possibly? these crashes are uploaded to a db somewhere.

The question would be is this a new way intended, atm or otherwise.
can't find any documentation on this so filed a bug to see
[https://bugs.launchpad.net/ubuntu/+source/apport/+bug/1078911](https://bugs.launchpad.net/ubuntu/+source/apport/+bug/1078911)

A bit  hesitant to post how to restore LP reporting on crashers if they aren't desired, but it's noted in the report on how to do so.
(I have until told otherwise..

---

### Post by ventrical on 2012-11-16
I think I just did this a few hours ago.

[http://ubuntuforums.org/showpost.php?p=12357852&postcount=6](http://ubuntuforums.org/showpost.php?p=12357852&postcount=6)

---

### Post by mc4man on 2012-11-16
This was specific to crashes & apport (gtk or cli
ubuntu-bug <whatever> has worked fine since the fix a ways back

On the other hand crashes which produce the pop up or using 
apport-cli /var/crash/whatever.crash seem to just upload to a db

At least here re-enabled by editing  /etc/apport/crashdb.conf as have heard nothing one way or the other on whether LP apport crash reports are desired or not.

---

### Post by ventrical on 2012-11-16
> **mc4man said:**
> This was specific to crashes & apport (gtk or cli
ubuntu-bug <whatever> has worked fine since the fix a ways back

On the other hand crashes which produce the pop up or using 
apport-cli /var/crash/whatever.crash seem to just upload to a db

At least here re-enabled by editing  /etc/apport/crashdb.conf as have heard nothing one way or the other on whether LP apport crash reports are desired or not.

Ahh .. yes..  I was thinking of something else.  

apologies..

---

