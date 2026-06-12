---
title: "Server Reboot: Normal or Abrupt"
date: 2022-07-06
forum: Server Platforms
---

### Post by abdullahmadani on 2022-07-06
Hi there,

We have an incident of a sudden reboot of our production ubuntu server 20.04. How to know what triggered the reboot and was it normal or abrupt? We do not have auditd installed. And the /var/log/syslog shows only clue that "[systemd] received: SIGINT" before shutdown.

Please advise

---

### Post by Doug S on 2022-07-06
Readers: See the same question on [askubuntu]("https://askubuntu.com/questions/1417551/server-reboot-how-to-analyze-the-root-cause").

Do you see anything in any other log file under /var/log? In particular /var/log/kern.log?

Is there anything in the journal? Try "journalctl --since=today" (I am not a journal expert, someone else might have a better suggestion).

---

### Post by abdullahmadani on 2022-07-07
Hi Doug S,

Thanks a lot for your reply.

Below is the entry in system journals (journalctl --since="<reboot time>")

Jul 05 06:58:22  systemd[1]: session-3042.scope: Stopping timed out. Killing.
Jul 05 06:58:22  systemd[1]: session-3042.scope: Killing process 4036182 (java) with signal SIGKILL.
Jul 05 06:58:22  systemd[1]: session-3042.scope: Killing process 4036265 (java) with signal SIGKILL.
...
...
Jul 05 06:58:22 systemd[1]: session-3042.scope: Failed with result 'timeout'.
Jul 05 06:58:22 systemd[1]: Stopped Session 3042 of user essam.
Jul 05 06:58:22 systemd[1]: Stopping Login Service...
Jul 05 06:58:22 systemd[1]: Stopping User Manager for UID 1000...
...
...
Jul 05 06:58:27 systemd[1]: Shutting down.
...
...
reboot

**From the above logs, it appears that the system went through a Normal Shutdown, isn't it?**
Also, we need to know **what triggered the shutdown**, as nobody from our team triggered it manually. Please advise

---

### Post by Doug S on 2022-07-07
> **abdullahmadani said:**
> 
**From the above logs, it appears that the system went through a Normal Shutdown, isn't it?**
Also, we need to know **what triggered the shutdown**, as nobody from our team triggered it manually. Please advise

Adding this from your comment over on askubuntu:

```
Unmounted Mount unit for lxd, revision 23243. swap.img.swap: Succeeded.
Deactivated swap /swap.img. shared.mount: Succeeded.
Unmounted /shared. multipathd[864]: --------shut down------- systemd-sysusers.service: Succeeded.
Stopped Create System Users. systemd-remount-fs.service: Succeeded.
Stopped Remount Root and Kernel File Systems.
Stopped Device-Mapper Multipath Device Controller.
Reached target Shutdown.
Reached target Final Step.
systemd-reboot.service: Succeeded
Finished Reboot Reached target Reboot Shutting down
```

From what has been provided, I do not know what triggered the shutdown. What is your processor make and model? Have you investigated thermal issues as was suggested on askubuntu?

---

### Post by abdullahmadani on 2022-07-07
Hi Doug S,

The Hardware make and model is Dell VxRail Hyper Converged Appliance running VMware on top of it. If it was a thermal issue then all the vm machines running on this Appliance would have been impacted. So we can rule out thermal issue.

As per the logs, please advise [B]does it seems normal shutdown or an abrupt shutdown?

[/B]Also, you see below the snipped output for "journalctl -b -3 -r | less", the shutdown process starts with the **"Received SIGINT."** journal entry. Does it give any clue?

