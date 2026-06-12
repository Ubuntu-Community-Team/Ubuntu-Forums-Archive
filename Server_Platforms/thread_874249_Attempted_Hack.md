---
title: "Attempted Hack?"
date: 2008-07-29
forum: Server Platforms
---

### Post by TreeFinger on 2008-07-29
Is this a sign of an attempted hack?

```

sshd:
    Authentication Failures:
       unknown (24-247-60-242.static.aldl.mi.charter.com): 129 Time(s)
       root (24-247-60-242.static.aldl.mi.charter.com): 15 Time(s)
       adm (24-247-60-242.static.aldl.mi.charter.com): 1 Time(s)
       apache (24-247-60-242.static.aldl.mi.charter.com): 1 Time(s)
       bin (24-247-60-242.static.aldl.mi.charter.com): 1 Time(s)
       daemon (24-247-60-242.static.aldl.mi.charter.com): 1 Time(s)
       ftp (24-247-60-242.static.aldl.mi.charter.com): 1 Time(s)
       games (24-247-60-242.static.aldl.mi.charter.com): 1 Time(s)
       gopher (24-247-60-242.static.aldl.mi.charter.com): 1 Time(s)
       halt (24-247-60-242.static.aldl.mi.charter.com): 1 Time(s)
       lp (24-247-60-242.static.aldl.mi.charter.com): 1 Time(s)
       mail (24-247-60-242.static.aldl.mi.charter.com): 1 Time(s)
       mailnull (24-247-60-242.static.aldl.mi.charter.com): 1 Time(s)
       named (24-247-60-242.static.aldl.mi.charter.com): 1 Time(s)
       news (24-247-60-242.static.aldl.mi.charter.com): 1 Time(s)
       nfsnobody (24-247-60-242.static.aldl.mi.charter.com): 1 Time(s)
       nobody (24-247-60-242.static.aldl.mi.charter.com): 1 Time(s)
       operator (24-247-60-242.static.aldl.mi.charter.com): 1 Time(s)
       rpc (24-247-60-242.static.aldl.mi.charter.com): 1 Time(s)
       rpcuser (24-247-60-242.static.aldl.mi.charter.com): 1 Time(s)
       rpm (24-247-60-242.static.aldl.mi.charter.com): 1 Time(s)
       shutdown (24-247-60-242.static.aldl.mi.charter.com): 1 Time(s)
       smmsp (24-247-60-242.static.aldl.mi.charter.com): 1 Time(s)
       sshd (24-247-60-242.static.aldl.mi.charter.com): 1 Time(s)
       sync (24-247-60-242.static.aldl.mi.charter.com): 1 Time(s)
       uucp (24-247-60-242.static.aldl.mi.charter.com): 1 Time(s)
    Invalid Users:
       Unknown Account: 129 Time(s)

```

that is an unknown ip (domain name ??) to me..

Wow there is more from different IPs.. All I run is a lonely samba share for my 2 computers. 

```

 sshd:
    Authentication Failures:
       unknown (58.240.48.27): 2756 Time(s)
       unknown (61.246.218.71): 671 Time(s)
       root (58.240.48.27): 165 Time(s)
       unknown (201.12.126.182): 28 Time(s)
       mail (58.240.48.27): 11 Time(s)
       adm (61.246.218.71): 8 Time(s)
       apache (58.240.48.27): 7 Time(s)
       ftp (61.246.218.71): 7 Time(s)
       mail (61.246.218.71): 7 Time(s)
       news (58.240.48.27): 7 Time(s)
       nobody (58.240.48.27): 7 Time(s)
       sshd (58.240.48.27): 7 Time(s)
       apache (61.246.218.71): 6 Time(s)
       games (58.240.48.27): 5 Time(s)
       adm (58.240.48.27): 4 Time(s)
       ftp (58.240.48.27): 4 Time(s)
       smmsp (58.240.48.27): 4 Time(s)
       sync (58.240.48.27): 4 Time(s)
       bin (58.240.48.27): 2 Time(s)
       lp (58.240.48.27): 2 Time(s)
       operator (58.240.48.27): 2 Time(s)
       rpm (58.240.48.27): 2 Time(s)
       daemon (58.240.48.27): 1 Time(s)
       ftp (201.12.126.182): 1 Time(s)
       gopher (58.240.48.27): 1 Time(s)
       halt (58.240.48.27): 1 Time(s)
       mailnull (58.240.48.27): 1 Time(s)
       named (58.240.48.27): 1 Time(s)
       nfsnobody (58.240.48.27): 1 Time(s)
       root (201.12.126.182): 1 Time(s)
       rpc (58.240.48.27): 1 Time(s)
       rpcuser (58.240.48.27): 1 Time(s)
       shutdown (58.240.48.27): 1 Time(s)
       squid (58.240.48.27): 1 Time(s)
       uucp (58.240.48.27): 1 Time(s)
    Invalid Users:
       Unknown Account: 3455 Time(s)

```

