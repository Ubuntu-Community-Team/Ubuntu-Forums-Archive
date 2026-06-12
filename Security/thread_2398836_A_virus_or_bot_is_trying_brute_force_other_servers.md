---
title: "A virus or bot is trying brute force other servers"
date: 2018-08-17
forum: Security
---

### Post by richeerichhh on 2018-08-17
Hey guys I keep getting these abuse emails from my ISP. They've already disabled my internet once, and I've convinced them I would find the problem. The only culprit is my ubuntuserver running 16.04. I've tried disabling every user but my main from accessing ssh, using IPTables to block traffic and still the same thing. Which logs can I check, that can help me identify the process or culprit? 

here is a quote from the email complaint. As you can see, a computer from my IP address 184.181.XXX.XXX (my ubuntu server) is using SSH against my permission to brute for another server.
[FONT=arial] Note: Local timez[/FONT][FONT=arial]one is +0300 (E[/FONT][FONT=arial]EST)[/FONT]
[FONT=arial]> Aug 17 21:49:41 mgw2 sshd[27945]: Invalid user odoo from 184.181.XXX.XXX[/FONT]
[FONT=arial]> Aug 17 21:49:41 mgw2 sshd[27945]: pam_unix(sshd:auth): au[/FONT][FONT=arial]thentication fa[/FONT][FONT=arial]ilure; logname= uid=0 euid=0 tty=ssh ruser= rhost=[/FONT][ip184-181-XXX.XXX.oc.oc.cox.net]("http://ip184-181-118-130.oc.oc.cox.net/")
[FONT=arial]> Aug 17 21[/FONT][FONT=arial]:49:43 mgw2 ssh[/FONT][FONT=arial]d[27945]: Failed password for invalid user odoo from 184.181.[/FONT][FONT=arial]XXX.XXX[/FONT][FONT=arial] port 36256 ssh2[/FONT]
[FONT=arial]> Aug 17 21:49:43 mgw2 sshd[27945]: Connection closed by 184.181.[/FONT][FONT=arial]XXX.XXX[/FONT][FONT=arial] [preauth][/FONT]
[FONT=arial]> Aug 17 21:52:03 mgw2 sshd[29644]: Invalid user odoo from 184.181.[/FONT][FONT=arial]XXX.XXX[/FONT]
[FONT=arial]> Aug 17 21:52:03 mgw2 sshd[29644]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=[/FONT][ip184-181-XXX.XXX.oc.oc.cox.net]("http://ip184-181-118-130.oc.oc.cox.net/")
[FONT=arial]> A[/FONT][FONT=arial]ug 17 21:52:05 [/FONT][FONT=arial]mgw2 sshd[29644]: Failed password for invalid user odoo from 184.18[/FONT][FONT=arial]1.XXX.XXX port [/FONT][FONT=arial]39012 ssh2[/FONT]
[FONT=arial]> Aug 17 21:52:05 mgw2 sshd[29644]: Connection [/FONT][FONT=arial]closed by 184.1[/FONT][FONT=arial]81.[/FONT][FONT=arial]XXX.XXX[/FONT][FONT=arial] [preauth][/FONT]
[FONT=arial]> Aug 17 21:52:30 mgw2 sshd[29916]: Invalid user odoo from 184.181.[/FONT][FONT=arial]XXX.XXX[/FONT]
[FONT=arial]> Aug 17 21:52:30 mgw2 sshd[29916]: pam_uni[/FONT][FONT=arial]x(sshd:auth): a[/FONT][FONT=arial]uthentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=[/FONT][ip184-181-XXX.XXX.oc.oc.cox.net]("http://ip184-181-118-130.oc.oc.cox.net/")
[FONT=arial]> Aug 17 21:52:32 mgw2 sshd[29916]: Failed password for invalid user odoo from 184.181.[/FONT][FONT=arial]XXX.XXX[/FONT][FONT=arial] port 37828 ssh2[/FONT]

---

### Post by TheFu on 2018-08-17
If you are still seeing 184.181.XXX.XXX in the logs, then you haven't got the firewall correct. If that is your public IP, then you or some automatic jobs are causing it.  Stop it.

Why not just block that subnet in the router if it isn't your public IP/subnet?

[http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures)
The easy things to do for securing ssh are:
* Install fail2ban - the defaults are reasonable, but you might want to block for a day at a time after you are sure everything else is correct.  I think the default ban is 1 hour.
* Don't use the default ssh port (22/tcp) on the internet
* Never allow remote root over ssh on the internet.  You can allow it on the LAN, with ssh-keys, never passwords
* Never allow password-based authentication over the internet. Force ssh-keys or ssh-certs to be used.

Or did I misread the problem? Is it your server or someone elses?  If it is someone else's, use netstat and lsof to figure out which process is running ssh to connect externally.

---

### Post by richeerichhh on 2018-08-17
> **TheFu said:**
> Or did I misread the problem? Is it your server or someone elses?  If it is someone else's, use netstat and lsof to figure out which process is running ssh to connect externally.
Whoops! The logs are from the email that my ISP send me, the IP Address is mine, which is why I blocked it out, even though it's not too hard to find, but a program or bot from my IP Address on my ubuntu server is brute forcing a random server.

---

### Post by richeerichhh on 2018-08-18
okay I did a lsof command and found something really sketchy.

COMMAND    PID       USER   FD   TYPE   DEVICE SIZE/OFF NODE NAME
/usr/bin/ 1489 shuttleboy   32u  IPv6    21707      0t0  UDP [fe80::1e6f:65ff:fec0:9584]:6771 
/usr/bin/ 1489 shuttleboy   33u  IPv6    21708      0t0  UDP [fe80::1e6f:65ff:fec0:9584]:44775 
/usr/bin/ 1489 shuttleboy   76u  IPv4 29971999      0t0  TCP 192.168.1.115:59747->94x158x10x38.dynamic.irkutsk.ertelecom.ru:64397 (SYN_SENT) <------- what is that???

---

### Post by The Cog on 2018-08-18
That really sketchy stuff looks like the culprit to me. I don't understand the command /usr/bin/ - maybe it's patched lsof to hide the name of the executable? 
I suggest you should back up your data and do a full re-install. I don't think you can trust that system any more.
SYN_SENT is a TCP state that says it has sent a SYN packet (a connect request) but not received a response yet (to somehwere in Russia).

---

### Post by TheFu on 2018-08-18
Nuke it from orbit. Only way to be sure.

Would be nice if you had a few months of versioned backups so you could see when the cracker got in and where they've put their tools.  Ensure you can have a few months of daily, versioned backups on the next build-out.

If you are allowing any services, learn how to secure them, BEFORE you put this machine back on the internet. For example, if you don't explicitly need and use IPv6, disable it and block all IPv6 traffic on your network.  

I'd also assume all other machines on the same subnet are cracked too. Check them for suspicious behavior. Be ready to nuke a few others.

I still remember the first time my computer (only had 1 at the time) got cracked.  Taught me much, it did.

---

