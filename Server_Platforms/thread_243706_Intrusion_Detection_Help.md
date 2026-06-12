---
title: "Intrusion Detection Help"
date: 2006-08-25
forum: Server Platforms
---

### Post by bunnynuts on 2006-08-25
I'm very new to Linux/Ubuntu, but have enjoyed the experience.  I'm currently running an openvpn server, a samba server, openssh, and plan on setting up a webserver using apache and gallery.  I'm working straight from command line and would like to know what applications could I use to detect people attempting to get into my server? Additionally, what logs should I monitor and what should I look for within those logs? Also, what are the classic signs/symptoms of a hacked machine? Finally, any other suggestions that you may have on the topic would really be appreciated.

Thanks for your time

---

### Post by Woei on 2006-08-25
> **bunnynuts said:**
> I'm very new to Linux/Ubuntu, but have enjoyed the experience.  I'm currently running an openvpn server, a samba server, openssh, and plan on setting up a webserver using apache and gallery.  I'm working straight from command line and would like to know what applications could I use to detect people attempting to get into my server? Additionally, what logs should I monitor and what should I look for within those logs? Also, what are the classic signs/symptoms of a hacked machine? Finally, any other suggestions that you may have on the topic would really be appreciated.


Well, the general idea is to only enable those services you absolutely *have* to enable for your users or applications, and secondly, only to those people that should be allowed to use them. However, if it's really a public system, then you'll probably want to install some extra software to help mitigate the risk.

First of all, there's the rootkit detector 'rkhunter', available in the Universe repository. You should run this program regularly to detect rootkits early. Secondly, there are so called 'Intrusion Detection' systems which md5sum your configuration files and store your directory contents, and immediately warn you (through e-mail or wall messages) when anything changes. The trick is configuring such IDS's in a way that you're not getting too much false positives, but still catch the bad guys if they do manage to exploit a loophole. The two best known IDS's are Snort and Tripwire, also available in the Universe repository.

Then there's the question of your logfiles. SSH logins are usually logged in /var/log/auth. Webtraffic in your http server's logfiles, which can reside anywhere depending on how you configure your webserver. Checking these files manually is a chore and usually not possible, as there are so many hacked systems on the net running bots that are continually scanning and poking SSH and webports that the signal to noise ratio in your logfiles becomes too low. To prevent SSH dictionary attacks, consider only allowing certain users and only allowing logins through [public/private keys](http://kimmo.suominen.com/docs/ssh/) and disabling password authentication completely. Moreover, you should install the excellent [DenyHosts](http://denyhosts.sourceforge.net/) (not in the repositories ?!) daemon. This will scan your /var/log/auth file and block IP's or IP ranges for a specific or all services through the /etc/hosts.{allow|deny} file provided by the standard TCPWrappers.

Lastly, keep up to date with security updates. Especially open source PHP scripts like 'Galleries' are vulnerable, as the source can be readily inspected for flaws that can allow XSS attacks, SQL injection attacks or worse. Allowing your users to install PHP scripts without being accounted for running outdated versions of their PHP programs is a big no-no without extra security in the form of chroot jails, Apache suExec or mandatory access control systems like SELinux, which are rather hard to configure correctly.

This should get you started. Do read up, do harden your systems, do take security seriously. There are already far too many bots and insecure systems on the net, administered poorly by careless operators.

---

