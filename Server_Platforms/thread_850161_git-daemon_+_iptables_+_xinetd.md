---
title: "git-daemon + iptables + xinetd"
date: 2008-07-05
forum: Server Platforms
---

### Post by pmaciver on 2008-07-05
What I want: To set git repos on my server
What I am using: xinetd, so that when people try and connect it gives them the git service
My problem: I am using iptables to block everything except port 80 (webserver), (2899 my alternate ssh server port) and now 9418 (which is what I thought that git uses).

This is what my git-daemon file under /etc/xinet.d/ looks like

# default: off
# description: The git server offers access to git repositories
service git
{
  disable = no
  type            = UNLISTED
  port            = 9418
  socket_type     = stream
  wait            = no
  user            = nobody
  server          = /usr/local/bin/git-daemon
  server_args     = --inetd --export-all --base-path=/var/www
  log_on_failure  += USERID
}


But whenever I try and connect to my server I look in my logs and see that iptables is blocking a connection trying to be made on port 32767

I am not quite sure why this is. All I want is to open up my firewall enough so that I can pull and push stuff to my git repos on my server. 

Any help appreciated.

---

### Post by afischer.aea on 2011-06-15
Wow this is an old thread, but hopfully someone sees this.

I have been trying something similar, and I think my problem lies in how i'm writing my /etc/xinetd.d/git-daemon file.  can someone post their configueration? I'd like to compare it to mine.

---

