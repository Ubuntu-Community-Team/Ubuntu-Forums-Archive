---
title: "Is my server under attack?"
date: 2006-10-11
forum: Server Platforms
---

### Post by JSVH on 2006-10-11
Hey, 

I am new to the whole server thing. I have set an old computer (PII 400Mhz) for me to toy around with as a server and host a web site for fun. I installed Ubuntu server and have it set up so I can use ssh and ftp to load my files onto my server.

I noticed that my server was making alot of noise so I decided to check the logs. syslog looked ok, but when I opened auth.log I got:

```
Oct 11 01:06:47 ServerJV vsftpd: (pam_unix) check pass; user unknown
Oct 11 01:06:47 ServerJV vsftpd: (pam_unix) authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=209.67.1.67
Oct 11 01:06:49 ServerJV vsftpd: (pam_unix) check pass; user unknown
Oct 11 01:06:49 ServerJV vsftpd: (pam_unix) authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=209.67.1.67
Oct 11 01:06:51 ServerJV vsftpd: (pam_unix) check pass; user unknown
Oct 11 01:06:51 ServerJV vsftpd: (pam_unix) authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=209.67.1.67
Oct 11 01:06:54 ServerJV vsftpd: (pam_unix) check pass; user unknown
Oct 11 01:06:54 ServerJV vsftpd: (pam_unix) authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=209.67.1.67
Oct 11 01:06:55 ServerJV vsftpd: (pam_unix) check pass; user unknown
Oct 11 01:06:55 ServerJV vsftpd: (pam_unix) authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=209.67.1.67
Oct 11 01:06:58 ServerJV vsftpd: (pam_unix) check pass; user unknown
Oct 11 01:06:58 ServerJV vsftpd: (pam_unix) authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=209.67.1.67
Oct 11 01:07:00 ServerJV vsftpd: (pam_unix) check pass; user unknown
Oct 11 01:07:00 ServerJV vsftpd: (pam_unix) authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=209.67.1.67
Oct 11 01:07:02 ServerJV vsftpd: (pam_unix) check pass; user unknown
Oct 11 01:07:02 ServerJV vsftpd: (pam_unix) authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=209.67.1.67
Oct 11 01:07:04 ServerJV vsftpd: (pam_unix) check pass; user unknown
Oct 11 01:07:04 ServerJV vsftpd: (pam_unix) authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=209.67.1.67
Oct 11 01:07:07 ServerJV vsftpd: (pam_unix) check pass; user unknown
Oct 11 01:07:07 ServerJV vsftpd: (pam_unix) authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=209.67.1.67
Oct 11 01:07:09 ServerJV vsftpd: (pam_unix) check pass; user unknown
Oct 11 01:07:09 ServerJV vsftpd: (pam_unix) authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=209.67.1.67
Oct 11 01:07:11 ServerJV vsftpd: (pam_unix) check pass; user unknown
Oct 11 01:07:11 ServerJV vsftpd: (pam_unix) authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=209.67.1.67
```

...going on for hours. 

I am new to this server thing but this is clearly not right. It looks to me like somebody was trying to get into my server by guessing my password by brute force. I rebooted my server and it seems to have stopped for now.

Is this something I need to worry about? Was this an attack? How can I stop future attacks? Is there a script or something that can automatically block an IP after too many failed password attempts or something?


Thanks!
John

---

### Post by Predius on 2006-10-11
Try reading [this]("http://www.debian-administration.org/articles/342") and see if it works for you. 

The bot probably decided that your system was down and moved on. Do you recognize the ip 209.67.1.67?

---

### Post by JSVH on 2006-10-11
Thanks for the reply,

No, I dont recognize the IP, and each attack is from a different IP. In fact another attack is going on now from a different IP. I am not to worried because given that its 3 seconds between guessses and my password is longer than 10 characters it will take the bot atleaset 347 million years to try every possible password. That, And I dont have anything important on the server.

However it is annoying, that link you sent is exactly what I am looking for. But in the second step when I went to my /etc/inetd.conf it did not have the ssh or ftp entrey that they showed. Do I just need to add them? or do I need to disable "standalone" mode or something?

