---
title: "Mdadm postfix notification problem alert"
date: 2008-11-20
forum: Server Platforms
---

### Post by Ocelaris on 2008-11-20
Having trouble sending mail with postfix and mdadm. 

I have postfix working, if I do a test message with telnet 127.0.0.1 25 I can walk through sending an email, and receive that through my ISP's mailhost mail.optimum.net

The problem is when I issue the mdadm "test email" command... I have in my /etc/mdadm/mdadm.conf 

mailaddr [email]myemailaddress@gmail.com[/email]

and a script in /etc/init.d/ called daemonize mdadm (so it'll run automatically)...

Rebooted, and tried doing the 

sudo mdadm --monitor --scan --test /dev/md0 

and it just prompts me for password and then sits there. So I tried --delay=3600  etc...  same thing.

tried looking in /var/log/mail.log  and I did read something about "can't find procmail" command or something, but I really am at a loss, it seems other people get it working all right... but not sure where to check for errors, or how to troubleshoot this.  

I did have sendmail running for a while, but realized postfix was what everyone else was using, so I switched to that. Made sure to do an apt-get autoremove sendmail, make sure ps aux|grep sendmail was not running, did a /etc/init.d/sendmail stop command, and removed the /etc/init.d/sendmail script... And then I rebooted

Even made sure that a netstat -an |grep 25 showed that postfix was running.  I've been searching for a really long time, any help would be appreciated. Bill

---

### Post by fjgaude on 2008-11-21
Seems this  has worked for many:

```
sudo mdadm --monitor --mail=xunil@theanykey.com --delay=30 --scan 
```

There may be more to it.

---

### Post by Ocelaris on 2008-11-21
> **fjgaude said:**
> Seems this  has worked for many:

```
sudo mdadm --monitor --mail=xunil@theanykey.com --delay=30 --scan 
```

There may be more to it.


Yeah, That's the non-daemonized method, which the problem seems to be that you would have to run that every time you reboot? But regardless, I had tried that with the -t (because I want it to send a test email) and same thing, just pauses and waits... 

Where would the mdadm error logs be?

---

### Post by Ocelaris on 2008-11-21
Well, I installed mailx and had 8 mails waiting... Basically I'm to understand that I'm not allowed to have my "from" field equal something which doesn't really exist... they'll let me relay out, but not from an unknown domain. SO... the question is if I do a 

```
 sudo dpkg-reconfigure sendmail 
```

And set my from FQDN to nothing... or gmail.com will it work? We'll find out shortly... But If I'm reading these headers wrong, let me know. Thanks!


<XXX>: host mail.optonline.net[167.206.5.250] said: 550 5.1.8
    invalid/host-not-in-DNS return address not allowed (in reply to MAIL FROM
    command)

--231AE380C6660.1227216911/ubuntu804
Content-Description: Delivery report
Content-Type: message/delivery-status

Reporting-MTA: dns; ubuntu804
X-Postfix-Queue-ID: 231AE380C6660
X-Postfix-Sender: rfc822; [email]XXX[/email]l
Arrival-Date: Thu, 20 Nov 2008 16:26:51 -0500 (EST)

Final-Recipient: rfc822; [email]XXXXX@gmail.com[/email]
Action: failed
Status: 5.1.8
Remote-MTA: dns; mail.optonline.net
Diagnostic-Code: smtp; 550 5.1.8 invalid/host-not-in-DNS return address not

---

### Post by fjgaude on 2008-11-21
Error logs:

/etc/logcheck/ignore.d.server/mdadm
/etc/logcheck/violations.d/mdadm

Maybe they will help you.

---

### Post by Ocelaris on 2008-11-21
thank you. I will give that a shot, but now in messing with postfix I've probably discombobulated it as I can't send out anymore... so going to have a long road ahead...

---

