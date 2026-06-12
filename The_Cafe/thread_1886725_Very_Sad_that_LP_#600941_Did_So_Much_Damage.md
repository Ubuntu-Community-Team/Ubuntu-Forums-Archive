---
title: "Very Sad that LP: #600941 Did So Much Damage"
date: 2011-11-25
forum: The Cafe
---

### Post by nutznboltz on 2011-11-25
What is the best way to submit a patch to fix all the damage that LP: #600941 causes?

I ask because LP: #600941 was put into every version of Ubuntu still supported at this time.

The story is that after it was pushed out all of our systems started experiencing Nagios nrpe restart failures.

Commands like

/etc/init.d/nagios-nrpe-server restart

would cause nrpe to stop but not restart.

I tracked this down to the way that the /etc/init.d/nagios-nrpe-server script is calling start-stop-daemon.

The issue is that the "stop" stanza in the /etc/init.d/nagios-nrpe-server script first calls start-stop-daemon which sends SIGTERM to nrpe and then waits only for one second.

If nrpe has not exited by that time the pid file will still exist and the /etc/init.d/nagios-nrpe-server script will remove it.

Worse if "/etc/init.d/nagios-nrpe-server restart" is used not only will the pid file be removed, the attempt to restart nrpe will fail provided that the nrpe daemon is still tardy in shutting down.

The attempt to start under those circumstances will fail because nrpe will still be bound to a socket and the second attempt at binding will cause the nrpe startup to abort.

They should have wondered why there was a comment about "sometimes the pid file does not get removed".

They should have tested on systems that have a heavy load and therefore slow nrpe response times.

Thanks

---

### Post by nutznboltz on 2011-11-25
Also asked on [http://askubuntu.com/questions/82631/what-is-the-way-to-submit-a-patch-to-fix-all-the-damage-that-lp-600941-causes](http://askubuntu.com/questions/82631/what-is-the-way-to-submit-a-patch-to-fix-all-the-damage-that-lp-600941-causes)

---

### Post by nutznboltz on 2011-11-25
[http://youtu.be/YPqfl7AeUsE](http://youtu.be/YPqfl7AeUsE)

---

### Post by nutznboltz on 2011-11-25
So I dump even more hours of time fixing what Canonical blithely broke

1. Put a checkpoint on an Oneric VM
2. Upgrade it to Precise
3. Fetch all the tools require to do software development.
4. Used ubuntu-bug to create LP: #896388
5. Used bzr to merge the patch into the ticket

Then I was told they are too busy to work on it.

Think about this when you are deciding which server OS to deploy.

If you choose Ubuntu they will damage your LTS platform and tell you to fix it yourself and be an obstacle to getting what you need to function.

---

### Post by cariboo on 2011-11-25
> **nutznboltz said:**
> So I dump even more hours of time fixing what Canonical blithely broke

1. Put a checkpoint on an Oneric VM
2. Upgrade it to Precise
3. Fetch all the tools require to do software development.
4. Used ubuntu-bug to create LP: #896388
5. Used bzr to merge the patch into the ticket

Then I was told they are too busy to work on it.

Think about this when you are deciding which server OS to deploy.

If you choose Ubuntu they will damage your LTS platform and tell you to fix it yourself and be an obstacle to getting what you need to function.

It seems to me you are going about this the wrong way, Ubuntu gets all the packages from Debian, does the problem show up in Debian too?

---

### Post by stgraber on 2011-11-25
Yes, the bug is in Debian as it's the source of the init script we SRUed.

I already asked nutznboltz to file the bug on Debian's bug tracker as that'll save him around a week of waiting if he does it rather than wait for me to have time to do it.
Once the Debian maintainer has a fix that he's happy with, SRUing it again is trivial.

Just a side note, altough I work for Canonical, I'm not paid to work on nagios-nrpe, I'm only interested in this package for personal reasons, so any time I spend on it is my free time.

---

### Post by cariboo on 2011-11-25
Thanks for your input stgraber.

---

### Post by nutznboltz on 2011-11-28
> **cariboo907 said:**
> It seems to me you are going about this the wrong way, Ubuntu gets all the packages from Debian, does the problem show up in Debian too?

I was fooled into wasting my time by:
[http://askubuntu.com/questions/82631/what-is-the-way-to-submit-a-patch-to-fix-all-the-damage-that-lp-600941-causes](http://askubuntu.com/questions/82631/what-is-the-way-to-submit-a-patch-to-fix-all-the-damage-that-lp-600941-causes)

---

