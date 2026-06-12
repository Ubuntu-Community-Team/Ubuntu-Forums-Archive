---
title: "h4x0rz all up in my machine"
date: 2010-02-24
forum: Security
---

### Post by oiper on 2010-02-24
Geez I hate posting this. I have this little nettop box, an Acer Revo, that I use for Boxee/Hulu Desktop with my tv. It's been a fairly enjoyable setup for months, until two mornings ago.

**The first strike**
Before work I poured myself some cereal, wandered over to the couch, plopped down and powered on the tv. After the set warmed up, a header image for some banking/something-another website made it from my screen, into my retinas, and slowly turned my otherwise uneventful morning into me chocking on a mouth full of Honey Nut Os as I lept over my coffee table and slammed the off button on my cable modem.

I clean up the Nut Os that I knocked on the floor and systematically change every password on my networked machines (Revo and two *laptops*). I check my router, disable my ssh port forwarding rule, kill remote admin access, change passwords, MAC addr whitelist my wifi connected machines just in case it's a local job.

I read through all running processes, check my bash history, look for screen sessions, and so on. Finally I decide that I must have been brute forced, either on my ssh port or perhaps even directly on my router. My laptops should have been, and seemed to still be, in sleep mode since that night.

**The second strike**
So tonight I'm watching a South Park episode (a show I hate to love), about to cut out for the night, when the Boxee menu pops up. I look at the remote and back at the tv; for just a moment I think that perhaps the mouse shifted slightly on the carpet and caused the menu to activate. Then Boxee stops the video, navigates the menu a few clicks, pulls up the exit menu and closes itself. 

Dang it all. I stick another 10 point landing as I hit the modem again. Now I'm confused and feel violated. I've showered 12 times but can't seem to get clean. I don't know where this person is getting access to my system.

Any suggestions on what to check? At this point I'm going to backup whatever settings I can and do a fresh install, but the question of how is going to drive me nuts. I'd like to review the issue before formatting my Revo.

---

### Post by detroit/zero on 2010-02-25
> **oiper said:**
> Geez I hate posting this. I have this little nettop box, an Acer Revo, that I use for Boxee/Hulu Desktop with my tv. It's been a fairly enjoyable setup for months, until two mornings ago.

**The first strike**
Before work I poured myself some cereal, wandered over to the couch, plopped down and powered on the tv. After the set warmed up, a header image for some banking/something-another website made it from my screen, into my retinas, and slowly turned my otherwise uneventful morning into me chocking on a mouth full of Honey Nut Os as I lept over my coffee table and slammed the off button on my cable modem.

I clean up the Nut Os that I knocked on the floor and systematically change every password on my networked machines (Revo and two *laptops*). I check my router, disable my ssh port forwarding rule, kill remote admin access, change passwords, MAC addr whitelist my wifi connected machines just in case it's a local job.

I read through all running processes, check my bash history, look for screen sessions, and so on. Finally I decide that I must have been brute forced, either on my ssh port or perhaps even directly on my router. My laptops should have been, and seemed to still be, in sleep mode since that night.

**The second strike**
So tonight I'm watching a South Park episode (a show I hate to love), about to cut out for the night, when the Boxee menu pops up. I look at the remote and back at the tv; for just a moment I think that perhaps the mouse shifted slightly on the carpet and caused the menu to activate. Then Boxee stops the video, navigates the menu a few clicks, pulls up the exit menu and closes itself. 

Dang it all. I stick another 10 point landing as I hit the modem again. Now I'm confused and feel violated. I've showered 12 times but can't seem to get clean. I don't know where this person is getting access to my system.

Any suggestions on what to check? At this point I'm going to backup whatever settings I can and do a fresh install, but the question of how is going to drive me nuts. I'd like to review the issue before formatting my Revo.
Impossible.

Ubuntu is immune to hackers and viruses.

---

### Post by NefariousNobo on 2010-02-25
> **detroit/zero said:**
> Impossible.

Ubuntu is immune to hackers and viruses.

