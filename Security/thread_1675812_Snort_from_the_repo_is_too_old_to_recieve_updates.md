---
title: "Snort from the repo is too old to recieve updates"
date: 2011-01-26
forum: Security
---

### Post by crashed111 on 2011-01-26
Hi guys

It looks like they no longer make new rule snapshots for the version of Ubuntu in the repos. The oldest they go back to is 2860 and the newest version in any Ubuntu release is 2850.

Ive now compiled it from source and all is working fine but someone may want to take a look at that. 

The stock version installs and runs fine but is using a rule set from 2005 by default so is pretty useless.

---

### Post by cipherboy_loc on 2011-01-26
What version of Ubuntu are you using? Also, though I don't know much about snort, but how much has changed in 5 years? Most of the IP addresses should be the same, it is just the new ones that you are missing.



Cipherboy

---

### Post by crashed111 on 2011-01-26
I am using 10.10.

Looking at the changelog there isnt a huge deal of change to snort itself other than the rule parser but the rules that install from the repo are totally out of date and will not help with detecting most modern exploits. 

The problem is with the rule parser not supporting all functions found in the later versions meaning if you do update it snort wont start at all.

---

### Post by cipherboy_loc on 2011-01-26
You could remove the snort package, download the source and compile/install that. Looking in the Gentoo repositories it seems like it is more up to date than what you describe the Ubuntu version of snort to be... Maybe you just need to compile/install it. Also, isn't there a place where you can download rules for snort?



Cipherboy

---

### Post by cariboo on 2011-01-26
Ubuntu uses a snapshot of Debian testing at the start of each development cycle, whatever version is in that repository, is the version you get for the life-cycle of that release.

---

### Post by bodhi.zazen on 2011-01-26
> **crashed111 said:**
> Hi guys

It looks like they no longer make new rule snapshots for the version of Ubuntu in the repos. The oldest they go back to is 2860 and the newest version in any Ubuntu release is 2850.

Ive now compiled it from source and all is working fine but someone may want to take a look at that. 

The stock version installs and runs fine but is using a rule set from 2005 by default so is pretty useless.

Snort rules has nothing to do with the version of snort =)

You download them from here:

[http://www.snort.org/snort-rules/](http://www.snort.org/snort-rules/)

They are freely available to registered users (meaning you have to register) after a 30 day delay.

If you want a more up to date rule set you will have to subscribe (pay).

You can also download the emerging rules for free

[http://www.emergingthreats.net/](http://www.emergingthreats.net/)

I personally find registered rules (30 day delay) + emerging rules are sufficient.

---

### Post by crashed111 on 2011-01-27
> **bodhi.zazen said:**
> Snort rules has nothing to do with the version of snort =)

You download them from here:

[http://www.snort.org/snort-rules/](http://www.snort.org/snort-rules/)

They are freely available to registered users (meaning you have to register) after a 30 day delay.

If you want a more up to date rule set you will have to subscribe (pay).

You can also download the emerging rules for free

[http://www.emergingthreats.net/](http://www.emergingthreats.net/)

I personally find registered rules (30 day delay) + emerging rules are sufficient.


Hi Guys

I have made an account at snort and generated an oinkcode to get the updates via oinkmaster.

However the version that installs by default with Ubuntu is 2.8.5.2 I believe and the oldest version of rules they release on the site is for version 2.8.6.0 (The exact numbers may be slightly out I am working off the top of my head)

When you download these rules and apply them to the version of Ubuntu in the repos you run into problems as there are features in these rules not supported by the older version. As a result snort wont start. If you remove the rules which are causing errors it starts fine. 

I checked the errors against posts on snort.org and it looked like it was because the version was too old. 

I downloaded and compiled a version of 2.9 and it worked fine once updating the latest rule sets for version 2.9. 

I am working with someone on this project who has used snort before and he has experienced this problem before.

---

### Post by bodhi.zazen on 2011-01-27
In that event you should file a bug report on Launchpad against snort.

I would copy the init script , purge snort, and compile it for source.

---

### Post by 0xC on 2011-02-16
> **bodhi.zazen said:**
> In that event you should file a bug report on Launchpad against snort.

I would copy the init script , purge snort, and compile it for source.

Although Bodhi.zazen is right about what you can do to fix it, it is NOT a bug. If one is going to use and rely on Snort, one needs to stay aware of the changes that take place. I strongly recommend monitoring (subscribing via email or feed reader) to the official Snort Blog, which posts when new rules are released as well as makes end-of-life announcements, like in this recent post:
 
[http://blog.snort.org/2011/01/vrt-rule-update-available-now-and-eol.html](http://blog.snort.org/2011/01/vrt-rule-update-available-now-and-eol.html)


I'm just beginning the process of "purging and compiling from source" myself. Although, since the Ubuntu package is really just a Debian package, I might first try to find a newer debian package to install. Debian/ubuntu doesn't use standard paths or config files for some reason, so upgrading would be a tricky and time consuming task. Just back up your /etc/snort directory, remove the package (apt-get remove snort) and then install a supported version.

Without a paid subscription to the VRT rules, you can still freely download any rules that are 30 days old. They release updates several times a month, so there's no way we should be relying on such an old version. New threats are obviously being missed.

---

### Post by Hopping_Ubu on 2011-06-07
How does one go about compiling Snort 2.9.0.5 and replace the current version installed? I followed the instructions in the Security Discussions sticky, but I cannot update the rules. Can someone assist since I did the default installation: "sudo apt-get install snort", I do not know where everything goes during the install. If I knew, I would just do an install for 2.9.0.5.

Any assistance would be greatly appreciated.

---

### Post by emiller12345 on 2011-06-07
```
http://www.snort.org/assets/167/deb_snort_howto.pdf
```
Take a look here, it's probably more then you need but it might help

---

