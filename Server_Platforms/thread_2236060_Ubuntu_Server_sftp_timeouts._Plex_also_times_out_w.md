---
title: "Ubuntu Server sftp timeouts. Plex also times out when off-network."
date: 2014-07-24
forum: Server Platforms
---

### Post by cswartzv6 on 2014-07-24
Hello! 

I have an Ubuntu home web/media server set up, hosts a website as well as my plex media. 

However, I have a bit of an on-going issue with things timing out. 

PLEX: If I'm off my home network, my plex app on IOS can see my content, but stops streaming after a few seconds. When I'm at home, everything seems to stream without issue. I have checked the port forwarding and things seem to be okay there.

SFTP: So, I can successfully SSH into the server from off network, see files, run commands. However, if I open up cyberduck or other sftp client, I can see the files but anything of any size will time out trying to download or upload. Same thing if I tried to do it with Dreamweaver, for example, it connects fine but times out. If I push something tiny, like the index page, it can sometimes complete. But anything larger, say an image, and it fails.

SSH: Sometimes when I ssh in, if I try to do edits with pico or something similar, it will say "Broken Pipe" and stop. 

Is there something obvious I'm missing here? I really hope so. Any ideas would be really appreciated.

---

### Post by Lars Noodén on 2014-07-24
Have you tried setting ServerAliveInterval and ServerAliveCountMax in ~/.ssh/config for that host?  (Or the corresponding ClientAliveCountMax and ClientAliveInterval in /etc/ssh/sshd_config on the server?)

```

ServerAliveCountMax	5
ServerAliveInterval	20

```

However, since Plex is also affected the problem might be elsewhere, maybe with networking.

---

### Post by cswartzv6 on 2014-07-24
Hello Again,

Thank you for your input. I'm not completely sure if that fixed my issue or if running the updates did, to be completely honest. But at the moment it seems to be working pretty well. Thanks!

---

### Post by TheFu on 2014-07-25
Sounds like an ISP or modem issue.  If you are on cable coax, perhaps it is time to get the cable company to run a new, larger, deeper line?  Mine gets flaky every 5 yrs or so. It takes a tech to convince Comcast the issue is on their side, but they drop a new cable and everything gets faster and more stable again.

---

