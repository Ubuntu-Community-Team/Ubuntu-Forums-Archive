---
title: "GPG error?"
date: 2005-10-14
forum: Repositories &amp; Backports
---

### Post by theplatypus on 2005-10-14
> W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>


Any ideas?

---

### Post by A-star on 2005-10-14
Same problem here.
No solution yet.

---

### Post by 1sy8 on 2005-10-14
Same here .. but with breezy-updates ??
> W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

---

### Post by kudu on 2005-10-16
Same here, Breezy updates:

BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

What the heck ?

kudu

---

### Post by moopere on 2005-10-16
[QUOTE=kudu]Same here, Breezy updates:

BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

What the heck ?

kudu[/QUOTE]

Try this:

[http://www.ubuntuforums.org/showthread.php?p=416599&posted=1#post416599](http://www.ubuntuforums.org/showthread.php?p=416599&posted=1#post416599)

---

### Post by andril on 2005-10-16
Add another user - scratching his head. I get the same error!

---

### Post by joshmachine on 2005-10-19
Sometimes it's just a bug, and not your fault.  I have created a bug at:

[https://bugzilla.ubuntu.com/show_bug.cgi?id=18088](https://bugzilla.ubuntu.com/show_bug.cgi?id=18088)

Cheers,
Josh

---

### Post by rumix on 2005-10-20
Same problem here...

---

### Post by kiwibird on 2005-10-20
Is there a fix for this yet? Getting the same thing myself...

---

### Post by bryan986 on 2005-10-20
Another here
```
W: GPG error: http://archive.ubuntu.com breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
```

---

### Post by jklick on 2005-10-20
I'm also getting the same error.

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

---

### Post by jgaynor on 2005-10-23
me as well:
> 
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

---

### Post by mapman on 2005-10-23
Yes, myself as well.  Then I run another sudo apt-get update soon after and I don't get the error.:confused:

---

### Post by ivago on 2005-10-25
same prob here... tired switchin' my sources.list and such without luck.. running apt-get update a few times is not the solution... this bug keeps comin back and back and back... :( man i wish i'd found the holy distro :wink:

---

### Post by billiejoex on 2005-10-25
It seems to be a repository server problem not regarding the distro itself.

---

### Post by heyanowut on 2005-10-25
Try this from

[http://www.linuxquestions.org/questions/showthread.php?s=&threadid=373441&highlight=GPG](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=373441&highlight=GPG)

1) Restore the default keys in Synaptic (settings > repositories > authentication > restore desault keys

2)

    code:

sudo apt-get clean



3) Change the repositories (/etc/apt/sources from [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) to [http://archive.ubuntu.com](http://archive.ubuntu.com) This actually got rid of one of the BADSIG instances but I still had one......

4) Commented out the cd in /etc/apt/sources

Finally::

5) I found on another forum, the suggestion to create a new /var/lib/apt/lists folder. (you also need a new lists/partial folder...) I renamed my old lists folder then created a new one with:

    code:

:/var/lib/apt$ sudo mkdir -p lists/partial



Then one more

    code:

sudo apt-get clean


    code:

apt-get update

This worked for me (so far) but I don't seem to be getting many updates. Thanks to jkmb111.

---

### Post by thepete on 2009-11-23
heyanowut... it's four years later and your advice fixed things for me! Thank you!!  I've been looking for a solution for days and following the process you detail above from 1-3 solved my problem. I can now install.  YES!

---

### Post by devilgate on 2010-01-16
Like thepete, it's years later, I'm on Jaunty, yet the  solution here worked for me.  I had to remove "gb.", rather than "us.", since I'm in the UK, but otherwise the same.

---

### Post by cadaverousmob on 2010-06-11
Using Lucid 10.04 and jkmb111's (per heyanowut) solution still works!

---

### Post by addroof on 2010-09-27
It still works for me 
Thank you

---

### Post by bobnn on 2010-12-10
> **heyanowut said:**
> Try this from

Finally::

5) I found on another forum, the suggestion to create a new /var/lib/apt/lists folder. (you also need a new lists/partial folder...) I renamed my old lists folder then created a new one with:

    code:

:/var/lib/apt$ sudo mkdir -p lists/partial



Then one more

    code:

sudo apt-get clean


    code:

apt-get update

This worked for me (so far) but I don't seem to be getting many updates. Thanks to jkmb111.

This part, by itself, worked for me on Ubuntu 10.04 LTS.  And it's **5 years later** - why don't they fix this thing?  It's still the exact same message: "BADSIG 40976EAF437D05B5..."

---

### Post by Ve5ahchoo8ah on 2011-01-13
Worked for me after 6 years!!

---

### Post by aloyr on 2011-08-31
this worked for me, but i had to ADD the 'us.' to the sources.list...

---

### Post by euroford on 2011-12-20
The most easy way is remove the temp file in /var/lib/apt/lists/partial, and sudo apt-get update.

---

