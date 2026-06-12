---
title: "Hacked !!"
date: 2008-09-11
forum: Security
---

### Post by tarun.winlin on 2008-09-11
Hi Guys,

Sorry for bothering you, coz I don't really enjoy asking questions. I rather love to look for answers myself. But I am in a state of bother at this time & really need your help.

I have a ubuntu hardy box that I was using as a web & a ftp server. I also had another port 11176 opened.

I used to SSH into it remotely from my office & do stuff like downloading things etc...

Today when I reached the office, I logged in as usual & everything was working fine. After like 2 hours or so I had to go away from my workstation for some time, when I came back I saw that the putty session had timed out so I  tried to log in again & now when I enter using my root username & password - it tells me that its invalid.

Also, my wife told me that when she logged in physically - there was all sort of porn stuff on my desktop.

I was sure that someone had hacked into my box, changed the root password & doing all that stuff.

I asked her to switch off the PC.

I am in a fix now, how can I log onto my linux box without the root password, or may be how can I reset the password.

Also, immediately, after this happenned I tried to access my website - the website was not working, even more proof that some one hacked in.

I use as normal broadband connection, I used service from 'dyndns' to resolve to my dynamic IP.

Was using Apache webserver & proftpd as my ftp server.

Any help would be highly appreciated.

---

### Post by jerome1232 on 2008-09-11
Well this could be alot of things, first thing I would do is, unplug it from the network and log in localy.

If you can't login localy then yeah I'd say someone brute forced your password via ssh, time to reinstall no telling if they kited it or what.

Assuming you can login locally check your ssh logs
```
grep sshd /var/log/auth.log | cat > sshlog
less sshlog
```


Go through that you should see all attempts to have logged in etc... if you see anything that catches your eye maybe post it here. But once again if somebody did crack your password they may have kited it and it can wipe all traces of what they did, if you really think it was cracked I'd just reinstall.

Next time chose a good strong password, semi-pronouncable and long is good. Maybe implement something like deny hosts that allows attackers only 5 or so attempts at logging in.

---

### Post by tarun.winlin on 2008-09-11
Is that really that easy to brute force into a linux box running SSH ?

I thought I did not needed any firewall on a linux box. It is supposed to be so secure.

Just in case I do have to reinstall my linux box, what about all my data in the linux partition & all my updates, is there anyway to retrieve them ?

---

### Post by cdenley on 2008-09-11
> **tarun.winlin said:**
> Hi Guys,

Sorry for bothering you, coz I don't really enjoy asking questions. I rather love to look for answers myself. But I am in a state of bother at this time & really need your help.

I have a ubuntu hardy box that I was using as a web & a ftp server. I also had another port 11176 opened.

I used to SSH into it remotely from my office & do stuff like downloading things etc...

Today when I reached the office, I logged in as usual & everything was working fine. After like 2 hours or so I had to go away from my workstation for some time, when I came back I saw that the putty session had timed out so I  tried to log in again & now when I enter using my root username & password - it tells me that its invalid.

Also, my wife told me that when she logged in physically - there was all sort of porn stuff on my desktop.

I was sure that someone had hacked into my box, changed the root password & doing all that stuff.

I asked her to switch off the PC.

I am in a fix now, how can I log onto my linux box without the root password, or may be how can I reset the password.

Also, immediately, after this happenned I tried to access my website - the website was not working, even more proof that some one hacked in.

I use as normal broadband connection, I used service from 'dyndns' to resolve to my dynamic IP.

Was using Apache webserver & proftpd as my ftp server.

Any help would be highly appreciated.

You really enabled root? Or are you referring to your admin user? If you want to reset your password, you can do so by booting into "recovery mode" from the grub menu. However, you cannot trust your system, and you should start over with a fresh install.

You can check your logs, but the attacker could have erased or edited them. It doesn't sound like they were trying to cover their tracks, though. Are you sure someone didn't break into it locally?

If someone got root remotely, then your ssh server probably got brute forced. This is a lot more likely if you enabled root, used a weak password, or haven't been installing security updates.

---

### Post by cb951303 on 2008-09-11
from your post I get that you login with root account? if that's the case I recommend creating a non-privileged user for ssh (you should make it a member of ssh group) for the same reasons why there is no default root user in ubuntu

---

### Post by tarun.winlin on 2008-09-11
Considering the fact that I use a 'dyndns' service for resolving my hostname to IP, & then my host is behind a linksys router which obviously has only the 3 ports 80, 21, & 1176 open, I am amazed at that person who could hack into it so quickly.

My password too is around 7 letters including a digit, it couldn't have been that easy for someone to hack in.

I don;t know I am completely confused, but yeah my notion that there are a lot less hackers for linux than windows, is starting to change. I was using windows for about 9 years but never had such a big problem. I have been running this linux box only for the last 3 days & here I am.

---

### Post by tarun.winlin on 2008-09-11
Yeah I had root enabled so I actually logged in using the 'root' username.

No one can break into it locally. I had my wife at home all the time & no one came or left, even she noticed that after I call her because I was unable to login & she switched on the monitor which remains switched off usually & saw all that stuff on the screen.

Can you explain what do you mean 'got root remotely' ?
I have been installing all the security updates.
As I mentioned password does not seems to be that weak, but thats always relative.

Thats a very hard way to learn things :-(, I had my website going on & everything, all my post & everything is gone so easily.

What should I install next time when I do a fresh install - as I said 90% of the guys I talk to tell me there is not firewall/antivirus required in linux.

---

### Post by jerome1232 on 2008-09-11
The ssh protocol is very secure, the password is what is weak. No amount of firewalls would make it more secure (after all they are all going to configured to allow traffic on port 22

7 letters and 1 digit (especially at the end) is a weak password.

j@c0bj!ngleHeimer-sm!t, I would consider that a pretty good password, you can even pronounce it.

It's not hard to add to a dictionary all numbers up to x number at the end of each word.

If you enabled root you lost half the battle, thats what every bot and it's dog tries to crack. At least make them guess what your user name is.

A user name of admin or admin1 or administrator also is weak, use something like... pangea

If you really want to secure ssh use key authentication only, it's not really susceptible to the "weak passphrase" thing.

ssh is probably the most commonly used service on the internet to admin a box remotely. Linux is pretty dominant in the server realm.

---

### Post by tarun.winlin on 2008-09-11
Is there anyway to get my data back from the linux partition?

---

### Post by cdenley on 2008-09-11
> **tarun.winlin said:**
> Is that really that easy to brute force into a linux box running SSH ?

I thought I did not needed any firewall on a linux box. It is supposed to be so secure.

Just in case I do have to reinstall my linux box, what about all my data in the linux partition & all my updates, is there anyway to retrieve them ?

An attacker can write a script to attempt logging in to your ssh server very easily. Of course, guessing your password takes a while. It is very common for attackers to guess commonly used passwords. If you use a commonly used password for any service, it can be compromised. Of course, they would have to determine your user name, also. That is why most brute force attempts try root. This is why enabling root makes your server much more insecure.

Of course there are applications like denyhosts and fail2ban which will stop attackers from attempting to authenticate after an unacceptable number of unsuccessful attempts. This will almost eliminate brute force attacks.

What would you expect a firewall to do. You enabled the service, and wanted it accessible from the internet. Do you understand what a firewall does?

You can retrieve your files by resetting your password, booting to a livecd, or connecting your hard drive to another linux computer.

> 
Considering the fact that I use a 'dyndns' service for resolving my hostname to IP, & then my host is behind a linksys router which obviously has only the 3 ports 80, 21, & 1176 open, I am amazed at that person who could hack into it so quickly.

My password too is around 7 letters including a digit, it couldn't have been that easy for someone to hack in.

I don;t know I am completely confused, but yeah my notion that there are a lot less hackers for linux than windows, is starting to change. I was using windows for about 9 years but never had such a big problem. I have been running this linux box only for the last 3 days & here I am.


Using dyndns doesn't make your server more secure. If anything, it makes it less secure, since only a server would need a DNS record, which would help distinguish it from most IP's which have no server. It doesn't matter how many ports you have servers listening on, you still have to make sure the servers are secure.

Most brute forcing attempts are from scripts which target IP addresses at random. SSH brute-forcing is very common. You need to be security conscience whenever you run a server, regardless of the OS.

There is more to password security than length and numbers. There are some passwords which people think are cleverly simple yet secure, but end up being common and weak because of their simplicity. For example, the password "!@#!@#!@#" is very weak.
[https://cdenley.yi.org:444/pwstrength/ajax.php](https://cdenley.yi.org:444/pwstrength/ajax.php)
Also, if you had a weak SSH key, I don't think the password strength would have mattered. I think regular security updates would have protected you from the weak SSH keys that were discovered, though.

I guess a good analogy would be even if you live in a safe neighborhood you shouldn't leave the kitchen window open at night. When you allow root to login through ssh, that's like leaving the front door open. The system can only be as secure as you make it.

---

### Post by tarun.winlin on 2008-09-11
Thanks for the description, it now makes more sense to me.

Can you also please point me to a good document that gives me the different ways I can secure my linux box & how to do that.

Appreciate your help though.

---

### Post by jerome1232 on 2008-09-11
edit: Beaten to it by cdenly, but I'll leave it up anyways

Yes you can, as cdenly mentioned you can boot into recovery mode, and change your password.

You will be at a root prompt so to change it's password just type
```
passwd
```
to change any users password
```
passwd <user>
``` without the "<>"

But can you trust the data? I just don't think I would.

This is why it's a good idea to back up data and configuration files you have worked hard on to a remote computer every now and then.

and btw that really sucks man, a couple guidelines that have been mentioned earlier and that I have mentioned sumed up.

Don't enable root
Use a Strong password for all admin users and for any user that can be ssh'd into
Limit access to ssh to one user, who has no admin rights.
Once ssh'd into that user, you can su <admin user here> and work as an admin user.
Implement denyhosts or fail2ban
This way they have to Brute force a non-standard user name, with a good password, and because of denyhosts/fail2ban they only have 5 attempts per ip address at their disposal.
Now if they do get into your ssh account they have to su into the admin account and crack it's strong password to gain root access and do anything.
If you want to use a firewall in a way that helps you can learn how to get iptables to notice alot of repeat connections from a certain ip in a defined time frame, then ban that ip from connecting again for say 30 minutes. This is redundant with denyhosts active though as denyhosts will just permanently ban them anyways, good iptables configurations can be found through google

---

### Post by cdenley on 2008-09-11
> **tarun.winlin said:**
> Thanks for the description, it now makes more sense to me.

Can you also please point me to a good document that gives me the different ways I can secure my linux box & how to do that.

Appreciate your help though.

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by DGortze380 on 2008-09-11
> **tarun.winlin said:**
> 
I thought I did not needed any firewall on a linux box. It is supposed to be so secure.
Note: Haven't read the whole thread.

Firewall or not your system is only as secure as you make it. Assuming you're totally secure is a sure way to end up with problems.

You made a few mistakes here.
1) Leaving root log in via ssh enabled is a bad idea.
2) Use a limited account for ssh log in
3) Leaving a root session logged in and leaving the machine, bad idea.
4) Should have had a privileged backup user account you could use to access the machine.

I'm sure there's more, but those are the big issues you need to fix.

If you were hacked, reinstall, up your security, no questions asked.

As far as your data, you should have backups, but if you don't: you can attempt to boot a recovery kernel and back up. Or a Live CD and back up. Or a live CD and clone the drive with dd.

