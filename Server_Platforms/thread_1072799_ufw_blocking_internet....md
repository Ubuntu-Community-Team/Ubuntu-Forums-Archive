---
title: "ufw blocking internet..."
date: 2009-02-17
forum: Server Platforms
---

### Post by Batuhan on 2009-02-17
Hello all,

I got my first vps hosting and trying to get the damn firewall working.
Using 8.04

I installed ufw, did:
```
$ ufw default deny
```

and added my ssh ports manually, and after I did 

```
$ ufw allow <mysshport>
$ ufw enable
```
ssh works fine...

But the os loses internet access. So I do:
```
$ ufw enable http
```

and "ufw status" shows port 80 tcp is ok, but no internet. I can't do apt-get etc... If I say "ufw disable" all works fine.

I'm not a seasoned professional, this is my first personal server so to say... I appreciate any help. What should I add to get http working?

Thanks

---

### Post by R.Bucky on 2009-02-17
Not much to say about this issue, but you might try something. Whenever I would open a port for an app, I would allow 80, ufw disable, then ufw enable. Basically, turn it off then on again. Otherwise, did you open port 443 as well?

Got me...

---

### Post by Batuhan on 2009-02-18
Yeah I also tried disablin-enabling and enabling and rebooting. Also tried enabling https.

When the firewall is enabled, actually I can access my server from a browser so my webpage serves well (when port 80 is open).

But can't access web from cli. apt-get can't resolve, I can't ping, so no tubes. Don't know what is going on.

---

### Post by moberry on 2009-02-18
Try allowing DNS. port 53.

---

### Post by Batuhan on 2009-02-18
Thanks but still no joy... I've enabled logging for ufw and nothing shows up in the log...

```

root@batuhan:~# ufw status
Firewall loaded

To                         Action  From
--                         ------  ----
<sshport>:tcp              ALLOW   Anywhere
<sshport>:udp              ALLOW   Anywhere
80:tcp                     ALLOW   Anywhere
53:tcp                     ALLOW   Anywhere
53:udp                     ALLOW   Anywhere

```

---

### Post by moberry on 2009-02-18
Just because I have to ask:

<sshport> is what you edited correct? and not what your ufw status actually says?

I use ufw on my box as well, ufw allows all outgoing connections with no restrictions. I can't think of why you would be having problems.

1. do a "dmesg" and paste in some of the firewall hits.
2. paste your "ifconfig" as well.

---

### Post by nefariouslacker on 2009-06-18
I am having exactly the same problem, also with a new VPS server.  Please let me know what you discover.

Thanks!

---

### Post by GG_Crew on 2010-04-07
I was having the same problem, but might have stumbled upon the solution!

[aside]
It's worth mentioning that ufw has undergone a significant evolution in recent versions.  Older versions did not discriminate between inbound and outbound traffic - blocking http meant nothing could get in or out on port 80/tcp.  Newer versions allow for one-way blocking.  If no direction is specified, ufw defaults to only allowing incoming traffic.
[/aside]

Using ufw 0.29-4ubuntu1

I have a server that's dedicated to SVN hosting.  Here  is my initial ufw setup:
```

ufw default deny incoming
ufw default deny outgoing
ufw limit ssh
ufw allow svn
ufw logging on
ufw enable
```Things were working swimmingly until I tried my first apt-get or aptitude.  Both programs errored with 'unable to resolve' messages.

A fair amount of trial and error later, plus a hint from another user in this thread, and here's what's working for me:
```

ufw default deny incoming
ufw default deny outgoing
ufw limit ssh
ufw allow svn
ufw allow out http
ufw allow out 53
ufw logging on
ufw enable
```Allowing outbound traffic on port 53 is needed to resolve domain names (ie translating "security.ubuntu.com" to "91.189.88.37")
Allowing outbound traffic on http (port 80/tcp) is needed to actually grab the package lists and packages.

I did not have to restart the firewall with a set of "ufw disable", "ufw enable" commands - the changes took effect immediately.

Here is the output of "ufw status":
```

Status: active

To                         Action      From
--                         ------      ----
22                         LIMIT       Anywhere
3690                       ALLOW       Anywhere

53                         ALLOW OUT   Anywhere
80/tcp                     ALLOW OUT   Anywhere
```Hope this helps!

---

