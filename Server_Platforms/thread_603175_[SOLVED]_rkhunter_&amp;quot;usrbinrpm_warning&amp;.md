---
title: "[SOLVED] rkhunter: &amp;quot;/usr/bin/rpm warning&amp;quot;?!!!"
date: 2007-11-04
forum: Server Platforms
---

### Post by odiseo77 on 2007-11-04
Hi people, I installed rkhunter and chkrootkit a few days after I installed Gutsy. Had not executed rkhunter until now. Well, the point is this: I just ran rkhunter and got the following warning:

```
Performing file properties checks
    Checking for prerequisites                               [ OK ]
(...)
/usr/bin/rpm                                             [ Warning ]
```

So I checked the rkhunter log file and I found this:

```
22:22:36]/usr/bin/rpm                                      [ Warning ]
[22:22:36] Warning: The file '/usr/bin/rpm' exists on the system, but it is not present in the rkhunter.dat file.
```

So, what does this mean? Am I possibly infected with some kind of unknown rootkit or cracked or something?

If this helps, I checked this /usr/bin/rpm file thinking that it might be a symbolic link to another application, but it isn't; this is what I got:

```
ls -l /usr/bin/rpm
-rwxr-xr-x 1 root root 80708 2007-09-12 12:00 /usr/bin/rpm
```

hmmm, I had used rkhunter before and had found some warnings (fake positives, I think), but nothing like this before :confused:

I checked, and I have the rpm package installed (I think it's a dependency of 'alien' which I use sometimes to convert packages), and it provides this file (/usr/bin/rpm), but what exactly do this rkhunter warning mean? 

Thanks in advance for your answers.

---

### Post by odiseo77 on 2007-11-05
Hi again. I found in another forum I had to run ***sudo rkhunter --propupd*** in order to update the rkhunter cache file. After I did it, I did a re-scan of my system and the warning disappeared. 

As a side note, I installed alien (with the rpm dependency included) on another Gutsy machine, did the rkhunter scan and got the same warning; then I checked the md5sum and sha1 sum of the /usr/bin/rpm executable on both machines and they matched exactly, so everything's ok.

---

### Post by kwilliam on 2008-05-30
Thanks! I got a similar warning after installing /usr/bin/mail... in order to read the reports that rkhunter had been sending me ironically. That command did the trick for me!

---

