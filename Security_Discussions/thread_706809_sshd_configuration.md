---
title: "sshd configuration"
date: 2008-02-24
forum: Security Discussions
---

### Post by donkyhotay on 2008-02-24
I run a small headless server on my personal network that I use for routing and printing. I used to admin my server from my desktop using ssh and blocked all ssh access from the internet. I now need to do some coding on my server remotely from the internet so I created a new user account without sudo access, configured sshd to only allow access on this new user account and opened up ssh access from the internet. For the times I need to admin my server I use my KVM to switch to it directly but this is inconvenient and would prefer to use ssh. What I want to know is if there is a way to allow me to ssh into my admin accounts from my internal network while only allowing ssh access to non-admin accounts from the internet. I've read through the online manuals of sshd_config located here [http://www.openbsd.org/cgi-bin/man.cgi?query=sshd_config](http://www.openbsd.org/cgi-bin/man.cgi?query=sshd_config) and I can't find anything that would help me to do this. One idea I had was to run 2 different instances of sshd on 2 different ports and allow admin accounts on one and disallow admin accounts on the second that by blocking those ports I should remain relatively secure. Does anyone out there have any ideas or suggestions for me on this?

---

### Post by HermanAB on 2008-02-24
Hmm, I think you are going about it all wrong.  By itself SSH is secure.  Insecurities are introduced by how you use it.  

The way to keep it secure is to use public keys or very very long passwords.  To discourage script kiddies, run SSH on a non-standard port and use a rate limiting rule in iptables.

If you always connect from a specific place, then  you could also limit connections to that specific IP address with iptables.

Hope that helps!

Herman

---

### Post by tubezninja on 2008-02-24
You could also use [DenyHosts]("http://packages.ubuntu.com/edgy/net/denyhosts") to help guard against script kiddies or bots running dictionary attacks.

---

### Post by bodhi.zazen on 2008-02-25
[http://www.cromwell-intl.com/unix/ssh.html#part1_5](http://www.cromwell-intl.com/unix/ssh.html#part1_5)

That section reviews what you are asking, both in hosts.allow and in sshd_config

---

### Post by The Cog on 2008-02-25
AllowUsers in sshd_config allows a list of username@address which should do what you want. man sshd_config describes AllowUsers and man ssh_config describes the format of the list.

---

### Post by brabo on 2008-02-27
you could also specify to use ssh 2 in /etc/ssh/sshd_config.
uncomment line #Protocol 2
it is said to be more secure.

grtz,
brabo.

---

