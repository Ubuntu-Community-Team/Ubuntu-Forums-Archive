---
title: "Server is partially unresponsive."
date: 2010-07-16
forum: Server Platforms
---

### Post by spynappels on 2010-07-16
I have a problem which I hope someone can help me with.

I have a remote server which has been working perfectly for about 1 year. It is in a secure location and used for serving a local web-app, and we remote administer it through an OpenVPN tunnel, and previously a Hamachi tunnel.

It has in the last few days become partially unresponsive. What I mean is that I can ping it fine through the VPN, and I can SSH into the box, but when I try to run some commands, it seems to freeze partway through, and I get the output interrupted and a blinking cursor. I have also tried to access the web-app through the VPN and while the page header in the browser changes to the correct page name, the actual page does not load.

A reboot does not seem to have cleared the problem, although I cannot be certain at this moment that the reboot command actually completed, or froze partway through.

Load average is at 0.02, memory is 4% used, hard disk is 5% full,it appears to be working fine locally serving the web-app and I am stumped....

Any ideas before I drive 60 miles to take a look?

---

### Post by iponeverything on 2010-07-16
check your available inodes:

```

df -i

```

also check for corrupted binaries, you may have hardware issues.


```

debsums -a

```

and look for clues /var/log/syslog /var/log/messages and /var/log/debug

---

### Post by gombadi on 2010-07-16
> 
It has in the last few days become partially unresponsive. What I mean is that I can ping it fine through the VPN, and I can SSH into the box, but when I try to run some commands, it seems to freeze partway through, and I get the output interrupted and a blinking cursor


May or may not be the same as your problem but I have seen this type of thing before. Can log in but could not run commands that produce a lot of output - MTU issue.

SSH into the machine and see if you can run the date command a few times. If you can run it fine then try a command that produces more output like ls on a directory.

A reboot fixed my problems. Have you made any changes to the VPN or network recently?

Run the uptime command to see how long the machine has been running will tell you if the reboot worked.

---

### Post by spynappels on 2010-07-16
The problem is that I cannot run any command with a lot of output, so Gombadi's idea looks like it may be what is happening. Uptime gives:

```
 uptime
 13:38:51 up  4:32,  1 user,  load average: 0.04, 0.03, 0.01
```

so my reboot did not work, but it did reboot 13 hours ago, or am I reading that wrong?  The problems have been going on longer than that.

Running date has output fine, but any command with more output freezes.

Will try to get someone to do a physical reboot before I do anything else.

---

### Post by spynappels on 2010-07-16
Ok, a hard reboot did not help.

Any other ideas?

checked inodes, not sure what I was looking for, but none were highly used must were 1% In use and one was 3% In use.

---

