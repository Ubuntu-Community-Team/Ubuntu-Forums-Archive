---
title: "Which of this tasks are safe to stop [Ubuntu Server 14.04]"
date: 2014-12-26
forum: Server Platforms
---

### Post by cfernanrodri on 2014-12-26
Hello, I run Ubuntu 14.04 in an android-tv device. Resources are limited to 1core and 512m RAM.

I would like to know which of this tasks are free to **stop and delete** and _how?_ I only use the devide as FTP, and in the future LAMP, so I would like to remove any kind of extra processes.

Thank you

[IMG]http://i.imgur.com/5XFAUpl.png[/IMG]

---

### Post by TheFu on 2014-12-27
First, stop using plain FTP. sftp should be used instead and is included with ssh. scp is also included with ssh. Just add fail2ban or denyhosts if the ssh is available over the internet. Also, disable password - only use ssh-keys for authentication.

pptpd is a vpn and not really secure.  Use ssh.

That's it from that list. Not much there.

512M is plenty provided there isn't much GUI.  I have Ubuntu servers running on 384M of RAM just fine without any swap.

Unused RAM is used by the OS for disk buffers as needed. This is good and expected.

---

