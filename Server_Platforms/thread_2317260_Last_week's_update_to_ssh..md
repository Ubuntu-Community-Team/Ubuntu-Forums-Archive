---
title: "Last week's update to ssh."
date: 2016-03-14
forum: Server Platforms
---

### Post by MAFoElffen on 2016-03-14
Has anyone else had this happen yet? 

Late last week there was an update to open ssh server. Before the update: Connection string with username > login credentials > command prompt. This is connecting to my Ubuntu Servers 14.04 through 16.04 LTS and My consoles (Ubuntu Server core with Gnome 3) @ 14.04.03 LTS.

Since update: Now all my servers from my console say about my servers: 
```

The authenticity of host 'HostName (xxx.xxx.xxx.xxx)' can't be established.
ECDSA key fingerprint is xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx.
Are you sure you want to continue connecting (yes/no)?

```
Even though I say 'yes'?
```

Failed to add the host to the list of known hosts (/home/UserName/.ssh/known_hosts).

```
Even though it has this error, it connects anyways... just fine.

So it seems like, at least partially, that it is not recognizing the fingerprints that have been there previously. I say "partially," because I added a new Xen Server on it's old IP address. It recognized that the new fingerprint was different for that IP, and I had to delete the previously before I could connect to it.

All now, it is just now acting the same and there is (to me) an error that it can't write fingerprints. 

Is this a new "feature/change"? Or is this a bug that I should report to launchpad?

EDIT:
I guess I should try to isolate this tomorrow. To see if it is a problem with just my console or on any Ubuntu system using shh with that update.

---

### Post by MAFoElffen on 2016-03-17
bump.

No one? Really?
*** All this would take to answer this, is for someone to answer if this is happening to them now or not. That would tell me what I need to report to launchpad-- If this is isolated (just my environment) or if this includes others.

It's not like it does not work, just not working as it did (should).

---

### Post by Habitual on 2016-03-17
What are the perms on /home/UserName/.ssh/known_hosts ?
Open terminal and issue 
```
ls -al /home/UserName/.ssh/known_hosts
``` and post the output here.

---

