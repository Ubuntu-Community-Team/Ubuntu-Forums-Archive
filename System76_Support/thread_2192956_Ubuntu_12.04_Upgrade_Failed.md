---
title: "Ubuntu 12.04 Upgrade Failed"
date: 2013-12-10
forum: System76 Support
---

### Post by Bill_Cole on 2013-12-10
Upgraded from 10.x to 12.04 on a Starling netbook.  After upgrade finished, reboot yielded a blinking cursor and nothing else.  Hard disk light not on ... no blinking to indicate activity.   Best way to recover from this please?

Thanks much ...

---

### Post by isantop on 2013-12-11
I'm thinking the best way to get running again after your failed upgrade would be to reinstall. You can reinstall from a Live Disk, which will preserve your home folder.

---

### Post by Bill_Cole on 2013-12-13
Thanks very much.  That worked nicely.  Fortunately I didn't have much in the way of local files stored on the machine so nothing material was lost in the process.  

I did, though, lose the System76 facility that was on the System Settings panel and wondered how I could restore that?

Very much appreciate the help and glad to have my machine back to working order.

Regards,

Bill Cole

---

### Post by traxtopel on 2013-12-13
ctrl-alt-t to open a terminal
sudo apt-add-repository ppa:system76-dev/stable
sudo apt-get update
sudo apt-get install system76-driver

---

### Post by Bill_Cole on 2013-12-15
Thank you very much for the help.  Everything worked except the last line "sudo apt-get install system76-driver" [I triple checked the spelling] which returned "Unable to locate system package system76-driver".  I double checked the repository file to make sure that "ppa:system76-dev/stable" had been added; it had.  What might I have done wrong, please?

---

### Post by isantop on 2013-12-16
What was the output of the second command?

```
sudo apt-get update
```

---

### Post by Bill_Cole on 2013-12-17
> **isantop said:**
> What was the output of the second command?

```
sudo apt-get update
```

Output: 

Fetched 2,230 kb in 4s (464 kB/s)
W: Failed to fetch [http://ppa.launchpad.net/system76-dev/stable/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/system76-dev/stable/ubuntu/dists/precise/main/binary-i386/Packages) 404 not found
E: Some index files failed to download.  They have been ignored, or old ones used instead.

---

### Post by isantop on 2013-12-17
Are you still using 12.04, or did you reinstall to 13.10?

---

### Post by Bill_Cole on 2013-12-23
> **isantop said:**
> Are you still using 12.04, or did you reinstall to 13.10?

Installed 12.04 LTS.  Old version was 10.something.

---

### Post by houstonbofh on 2014-01-01
Not sure why he did not point you here...  [http://ubuntuforums.org/showthread.php?t=2165676](http://ubuntuforums.org/showthread.php?t=2165676)

You need to pull out the PPA and just download the file.  The LTS 12.04 has no System76 love anymore...

---

### Post by Bill_Cole on 2014-01-02
Thanks much.   I'll consider this closed then, I guess.

---