[B][FONT=book antiqua][I]--output in reverse chronological order--
[/I][/FONT][/B]
Jul 05 06:56:52 systemd[1]: Stopped Daily rotation of log files.
Jul 05 06:56:52 systemd[1]: logrotate.timer: Succeeded.
Jul 05 06:56:52 systemd[1]: Stopped Refresh fwupd metadata regularly.
Jul 05 06:56:52 systemd[1]: fwupd-refresh.timer: Succeeded.
Jul 05 06:56:52 systemd[1]: Stopped Discard unused blocks once a week.
Jul 05 06:56:52 systemd[1]: fstrim.timer: Succeeded.
Jul 05 06:56:52 systemd[1]: Stopped Periodic ext4 Online Metadata Check for All Filesystems.
Jul 05 06:56:52 systemd[1]: e2scrub_all.timer: Succeeded.
Jul 05 06:56:52 systemd[1]: Stopped Daily apt download activities.
Jul 05 06:56:52 systemd[1]: apt-daily.timer: Succeeded.
Jul 05 06:56:52 systemd[1]: Stopped Daily apt upgrade and clean activities.
Jul 05 06:56:52 systemd[1]: apt-daily-upgrade.timer: Succeeded.
Jul 05 06:56:52 systemd[1]: Stopped target Timers.
Jul 05 06:56:52 systemd[1]: Stopped target RPC Port Mapper.
Jul 05 06:56:52 systemd[1]: Stopped target Host and Network Name Lookups.
Jul 05 06:56:52 systemd[1]: Stopped target Graphical Interface.
Jul 05 06:56:52 systemd[1]: Stopped target Cloud-init target.
Jul 05 06:56:52 systemd[1]: Removed slice system-modprobe.slice.
Jul 05 06:56:52 systemd[1]: Stopping Session 3042 of user essam.
Jul 05 06:56:52 systemd[1]: Received SIGINT.

---

### Post by Doug S on 2022-07-07
> **abdullahmadani said:**
> The Hardware make and model is Dell VxRail Hyper Converged Appliance running VMware on top of it. If it was a thermal issue then all the vm machines running on this Appliance would have been impacted. So we can rule out thermal issue.O.K., that is rather important information. That it was a VM really should have been mentioned in your original posts.

> **abdullahmadani said:**
> As per the logs, please advise [B]does it seems normal shutdown or an abrupt shutdown?

[/B]I do not know. It appears that something asked for a shutdown, but I am not certain.

I suggest looking for clues in all the logs on the host computer.

---

### Post by SeijiSensei on 2022-07-07
Do any other users have root access to this virtual machine besides you and could trigger a shutdown event?

---

### Post by abdullahmadani on 2022-07-07
Hi Doug s,

I have looked at syslog, journals, last -x but all I am getting to know is that there was a Shutdown triggered followed by a reboot. But what's unclear is:

What triggered Shutdown?
or 
Was it simply a crash?

Please advise am I missing something here?

---

### Post by abdullahmadani on 2022-07-07
Hi Seiji,

There is a user which has root access, but interestingly "last" command doesn't show any trace of login of that user before shutdown was triggered. Please see the output below:

essam       pts/0               <hostname IP>          Tue Jul  5 06:59 - 09:48  (02:49)
runlevel    (to lvl 5)           5.4.0-121-generi Tue Jul  5 06:59 - 09:50  (02:51)
reboot      system boot      5.4.0-121-generi Tue Jul  5 06:58 - 09:50  (02:51)
[COLOR=#ff0000]**shutdown system down     5.4.0-104-generi Tue Jul  5 06:58 - 06:58  (00:00)**[/COLOR]
essam      pts/1               <hostname IP>           Fri Jul  1 04:00 - 04:05  (00:04)

"essam" (root access user) was not logged-in on or before shutdown. However the user logged in soon after the reboot completed (Tue Jul  5 06:59). If the user has triggered the shutdown, it should have been reported in "last -x" command before shutdown event, isn't it. Please advise

---

### Post by Doug S on 2022-07-07
If someone local to the VM initiated the shutdown, then it should be noted in the /var/log/auth.log file.
You should also be examining the /var/log/kern.log file and all log files, including sub-directories, in /var/log.

It does not look like a crash me, but rather an initiated shutdown. However, I am not certain.

I would also suggest you look at all log files on your host computer. Is your host OS also Ubuntu linux or something else?

I am not familiar with vmware, but with QEMU/KVM a guest VM can be shutdown from the host. I would think such ability would be available for vmware guests also.

---

### Post by TheFu on 2022-07-11
When I've had a VM shutdown unrequested, it was due to some hardware fault on the host.  In my situation, it was that the storage was failing and corruption was happening, so the hypervisor was shutting down the VM to protect it.

There are lots of VMware hypervisors (6 at last count), so perhaps stating clearly which it is so we don't have to dig for hardware/machine information (I don't recognize that dell).
Was the system bought new from Dell or used?  There have been lots and lots of used servers on the market with tiny hardware issues the last few years. Add in the bouncy shipping for a second time and parts get looser.  I've transported a server 4 hrs and on arrival, it seemed fine, booted, ran ... but there was some software licenses tied to the 2nd CPU socket (which had become loose).  The following Monday, a team of devs noticed that they couldn't work due to license failures.  Everything else about the system was working and seemed fine.

