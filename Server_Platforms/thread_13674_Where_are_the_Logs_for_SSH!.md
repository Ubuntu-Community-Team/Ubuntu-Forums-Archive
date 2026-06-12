---
title: "Where are the Logs for SSH?!"
date: 2005-02-02
forum: Server Platforms
---

### Post by ming0 on 2005-02-02
I can't find my SSH logs? I checked in /var/log/, and didn't find them?

Anyone know where to look (or how to enable thum)?

If the logs aren't on by default, I really think they should be.

---

### Post by mendicant on 2005-02-02
What kind of logs are you looking for?  For some information about who's been logging in, check out auth.log.

---

### Post by mendicant on 2005-02-02
Oh, and for the last few people to log in, use the command:

% last

and:

% man wtmp

---

### Post by ming0 on 2005-02-02
Cool thanks :) 

I have another question:

I sometimes like to use ssh as a fileserver for friends, and for remote admin stuff. I generally leave port 22 forwarded from my little cable router to my ubuntu pc and leave the ssh service running. I keep my system up to date w/ synaptic, and don't have remote root enabled...

Is this generally safe to do? Just cruising the logs, I see some break-in attempts and stuff--my username isn't too common, so I assume I'll be safe, but I figure it's good to get a second opinion.

```
Feb  1 05:54:33 localhost sshd[7363]: reverse mapping checking getaddrinfo for h216-203-70-47.seed.net.tw failed - POSSIBLE BREAKIN ATTEMPT!
Feb  1 05:54:35 localhost sshd[7367]: reverse mapping checking getaddrinfo for h216-203-70-47.seed.net.tw failed - POSSIBLE BREAKIN ATTEMPT!
Feb  1 05:54:35 localhost sshd[7373]: reverse mapping checking getaddrinfo for h216-203-70-47.seed.net.tw failed - POSSIBLE BREAKIN ATTEMPT!
Feb  1 05:54:35 localhost sshd[7373]: User lp not allowed because not listed in AllowUsers
Feb  1 05:54:40 localhost sshd[7377]: Illegal user maria from ::ffff:203.70.47.216

```
thanks!

---

### Post by mendicant on 2005-02-02
You have a number of options:
1. Use a firewall to only allow incoming ssh connections from certain (known) places.  This is a very good idea for anybody that is a sudoer.
2. Only allow ssh keys to be used, not passwords
   a) restrict these keys to only be able to do certain things (like sftp), make home directory read-only and use a separate, writeable work area
3. Make your password using a very large search space. Using lower and upper case letters, numbers and standard symbols ([http://www.unicode.org/charts/PDF/U0000.pdf](http://www.unicode.org/charts/PDF/U0000.pdf)) gives an attacker at least 92 choices per character in your password. Use a longish password--10^92 makes for a big search space to brute force.

---

