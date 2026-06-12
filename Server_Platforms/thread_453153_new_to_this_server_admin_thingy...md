---
title: "new to this server admin thingy.."
date: 2007-05-24
forum: Server Platforms
---

### Post by adza on 2007-05-24
Hi there, after noticing today that there has been some security releases for apache, php etc... i ssh into my server (sun ultra 60) and run the apt-get update & upgrade etc... server now upgraded now probs... my question is, how do i go about automating this process on my server? It is a head only config, can only ssh into it... can i write a shell script with the code sudo apt-get update && sudo apt-get upgrade then configure it to run automatically, say once a week? this sounds like it should be possible... nay easy even?

---

### Post by renzokuken on 2007-05-24
it should be easy yeah

you could write a very simple bash script containing the update commands and then use "cron" to execute that script once a week

so create a file to use as your bash script

```
sudo nano update_script
```

slap in the following text

#!/bin/bash          
sudo apt-get update
sudo apt-get upgrade

Ctrl+X, then Y then enter to save and exit. may also have to make it executable

as for cron, you may have to ask someone else since i have no idea how to use it to automate processes ( here may help [http://www.unixgeeks.org/security/newbie/unix/cron-1.html](http://www.unixgeeks.org/security/newbie/unix/cron-1.html) )

sorry its only half an answer

EDIT: i think this would still require you to enter your password each time it updates, not sure, and also not sure how to get round it

---

### Post by craigp84 on 2007-05-24
Hi adza,

There's a package called "unattended-upgrades" which will install security updates (and optionally bug fixes etc.) automatically.

It's as simple as "sudo apt-get install unattended-upgrades" to install. Do a "dpkg -L unattended-upgrades" to see the cron jobs and apt config that's been installed - this will let you see how it hangs together.

renzokuken,

You're 90% of the way there, (ignoring the sudo issue which can be sidestepped easily) the problem here is that during a package upgrade, a package may elect to ask you a question. If it's running from cron (unattended) you can't answer that question, and so the update fails. You could set the debconf priority high so that you're not asked questions though, but unattended-upgrades package does it for you and it's only a quick apt-get install away.

Hope this helps both of you,

Craig

---

### Post by DrNick on 2007-05-24
The only thing I'd say with that, is that it might not always be a good idea to have things update automatically.  There are a few reasons for that:

1) Whilst it is very rare for any updates to require a reboot, there are situations where this is the case - a kernel upgrade being one of them.  You'd want to be there when that happened.
2) With complete automation, there would be no easy way to tell what got updated or replaced.  From a troubleshooting point of view this could be pretty hellish.  You could always pipe the output of the update command to a log file, and you could even get it to mail you the log file.  
3) With complete automation  you have no say whatsoever in what gets updated or not.
4) There are some cases where post-update tasks need to be performed.  You wouldn't know about this with automating it.  Also when something big (like apache2) get's updated, its quite a good idea to read up on what's been changed in the update.  Then if you need to adjust any of your configuration to reflect those changes, you can do.

Hope those considerations help...

-- Tom

---

### Post by adza on 2007-05-24
thanks craig, that's installed, how does it run? Is it a service like apache/mysql etc? Do i need to start it?


***EDIT*** hehe.. although drnick has made a couple of good points there as well :) my main concern is security updates for the webserver (apache) so... hmmmm

---

### Post by craigp84 on 2007-05-24
It runs from cron, do the dpkg -L command i mention before and all will become clear.

DrNick does indeed make some good common-sense points. As always it really depends on your situation.

Quickly though:

1) not practical for 100+ servers, and i'd argue with 5+ servers you're time's better spent elsewhere - invest in proper automation.
2) As part of your automation you'd build in reporting & alerting so this isn;'t much of a concern.
3) Again with a complete automation solution you'd have a satelite server providing the updates. A precondition of the package being uploaded to the satelite would be that it would have to pass all verification tests. Therefore, you have 100% complete authority over what does  / does not get updated
4) I think this is more to do with feature upgrades & bug fixes rahter than security updates. Bug fixes etc. probably should not be automated. Indeed there's a good case for never applying these types of updates unless you have experienced the issue it fixes.

-c

---

### Post by adza on 2007-05-24
great responses people! thanks for all your help :) hehehe... i've only got a concern for a single server running from my office at home however, hosting a web page that is purely a hobby only ;) i can quite easily do this stuff manually, however since this whole experiment is about learning shyte... i actually might try shell scripting this stuff....

---

