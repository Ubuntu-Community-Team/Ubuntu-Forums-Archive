---
title: "What to install/disable for running a simple server?"
date: 2008-01-30
forum: Server Platforms
---

### Post by Jengu on 2008-01-30
I want to setup an old box to just run a git server. It'll be running on a semi-stable IP (changes every few days) so I've written a python script to periodically send an e-mail with the current IP to a gmail account that I can check to find out the IP. These are the only 2 things that the box will do. Let people login and commit git changes and checkout and such, and send its IP by e-mail periodically.

For best security, is there anything I should install/disable after a default server install? I've never really run a server before, but security is important. Is there, for example, a way to set Ubuntu to automatically download and install security updates without my intervention? (say, in case I'm sleeping). Do I need a firewall?

---

### Post by foxylad on 2008-01-30
I'd install the LAMP server version (no X windows etc) and then remove PHP, Apache and MySQL. Then install ssh and harden it security-wise (see sticky posts in this forum). You also need to get your head around apt-get or aptitude, both of which you can automate to run regulalry with cron.

I use iptables as my firewall, again you need to research it to find out exactly how to deny anything but the services you want to provide. You can also use this to stop dictionary attacks on ssh, by only allowing 3 connection attempts in five minutes - google for how to do this.

---

