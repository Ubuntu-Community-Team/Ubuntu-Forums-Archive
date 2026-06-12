---
title: "Only allow SSH for PHP applications"
date: 2011-09-16
forum: Server Platforms
---

### Post by iTimOSX on 2011-09-16
Hi Guys,

I currently have a control panel that uses SSH but I only want to allow that specific control panel to use SSH.
I own a VPS so I can always login even without SSH so thats not the problem

My Problem is that the FTP and SSH credentials are the same and I don't want any of my clients to use SSH via command line.

Is there any way I can block them from logging in via a command line but keep allowing them to use the web control panel with PHP-SSH?

I tried to use the hosts.allow and hosts.deny files for SSH but My control panel got bugged when I did.
Blocking a SSH client is no option because they need to login via the control panel!

Thanks in advance,

Tim

---

### Post by Porcini M. on 2011-09-17
One thing you could try is confining the sshd process with an apparmor profile, and have that profile disallow /bin/bash for example. The a bash shell cannot get invoked on ssh login.

---

### Post by zackwasa on 2011-09-17
We will need more details. What control panel do you have? What do you mean by "it uses ssh"? What does it do via SSH? If you want to disable SSH for a username you can just change its shell account to /bin/false and add that shell to /etc/shells so he can still login via FTP

---

### Post by iTimOSX on 2011-09-17
> **zackwasa said:**
> We will need more details. What control panel do you have? What do you mean by "it uses ssh"? What does it do via SSH? If you want to disable SSH for a username you can just change its shell account to /bin/false and add that shell to /etc/shells so he can still login via FTP


Hi, Thanks for the reply
It's a game control panel.
Just a control panel that uses SSH to start/stop/restart the gameserver I Don't wanna disable SSH because the script needs it.

Thanks in advance,
Tim

---

### Post by zackwasa on 2011-09-18
Well you can leave ssh enabled for it by giving it a shell and disabling for the other the way I described in my previous post

---

### Post by iTimOSX on 2011-09-19
> **zackwasa said:**
> Well you can leave ssh enabled for it by giving it a shell and disabling for the other the way I described in my previous post

Thanks but can you explain it a little bit more? I'm a beginner.

---

### Post by zackwasa on 2011-09-19
For each user you want to disable SSH access edit /etc/passwd and change:
```

/bin/bash

```
to
```

/bin/false

```
Then add */bin/false* to /etc/shells

This should allow them to FTP only. I hope it explains everything

---