Are you kidding me? Ubuntu is just based off of a different kernel. The Linux kernel is generally superior to the NT kernel as far as safety is concerned (it's very UNIX-style), but it is by no means immune to either hackers or viruses. However, that being said, I have no idea how that could possibly happen, because despite the lack of total immunity, I've yet to see an Ubuntu virus, and I've yet to see anyone be *really* hacked.

---

### Post by detroit/zero on 2010-02-25
> **NefariousNobo said:**
> Are you kidding me? Ubuntu is just based off of a different kernel. The Linux kernel is generally superior to the NT kernel as far as safety is concerned (it's very UNIX-style), but it is by no means immune to either hackers or viruses. However, that being said, I have no idea how that could possibly happen, because despite the lack of total immunity, I've yet to see an Ubuntu virus, and I've yet to see anyone be *really* hacked.
Take your FUD somewhere else, you paid MS shill.

---

### Post by kemra on 2010-02-25
> **detroit/zero said:**
> Take your FUD somewhere else, you paid M$ shill.

Actually I think you should mind what you say as NefariousNobo is actually correct. Although Linux/UNIX kernels are far safer than any NT kernel they are not immune.

That being said to try and keep this ontopic:

oiper have you checked the logs on your router's firewall at all to see if it logged anything meaningful? It could tell us how an attacker gained access assuming that is what happened.

EDIT: You may want to take a look at the [Security Sticky]("http://ubuntuforums.org/showthread.php?t=510812") at the top of the page and just use this as a sort of checklist to see if there's anything you could do to tighten security a little.

---

### Post by CharlesA on 2010-02-25
Check the auth.log file to see if anyone got in via ssh. Do you happen to have "remote desktop" enabled by chance?

Since you disabled the forwarding of the SSH port, I can only figure that during the first attack, something was installed on the machine to let that person back in.

However, if someone got in once, the best thing to do is wipe the box and start with a clean install.

> **detroit/zero said:**
> Impossible.

Ubuntu is immune to hackers and viruses.

Ubuntu is immune to hackers? Mmk. While it is better then NT, nothing is completely immune to hackers/crackers/whatever, and that includes Ubuntu/Linux. I believe the services  most often used by an attacker to access a system remotely are VNC/"remote desktop" and SSH.

---

### Post by clanky on 2010-02-25
teehee, I think a few people may have missed the sarcasm.

---

### Post by HermanAB on 2010-02-25
Hmm, by default, Ubuntu PAM setup doesn't enforce the use of decent passwords.  Most (all?) successful hacking tales of woe in these forums are from people who thought a 4 character password is kewl and then they enabled VNC, SSH or FTP with predictable results.

So, you got to re-install dude - sorry - then put cracklib in /etc/pam.d/common-password to enable it for all services and set the minimum length. 

Here's an example common-password file:

password required pam_unix.so use_authtok md5
password required pam_cracklib.so retry=1 minlen=9 difok=3

---

### Post by Giant Speck on 2010-02-25
> **clanky said:**
> teehee, I think a few people may have missed the sarcasm.

But... the Internet is serious business...

---

### Post by CharlesA on 2010-02-25
> **clanky said:**
> teehee, I think a few people may have missed the sarcasm.

Needs moar sarcasm tags!

Besides, the internet is srs bsns.

---

### Post by Frak on 2010-02-25
<----- Got the joke.

Anyways, Boxee is slightly unstable. It may have just crashed.

---

### Post by oiper on 2010-02-25
Thanks for the comments.
@Frak It was certainly no crash, though I've had a number of those in the past.

In the meantime I decided to plow through the web history in Firefox. For whatever reason, he/she left it alone. An abbreviated list of sites hit are:

[IMG]http://www.flickr.com/photos/originalbryan/4387952045/[/IMG]
[http://www.flickr.com/photos/originalbryan/4387952045/](http://www.flickr.com/photos/originalbryan/4387952045/)

The list is longer, but many are pretty much dups.  Most deal with Online Derivatives And Forex Trading Brokers type sites.
Some adsense type entries were hit a lot.

Then I noticed a more interesting one:
[ftp://name:wick22@62.141.54.194:666/wicks.tar](ftp://name:wick22@62.141.54.194:666/wicks.tar)

A whois lookup fingers some German server 
```

address:        Keyweb AG
address:        Neuwerkstr. 45/46
address:        99084 Erfurt
address:        Germany
phone:          +49-361-658530
abuse-mailbox:  
```

I downloaded and checked out the file. It contains a small HTTP and HTTPS server. I haven't figured out much beyond that.

Per some comments, I checked my auth.log file:
```

Feb 21 08:17:01 revo CRON[14953]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 21 08:17:01 revo CRON[14953]: pam_unix(cron:session): session closed for user root
Feb 21 09:17:01 revo CRON[15037]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 21 09:17:01 revo CRON[15037]: pam_unix(cron:session): session closed for user root
Feb 21 10:17:01 revo CRON[15121]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 21 10:17:01 revo CRON[15121]: pam_unix(cron:session): session closed for user root
Feb 21 11:17:01 revo CRON[15205]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 21 11:17:01 revo CRON[15205]: pam_unix(cron:session): session closed for user root
Feb 21 12:17:01 revo CRON[15289]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 21 12:17:01 revo CRON[15289]: pam_unix(cron:session): session closed for user root
Feb 21 13:17:01 revo CRON[15375]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 21 13:17:01 revo CRON[15375]: pam_unix(cron:session): session closed for user root
Feb 21 14:17:01 revo CRON[15458]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 21 14:17:01 revo CRON[15458]: pam_unix(cron:session): session closed for user root
Feb 21 15:17:01 revo CRON[15541]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 21 15:17:01 revo CRON[15541]: pam_unix(cron:session): session closed for user root
Feb 21 16:17:01 revo CRON[15624]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 21 16:17:01 revo CRON[15624]: pam_unix(cron:session): session closed for user root
Feb 21 17:17:01 revo CRON[15708]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 21 17:17:01 revo CRON[15708]: pam_unix(cron:session): session closed for user root
Feb 21 18:17:01 revo CRON[15792]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 21 18:17:01 revo CRON[15792]: pam_unix(cron:session): session closed for user root
Feb 21 19:17:01 revo CRON[15886]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 21 19:17:01 revo CRON[15886]: pam_unix(cron:session): session closed for user root
Feb 21 20:17:01 revo CRON[16012]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 21 20:17:01 revo CRON[16012]: pam_unix(cron:session): session closed for user root
Feb 21 21:17:01 revo CRON[16136]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 21 21:17:01 revo CRON[16136]: pam_unix(cron:session): session closed for user root
Feb 21 22:17:01 revo CRON[16260]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 21 22:17:01 revo CRON[16260]: pam_unix(cron:session): session closed for user root
Feb 21 23:17:02 revo CRON[16971]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 21 23:17:02 revo CRON[16971]: pam_unix(cron:session): session closed for user root
Feb 22 00:17:01 revo CRON[17155]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 22 00:17:01 revo CRON[17155]: pam_unix(cron:session): session closed for user root
Feb 22 01:17:01 revo CRON[17336]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 22 01:17:01 revo CRON[17336]: pam_unix(cron:session): session closed for user root
Feb 22 02:17:01 revo CRON[17500]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 22 02:17:01 revo CRON[17500]: pam_unix(cron:session): session closed for user root
Feb 22 03:17:01 revo CRON[17664]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 22 03:17:01 revo CRON[17664]: pam_unix(cron:session): session closed for user root
Feb 22 04:17:01 revo CRON[17815]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 22 04:17:01 revo CRON[17815]: pam_unix(cron:session): session closed for user root
Feb 22 05:17:01 revo CRON[17959]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 22 05:17:01 revo CRON[17959]: pam_unix(cron:session): session closed for user root
Feb 22 05:43:20 revo sshd[18019]: Invalid user oracle from 71.183.86.38
Feb 22 05:43:20 revo sshd[18019]: pam_unix(sshd:auth): check pass; user unknown
Feb 22 05:43:20 revo sshd[18019]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=static-71-183-86-38.nycmny.fios.verizon.net 
Feb 22 05:43:22 revo sshd[18019]: Failed password for invalid user oracle from 71.183.86.38 port 41797 ssh2
Feb 22 05:43:23 revo sshd[18022]: Invalid user oracle from 71.183.86.38
Feb 22 05:43:23 revo sshd[18022]: pam_unix(sshd:auth): check pass; user unknown
Feb 22 05:43:23 revo sshd[18022]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=static-71-183-86-38.nycmny.fios.verizon.net 
Feb 22 05:43:25 revo sshd[18022]: Failed password for invalid user oracle from 71.183.86.38 port 42091 ssh2
Feb 22 05:43:25 revo sshd[18024]: Invalid user oracle from 71.183.86.38
Feb 22 05:43:25 revo sshd[18024]: pam_unix(sshd:auth): check pass; user unknown
Feb 22 05:43:25 revo sshd[18024]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=static-71-183-86-38.nycmny.fios.verizon.net 
Feb 22 05:43:27 revo sshd[18024]: Failed password for invalid user oracle from 71.183.86.38 port 42327 ssh2
Feb 22 05:43:28 revo sshd[18026]: Invalid user public from 71.183.86.38
Feb 22 05:43:28 revo sshd[18026]: pam_unix(sshd:auth): check pass; user unknown
Feb 22 05:43:28 revo sshd[18026]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=static-71-183-86-38.nycmny.fios.verizon.net 
Feb 22 05:43:29 revo sshd[18026]: Failed password for invalid user public from 71.183.86.38 port 42548 ssh2
Feb 22 05:43:30 revo sshd[18028]: Invalid user public from 71.183.86.38
Feb 22 05:43:30 revo sshd[18028]: pam_unix(sshd:auth): check pass; user unknown
Feb 22 05:43:30 revo sshd[18028]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=static-71-183-86-38.nycmny.fios.verizon.net 
Feb 22 05:43:32 revo sshd[18028]: Failed password for invalid user public from 71.183.86.38 port 42754 ssh2
Feb 22 05:43:33 revo sshd[18030]: Invalid user pgsql from 71.183.86.38
Feb 22 05:43:33 revo sshd[18030]: pam_unix(sshd:auth): check pass; user unknown
Feb 22 05:43:33 revo sshd[18030]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=static-71-183-86-38.nycmny.fios.verizon.net 
Feb 22 05:43:35 revo sshd[18030]: Failed password for invalid user pgsql from 71.183.86.38 port 42955 ssh2
Feb 22 05:43:35 revo sshd[18032]: Invalid user pgsql from 71.183.86.38
Feb 22 05:43:35 revo sshd[18032]: pam_unix(sshd:auth): check pass; user unknown
Feb 22 05:43:35 revo sshd[18032]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=static-71-183-86-38.nycmny.fios.verizon.net 
Feb 22 05:43:37 revo sshd[18032]: Failed password for invalid user pgsql from 71.183.86.38 port 43208 ssh2
Feb 22 05:43:38 revo sshd[18034]: Invalid user user from 71.183.86.38
Feb 22 05:43:38 revo sshd[18034]: pam_unix(sshd:auth): check pass; user unknown
Feb 22 05:43:38 revo sshd[18034]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=static-71-183-86-38.nycmny.fios.verizon.net 
Feb 22 05:43:40 revo sshd[18034]: Failed password for invalid user user from 71.183.86.38 port 43430 ssh2
Feb 22 05:43:41 revo sshd[18036]: Invalid user nagios from 71.183.86.38
Feb 22 05:43:41 revo sshd[18036]: pam_unix(sshd:auth): check pass; user unknown
Feb 22 05:43:41 revo sshd[18036]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=static-71-183-86-38.nycmny.fios.verizon.net 
Feb 22 05:43:43 revo sshd[18036]: Failed password for invalid user nagios from 71.183.86.38 port 43729 ssh2
Feb 22 05:43:43 revo sshd[18038]: Invalid user nagios from 71.183.86.38
Feb 22 05:43:44 revo sshd[18038]: pam_unix(sshd:auth): check pass; user unknown
Feb 22 05:43:44 revo sshd[18038]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=static-71-183-86-38.nycmny.fios.verizon.net 
Feb 22 05:43:46 revo sshd[18038]: Failed password for invalid user nagios from 71.183.86.38 port 43989 ssh2
Feb 22 05:43:46 revo sshd[18040]: Invalid user test from 71.183.86.38
Feb 22 05:43:46 revo sshd[18040]: pam_unix(sshd:auth): check pass; user unknown
Feb 22 05:43:46 revo sshd[18040]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=static-71-183-86-38.nycmny.fios.verizon.net 
Feb 22 05:43:48 revo sshd[18040]: Failed password for invalid user test from 71.183.86.38 port 44245 ssh2
Feb 22 05:43:49 revo sshd[18042]: Invalid user test from 71.183.86.38
Feb 22 05:43:49 revo sshd[18042]: pam_unix(sshd:auth): check pass; user unknown
Feb 22 05:43:49 revo sshd[18042]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=static-71-183-86-38.nycmny.fios.verizon.net 
Feb 22 05:43:51 revo sshd[18042]: Failed password for invalid user test from 71.183.86.38 port 44500 ssh2
Feb 22 05:43:51 revo sshd[18044]: Invalid user test from 71.183.86.38
Feb 22 05:43:51 revo sshd[18044]: pam_unix(sshd:auth): check pass; user unknown
Feb 22 05:43:51 revo sshd[18044]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=static-71-183-86-38.nycmny.fios.verizon.net 
Feb 22 05:43:54 revo sshd[18044]: Failed password for invalid user test from 71.183.86.38 port 44739 ssh2
Feb 22 05:43:54 revo sshd[18046]: Invalid user test from 71.183.86.38
Feb 22 05:43:54 revo sshd[18046]: pam_unix(sshd:auth): check pass; user unknown
Feb 22 05:43:54 revo sshd[18046]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=static-71-183-86-38.nycmny.fios.verizon.net 
Feb 22 05:43:56 revo sshd[18046]: Failed password for invalid user test from 71.183.86.38 port 45009 ssh2
Feb 22 05:43:57 revo sshd[18048]: Invalid user anonymous from 71.183.86.38
Feb 22 05:43:57 revo sshd[18048]: pam_unix(sshd:auth): check pass; user unknown
Feb 22 05:43:57 revo sshd[18048]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=static-71-183-86-38.nycmny.fios.verizon.net 
Feb 22 05:43:59 revo sshd[18048]: Failed password for invalid user anonymous from 71.183.86.38 port 45271 ssh2
Feb 22 06:17:01 revo CRON[18134]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 22 06:17:01 revo CRON[18134]: pam_unix(cron:session): session closed for user root
Feb 22 06:23:12 revo sshd[18147]: Did not receive identification string from 121.34.248.1
Feb 22 06:25:01 revo CRON[18156]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 22 06:25:01 revo CRON[18156]: pam_unix(cron:session): session closed for user root
Feb 22 07:17:01 revo CRON[18283]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 22 07:17:01 revo CRON[18283]: pam_unix(cron:session): session closed for user root
Feb 22 07:30:01 revo CRON[18316]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 22 07:30:01 revo CRON[18316]: pam_unix(cron:session): session closed for user root
Feb 22 07:35:03 revo sudo:     root : TTY=unknown ; PWD=/ ; USER=htpc ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/use_http_proxy
Feb 22 07:35:03 revo sudo:     root : TTY=unknown ; PWD=/ ; USER=htpc ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/host
Feb 22 07:35:03 revo sudo:     root : TTY=unknown ; PWD=/ ; USER=htpc ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port
Feb 22 08:17:01 revo CRON[18638]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 22 08:17:01 revo CRON[18638]: pam_unix(cron:session): session closed for user root
Feb 22 09:17:01 revo CRON[18811]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 22 09:17:01 revo CRON[18811]: pam_unix(cron:session): session closed for user root
Feb 22 10:17:01 revo CRON[18977]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 22 10:17:01 revo CRON[18977]: pam_unix(cron:session): session closed for user root
Feb 22 11:17:01 revo CRON[19141]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 22 11:17:01 revo CRON[19141]: pam_unix(cron:session): session closed for user root
Feb 22 12:17:01 revo CRON[19305]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 22 12:17:01 revo CRON[19305]: pam_unix(cron:session): session closed for user root
Feb 22 13:01:47 revo sshd[19425]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.65.22.18  user=root
Feb 22 13:01:49 revo sshd[19425]: Failed password for root from 201.65.22.18 port 33412 ssh2
Feb 22 13:01:57 revo sshd[19428]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.65.22.18  user=root
Feb 22 13:01:58 revo sshd[19428]: Failed password for root from 201.65.22.18 port 34108 ssh2
Feb 22 13:02:05 revo sshd[19430]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.65.22.18  user=root
Feb 22 13:02:07 revo sshd[19430]: Failed password for root from 201.65.22.18 port 34964 ssh2
Feb 22 13:02:14 revo sshd[19432]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.65.22.18  user=root
Feb 22 13:02:16 revo sshd[19432]: Failed password for root from 201.65.22.18 port 35795 ssh2
Feb 22 13:02:23 revo sshd[19434]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.65.22.18  user=root
Feb 22 13:02:25 revo sshd[19434]: Failed password for root from 201.65.22.18 port 36520 ssh2
Feb 22 13:02:32 revo sshd[19437]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.65.22.18  user=root
Feb 22 13:02:34 revo sshd[19437]: Failed password for root from 201.65.22.18 port 37367 ssh2
Feb 22 13:02:41 revo sshd[19439]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.65.22.18  user=root
Feb 22 13:02:44 revo sshd[19439]: Failed password for root from 201.65.22.18 port 38193 ssh2
Feb 22 13:02:51 revo sshd[19441]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.65.22.18  user=root
Feb 22 13:02:53 revo sshd[19441]: Failed password for root from 201.65.22.18 port 38871 ssh2
Feb 22 13:03:01 revo sshd[19443]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.65.22.18  user=root
Feb 22 13:03:03 revo sshd[19443]: Failed password for root from 201.65.22.18 port 39601 ssh2
Feb 22 13:03:10 revo sshd[19445]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.65.22.18  user=root
Feb 22 13:03:12 revo sshd[19445]: Failed password for root from 201.65.22.18 port 40244 ssh2
Feb 22 13:03:19 revo sshd[19447]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.65.22.18  user=root
Feb 22 13:03:22 revo sshd[19447]: Failed password for root from 201.65.22.18 port 40915 ssh2
Feb 22 13:03:29 revo sshd[19449]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.65.22.18  user=root
Feb 22 13:03:30 revo sshd[19449]: Failed password for root from 201.65.22.18 port 41609 ssh2
Feb 22 13:03:37 revo sshd[19452]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.65.22.18  user=root
Feb 22 13:03:39 revo sshd[19452]: Failed password for root from 201.65.22.18 port 42165 ssh2
Feb 22 13:03:46 revo sshd[19454]: Invalid user oracle from 201.65.22.18
Feb 22 13:03:46 revo sshd[19454]: pam_unix(sshd:auth): check pass; user unknown
Feb 22 13:03:46 revo sshd[19454]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.65.22.18 
Feb 22 13:03:48 revo sshd[19454]: Failed password for invalid user oracle from 201.65.22.18 port 42835 ssh2
Feb 22 13:17:01 revo CRON[19498]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 22 13:17:01 revo CRON[19498]: pam_unix(cron:session): session closed for user root
Feb 22 14:17:01 revo CRON[20009]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 22 14:17:01 revo CRON[20009]: pam_unix(cron:session): session closed for user root
Feb 22 15:17:01 revo CRON[20314]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 22 15:17:01 revo CRON[20314]: pam_unix(cron:session): session closed for user root
Feb 22 16:17:01 revo CRON[20488]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 22 16:17:01 revo CRON[20488]: pam_unix(cron:session): session closed for user root
Feb 22 17:17:01 revo CRON[20570]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 22 17:17:01 revo CRON[20570]: pam_unix(cron:session): session closed for user root
Feb 22 17:17:22 revo sshd[20574]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.186.175.14  user=root
Feb 22 17:17:23 revo sshd[20574]: Failed password for root from 211.186.175.14 port 33040 ssh2
Feb 22 17:17:30 revo sshd[20576]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.186.175.14  user=root
Feb 22 17:17:33 revo sshd[20576]: Failed password for root from 211.186.175.14 port 34852 ssh2
Feb 22 17:17:40 revo sshd[20578]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.186.175.14  user=root
Feb 22 17:17:42 revo sshd[20578]: Failed password for root from 211.186.175.14 port 36766 ssh2
Feb 22 17:17:49 revo sshd[20580]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.186.175.14  user=root
Feb 22 17:17:51 revo sshd[20580]: Failed password for root from 211.186.175.14 port 38649 ssh2
Feb 22 17:17:58 revo sshd[20582]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.186.175.14  user=root
Feb 22 17:18:00 revo sshd[20582]: Failed password for root from 211.186.175.14 port 40530 ssh2
Feb 22 17:18:07 revo sshd[20584]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.186.175.14  user=root
Feb 22 17:18:10 revo sshd[20584]: Failed password for root from 211.186.175.14 port 42377 ssh2
Feb 22 17:18:17 revo sshd[20586]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.186.175.14  user=root
Feb 22 17:18:19 revo sshd[20586]: Failed password for root from 211.186.175.14 port 44428 ssh2
Feb 22 17:18:26 revo sshd[20591]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.186.175.14  user=root
Feb 22 17:18:29 revo sshd[20591]: Failed password for root from 211.186.175.14 port 46570 ssh2
Feb 22 17:18:36 revo sshd[20593]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.186.175.14  user=root
Feb 22 17:18:38 revo sshd[20593]: Failed password for root from 211.186.175.14 port 48894 ssh2
Feb 22 17:18:46 revo sshd[20595]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.186.175.14  user=root
Feb 22 17:18:48 revo sshd[20595]: Failed password for root from 211.186.175.14 port 51175 ssh2
Feb 22 17:18:55 revo sshd[20597]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.186.175.14  user=root
Feb 22 17:18:57 revo sshd[20597]: Failed password for root from 211.186.175.14 port 53521 ssh2
Feb 22 17:19:05 revo sshd[20599]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.186.175.14  user=root
Feb 22 17:19:07 revo sshd[20599]: Failed password for root from 211.186.175.14 port 55885 ssh2
Feb 22 17:19:14 revo sshd[20602]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.186.175.14  user=root
Feb 22 17:19:16 revo sshd[20602]: Failed password for root from 211.186.175.14 port 58072 ssh2
Feb 22 17:19:23 revo sshd[20604]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.186.175.14  user=root
Feb 22 17:19:26 revo sshd[20604]: Failed password for root from 211.186.175.14 port 60365 ssh2
Feb 22 17:19:33 revo sshd[20606]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.186.175.14  user=root
Feb 22 17:19:35 revo sshd[20606]: Failed password for root from 211.186.175.14 port 34554 ssh2
Feb 22 17:19:42 revo sshd[20608]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.186.175.14  user=root
Feb 22 17:19:44 revo sshd[20608]: Failed password for root from 211.186.175.14 port 36907 ssh2
Feb 22 17:19:51 revo sshd[20610]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.186.175.14  user=root
Feb 22 17:19:54 revo sshd[20610]: Failed password for root from 211.186.175.14 port 39229 ssh2
Feb 22 17:20:01 revo sshd[20612]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.186.175.14  user=root
Feb 22 17:20:03 revo sshd[20612]: Failed password for root from 211.186.175.14 port 41333 ssh2
Feb 22 17:20:10 revo sshd[20614]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.186.175.14  user=root
Feb 22 17:20:12 revo sshd[20614]: Failed password for root from 211.186.175.14 port 43441 ssh2
Feb 22 17:20:20 revo sshd[20616]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.186.175.14  user=root
Feb 22 17:20:22 revo sshd[20616]: Failed password for root from 211.186.175.14 port 45537 ssh2
Feb 22 17:20:30 revo sshd[20618]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.186.175.14  user=root
Feb 22 17:20:32 revo sshd[20618]: Failed password for root from 211.186.175.14 port 47806 ssh2
Feb 22 17:20:39 revo sshd[20620]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.186.175.14  user=root
Feb 22 17:20:41 revo sshd[20620]: Failed password for root from 211.186.175.14 port 49876 ssh2
Feb 22 17:20:48 revo sshd[20622]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.186.175.14  user=root
Feb 22 17:20:50 revo sshd[20622]: Failed password for root from 211.186.175.14 port 51903 ssh2
Feb 22 17:20:57 revo sshd[20624]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.186.175.14  user=root
Feb 22 17:20:59 revo sshd[20624]: Failed password for root from 211.186.175.14 port 53888 ssh2
Feb 22 17:21:07 revo sshd[20626]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.186.175.14  user=root
Feb 22 17:21:09 revo sshd[20626]: Failed password for root from 211.186.175.14 port 55923 ssh2
Feb 22 17:21:16 revo sshd[20629]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.186.175.14  user=root
Feb 22 17:21:19 revo sshd[20629]: Failed password for root from 211.186.175.14 port 58009 ssh2
Feb 22 17:21:26 revo sshd[20631]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.186.175.14  user=root
Feb 22 17:21:28 revo sshd[20631]: Failed password for root from 211.186.175.14 port 59951 ssh2
Feb 22 17:21:35 revo sshd[20634]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.186.175.14  user=root
Feb 22 17:21:37 revo sshd[20634]: Failed password for root from 211.186.175.14 port 33682 ssh2
Feb 22 17:21:44 revo sshd[20636]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.186.175.14  user=root
Feb 22 17:21:46 revo sshd[20636]: Failed password for root from 211.186.175.14 port 35521 ssh2
Feb 22 17:21:53 revo sshd[20638]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.186.175.14  user=root
Feb 22 17:21:55 revo sshd[20638]: Failed password for root from 211.186.175.14 port 37326 ssh2
Feb 22 17:22:03 revo sshd[20640]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.186.175.14  user=root
Feb 22 17:22:05 revo sshd[20640]: Failed password for root from 211.186.175.14 port 39241 ssh2
Feb 22 17:22:12 revo sshd[20643]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.186.175.14  user=root
Feb 22 17:22:14 revo sshd[20643]: Failed password for root from 211.186.175.14 port 41168 ssh2
Feb 22 17:22:21 revo sshd[20645]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.186.175.14  user=root
Feb 22 17:22:23 revo sshd[20645]: Failed password for root from 211.186.175.14 port 43246 ssh2
Feb 22 17:22:30 revo sshd[20647]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.186.175.14  user=root
Feb 22 17:22:32 revo sshd[20647]: Failed password for root from 211.186.175.14 port 45324 ssh2
Feb 22 17:22:39 revo sshd[20649]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.186.175.14  user=root
Feb 22 17:22:41 revo sshd[20649]: Failed password for root from 211.186.175.14 port 47395 ssh2
Feb 22 17:22:49 revo sshd[20651]: Invalid user user from 211.186.175.14
Feb 22 17:22:49 revo sshd[20651]: pam_unix(sshd:auth): check pass; user unknown
Feb 22 17:22:49 revo sshd[20651]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.186.175.14 
Feb 22 17:22:50 revo sshd[20651]: Failed password for invalid user user from 211.186.175.14 port 49632 ssh2
Feb 22 17:22:57 revo sshd[20653]: Invalid user user from 211.186.175.14
Feb 22 17:22:57 revo sshd[20653]: pam_unix(sshd:auth): check pass; user unknown
Feb 22 17:22:57 revo sshd[20653]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.186.175.14 
Feb 22 17:22:59 revo sshd[20653]: Failed password for invalid user user from 211.186.175.14 port 51732 ssh2
Feb 22 17:23:06 revo sshd[20655]: Invalid user user from 211.186.175.14
Feb 22 17:23:06 revo sshd[20655]: pam_unix(sshd:auth): check pass; user unknown
Feb 22 17:23:06 revo sshd[20655]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.186.175.14 
Feb 22 17:23:09 revo sshd[20655]: Failed password for invalid user user from 211.186.175.14 port 53864 ssh2
Feb 22 17:23:16 revo sshd[20657]: Invalid user user from 211.186.175.14
Feb 22 17:23:16 revo sshd[20657]: pam_unix(sshd:auth): check pass; user unknown
Feb 22 17:23:16 revo sshd[20657]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.186.175.14 
Feb 22 17:23:18 revo sshd[20657]: Failed password for invalid user user from 211.186.175.14 port 56036 ssh2
Feb 22 17:23:25 revo sshd[20659]: Invalid user test from 211.186.175.14
Feb 22 17:23:25 revo sshd[20659]: pam_unix(sshd:auth): check pass; user unknown
Feb 22 17:23:25 revo sshd[20659]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.186.175.14 
Feb 22 17:23:27 revo sshd[20659]: Failed password for invalid user test from 211.186.175.14 port 58188 ssh2
Feb 22 17:23:34 revo sshd[20661]: Invalid user test from 211.186.175.14
Feb 22 17:23:34 revo sshd[20661]: pam_unix(sshd:auth): check pass; user unknown
Feb 22 17:23:34 revo sshd[20661]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.186.175.14 
Feb 22 17:23:36 revo sshd[20661]: Failed password for invalid user test from 211.186.175.14 port 60226 ssh2
Feb 22 17:23:43 revo sshd[20663]: Invalid user test from 211.186.175.14
Feb 22 17:23:43 revo sshd[20663]: pam_unix(sshd:auth): check pass; user unknown
Feb 22 17:23:43 revo sshd[20663]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.186.175.14 
Feb 22 17:23:45 revo sshd[20663]: Failed password for invalid user test from 211.186.175.14 port 34110 ssh2
Feb 22 17:23:52 revo sshd[20665]: Invalid user test from 211.186.175.14
Feb 22 17:23:52 revo sshd[20665]: pam_unix(sshd:auth): check pass; user unknown
Feb 22 17:23:52 revo sshd[20665]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.186.175.14 
Feb 22 17:23:54 revo sshd[20665]: Failed password for invalid user test from 211.186.175.14 port 36270 ssh2
Feb 22 17:24:02 revo sshd[20668]: Invalid user test from 211.186.175.14
Feb 22 17:24:02 revo sshd[20668]: pam_unix(sshd:auth): check pass; user unknown
Feb 22 17:24:02 revo sshd[20668]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.186.175.14 
Feb 22 17:24:03 revo sshd[20668]: Failed password for invalid user test from 211.186.175.14 port 38571 ssh2
Feb 22 17:24:10 revo sshd[20670]: Invalid user test from 211.186.175.14
Feb 22 17:24:10 revo sshd[20670]: pam_unix(sshd:auth): check pass; user unknown
Feb 22 17:24:10 revo sshd[20670]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.186.175.14 
Feb 22 17:24:12 revo sshd[20670]: Failed password for invalid user test from 211.186.175.14 port 40703 ssh2
Feb 22 17:24:20 revo sshd[20673]: Invalid user test from 211.186.175.14
Feb 22 17:24:20 revo sshd[20673]: pam_unix(sshd:auth): check pass; user unknown
Feb 22 17:24:20 revo sshd[20673]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.186.175.14 
Feb 22 17:24:22 revo sshd[20673]: Failed password for invalid user test from 211.186.175.14 port 42936 ssh2
Feb 22 17:24:29 revo sshd[20675]: Invalid user oracle from 211.186.175.14
Feb 22 17:24:29 revo sshd[20675]: pam_unix(sshd:auth): check pass; user unknown
Feb 22 17:24:29 revo sshd[20675]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.186.175.14 
Feb 22 17:24:31 revo sshd[20675]: Failed password for invalid user oracle from 211.186.175.14 port 45303 ssh2
Feb 22 17:24:38 revo sshd[20677]: Invalid user oracle from 211.186.175.14
Feb 22 17:24:38 revo sshd[20677]: pam_unix(sshd:auth): check pass; user unknown
Feb 22 17:24:38 revo sshd[20677]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.186.175.14 
Feb 22 17:24:40 revo sshd[20677]: Failed password for invalid user oracle from 211.186.175.14 port 47634 ssh2
Feb 22 17:24:47 revo sshd[20679]: Invalid user oracle from 211.186.175.14
Feb 22 17:24:47 revo sshd[20679]: pam_unix(sshd:auth): check pass; user unknown
Feb 22 17:24:47 revo sshd[20679]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.186.175.14 
Feb 22 17:24:50 revo sshd[20679]: Failed password for invalid user oracle from 211.186.175.14 port 50029 ssh2
Feb 22 17:24:57 revo sshd[20681]: Invalid user oracle from 211.186.175.14
Feb 22 17:24:57 revo sshd[20681]: pam_unix(sshd:auth): check pass; user unknown
Feb 22 17:24:57 revo sshd[20681]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.186.175.14 
Feb 22 17:24:59 revo sshd[20681]: Failed password for invalid user oracle from 211.186.175.14 port 52588 ssh2
Feb 22 17:25:06 revo sshd[20683]: Invalid user student from 211.186.175.14
Feb 22 17:25:06 revo sshd[20683]: pam_unix(sshd:auth): check pass; user unknown
Feb 22 17:25:06 revo sshd[20683]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.186.175.14 
Feb 22 17:25:08 revo sshd[20683]: Failed password for invalid user student from 211.186.175.14 port 55129 ssh2
Feb 22 18:17:01 revo CRON[20736]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 22 18:17:01 revo CRON[20736]: pam_unix(cron:session): session closed for user root
Feb 22 19:17:01 revo CRON[20774]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 22 19:17:01 revo CRON[20774]: pam_unix(cron:session): session closed for user root
Feb 22 20:17:01 revo CRON[20802]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 22 20:17:01 revo CRON[20802]: pam_unix(cron:session): session closed for user root
Feb 22 21:17:02 revo CRON[20838]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 22 21:17:02 revo CRON[20838]: pam_unix(cron:session): session closed for user root
Feb 22 22:17:01 revo CRON[20864]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 22 22:17:01 revo CRON[20864]: pam_unix(cron:session): session closed for user root
Feb 22 23:17:01 revo CRON[20890]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 22 23:17:01 revo CRON[20890]: pam_unix(cron:session): session closed for user root
Feb 23 00:17:01 revo CRON[20916]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 23 00:17:01 revo CRON[20916]: pam_unix(cron:session): session closed for user root
Feb 23 01:17:01 revo CRON[20942]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 23 01:17:01 revo CRON[20942]: pam_unix(cron:session): session closed for user root
Feb 23 02:17:01 revo CRON[20969]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 23 02:17:01 revo CRON[20969]: pam_unix(cron:session): session closed for user root
Feb 23 03:17:01 revo CRON[20995]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 23 03:17:01 revo CRON[20995]: pam_unix(cron:session): session closed for user root
Feb 23 04:17:01 revo CRON[21021]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 23 04:17:01 revo CRON[21021]: pam_unix(cron:session): session closed for user root
Feb 23 05:17:01 revo CRON[21047]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 23 05:17:01 revo CRON[21047]: pam_unix(cron:session): session closed for user root
Feb 23 06:17:01 revo CRON[21073]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 23 06:17:01 revo CRON[21073]: pam_unix(cron:session): session closed for user root
Feb 23 06:25:01 revo CRON[21081]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 23 06:25:01 revo CRON[21081]: pam_unix(cron:session): session closed for user root
Feb 23 07:17:01 revo CRON[21191]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 23 07:17:01 revo CRON[21191]: pam_unix(cron:session): session closed for user root
Feb 23 07:30:01 revo CRON[21305]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 23 07:30:01 revo CRON[21305]: pam_unix(cron:session): session closed for user root
Feb 23 07:35:02 revo sudo:     root : TTY=unknown ; PWD=/ ; USER=htpc ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/use_http_proxy
Feb 23 07:35:03 revo sudo:     root : TTY=unknown ; PWD=/ ; USER=htpc ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/host
Feb 23 07:35:03 revo sudo:     root : TTY=unknown ; PWD=/ ; USER=htpc ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port
Feb 23 08:17:02 revo CRON[25869]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 23 08:17:02 revo CRON[25869]: pam_unix(cron:session): session closed for user root
Feb 23 09:17:01 revo CRON[25929]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 23 09:17:01 revo CRON[25929]: pam_unix(cron:session): session closed for user root
Feb 23 10:17:01 revo CRON[25982]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 23 10:17:01 revo CRON[25982]: pam_unix(cron:session): session closed for user root
Feb 23 11:17:01 revo CRON[25999]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 23 11:17:01 revo CRON[25999]: pam_unix(cron:session): session closed for user root
Feb 23 12:17:01 revo CRON[26007]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 23 12:17:01 revo CRON[26007]: pam_unix(cron:session): session closed for user root
Feb 23 13:17:01 revo CRON[26014]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 23 13:17:01 revo CRON[26014]: pam_unix(cron:session): session closed for user root
Feb 23 13:57:50 revo sshd[26020]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.157.105.114  user=root
Feb 23 13:57:52 revo sshd[26020]: Failed password for root from 211.157.105.114 port 39716 ssh2
Feb 23 13:57:59 revo sshd[26023]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.157.105.114  user=root
Feb 23 13:58:01 revo sshd[26023]: Failed password for root from 211.157.105.114 port 41253 ssh2
Feb 23 13:58:09 revo sshd[26025]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.157.105.114  user=root
Feb 23 13:58:11 revo sshd[26025]: Failed password for root from 211.157.105.114 port 42810 ssh2
Feb 23 13:58:18 revo sshd[26027]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.157.105.114  user=root
Feb 23 13:58:20 revo sshd[26027]: Failed password for root from 211.157.105.114 port 44311 ssh2
Feb 23 13:58:27 revo sshd[26029]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.157.105.114  user=root
Feb 23 13:58:29 revo sshd[26029]: Failed password for root from 211.157.105.114 port 45731 ssh2
Feb 23 13:58:36 revo sshd[26031]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.157.105.114  user=root
Feb 23 13:58:38 revo sshd[26031]: Failed password for root from 211.157.105.114 port 47223 ssh2
Feb 23 13:58:46 revo sshd[26033]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.157.105.114  user=root
Feb 23 13:58:48 revo sshd[26033]: Failed password for root from 211.157.105.114 port 48769 ssh2
Feb 23 13:58:55 revo sshd[26035]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.157.105.114  user=root
Feb 23 13:58:58 revo sshd[26035]: Failed password for root from 211.157.105.114 port 50323 ssh2
Feb 23 13:59:05 revo sshd[26037]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.157.105.114  user=root
Feb 23 13:59:07 revo sshd[26037]: Failed password for root from 211.157.105.114 port 51976 ssh2
Feb 23 13:59:15 revo sshd[26039]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.157.105.114  user=root
Feb 23 13:59:17 revo sshd[26039]: Failed password for root from 211.157.105.114 port 53702 ssh2
Feb 23 13:59:25 revo sshd[26041]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.157.105.114  user=root
Feb 23 13:59:27 revo sshd[26041]: Failed password for root from 211.157.105.114 port 55373 ssh2
Feb 23 13:59:34 revo sshd[26043]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.157.105.114  user=root
Feb 23 13:59:36 revo sshd[26043]: Failed password for root from 211.157.105.114 port 56946 ssh2
Feb 23 13:59:44 revo sshd[26045]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.157.105.114  user=root
Feb 23 13:59:46 revo sshd[26045]: Failed password for root from 211.157.105.114 port 58480 ssh2
Feb 23 13:59:53 revo sshd[26047]: Invalid user oracle from 211.157.105.114
Feb 23 13:59:53 revo sshd[26047]: pam_unix(sshd:auth): check pass; user unknown
Feb 23 13:59:53 revo sshd[26047]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.157.105.114 
Feb 23 13:59:56 revo sshd[26047]: Failed password for invalid user oracle from 211.157.105.114 port 60033 ssh2
Feb 23 14:17:01 revo CRON[26049]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 23 14:17:01 revo CRON[26049]: pam_unix(cron:session): session closed for user root
Feb 23 15:17:01 revo CRON[26056]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 23 15:17:01 revo CRON[26056]: pam_unix(cron:session): session closed for user root
Feb 23 16:17:01 revo CRON[26063]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 23 16:17:01 revo CRON[26063]: pam_unix(cron:session): session closed for user root
Feb 23 17:17:01 revo CRON[26131]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 23 17:17:01 revo CRON[26131]: pam_unix(cron:session): session closed for user root
Feb 23 18:17:01 revo CRON[26305]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 23 18:17:01 revo CRON[26305]: pam_unix(cron:session): session closed for user root
Feb 23 19:17:01 revo CRON[26922]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 23 19:17:02 revo CRON[26922]: pam_unix(cron:session): session closed for user root
Feb 23 20:17:01 revo CRON[27150]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 23 20:17:01 revo CRON[27150]: pam_unix(cron:session): session closed for user root
Feb 23 21:17:01 revo CRON[27463]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 23 21:17:01 revo CRON[27463]: pam_unix(cron:session): session closed for user root
Feb 23 22:17:01 revo CRON[27693]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 23 22:17:01 revo CRON[27693]: pam_unix(cron:session): session closed for user root
Feb 23 23:17:01 revo CRON[27892]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 23 23:17:01 revo CRON[27892]: pam_unix(cron:session): session closed for user root
Feb 23 23:31:02 revo sshd[27920]: Did not receive identification string from 58.64.144.85
Feb 23 23:32:47 revo sshd[27929]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=58.64.163.101  user=root
Feb 23 23:32:49 revo sshd[27929]: Failed password for root from 58.64.163.101 port 60613 ssh2
Feb 24 00:17:01 revo CRON[28008]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 24 00:17:01 revo CRON[28008]: pam_unix(cron:session): session closed for user root
Feb 24 01:17:01 revo CRON[28119]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 24 01:17:01 revo CRON[28119]: pam_unix(cron:session): session closed for user root
Feb 24 02:00:27 revo sshd[28201]: Did not receive identification string from 202.202.43.18
Feb 24 02:02:13 revo sshd[28210]: Invalid user sekretariat from 202.202.43.18
Feb 24 02:02:13 revo sshd[28210]: pam_unix(sshd:auth): check pass; user unknown
Feb 24 02:02:13 revo sshd[28210]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=202.202.43.18 
Feb 24 02:02:15 revo sshd[28210]: Failed password for invalid user sekretariat from 202.202.43.18 port 34413 ssh2
Feb 24 02:02:23 revo sshd[28212]: Invalid user sekretariat from 202.202.43.18
Feb 24 02:02:23 revo sshd[28212]: pam_unix(sshd:auth): check pass; user unknown
Feb 24 02:02:23 revo sshd[28212]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=202.202.43.18 
Feb 24 02:02:25 revo sshd[28212]: Failed password for invalid user sekretariat from 202.202.43.18 port 37219 ssh2
Feb 24 02:02:33 revo sshd[28214]: Invalid user sekretariat from 202.202.43.18
Feb 24 02:02:33 revo sshd[28214]: pam_unix(sshd:auth): check pass; user unknown
Feb 24 02:02:33 revo sshd[28214]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=202.202.43.18 
Feb 24 02:02:35 revo sshd[28214]: Failed password for invalid user sekretariat from 202.202.43.18 port 39147 ssh2
Feb 24 02:17:01 revo CRON[28240]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 24 02:17:01 revo CRON[28240]: pam_unix(cron:session): session closed for user root
Feb 24 03:17:01 revo CRON[28350]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 24 03:17:01 revo CRON[28350]: pam_unix(cron:session): session closed for user root
Feb 24 04:17:01 revo CRON[28461]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 24 04:17:01 revo CRON[28461]: pam_unix(cron:session): session closed for user root
Feb 24 05:17:01 revo CRON[28573]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 24 05:17:01 revo CRON[28573]: pam_unix(cron:session): session closed for user root
Feb 24 06:17:01 revo CRON[28684]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 24 06:17:01 revo CRON[28684]: pam_unix(cron:session): session closed for user root
Feb 24 06:25:01 revo CRON[28705]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 24 06:25:01 revo CRON[28705]: pam_unix(cron:session): session closed for user root
Feb 24 07:17:01 revo CRON[28798]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 24 07:17:01 revo CRON[28798]: pam_unix(cron:session): session closed for user root
Feb 24 07:30:01 revo CRON[28895]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 24 07:30:01 revo CRON[28895]: pam_unix(cron:session): session closed for user root
Feb 24 07:35:04 revo sudo:     root : TTY=unknown ; PWD=/ ; USER=htpc ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/use_http_proxy
Feb 24 07:35:05 revo sudo:     root : TTY=unknown ; PWD=/ ; USER=htpc ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/host
Feb 24 07:35:05 revo sudo:     root : TTY=unknown ; PWD=/ ; USER=htpc ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port
Feb 24 08:17:01 revo CRON[29139]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 24 08:17:01 revo CRON[29139]: pam_unix(cron:session): session closed for user root
Feb 24 09:17:02 revo CRON[29863]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 24 09:17:02 revo CRON[29863]: pam_unix(cron:session): session closed for user root
Feb 24 10:17:01 revo CRON[30087]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 24 10:17:01 revo CRON[30087]: pam_unix(cron:session): session closed for user root
Feb 24 11:17:01 revo CRON[30206]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 24 11:17:01 revo CRON[30206]: pam_unix(cron:session): session closed for user root
Feb 24 12:17:01 revo CRON[30312]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 24 12:17:01 revo CRON[30312]: pam_unix(cron:session): session closed for user root
Feb 24 13:17:01 revo CRON[30434]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 24 13:17:01 revo CRON[30434]: pam_unix(cron:session): session closed for user root
Feb 24 14:17:01 revo CRON[30526]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 24 14:17:01 revo CRON[30526]: pam_unix(cron:session): session closed for user root
Feb 24 15:17:01 revo CRON[30572]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 24 15:17:01 revo CRON[30572]: pam_unix(cron:session): session closed for user root
Feb 24 16:17:01 revo CRON[30621]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 24 16:17:01 revo CRON[30621]: pam_unix(cron:session): session closed for user root
Feb 24 17:17:01 revo CRON[30668]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 24 17:17:01 revo CRON[30668]: pam_unix(cron:session): session closed for user root
Feb 24 18:17:01 revo CRON[30890]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 24 18:17:01 revo CRON[30890]: pam_unix(cron:session): session closed for user root
Feb 24 19:17:01 revo CRON[31102]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 24 19:17:01 revo CRON[31102]: pam_unix(cron:session): session closed for user root
Feb 24 20:17:01 revo CRON[31311]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 24 20:17:01 revo CRON[31311]: pam_unix(cron:session): session closed for user root
Feb 24 21:17:01 revo CRON[31488]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 24 21:17:01 revo CRON[31488]: pam_unix(cron:session): session closed for user root
Feb 24 22:17:01 revo CRON[32022]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 24 22:17:01 revo CRON[32022]: pam_unix(cron:session): session closed for user root
Feb 24 22:41:08 revo sshd[32100]: Accepted password for htpc from 192.168.1.103 port 57127 ssh2
Feb 24 22:41:08 revo sshd[32100]: pam_unix(sshd:session): session opened for user htpc by (uid=0)
Feb 24 22:59:41 revo sshd[32100]: pam_unix(sshd:session): session closed for user htpc
Feb 24 23:08:53 revo sudo:     htpc : TTY=pts/0 ; PWD=/home/netlogon ; USER=root ; COMMAND=/bin/bash
Feb 24 23:17:01 revo CRON[601]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 24 23:17:01 revo CRON[601]: pam_unix(cron:session): session closed for user root
Feb 25 00:17:01 revo CRON[656]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 25 00:17:01 revo CRON[656]: pam_unix(cron:session): session closed for user root
Feb 25 01:17:01 revo CRON[665]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 25 01:17:01 revo CRON[665]: pam_unix(cron:session): session closed for user root
Feb 25 02:17:01 revo CRON[673]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 25 02:17:01 revo CRON[673]: pam_unix(cron:session): session closed for user root
Feb 25 03:17:01 revo CRON[682]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 25 03:17:01 revo CRON[682]: pam_unix(cron:session): session closed for user root
Feb 25 04:17:01 revo CRON[690]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 25 04:17:01 revo CRON[690]: pam_unix(cron:session): session closed for user root
Feb 25 05:17:01 revo CRON[699]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 25 05:17:01 revo CRON[699]: pam_unix(cron:session): session closed for user root
Feb 25 06:17:01 revo CRON[708]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 25 06:17:01 revo CRON[708]: pam_unix(cron:session): session closed for user root
Feb 25 06:25:01 revo CRON[713]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 25 06:25:01 revo CRON[713]: pam_unix(cron:session): session closed for user root
Feb 25 07:17:01 revo CRON[719]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 25 07:17:01 revo CRON[719]: pam_unix(cron:session): session closed for user root
Feb 25 07:30:01 revo CRON[725]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 25 07:30:01 revo CRON[725]: pam_unix(cron:session): session closed for user root
Feb 25 07:35:04 revo sudo:     root : TTY=unknown ; PWD=/ ; USER=htpc ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/use_http_proxy
Feb 25 07:35:04 revo sudo:     root : TTY=unknown ; PWD=/ ; USER=htpc ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/host
Feb 25 07:35:04 revo sudo:     root : TTY=unknown ; PWD=/ ; USER=htpc ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port
Feb 25 08:17:01 revo CRON[986]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 25 08:17:01 revo CRON[986]: pam_unix(cron:session): session closed for user root
Feb 25 09:17:01 revo CRON[994]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 25 09:17:01 revo CRON[994]: pam_unix(cron:session): session closed for user root
Feb 25 10:17:01 revo CRON[1003]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 25 10:17:01 revo CRON[1003]: pam_unix(cron:session): session closed for user root
Feb 25 11:17:01 revo CRON[1012]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 25 11:17:01 revo CRON[1012]: pam_unix(cron:session): session closed for user root
Feb 25 12:17:01 revo CRON[1020]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 25 12:17:01 revo CRON[1020]: pam_unix(cron:session): session closed for user root
Feb 25 13:17:01 revo CRON[1029]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 25 13:17:01 revo CRON[1029]: pam_unix(cron:session): session closed for user root
Feb 25 14:17:01 revo CRON[1039]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 25 14:17:01 revo CRON[1039]: pam_unix(cron:session): session closed for user root
Feb 25 15:17:01 revo CRON[1051]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 25 15:17:01 revo CRON[1051]: pam_unix(cron:session): session closed for user root
Feb 25 16:17:01 revo CRON[1062]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 25 16:17:02 revo CRON[1062]: pam_unix(cron:session): session closed for user root
Feb 25 17:17:02 revo CRON[1416]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 25 17:17:02 revo CRON[1416]: pam_unix(cron:session): session closed for user root
Feb 25 17:54:25 revo sshd[1522]: Accepted password for htpc from 192.168.1.103 port 59506 ssh2
Feb 25 17:54:25 revo sshd[1522]: pam_unix(sshd:session): session opened for user htpc by (uid=0)
Feb 25 18:17:01 revo CRON[1735]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 25 18:17:01 revo CRON[1735]: pam_unix(cron:session): session closed for user root
Feb 25 18:24:57 revo sshd[1757]: Accepted password for htpc from 192.168.1.103 port 60048 ssh2
Feb 25 18:24:57 revo sshd[1757]: pam_unix(sshd:session): session opened for user htpc by (uid=0)


```

The rest of my auth logs are similar. A ton of Invalid user... entries. None of them contain an accepted password entry for anyone by my htpc user; all originating from my laptop.

Is anyone familiar with that wicks file? I suspect the perp is gaining entry through it now, though I haven't been able to locate it running or living anywhere. Also, the web history goes back to early January. So he's been playing for a while.

I should consider the possibility that he didn't hack in through my ssh, but rather used a hole when I was playing with the motion (webcam software) server and left it's web ports open for a few weeks. That or some unknown ssh vulnerability, because my username isn't common and my password is reasonably strong (13 chars, upper, lower, numbers, no words or partial words). I've definitely upped my password strength anyways. It takes forever just to type it now.

---

### Post by CharlesA on 2010-02-25
If you are using password logins for SSH, you really should install something like Fail2Ban or DenyHosts which blocks an IP address after a set number of unsuccessful login attempts. For more security, you can use ssh keys instead of passwords.

---