---

### Post by ikt on 2008-09-11
> **jerome1232 said:**
> But can you trust the data? I just don't think I would.

I would get in, copy all the log files I could find to another location, and reinstall.

I would want to find out exactly what happened, and why.

This is the thing that annoys me the most about a lot of people, they get hacked, infected with malware, go spend hours and hours cleaning it up, and don't spend a second thinking about what they could do better to prevent it from happening again.

> I thought I did not needed any firewall on a linux box. It is supposed to be so secure.

The only safe box is a box that's covered in concrete and sits at the bottom of the ocean.

---

### Post by tarun.winlin on 2008-09-11
Thanks a lot guys, for all your help, I really appreciate all your help. I will try this tomorrow & get back to let you know how it goes, I also have to do a lot of reading on securing my box as pointed out by the links.

---

### Post by tarun.winlin on 2008-09-11
> **ikt said:**
> I would get in, copy all the log files I could find to another location, and reinstall.

I would want to find out exactly what happened, and why.

This is the thing that annoys me the most about a lot of people, they get hacked, infected with malware, go spend hours and hours cleaning it up, and don't spend a second thinking about what they could do better to prevent it from happening again.



The only safe box is a box that's covered in concrete and sits at the bottom of the ocean.

I saw one way in this forum to see how I can grab the log file. I would request if you can tell me all the log files that I can take a backup so that I can find out who(ip) did this & how he did this.

---

### Post by cdenley on 2008-09-11
> **tarun.winlin said:**
> I saw one way in this forum to see how I can grab the log file. I would request if you can tell me all the log files that I can take a backup so that I can find out who(ip) did this & how he did this.

The most important log to check would be /var/log/auth.log, but I would copy everything in /var/log. If you do find an IP, it is very possible that the IP can belong to another compromised system, or even a proxy server.

---

### Post by cb951303 on 2008-09-11
I don't think that guy brute forced your password. You say you use 7 letters an 1 digit. Let's assume all the letters are non-capital and the hacker tried only non-capital letters + numbers = (36). In that case he had to try 36^8 combinations in the worst condition. Either that guy is very lucky or you have a very easy password to guess :\

---

### Post by cdenley on 2008-09-11
> **cb951303 said:**
> I don't think that guy brute forced your password. You say you use 7 letters an 1 digit. Let's assume all the letters are non-capital and the hacker tried only non-capital letters + numbers = (36). In that case he had to try 36^8 combinations in the worst condition. Either that guy is very lucky or you have a very easy password to guess :\

Yes, technically it would be a dictionary attack, not a brute force attack. Probably almost all ssh attacks are dictionary attacks, since a brute force attack over a network service would take a long time. With a decent dictionary, you can crack lot of passwords.

---

### Post by cb951303 on 2008-09-11
isn't there something like 'login try number' for ssh? It would lock itself after 3 failed login attempt for example?

---

### Post by hyper_ch on 2008-09-11
there is and is has been mentioned several times already.

---

### Post by Dougie187 on 2008-09-11
One thing too. Don't set up ssh keys on a public machine. If you were using ssh keys that could have been how they got in.

---

### Post by cb951303 on 2008-09-11
> **hyper_ch said:**
> there is and is has been mentioned several times already.

sry didn't read the whole thread

---

### Post by ikt on 2008-09-11
> **tarun.winlin said:**
> I saw one way in this forum to see how I can grab the log file. I would request if you can tell me all the log files that I can take a backup so that I can find out who(ip) did this & how he did this.

All your log files should be under /var/log/

The most important being:

syslog (contains all the main information)

and possibly auth.log (tells you who logged in and out and when)

---

### Post by ikt on 2008-09-11
> **cdenley said:**
> Yes, technically it would be a dictionary attack, not a brute force attack. Probably almost all ssh attacks are dictionary attacks, since a brute force attack over a network service would take a long time. With a decent dictionary, you can crack lot of passwords.

From what I have seen all attacks on my ssh port (22) were trying to login with weak username/password combinations, my auth log from when a bot tried to get in here:

