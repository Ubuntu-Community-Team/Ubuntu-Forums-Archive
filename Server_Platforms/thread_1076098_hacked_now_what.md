---
title: "hacked now what?"
date: 2009-02-21
forum: Server Platforms
---

### Post by D0T-C0M on 2009-02-21
I was hacked and I have all the files the guy used. I have all the .bach_history. I disconnected this hacked server from the net and brought my backup online and I need to know what to do next in order to determine the method and possible ip information.

The guy had root access. He installed an irc bot with alot of nasty scripts on Feb16th in /root/.ssh . He also installed plesk on the 18th. In "/root/.ssh" there was a funny sub directory called " -- " (2 dashes). It was tricky to access this directory because you needed to run "cd /--/ " to get inside. In there was a whack of files and I can only speculate at this time that it is a rootkit. 

The Ubuntu 8.04 server is still running to preserve data. All I need is a plan of attack. I had enabled the root account during the Ubuntu installation nad I had no other users set, just one normal user(me) and the root(me) account was on this machine. 

thanks everyone.

---

### Post by D0T-C0M on 2009-02-21
After looking over my auth.log I have hundreds of entries of failed password attempts. I think that the sshd server was the method that was used to gain access.

---

### Post by R.Bucky on 2009-02-21
Yet another reason to have a strong password. Make the next password a solid one...

---

### Post by D0T-C0M on 2009-02-21
my password was 8 characters with numbers and upper and lower case letters.

---

### Post by knight187 on 2009-02-21
I always change the default port that sshd runs on and / or add an iptables rule to restrict access to sshd from all but a few ip's

iptables -A INPUT -p tcp -s SOURCE.IP --dport 22 -j ACCEPT
iptables -A INPUT -j DROP

Cheers.

---

### Post by D0T-C0M on 2009-02-21
> **knight187 said:**
> I always change the default port that sshd runs on and / or add an iptables rule to restrict access to sshd from all but a few ip's

iptables -A INPUT -p tcp -s SOURCE.IP --dport 22 -j ACCEPT
iptables -A INPUT -j DROP

Cheers.

thanks for the tip. My nat router is now configured to only allow local connections to my servers ftp ports.

I have all the exploit files that he used. Do I submit them anywhere like a virus company or something like that? I have his websites where he hosts his files. He hides his files by renaming changing the extension. For example he downloaded a file called a.gif and then untarred it. This created a directory consisting of 2 dashes --  , You couldn't use cd -- so you had to use cd ./--/ to get inside. Its a good thing he didn't erase his .bash_history.

---

### Post by amauk on 2009-02-21
you can also use denyhosts (it's in the repos)
it monitors /var/log/auth.log and bans IPs that try to brute force passwords

for a server, an 8 letter password on your account is low
(just for reference, mine is 21 chars using upper, lower, numeric & symbols)

long passwords don't have to be difficult to remember

Sonic3>MarioAllStars
or whatever, something you'll remember
(and no, that's not mine)

Strong password on user account, plus public/private key auth is the way to go

also, evaluate whether you need ssh open to everybody, or just a select few IPs

---

### Post by inphektion on 2009-02-21
Also take a look at Fail2Ban.  I just installed it a bit ago and works well.  After x (you configure) failed attempts it will ban the IP for XX (you decide) amount of time. 

This will prevent anyone from being able to run "hundreds of entries of failed password attempts".  Which is a nice deterrence.

---

### Post by police512 on 2009-02-21
ok that sounds like a good program but what happens if the ip address changes auto like mine does??
my ip address  changes all the time auto without me doing anything...

---

### Post by R.Bucky on 2009-02-21
I have found that [IPlist]("http://sourceforge.net/projects/iplist") is a solid way to go, when denying IP's. You can change/add lists from which to block, most of which pull from Bluetack. Bluetack seems to be on top of it with hackers and such. Also, I create and maintain my own blocked_list.gz for people that I find "wandering around." Also, you can block countries by their range by visiting this site - [http://blockacountry.com/]("http://blockacountry.com/")

---

### Post by inphektion on 2009-02-21
> **police512 said:**
> ok that sounds like a good program but what happens if the ip address changes auto like mine does??
my ip address  changes all the time auto without me doing anything...

it doesn't matter what your IP is.  just who is repeatedly hitting you.  You use fail2ban per service.  I have mine on ssh and vsftpd.  I didn't set it up for apache.

---

### Post by D0T-C0M on 2009-02-23
Thanks guys for all your help. I installed fail2ban and I am using it to monitor my sshd and proftpd connections.  Is there any good programs to monitor users that have actual shell access?

---

### Post by PilotJLR on 2009-02-23
Reformatting and reinstalling the OS are the most ideal steps now... you can backtrack and clean up based on the .bash_history, but the only way to be SURE the machine is clean is to reinstall, and then restore data from backups (that are known to be clean).

I've had more than one hacker get stopped by denyhosts, despite having my ssh server on an arbitrary port number.

---