---

### Post by tamoneya on 2008-07-29
looks malicious to me.  Looks like they are brute forcing common usernames for services.

---

### Post by thedevnull on 2008-07-29
I would put a real firewall in front of your machine and any internet facing services you want available outside.  Then I would set up a VPN with strong authentication to it.  

There are tons of FOSS firewalls out there like IPCop, Pfsense, Untangle, etc. that will do all of this and then some on an off an old Pentium junker..  

:guitar:

---

### Post by TreeFinger on 2008-07-29
> **thedevnull said:**
> I would put a real firewall in front of your machine and any internet facing services you want available outside.  Then I would set up a VPN with strong authentication to it.  

There are tons of FOSS firewalls out there like IPCop, Pfsense, Untangle, etc. that will do all of this and then some on an off an old Pentium junker..  

:guitar:

I'm purchasing another NIC for this machine and then I plan on setting it up as my firewall. Currently I have a hardware firewall. Could someone point me to a link to set up my firewall to block incoming connections for ssh from outside my LAN? I only ssh into my server from inside my LAN

---

### Post by tamoneya on 2008-07-30
> **TreeFinger said:**
> I'm purchasing another NIC for this machine and then I plan on setting it up as my firewall. Currently I have a hardware firewall. Could someone point me to a link to set up my firewall to block incoming connections for ssh from outside my LAN? I only ssh into my server from inside my LAN

