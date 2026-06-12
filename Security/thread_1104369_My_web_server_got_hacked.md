---
title: "My web server got hacked"
date: 2009-03-23
forum: Security
---

### Post by Johnsie on 2009-03-23
I had my shell port open and someone ran a dictionary attack against it. The last two lines show when the hack took place. Does anyone know any good ways to stop this from occuring but still alow me to access my computer remotely? In the meantime I have disconnected the machine from the Internet.

---

### Post by Dr Small on 2009-03-23
You can use iptables to slow down connections:
```
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit -burst 5 -j ACCEPT
```

And, install Denyhosts. But those last two lines do not mean that your system has been compromised, as the session for root has been opened by CRON (cron:session). That means, the bruteforce attempt failed.

Dr Small

---

### Post by bodhi.zazen on 2009-03-23
Those lines are normal, it is a cron job.

In terms of preventing an attack, take a look here :

[AdvancedOpenSSH - Community Ubuntu Documentation]("https://help.ubuntu.com/community/AdvancedOpenSSH") 

And then use either a 1 liner in iptables or something like denyhosts or fail2ban.

Edit: What Dr Small said :twisted: .

---

### Post by Johnsie on 2009-03-23
Ok, but my welcome message when I logged on said the last user to login was from an ip address that I didnt recognise. I only access my server from home and work. The isp for this other ip address was not one that I use.

---

### Post by bodhi.zazen on 2009-03-23
Well, can you post the message ?

---

### Post by Dr Small on 2009-03-23
Was it the same IP address as was mentioned in the log?

---

### Post by Velnias on 2009-03-23
It's easy, but be carefull!
"8.If possible, consider RSA Authentication instead of interactive password logins. If you're in a scenario where it's prudent to use public keys for authentication rather than password-based logins, you might consider it. Crpytographically, RSA key authentication is more secure than even very strong passwords, and can make the connection phase of SSH much more VPN-like in nature. There are advantages and disadvantes to this method however. The primary advantages are convenience, added cryptographic durability, and the ability to prevent brute-force attacks to an extremely high degree. Note, however, that this form of authentication is only truly effective as a brute-force deterrent if all other forms of interactive authentication are disabled."