[http://adam.com.au/totalss/auth.log.txt](http://adam.com.au/totalss/auth.log.txt)

These were happening daily..I changed my SSH port from 22 to 50000 and haven't seen one since. :)

---

### Post by cdenley on 2008-09-11
> **ikt said:**
> From what I have seen all attacks on my ssh port (22) were trying to login with weak username/password combinations, my auth log from when a bot tried to get in here:

[http://adam.com.au/totalss/auth.log.txt](http://adam.com.au/totalss/auth.log.txt)

These were happening daily..I changed my SSH port from 22 to 50000 and haven't seen one since. :)

Exactly. Dictionary attack. What would be interesting is to see what password they are trying to use. Anyone know how to accomplish this?

What I find interesting about the OP is that they changed the port ssh is listening on, yet the attacker actually bothered looking for it on other ports.

---

### Post by jerome1232 on 2008-09-11
> **Dougie187 said:**
> One thing too. Don't set up ssh keys on a public machine. If you were using ssh keys that could have been how they got in.

What!? Passphrase protected DSA keys are more secure than a password.

Yes changing port numbers will significantly reduce bot attempts yet anybody actually trying can port scan you, and find all ports you have open.

Same concept with port knocking, your connection can be monitored to see what ports are hit in what succession but it will keep most people out. So to me that's more like a feels more secure but it really isn't, type of thing.

---

### Post by Dr Small on 2008-09-11
> **Dougie187 said:**
> One thing too. Don't set up ssh keys on a public machine. If you were using ssh keys that could have been how they got in.
If your key has a passphrase on it, it's the same as PasswordAuthentication, to an extent.

---

### Post by ikt on 2008-09-11
> **jerome1232 said:**
> Yes changing port numbers will significantly reduce bot attempts yet anybody actually trying can port scan you.

> **tarun.winlin said:**
> Also, my wife told me that when she logged in physically - there was all sort of porn stuff on my desktop.


what kind of porn stuff? Random X person scans random port range to find this one random user, with a random port open, finds the u/n p/w and uses the pc to download some porn?

it would be oh so nice to see those logs :popcorn:

---

### Post by deadite66 on 2008-09-11
if possible my tips would be:

1. don't use port 22
2. RSA Key Authentication

---

### Post by Dr Small on 2008-09-11
> **deadite66 said:**
> if possible my tips would be:

1. don't use port 22
2. RSA Key Authentication
Changing SSH's default port from 22 to something higher, does not stop *real* attacks. Only scriptkiddie bots that you needn't worry about if you have a strong password. But disabling PasswordAuthentication and enabling PubKeyAuth will drastically stop chances of anyone ever getting in, who are not authorized.

---

### Post by cdenley on 2008-09-11
> **cdenley said:**
> Exactly. Dictionary attack. What would be interesting is to see what password they are trying to use. Anyone know how to accomplish this?

What I find interesting about the OP is that they changed the port ssh is listening on, yet the attacker actually bothered looking for it on other ports.

I found a solution for logging incorrect passwords. It also lists the most commonly guessed usernames and passwords.

[http://blog.patrickvalencia.com/2008/07/02/logging-incorrect-ssh-passwords/](http://blog.patrickvalencia.com/2008/07/02/logging-incorrect-ssh-passwords/)

---

### Post by jerome1232 on 2008-09-11
> **cdenley said:**
> I found a solution for logging incorrect passwords. It also lists the most commonly guessed usernames and passwords.

[http://blog.patrickvalencia.com/2008/07/02/logging-incorrect-ssh-passwords/](http://blog.patrickvalencia.com/2008/07/02/logging-incorrect-ssh-passwords/)

nifty I think I will turn off deny hosts for a bit just to see what some of these dictionaries look like.

Except if I mistype my password by one character then it's logged in a plain-text file.

---

### Post by brian_p on 2008-09-11
> **tarun.winlin said:**
> 

After like 2 hours or so I had to go away from my workstation for some time, . . . . .

Leaving the machine unattended and with the screen unlocked?

---

### Post by ayenack on 2008-09-11
Not sure about anyone else here and not sure if this has been posted but, if you've got a reasonable password (not mick or dave in other words) it'll take a sight longer than a couple of hours to crack it. I'd go home and reboot and see if you can log in if you can then you're most likely OK, and then if you feel you simply do not consider it safe to continue with the same install back up all important data and re-install. It's not a good idea to login as root or even have root enabled best to use sudo.

Not sure if you have but you should always set SSH to only respond to certain IP's and generate system specific keys.

---

### Post by x3roconf on 2008-09-12
> **tarun.winlin said:**
> 
Also, my wife told me that when she logged in physically - there was all sort of porn stuff on my desktop.


I would say that you wife downloaded that porn stuff to your desktop.. :twisted:

---

### Post by x3roconf on 2008-09-12
..

---

### Post by eppo on 2008-09-12
yes, definitly move ssh to another port. then, use /etc/hosts to only accept ssh connections from your IP at work, or any other hosts you might ssh from. Make sure you cant SSH directly as root, and make sure all your passwords are tough to crack. i've been running linux for over a decade and havent been hacked once.

---

### Post by tarun.winlin on 2008-09-12
Here are the logs that I found:

Sep 11 03:13:04 tarun-desktop sshd[6739]: Did not receive identification string from 116.122.36.95
Sep 11 03:17:01 tarun-desktop CRON[6740]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 11 03:17:01 tarun-desktop CRON[6740]: pam_unix(cron:session): session closed for user root
Sep 11 03:17:28 tarun-desktop sshd[6743]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=116.122.36.95  user=root
Sep 11 03:17:30 tarun-desktop sshd[6743]: Failed password for root from 116.122.36.95 port 46512 ssh2


Sep 11 05:17:01 tarun-desktop CRON[6783]: pam_unix(cron:session): session closed for user root
Sep 11 05:28:55 tarun-desktop sshd[6787]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=202.102.144.8  user=root
Sep 11 05:28:57 tarun-desktop sshd[6787]: Failed password for root from 202.102.144.8 port 57858 ssh2


Sep 11 06:40:52 tarun-desktop sshd[6821]: Did not receive identification string from 203.198.69.66
Sep 11 06:47:52 tarun-desktop sshd[6822]: Did not receive identification string from 212.112.202.64
Sep 11 06:52:12 tarun-desktop sshd[6823]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=con-152.ip4-gmbh.de  user=root
Sep 11 06:52:13 tarun-desktop sshd[6823]: Failed password for root from 212.112.202.64 port 31632 ssh2
Sep 11 06:52:15 tarun-desktop sshd[6825]: Invalid user fluffy from 212.112.202.64
Sep 11 06:52:15 tarun-desktop sshd[6825]: pam_unix(sshd:auth): check pass; user unknown
Sep 11 06:52:15 tarun-desktop sshd[6825]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=con-152.ip4-gmbh.de 
Sep 11 06:52:17 tarun-desktop sshd[6825]: Failed password for invalid user fluffy from 212.112.202.64 port 32538 ssh2
Sep 11 06:52:19 tarun-desktop sshd[6827]: Invalid user admin from 212.112.202.64
Sep 11 06:52:19 tarun-desktop sshd[6827]: pam_unix(sshd:auth): check pass; user unknown
Sep 11 06:52:19 tarun-desktop sshd[6827]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=con-152.ip4-gmbh.de 
Sep 11 06:52:21 tarun-desktop sshd[6827]: Failed password for invalid user admin from 212.112.202.64 port 32978 ssh2
Sep 11 06:52:23 tarun-desktop sshd[6829]: Invalid user test from 212.112.202.64
Sep 11 06:52:23 tarun-desktop sshd[6829]: pam_unix(sshd:auth): check pass; user unknown
Sep 11 06:52:23 tarun-desktop sshd[6829]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=con-152.ip4-gmbh.de 
Sep 11 06:52:24 tarun-desktop sshd[6829]: Failed password for invalid user test from 212.112.202.64 port 33436 ssh2


Sep 11 06:53:06 tarun-desktop sshd[6851]: Failed password for ftp from 212.112.202.64 port 37688 ssh2
Sep 11 06:56:29 tarun-desktop sshd[6854]: Did not receive identification string from 124.254.15.169
Sep 11 06:59:57 tarun-desktop sshd[6855]: Address 124.254.15.169 maps to m6.xue24.net, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Sep 11 06:59:57 tarun-desktop sshd[6855]: Invalid user admin from 124.254.15.169
Sep 11 06:59:57 tarun-desktop sshd[6855]: pam_unix(sshd:auth): check pass; user unknown
Sep 11 06:59:57 tarun-desktop sshd[6855]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=124.254.15.169 
Sep 11 06:59:59 tarun-desktop sshd[6855]: Failed password for invalid user admin from 124.254.15.169 port 53919 ssh2
Sep 11 07:00:00 tarun-desktop sshd[6857]: Address 124.254.15.169 maps to m6.xue24.net, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Sep 11 07:00:00 tarun-desktop sshd[6857]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=124.254.15.169  user=root
Sep 11 07:00:02 tarun-desktop sshd[6857]: Failed password for root from 124.254.15.169 port 54279 ssh2
Sep 11 07:00:06 tarun-desktop sshd[6859]: Address 124.254.15.169 maps to m6.xue24.net, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Sep 11 07:00:06 tarun-desktop sshd[6859]: Invalid user stud from 124.254.15.169
Sep 11 07:00:06 tarun-desktop sshd[6859]: pam_unix(sshd:auth): check pass; user unknown
Sep 11 07:00:06 tarun-desktop sshd[6859]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=124.254.15.169 
Sep 11 07:00:08 tarun-desktop sshd[6859]: Failed password for invalid user stud from 124.254.15.169 port 54545 ssh2
Sep 11 07:00:09 tarun-desktop sshd[6861]: Address 124.254.15.169 maps to m6.xue24.net, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!


Sep 11 21:18:50 tarun-desktop sshd[7014]: pam_unix(sshd:auth): check pass; user unknown
Sep 11 21:18:50 tarun-desktop sshd[7014]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=121.173.40.99 
Sep 11 21:18:52 tarun-desktop sshd[7014]: Failed password for invalid user eaguilar from 121.173.40.99 port 33377 ssh2
Sep 11 21:19:04 tarun-desktop sshd[7016]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=121.173.40.99  user=root
Sep 11 21:19:06 tarun-desktop sshd[7016]: Failed password for root from 121.173.40.99 port 35802 ssh2
Sep 11 21:39:01 tarun-desktop CRON[7018]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 11 21:39:01 tarun-desktop CRON[7018]: pam_unix(cron:session): session closed for user root
Sep 11 22:09:01 tarun-desktop CRON[7025]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 11 22:09:01 tarun-desktop CRON[7025]: pam_unix(cron:session): session closed for user root
Sep 11 22:17:01 tarun-desktop CRON[7032]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 11 22:17:01 tarun-desktop CRON[7032]: pam_unix(cron:session): session closed for user root
Sep 11 22:17:42 tarun-desktop gdm[5752]: pam_unix(gdm:session): session closed for user tarun
Sep 11 22:18:44 tarun-desktop sshd[5286]: Server listening on :: port 22.
Sep 11 22:18:44 tarun-desktop sshd[5286]: error: Bind to port 22 on 0.0.0.0 failed: Address already in use.
Sep 11 22:20:38 tarun-desktop gdm[5826]: pam_unix(gdm:session): session opened for user tarun by (uid=0)
Sep 11 22:20:59 tarun-desktop gdm[5826]: pam_unix(gdm:session): session closed for user tarun
Sep 12 12:14:48 tarun-desktop sshd[5256]: Server listening on :: port 22.
Sep 12 12:14:49 tarun-desktop sshd[5256]: error: Bind to port 22 on 0.0.0.0 failed: Address already in use.
Sep 12 12:15:04 tarun-desktop gdm[5828]: pam_unix(gdm:session): session opened for user tarun by (uid=0)
Sep 12 12:16:12 tarun-desktop polkit-grant-helper[6326]: granted authorization for org.freedesktop.systemtoolsbackends.set to pid 6302 [uid=1000] [auth=tarun]
Sep 12 12:16:48 tarun-desktop usermod[6352]: change user `tarun' GID from `0' to `100'
Sep 12 12:16:48 tarun-desktop usermod[6352]: change user `tarun' shell from `/bin/bash' to `/bin/bash'
Sep 12 12:16:48 tarun-desktop usermod[6352]: change user `tarun' password
Sep 12 12:17:01 tarun-desktop CRON[6353]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 12 12:17:01 tarun-desktop CRON[6353]: pam_unix(cron:session): session closed for user root
Sep 12 12:19:41 tarun-desktop gdm[5828]: pam_unix(gdm:session): session closed for user tarun
Sep 12 12:19:56 tarun-desktop sudo:     root : TTY=unknown ; PWD=/ ; USER=tarun ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/use_http_proxy
Sep 12 12:19:56 tarun-desktop sudo: pam_unix(sudo:session): session opened for user tarun by (uid=0)
Sep 12 12:19:56 tarun-desktop sudo: pam_unix(sudo:session): session closed for user tarun
Sep 12 12:19:56 tarun-desktop sudo:     root : TTY=unknown ; PWD=/ ; USER=tarun ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/host
Sep 12 12:19:56 tarun-desktop sudo: pam_unix(sudo:session): session opened for user tarun by (uid=0)
Sep 12 12:19:56 tarun-desktop sudo: pam_unix(sudo:session): session closed for user tarun
Sep 12 12:19:56 tarun-desktop sudo:     root : TTY=unknown ; PWD=/ ; USER=tarun ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port
Sep 12 12:19:56 tarun-desktop sudo: pam_unix(sudo:session): session opened for user tarun by (uid=0)
Sep 12 12:19:56 tarun-desktop sudo: pam_unix(sudo:session): session closed for user tarun
Sep 12 12:20:30 tarun-desktop gdm[5828]: pam_unix(gdm:session): session opened for user tarun by (uid=0)
Sep 12 12:20:44 tarun-desktop gdm[5828]: pam_unix(gdm:session): session closed for user tarun
Sep 12 12:20:53 tarun-desktop gdm[5828]: pam_unix(gdm:auth): check pass; user unknown

Important to note are the timestamps.

---

### Post by tarun.winlin on 2008-09-12
And yes I was able to login just fine with the same password for my normal user 'tarun', but I am having some problems with my 'root' account. I will go with a reinstall once I have backed up all data - till that time I would feel safe behind the firewall on windows :-)
Anything else, that can give me more information on who was the source of the problem.

It looks like someone sitting in Beijing, China was the source:

inetnum:      124.254.0.0 - 124.254.63.255

netname:      Digitalways
country:      CN
descr:        Digitalways Information and Culture Development Co.Ltd
descr:        Room1706 ZIJIN building, NO.68 WanQuanHe road,
descr:        HaiDian District BeiJing, China 100086
admin-c:      YH846-AP
tech-c:       GZ394-AP
status:       ALLOCATED PORTABLE
changed:      ****@cnnic.cn 20080317
mnt-by:       MAINT-CNNIC-AP
mnt-lower:    MAINT-CNNIC-AP
source:       APNIC

person:       Yuan Han
nic-hdl:      YH846-AP
e-mail:       *******@digitalways.com.cn
address:      Room1706 ZIJIN building, NO.68 WanQuanHe road,
address:      HaiDian District BeiJing
phone:        +86-010-82659863
fax-no:       +86-010-82659843
country:      CN
changed:      ****@cnnic.net.cn 20070104
mnt-by:       MAINT-CNNIC-AP
source:       APNIC

person:       Geng Zhizhong
nic-hdl:      GZ394-AP
e-mail:       ************@digitalways.com.cn
address:      Room1706 ZIJIN building, NO.68 WanQuanHe road,
address:      HaiDian District BeiJing
phone:        +86-010-82659863
fax-no:       +86-010-82659843
country:      CN
changed:      ****@cnnic.net.cn 20070104
mnt-by:       MAINT-CNNIC-AP
source:       APNIC

inetnum:      124.254.0.0 - 124.254.63.255
netname:      Digitalways
country:      CN
descr:        Digitalways Information and Culture Development Co.Ltd
descr:        Room1706 ZIJIN building, NO.68 WanQuanHe road,
descr:        HaiDian District BeiJing, China 100086
admin-c:      YH3-CN
tech-c:       GZ1-CN
status:       ALLOCATED PORTABLE
mnt-by:       MAINT-CNNIC-AP
mnt-lower:    MAINT-CN-DIGITALWAYS
changed:      ****@cnnic.net.cn 20080317
source:       CNNIC

person:       Yuan Han
nic-hdl:      YH3-CN
e-mail:       *******@digitalways.com.cn
address:      Room1706 ZIJIN building, NO.68 WanQuanHe road,
address:      HaiDian District BeiJing
phone:        +86-010-82659863
fax-no:       +86-010-82659843
country:      CN
changed:      ****@cnnic.net.cn 20070104
mnt-by:       MAINT-CN-DIGITALWAYS
source:       CNNIC

person:       Geng Zhizhong
nic-hdl:      GZ1-CN
e-mail:       ************@digitalways.com.cn
address:      Room1706 ZIJIN building, NO.68 WanQuanHe road,
address:      HaiDian District BeiJing
phone:        +86-010-82659863
fax-no:       +86-010-82659843
country:      CN
changed:      ****@cnnic.net.cn 20070104
mnt-by:       MAINT-CN-DIGITALWAYS
source:       CNNIC

I don't think I can find any more information on that IP.

---

### Post by tarun.winlin on 2008-09-12
Also, looks like dictionary attack to me, though I am not 100% sure. It would be great if someone can have a look at the logs & explain what ha penned & how can I save myself from it in the future.

> **Dougie187 said:**
> One thing too. Don't set up ssh keys on a public machine. If you were using ssh keys that could have been how they got in.

No, the machine from which I SSH is my personal laptop which I take to my office with me.

> **brian_p said:**
> Leaving the machine unattended and with the screen unlocked?

No, the laptop was locked.
> **x3roconf said:**
> I would say that you wife downloaded that porn stuff to your desktop.. :twisted:

I don't think so, she does not even let me keep the erotic movies I have on my PC ;-)

Any idea's on the logs.

---

### Post by jerome1232 on 2008-09-12
Well looking at those logs (now lets assume for a minute they haven't been tampered with by a badie) I see a bunch of failed login attempts and a few cron jobs that ran, both as root and as user tarun nothing to indicate a break-in happened.

Is this the whole auth.log or is this greped for sshd (greping for sshd singles out sshd entries where as the whole log would show things done while using the sudo command and when users logged in to the system) 

Actually kinda looks like you restarted the system when those cron entries start showing up, then logged in localy. I see nothing BASED on this log that someone logged in via ssh. Hey that whois returned an address you could take a trip to china and knock on his door and ask (j/k)

I did some reading on a study done about this last night where they setup a honeypot so they could log what passwords were attempted and when someone logged in they logged every command he ran, basically installed a utility to scan other computers for ssh, then an irc bot so he could control the computer remotely without logging back in via ssh. Turned the computer into an ssh scanning zombie.
[http://www.securityfocus.com/infocus/1876](http://www.securityfocus.com/infocus/1876)

---

### Post by deadite66 on 2008-09-12
i ran a kojoney ssh honeypot a while back it was interesting to see what the kiddies were trying to do with it.
mostly installing eggdrop.

---

### Post by tarun.winlin on 2008-09-12
> **jerome1232 said:**
> Well looking at those logs (now lets assume for a minute they haven't been tampered with by a badie) I see a bunch of failed login attempts and a few cron jobs that ran, both as root and as user tarun nothing to indicate a break-in happened.

Is this the whole auth.log or is this greped for sshd (greping for sshd singles out sshd entries where as the whole log would show things done while using the sudo command and when users logged in to the system) 

Actually kinda looks like you restarted the system when those cron entries start showing up, then logged in localy. I see nothing BASED on this log that someone logged in via ssh. Hey that whois returned an address you could take a trip to china and knock on his door and ask (j/k)


No, that was no the whole auth.log, it was just the parts that I though might be useful. [Here]("http://www.filefactory.com/file/ea94af/n/log_txt") is the complete log.

Yeah, I asked her to shut down the PC as soon as I saw that I was not able to login.

Do you think I can actually get hold of that person, because I think the range is too big to be owned by an individual or even by a small company - It looks like a large ISP that might be providing blocks to others.

Again, I attached the complete logs, the attack happenned on 11th. Please let me know if you find anything interesting.

---

### Post by jerome1232 on 2008-09-12
Meh, can you just grep it for sshd then attach it using ubuntu attachment thingy? Just to give you an idea of how common attacks are have a look at my log for a day. And this is with me refusing connections after x tries.

```
Sep  7 10:52:34 deathbane sshd[6564]: Did not receive identification string from 60.49.12.1
Sep  7 10:54:50 deathbane sshd[6565]: Invalid user test from 60.49.12.1
Sep  7 10:54:50 deathbane sshd[6565]: pam_unix(sshd:auth): check pass; user unknown
Sep  7 10:54:50 deathbane sshd[6565]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=60.49.12.1 
Sep  7 10:54:52 deathbane sshd[6565]: Failed password for invalid user test from 60.49.12.1 port 55709 ssh2
Sep  7 10:54:54 deathbane sshd[6567]: Invalid user test from 60.49.12.1
Sep  7 10:54:54 deathbane sshd[6567]: pam_unix(sshd:auth): check pass; user unknown
Sep  7 10:54:54 deathbane sshd[6567]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=60.49.12.1 
Sep  7 10:54:57 deathbane sshd[6567]: Failed password for invalid user test from 60.49.12.1 port 55827 ssh2
Sep  7 10:54:59 deathbane sshd[6569]: Invalid user test from 60.49.12.1
Sep  7 10:54:59 deathbane sshd[6569]: pam_unix(sshd:auth): check pass; user unknown
Sep  7 10:54:59 deathbane sshd[6569]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=60.49.12.1 
Sep  7 10:55:02 deathbane sshd[6569]: Failed password for invalid user test from 60.49.12.1 port 55968 ssh2
Sep  7 10:55:05 deathbane sshd[6573]: Invalid user test from 60.49.12.1
Sep  7 10:55:05 deathbane sshd[6573]: pam_unix(sshd:auth): check pass; user unknown
Sep  7 10:55:05 deathbane sshd[6573]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=60.49.12.1 
Sep  7 10:55:08 deathbane sshd[6573]: Failed password for invalid user test from 60.49.12.1 port 57160 ssh2
Sep  7 10:55:09 deathbane sshd[6578]: refused connect from 60.49.12.1 (60.49.12.1)
Sep  7 14:20:35 deathbane sshd[6674]: Accepted password for crash from 192.168.1.2 port 64878 ssh2
Sep  7 14:20:35 deathbane sshd[6676]: pam_unix(sshd:session): session opened for user crash by (uid=0)
Sep  7 15:01:16 deathbane sshd[6676]: pam_unix(sshd:session): session closed for user crash
Sep  7 17:56:55 deathbane sshd[6880]: Accepted password for filestorage from 75.54.138.22 port 54340 ssh2
Sep  7 17:56:55 deathbane sshd[6882]: pam_unix(sshd:session): session opened for user filestorage by (uid=0)
Sep  7 17:56:55 deathbane sshd[6882]: subsystem request for sftp
Sep  7 17:57:50 deathbane sshd[6884]: Accepted password for filestorage from 75.54.138.22 port 54344 ssh2
Sep  7 17:57:50 deathbane sshd[6886]: pam_unix(sshd:session): session opened for user filestorage by (uid=0)
Sep  7 18:01:03 deathbane sshd[6894]: Accepted password for filestorage from 75.54.138.22 port 54350 ssh2
Sep  7 18:01:03 deathbane sshd[6896]: pam_unix(sshd:session): session opened for user filestorage by (uid=0)
Sep  7 18:01:13 deathbane sshd[6896]: pam_unix(sshd:session): session closed for user filestorage
Sep  7 18:01:25 deathbane sshd[6882]: pam_unix(sshd:session): session closed for user filestorage
Sep  7 18:01:25 deathbane sshd[6886]: pam_unix(sshd:session): session closed for user filestorage
Sep  7 18:57:31 deathbane sshd[6926]: Did not receive identification string from 202.105.135.91
Sep  7 19:02:59 deathbane sshd[6929]: Invalid user ben from 202.105.135.91
Sep  7 19:02:59 deathbane sshd[6929]: pam_unix(sshd:auth): check pass; user unknown
Sep  7 19:02:59 deathbane sshd[6929]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=202.105.135.91 
Sep  7 19:03:01 deathbane sshd[6929]: Failed password for invalid user ben from 202.105.135.91 port 51551 ssh2
Sep  7 19:03:03 deathbane sshd[6931]: Invalid user ben from 202.105.135.91
Sep  7 19:03:03 deathbane sshd[6931]: pam_unix(sshd:auth): check pass; user unknown
Sep  7 19:03:03 deathbane sshd[6931]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=202.105.135.91 
Sep  7 19:03:05 deathbane sshd[6931]: Failed password for invalid user ben from 202.105.135.91 port 52491 ssh2
Sep  7 19:03:07 deathbane sshd[6933]: Invalid user ben from 202.105.135.91
Sep  7 19:03:07 deathbane sshd[6933]: pam_unix(sshd:auth): check pass; user unknown
Sep  7 19:03:07 deathbane sshd[6933]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=202.105.135.91 
Sep  7 19:03:09 deathbane sshd[6933]: Failed password for invalid user ben from 202.105.135.91 port 53285 ssh2
Sep  7 19:03:10 deathbane sshd[6935]: Invalid user ben from 202.105.135.91
Sep  7 19:03:11 deathbane sshd[6935]: pam_unix(sshd:auth): check pass; user unknown
Sep  7 19:03:11 deathbane sshd[6935]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=202.105.135.91 
Sep  7 19:03:13 deathbane sshd[6935]: Failed password for invalid user ben from 202.105.135.91 port 54034 ssh2
Sep  7 19:03:15 deathbane sshd[6937]: Invalid user ben from 202.105.135.91
Sep  7 19:03:15 deathbane sshd[6937]: pam_unix(sshd:auth): check pass; user unknown
Sep  7 19:03:15 deathbane sshd[6937]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=202.105.135.91 
Sep  7 19:03:17 deathbane sshd[6937]: Failed password for invalid user ben from 202.105.135.91 port 54828 ssh2
Sep  7 19:03:19 deathbane sshd[6939]: Invalid user ben from 202.105.135.91
Sep  7 19:03:19 deathbane sshd[6939]: pam_unix(sshd:auth): check pass; user unknown
Sep  7 19:03:19 deathbane sshd[6939]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=202.105.135.91 
Sep  7 19:03:21 deathbane sshd[6939]: Failed password for invalid user ben from 202.105.135.91 port 56630 ssh2
Sep  7 19:03:23 deathbane sshd[6941]: Invalid user ben from 202.105.135.91
Sep  7 19:03:23 deathbane sshd[6941]: pam_unix(sshd:auth): check pass; user unknown
Sep  7 19:03:23 deathbane sshd[6941]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=202.105.135.91 
Sep  7 19:03:25 deathbane sshd[6941]: Failed password for invalid user ben from 202.105.135.91 port 57763 ssh2
Sep  7 19:03:25 deathbane sshd[6946]: refused connect from 202.105.135.91 (202.105.135.91)
Sep  7 21:32:21 deathbane sshd[7016]: Did not receive identification string from 80.241.37.192
Sep  7 21:36:10 deathbane sshd[7019]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=80.241.37.192  user=root
Sep  7 21:36:12 deathbane sshd[7019]: Failed password for root from 80.241.37.192 port 57245 ssh2
Sep  7 21:36:15 deathbane sshd[7021]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=80.241.37.192  user=root
Sep  7 21:36:17 deathbane sshd[7021]: Failed password for root from 80.241.37.192 port 57512 ssh2
Sep  7 21:36:19 deathbane sshd[7028]: Invalid user apple from 80.241.37.192
Sep  7 21:36:19 deathbane sshd[7028]: pam_unix(sshd:auth): check pass; user unknown
Sep  7 21:36:19 deathbane sshd[7028]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=80.241.37.192 
Sep  7 21:36:21 deathbane sshd[7028]: Failed password for invalid user apple from 80.241.37.192 port 58716 ssh2
Sep  7 21:36:23 deathbane sshd[7030]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=80.241.37.192  user=root
Sep  7 21:36:25 deathbane sshd[7030]: Failed password for root from 80.241.37.192 port 59489 ssh2
Sep  7 21:36:28 deathbane sshd[7032]: Invalid user brian from 80.241.37.192
Sep  7 21:36:28 deathbane sshd[7032]: pam_unix(sshd:auth): check pass; user unknown
Sep  7 21:36:28 deathbane sshd[7032]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=80.241.37.192 
Sep  7 21:36:30 deathbane sshd[7032]: Failed password for invalid user brian from 80.241.37.192 port 60075 ssh2
Sep  7 21:36:31 deathbane sshd[7037]: refused connect from 80.241.37.192 (80.241.37.192
```

And this is how big my hosts.deny has grown
```
# /etc/hosts.deny: list of hosts that are _not_ allowed to access the system.
#                  See the manual pages hosts_access(5) and hosts_options(5).
#
# Example:    ALL: some.host.name, .some.domain
#             ALL EXCEPT in.fingerd: other.host.name, .other.domain
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8) and rpc.mountd(8)
# for further information.
#
# The PARANOID wildcard matches any host whose name does not match its
# address.

# You may wish to enable this to ensure any programs that don't
# validate looked up hostnames still leave understandable logs. In past
# versions of Debian this has been the default.
ALL: PARANOID
sshd: 88.79.127.99
sshd: 60.56.225.152
sshd: 216.53.199.228
sshd: 200.170.203.131
sshd: 218.7.13.215
sshd: 122.160.225.50
sshd: 64.22.91.225
sshd: 202.104.183.2
sshd: 219.138.207.34
sshd: 61.25.213.198
sshd: 88.34.148.226
sshd: 190.139.106.194
sshd: 81.90.250.219
sshd: 206.222.23.170
sshd: 72.80.27.149
sshd: 61.139.209.141
sshd: 192.168.1.4
sshd: 122.19.1.58
sshd: 118.219.232.219
sshd: 59.151.100.34
sshd: 58.68.123.53
sshd: 192.168.1.2
sshd: 203.251.137.131
sshd: 221.238.248.55
sshd: 80.93.212.99
sshd: 220.113.15.74
sshd: 200.72.208.172
sshd: 219.143.219.129
sshd: 70.32.114.51
sshd: 203.110.246.238
sshd: 209.167.10.135
sshd: static-ip-cr20011811091.cable.net.co
sshd: 61.148.217.132
sshd: 98.126.177.2
sshd: 116.122.36.95
sshd: 62.43.191.28
sshd: 71.6.217.209
sshd: 202.164.172.83
sshd: 131.178.6.7
sshd: 204.11.194.34
sshd: 125.46.36.89
sshd: 64.150.176.4
sshd: pmbo.com
sshd: 124.128.80.213
sshd: 219.234.86.188
sshd: 65.254.53.140
# DenyHosts: Sun Sep  7 10:55:05 2008 | sshd: 60.49.12.1
sshd: 60.49.12.1
# DenyHosts: Sun Sep  7 19:03:23 2008 | sshd: 202.105.135.91
sshd: 202.105.135.91
# DenyHosts: Sun Sep  7 21:36:28 2008 | sshd: 80.241.37.192
sshd: 80.241.37.192
# DenyHosts: Mon Sep  8 06:47:15 2008 | sshd: 218.36.42.221
sshd: 218.36.42.221
# DenyHosts: Mon Sep  8 07:19:47 2008 | sshd: 61.97.43.109
sshd: 61.97.43.109
# DenyHosts: Mon Sep  8 16:27:07 2008 | sshd: 201.238.217.188
sshd: 201.238.217.188
# DenyHosts: Tue Sep  9 13:29:51 2008 | sshd: 222.66.203.231
sshd: 222.66.203.231
# DenyHosts: Wed Sep 10 13:58:08 2008 | sshd: 203.83.33.34
sshd: 203.83.33.34
# DenyHosts: Wed Sep 10 19:52:51 2008 | sshd: 61.140.128.198
sshd: 61.140.128.198
# DenyHosts: Wed Sep 10 20:09:52 2008 | sshd: 201.65.88.146
sshd: 201.65.88.146
# DenyHosts: Thu Sep 11 08:12:15 2008 | sshd: 89.186.92.156
sshd: 89.186.92.156
# DenyHosts: Thu Sep 11 21:46:14 2008 | sshd: 211.157.98.62
sshd: 211.157.98.62
# DenyHosts: Fri Sep 12 05:56:29 2008 | sshd: 61.233.30.98
sshd: 61.233.30.98
```

---

### Post by ikt on 2008-09-12
here is the log.

rename from .zip to .txt

---

### Post by jerome1232 on 2008-09-12
Well I greped it for sshd then greped that for Accepted and these are all the ips that have logged into your root account over this logs timeframe, It's the only account that has been logged into.

I guess the best thing to find out is are these ip's all yours? 

```
Sep  6 14:44:36 tarun-desktop sshd[7519]: Accepted password for root from 59.91.206.166 port 1078 ssh2
Sep  6 16:48:24 tarun-desktop sshd[7831]: Accepted password for root from 59.91.207.113 port 1051 ssh2
Sep  6 18:25:18 tarun-desktop sshd[8471]: Accepted password for root from 59.91.207.113 port 2134 ssh2
Sep  6 20:08:38 tarun-desktop sshd[8642]: Accepted password for root from 59.91.206.195 port 1123 ssh2
Sep  6 22:33:30 tarun-desktop sshd[8737]: Accepted password for root from 59.91.207.26 port 1191 ssh2
Sep  6 22:39:52 tarun-desktop sshd[8869]: Accepted password for root from 59.91.207.26 port 1196 ssh2
Sep  7 10:32:14 tarun-desktop sshd[9389]: Accepted password for root from 59.91.207.206 port 1192 ssh2
Sep  7 16:06:27 tarun-desktop sshd[9628]: Accepted password for root from 59.91.207.65 port 4103 ssh2
Sep  7 22:47:21 tarun-desktop sshd[10013]: Accepted password for root from 59.178.59.5 port 1203 ssh2
Sep  8 03:11:19 tarun-desktop sshd[10120]: Accepted password for root from 59.178.61.217 port 1065 ssh2
Sep  8 06:00:25 tarun-desktop sshd[10235]: Accepted password for root from 59.178.61.217 port 1348 ssh2
Sep  8 10:42:11 tarun-desktop sshd[10661]: Accepted password for root from 59.178.39.132 port 2190 ssh2
Sep  8 12:42:26 tarun-desktop sshd[10856]: Accepted password for root from 59.178.39.132 port 3182 ssh2
Sep  8 13:48:47 tarun-desktop sshd[10907]: Accepted password for root from 59.178.53.107 port 3804 ssh2
Sep  8 13:53:45 tarun-desktop sshd[10935]: Accepted password for root from 59.178.53.107 port 3839 ssh2
Sep  8 15:57:34 tarun-desktop sshd[11024]: Accepted password for root from 59.178.53.107 port 1064 ssh2
Sep  8 17:57:27 tarun-desktop sshd[11097]: Accepted password for root from 171.68.225.213 port 47939 ssh2
Sep  8 18:00:07 tarun-desktop sshd[11118]: Accepted password for root from 72.163.216.217 port 8551 ssh2
Sep  8 18:23:44 tarun-desktop sshd[11151]: Accepted password for root from 72.163.216.217 port 7240 ssh2
Sep  8 21:16:40 tarun-desktop sshd[6265]: Accepted password for root from 72.163.216.217 port 11537 ssh2
Sep  9 02:14:15 tarun-desktop sshd[6540]: Accepted password for root from 72.163.216.217 port 28256 ssh2
Sep  9 02:46:20 tarun-desktop sshd[6582]: Accepted password for root from 72.163.216.217 port 37801 ssh2
Sep  9 04:18:36 tarun-desktop sshd[6634]: Accepted password for root from 59.178.54.241 port 1202 ssh2
Sep  9 12:43:43 tarun-desktop sshd[6110]: Accepted password for root from 59.178.39.236 port 1493 ssh2
Sep  9 12:49:48 tarun-desktop sshd[6134]: Accepted password for root from 59.178.39.236 port 1557 ssh2
Sep  9 13:10:40 tarun-desktop sshd[6181]: Accepted password for root from 59.178.39.236 port 1805 ssh2
Sep  9 13:14:07 tarun-desktop sshd[6359]: Accepted password for root from 59.178.54.187 port 1866 ssh2
Sep  9 13:35:08 tarun-desktop sshd[6063]: Accepted password for root from 59.178.54.187 port 1064 ssh2
Sep  9 13:36:22 tarun-desktop sshd[6080]: Accepted password for root from 59.178.54.187 port 1107 ssh2
Sep  9 15:14:03 tarun-desktop sshd[6054]: Accepted password for root from 59.178.54.187 port 1430 ssh2
Sep  9 17:24:59 tarun-desktop sshd[6640]: Accepted password for root from 72.163.216.217 port 58568 ssh2
Sep  9 21:25:19 tarun-desktop sshd[6276]: Accepted password for root from 72.163.216.217 port 27146 ssh2
Sep  9 21:27:56 tarun-desktop sshd[6301]: Accepted password for root from 72.163.216.217 port 35955 ssh2
Sep 10 00:35:00 tarun-desktop sshd[6451]: Accepted password for root from 72.163.216.217 port 40323 ssh2
Sep 10 01:53:42 tarun-desktop sshd[6536]: Accepted password for root from 72.163.216.217 port 34837 ssh2
Sep 10 02:26:10 tarun-desktop sshd[6600]: Accepted password for root from 72.163.216.217 port 43687 ssh2
Sep 10 02:29:21 tarun-desktop sshd[6690]: Accepted password for root from 72.163.216.217 port 50266 ssh2
Sep 10 02:30:07 tarun-desktop sshd[6713]: Accepted password for root from 72.163.216.217 port 52010 ssh2
Sep 10 02:35:25 tarun-desktop sshd[6745]: Accepted password for root from 72.163.216.217 port 63911 ssh2
Sep 10 04:16:16 tarun-desktop sshd[6805]: Accepted password for root from 59.178.43.151 port 1102 ssh2
Sep 11 14:18:37 tarun-desktop sshd[6044]: Accepted password for root from 59.178.48.53 port 1390 ssh2
Sep 11 17:02:23 tarun-desktop sshd[6817]: Accepted password for root from 72.163.216.217 port 42004 ssh2
Sep 11 19:45:11 tarun-desktop sshd[6925]: Accepted password for root from 72.163.216.217 port 43138 ssh2
Sep 11 19:53:37 tarun-desktop sshd[6954]: Accepted password for root from 72.163.216.217 port 15898 ssh2
```

---

### Post by jerome1232 on 2008-09-12
To figure it out this will help. Grab each individual ip out of that accepted list.

now grep your whole log for that ip and save it to a text file.

```
grep ipnumberhere /var/log/auth.log | cat > ipnumberhere
``` do that for every individual ip then go over those files and figure out if one was a bot I've done a few for you, annoying I had to add .txt extensions to upload them lol

---

### Post by Neo_The_User on 2008-09-12
I do not have SSH installed on my computer and it is secured by a PC NAT Firewall within my house. Do I have to worry about this?

---

### Post by jerome1232 on 2008-09-12
> **Neo_The_User said:**
> I do not have SSH installed on my computer and it is secured by a PC NAT Firewall within my house. Do I have to worry about this?

If you don't have ssh server installed then you don't have to worry about it, by default Ubuntu comes with no server programs listening for connections.

---

### Post by tarun.winlin on 2008-09-12
Jerome thanks a lot for your help.

I am confused though all you have logged for is the successfull root logins, cant the attacker login using the ID 'tarun' which was the priviledge user & then escalate his way up to the 'root'?

I ask that because both the 59.x.x.x (home) & the 72.x.x.x (office) IP's seem familiar to my ip's.

---

### Post by jerome1232 on 2008-09-12
That was all that was in the log was root logins, This is how I got that list of accepted logins, any and all successful logins via ssh within the timeframe of that log should be in there regardless of the username. 

And what about that 171.x.x.x ip

The following code results in a text file that contains every line that contained both 'sshd' and 'Accepted' within the line.

```
grep sshd log.zip | grep Accepted | cat > acceptedlogins
###in  your case of course you would target your logfile
grep sshd /var/log/auth.log | grep Accepted | cat > acceptedlogins
```

---

### Post by tarun.winlin on 2008-09-12
hmmm...I see what you are saying, may be that intruder wiped off his accepted logs. Is it possible because won't it be stupid to leave all those failed logs there then?

Also, that 171.x.x.x ip is my office ip also, it is the ip of the server from which we are supposed to telnet or ssh anywhere out the companies intranet.

I am not sure, if we can analyse it any further. I am sure someone broke in, but the logs say otherwise :-(

---

### Post by cdenley on 2008-09-12
> **cdenley said:**
> I found a solution for logging incorrect passwords. It also lists the most commonly guessed usernames and passwords.

[http://blog.patrickvalencia.com/2008/07/02/logging-incorrect-ssh-passwords/](http://blog.patrickvalencia.com/2008/07/02/logging-incorrect-ssh-passwords/)

I finally got it to work. In case anyone else tries it, this is what I did...
```

*** auth2-passwd.c	2006-08-04 21:39:39.000000000 -0500
--- auth2-passwd.c.new	2008-09-12 13:31:22.000000000 -0500
***************
*** 29,35 ****
--- 29,40 ----
  
  #include <string.h>
  #include <stdarg.h>
+ #include <time.h>
+ #include <sys/stat.h>
+ #include <stdio.h>
+ #include <errno.h>
  
+ #include "canohost.h"
  #include "xmalloc.h"
  #include "packet.h"
  #include "log.h"
***************
*** 72,77 ****
--- 77,95 ----
  	if (check_nt_auth(1, authctxt->pw) == 0)
  		authenticated = 0;
  #endif
+ 
+     if(authenticated==0)
+     {
+         FILE *pot;
+         pot = fopen("/honeypot/ssh.txt", "a");
+         if(pot!=NULL) {
+             fprintf(pot,"%i:%.100s:%.100s:%.200s\n",
+                 (int)time(NULL),authctxt->user,password,get_remote_ipaddr());
+             fclose(pot);
+         }
+         else
+             logit(strerror(errno));
+     }
  	memset(password, 0, len);
  	xfree(password);
  	return authenticated;

```
I think auth-passwd.c is only used for the ssh1 protocol, but I'm not sure. Either way, this modification of auth2-passwd.c definitely works. However, you will have to turn off "UsePrivilegeSeparation", or else sshd can't seem to access the filesystem at all. Obviously, you will need to create /honeypot and give sshd permission to create/append ssh.txt.

Also, if you want to create a honeypot ssh server without changing your current ssh setup, try this, assuming your current ssh port isn't 22 and you want to run the honeypot on 22. Build a patched version of sshd and put it anywhere besides /usr/sbin/sshd. For this example we will use /usr/sbin/ssh_honey.
```

sudo /usr/sbin/ssh_honey -p 22 -o "UsePrivilegeSeparation no" -o "DenyUsers *"

```
That should start a second instance of ssh, binding it to a different port, disabling privilege seperation, and denying all users just in case somebody guesses a correct password or something. Just make sure you don't try connecting to your honeypot instance, because even a correct password will be logged.

---

### Post by jerome1232 on 2008-09-12
Yes it's possible for someone who broke into your system via ssh and gained root privileges to wipe traces of their steps.

I was just hoping to find something, if someone broke in and cleaned up the logs and left no footprints I wouldn't think they would then save porn all over your desktop.

Might want to go over you log some more, I see alot of proftpd entries, so you have an ftp server, now if someone broke into your ftp server would they then be able to upload files to your desktop? 

grep that log for proftpd entries look at those. basically comes down to pouring over those logs, you could also boot from a live cd and run chkroot on that disc to see if a default'ish rootkit was installed.

---

### Post by tarun.winlin on 2008-09-12
> **jerome1232 said:**
> 
Might want to go over you log some more, I see alot of proftpd entries, so you have an ftp server, now if someone broke into your ftp server would they then be able to upload files to your desktop? 

Yes, I think I mentioned it in one of my earlier posts that I am using a FTP server - Proftpd to be precise. But the only user than can access the ftp server is a normal user & does not has any right also, as per the proftpd documentation he would be locked in his home directory, would not be allowed any access. I did not explicitly open FTP for root.

> **jerome1232 said:**
> you could also boot from a live cd and run chkroot on that disc to see if a default'ish rootkit was installed.

Can you elaborate on that a little more, probably a document.

---

### Post by EnGorDiaz on 2008-09-13
i suggest as someone else said put a non priviledged user into the ssh group

---

### Post by tarun.winlin on 2008-09-13
Thanks for all the great inputs that I got from you guys. Because of what happenned to me I am going to implement the following security features for my OpenSSH server as of now:

Securing SSH Server:
1) Strong Password, Custom user name.
2) Disable the 'root' user
3) Install security updates
4) Create a limited account user for SSH
5) Change the default SSH port
6) Disabling PasswordAuthentication and enabling PubKeyAuth using RSA keys.
7) Allow hosts only limited attempts at logging in - Using denyhosts and fail2ban
8) Set SSH to only respond to certain IP's and generate system specific keys - use /etc/hosts to only accept ssh connections from your IP at work

I have already changed my root password to something that is 22 characters in length & pretty strong my any standards - even I take around 1min to type it ;-)

I disabled the 'root' user after changing the password using the command 'sudo passwd -l root'

Installed security updates, that was something I already had covered.

I created a limited non-sudo user 'sshuser1' assigned to group 'sshgroup' & only that group allowed to ssh into the box.

Changed the default SSH port from 22 to 50,001. That brings another questions, I have VNC server running on port 11176, I want to disable it, do not use it anymore, but I still want to keep the software - How can I disable only the VNC server listening on the port, but still keep the software.

I am stuck on step 6 though which. I am trying to setup PubKeyAuth for my laptop which I take with me to the office from which I usually SSH into the linux box at home. Following is all I have done:

Generated RSA keys for SSH2 with 1024 bit strength. Saved the private key on my laptop & copied the public key to the linux box.

The user allowed to 'sshuser1' is the user in 'sshgroup' who is allowed to ssh into the linux box. The home directory for the ssh user is '/home/sshuser1'

Here is the long listing of the .ssh folder:
```

tarun@tarun-desktop:/home/sshuser1$ ls -al
total 32
drwxr-xr-x 3 sshuser1 sshusers 4096 2008-09-13 07:44 .
drwxr-xr-x 5 root     root     4096 2008-09-13 05:28 ..
-rw------- 1 sshuser1 sshusers 1175 2008-09-13 08:39 .bash_history
-rw-r--r-- 1 sshuser1 sshusers  220 2008-09-13 05:28 .bash_logout
-rw-r--r-- 1 sshuser1 sshusers 2940 2008-09-13 05:28 .bashrc
lrwxrwxrwx 1 sshuser1 sshusers   26 2008-09-13 05:28 Examples -> /usr/share/example-content
-rw------- 1 sshuser1 sshusers   45 2008-09-13 07:44 .lesshst
-rw-r--r-- 1 sshuser1 sshusers  586 2008-09-13 05:28 .profile
drwx------ 2 sshuser1 sshusers 4096 2008-09-13 07:05 .ssh

```

Here is the long listing of the 'authorized_keys' inside the .ssh folder
```

sshuser1@tarun-desktop:~/.ssh$ ls -la
total 16
drwx------ 2 sshuser1 sshusers 4096 2008-09-13 07:05 .
drwxr-xr-x 3 sshuser1 sshusers 4096 2008-09-13 07:44 ..
-rw-r--r-- 1 sshuser1 sshusers  396 2008-09-13 07:27 authorized_keys
-rw-r--r-- 1 sshuser1 sshusers  238 2008-09-13 07:05 authorized_keys2

```

I created that 'authorized_keys2' just to try & see if that works, because I read in some places that it worked with some guys out there.

Here is the public key in the 'authorized_keys' file above:
```

ssh-rsa
AAAAB3NzaC1yc2EAAAABJQAAAQB64iqtJlGSJmfm8MYU7qy+j7bjDMmzTEUxyGA1JfIArjv9khtb5pfRYtLdqtcWxLSFCG3E04YXXiZJJme9+ggdz8b0PZIfyOQChKSuOegEqIC5ex5uPkWjMhrWLoobKjZw2Shr29oP/lgkzxK4WLPPNDIQrHRghAxjuQHM4merKdawApmbcu3/377T9pJQQntYjj8XKR3AOAtnJRAjeCP8zsxiculi6U2j19zjSLYjlqNLWkcHbZ/mYI2F+lRj13zkc98Z+oXDBznAHGUfjcyaOuBSxg7s83yJyAmZ57szbLXpVBsuKcVSmPzkx5A/RWF9EDaMdDWHgnW3rzWPgJLx
rsa-key-20080913

```

Here is my /etc/ssh/sshd_config file:
```

# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 50001
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel VERBOSE

# Authentication:
LoginGraceTime 20
PermitRootLogin no
StrictModes no

# Allow users only in the 'sshusers' group to login using ssh
AllowGroups     sshusers

RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile      %h/.ssh/authorized_keys2

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication yes

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no


#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes

```

I have my private key corresponding to the public key on the linux box generated using Putty_gen on my laptop & loaded but whenever I try to login using RSA keys I get this error

[[IMG]http://img84.imageshack.us/img84/3361/screenrsaje4.th.png[/IMG]](http://img84.imageshack.us/my.php?image=screenrsaje4.png)

Note that when I try to ssh using PasswordAuthentication only on port 50001 it works fine, so the problem is not with port forwarding or anything, neither with the SSH deamon.

Any ideas what am I doing wrong here.

Also, 1 more questions, since, I generated the private key on my laptop, can I ssh only from my laptop. Or if I want to SSH from some other device I will have to create its private/public key pair & upload the public key to my linux box. In general the ssh server you want to login should have the public key & client should have the corresponding private key, is that hypothesis correct?

I know this one is long, but I cannot think of too many ways to make it short without removing vital information. 

Thanks again guys !! you rock..

---

### Post by cdenley on 2008-09-13
I'm not sure how to fix your public key authentication problem. I think you can list multiple public keys in your authorized_keys2 file. Perhaps you should try a linux client to make sure the server is configured correctly. Maybe there is a clue why it is failing in one of your logs. Try running these after a failed login attempt
```

tail /var/log/auth.log
tail /var/log/syslog

```
Also, you might get more information running sshd in debug mode.
```

sudo /etc/init.d/ssh stop
sudo /usr/sbin/sshd -d
sudo /etc/init.d/ssh start

```

Also, the best way to disable root is
```

sudo usermod -p ! root

```
This is the default for ubuntu. It sets an invalid password hash that will never match any password. This way, the root account is still enabled and valid, but an attacker will never be able to guess the password since there is none.

---

### Post by tarun.winlin on 2008-09-13
I deleted the 'authorized_keys' file in the home directory for the ssh user. Recreated a key on my laptop & transferred the public key again to the server

Now this is what I get when I try to login using RSA:

```
Using username "sshuser1".
Server refused our key
Using keyboard-interactive authentication.
Password:
```

---

### Post by kevdog on 2008-09-13
Hate to beat a dead drum here, but if you were using ssh in conjunction with a port knocker utility such as fwknop -- I'm fairly certain this would never have happened.

For a less elegant solution, you could have also set up a firewall (manually since firestarter just aint going to cut it), and allow only x amount of login attempts per hour.  This could also be done in conjuction with fail2ban or denyhost which act to permanently (or temporarily) alter the iptables firewall to limit access to the box.

---

### Post by tarun.winlin on 2008-09-13
I think I cracked it !! Here is how I did it.

1) Generate the keys on the server with something like 'ssh-keygen -t rsa'

2) Accept the file names it wants to use

3) Enter a strong passphrase

4) Add the pub key to the authorized_keys file with something like 'cat id_rsa.pub >> .ssh/authorized_keys'

5) Copy the private key (id_rsa) to your local windows machine (use winscp or sftp or some such tool)

6) Now open puttygen.exe

7) Under actions select "load" and load the id_rsa file

8) Enter the passphrase you set when you generated the key on the server. Puttygen will now convert the key to something that putty will understand

9) Save that file to something like 'pivatekey.ppk'

10) Now change your putty settings under "connection > SSH > auth" to use 'privatekey.ppk'

I am not sure if thats an issue with ubuntu Hardy but I could recreate this issue again & again. It looks that any public key generated by putty on windows platform is not accepted by linux. Once we generate the private key in linux & export it to windows putty it starts working.

I hope that would be helpful to someone who is trying to do this from now on !!

Administrator can you please shed some light on this ?

Also, while I am securing my SSH server can any one of you experts give me a few pointers on ways & tools to secure my Webserver & ftp server & if possible my VNC server too.

Thanks again...!!

---

### Post by CarrotRevelation on 2008-09-13
Man that's a lot of good work tarun! I hope to one day get the bawls to set up public servers and I will be referring to this post when I do.

[U]
Just to review some things I'm sure your aware of.[/U]

1. When a server presents a certificate to you, you should validate it's legitimacy.

2. Protect your .ppk & .p12 files (perhaps encrypt them). You definitely don't want these keys just lying out in the open.

3. Make sure the keys you generated are not on any blacklist.

4. FTP as you know is plaintext, so the the question is can you trust the files you download from your FTP site to your laptop? Can they crash your windows programs? Can you trust the files you upload to the server? Were they changed in transit to exploit undisclosed bugs in Linux and when you go to open it in Ubuntu, etc etc happens? Is your FTP server setup in PASV mode? You seem like the adventurous type so I would go ahead and switch to SFTP.

5. If you can you should set your website to listen on port 443 and use SSLv3 and TLS 1.0 and enable some kind of sign on.

I don't want to go to far out of scope here either, but alot of people tend to look at server and client software as two different things. To me it's all code. Both Servers/Clients need to be authenticated, validated and tested.

Here are a couple of good articles. 
[http://www.securityfocus.com/infocus/1806]("http://www.securityfocus.com/infocus/1806")
[http://searchnetworking.techtarget.com/sDefinition/0,,sid7_gci512897,00.html]("http://searchnetworking.techtarget.com/sDefinition/0,,sid7_gci512897,00.html")
[http://www.bindshell.net/papers/ftppasv]("http://www.bindshell.net/papers/ftppasv")

Best of luck and I hope you keep us updated!:D

---

### Post by kevdog on 2008-09-13
openssh keys and those created by putty (non openssh keys) are not compatible.  You need to convert your openssh generated key into a key recognized by putty.  The puttygen program can do this.

---

### Post by tarun.winlin on 2008-09-14
> **kevdog said:**
> openssh keys and those created by putty (non openssh keys) are not compatible.  You need to convert your openssh generated key into a key recognized by putty.  The puttygen program can do this.

Yes, thats what happenned when I used the private key generated on my linux server with my windows putty client. Putty converted it to putty 'like' ssh keys.
But I think, the opposite was what was not working. Ubuntu was not able to recognize the key's generated by putty & I am not aware of any command to do that conversion if any !! :-)

Thanks CarrotRevelation...encouragement is always welcome :-)

---

### Post by cprofitt on 2008-09-14
> **tarun.winlin said:**
> Considering the fact that I use a 'dyndns' service for resolving my hostname to IP, & then my host is behind a linksys router which obviously has only the 3 ports 80, 21, & 1176 open, I am amazed at that person who could hack into it so quickly.

My password too is around 7 letters including a digit, it couldn't have been that easy for someone to hack in.

I don;t know I am completely confused, but yeah my notion that there are a lot less hackers for linux than windows, is starting to change. I was using windows for about 9 years but never had such a big problem. I have been running this linux box only for the last 3 days & here I am.

With three open ports and a weak seven character password I am not shocked that you were hacked.

Any 'box' you allow the 'wild' internet to touch should have a firewall on it. I prefer to setup incoming rules to match the holes on the firewall and I also prefer to block all traffic leaving the box on any other port as well.

As for passwords -- I use a password with a minimum of fifteen characters.

As an FYI from a person who also switched from Windows to Linux -- Linux is not 'more' secure than Windows... it is just more secure by default. Once you start loading up services it becomes vulnerable unless you take security precautions.

---

### Post by tarun.winlin on 2008-09-15
> **tarun.winlin said:**
> 
Also, while I am securing my SSH server can any one of you experts give me a few pointers on ways & tools to secure my Webserver & ftp server & if possible my VNC server too.
Thanks again...!!

Anyone please ?

I have read about tunneling all my traffic ftp, VNC etc.. using SSH. But could not fin much documentation on it. Can anyone point me towards that documentation.

---

### Post by cdenley on 2008-09-15
> **tarun.winlin said:**
> Anyone please ?

I have read about tunneling all my traffic ftp, VNC etc.. using SSH. But could not fin much documentation on it. Can anyone point me towards that documentation.

SSH tunneling is easy. If you want to connect to port 5900 on your server, use this command from the client
```

ssh -L 5900:127.0.0.1:5900 myuser@myhost

```
The first port number is the one the client will bind to locally. The host and second port is the one you want to connect to on the server side. You can tunnel to any host on your server's network. Once the tunnel is created, simply connect to 127.0.0.1:5900 on your client.

If you want to secure FTP, you can configure SSL encryption. SSH tunneling might be complicated with FTP, since I think it switches to a different port for file transfers. Of course, the easy alternative would be to use SFTP/SCP, since you already have an SSH server. From windows, you could use Filezilla or WinSCP as a client.

Plain old FTP sends everything, including passwords, in plain text.

---

### Post by kevdog on 2008-09-15
WinSCP is very easy to use, and I second this recommendation.  Using WinSCP in combination with ssh keys (WinSCP uses putty style keys) is a winning solution.


Just a quick followup -- putty is one method of generating ssh keys on windows.  If communicating with a server running OpenSSH (most do), a conversion from the Openssh style key to the putty key format is needed using the putty keygen utility (a really easy process, but very painful if you are not aware that you have to actually perform this step).

Another method would be to use cygwin on windows instead of putty.  Cygwin is a linux emulator, and actually installs the Openssh utility whereby you can generate keys and work with openssh servers without the key conversion.  Some people prefer this method, so do not.  

I use both methods depending on the situation, however by adding cygwin to a windows installation, it does give you the same exact capabilities as running an openssh server on the windows box as it does the linux box.

---

### Post by tarun.winlin on 2008-09-15
> **cdenley said:**
> SSH tunneling is easy. If you want to connect to port 5900 on your server, use this command from the client
```

ssh -L 5900:127.0.0.1:5900 myuser@myhost

```


I am using putty on a windows box, I don't suppose I can use this command on that in any way.

> **cdenley said:**
> 
If you want to secure FTP, you can configure SSL encryption. SSH tunneling might be complicated with FTP, since I think it switches to a different port for file transfers. Of course, the easy alternative would be to use SFTP/SCP, since you already have an SSH server. From windows, you could use Filezilla or WinSCP as a client.

Plain old FTP sends everything, including passwords, in plain text.

Perfect, that is what I would want to do, to secure my ftp server. I have proftpd installed as my ftp server, how can I use SSL for it ?

Also, is that the only thing I can do to secure my ftp server or is there anything else I can do for it?

---

### Post by mwilliam13 on 2008-09-16
First - the topology:

firewall - smoothwall 3.0

server - Ubuntu 8.04 server running proftpd

Recently having been a victim of an unsuccessful brute force attack on my server, I have realized that I need to implement a better level of security on my server(s).  The server in question, primary service proftpd, is behind a smoothwall firewall, port forwarding ftp traffic and others defined appropriately.  Of course the smoothwall passes legit traffic as necessary and only reports on the firewall IDS log attempts to ports that are not already open.  I can then specify drop packets from these IP addresses on the firewall – all manually.  The thought I have is that I want to find in my proftpd.log contiguous attempts (probably a string of < 8\) noticing attempts using incorrect usernames, auth attempts that occur several times in an inhuman timeframe, and then add the associated public IP to the firewall at the public interface, writing a rule to drop packets from that address.  Any thoughts, or maybe motions to move in another direction?  I have used smoothwall for several years, and have upgraded many times.  I really like the interface and the functionality, but I am coming to terms with the fact that I may be outgrowing it, and may need something more advanced.

---

### Post by jerome1232 on 2008-09-16
[http://ubuntuforums.org/showthread.php?t=919472](http://ubuntuforums.org/showthread.php?t=919472)

This guide sets up a few programs to do something very similar give it a read over and see if it's what you want.

---

### Post by Penetration Testing on 2008-09-17
> **mwilliam13 said:**
> First - the topology:

firewall - smoothwall 3.0

server - Ubuntu 8.04 server running proftpd

Recently having been a victim of an unsuccessful brute force attack on my server, I have realized that I need to implement a better level of security on my server(s).  The server in question, primary service proftpd, is behind a smoothwall firewall, port forwarding ftp traffic and others defined appropriately.  Of course the smoothwall passes legit traffic as necessary and only reports on the firewall IDS log attempts to ports that are not already open.  I can then specify drop packets from these IP addresses on the firewall – all manually.  The thought I have is that I want to find in my proftpd.log contiguous attempts (probably a string of < 8\) noticing attempts using incorrect usernames, auth attempts that occur several times in an inhuman timeframe, and then add the associated public IP to the firewall at the public interface, writing a rule to drop packets from that address.  Any thoughts, or maybe motions to move in another direction?  I have used smoothwall for several years, and have upgraded many times.  I really like the interface and the functionality, but I am coming to terms with the fact that I may be outgrowing it, and may need something more advanced.

Maybe [fail2ban]("http://www.fail2ban.org/") is what you're looking for. It scans logs and blocks with IPTables.

---

### Post by tarun.winlin on 2008-09-17
Ok guys, I have done a lot of reading in the last few days & I managed to setup IPTABLES on my linux box. Here is what my IPTABLES looks as of now:

```

*filter

#  Allows all loopback (lo0) traffic and drop all traffic to 127/8 that doesn't use lo0
-A INPUT -i lo -j ACCEPT
-A INPUT -i ! lo -d 127.0.0.0/8 -j REJECT

#  Accepts all established inbound connections
-A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

#  Allows all outbound traffic
#  You can modify this to only allow certain traffic
-A OUTPUT -j ACCEPT

# Allows HTTP connections from anywhere (the normal ports for websites)
-A INPUT -p tcp --dport 80 -j ACCEPT

#  Allows SSH connections
#
# THE -dport NUMBER IS THE SAME ONE YOU SET UP IN THE SSHD_CONFIG FILE
#
-A INPUT -p tcp -m state --state NEW --dport 50001 -j ACCEPT

# Prevent SSH Deamon from Dictionary/BruteForce attacks
-I INPUT -p tcp --dport 50001 -i eth0 -m state --state NEW -m recent --set LOG

-I INPUT -p tcp --dport 50001 -i eth0 -m state --state NEW -m recent --update --seconds 60 --hitcount 4 -j DROP

#  Allows FTP connections
#
# THE -dport NUMBER IS THE SAME ONE YOU SET UP IN THE /etc/proftpd/proftpd.conf FILE
#
-A INPUT -p tcp -m state --state NEW --dport 21 -j ACCEPT

# Prevent FTP Deamon from Dictionary/BruteForce attacks
-I INPUT -p tcp --dport 21 -i eth0 -m state --state NEW -m recent --set

-I INPUT -p tcp --dport 21 -i eth0 -m state --state NEW -m recent \
 --update --seconds 60 --hitcount 4 -j DROP

# Allow ping
-A INPUT -p icmp -m icmp --icmp-type 8 -j ACCEPT

# log iptables denied calls
-A INPUT -m limit --limit 5/min -j LOG --log-prefix "iptables denied: " --log-level 7

# Reject all other inbound - default deny unless explicitly allowed policy
-A INPUT -j REJECT
-A FORWARD -j REJECT

COMMIT

```

Its still in testing phases so no issues changing anything.

I have a question about the section which is for preventing brute force/dictionary attacks against my SSH deamon, i guess its called rate limiting using iptables.

I have some questions:
1) How can I check if its working, I tried to repeatedly login into the SSH server from outside using the same IP but did not see it blocking, may be I am testing it the wrong way?
2) The configuration that I have, does it drop packets even if I have 3 successful attempt within 60Secs. So, if I try to login successfully the 4th time even if its the correct credentials it will drop the packet?
3) Once it starts to drop the packets, when would it allow me back again?

Thanks, any pointers on this would be great !!

---

### Post by tarun.winlin on 2008-09-19
Nevermind, its working now I was missing this after making changes to the iptables

iptables-restore < /etc/iptables.test.rules :-)

Did it & it works like a charm.

---

### Post by tarun.winlin on 2008-09-19
Thanks for all your guys help. 

I would always remember this place as one forum which allowed me to carry on ubuntu/linux. I am now in a position where I have completely transitioned from Windows to Linux & can run Linux standalone on my PC, all because of the help on this forum.

This is the best forum I have ever seen, so many HowTo's, so many intelligent MOD's :-)

Love u all, thanks for all your help again. Of course I would need it again time & again ;-)

---

### Post by Wickedone on 2008-09-19
> **tarun.winlin said:**
> I am using putty on a windows box, I don't suppose I can use this command on that in any way. 

Here are a couple of links on how to setup putty to tunnel traffic.  The same steps to setup a tunnel for browsing can be done with other services.  For instance if you want to setup a tunnel for the default vnc port you would replace port 80 in the instructions with 5900.

[http://vectrosecurity.com/content/view/67/26/]("http://vectrosecurity.com/content/view/67/26/")
[http://vectrosecurity.com/content/view/68/26/]("http://vectrosecurity.com/content/view/68/26/")

> **tarun.winlin said:**
> Perfect, that is what I would want to do, to secure my ftp server. I have proftpd installed as my ftp server, how can I use SSL for it ?

Also, is that the only thing I can do to secure my ftp server or is there anything else I can do for it?

I suggest blocking incoming connections to all ports except SSH which you have setup with key based authentication.  That way the services are secure and can be accessed from the local machine or via a SSH tunnel.  As mentioned above you can use putty to create a tunnel to just about any service just by changing the port number.

Don't allow secure connections to ftp/website/vnc/etc.  They are too easy to dictionary hack.  To put up as many obstacles as you can only allow a connection to the machine over a SSH with a strong password protected key.  

I am currently using ufw for my firewall and I like it so far.  I used to be a shorewall guy, which is also good.

For example I only allow explicit connection to the machine.

```
sudo ufw enable
sudo ufw logging on
sudo ufw default deny // deny all connections by default
sudo ufw allow from 192.168.0.x to any port 22 // insert your work ip and ssh port here
```

Done... thats it.  You now have a pretty strong firewall, you can make it stronger by disallowing outgoing connections by default, unfortunately ufw doesn't allow this currently.  Besides if you use the box yourself trying to enter every connection you want to allow would likely end up being a full time job.  It really is only useful on a dedicated server that will only connect to a few services IE a MySQL database in the backend.  Also that last rule is a very good practice.  By only allowing SSH connections from IP addresses you trust you pretty much take out the enemies ability connect to the box.  (Of coarse if they are hardcore they will sniff packets and find what IP's you connect to it with then try spoofing which can also be prevented but then the war will just escalate to nuclear weapons ;-) and we wouldn't want that now would we?) The catch 22 is you won't be able to connect to your box from your favorite coffee shop's wifi.  (well unless you add it but that would kind of defeat the trust relationship.)

I normally have three terminals open on my box when logged in.  

```
tail -f -s3 /var/log/messages  // this will show connections being blocked by the firewall
tail -f -s3 /var/log/auth.log // displays who's trying to log in
tail -f -s3 /etc/hosts.deny  // if you use denyhosts this will pickup a address or two a day
```

Also make certain to use a port scanner like nmap on the box from an external connection.  You can read up on all the commands but a good starting point is:

```
nmap -T Aggressive -P0 -sV -p 1-65535 192.168.0.x
```

W

---

### Post by tarun.winlin on 2008-09-19
> **Wickedone said:**
> 
I suggest blocking incoming connections to all ports except SSH which you have setup with key based authentication.  That way the services are secure and can be accessed from the local machine or via a SSH tunnel.  As mentioned above you can use putty to create a tunnel to just about any service just by changing the port number.  


Thanks for the informative post but if I want my ftp server to be accessible by everyone in that case I will have to open up port 21 right, or can I still work with just one port open for SSH?

BTW I am using IPTABLES, I think that's ultimate when it comes to flexibility in configuration, its just like configuring an extended ACL on a cisco router :-)

---

### Post by Wickedone on 2008-09-20
> **tarun.winlin said:**
> Thanks for the informative post but if I want my ftp server to be accessible by everyone in that case I will have to open up port 21 right, or can I still work with just one port open for SSH?

BTW I am using IPTABLES, I think that's ultimate when it comes to flexibility in configuration, its just like configuring an extended ACL on a cisco router :-)

If you want to allow everyone access to FTP the command for ufw is:
```
sudo ufw allow ftp
```

Although when you open FTP you are giving an attacker another avenue to pursue.  Many machines have been compromised by FTP.  If you really need it then I suggest only allowing anonymous logins.  You don't want to use it for any sensitive files.  

You can use SSH for transferring files that are sensitive using SCP or SFTP.  A good client for Windows is WinSCP.  It allows key based authentication and has a batch mode to allow you to work with files in numerous directories.  Or if you are dealing with large or lots of files or a slow link you can setup your batch processing and do other things while it processes.

Also if you only need to allow some users access to sensitive files via FTP but don't want to allow them shell access that can be achieved as well by jailing SSH .  

Some links on setting up SSH so it allows transfers but denies shell access:
[http://ubuntuforums.org/showthread.php?t=128206]("RSSH Method")
[http://forums.theplanet.com/index.php?showtopic=46724]("SCPONLY Method")  ** note SCP and RSSH are both in the repos no need to compile...

IPTables are hardcore.  It is the ultimate in flexibility but you have to pay a heavy administration price.  As I mentioned I default to denying all traffic, but often open access for a service for brief periods.  UFW has made administration simple.  If your not a firewall god and don't really need an elaborate configuration UFW is the way to go.

---

### Post by tarun.winlin on 2008-09-21
> **Wickedone said:**
> 
I suggest blocking incoming connections to all ports except SSH which you have setup with key based authentication.  That way the services are secure and can be accessed from the local machine or via a SSH tunnel.  As mentioned above you can use putty to create a tunnel to just about any service just by changing the port number.

I tried that last night, but could not get it to work.
Used the following URL to setup putty for a tunnel to my SSH server (ubuntu box):
[http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_16126](http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_16126)
My VNC server is configured to accept connections on port 11176, but my iptables does not allows any traffic on that port. Now if I am coming through an SSH tunnel, I should not need to open port 11176 on the iptables firewall or my linksys router right?

```
7f:28:0e:08:00 SRC=59.178.56.20 DST=192.168.1.101 LEN=60 TOS=0x00 PREC=0x00 TTL=62 ID=14274 DF PROTO=TCP SPT=29399 DPT=11176 WINDOW=5840 RES=0x00 SYN URGP=0

```

Above is the log that I get, I confirmed that I had to open port 11176 because when I disable iptables using 'iptables -F' I am able to make that VNC work through SSH tunnel, but when I enable it back, the VNC through SSH stops working :-(

If I have to open port 11176 on my linux box, then what is the use of SSH tunnelling, I want to keep only SSH port 50001 open on my linux box & all other services I will access through SSH Tunnel.

---

### Post by kevdog on 2008-09-21
Can you tell me how you are opening up the ssh port with iptables?  Are you sure your ssh server is listening on that port?  What command are you using to tunnel your client?

Once again Im just asking for some more information.

---

### Post by tarun.winlin on 2008-09-21
> **kevdog said:**
> Can you tell me how you are opening up the ssh port with iptables?

I have no problems logging in using SSH on port 50001, but since you asked, here is the iptables entry that opens port 50001
```
# THE -dport NUMBER IS THE SAME ONE YOU SET UP IN THE SSHD_CONFIG FILE
#
-A INPUT -p tcp -m state --state NEW --dport 50001 -j ACCEPT

```

> **kevdog said:**
>   Are you sure your ssh server is listening on that port?

Again, as I mentioned SSH server in itself just works fine with port 50001, for your satisfaction here is the excerpt from the /etc/sshd_config file
```
# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 50001
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
ListenAddress 0.0.0.0
Protocol 2
```

> **kevdog said:**
>  What command are you using to tunnel your client?
I am using my putty application on a windows laptop, & I configured it as per the instructions on [this]("http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_16126") link 


> **kevdog said:**
> Once again Im just asking for some more information.

No problems at all, I would be happy to provide as much information as you want, until you want to help me ;-)

---

### Post by tarun.winlin on 2008-09-21
To clarify it a little more about using the SSH client software on windows, here is what I do.

Create a tunnel using
source port - 2021 (Any random port)
destination - tarunlohumi.homeip.net:11176 <--Port VNC is listening on
Select 'Local' & 'Auto' On those radios button's below that.

Then using VNC Viewer I connect to localhost:2021, but it gives me this error instead of opening a session
[[IMG]http://img129.imageshack.us/img129/6317/erroroi1.th.jpg[/IMG]](http://img129.imageshack.us/my.php?image=erroroi1.jpg)[[IMG]http://img129.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

---

### Post by tarun.winlin on 2008-09-21
Ok, update, SSH tunnelling for HTTP traffic works.

Any suggestions please, its confusing me now :-(

---

### Post by kevdog on 2008-09-21
What do you need to know?  

Does your firewall also keep open established connections?

It may have been the way you were configuring your client?

---

### Post by Wickedone on 2008-09-21
Tarun,

It is easy to get confused when using tunnels, they are inherently more complex.  You do not need to open any port on your firewall except your SSH port.  But you must remember that the applications you use needs to be configured to use the SSH tunnel.  Here is a link to setup Putty and TightVNC viewer on Windows.  [http://home.chattanooga.net/~john/Putty-Tunnel/putty-tunnel.html]("http://home.chattanooga.net/~john/Putty-Tunnel/putty-tunnel.html")  

That is the software I have been using for years and it works for me.

---

### Post by kevdog on 2008-09-21
I looked at that page -- fairly accurate.

In the last step it could be 

localhost:4
or
localhost::5604

The first is the relative port number (in relation to the 5600 default, the second is the absolute port number)

---

### Post by tarun.winlin on 2008-09-22
> **Wickedone said:**
> Here is a link to setup Putty and TightVNC viewer on Windows. 

I am using putty to setup the SSH session & VNC Viewer to connect to the VNC server.

I thought that should be ok or do I need to use tight TightVNC only?

---

### Post by kevdog on 2008-09-22
Any VNC product (VNC, tightVNC, ultraVNC) will work.  I know there are subtle differences in the products, however all are built from the same foundation and hence interoperable.

---

