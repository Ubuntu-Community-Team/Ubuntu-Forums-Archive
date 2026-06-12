---
title: "SSH Banner Question"
date: 2008-11-12
forum: Security
---

### Post by rmccarri on 2008-11-12
Hi,
I have two Ubuntu systems which I recently upgraded to version 8.10, one with the server edition installed and one with a desktop install.  Both are running as LAMP servers with OpenSSH access.  I recently established an SSH connection on my desktop machine and noticed the following in the banner:

[I]  System information as of Wed Nov 12 09:40:01 EST 2008

  System load:  0.0                 Swap usage:  0%     Users logged in: 1
  Usage of /:   29.5% of 223.53GB   Temperature: 40 C
  Memory usage: 29%                 Processes:   140

  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)[/I]

My server installation does not have this.  I'm a little paranoid as my web site on the desktop install had recently been hacked and I reinstalled everything to ensure that there hadn't been anything left behind in the hack.  Is this something that might have been automatically installed as part of the desktop platform and not the server platform, or is it possible that someone has tried to install a package to monitor my system remotely?

---

### Post by puppywhacker on 2008-11-12
SHORT: All is well :)

LONG: it is the MOTD, message of the day message which is comes from /etc/motd (a softlink of /var/run/motd )
which is updated every 10 minutes by a cronjob
/etc/cron.d/update-motd
which executes 
/usr/sbin/update-motd

/etc/ssh/sshd_config you could uncomment Banner so that it uses a static /etc/issue.net instead.

and totally unrelated, I use fail2ban to temporary block ip-addresses that try passwords more than 3 times. it makes brute-force attacks a bit more difficult.

---

### Post by rmccarri on 2008-11-12
Thanks for the detailed explanation.  I was pretty weirded out as I had never seen anything like it in my previous installs.

---