[http://anti-trend.homelinux.org/index.php?option=com_content&task=view&id=52&Itemid=46]("http://anti-trend.homelinux.org/index.php?option=com_content&task=view&id=52&Itemid=46")

---

### Post by HermanAB on 2009-03-24
Re-install your system and this time, use a proper password.

Cheers,

Herman

---

### Post by bodhi.zazen on 2009-03-24
> **HermanAB said:**
> Re-install your system and this time, use a proper password.

Cheers,

Herman

Normally I agree with this advice, but I would like to be sure before advising this as the OP may or may not be reading errors properly.

But yes, if you were compromised, IMO you need to re-install and restore data from a known good backup.

---

### Post by shad0w_crash on 2009-03-25
Configure a firewall (like firewalker).

IF access from (yourIP)
 then 22 = open
ELSE
 22 = closed
exit

also if 3 passwords guesses where made block that IP from trying for like 2 hours, the next 3 guesses ban permantly.

If you're afraid he got access run rchunter to find out if he placed a rootkit.

If you're paranoid use ossec (HIDS) and monitor for a while). If you think permanently dammege is done reinstall :)

---

### Post by gregor171 on 2009-03-29
consider changing your 22 port to something else

---

### Post by kustomjs on 2009-03-30
so go get yourself setup for smoothwall.

---

### Post by hyper_ch on 2009-03-30
use a safe password (10+ chars with large & small letters and numbers and preferably also special chars).

then use a iptables rule that blocks after x unsuccessfull tries or install denyhosts or fail2ban which do basically the same.

Port change isn't needed.

If you connect to that computer always from the same (couple of) ip(s) then you might want, as already suggested, to deny all connections not originating from one of those ips.

---

### Post by [pl]ice on 2009-03-30
Dude, 

start reading your logs! if it was dictionary attach, you will have full logs!

  This is common :( I got VPS and ppl are trying like every 20 min for ssh and ftp brute force.

  Yes, you can do many ways, firewall, to block users from trying too much, eg fail2ban or that other one. BEWARE fail2ban and that other program,(can't remember) are not that clever... you can do very simple injection, which will add IPs to block to your firewall, so If I knew you were running fail2ban, I could block your IP (and any other IP) withing minutes :( (Hope they'll fix that soon)
  Have a look at wrapping, its not hard to setup and easy to control, but its just a delay system. Best to block via firewall after eg 3 trials.
 
Good luck man!

---

### Post by Dr Small on 2009-03-30
> **'[pl]ice said:**
> BEWARE fail2ban and that other program,(can't remember) are not that clever... you can do very simple injection, which will add IPs to block to your firewall, so If I knew you were running fail2ban, I could block your IP (and any other IP) withing minutes :( (Hope they'll fix that soon)

Could you please provide a link to this bug/report?

---

### Post by [pl]ice on 2009-03-30
[http://www.ossec.net/en/attacking-loganalysis.html](http://www.ossec.net/en/attacking-loganalysis.html)

have a look at that one, theres more on wiki fail2ban, google rest i have to go to sleep (sorry)
 I guess you can test that using 2 servers / socks if one got script blocking

---

### Post by Dr Small on 2009-03-30
> **'[pl]ice said:**
> [http://www.ossec.net/en/attacking-loganalysis.html](http://www.ossec.net/en/attacking-loganalysis.html)

have a look at that one, theres more on wiki fail2ban, google rest i have to go to sleep (sorry)
 I guess you can test that using 2 servers / socks if one got script blocking
Oww. That does look rather serious. That's basically the same as SQL injection.

---

### Post by albinootje on 2009-03-30
> **'[pl]ice said:**
> [http://www.ossec.net/en/attacking-loganalysis.html](http://www.ossec.net/en/attacking-loganalysis.html)


Thanks for that link, interesting, ..but it also says in the end :
> 
*I want to thank Cyril Jaquier from Fail2ban, Avinash Chopde from BlockHosts and Phil Schwartz from DenyHosts for the prompt reply and willingness to fix those issues. I also want to thank Liliane Cid for helping me writing and reviewing this document.

So.. perhaps it's fixed already ?

And you can use /etc/hosts.allow to prevent blocking yourself.
For example :
```

sshd : 192.168.1.* : allow
sshd : /etc/hosts.deny : deny
sshd : ALL : allow

```
Because of the order /etc/hosts.allow is read you can never lock yourself out from 192.168.1.* in this example.

---

### Post by Fatjoint on 2009-03-30
> **albinootje said:**
> Thanks for that link, interesting, ..but it also says in the end :

So.. perhaps it's fixed already ?

And you can use /etc/hosts.allow to prevent blocking yourself.
For example :
```

sshd : 192.168.1.* : allow
sshd : /etc/hosts.deny : deny
sshd : ALL : allow

```
Because of the order /etc/hosts.allow is read you can never lock yourself out from 192.168.1.* in this example.

I'm under the impression that the exploits documented on that webpage are resolved.  If you check DenyHosts webpage and examine the change log, it looks like the most recent updates were done Dec-2008 which include regex fixes for parsing.

The most important thing however is that while yes, it's possible that someone could DoS you, using this script helps prevent being pwned, and given those choices I'll take the latter.

---

### Post by [pl]ice on 2009-03-30
yes,lots of that stuff got fixed, the latest one is: Fail2ban 'wuftpd.conf' Remote Denial of Service Vulnerability
  The way the main program was designed is not that good; so I'm really worried that there will be more patches...
But then it's working well, the amount of ssh connections dropped is enormous, so I better don't complain :)

---

### Post by bodhi.zazen on 2009-03-30
> **'[pl]ice said:**
> yes,lots of that stuff got fixed, the latest one is: Fail2ban 'wuftpd.conf' Remote Denial of Service Vulnerability
  The way the main program was designed is not that good; so I'm really worried that there will be more patches...
But then it's working well, the amount of ssh connections dropped is enormous, so I better don't complain :)

You can either :

Restrict access by ip address in your sshd config file (/etc/ssh/sshd) or add a few lines to iptables.

If you do those things you will not need denyhosts or fail2ban ;)

---

### Post by Dr Small on 2009-03-31
> **'[pl]ice said:**
> yes,lots of that stuff got fixed, the latest one is: Fail2ban 'wuftpd.conf' Remote Denial of Service Vulnerability
  The way the main program was designed is not that good; so I'm really worried that there will be more patches...
But then it's working well, the amount of ssh connections dropped is enormous, so I better don't complain :)
I set my DENY_THRESHOLD to 1 on DenyHosts, so a user is given 3 attempts (in one connection) to try to log in. If they fail at the end, their IP address gets added to /etc/hosts.deny. I've been getting at least one entry added to host.deny each day. :)

Of course for me, I use SSH keys so I never enter a password, but I opened up PasswordAuthentication just so I can run and test DenyHosts :)

---

