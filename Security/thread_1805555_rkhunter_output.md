---
title: "rkhunter output"
date: 2011-07-16
forum: Security
---

### Post by pastet89 on 2011-07-16
Hey, 

today I ran a rkhunter check on my ubunto 9.10.

It said:
```
    /usr/sbin/unhide                                         [ Warning ]
    /usr/sbin/unhide-linux26                                 [ Warning ]


    Checking /dev for suspicious file types                  [ Warning ]
    Checking for hidden files and directories                [ Warning ]
```
and in the log there is:

```
[14:43:05]   Checking /dev for suspicious file types         [ Warning ]
[14:43:05] Warning: Suspicious file types found in /dev:
[14:43:05]          /dev/shm/pulse-shm-3072292985: data
[14:43:05]          /dev/shm/pulse-shm-263919931: data
[14:43:05]          /dev/shm/pulse-shm-846257162: data
[14:43:05]          /dev/shm/pulse-shm-1002017371: data
[14:43:05]   Checking for hidden files and directories       [ Warning ]
[14:43:05] Warning: Hidden directory found: /etc/.java
[14:43:05] Warning: Hidden directory found: /dev/.udev
[14:43:05] Warning: Hidden directory found: /dev/.initramfs
[14:43:05] Warning: Hidden file found: /dev/.blkid.tab: ASCII text
[14:43:05] Warning: Hidden file found: /dev/.blkid.tab.old: ASCII text
[14:43:19]




```


Ny ideas what should that mean?

10x in adavnce...

---

### Post by Rubi1200 on 2011-07-16
Hi and welcome to the forums :-)

Running security tools is a bit pointless if you are not willing to do the legwork and research the results.

As it stands, there does not appear to be anything suspicious in those results.

Tools like rkhunter are notorious for producing false positives and for flagging even safe processes as warnings.

Here are some links to help you:
[http://ubuntuforums.org/showpost.php?p=9265649&postcount=8](http://ubuntuforums.org/showpost.php?p=9265649&postcount=8)
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by Dangertux on 2011-07-16
IMO false positive. Due to the way Ubuntu handles comparability with certain scripts designed for other distros.

---

### Post by Soul-Sing on 2011-07-16
ubuntu security sticky:rkhunter: [http://wiki.linuxquestions.org/wiki/Rootkit_Hunter](http://wiki.linuxquestions.org/wiki/Rootkit_Hunter)
"This page has been deleted. The deletion log for the page is provided below for reference."

---

### Post by unspawn on 2011-07-17
> **leoquant said:**
> ubuntu security sticky:rkhunter: [http://wiki.linuxquestions.org/wiki/Rootkit_Hunter](http://wiki.linuxquestions.org/wiki/Rootkit_Hunter)
"This page has been deleted. The deletion log for the page is provided below for reference."
I can't remember there was anything on the page to begin with but I'll check. In the meanwhile, instead of replying with slash to link rot, why not point to [https://help.ubuntu.com/community/RKhunter](https://help.ubuntu.com/community/RKhunter) and [http://sourceforge.net/apps/trac/rkhunter/wiki/MPRKH](http://sourceforge.net/apps/trac/rkhunter/wiki/MPRKH) instead? Way more constructive IMHO.

---

### Post by Soul-Sing on 2011-07-17
> I can't remember there was anything on the page to begin with but I'll check. In the meanwhile, 

did you check it? 

http://ubuntuforums.org/showthread.php?t=510812===> rkhunter?

[https://help.ubuntu.com/community/RKhunter](https://help.ubuntu.com/community/RKhunter) 
I started it, with a nice correction here: To run rkhunter --propupd, automatic after software updates, [COLOR="Red"]add the line APT_AUTOGEN="yes"[/COLOR] to /etc/default/rkhunter (this gets read by /etc/apt/apt.conf.d/90rkhunter). 
thx to Douglas Bagnall.

---

### Post by unspawn on 2011-07-18
> **leoquant said:**
> did you check it?
Yes, at time of deletion in 2009 the only relevant content was a link to http://rkhunter.wiki.sourceforge.net/" which redirects to [http://sourceforge.net/apps/trac/rkhunter/wiki](http://sourceforge.net/apps/trac/rkhunter/wiki) from which you basically want the [http://sourceforge.net/apps/trac/rkhunter/wiki/MPRKH](http://sourceforge.net/apps/trac/rkhunter/wiki/MPRKH) as I posted already...


> **leoquant said:**
> I started it
Well done, good work.

---