firestarter is pretty simple and has a nice GUI.  [https://help.ubuntu.com/community/Firestarter](https://help.ubuntu.com/community/Firestarter)

---

### Post by BLTicklemonster on 2008-07-30
How the heck did you find all that?

---

### Post by lisati on 2008-07-30
> **TreeFinger said:**
> Is this a sign of an attempted hack?

```

sshd:
    Authentication Failures:
       unknown (24-247-60-242.static.aldl.mi.charter.com): 129 Time(s)
       root (24-247-60-242.static.aldl.mi.charter.com): 15 Time(s)
       adm (24-247-60-242.static.aldl.mi.charter.com): 1 Time(s)
       apache (24-247-60-242.static.aldl.mi.charter.com): 1 Time(s)
       bin (24-247-60-242.static.aldl.mi.charter.com): 1 Time(s)
       daemon (24-247-60-242.static.aldl.mi.charter.com): 1 Time(s)
       ftp (24-247-60-242.static.aldl.mi.charter.com): 1 Time(s)
       games (24-247-60-242.static.aldl.mi.charter.com): 1 Time(s)
       gopher (24-247-60-242.static.aldl.mi.charter.com): 1 Time(s)
       halt (24-247-60-242.static.aldl.mi.charter.com): 1 Time(s)
       lp (24-247-60-242.static.aldl.mi.charter.com): 1 Time(s)
       mail (24-247-60-242.static.aldl.mi.charter.com): 1 Time(s)
       mailnull (24-247-60-242.static.aldl.mi.charter.com): 1 Time(s)
       named (24-247-60-242.static.aldl.mi.charter.com): 1 Time(s)
       news (24-247-60-242.static.aldl.mi.charter.com): 1 Time(s)
       nfsnobody (24-247-60-242.static.aldl.mi.charter.com): 1 Time(s)
       nobody (24-247-60-242.static.aldl.mi.charter.com): 1 Time(s)
       operator (24-247-60-242.static.aldl.mi.charter.com): 1 Time(s)
       rpc (24-247-60-242.static.aldl.mi.charter.com): 1 Time(s)
       rpcuser (24-247-60-242.static.aldl.mi.charter.com): 1 Time(s)
       rpm (24-247-60-242.static.aldl.mi.charter.com): 1 Time(s)
       shutdown (24-247-60-242.static.aldl.mi.charter.com): 1 Time(s)
       smmsp (24-247-60-242.static.aldl.mi.charter.com): 1 Time(s)
       sshd (24-247-60-242.static.aldl.mi.charter.com): 1 Time(s)
       sync (24-247-60-242.static.aldl.mi.charter.com): 1 Time(s)
       uucp (24-247-60-242.static.aldl.mi.charter.com): 1 Time(s)
    Invalid Users:
       Unknown Account: 129 Time(s)

```that is an unknown ip (domain name ??) to me..

<snip>
I looked 24-247-60-242 up at  [http://whatismyipaddress.com](http://whatismyipaddress.com) and it *appears* to be someone who is in Hudsonville, MI (or at least using a service that connects through there) - you might want to consider reporting this.

---

### Post by DocWu on 2008-07-30
Did this just start or is it something that you just noticed?

The internet is a pretty ugly place with thousands of compromised machines out there just trying to find more to infect. What you see looks pretty typical to me. Most people never realize it's going on, though.

Their are loads of botnets out there that most of their time is spent probing for more open machines to root and add their trojan to. That's how they get so many in the botnet.

A firewall is good, even being behind NAT helps. You can see a non-obvious username is important, as is a complex password. Of course, Linux is usually more secure, too. Odds are good, even if they got in, their rootkit wouldn't work.

---

### Post by TreeFinger on 2008-07-30
Morning all and thank you for the replies.

I believe my password ended up getting cracked. What should I do about this? I have to change the password of course.. but I'm guessing that another account may have already been created. 

I'm guessing I need to figure out what accounts, if any, are not suppose to be there?

Should I backup any configuration files I need and just reinstall?

I'm sort of paranoid and I'd like to make sure my system is secure, without a doubt!

---

### Post by Joeb454 on 2008-07-30
If an account was creating there should be a home folder for it. You could try running ```
ls /home
``` to see if there are any usernames you haven't created

---

### Post by Dr Small on 2008-07-30
> **Joeb454 said:**
> If an account was creating there should be a home folder for it. You could try running ```
ls /home
``` to see if there are any usernames you haven't created
That isn't always the case.
Try:
```
cat /etc/passwd
```

And look around for anything that might be suspicious.

---

### Post by TreeFinger on 2008-07-30
I'm just going to do a new install, backing up any important configuration files I need.

Who knows what has gone on and I'm sure if it is an experienced hacker he wouldn't have left a home dir :p

I know how the hacker got in.. so I'll be able to fix that after a clean install.

---

### Post by jdavis on 2008-07-30
Just a quick note on this. 

I have used tools like [fail2ban]("http://www.fail2ban.org/") and [denyhosts]("http://denyhosts.sourceforge.net/") in the past, which check various system log files (ssh, apache, ftp, samba, etc) for failed login attempts, and ban the IP address from one (or all) system services after a set number of failures.

fail2ban adds iptables rules, and denyhosts adds malicious IP's to '/etc/hosts.deny'. Both are available through the Ubuntu repositories.

Jonathan

---

### Post by gyterpena on 2008-07-30
Move ssh to different port if possible.

---

### Post by jdavis on 2008-07-30
> **gyterpena said:**
> Move ssh to different port if possible.

Which can be done by editing the 'Port' value in: /etc/sshd_config and then restarting sshd.

```
sudo vim /etc/sshd_config
```
change the port value then restart the service:
```
/etc/init.d/sshd restart
```

Although some might say that altering ports is really security through obscurity, and wouldn't deter a knowledgable or determined malicious hacker.

---

### Post by BLTicklemonster on 2008-07-30
I can imagine that this thread is getting a lot of looks from people like myself who are wondering:

How can I look to see the same information (on my system) as is listed in the original post?

From that point, what steps can I take to stay on top of this?

Are there any useful links that can be provided for these people?

(sorry to hijack this thread, but as long as it's here, it might as well have some solution type links, eh?)

Thank you.

---

### Post by TreeFinger on 2008-07-30
> **BLTicklemonster said:**
> I can imagine that this thread is getting a lot of looks from people like myself who are wondering:

How can I look to see the same information (on my system) as is listed in the original post?

From that point, what steps can I take to stay on top of this?

Are there any useful links that can be provided for these people?

(sorry to hijack this thread, but as long as it's here, it might as well have some solution type links, eh?)

Thank you.

I'm not sure how this is done on Ubuntu. I am running centOS 5.1 and i get security messages through 'mail'.

Not sure if it is done through SELinux or some other daemon.

Just automatically has done it since I installed.

---

### Post by MJN on 2008-07-30
> **Joeb454 said:**
> If an account was creating there should be a home folder for it. You could try <snip>
 
Whoa there!
 
If a machine has been compromised you cannot trust **_anything_** that's on it as you have no idea of what might have been changed.
 
The only 'solution' is to rebuild from your backups. If you don't have secure backups then hand-pick what you need from this machine - pure non-binary files and, in the case of configuration, each manually checked to ensure integrity.
 
There is no safe alternative. Period.
 
Mathew

---

### Post by ChumleyEX on 2008-07-30
My personal solution would be to make sure you get a router and lock down the network with that. Don't foward any ip's via the router and your safe. (assuming the DMZ if off)

Also make sure you have a pretty nifty password, nothing that would be in the dictionary. I use a mix of numbers and words, so a dictionary attack wouldn't work on mine, only a bruteforce. I have people attacking my computer all of the time and between my router, a good password, and fail2ban they haven't gotten a damn thing. 

The only ports open on my router are 22(ssh) for tunneling all my other ports such as the vnc's, 21(proftp) you know what that is, 80(http), 25 and 110 for email server.



For those that don't know (which I'm sure are the minority), ssh and the other services has log files that keep track of everything. All the log files are in /var/log and thats where you should look for the crackers foot prints. 

ssh has /var/log/auth.log
proftp /var/log/secure
apache has several and are all in /var/log/apache2

There are several more and are usually outlined in the .conf file of there program in question.

---

### Post by TreeFinger on 2008-07-30
The logs I posted were created by the 'logwatch' application I believe.

---

### Post by StickyStyle on 2008-07-30
> **BLTicklemonster said:**
> I can imagine that this thread is getting a lot of looks from people like myself who are wondering:

How can I look to see the same information (on my system) as is listed in the original post?

From that point, what steps can I take to stay on top of this?

Are there any useful links that can be provided for these people?

(sorry to hijack this thread, but as long as it's here, it might as well have some solution type links, eh?)

Thank you.

These are kept in /var/log/auth.log, install logwatch to see all the people trying to crack your passwords.

If you must have internet facing SSH **these scans will always happen non-stop**, it's just a fact of todays internet.  Follow the following precautions...
1. Limit the users that can SSH in with AllowUsers in /etc/ssh/sshd_config
2a. Use strong passwords on the users that are in AllowUsers
2b (better). Only allow public key authentication by setting 'PasswordAuthentication no' and 'ChallengeResponseAuthentication no' in sshd_config (make sure you setup a public key first, our you just locked yourself out).
3. you can change the port, 2222 is commonly used, and is often scanned in addition to 22; so pick another.


The OP is right in that he needs to reinstall if he thinks his PW was cracked, once a system is compromised you cannot trust the output of **any** program.  So cat /etc/passwd may look fine, but if the hacker replaced 'cat' with his version that may not show you the new accounts he created as it may filter those lines.

---

### Post by windependence on 2008-07-31
StickyStyle is exactly right on this:

> If you must have internet facing SSH these scans will always happen non-stop, it's just a fact of todays internet. Follow the following precautions...

If you are shocked by this you shouldn't be. My web servers are hit thousands of times daily by brute force attempts like this. Note I said "attempts" because attempts are logged (and sometimes successful logons). I personally don't think he has been hacked, there was just some attempts made, but of course without looking at some more stuff I would not know.

The OP said he had a hardware firewall. This is the best way to protect his network, it just isn't configured correctly. All the steps above in Sticky's post are good ones. First, however, the firewall should be locked down. No need for a software firewall IMHO.

-Tim

---

### Post by magicplayr2000 on 2008-07-31
Once you get your server up and running again, I highly recommend installing denyhosts.  My server blocks out requests after 8 failed attempts, and I've got my computer set up to email me nightly with logwatch reports, which show new denied IPs.  I probably block 5 or 6 new ones a day.  If nothing else it'll keep your server from having to process every single one of those requests.

---

### Post by ChumleyEX on 2008-07-31
I decided to try denyhosts, which was super easy to install 

> sudo apt-get install denyhosts

I then went in and edited /etc/denyhosts.conf

I made an email accout for it called security guard and put in all the info needed. I didn't see where you set the value for retrys though. 


Does this work with more then SSH?

---

### Post by Kolipoki on 2008-07-31
> **StickyStyle said:**
> ...
1. Limit the users that can SSH in with AllowUsers in /etc/ssh/sshd_config
...

I didn't find that line in my sshd_config. Do I need to add it as a new line? If so, would this be the correct way?:
```
AllowUsers 5
```(Where 5 is the ammount of users)

---

### Post by MJN on 2008-07-31
Check the SSHD config man page:

```
man sshd_config
```

Mathew

---

### Post by ChumleyEX on 2008-08-01
These just started in my auth.log file after isntalling denyhosts. Is this ok?


> Aug  1 08:17:01 sage CRON[1048]: pam_unix(cron:session): session closed for user  root
Aug  1 08:18:01 sage CRON[1055]: pam_unix(cron:session): session opened for user  root by (uid=0)
Aug  1 08:18:01 sage CRON[1055]: pam_unix(cron:session): session closed for user  root
Aug  1 08:20:01 sage CRON[1065]: pam_unix(cron:session): session opened for user  www-data by (uid=0)
Aug  1 08:20:03 sage CRON[1065]: pam_unix(cron:session): session closed for user  www-data


---

### Post by StickyStyle on 2008-08-01
> **ChumleyEX said:**
> These just started in my auth.log file after isntalling denyhosts. Is this ok?

Those are cron jobs running, they where most likely all ready there.
If I had to guess I would say the www-data one is PHP doing it's session cleanup, not sure what root is doing.

There are quite a few places you may have to look to figure out all the scheduled jobs your box is running when you don't know what something is, which kind of sucks.

This is the system wide cron scripts
/etc/cron.d/

These are user crontabs created when you do $crontab -e
/var/spool/cron/crontabs (these will be named for the user that created the crontab)

These are run though anacron, its config file is /etc/crontab
/etc/cron.hourly/
/etc/cron.daily/
/etc/cron.monthly/

All the files in these folders are text files, in the normal crontab format.

---

### Post by Kolipoki on 2008-08-05
I had been following this thread since the beginning. Quite useful and interesting. As a result I checked my auth log and more or less found the same lines regarding the cron jobs. 

However, among those, I found these:```
Aug  1 06:25:02 servername sudo:     root : TTY=unknown ; PWD=/ ; USER=administrator ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/use_http_proxy
Aug  1 06:25:02 servername sudo: pam_unix(sudo:session): session opened for user administrator by (uid=0)
Aug  1 06:25:02 servername sudo: pam_unix(sudo:session): session closed for user administrator
Aug  1 06:25:02 servername sudo:     root : TTY=unknown ; PWD=/ ; USER=administrator ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/host
Aug  1 06:25:02 servername sudo: pam_unix(sudo:session): session opened for user administrator by (uid=0)
Aug  1 06:25:02 servername sudo: pam_unix(sudo:session): session closed for user administrator
Aug  1 06:25:02 servername sudo:     root : TTY=unknown ; PWD=/ ; USER=administrator ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port
Aug  1 06:25:02 servername sudo: pam_unix(sudo:session): session opened for user administrator by (uid=0)
Aug  1 06:25:02 servername sudo: pam_unix(sudo:session): session closed for user administrator
```

If this means that I shouldn't sleep well tonight, let me know asap. Thanks for your time.

EDIT: FYI,  googling gconftool shows that it is a GUI tool but I don't have a GUI server, only Webmin and Phpmyadmin as graphical interfaces, but they shouldn't be the apps generating those lines (or Webmin is?.

---

### Post by evymetal on 2008-09-03
^
I believe that gconftool gets settings from  the gnome configuration files, it certainly doesn't need a gui.

it seems those commands have been run under sudo though, so I'd have thought it's either you or a shell script somewhere.

To be honest, if someone had really hacked in to root and you're box is relatively secure (i.e. they knew what they were doing), they would probably have removed the offending lines from /var/log/auth.log


Others have said it, but don't worry about the OP's logs, they're a standard bot that's scanning everywhere at the moment looking for people leaving default passwords etc.

when you do need to worry is when someone tries to log in as your username - then they have some knowledge of your box already...

---

### Post by windependence on 2008-09-04
....And don't use names for user names. Might as well make them guess both parts, user name and pass.

-Tim

---

### Post by schettj on 2008-09-04
sshd is one of many brute=force attack vectors these days

for sshd, disable root login, only allow specific users to sshd in (I only allow a single user) run sshd on two ports - port 22 and some other unusual port. The port 22 is for access from places that only support port 22 out for ssh (many corporations with strong firewalls) - you deny all and allow ssh in from just these ips/blocks in your firewall.

You can also disallow all text logins and only use preshared keys for extra strength.

And use fail2ban. It's a simple way to block these bozos after 3-5 attempts.

Unless your server has a huge russian, asian, middle-eastern, or african following (mine doesn't) you can also google around for "banning ip ranges by country" to find ip ranges to blacklist from such locations. Doing that will cut your ssh probes, smtp probes, and script-kiddie http probes down to nearly nothing.

---

