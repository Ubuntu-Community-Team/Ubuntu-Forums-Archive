---
title: "Warning Signs of Having Been Hacked"
date: 2011-02-19
forum: Security
---

### Post by SlowDemiseOfWindows on 2011-02-19
Hi all,  I had a serious breach of the cellular segment of my communications network this week. All I can say is nobody got hurt.   The attackers also knew where to find me via email. I'm concerned that perhaps they've penetrated this aspect of my system as well, although they seemed pretty specifically focused on the phone. There have been no changes on anything on my computer, and of course, I went ahead and changed all the passwords. How can I verify or at least look into the possibility of having been hacked as well.   Thanks much and wish me luck!

---

### Post by HermanAB on 2011-02-19
Read the system logs.

---

### Post by SlowDemiseOfWindows on 2011-02-19
How do I get to them? I am new to this, and I don't see that topic anywhere in the link you sent me.

---

### Post by cariboo on 2011-02-19
Try System->Administration->log File Viewer on Ubuntu desktop, or look in Places->File System->var->log.

---

### Post by SlowDemiseOfWindows on 2011-02-22
The first of those worked. Thanks! What am I looking for in there though? Furthermore, it's only displaying Feb 20-22, and what I need to see is before that.  Thanks again!

---

### Post by cariboo on 2011-02-22
Ubuntu Desktop is setup to store a month of logs, the previous logs are gzipped, go to /var/log, and have a look at auth.log, on my system I also have auth.log.1, auth.log.2.gz, auth.log.3.gz and auth.log.4.gz

---

### Post by SlowDemiseOfWindows on 2011-02-26
Ok, got it and can now look at the relevant dates! Thanks all! What actions specifically am I looking for? I'll be damned, if I remember what times I logged on two weeks ago. 

What are the chances of being hacked anyway? I'm running ubuntu and I have different passwords for every account, containing a very extended combination of uppercase letters, lowercase letters, numbers, and symbols. I know ubuntu is specifically hard to hack, and I don't eave the machine on or in network for extended periods of time. 

I had a problem with my phone system, not my computer. Furthermore, none of my clients report any problems with sensitive information either. 

Any thoughts are much appreciated!

---

### Post by cariboo on 2011-02-26
Are you running Asterisk? I'd suggest typing:

```
sudo lsof -i -P - n
```

to see it there are any unrecognized services running.

---

### Post by asmoore82 on 2011-02-26
This happened to me once, not on Ubuntu, a long time ago...

If they attempted to install some kiddie rootkit, your `ps` command and other
admin utilities will have been replaced by shell scripts instead of binaries.
```
file `which ps`
```

---

