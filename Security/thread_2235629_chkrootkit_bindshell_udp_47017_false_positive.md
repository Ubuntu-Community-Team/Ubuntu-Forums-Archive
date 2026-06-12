---
title: "chkrootkit bindshell udp 47017 false positive???"
date: 2014-07-22
forum: Security
---

### Post by a-you on 2014-07-22
Hi all. Not sure if this is the place to ask this, sorry if not. I'm using ubuntu studio 14.4 64 bit. Just a few minutes ago chkrootkit reported:

Checking `bindshell'...                                     INFECTED (PORTS:  47017)

and
```
netstat -taupen
```
was showing

udp        0      0 0.0.0.0:47017           0.0.0.0:*                           109        12648       -

but in searching the interwebs I'm getting the impression that this is used specifically by steaming media sometimes, and I *think*, though not certain, that I happened to be watching a flash presentation in firefox at the moment ckrootkit happened to be run.

I have rebooted and now
```
netstat -taupen
```
doesn't return anything re port 47017

chkrootkit also now (since restarting) shows

Checking `bindshell'...                                     not infected

Rkhunter reported no problems, even before the restart.

To me it seems like it was a brief false positive from chkrootkit, but I'm naive about these things, so if anybody that knows would please comment I'd much appreciate it. Thanks in advance!!!

---

### Post by a-you on 2014-07-23
Bumping, if I may. If anybody that's more expert in this could quickly comment it'd be appreciated (thanks).

---

### Post by unspawn on 2014-07-24
> **a-you said:**
> Hi all. Not sure if this is the place to ask this, sorry if not.  Well it's this boards security forum so...   > **a-you said:**
> ```
Checking `bindshell'...                                     INFECTED (PORTS:  47017)
``` Chkrootkit may not show the Process Id in its output but that's what you should be looking for, because most of the time a process using networking will show resources in use. Those resources may give you a clue as to what's going on. Check with ```
lsof -Pwlnp [PID_or_Process]
``` Obviously that won't work when process hiding is used or if a network socket is at the end of its close down cycle or if there's no response time like when you're running Chkrootkit from a cron job. Also note Chkrootkit hasn't been updated in ages and you shouldn't rely on a single tool anyway. More importantly security is a continuous process of auditing and adjusting. The investment of hardening a machine and configuring regular auditing before exposing it (and actually following up on audit reports) always pays off.

---

### Post by HermanAB on 2014-07-24
Howdy,

Chrootkit and its ilk are not particularly useful and don't work very well.  The last time I encountered a root kit was circa 1987 on a Sun work station, so maybe you should just relax a bit!

---

### Post by a-you on 2014-07-25
Thanks for both of your comments.

Wow 1987!! That's kind of astonishing. From things I read on the interenet I'd have imagined they're some kind of imminent danger, sort of like the virus fears of some years ago.

And to unspawn: that's very informative, thanks! I mean the details of what to look for and how to go about it. chkrootkit was running from cron (or anacron). I still have chkrootkit installed though since rkhunter is kept up to date I consider its output to be far more definitive/informative/trustworthy.

Just for the sake of education here: it looks like if this sort of message surfaces again the thing to do would be to try to determine the PID. Again, just for the sake of education, perhaps chkrootkit in "expert" mode would provide that info. I'm looking at the man page for unhide at the moment and it looks like this is a tool that can reveal process IDs even for processes that have tried to hide themselves.

---

### Post by unspawn on 2014-07-26
> **a-you said:**
> Wow 1987!! That's kind of astonishing.  No it isn't. (Apart from the fact some people thinking personal experience equals whatever happens on the 'net right now) traditional root kit usage simply has been dwindling for years now.    > **a-you said:**
> I still have chkrootkit installed though since rkhunter is kept up to date I consider its output to be far more definitive/informative/trustworthy. Like I said before Chkrootkit hasn't been maintained for some years now. (But then again that never kept people from using obsolete software like PortSentry either.) Chkrootkit, Rootkit Hunter, AIDE or even tripwire are examples of post-incident tools. They all serve some purpose but they will only note changes after the fact. Also people scare each other often and easily with root kits (ohhh, Evil...) while conveniently forgetting all the other stuff Linux machines may be susceptible to. Ounce of Prevention-wise the best way would be to *forestall* situations that could lead to a breach of compromise. Best way to start with that would be to follow the installation and security documentation your distribution provides, regularly (continuously?) audit the machine, follow best practices and use common sense.   > **a-you said:**
> Just for the sake of education here: it looks like if this sort of message surfaces again the thing to do would be to try to determine the PID.  Yes, but that will be difficult when running a cron job. Plus for shortlived processes gathering the nfo may be too late anyway. Would be more helpful if Chkrootkit provided 'lsof -Pwln'-like nfo in the first place...   > **a-you said:**
> I'm looking at the man page for unhide at the moment and it looks like this is a tool that can reveal process IDs even for processes that have tried to hide themselves. It can but only under certain circumstances. If you ever suspect a breach of compromise involving a traditional root kit it's prolly easier to boot a Live CD like HELIX or KNOPPIX, mount the file system read-only and then look for clues.

---

### Post by a-you on 2014-07-30
Thanks a lot for the additional comments.

---