---

### Post by MAFoElffen on 2022-07-13
I agree with TheFu on sometimes hidden HW issues of Used, but you didn't mention that it was used... 

I have a Dell PowerEdge 740, that I got used, that about once every 6 months gets a timer chip error and reboots. I don't know why. But on reboot it is fine. But things like that (that have to do with hardware) show up in the Dell IDRAC logs, and trigger the Front console LED error messages. And something like that would affect more than just one VM.

You didn't see any errors or warnings in the logs before those that you posted? It just seems odd that it was without any kind of warning. Or that there is no evidence of a user that asked for it.

EDIT:
I am with Doug S and would check from 3 minutes before that SIGINT timestamp (leading up to that) in all those logs.

---

### Post by abdullahmadani on 2022-07-17
Hi Doug S,

Below is the output from auth.log file. Does it suggest that essam user has triggered reboot? Can you please help me understanding the below output

Jul  5 06:59:13  sshd[1029]: Server listening on 0.0.0.0 port 22.
Jul  5 06:59:13  sshd[1029]: Server listening on :: port 22.
Jul  5 06:59:13  systemd-logind[1008]: New seat seat0.
Jul  5 06:59:13  systemd-logind[1008]: Watching system buttons on /dev/input/event0 (Power Button)
Jul  5 06:59:13  systemd-logind[1008]: Watching system buttons on /dev/input/event1 (AT Translated Set 2 keyboard)
Jul  5 06:59:22  sshd[1263]: Accepted password for essam from 10.2.15.52 port 63714 ssh2
Jul  5 06:59:22  sshd[1263]: pam_unix(sshd:session): session opened for user essam by (uid=0)
Jul  5 06:59:22  systemd-logind[1008]: New session 1 of user essam.
Jul  5 06:59:22  systemd: pam_unix(systemd-user:session): session opened for user essam by (uid=0)

---

### Post by TheFu on 2022-07-17
That login just shows that the user logged in, changed to root, nothing more.  Would be smart to train your team not to use the root account, rather, use sudo for command. All sudo commands are logged, unlike root.

---

### Post by Doug S on 2022-07-17
You keep showing us log entries from after the reboot and/or after the reboot has been initiated. You are looking for events just prior to July 5th 06:56:52.

@TheFu , and for my own education. How did you deduce that user essam changed to root? I am not able to make that deduction from the log file snipet. If I just log in as me via ssh on a VM I get:

```
Jul 17 10:14:51 desk-ff sshd[33581]: Accepted password for doug from 192.168.111.122 port 51805 ssh2
Jul 17 10:14:51 desk-ff sshd[33581]: pam_unix(sshd:session): session opened for user doug by (uid=0)
Jul 17 10:14:51 desk-ff systemd-logind[538]: New session 9 of user doug.
```

If I later switch to root (and then exit), I get:

```

Jul 17 10:26:27 desk-ff sudo:     doug : TTY=pts/1 ; PWD=/home/doug ; USER=root ; COMMAND=/usr/bin/su
Jul 17 10:26:27 desk-ff sudo: pam_unix(sudo:session): session opened for user root by doug(uid=0)
Jul 17 10:26:27 desk-ff su: (to root) doug on pts/1
Jul 17 10:26:27 desk-ff su: pam_unix(su:session): session opened for user root by doug(uid=0)
Jul 17 10:26:30 desk-ff su: pam_unix(su:session): session closed for user root
Jul 17 10:26:30 desk-ff sudo: pam_unix(sudo:session): session closed for user root

```

@ abdullahmadani : If I initiate a reboot I get:

```

Jul 17 10:29:46 desk-ff [COLOR="#FF0000"]sudo[/COLOR]:     doug : TTY=pts/1 ; PWD=/home/doug ; USER=root ; COMMAND=[COLOR="#FF0000"]/usr/sbin/shutdown -r now[/COLOR]
Jul 17 10:29:46 desk-ff sudo: pam_unix(sudo:session): session opened for user root by doug(uid=0)

```

