---
title: "Advise About Security"
date: 2009-01-04
forum: Security
---

### Post by newbux on 2009-01-04
hello ive been hacked using windows repeatedly and have just switched to ubuntu. so im concerned about security. what would you do to protect your system. i currently have clam virus scanner rkhunter chkrootkit and firestarter firewall. how does a rootkit get in your system. can firewalls get hacked through? can they still install  trojans? if you reinstall ubuntu do you wipe all viruses?

as well i ran rkhunter and it found three suspicious files can you tell me what to do now?

---

### Post by HermanAB on 2009-01-04
The default install of Ubuntu is secure.  Relax and enjoy your new Linux system.

Root kits are not really a problem.  In over 25 years of using Unix, I have never encountered a root kit.  I guess that you have to be really, really dumb and reckless to get one.  The reports by rkhunter and others are notoriously inaccurate and tend to raise false alarms, so just forget about it.

Cheers,

Herman

---

### Post by albinootje on 2009-01-04
> **newbux said:**
> hello ive been hacked using windows repeatedly and have just switched to ubuntu. so im concerned about security. what would you do to protect your system. 

Are you in a situation of a home desktop behind a DSL-router or cable-modem ?

Then I recommend just the following :

1) Use only deb packages from Ubuntu repositories or from Launchpad.net (or getdeb.net, which seems offline right now). 

If you want to use deb packages from other sources, do a little bit of research and try to judge whether the maintainer(s) and/or developer(s) can be trusted enough in your opinion.

2) Do not run shell scripts unless you've inspected them or trust where it's coming from. 
Be a little careful with downloading via p2p software like amule, downloading Ubuntu iso images via p2p software, instead of from the official Ubuntu sources, without checking the md5sum with the md5sums at the Ubuntu website is pretty senseless for example.

3) Check out the no-script add-on for Firefox, it can be a hassle to work with first, but you might like it for security. I like it a lot!

4) Keep applications like Firefox, Thunderbird, openssl, openssh, and other desktop internet communication related software up to date.

5) Anti-virus software on a Linux desktop is imho useless, unless you have Windows friends,relatives,coworkers who you are exchanging files with.

If you're really paranoid, install :
```

sudo apt-get install fcheck

```
and make sure the output of its cronjob can be emailed to you.
Or look at other integrity checking software.

---

### Post by albinootje on 2009-01-04
> **HermanAB said:**
> The default install of Ubuntu is secure.  Relax and enjoy your new Linux system.

Root kits are not really a problem.  In over 25 years of using Unix, I have never encountered a root kit.  I guess that you have to be really, really dumb and reckless to get one.

If I may partially disagree with this :)
We're talking desktop Linux users here in this thread I assume.

However, for example the serious OpenSSL vulnerability in Ubuntu and Debian could have lead to break-ins without the sysadmin knowing, and looking at the nature of the Linux kernel usage, which is kernel+modules, the attacker could have installed a rootkit and/or a kernel module which could have hidden itself. But... then we're talking about servers.

For a desktop user in my opinion the danger comes mainly via the webbrowser (Though the no-script Firefox add-on comes to the rescue there), but then again currently I don't see much danger concerning rootkits at all in an up to date Ubuntu desktop installation, because there are probably not that much local root exploits in the wild that are exploitable via a web-browser on an up-to-date Ubuntu desktop installation.

---

### Post by 2hot6ft2 on 2009-01-04
> **newbux said:**
> 
as well i ran rkhunter and it found three suspicious files can you tell me what to do now?
Don't worry it's the same 3 I have and so does everyone else. It just says suspicious it doesn't say dangerous or that they are a threat.
I forget what they were now but it's just just saying look and decide for yourself if they are safe because it doesn't recognize them or can't read them or they change.

---

### Post by bodhi.zazen on 2009-01-04
> **newbux said:**
> hello ive been hacked using windows repeatedly and have just switched to ubuntu. so im concerned about security. what would you do to protect your system. i currently have clam virus scanner rkhunter chkrootkit and firestarter firewall. how does a rootkit get in your system. can firewalls get hacked through? can they still install  trojans? if you reinstall ubuntu do you wipe all viruses?

as well i ran rkhunter and it found three suspicious files can you tell me what to do now?

Thread closed to keep it from becoming a meandering off topic quagmire.

Read the stickies at the top of this forum, that is why they are stickies. If you have a specific question please start a new thread.

---

