---
title: "chkrootkit &amp; rkhunter results / gen. security"
date: 2013-01-15
forum: Security
---

### Post by MyTinFoilHat on 2013-01-15
Hello and thanks for the stickies - as well as your patience and time. I have a lot to learn about Ubuntu Security, so I've been doing a lot of reading lately.

I'm posting for both chkrootkit and rkhunter here because results from both also have references to java and I have a general security question that covers both, in addition to a request for info/help.


I've just run chkrootkit and rkhunter. I got a couple odd results (read warnings and suspicious) in both results and have prowled the threads for answers. I'm still left with questions...

PART 1: RKHUNTER 
(I ran a full check earlier). Ran this for the post:
```
sudo rkhunter -c --rwo --summary

```
yielded the following results:

```
Warning: The command '/usr/bin/unhide.rb' has been replaced by a script: /usr/bin/unhide.rb: Ruby script, ASCII text
Warning: Suspicious file types found in /dev:
         /dev/.udev/rules.d/root.rules: ASCII text
Warning: Hidden directory found: '/etc/.java'
Warning: Hidden directory found: '/dev/.udev'
Warning: Hidden file found: /dev/.initramfs: symbolic link to `/run/initramfs'

System checks summary
=====================
File properties checks...
    Files checked: 135
    Suspect files: 1
Rootkit checks...
    Rootkits checked : 292
    Possible rootkits: 0
Applications checks...
    All checks skipped
The system checks took: 53 seconds
All results have been written to the log file (/var/log/rkhunter.log)
```

I've seen several thread responses to the Ruby Script, pointing OP to using --propupd; that this is likely the result of distro changes. 

QUESTION: How can the user (or in my case, me, as a novice) know that this is genuine and reliable? What steps can I take to verify this before I --propupd? 

QUESTION: Should the hidden directories and file be any cause for alarm?


PART 2: CHKROOTKIT (TL;DR version)
A lot "nothing found", "not infected" and "no suspect files", etc. results, but I have no idea what to do with this information:

```

The following suspicious files and directories were found:  
/usr/lib/jvm/.java-1.6.0-openjdk-amd64.jinfo /usr/lib/jvm/.java-1.7.0-openjdk-amd64.jinfo /usr/lib/python2.7/dist-packages/PyQt4/uic/widget-plugins/.noinit /usr/lib/pymodules/python2.7/.path

```

Any info will be useful. Thank you to all who read and respond.

---

### Post by DanR01 on 2013-01-16
With the exception of the warning about 'unhide' I get the same results on running rkhunter and chkrootkit on my system.

Either both our systems have been compromised or you are in the clear.

---

### Post by MyTinFoilHat on 2013-01-16
> **DanR01 said:**
> With the exception of the warning about 'unhide' I get the same results on running rkhunter and chkrootkit on my system.

Either both our systems have been compromised or you are in the clear.

Thanks for the reply.
Hmmm. Not nearly as reassuring as I had hoped. :-) :-S
I guess I have a lot more reading ahead of me. I like to be certain. If only there were more hours in a day...

In the meantime, if anyone else has an idea, feel free...

---

### Post by cariboo on 2013-01-16
Truthfully, rkhunter and chkroot results have been discussed so many times in this sub-forum, I'm almost tempted to move these types of questions to [Recurring Discussions]("http://ubuntuforums.org/forumdisplay.php?f=302").

That being said, the results you got are pretty normal, and are called false positives. When searching for more information on the results you got, don't restrict your self to Ubuntu solutions only, as there are plenty of other great Linux resources out there.

---

