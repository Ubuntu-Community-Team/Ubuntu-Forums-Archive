---
title: "Trying to brute force me!!!!"
date: 2007-06-20
forum: Server Platforms
---

### Post by umattu on 2007-06-20
Hi all,

I run a Dapper LAMP server from home, I use it for a family website, I also have an ftp server on it as well as ssh. The ssh server alIows my account only, and the ftp has no annonymous loggin and only has 2 accounts, mine and a good friend. I have been checking my auth.log and have been seeing, what I beleive to be someone trying to brute force my ftp and ssh servers. 

Here is a snippet from ssh:

Jun 18 21:46:50 ubuntu-server sshd[7918]: reverse mapping checking getaddrinfo for 203-81-23-9.net-infinity.net failed - POSSIBLE BREAKIN ATTEMPT!
Jun 18 21:46:50 ubuntu-server sshd[7918]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=203.81.23.9  user=root
Jun 18 21:46:52 ubuntu-server sshd[7918]: Failed password for root from 203.81.23.9 port 47735 ssh2
Jun 18 21:47:01 ubuntu-server sshd[7920]: reverse mapping checking getaddrinfo for 203-81-23-9.net-infinity.net failed - POSSIBLE BREAKIN ATTEMPT!
Jun 18 21:47:01 ubuntu-server sshd[7920]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=203.81.23.9  user=root
Jun 18 21:47:03 ubuntu-server sshd[7920]: Failed password for root from 203.81.23.9 port 49129 ssh2


more

Jun 20 00:02:28 ubuntu-server sshd[13454]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.178.108.204 
Jun 20 00:02:30 ubuntu-server sshd[13454]: Failed password for invalid user pgsql from 61.178.108.204 port 59841 ssh2
Jun 20 00:02:32 ubuntu-server sshd[13456]: Invalid user photo from 61.178.108.204
Jun 20 00:02:32 ubuntu-server sshd[13456]: reverse mapping checking getaddrinfo for 204.108.178.61.dail.qy.gs.dynamic.163data.com.cn failed - POSSIBLE BREAKIN ATTEMPT!
Jun 20 00:02:32 ubuntu-server sshd[13456]: (pam_unix) check pass; user unknown
Jun 20 00:02:32 ubuntu-server sshd[13456]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.178.108.204 
Jun 20 00:02:34 ubuntu-server sshd[13456]: Failed password for invalid user photo from 61.178.108.204 port 59933 ssh2
Jun 20 00:02:36 ubuntu-server sshd[13458]: Invalid user scott from 61.178.108.204
Jun 20 00:02:36 ubuntu-server sshd[13458]: reverse mapping checking getaddrinfo for 204.108.178.61.dail.qy.gs.dynamic.163data.com.cn failed - POSSIBLE BREAKIN ATTEMPT!
Jun 20 00:02:36 ubuntu-server sshd[13458]: (pam_unix) check pass; user unknown
Jun 20 00:02:36 ubuntu-server sshd[13458]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.178.108.204 
Jun 20 00:02:38 ubuntu-server sshd[13458]: Failed password for invalid user scott from 61.178.108.204 port 60017 ssh2
Jun 20 00:02:40 ubuntu-server sshd[13460]: Invalid user scott from 61.178.108.204
Jun 20 00:02:40 ubuntu-server sshd[13460]: reverse mapping checking getaddrinfo for 204.108.178.61.dail.qy.gs.dynamic.163data.com.cn failed - POSSIBLE BREAKIN ATTEMPT!
Jun 20 00:02:40 ubuntu-server sshd[13460]: (pam_unix) check pass; user unknown

and ftp

Jun 20 18:05:30 ubuntu-server vsftpd: (pam_unix) authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=59.107.0.190 
Jun 20 18:05:33 ubuntu-server vsftpd: (pam_unix) check pass; user unknown
Jun 20 18:05:33 ubuntu-server vsftpd: (pam_unix) authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=59.107.0.190 
Jun 20 18:05:35 ubuntu-server vsftpd: (pam_unix) check pass; user unknown
Jun 20 18:05:35 ubuntu-server vsftpd: (pam_unix) authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=59.107.0.190 
Jun 20 18:05:37 ubuntu-server vsftpd: (pam_unix) check pass; user unknown

