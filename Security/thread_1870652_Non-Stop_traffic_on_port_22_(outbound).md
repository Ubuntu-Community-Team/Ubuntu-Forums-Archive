---
title: "Non-Stop traffic on port 22 (outbound)"
date: 2011-10-27
forum: Security
---

### Post by Anton Wan on 2011-10-27
I have been getting emails from my ISP that my Ubuntu server is sending out ssh traffic trying to get into other servers on the Internet.  I have setup my firewall to block all traffic outbound from it.  This seems to have stopped the outgoing traffic, but it seems that it's overwhelming my firewall.  Slowing down my network.  

This server is also running Moodle, so I don't really want to take it down if possible.  I'm new to Linux and don't really know where to start. I just started here a month ago and don't have much info on the configuration of the server.  I have been bouncing around on the Internet trying to find documentation.  Can only one point me in the right direction?  

Log file from my firewall:

Oct 27 15:12:01 kernel deny out eth1 60 tcp 20 63 172.20.0.16 221.16.221.156 54869 22 syn  
Oct 27 15:12:01 kernel deny out eth1 60 tcp 20 63 172.20.0.16 183.254.156.78 38713 22 syn
Oct 27 15:12:01 kernel deny out eth1 60 tcp 20 63 172.20.0.16 36.187.94.202 55067 22 syn

Thanks in Advance,

Anton

---

### Post by Dangertux on 2011-10-27
There is a chance your ssh server was cracked or is in the process of being cracked you need to check /var/log/auth.log for failed login attempts or authentication as a user from an ip other than yours. 

This is particularly likely if you are using passwords instead of keys.

---

### Post by CharlesA on 2011-10-27
> **Dangertux said:**
> There is a chance your ssh server was cracked or is in the process of being cracked you need to check /var/log/auth.log for failed login attempts or authentication as a user from an ip other than yours. 

This is particularly likely if you are using passwords instead of keys.
This would be my first thought as well.

Check the auth logs and see if someone got in.

---

### Post by Anton Wan on 2011-10-28
Thanks for the response.  I did check this log and I do see attempts trying to get in, but that's it.  I do notice that these are showing up:

Oct 28 10:35:01 web CRON[17890]: pam_unix(cron:session): session opened for user root by (uid=0)
Oct 28 10:35:04 web CRON[17890]: pam_unix(cron:session): session closed for user root
Oct 28 10:39:01 web CRON[17915]: pam_unix(cron:session): session opened for user root by (uid=0)
Oct 28 10:39:01 web CRON[17915]: pam_unix(cron:session): session closed for user root
Oct 28 10:40:01 web CRON[17925]: pam_unix(cron:session): session opened for user root by (uid=0)


What are these?

Thanks,

Anton

---

### Post by CharlesA on 2011-10-28
> **Anton Wan said:**
> Thanks for the response.  I did check this log and I do see attempts trying to get in, but that's it.  I do notice that these are showing up:

Oct 28 10:35:01 web CRON[17890]: pam_unix(cron:session): session opened for user root by (uid=0)
Oct 28 10:35:04 web CRON[17890]: pam_unix(cron:session): session closed for user root
Oct 28 10:39:01 web CRON[17915]: pam_unix(cron:session): session opened for user root by (uid=0)
Oct 28 10:39:01 web CRON[17915]: pam_unix(cron:session): session closed for user root
Oct 28 10:40:01 web CRON[17925]: pam_unix(cron:session): session opened for user root by (uid=0)


What are these?

Thanks,

Anton
Just cron running. My logs say the same thing.

---

### Post by secret resistor on 2011-10-31
Most likely your server has been compromised and is probing other machines for weak ssh passwords (and reporting results to somebody). Assuming that the attempts are still being made you can see the the ones in progress with netstat:
```
sudo netstat -np --protocol=inet
```Then look for entries with outgoing port 22 and check the "PID/Program name" column to see what is generating them. Note that if your firewall is blocking them with a REJECT rule you will probably not see anything there because the connection would be dropped right away. In this case you may want to temporarily change the rule to use DROP which will keep the connection attempt for some time, giving you a chance to see it with netstat (but still won't actually let any packets out).

As for how they got in - it could be through your own ssh server like others said, in which case there should be something in the auth logs (unless they got root and are modifying the logs) but the most likely case is they got in through some unpatched web service. You should make sure that any web-based applications that you are running are always updated.

---

### Post by clurect on 2011-10-31
I cannot really help you with your current problem, but if you want to help lessen your chances of getting an attack change you ssh port to something different than 22. I have been told this is a simple way to thwart a lot of cracks.

---

### Post by CharlesA on 2011-10-31
> **clurect said:**
> I cannot really help you with your current problem, but if you want to help lessen your chances of getting an attack change you ssh port to something different than 22. I have been told this is a simple way to thwart a lot of cracks.
Only works for bots. It's a form of security through obscurity and won't work if someone really wants to get in.

You are better off securing your ssh server in the first place.

---

### Post by Dangertux on 2011-10-31
Basic SSH hardening is the best bet here

- Use keys
- Use denyhosts/fail2ban to prevent brute force
- Rate limit via iptables (not really necessary if you use fail2ban/denyhosts)
- limit the connection accepted to a certain group of IP's (if you can) via iptables.
- no root login 


Should be more than enough, changing the standard port doesn't really help you all that much.

---

### Post by CharlesA on 2011-10-31
> **Dangertux said:**
> Basic SSH hardening is the best bet here

- Use keys
- Use denyhosts/fail2ban to prevent brute force
- Rate limit via iptables (not really necessary if you use fail2ban/denyhosts)
- limit the connection accepted to a certain group of IP's (if you can) via iptables.
- no root login 


Should be more than enough, changing the standard port doesn't really help you all that much.

I just use iptables to drop any connections from an IP that connects more then 3 times in 60 seconds instead of using fail2ban or denyhosts.

I also use AllowUser to limit who can login, in addition to using keys instead of passwords.

---

