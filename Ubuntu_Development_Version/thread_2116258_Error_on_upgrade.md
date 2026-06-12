---
title: "Error on upgrade"
date: 2013-02-15
forum: Ubuntu Development Version
---

### Post by mcellius on 2013-02-15
I tried to run ```
sudo apt-get update && sudo apt-get upgrade
``` in Raring and got the following error:
```

99 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/120 MB of archives.
After this operation, 677 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: error: parsing file '/var/lib/dpkg/available' near line 0:
 field name `#' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

I've been running Raring on this computer for a couple months, and have been running updates and upgrades daily; this is the first problem I've had of this sort. Anyone else?  Anyone know how to fix it?

---

### Post by zika on 2013-02-15
> **mcellius said:**
> I tried to run ```
sudo apt-get update && sudo apt-get upgrade
``` in Raring and got the following error:
```

99 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/120 MB of archives.
After this operation, 677 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: error: parsing file '/var/lib/dpkg/available' near line 0:
 field name `#' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

I've been running Raring on this computer for a couple months, and have been running updates and upgrades daily; this is the first problem I've had of this sort. Anyone else?  Anyone know how to fix it?
In Your place, I would try moving /var/lib/dpkg/available to some other place or (simply) renaming it (/var/lib/dpkg/available.zika for example) and trying update/upgrade again...

---

### Post by schragge on 2013-02-15
You can safely delete /var/lib/dpkg/available.
```
sudo dpkg --clear-avail
```
It's rarely used nowadays (the main user is dselect), and can be easily recreated if needed by dselect or aptitude from the apt package database:
```
sudo aptitude update
```
or
```
sudo dselect --expert update
```

Note that *sudo apt-get update* doesn't update */var/lib/dpkg/available*

---

### Post by mcellius on 2013-02-15
Zika: Thank you!  I tried this:

> In Your place, I would try moving /var/lib/dpkg/available to some other  place or (simply) renaming it (/var/lib/dpkg/available.zika for example)  and trying update/upgrade again...It didn't work.  I got this:

```
dpkg: error: failed to open package info file `/var/lib/dpkg/available' for reading: No such file or directory
E: Sub-process /usr/bin/dpkg returned an error code (2)
```Apparently it needs that file.  (But I did, in your honor, rename the file to "available.zika".)

---

### Post by zika on 2013-02-15
> **schragge said:**
> You can safely delete /var/lib/dpkg/available.
```
sudo dpkg --clear-avail
```
It's rarely used nowadays (the main user is dselect), and can be easily recreated if needed by dselect or aptitude from the apt package database:
```
sudo aptitude update
```
or
```
sudo dselect --expert update
```

Note that *sudo apt-get update* doesn't update */var/lib/dpkg/available*
I did not use aptitude in weeks but still file /var/lib/dpkg/available carry the time and date of my last update/upgrade via apt-get several minutes ago... Not the time of update but of one of these:
```
:~$ alias UPALL
alias UPALL='/usr/bin/sudo /usr/bin/apt-get update ; /usr/bin/sudo /usr/bin/apt-get upgrade ; /usr/bin/sudo /usr/bin/apt-get clean ; /usr/bin/sudo /usr/bin/apt-get --purge autoremove'
```

---

### Post by zika on 2013-02-15
> **mcellius said:**
> Zika: Thank you!  I tried this:

It didn't work.  I got this:

```
dpkg: error: failed to open package info file `/var/lib/dpkg/available' for reading: No such file or directory
E: Sub-process /usr/bin/dpkg returned an error code (2)
```Apparently it needs that file.  (But I did, in your honor, rename the file to "available.zika".)That is why I suggested You to rename, so that it can be returned if needed... ;)

---

### Post by schragge on 2013-02-15
Well, obviously it's presence gets checked by dpkg, but the information in it doesn't get used by apt-get. As said, you can
```
sudo dpkg --clear-avail
``` any time.

On my system, I use custom /var/lib/dpkg/available that contains only packages with priority standard or higher. I generate it from /var/lib/apt/lists/* with a script.

[highlight]Update.[/highlight]
Besides dselect, the only other command I can think of that evaluates it is dpkg -l (for not installed packages).

---

### Post by mcellius on 2013-02-15
Schragge:  That worked, thank you!

Just to be obsessive about everything, I copied available.zika back, then followed your instructions for clearing it.  I then ran update and upgrade again, and it made it all the way through.  Excellent!

Thank you, both of you, for your help.  I was figuring I was just going to need to reinstall Raring - not a big deal, as it's for testing, anyway, but I didn't really want to do that today.  Now it all looks good.

---

### Post by schragge on 2013-02-15
I'm curious, what /var/lib/dpkg/availalble contains now, after you've updated the package database? I guess it's still empty even if it got timestamped during update.

---

### Post by zika on 2013-02-15
This is why I like to be on Forum like this... I learn every day... Thank You both of You. For stimulus and for new pieces of puzzle...

---

### Post by mcellius on 2013-02-15
I hate to post the entire "available" file as it is right now, since it's pretty long.  However, since I looked at it earlier when it wasn't working, I can tell you that it looks very different now.  The earlier, non-working version had lots and lots of lines commented-out (lots of #s) and now there aren't any.  (If you want me to attach it as a file, let me know.)

Once everything was working I deleted the copy of the old file (that I had named "available.zika") so I can't go back and compare any longer.

---

### Post by mcellius on 2013-02-15
0

---

### Post by schragge on 2013-02-15
Thanks, I stand corrected then. That means apt-get **does** update */var/lib/dpkg/available* even if it doesn't uses it. No need to post it, I know what it is: a text file in Debian control format like /var/lib/apt/lists/* or /var/lib/dpkg/status.

---