none of the attempts have been successful. As I said ssh only allows my account and the ftp mine and a friends. It is my beleif that they would have to be able to crack one of these 2 accounts to get in. Is this correct?

 Today when I came home I saw the above attempts happening, so I went into my router settings and blocked that IP. I am sure who ever is doing this is using a proxy, so they most likely will be back.

My passwords are tough, I keep everything nice and locked up.

What can I do to really give this chump a run for his/her money? Is it possible for me to retaliate in some way, or even track them down? I would really like to cause this person some grief. Put them on a wild goose chase or something.

Any advice will be GREATLY appreciated!!!!!!

---

### Post by srt4play on 2007-06-21
It probably is a bot, I see it all the time also on my ssh server. There's really nothing you can do about it besides keep a really strong password.

---

### Post by Mr. C. on 2007-06-21
Unfortunately it is common and usual.  There are numerous bot'd machines runnng scripts trying large lists of username/password combinations.  Their goal is to find any easy target.

[LIST]
[*]Keep strong passwords.
[*]If possible, limit incoming IPs to only those that are required.
[*]Change your SSH port to (eg. 221, 222) to avoid the automated attacks.
[/LIST]

Or just learn to ignore the noise.

MrC

---

### Post by chris.zeman on 2007-06-21
I wouldn't worry too much about it. I see that happening on my servers all the time. Like srt4play said, it's probably just a bot. You could always set something up so an IP Address gets blocked for a period of time after a set amount of failed login attempts. That might be the best thing you could do.

Chris

---

### Post by gaten on 2007-06-21
Here are my suggestions (some were mentioned already)

[LIST=1]
[*]Change the default ssh port. This is probably the easiest thing to do and it's also fairly effective at keeping the script kiddies away.
[*]Use public key authentication *only*. Completely disable passwords.
[*]Setup fail2ban (it's in the repos). It will detect ssh login attempt and ban the IP address after so many bogus tries.[/LIST]See the tutorial I wrote in my sig, it tells you how to do everything above but setup Fail2ban (which is very easy, just look through the readme file and the config file).

---

### Post by umattu on 2007-06-21
Thanks for the reassurance. 

I have had this server up and running for like 6months now and this last week is the first time I have seen this, and got a little worried.

---

### Post by netlogic on 2007-06-21
I believe ssh is the securest protocol for management, tunneling, and file transfer.
If you properly configured your ssh, you got nothing to worry about. That is just few static noises from the net. In large corporations, you will get around 45,000 attempts a day.

Few recommendations.
1. limit who can use ssh
2. limit ip ranges that can connect to your sshd server
3. change your port to higher ports like 15578
4. turn off X forwarding if you don't use it
5. do not allow root login through ssh
6. use Key-Based Authentication (guessing 2048 bit will take many centuries).
7. Disabling Password Authentication 
8, install denyhosts

---

### Post by HermanAB on 2007-06-21
In short, don't use FTP.  Use SSH instead.  
Don't use SSH passwords.  Use public keys instead.

See this: [http://aeronetworks.ca/ssh-kiddies.html](http://aeronetworks.ca/ssh-kiddies.html)

Cheers,

Herman

---

### Post by umattu on 2007-06-21
> **HermanAB said:**
> In short, don't use FTP.  Use SSH instead.  
Don't use SSH passwords.  Use public keys instead.

See this: [http://aeronetworks.ca/ssh-kiddies.html](http://aeronetworks.ca/ssh-kiddies.html)

Cheers,

Herman

How would I go about using ssh to transfer files, like on ftp? I use ssh to remotely manage my server. I have never used it for file transfer, honestly I didn't know it could.

---

### Post by vexorian on 2007-06-21
nautilus can connect using ssh, also winscp I think.

But I would simply change the port...

And yes, it is to worry since even though it is unlikely the bot will find the password out it consumes system resources... tiny ones but still...

---

### Post by netlogic on 2007-06-21
sftp works like ftp. it is mostly the same commands with less stuff to worry about. it is easier than ftp. never use ftp. people stop using ftp for a personal account in the late 90s. ftp is only usable with ssl or you are looking to setup an anonymous download. NEVER USE FTP that is associated with your ssh account.

---

### Post by umattu on 2007-06-21
> **vexorian said:**
> nautilus can connect using ssh, also winscp I think.

But I would simply change the port...

And yes, it is to worry since even though it is unlikely the bot will find the password out it consumes system resources... tiny ones but still...

you know now that I ethink about it I have usedd ssh that way, when I first got the server running I would get to my drives via ssh on my desktop. Thanks man!!!!!

---

