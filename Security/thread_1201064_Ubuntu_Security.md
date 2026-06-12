---
title: "Ubuntu Security"
date: 2009-06-30
forum: Security
---

### Post by aphexcoil on 2009-06-30
Today I was working on SSH and could not get putty to work with the keys. I checked the auth.log in /var/log and noticed it was constantly changing -- tail auth.log
 
Some hacker from China was slamming my computer on port 22 trying to get in. 
 
I use ufw and feel comfortable with it, but what I would like to know is this:
 
1) Is there a program or firewall setting that detects a high amount of failed logins from an IP and temporarily puts up a rule denying all to that IP? I would like to have a 30 minute lockout for say 10 failed attempts. 
 
2) In ufw, what rules take charge when you have conflicting rules: 
 
allow all to port 22
deny from ip xxx.xxx.xxx.xxx
 
Can ip xxx.xxx.xxx.xxx still get to port 22? Is it just how the rules are listed in ufw status numbered?
 
3) I'd like to block all IP's from Asia. Is there a simple way to do this? Is there a list of IP's that originate from Asia that I can add to my configuration? Blocking entire A classes might be helpful if it belongs solely to Asia.
 
Thanks!

---

### Post by 3Miro on 2009-06-30
AFIK the IP location can be faked, so no IPs from China is useless (the hacker might have been somewhere else altogether)

I don't know about setting the firewall, but a simple defense is to change the default SSH port. Move it to a random number that only you will know so no automated script attacking port 22 can ever hope to get trough (port 22 will be closed).

---

### Post by aphexcoil on 2009-06-30
> **3Miro said:**
> AFIK the IP location can be faked, so no IPs from China is useless (the hacker might have been somewhere else altogether)
 
I don't know about setting the firewall, but a simple defense is to change the default SSH port. Move it to a random number that only you will know so no automated script attacking port 22 can ever hope to get trough (port 22 will be closed).
 
Here is a snip from my auth.log:
 

Jun 30 15:51:09 xxxxxxx sshd[3523]: User root not allowed because account is locked
Jun 30 15:51:09 xxxxxxx sshd[3523]: error: Could not get shadow information for NOUSER
Jun 30 15:51:09 xxxxxxx sshd[3523]: Failed password for invalid user root from 124.254.15.169 port 37109 ssh2
Jun 30 15:51:11 xxxxxxx sshd[3525]: Address 124.254.15.169 maps to m6.xue24.net, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
 
 
---------------------------------------------------------------------------------------
 
I didn't know you could fake an IP address.  I would imagine that it would cause serious routing problems from the point of origin once it left the computer.  I thought you could fake a source address but that routers on the major backbones will append the real IP address somewhere.
 
???

---

### Post by bodhi.zazen on 2009-06-30
> **aphexcoil said:**
> Today I was working on SSH and could not get putty to work with the keys. I checked the auth.log in /var/log and noticed it was constantly changing -- tail auth.log
 
Some hacker from China was slamming my computer on port 22 trying to get in. 
 
I use ufw and feel comfortable with it, but what I would like to know is this:
 
1) Is there a program or firewall setting that detects a high amount of failed logins from an IP and temporarily puts up a rule denying all to that IP? I would like to have a 30 minute lockout for say 10 failed attempts. 

iptables is all you need.

[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

If you prefer use denyhosts, fail2ban, or configure /etc/hosts.allow (or more specifically /etc/hosts.deny).
 
> 2) In ufw, what rules take charge when you have conflicting rules: 
 
allow all to port 22
deny from ip xxx.xxx.xxx.xxx
 
Can ip xxx.xxx.xxx.xxx still get to port 22? Is it just how the rules are listed in ufw status numbered?with iptables it is first rule that matches

so 

deny ip xxxx
allow port 22

blocks ip xxx , allows others access to port 22

allow port 22
deny ip xxxx

allows ip xxx port 22, but blocks all other ports ...
 
> 3) I'd like to block all IP's from Asia. Is there a simple way to do this? Is there a list of IP's that originate from Asia that I can add to my configuration? Blocking entire A classes might be helpful if it belongs solely to Asia.
 
Thanks!Probably overkill and, as has been mentioned, spoofing an ip is not that difficult.

---

