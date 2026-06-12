---
title: "Running SSHD on multiple ports?"
date: 2007-06-05
forum: Server Platforms
---

### Post by apoth on 2007-06-05
I thought you could just specify two ports like:

Port 22
Port 3690

in /etc/ssh/sshd_config

But the ssh server runs on port 22 and not on 3690? Does anyone know why and how I can fix it?

Thanks

---

### Post by turinglabs on 2007-06-05
This should work. The sshd_config(5) man page says " Multiple options of this type are permitted", and I've done this before. After you reload your SSH server config, what does a 'netstat -ant' return? What do you have as a 'ListenAddress' in your config file, and does it precede your Port option (Port is generally near the top of the file)?

---

### Post by apoth on 2007-06-05
It doesn't return any sign of the second port.

```
$ sudo netstat -antp|grep ssh
tcp6       0      0 :::22                   :::*                    LISTEN     27880/sshd
tcp6       0      0 ::ffff:192.168.42.18:22 ::ffff:192.168.42.:3774 ESTABLISHED26318/sshd: rich [p
tcp6       0      0 ::ffff:192.168.42.18:22 ::ffff:192.168.42.:3509 ESTABLISHED28044/sshd: dev [pr
tcp6       0     52 ::ffff:192.168.42.18:22 ::ffff:192.168.42.:4990 ESTABLISHED28325/sshd: rich [p
```

I haven't got any ListenAddress lines in at the moment. I've tried putting in ListenAddress 192.168.42.186 afterwards, and ListenAddress 192.168.42.186:22 with ListenAddress 192.168.42.186:3096. No luck with any.

---

### Post by apoth on 2007-06-05
I've just checked my home machine and that works fine with the two ports and no ListenAddress. The problem machine though is running edgy while the home machine is running feisty - that wouldn't be the issue would it?

---

### Post by turinglabs on 2007-06-05
> **apoth said:**
> I've just checked my home machine and that works fine with the two ports and no ListenAddress. The problem machine though is running edgy while the home machine is running feisty - that wouldn't be the issue would it?

No, the config format is the same. Do you have something already running on that secondary port? I can't think of another reason for this not to work. Is there anything in your syslog or daemon.log during a restart?

---

### Post by apoth on 2007-06-05
Argh, yes, subversion's running there, I must've missed that earlier. Problem solved, thanks. :)

---