Again thanks helping out.

John

---

### Post by Endwin on 2006-10-11
I had the problem too with my SSH server that I have open to the net so I can get to the netwoek wherever I am. I installed fail2ban and that helped solve the problem. What it does is look at your logs for whatever you tell it to and then if something fails to log in X times it will block them for a period of time (or forever). 

```
sudo aptitude -R install fail2ban
```

Might be more what you are after.

---

### Post by foxylad on 2006-10-11
My internet exposed server got several attacks a day from bots trying dictionary attacks. I'm a little confused that the attempts on your server have "logname=" - I think that means they are trying to log in with an empty user ID. My solution was to block them at the firewall, so after three connections in five minutes it didn't accept any more. I used this in my iptables script:
```
#------------------------#
# SSH daemon - tcp Port 22 - drop any more than 3 new connections from one address every 5 mins
$IPTABLES -I INPUT -p tcp -i eth+ --dport 22 -m state --state NEW -m recent --set
$IPTABLES -I INPUT -p tcp -i eth+ --dport 22 -m state --state NEW -m recent --update --seconds 300 --hitcount 3 -j DROP
$IPTABLES -A INPUT -p tcp -i eth+ --dport 22 -j ACCEPT
```

---

### Post by JSVH on 2006-10-12
I have been playing around with fail2ban and blockhosts for a day now, I cant get them to block the vsftpd attempts automatically. It looks like they are blocking SSH attacks but nothing on the vsftpd, I have two simultaneous attacks going on right now :( . fail2ban says I just need to edit the configuration file to get it to block vsftpd attacks but I don't see anything on vsftpd.  I see an SSH and an Apache section. Do I need to add my own code or something?

Thanks, 
John

---

### Post by seuaniu on 2006-10-12
The short answer is yes, your server is under attack.  All public facing servers are under attack all of the time :-? .  there are a few things you can do to mitigate the bots out there looking for bad passwords, as you have in your logfile above:

1. choose good passwords.  That means, longer than 8 chars, upper and lower case letters, numbers, and some other chars too, ie n0T_a-bAdpas5woRD, or something similar.

2. Move any services you can to non-standard ports.  This is easy to do with ssh, since presumably you aren't using that for anything other than administration.  FTP and HTTP might not work for this though, since you want regular people to be able to access your server.

3. Use fail2ban or some equivilant.  I use fail2ban on a couple of low-traffic servers that I run at work, and its worked pretty good.  I'm not sure if it has built-in support for vs-ftpd, but it works fine for me with apache2 and proftpd.  either way, if vs-ftpd can output standard logfiles, fail2ban should be compatible with it.  -- Also, check out portsentry and see if its still alive.  That was a good tool back in the day.

4.  use encryption whenever possible.

5.  Get used to it.  Every server connected to the internet gets attacked by bots like these.  Some of the bots are coming from rooted linux servers, so don't let yourself become one of them.  

This type of thing is what makes computer security interesting.  The attack above was one of the less sophisticated types out there.  People with real skills and motivation are the ones you have to worry about, since they will use tools like sniffers and packet-generators to figure out whats *really* going on, and find real weaknesses in your setup.

---

### Post by JSVH on 2006-10-19
I finally got one of these scripts working. The reason I could not get VSFTPD to work in Fail2Ban is because it was not supported in the config file. I found another config file ( [http://www.greenhydrant.com/~drees/stuff/fail2ban.conf](http://www.greenhydrant.com/~drees/stuff/fail2ban.conf) ) and copied the "VSFTPD" section into my config and enabled it. Fail2Ban now blocks brute force attacks on VSFTPD. However I do get an "WARNING: Must have been using old style of failregex! Security Breach! Read README.Debian" error message in the log file (/var/log/fail2ban.log) everytime it does some thing.

I opened up a [bug (#66865)]("https://launchpad.net/distros/ubuntu/+source/fail2ban/+bug/66865") in launchpad since the upstream versions seem to support VSFTPD and many other programs "out of the box".

---

