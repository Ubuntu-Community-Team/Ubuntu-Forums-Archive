---
title: "[SOLVED] I keep getting myself blacklisted by Denyhosts"
date: 2008-08-11
forum: Server Platforms
---

### Post by Kolipoki on 2008-08-11
Hello everyone,

Might be something trivial, but even without failing authentication, my computer's local IP keeps getting listed on the /etc/hosts.deny . 

I go as root and erase it. IP is not there if I check right back after saving and exiting. But if I check again in a couple of minutes and the IP is there, again and again. :eek: 

Why could this be happening? I already put the IP in the hosts.allow and so I'm not having problems reaching server thru ssh. But can't help thinking there is something wrong.

Any lead to this inconvenience, will be greatly appreciated. K.

---

### Post by MJN on 2008-08-11
I used to use Denyhosts and do recollect that manually removing an entry was often a painful process - you will likely find you are listed in more than one file and any left behind keep bringing you back into the loop.

I would suggest stopping Denyhosts (it doesn't like you working on its backend whilst running) and looking in all the relevent data files (all those in /usr/share/denyhosts) to remove your IP or, do what I did, install Fail2Ban instead. Seriously, it works just as well (indeed I prefer its blocking mechanism using iptables rather than TCP wrappers) and all-in-all is a lot 'cleaner' when it comes to keeping tabs on who's blocked out and who isn't!

Mathew

---

### Post by Kolipoki on 2008-08-11
Perfect. Nice piece of advice Mathew. Thanks a lot.

One last question, do I need to uninstall Denyhost, in order to install Fail2ban? .

Thanks again for your time...

---

### Post by MJN on 2008-08-11
You don't *need* to, but you'd be nuts for leaving it in place running as they'll soon be trying to outdo each other seeing who can block the most users, legitimate or otherwise! ;)

Mathew

---

