---
title: "shut down takes a lot of time"
date: 2023-11-18
forum: Ubuntu Development Version
---

### Post by Claus7 on 2023-11-18
Hello,

I'm noticing this from mantic days and using mantic I face it from time to time, not always. Trying to shut down ubuntu was a really fast process. I might have to wait 3' in order for ubuntu desktop to appear irrespective of using wayland, X11 or flashback, yet when attempting to shut down, the vast majority of times it was really fast: max 5" or so.

This is not the case for mantic and noble. While installing noble under virtualbox, I think that I pressed something and during boot and shut down processes I'm able to see text. During the last shut down I noticed the following message:
Job session-6.scope/stop running (.../1min 30s)

and it took around that time in order for the system to shut down. The "..." represent the time counting until this process stops running. Have you noticed anything similar?

I'm attaching a screenshot I had the time to take. During shutdown I haven't any processes running, at least that I know of.

Regards!

---

### Post by Doug S on 2023-11-18
Do the logs for the last session reveal anything?

```
journalctl -b -1
```

---

### Post by Claus7 on 2023-11-18
Hello,

thank you *Doug S* for your response. Luckily I hadn't used the noble session after the shutdown problem. Taking a look at it, I have isolated some parts, which I consider relevant (&#925;&#959;&#949; stands for Nov):
> &#925;&#959;&#949; 18 15:20:48 noble systemd[1]: Started session-6.scope - Session 6 of User snap.

> &#925;&#959;&#949; 18 15:21:28 noble systemd[1]: Stopping session-6.scope - Session 6 of User snap...

> &#925;&#959;&#949; 18 15:21:31 noble systemd[2470]: snap.snapd-desktop-integration.snapd-desktop-integration.service: Failed with result 'exit-code'.
&#925;&#959;&#949; 18 15:21:48 noble systemd-logind[731]: Session 6 logged out. Waiting for processes to exit.
&#925;&#959;&#949; 18 15:22:58 noble systemd[1]: session-6.scope: Stopping timed out. Killing.

with the last three being consecutive messages, so I suppose that snap might be the root of the problem. Do you agree? 
The file size is greater than what I can attach (~550kB).

Regards!

---

### Post by Claus7 on 2023-11-18
Hello,

shutting down anew noble, process was really fast. 
I have to mention that I have noticed a lot of logging out problems in the meantime (while trying to copy paste the output of messages e.t.c.), yet this is another issue.

Regards!

---

### Post by MAFoElffen on 2023-11-19
Depends. I read this thread, mainly because, lately, there has been more and more users who cannot shut down their computers or reboot. Not sure if this is something with the newer kernels, or some kind of 'perfect-storm' combination of hardware or configs... But it is concerning that the frequency of this seem to be on the rise.

The first time I saw it was with Rubi1200 with Mantic. Since then, users affects, I recommend to them to join Rubi1200 Bug report as affected. Even htogh the numbers of users affected has gone up, I don;t see any progress on the bug report.

---

### Post by Claus7 on 2023-11-19
Hello,

> **MAFoElffen said:**
> Depends. I read this thread, mainly because, lately, there has been more and more users who cannot shut down their computers or reboot. Not sure if this is something with the newer kernels, or some kind of 'perfect-storm' combination of hardware or configs... But it is concerning that the frequency of this seem to be on the rise.

The first time I saw it was with Rubi1200 with Mantic. Since then, users affects, I recommend to them to join Rubi1200 Bug report as affected. Even htogh the numbers of users affected has gone up, I don;t see any progress on the bug report.

now that you mentioned the name I remember. I provide two links that mentioned that issue:
[https://ubuntuforums.org/showthread.php?t=2492002&highlight=Rubi1200](https://ubuntuforums.org/showthread.php?t=2492002&highlight=Rubi1200)
[https://ubuntuforums.org/showthread.php?t=2490772&page=2&highlight=Rubi1200](https://ubuntuforums.org/showthread.php?t=2490772&page=2&highlight=Rubi1200)


the bug report here:
[https://bugs.launchpad.net/ubuntu/+bug/2036987](https://bugs.launchpad.net/ubuntu/+bug/2036987)

in my case system will shutdown hopefully after some time. Yet, it will need more time than usual in order to accomplish the task.

Regards!

---

### Post by Claus7 on 2023-11-22
Hello,

this is part of the mantic output that takes a lot of time:
> &#925;&#959;&#949; 22 00:33:51 inno-U5 systemd[1]: Stopped systemd-remount-fs.service - Remount Root and Kernel File Systems.
&#925;&#959;&#949; 22 00:35:08 inno-U5 systemd[1]: lvm2-monitor.service: Deactivated successfully.


I saw that there is an update for systemd that might fix the issue.

Regards!

---

### Post by MAFoElffen on 2023-11-22
Crossing fingers...

---

### Post by Claus7 on 2023-11-25
Hello,

for some time now, I face no issues with shutdown process of mantic. Also I noticed a considerable decrease in ram usage after the latest update of systemd. I do not know if these are related though. An update on the issue.

Regards!

---

### Post by ajgreeny on 2023-12-07
I'm writing this on an Android tab at the moment so can't search for logs etc but I sometimes see a 90s delay waiting for a cups systemd job to stop running. When that 90s times out shutdown happens normally.
I will search for proper details when back on my Xubuntu Noble system and report back.

---

### Post by MAFoElffen on 2023-12-08
Hint... Use
```

journalctl -b -1 -r -g 'systemd' --no-pager | head -n200

```
That should get what is pertinent on shutdown. Journal still logs after syslog shuts down until it reaches the shutdown target.

---

### Post by Claus7 on 2023-12-11
Hello,

observing for some time now both mantic and noble I can report the following:
1) after today's updates noble shuts down really fast. Usually I had to wait for 1' and 30" for a process to finish, yet when it was done, system was off as normal. 
2) I think that mantic, for a long time now, shuts down even faster that what I got used to. The great difference was notable after the latest update on systemd. 

Just that for the time being,
Regards!

---

### Post by Claus7 on 2024-02-26
Hello,

an update to this issue is the following:
1) for mantic: (since this thread started during mantic dev days) the last time I noticed a delay it was due to tracker miner
2) for noble: under virtualbox seems that it goes well

Regards!

---

### Post by Claus7 on 2024-05-03
Hello,

having upgraded to noble, for some time now, the shutdown process seems normal.

Regards!

---

