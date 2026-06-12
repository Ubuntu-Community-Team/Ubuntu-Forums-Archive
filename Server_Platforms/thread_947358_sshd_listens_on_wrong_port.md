---
title: "sshd listens on wrong port"
date: 2008-10-14
forum: Server Platforms
---

### Post by fantata on 2008-10-14
I got a new unbuntu (dapper) server about a month ago. I installed shorewall and changed the port in /etc/ssh/sshd_config to be something other than 22. This has been working fine for a month, but this week the sshd is running again on port 22.

Initially I panicked and thought it was a hack or some-such. I checked sshd_config (still stating the non-standard port) and restarted. It came up again on port 22. It's like sshd_config is suddenly being ignored.

Could this be anything to do with an update to openssh by apt-get update?

In addition, my load average is being pushed up by ssh sessions that don't die. If I leave the machine for a couple of hours, when I next log in, the LA will be 1 with 100% CPU under ssh process. I kill to process and all is well until to cycle repeats in another couple of hours.

Can't see anything unusual in auth.log, or syslog. Can anyone help me get to the bottom of this?

---

### Post by iponeverything on 2008-10-14
First we can see what what is going on by running sshd from prompt in debug mode.. You can at lease see where it will pulling its config from or why it's ignoring it.

```
sudo sshd -d
```

this is place to start.

What you also do is next time it is eating the cpu -- run


```
sudo lsof -p <sshdpid>

```
where sshpid is pid of runaway sshd process.

after you do that you can attach a strace to it like so:

```
sudo strace -p <sshdpid>
```

---

### Post by fantata on 2008-10-14
right, when i restart the sshd in debug mode, initially i had to kill the sshd already running on port 22, then i got...

:  OpenSSH_3.6.1p2  on i686-pc-linux-gnu
debug: Becoming server.
debug: Creating listener
debug: Listener created
debug: no udp listener created.
[16839]: Listener created on port 22.
[16839]: Daemon is running.
debug: Running event loop

...no mention of config files. Is there a verbose log also somewhere?


Regards the CPU usage, I ran strace and got this...

gettimeofday({1223996758, 812246}, NULL) = 0
gettimeofday({1223996758, 812266}, NULL) = 0
gettimeofday({1223996758, 812286}, NULL) = 0
select(10, [5 7 9], [9], NULL, {0, 0})  = 0 (Timeout)

...over and over and over again.

Any ideas?

---

### Post by iponeverything on 2008-10-15
pump the debug level up to 3 -- there is not enough info there.


/usr/sbin/sshd -d -d -d

---

### Post by fantata on 2008-10-15
hmmm, still getting the same output i'm afraid.

---

### Post by iponeverything on 2008-10-15
yea .. you might be dealing with a trojan.

check the md5 for sshd.

```
sudo apt-get install debsums
debsums -c openssh-server

```
you might also do this to check for changed md5's on the whole system:
```
debsums -c 

```

---

### Post by fantata on 2008-10-15
ok, i had to download the latest debsums as the dapper package seems to be broken.

It does indeed say sshd FAILED - what can I do now?!

I thought everything was secure, but I didn't disallow root ssh access straight away - is this my mistake?

Thanks for your help so far.

---

### Post by fantata on 2008-10-15
also these...

/lib/modules/2.6.22-8-server/modules.pcimap                               FAILED
/lib/modules/2.6.22-8-server/modules.dep                                  FAILED
/lib/modules/2.6.22-8-server/modules.ieee1394map                          FAILED
/lib/modules/2.6.22-8-server/modules.usbmap                               FAILED
/lib/modules/2.6.22-8-server/modules.isapnpmap                            FAILED
/lib/modules/2.6.22-8-server/modules.seriomap                             FAILED
/lib/modules/2.6.22-8-server/modules.alias                                FAILED
/lib/modules/2.6.22-8-server/modules.symbols                              FAILED

---

### Post by iponeverything on 2008-10-15
If your machine is compromised, trying to clean it is far more trouble that its worth. I have done root-kit removals that have taken me days to figure out and even then I could not be totally sure the machine was secure.

I think its time for you to upgrade to hardy.

Back-up /home so that have your stuff and do a clean reinstall.

If you are afraid that you will loose something on that drive you will need, just take it out and install a new one and do the fresh install on that.

Either way -- I would get it off the net in case it is being used for something illegal.

---

### Post by fantata on 2008-10-16
Oh right. It's a dedicated server unfortunately, not used very much, but the plan is to use it more in the coming months. It would be tricky to remove this from the web and to start from scratch again.

I re-installed openssh - which seems to have solved the obvious problems. I have now restricted ssh access using hosts.allow and tcp-wrappers on openssh, and disabled root access. shorewall is blocking most ports too. I guess it's tricky to say for sure whether it's still compromised.

Would an upgrade to Hardy be good enough to eliminate the risks, or would that even not be enough?

If I have to start from scratch I guess I'll have to just suck up the webfusion cost for reinstating the original image and secure it right from the start next time. Any other options would be appreciated though.

Out of interest, is it likely to be a brute force attack on the root user account that lead to this? the pass was in the style of xxx0xxx00 - have now changed to a lot more complex for all users with ssh access.

---

### Post by fantata on 2008-10-16
I just ran chkrootkit, all ok.
I ran rkhunter and it found a file in /dev that listed logins with passwords in plain text up to the point I re-installed sshd.

Scary stuff for a linux noob.

---

### Post by iponeverything on 2008-10-16
> **fantata said:**
> Oh right. It's a dedicated server unfortunately, not used very much, but the plan is to use it more in the coming months. It would be tricky to remove this from the web and to start from scratch again.

I re-installed openssh - which seems to have solved the obvious problems. I have now restricted ssh access using hosts.allow and tcp-wrappers on openssh, and disabled root access. shorewall is blocking most ports too. I guess it's tricky to say for sure whether it's still compromised.

Would an upgrade to Hardy be good enough to eliminate the risks, or would that even not be enough?

If I have to start from scratch I guess I'll have to just suck up the webfusion cost for reinstating the original image and secure it right from the start next time. Any other options would be appreciated though.

Out of interest, is it likely to be a brute force attack on the root user account that lead to this? the pass was in the style of xxx0xxx00 - have now changed to a lot more complex for all users with ssh access.

There could have been any number of vectors, I can't really speculate without a little more to go on. Though, I don't think it was brute force against the root account. More than likely the initial breach was through a web application, and from there they were able to escalate through a local exploit. If that was the case then, no doubt, the vector still exist.

---