If I force a reboot from the host I get:

```

Jul 17 10:36:42 desk-ff systemd-logind[566]: Power key pressed.
Jul 17 10:36:42 desk-ff systemd-logind[566]: System is powering down.
Jul 17 10:36:42 desk-ff sshd[1760]: pam_unix(sshd:session): session closed for user doug
Jul 17 10:36:50 desk-ff sshd[623]: Server listening on 0.0.0.0 port 22.
Jul 17 10:36:50 desk-ff sshd[623]: Server listening on :: port 22.
Jul 17 10:36:50 desk-ff systemd-logind[570]: Watching system buttons on /dev/input/event0 (Power Button)
Jul 17 10:36:50 desk-ff systemd-logind[570]: Watching system buttons on /dev/input/event1 (AT Translated Set 2 keyboard)
Jul 17 10:36:50 desk-ff systemd-logind[570]: New seat seat0.

```

---

### Post by TheFu on 2022-07-17
```
 Jul 5 06:59:22 systemd: pam_unix(systemd-user:session): session opened for user essam by (uid=0) 
```
 
made me think it was root. I misread, clearly.

---

### Post by MAFoElffen on 2022-07-17
Yes... and if caused by a hardware or OS error triggered event, there would be a traceback within the previous 100 log entries previous to the reboot... Right?

---

### Post by abdullahmadani on 2022-07-18
> **Doug S said:**
> You keep showing us log entries from after the reboot and/or after the reboot has been initiated. You are looking for events just prior to July 5th 06:56:52.

Hi Doug,
Apologies for the inconvenience. But the reason I am showing log entries from after the reboot and/or after the reboot has been initiated is because there is no clue of any user (human) activity before the reboot. Please see the below complete output including log entries before the reboot:

Jul  5 00:00:01  CRON[113615]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul  5 00:00:04  CRON[113615]: pam_unix(cron:session): session closed for user root
Jul  5 00:17:01  CRON[114568]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul  5 00:17:01  CRON[114568]: pam_unix(cron:session): session closed for user root
Jul  5 01:17:01  CRON[117789]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul  5 01:17:01  CRON[117789]: pam_unix(cron:session): session closed for user root
Jul  5 02:17:01  CRON[121044]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul  5 02:17:01  CRON[121044]: pam_unix(cron:session): session closed for user root
Jul  5 03:10:01  CRON[123918]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul  5 03:10:01  CRON[123918]: pam_unix(cron:session): session closed for user root
Jul  5 03:17:01  CRON[124342]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul  5 03:17:01  CRON[124342]: pam_unix(cron:session): session closed for user root
Jul  5 04:17:01  CRON[127710]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul  5 04:17:01  CRON[127710]: pam_unix(cron:session): session closed for user root
Jul  5 05:17:01  CRON[130837]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul  5 05:17:01  CRON[130837]: pam_unix(cron:session): session closed for user root
Jul  5 06:17:01  CRON[133835]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul  5 06:17:01  CRON[133835]: pam_unix(cron:session): session closed for user root
Jul  5 06:25:01  CRON[134240]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul  5 06:25:01  CRON[134240]: pam_unix(cron:session): session closed for user root
Jul  5 06:59:13  sshd[1029]: Server listening on 0.0.0.0 port 22.
Jul  5 06:59:13  sshd[1029]: Server listening on :: port 22.
Jul  5 06:59:13  systemd-logind[1008]: New seat seat0.
Jul  5 06:59:13  systemd-logind[1008]: Watching system buttons on /dev/input/event0 (Power Button)
Jul  5 06:59:13  systemd-logind[1008]: Watching system buttons on /dev/input/event1 (AT Translated Set 2 keyboard)
Jul  5 06:59:22  sshd[1263]: Accepted password for essam from 10.2.15.52 port 63714 ssh2
Jul  5 06:59:22  sshd[1263]: pam_unix(sshd:session): session opened for user essam by (uid=0)
Jul  5 06:59:22  systemd-logind[1008]: New session 1 of user essam.
Jul  5 06:59:22  systemd: pam_unix(systemd-user:session): session opened for user essam by (uid=0)

