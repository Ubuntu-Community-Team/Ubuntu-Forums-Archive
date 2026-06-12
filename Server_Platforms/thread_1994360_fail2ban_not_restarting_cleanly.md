---
title: "fail2ban not restarting cleanly"
date: 2012-06-02
forum: Server Platforms
---

### Post by lackhead on 2012-06-02
Hey all-

   I have spent more time than I care to admit tracking down an issue with fail2ban. I've reduced it to what I hope is a simple case:

1 ) install 12.04 server from CD
2 ) aptitude -r install fail2ban
3 ) trigger an ssh login with wrong password
4 ) verify fail2ban picks this up with "fail2ban-client status ssh"
5 ) /etc/init.d/fail2ban stop
6 ) /etc/init.d/fail2ban start
7 ) again, trigger an ssh login with wrong password
8 ) "fail2ban-client status ssh" will now show nothing but 0s, and won't pick up any new log entries in /var/log/auth.log

Sometimes I have had to restart fail2ban twice before this problem kicks in, but once it does, I am not able to return functionality to fail2ban without a reboot.  I have tried:

1 ) /etc/init/d/fail2ban stop
2 ) restart syslog
3 ) restart ssh
4 ) flush everything from iptables
5 ) verify fail2ban socket file doesn't exist
6 ) /etc/init.d/fail2ban start

And still fail2ban will refuse to notice any new log entries to auth.log.  A reboot of the box, however, will restore functionality (until you restart fail2ban, which breaks everything again). 

Any ideas?  Anybody else running into this issue?  Seems kinda scary to have fail2ban just sitting there, apparently up and functional but silently ignoring your logs. 


         -c

---

### Post by kevinthecomputerguy on 2012-06-03
Is everything still port 22?

If you have changed your ssh port i could see that happening.

Also try commenting out all your other jails beside ssh, to see if one of the other jails cant be reloaded or something.

---

### Post by lackhead on 2012-06-07
ssh is the only jail enabled. :(

Note this is using the plain-jane default 12.04 server, built off the CD with *no* modifications other than an "aptitude install fail2ban".

---

### Post by jbuhrmann on 2012-06-27
I'm running into the exact same problem. I installed 12.04LTS from an OpenVZ template on a Proxmox host and had this problem. Then I just tried it on a clean install of 12.04 as the only OS with no virtualization and it does the same thing. I just installed it on another 8.04 server using apt-get and it installs fail2ban v0.8.2 and that works fine. Thinking about hand compiling an older version of fail2ban to see if that works.    Also wanted to note that it works properly after rebooting the server, but as soon as you stop the fail2ban service it won't work right again.  Ok - I loaded v0.8.4 from source instead of the v0.8.6 from apt. Same results. Seems like it can't hook the auth file after restart.

---

