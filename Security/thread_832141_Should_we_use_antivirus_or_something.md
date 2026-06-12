---
title: "Should we use antivirus or something ?"
date: 2008-06-17
forum: Security
---

### Post by sowhat12345 on 2008-06-17
Should Should we use antivirus software or something ? Because I heart that there are some open source antivirus and firewall softwares ... ?!! Maybe some people is making virus...How do we know that ? It is possible ... 
Also I have install my friend ubuntu 8 . He use just aMSN, firefox, open office and he listen musics . AT the beginning everything was fine,but after 2 weeks he start to call me for problems. He is sure that he didn't do anything else . If he didn't do something else how the problems started ?
The problems are : Firefox was very slow ... aMSN can't connected... Sometimes at the beginning when he log in about 5 minutes cpu works %100 ... Sometimes ubuntu didn't shut down... 
(He did not use two operation system. He use just ubuntu . I had everything delete...)
Now I have installed ubuntu 8 .. But I couldn't install my driver :( ( If you can help me ---> [http://ubuntuforums.org/showthread.php?t=831789](http://ubuntuforums.org/showthread.php?t=831789) ) If I can connect internet , should I install firewall or something ?
Thanks

---

### Post by HermanAB on 2008-06-17
Here is a Free GPL, generic Linux virus scanner for you.  Copy this to a file in /usr/local/bin and make it executable, then link it from /etc/cron.hourly:

#! /bin/bash
echo Generic virus scanner for Linux.
echo Copyright reserved Herman 2008, GPL.
sleep 10
echo Do you really want to scan the disk?
sleep 5
echo are you sure?
sleep 7
echo Really, really sure?
sleep 5
echo Scanning...
sleep 10
echo Analyzing...
sleep 20
echo Thinking...
sleep 10
echo Almost done...
sleep 600
echo Drum roll!!!
sleep 10
echo Wait for it...
echo 30
echo No viruses found!!!
sleep 5
echo Done
exit 0

---

### Post by attari on 2008-06-17
> **HermanAB said:**
> Here is a Free GPL, generic Linux virus scanner for you.  Copy this to a file in /usr/local/bin and make it executable, then link it from /etc/cron.hourly:

#! /bin/bash
echo Generic virus scanner for Linux.
echo Copyright reserved Herman 2008, GPL.
sleep 10
echo Do you really want to scan the disk?
sleep 5
echo are you sure?
sleep 7
echo Really, really sure?
sleep 5
echo Scanning...
sleep 10
echo Analyzing...
sleep 20
echo Thinking...
sleep 10
echo Almost done...
sleep 600
echo Drum roll!!!
sleep 10
echo Wait for it...
echo 30
echo No viruses found!!!
sleep 5
echo Done
exit 0





Hilarious!!!! hahahhaha:)

---

### Post by attari on 2008-06-17
> **sowhat12345 said:**
> Should Should we use antivirus software or something ? Because I heart that there are some open source antivirus and firewall softwares ... ?!! Maybe some people is making virus...How do we know that ? It is possible ... 

No need. Virus is a Windows animal. No virus for Ubuntu, I am actively tring to find one,... plz share if you have it. (You might have Windows virus in your data that you copied from Windows but they will be harmless in Linux)


> **sowhat12345 said:**
> Also I have install my friend ubuntu 8 . He use just aMSN, firefox, open office and he listen musics . AT the beginning everything was fine,but after 2 weeks he start to call me for problems. He is sure that he didn't do anything else . If he didn't do something else how the problems started ?
The problems are : Firefox was very slow ... aMSN can't connected... Sometimes at the beginning when he log in about 5 minutes cpu works %100 ... Sometimes ubuntu didn't shut down... 
(He did not use two operation system. He use just ubuntu . I had everything delete...)

aMSN gives connection errors, use Pidgin. Firefox is fast unless you screw up and install uncompatable extensions. Disable all extensions and then check. CPU usage should never be 100% (How did you check CPU utilization?) May be your CPU utilization reading were wrong... else your friend computer was damn slow and he is running full desktop effects! :)


> **sowhat12345 said:**
> Now I have installed ubuntu 8 .. But I couldn't install my driver :( ( If you can help me ---> [http://ubuntuforums.org/showthread.php?t=831789](http://ubuntuforums.org/showthread.php?t=831789) ) If I can connect internet , should I install firewall or something ?
Thanks

Agreed driver issue is their for the time being. Make sure you have a linux compatable hardware.


Regards and the best of luck.

PS: You can check out here how to customize your Ubuntu: [http://www.attari.net/index.php?My_space...:Customizing_Ubuntu]("http://www.attari.net/index.php?My_space...:Customizing_Ubuntu")

---

### Post by Paul Weaver on 2008-06-19
He almost certainly has installed a firefox plugin or extension that's caused issues. Flash is a common one that can peg firefox at 100% fairly easily. 

No experience with amsn.

---

### Post by lisati on 2008-06-19
> **sowhat12345 said:**
> Should Should we use antivirus software or something ? Because I heart that there are some open source antivirus and firewall softwares ... ?!! Maybe some people is making virus...How do we know that ? It is possible ... 


Although a virus for Linux is extremely unlikely, you might want to consider something for occasional use to double check files that you get from elsewhere and might want to pass on to Windows users. Some ISPs write it into their terms of service not to pass nasty things on.....It's more a matter of courtesy than necessity.

---

### Post by hyper_ch on 2008-06-19
antivirus is not needed.. I'm of the opinion that it is each user's own responsability to make sure they are safe.

---

### Post by benny bronx on 2008-06-19
An antivirus is not needed, but I sometimes share work files with windowians. so I installed Avast Free, I have the disk space and it does not run in the background, so why not.  But, except for some proof of concept malware that may or may not exist, you could download any of the in the wild MS killing viri, and it would do nothing since it can not execute,  Sort of like a great white shark stranded on a beach: it looks dangerous, but is pretty harmless.

---