Please advise.

---

### Post by Doug S on 2022-07-18
> **abdullahmadani said:**
> Hi Doug,
Apologies for the inconvenience. But the reason I am showing log entries from after the reboot and/or after the reboot has been initiated is because there is no clue of any user (human) activity before the reboot.
...

Please advise.

I am out of ideas. Rereading all the posts, I would consider a hardware issue, as suggested by others, and that the re-boot might have been initiated by the host.

---

### Post by abdullahmadani on 2022-07-18
> **Doug S said:**
> I am out of ideas. Rereading all the posts, I would consider a hardware issue, as suggested by others, and that the re-boot might have been initiated by the host.

Thanks for your time and I really appreciate your level of engagement in this issue. Lastly, can you please advise on the only clue that I mentioned in my earlier posts. You see, the shutdown got initiated soon after receiving "SIGINT", as reported by syslog file:

Jul  5 05:17:01  CRON[130838]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  5 06:17:01  CRON[133836]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  5 06:25:01  CRON[134241]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))
Jul  5 06:38:24  systemd[1]: Starting Daily apt upgrade and clean activities...
Jul  5 06:38:27  systemd[1]: apt-daily-upgrade.service: Succeeded.
Jul  5 06:38:27  systemd[1]: Finished Daily apt upgrade and clean activities.
[SIZE=3]**Jul  5 06:56:52  systemd[1]: Received SIGINT.**[/SIZE]
Jul  5 06:56:52  systemd[1]: Stopping Session 3042 of user essam.
Jul  5 06:56:52  systemd[1]: Removed slice system-modprobe.slice.
Jul  5 06:56:52  systemd[1]: Stopped target Cloud-init target.
Jul  5 06:56:52  systemd[1]: Stopped target Graphical Interface.
Jul  5 06:56:52  systemd[1]: Stopped target Host and Network Name Lookups.
Jul  5 06:56:52  systemd[1]: Stopped target RPC Port Mapper.
Jul  5 06:56:52  systemd[1]: Stopped target Timers.

I know this is not enough to conclude something concrete, but please consider and tell me what do you think about **sigint **signal. What might be the possible interpretations of receiving SIGINT before a Shutdown / Reboot.

Thanks a lot.

---

### Post by Doug S on 2022-07-18
> **abdullahmadani said:**
> 
I know this is not enough to conclude something concrete, but please consider and tell me what do you think about **sigint **signal. What might be the possible interpretations of receiving SIGINT before a Shutdown / Reboot.
Well yes, SIGINT is definitely involved and is telling systemd to terminte everything (I think). The question is why was the signal sent?

I only have 3 occurrences in my journal and they are a year or more old, so I don't recall what I was doing, but the computer is my main Ubuntu 20.04.4 test server so abusing it during testing is normal. The only example I have with any other insight is from over a year ago where the watchdog timed out and I seem to have been playing with MSRs (Machine Specific Registers) at the time.

```

Note: that is 2021 below:
Jul 05 16:57:49 s19 systemd[1]: systemd-timesyncd.service: Watchdog timeout (limit 3min)!
Jul 05 16:57:49 s19 systemd[1]: systemd-timesyncd.service: Killing process 785 (systemd-timesyn) with signal SIGABRT.
Jul 05 16:57:55 s19 sudo[5468]:     doug : TTY=pts/2 ; PWD=/home/doug/c ; USER=root ; COMMAND=/usr/sbin/rdmsr --bitfield 31:16 -u 0x611
Jul 05 16:57:55 s19 sudo[5468]: pam_unix(sudo:session): session opened for user root by doug(uid=0)
Jul 05 16:57:55 s19 sudo[5468]: pam_unix(sudo:session): session closed for user root
Jul 05 16:58:49 s19 systemd[1]: systemd-udevd.service: Watchdog timeout (limit 3min)!
Jul 05 16:58:49 s19 systemd[1]: systemd-udevd.service: Killing process 510 (systemd-udevd) with signal SIGABRT.
Jul 05 16:58:55 s19 sudo[5473]:     doug : TTY=pts/2 ; PWD=/home/doug/c ; USER=root ; COMMAND=/usr/sbin/rdmsr --bitfield 31:16 -u 0x611
Jul 05 16:58:55 s19 sudo[5473]: pam_unix(sudo:session): session opened for user root by doug(uid=0)
Jul 05 16:59:19 s19 systemd[1]: systemd-timesyncd.service: State 'stop-watchdog' timed out. Terminating.
Jul 05 17:00:19 s19 systemd[1]: systemd-udevd.service: State 'stop-watchdog' timed out. Terminating.
Jul 05 17:00:50 s19 systemd[1]: systemd-timesyncd.service: State 'stop-sigterm' timed out. Killing.
Jul 05 17:00:50 s19 systemd[1]: systemd-timesyncd.service: Killing process 785 (systemd-timesyn) with signal SIGKILL.
Jul 05 17:00:50 s19 systemd[1]: systemd-timesyncd.service: Killing process 933 (sd-resolve) with signal SIGKILL.
Jul 05 17:01:50 s19 systemd[1]: systemd-udevd.service: State 'stop-sigterm' timed out. Killing.
Jul 05 17:01:50 s19 systemd[1]: systemd-udevd.service: Killing process 510 (systemd-udevd) with signal SIGKILL.
Jul 05 17:02:10 s19 systemd[1]: [COLOR="#FF0000"]Received SIGINT[/COLOR].

```

