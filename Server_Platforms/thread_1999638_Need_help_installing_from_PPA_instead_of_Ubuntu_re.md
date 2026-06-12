---
title: "Need help installing from PPA *instead* of Ubuntu repo"
date: 2012-06-08
forum: Server Platforms
---

### Post by osx on 2012-06-08
I installed Ubuntu 12.04, 64-bit, server and want to install Nagios.

The version of Nagios in the Ubuntu repos is for an outdated version.

I read [here]("https://launchpad.net/~nagiosinc/+archive/ppa") how to add the Nagios PPA hosted on Launchpad and followed the steps it provided. That is, I modified the apt sources.list file, added the PPA key, and ran "sudo apt-get update".

However, when I run "sudo apt-get -s install nagios3" it still appears to be trying to get Nagios from the Ubuntu repo instead of the Nagios PPA.

How do I force it to install from the PPA instead?

Thanks.

---

### Post by IWantFroyo on 2012-06-08
There should be an apt-get command that keeps a package from being updated. I'm not at my Ubuntu computer right now, so you'll have to look for it.
 
```
man apt-get
```
 
```
apt-get --help
```

---

### Post by osx on 2012-06-08
IWantFroyo, I looked at the option for holding back packages and that doesn't appear to do what I am wanting.

I think the issue may be that the package name in the PPA is different than the package name in the Ubuntu repo.

I ran "sudo apt-get -sV nagios3" and "sudo apt-get -sV nagios-agent" and think that may be the difference. I've not used PPAs before so this is new territory for me and the [Ubuntu documentation for repositories]("https://help.ubuntu.com/community/Repositories/CommandLine") was of no help for this issue.

I'm doing a test in just a couple of minutes, but the Nagios PPA site didn't explain how to install from their PPA either, just how to add it.

I'll post what I found after my next test.

Thanks.

---

### Post by osx on 2012-06-08
That was the issue. The package name in the PPA is different than the Ubuntu repo.

Using the command "sudo apt-get install nagios-agent" installed from the PPA.

---