### Post by sasho_zl on 2009-07-01
You can also consider trying Host Intrusion Detection System with active response which will automatically block any IP address who tries to scan you or something else defined by your rules. I'm using OSSEC HIDS and it's very light and works great for now - [http://www.ossec.net]("http://www.ossec.net/")

---

### Post by bodhi.zazen on 2009-07-01
+1 OSSEC , although to be honest, if you have the time, you can achieve the same thing with iptables.

The reason I keep harping on iptables is it takes the place of sooo many applications -

denyhosts/fail2ban , tcpwrappers , server config files, GUFW/firestarter/Shorewall, OSSEC , etc, etc, etc.

by time you learn all these things you could just learn iptables, which is very portable.

Or if you prefer may layers of security.

---

### Post by ronaldprettyman on 2009-07-01
> **aphexcoil said:**
> Today I was working on SSH and could not get putty to work with the keys. I checked the auth.log in /var/log and noticed it was constantly changing -- tail auth.log
 
Some hacker from China was slamming my computer on port 22 trying to get in. 
 
I use ufw and feel comfortable with it, but what I would like to know is this:
 
1) Is there a program or firewall setting that detects a high amount of failed logins from an IP and temporarily puts up a rule denying all to that IP? I would like to have a 30 minute lockout for say 10 failed attempts. 
 
2) In ufw, what rules take charge when you have conflicting rules: 
 
allow all to port 22
deny from ip xxx.xxx.xxx.xxx
 
Can ip xxx.xxx.xxx.xxx still get to port 22? Is it just how the rules are listed in ufw status numbered?
 
3) I'd like to block all IP's from Asia. Is there a simple way to do this? Is there a list of IP's that originate from Asia that I can add to my configuration? Blocking entire A classes might be helpful if it belongs solely to Asia.
 
Thanks!
1 yes blacklist or blackninja
2 I'm not sure
3 Yes, but good luck with that. Just disable normal account names, such as root mysql and such, only enable ssh access to a certain account name, thats unusual with a strange password, with blacklisting after 4 or 5 tries, the chances of someone guessing the username and password are slim to none

Most attacks are though convential usernames adding a bang to your password (bang=!) makes it almost imposible for it to be bruteforced, using lots of special characters and case changes as well

you never know where an actual attacker is coming from you only know the machine their are using to attack. They could be in the other room, connected to a machine in china and attacking your machine from the machine in china. Alot of foreign countries have companies that give trials on dedicated and virtual servers with root access that hackers use to attack from.Not to mention other devious ways to gain access to a machine for the use of attacking others.

---

### Post by movieman on 2009-07-01
If you allow external access to SSH, you should always run it on a non-standard port so script kiddies will see port 22 is closed and go elsewhere. If you're behind a router/firewall you can probably configure it to forward from port 39965 (or whatever you choose) on the router to port 22 on the system you want to be able ssh to so you can still use port 22 on your internal LAN.

---

### Post by HermanAB on 2009-07-01
Howdy,

Edit /etc/ssh/sshd_config and change:
# port 22

to:
port 22222
(or whatever you want <65000)

Then restart SSH.

SSH Daemon will then listen on the new port and your script kiddie problem will be solved.  

These SSH attacks are actually not script kiddies at all - they are automated attacks to find vulnerable servers to set up spam engines.  Linux servers are highly prized for that, since they are usually on high speed fibre links and can send out more spam in an hour than a Windows home PC can send in a lifetime.

---

### Post by scorp123 on 2009-07-02
> **aphexcoil said:**
>  1) Is there a program or firewall setting that detects a high amount of failed logins from an IP and temporarily puts up a rule denying all to that IP? I would like to have a 30 minute lockout for say 10 failed attempts.  The package you want is called **denyhosts** ...  It monitors SSH's logs and it then reacts based on the rules that you defined.

Here is a nice tutorial:

[http://www.ubuntugeek.com/securing-ssh.html](http://www.ubuntugeek.com/securing-ssh.html)
[http://www.howtoforge.com/preventing_ssh_dictionary_attacks_with_denyhosts](http://www.howtoforge.com/preventing_ssh_dictionary_attacks_with_denyhosts)


EDIT: ... errors corrected. Never mind :)

---