---

### Post by abdullahmadani on 2022-07-19
> **Doug S said:**
> Well yes, SIGINT is definitely involved and is telling systemd to terminte everything (I think). The question is why was the signal sent?

Since the systemd had received the SIGINT signal, I referred to "man systemd" pages. The man pages say:

 SIGINT
           Upon receiving this signal the systemd system manager will start the ctrl-alt-del.target unit. This is mostly equivalent to systemctl start
           ctrl-alt-del.target --job-mode=replace-irreversibly. If this signal is received more than 7 times per 2s, an immediate reboot is triggered. Note that
           pressing Ctrl+Alt+Del on the console will trigger this signal. Hence, if a reboot is hanging, pressing Ctrl+Alt+Del more than 7 times in 2 seconds is a
           relatively safe way to trigger an immediate reboot.

Do you think the above relates to some reboot signal from the Host (VMware)? Please advise

---

### Post by Doug S on 2022-07-19
> **abdullahmadani said:**
> Do you think the above relates to some reboot signal from the Host (VMware)? Please adviseYes, I think that is a real possibility. I use KVM/QEMU and have no experience with VMware, but suggest you try all possible VMware methods to force a guest to reboot and look for a correlation.

---

### Post by TheFu on 2022-07-19
> **abdullahmadani said:**
>  Do you think the above relates to some reboot signal from the Host (VMware)? Please advise

See my first post, first sentence.
>  When I've had a VM shutdown unrequested, it was due to some hardware fault on the host. In my situation, it was that the storage was failing and corruption was happening, so the hypervisor was shutting down the VM to protect it.

---

### Post by kinddolphin8827 on 2022-08-13
In my  humble opinion this is a prime example of system overload either that or  maybe even an issue with a storage device beginning to fail. It may even  be that the OP is experiencing  these issues do to bugs in the kernel or other user land   software in  the  daily  workload that they  are placing on the system. Are theier any fault talerant storage  subsystem measures being taken like say a raid array, or is it a jbod configuration?

---

### Post by TheFu on 2022-08-13
The OP posted and hasn't been back here in 3 weeks.  

That says that this wasn't important or they found a solution.  I tend to give people a few days to follow up and when they don't, de-subscribe from the thread.
Avoiding necro-posting is a judgement call here.

---

### Post by abdullahmadani on 2022-11-09
> **TheFu said:**
>  The OP posted and hasn't been back here in 3 weeks.  

That says that this wasn't important, or they found a solution. 

Honestly, this is not the case. Neither it was insignificant, nor did I find the solution. Actually, we were just going into loop, from VM Host to Storage subsystem and back into the OS kernel, without able to figure out the root cause. There are more than 500 VMs in this host, but none of them impacted except this Server and a few others that are hosting the same Application (Appian). There was no issue reported in Application logs before the abrupt shutdown.

The abrupt restart was very weird and did not reoccur since then. However, what caused the abrupt reboot is still an "unknown risk" for us that may or may not hit again in future.

---

