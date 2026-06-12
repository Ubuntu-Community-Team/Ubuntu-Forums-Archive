---
title: "Ubuntu webserver lockdown - remove unwanted services help."
date: 2013-02-06
forum: Server Platforms
---

### Post by Coder68 on 2013-02-06
This is what I have done to lock down my Ubuntu webserver running several sites and will have a mail server that connects only to our DMZ mail server to send emails to us:

1. I have instaled 12.04 LTS and all updates.
2. Set it to auto install security updates
3. Set a cron job to reboot nightly
4. Installed Apache2 + all updates
5. Installed and configured ModSecurity + latest OWASP rules
6. Installed PHP + Suhosin + configured
7. Removed all test/debugging scripts
8. Turned off server status page
9. Turned off Apache banner/HTTP trace info
10. **Anything I missed?????**

I have two things left to do, to the best of my knowledge.
1. Install sendmail (DMZ to DMZ email server only) + lockdown
2. **Turn off unnecessary services.** 

I have the list of running services and marked what I "know" to keep in green, and what I know to turn off in red.  The rest are totally unknown to me. Goggling around has not give me any yes/no answers...just what the do, but that has not been a lot of help at this point. Several more of these I want to make green... but I want to talk to the experts first. :D This is my first web server build that will actually sit in a DMZ!

*Can anyone please help?*

Results of:** sudo initctl list | grep running**

 rsyslog start/running, process 819
  tty4 start/running, process 882
  udev start/running, process 344
  upstart-udev-bridge start/running, process 342
  [COLOR=red]whoopsie start/running, process 945[/COLOR]
  apport start/running
  irqbalance start/running, process 932
  tty5 start/running, process 887
  atd start/running, process 906
  dbus start/running, process 821
  [COLOR=#00B050]resolvconf start/running[/COLOR]
  [COLOR=#00B050]ssh start/running, process 808[/COLOR]
  [COLOR=#00B050]cron start/running, process 905[/COLOR]
  [COLOR=#00B050]acpid start/running, process 904[/COLOR]
  [COLOR=#00B050]ufw start/running[/COLOR]
  upstart-socket-bridge start/running, process 522
  tty2 start/running, process 894
  tty3 start/running, process 895
  network-interface (lo) start/running
  [COLOR=#00B050]network-interface (eth0) start/running[/COLOR]
  tty1 start/running, process 981
  network-interface-security (network-interface/eth0) start/running
  network-interface-security (network-interface/lo) start/running
  network-interface-security (networking) start/running
  tty6 start/running, process 897

*What is the best way to turn off the unwanted services?*

*What is the best way to prevent a hacker from being able to log in as one of the must have services? (Set shell to false???)*
  
Thank you,

Coder68

---

### Post by SeijiSensei on 2013-02-06
You are running a firewall, right?  Just have the default INPUT rule be DENY and only allow access to the ports you need.  If you use SSH to manage it, include rules that allow connections from the specific IP addresses you use, and block anyone else. 

It's a lot easier to firewall off the machine than it is to start trying to pick and choose among services.

My servers rarely expose more than SMTP, POP3/IMAP4, HTTP, and HTTPS.  I use SSH from designated addresses or over an OpenVPN tunnel.  The last time I had a successful intrusion was over a decade ago when I failed to update Apache when a security flaw was revealed.  Even then all that happened was that someone installed an IRC forwarder so they attack somebody else they didn't like.

You're much more at risk from flaws in web services like cross-site scripting attacks.  Common applications like WordPress are a standard target.

---

### Post by Coder68 on 2013-02-06
The DMZ firewall will limit access to just port (80), and for good measure I turned on the Ubuntu firewall and only opened port 80 and 22. SSH is only allowed between an internal box and the server, started by the internal computer.

I agree it is easier to just rely on the firewall, but I would like to minimize the risk even further by turning off any services that might be used to further exploit the box if a flaw in the web server was exploited. If needed, they might be able to use one of these services to escalate privileges. This is also the reason I want to disable log on shells for these services. 

> You're much more at risk from flaws in web services like cross-site  scripting attacks.  Common applications like WordPress are a standard  target.
Exactly why I installed Suhosin, modesecurity and the OWASP rules.  :)

Thank you,

C68

---

### Post by SeijiSensei on 2013-02-06
I'll just warn you that modsecurity can generate false positives or interpret certain legitimate events as dangerous.  I've had to turn it off on a couple of sites because it interfered with normal operations.  It's been a while since I had to do this, so I can't recall the precise circumstances, but when I searched Google for problems with the module I discovered I was not alone.

---

### Post by Coder68 on 2013-02-07
Good to know. Our sites are really simple mostly static PHP pages, but there is one page that lets you fill in a form and on submission, it emails it to us. 

Anyone on the services or users question?

Thank you,

C68

---

