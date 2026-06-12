---
title: "How can I verify that installed packages have not been tampered with?"
date: 2007-02-25
forum: Server Platforms
---

### Post by mjgumbley on 2007-02-25
How can I verify that the contents of a package are correct, i.e. checking that the individual files have not been altered, either via file date/times, checksums, digital signatures, etc?

I couldn't find anything obvious in the various apt, dpkg man pages, Linux in a Nutshell, etc.


Thanks,
Matt

---

### Post by kwambus on 2007-02-26
Not sure exactly if you mean changed before you install them, or changed when running on your live machine. In any case I have used OSSEC-HIDS for a long time. As well as intrusion detection the package maintains a watchful eye for files changing size and checksum on your system, even root-kit detection.

Further information at:
[http://www.ossec.net/](http://www.ossec.net/)

Ubuntu install instructions:
[http://doc.gwos.org/index.php/Setup_OSSEC-HIDS](http://doc.gwos.org/index.php/Setup_OSSEC-HIDS)

Hope this helps, if not try it anyway :)

---

### Post by yota on 2007-02-26
You can use the "debsums" command from the homonym package to check each file of a given package:
> 
yota@linbook:~$ debsums binutils
/usr/share/man/man1/ar.1.gz                                                   OK
/usr/share/man/man1/as.1.gz                                                   OK
/usr/share/man/man1/gprof.1.gz                                                OK
/usr/share/man/man1/nm.1.gz                                                   OK
/usr/share/man/man1/objdump.1.gz                                              OK
/usr/share/man/man1/ranlib.1.gz                                               OK
/usr/share/man/man1/readelf.1.gz                                              OK
/usr/share/man/man1/size.1.gz                                                 OK
/usr/share/man/man1/strings.1.gz                                              OK
....


Hope this helps!

---

### Post by mjgumbley on 2007-02-26
Yota, that looks like the sort of thing I need. Many thanks.
Essentially, I want to see if files have been compromised since I installed/updated them.

I run AIDE, but haven't reset its database since starting it - and I've upgraded packages quite a bit since then - so I want to see if any files have changed from the package database..

I'll also certainly check out OSSEC-HIDS, thanks kwambus.

---

### Post by mjgumbley on 2007-02-26
For the archive, a useful page relating to this is
[http://ch.tudelft.nl/~arthur/recovery.html](http://ch.tudelft.nl/~arthur/recovery.html)

---

### Post by dannyboy79 on 2007-02-26
tripwire is awesome. i use that and it runs thru cron every day and informs me of ANY changes to a database that you create after installing tripwire. i have a good tw.pol file if you'd like to use it. this is the policy file for what tripwire looks for when comparing your database you created (it's created to basically setup a "base" of what your system looks like whne you know it hasn't been  tampered with. i also have a good tw.cfg file, that's the config file for tripwire for various settings. so really tripwire should be installed immediately after a fresh install)  tripwire is in the universe repo. it does tell you when checksum changes and tons of other stuff.

---

### Post by mjgumbley on 2007-03-08
Presumably, debsums is checking the checksums against a local copy of a package's checksums - so if I were a hacker, I'd modify a binary, and the checksum database, and so after running debsums, one wouldn't be any wiser....

Is there anything that checks package contents against those on the repositories? Can I ask debsums to get the ckecsums from the repositories?

Thanks,
Matt

---

### Post by dannyboy79 on 2007-03-08
again, I would suggest using tripwire, you would install tripwire right after you have your machine the way you want it, it would create the database of all the checksums, dates, who wrote the file etc etc. then you keep this database and all tripwire config files on a floppy, then when you run tripwire, you compare it against the database. eventually YOU will make chnages to your system, that's when you "update" your tripwire database and resave it to your floppy. it's probably more than what you are looking for, but you can easily customize it to only check the checksums if you want.

---

### Post by mjgumbley on 2007-03-12
Yes, a proper IDS (intrusion detection system) is what I'm aiming for - so I installed AIDE when I first started with Ubuntu... (don't seem to recall tripwire being available?) since then I haven't updated my checksum database after upgrading components.... so am looking for a way of verifying exactly what is correct, and what I might have modified - without letting any files that might have been modified without my consent through. Then, when I'm sure that I've got a valid, uncompromised installation, reset AIDE, and start using it properly as you suggest, updating its database on removable media after each upgrade.

Regards,
Matt

---

