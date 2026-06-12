---
title: "URGENT: Server being hit w/ dictionary attack"
date: 2010-10-01
forum: Security
---

### Post by hamilton.jason on 2010-10-01
i setup a ubuntu server 10.04.1 2 weeks ago and i am basically just using it for FTP and as a SAMBA share drive. I have SSH enabled on it. Ive been trying to set it up for VPN, still failing at that, but i was checking the logs today and i found thousands of failed attempts to log in. What i want to do is block all non US ip addresses from hitting my server and also i wanted to set it up so that after x amount of tries to SSH, ip address will be blocked. Any assistance. Time is of the essense. I am currently still under attack. 

```

Sep 29 10:35:25 homeserver sshd[14796]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0$
Sep 29 10:35:28 homeserver sshd[14796]: Failed password for invalid user deploy from 123.55.197.9 port 289$
Sep 29 10:35:31 homeserver sshd[14798]: Invalid user deploy from 123.55.197.9
Sep 29 10:35:31 homeserver sshd[14798]: pam_unix(sshd:auth): check pass; user unknown
Sep 29 10:35:31 homeserver sshd[14798]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0$
Sep 29 10:35:33 homeserver sshd[14798]: Failed password for invalid user deploy from 123.55.197.9 port 440$
Sep 29 10:35:35 homeserver sshd[14800]: Invalid user mongrel from 123.55.197.9
Sep 29 10:35:35 homeserver sshd[14800]: pam_unix(sshd:auth): check pass; user unknown
Sep 29 10:35:35 homeserver sshd[14800]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0$
Sep 29 10:35:38 homeserver sshd[14800]: Failed password for invalid user mongrel from 123.55.197.9 port 31$
Sep 29 10:35:40 homeserver sshd[14802]: Invalid user mongrel from 123.55.197.9
Sep 29 10:35:40 homeserver sshd[14802]: pam_unix(sshd:auth): check pass; user unknown
Sep 29 10:35:40 homeserver sshd[14802]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0$
Sep 29 10:35:42 homeserver sshd[14802]: Failed password for invalid user mongrel from 123.55.197.9 port 54$
Sep 29 10:35:45 homeserver sshd[14804]: Invalid user mongrel from 123.55.197.9
Sep 29 10:35:45 homeserver sshd[14804]: pam_unix(sshd:auth): check pass; user unknown
Sep 29 10:35:45 homeserver sshd[14804]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0$
Sep 29 10:35:47 homeserver sshd[14804]: Failed password for invalid user mongrel from 123.55.197.9 port 55$


```

---

### Post by SlugSlug on 2010-10-01
sudo apt-get install denyhosts

you can also change from the default port 22, that would reduce attempts

---

### Post by coffee412 on 2010-10-01
I would suggest two things to stop this stuff:

1. Change the port that ssh runs on. You can do this by editing the config file for ssh. Most bad people scan for port 22 which is the default port for ssh.

2. Install and configure either Deny-hosts or fail-to-ban. I have deny-hosts installed on my server and it blacklists ips after 3 bad attempts to connect.

Of course, If your the only one that should be using ssh to connect you can only allow your ipaddress if its static or maybe just a range of dynamic addresses.

:)

---

### Post by hamilton.jason on 2010-10-01
Ok i went and installed denyhosts and i did a quick look through. Through the config file it looks like by default it will block the ip address after 5 failed attempts. I am ok w/ that. I would just allow my ip address but i access my server from work and from phone which are both dynamically assigned. I will see how that works out. To change the port # that it uses i would have to change the UFW settings and the config file for SSH while also changing the port forwarding on my router. I will think about it. Thank you for the fast reply guys.

---

### Post by hamilton.jason on 2010-10-01
One last thing, is there some sort of program or access list that can be implemented to block access from all ip addresses out of country? Seems like all of the ip addresses hitting me are from Asia.

---

### Post by coffee412 on 2010-10-01
> **hamilton.jason said:**
> One last thing, is there some sort of program or access list that can be implemented to block access from all ip addresses out of country? Seems like all of the ip addresses hitting me are from Asia.

sure, Just block them in your firewall. If you dont have it you might install the gnome firewall program. I think its called Gufw. Then I think you can block a whole range of ips. Something like 93.0.0.0  I think you would just use the first number in the ip address like the example I gave.

Here is a handy intro to using it:

[http://www.ubuntugeek.com/gufw-simple-gui-for-ufw-uncomplicated-firewall.html](http://www.ubuntugeek.com/gufw-simple-gui-for-ufw-uncomplicated-firewall.html)

---

### Post by hamilton.jason on 2010-10-01
well im doing it on my server in cl so i have to use UFW. The problem w/ doing it by ip address is that there are so many blocks. I really just want to block all ip blocks that source from outside of the US. anyone have any kind of script or something that will do it. i am not a wiz at linux by any stretch so i like simple.

---

### Post by SlugSlug on 2010-10-01
> **hamilton.jason said:**
> well im doing it on my server in cl so i have to use UFW. The problem w/ doing it by ip address is that there are so many blocks. I really just want to block all ip blocks that source from outside of the US. anyone have any kind of script or something that will do it. i am not a wiz at linux by any stretch so i like simple.

am sure you'll be fine with denyhosts

you can also let it sync to its servers to download loads of IP's that have been blocked from her servers.. but I find that over kill

A 3strike lock out is enough for me :)

---

### Post by hamilton.jason on 2010-10-01
Alrighty, well ill keep an eye on it and see if i notice any more attacks. Thank you guys. Marking thread as solved.

---

### Post by bodhi.zazen on 2010-10-01
See also : 

[http://bodhizazen.net/Tutorials/ssh_security](http://bodhizazen.net/Tutorials/ssh_security)

---

### Post by Jive Turkey on 2010-10-01
There is also a program called moblock (i think) that lets you use block lists from the p2p community.  There are some downloadable IP lists categorized by country, industry, and various other types.
You can find a bunch of IP lists here: [http://iblocklist.com/lists.php](http://iblocklist.com/lists.php)

---

### Post by SeijiSensei on 2010-10-01
If you use shared-key authorization, you can configure sshd to refuse root logins and block password authentication.  Then only you could log in, though only from devices where your keys are available.  Even without shared keys, denying root logins is a good idea.  Log into a user account on the remote box and use su or sudo to run root-level commands.

You can also rate-limit connections to a daemon by "wrapping" it with xinetd, though it's probably easier to use iptables for this if you're comfortable with writing rules.

Blocking by IP address is not an easy task.  Addresses are not well-distributed across countries so most country lists have "holes" in them.  If you want to continue down this path, take a look at [http://www.countryipblocks.net/](http://www.countryipblocks.net/).

---

