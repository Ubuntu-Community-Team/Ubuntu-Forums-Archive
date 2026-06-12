---
title: "Suspicious files found by 'chkrootkit'"
date: 2011-09-07
forum: Security
---

### Post by Starfleet on 2011-09-07
Hi guys (girls too!),

Just a quickie. I've recently loaded 'chkrootkit' and after running it on my Linux Ubuntu 10.04.2LTS system it reports the following...

Searching for suspicious files and dirs, it may take a while... The following suspicious files and directories were found:  
/usr/lib/jvm/.java-6-openjdk.jinfo /usr/lib/xulrunner-1.9.2.22/.autoreg /usr/lib/pymodules/python2.6/PyQt4/uic/widget-plugins/.noinit /usr/lib/pymodules/python2.6/.path 

It reports no other infections or suspicious files.

I suspect it is a false positive...if you see what I mean. But anyone else got this. Cheers everyone and thanks for any replies.

---

### Post by Dangertux on 2011-09-07
You are correct in your assumption that this is a false positive.

---

### Post by CharlesA on 2011-09-07
chkrootkit and rkhunter are notorious for false positives.

---

### Post by Starfleet on 2011-09-07
Thanks guys...I appreciate your replies, and anyone else who wants to comment - I'd be grateful.


I've just marked this thread as solved, as I feel confident Charles and Dangertux are correct...but still, if anyone else has had this just let me know please. Ta!

---

### Post by KIAaze on 2011-10-02
Well, I would like to know how to ignore them, since otherwise chkrootkit keeps sending warning emails, and too many emails means they are not read.
How do I configure chkrootkit to ignore them? Or better: to memorize what they look like and send a warning if they change.

In my case, it's just: /usr/lib/pymodules/python2.6/.path

edit: I followed these instructions: [http://www.electricmonk.nl/log/2007/11/29/chkrootkit-false-positives-filtering/](http://www.electricmonk.nl/log/2007/11/29/chkrootkit-false-positives-filtering/)
Should work in principle. Will see if I still get emails or not.

---

