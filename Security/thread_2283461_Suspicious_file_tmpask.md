---
title: "Suspicious file /tmp/ask"
date: 2015-06-22
forum: Security
---

### Post by Wtower on 2015-06-22
On one of my ubuntu web servers I found the following file:

/tmp/ask

<snip>

My perl knowledge is limited, but it looks to me like an irc bot with flooding capabilities.

My questions are:

[LIST=1]
[*]Have you ever encountered this?
[*]How did this end up in that folder? I only suspect from some site that has not validated something, as /tmp is writtable by apache and the file ownership has been www-data.
[*]How does this even launch?
[*]Is there a chance of any bigger compromise?
[/LIST]

---

### Post by Wtower on 2015-06-22
Following a [previous question]("http://ubuntuforums.org/showthread.php?t=2283461&referrerid=1085139"), on one of my ubuntu web servers I have found the following files:

```

/tmp/.X11-unix/
/tmp/.X11-unix/dorks.txt
/tmp/.X11-unix/ipays2.php
/tmp/.X11-unix/malink.php
/tmp/.X11-unix/act.zip
/tmp/.X11-unix/inc.zip
/tmp/.X11-unix/ipays.phtml
/tmp/.X11-unix/ipays.php
/tmp/.X11-unix/ipays3.php
/tmp/.X11-unix/ext.zip
/tmp/.X11-unix/ipays.gif

```

Obviously these files are something malicious, there is not even x installed. If you requireme to cat any of the files I would be glad too.

My questions are:


[LIST=1]
[*]Have you ever encountered this?
[*]How did this end up in that folder?
[*]How does this even launch?
[*]Is there a chance of any bigger compromise?
[/LIST]

---

### Post by Bucky Ball on 2015-06-22
*Threads merged.*

Please do not post multiple threads regarding the same issue. By doing so you dissipate community support and reduce your chances of getting support. These two are no doubt related and are about the same security issue you are having.

---

### Post by Wtower on 2015-06-22
Thank you for that and apologies. Well, actualy, they are on different servers but they may be as well probably related. I got a third issue, again on another machine, which I will post sepearately. Please do merge it if you feel like it is related.

---

### Post by zero212 on 2015-06-23
Well /tmp/ is literally just temporary, it's used by programs/services to store temporary information for that session.
The name of the file is usually an indicator of what service/program created it.
If you found something malicious and rkhunter or chkrootkit turn up false, then reinstall. 
Install only from secure repositories and use HTTPS when necessary.

---

### Post by bashiergui on 2015-06-23
If this server has the same ssh configuration as the one in [your other post,]("http://ubuntuforums.org/showthread.php?t=2283466") then someone probably brute forced the ssh password and has root. Look through the auth logs to see who's been logging in and when.

---

### Post by tgalati4 on 2015-06-24
Check the creation dates of all of the suspicious files and compare them to /var/log/auth.log and your apache logs to determine what additional activity has taken place.  I would presume that both servers are now compromised, so now you need to take them off line and perform a wipe and clean install.

---

### Post by Wtower on 2015-06-25
> **zero212 said:**
> Well /tmp/ is literally just temporary, it's used by programs/services to store temporary information for that session.
The name of the file is usually an indicator of what service/program created it.
If you found something malicious and rkhunter or chkrootkit turn up false, then reinstall. 
Install only from secure repositories and use HTTPS when necessary.

Thank you again @zero212. Well, I understand that. It is obvious that the files ended up there from some web site exploit as their owner was www-data. Both rootkit checks are good, I wouldn't expect them to trat these files as rootkits anyway. I am just very curious if anyone knows what kind of exploits or if anyone has met these before.

> **bashiergui said:**
> If this server has the same ssh configuration as the one in [your other post,]("http://ubuntuforums.org/showthread.php?t=2283466") then someone probably brute forced the ssh password and has root. Look through the auth logs to see who's been logging in and when.

Thank you again @bashierui. This server does not have the same ssh configuration, and it does not have password authentication on. There is nothing suspicious in the auth logs for both servers as I monitor them daily.

> **tgalati4 said:**
> Check the creation dates of all of the suspicious files and compare them to /var/log/auth.log and your apache logs to determine what additional activity has taken place.  I would presume that both servers are now compromised, so now you need to take them off line and perform a wipe and clean install.

Thank you @tgalati4. Excellent idea. Auth logs are clean, but apache error logs are not and it might give me some idea how these files ended up there and from where. Atm I believe that one of them ended up there from a magento site (magmi exploit).

I am afraid there is no other choice than clean install for the server on the other post, but for this one I am not so sure. I believe that these are only web site-wide issues.

---

### Post by bashiergui on 2015-07-07
You saw the "log cleaner" part of the script, right? Unless you're sending logs from this machine somewhere else, I wouldn't trust the logs on this machine at all.

You asked if anyone had seen this before: the short answer is yes. 

Your perl coder seems to be an anime fan based on the irc nicks in the script:[http://naruto.wikia.com]("http://naruto.wikia.comAlso")

Also the url in the perl script (h++p://www.utama-audio.com/ipays/tool/) was used in other exploit attempts that people blogged about dating back to 2011. One is here:[http://armoredcode.com/blog/ghost-in-the-shell-an-exploiting-attempt-examinated]("http://armoredcode.com/blog/ghost-in-the-shell-an-exploiting-attempt-examinated/It's")

It's had many different IPs which is typical for malware.

Googling the line in the script "I'm not living Im just killing time" yields the entire script on a pastebin type site, which tells me it's been used by anyone that has found it there.This is probably an opportunistic attack that tries to exploit anyone it can find.

---

