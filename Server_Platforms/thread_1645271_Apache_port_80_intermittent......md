---
title: "Apache port 80 intermittent....."
date: 2010-12-14
forum: Server Platforms
---

### Post by rectifiercc on 2010-12-14
I have an Apache2 webserver that works flawlessly on my LAN on port 80 but when I try to access from outside my LAN (say on my iphone) sometimes it works and sometimes it doesn't. I have to keep reloading the page over and over until it finally lets me access it. I thought it might have been my password protection on certain folders but I removed that and no change. Other people on their computers are having the same issues accessing my site. Sometimes they can connect, other times error messages (can't connect etc).

So I did an experiment and changed the port config on Apache to accept on port 3352 (a random number) and it works perfectly. The drag is I have to append :3352 to all my URLs.

Anyone know why this is off the top of their heads?

I also rebooted my router and checked the firewall rules.

I don't remember this problem when I first installed months ago. Seemed like it was working back then.

Is there a way to tell if some other program is accessing port 80?

thx

---

### Post by arrrghhh on 2010-12-14
You can do a netstat to see if anything else is functioning on port 80.

One culprit may be that router...

However, if it works on your LAN have you ruled out your ISP?  A lot of ISPs that sell residental connections won't let you run a webserver, ftp server, etc...

---

### Post by rectifiercc on 2010-12-14
Yes I wondered about my ISP. I'm using AT&T. I will do a search to see if they block it. Like I said if it were blocked then would I be able to connect at all using port 80 outside my LAN. I guess a good way to check my router would be to connect without it.

Here is my netstat listening info. I see my 3352 listening but I don't see any port 80 listens:

```
sudo netstat --tcp --listening
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 *:microsoft-ds          *:*                     LISTEN     
tcp        0      0 localhost:10023         *:*                     LISTEN     
tcp        0      0 localhost:10024         *:*                     LISTEN     
tcp        0      0 localhost:10025         *:*                     LISTEN     
tcp        0      0 localhost:mysql         *:*                     LISTEN     
tcp        0      0 *:netbios-ssn           *:*                     LISTEN     
tcp        0      0 localhost:spamd         *:*                     LISTEN     
tcp        0      0 *:ssh                   *:*                     LISTEN     
tcp        0      0 *:ipp                   *:*                     LISTEN     
tcp        0      0 *:3352                  *:*                     LISTEN     
tcp        0      0 *:smtp                  *:*                     LISTEN     
tcp6       0      0 [::]:9412               [::]:*                  LISTEN     
tcp6       0      0 [::]:4040               [::]:*                  LISTEN     
tcp6       0      0 [::]:5900               [::]:*                  LISTEN     
tcp6       0      0 [::]:pop3               [::]:*                  LISTEN     
tcp6       0      0 [::]:imap2              [::]:*                  LISTEN     
tcp6       0      0 [::]:37427              [::]:*                  LISTEN     
tcp6       0      0 [::]:ftp                [::]:*                  LISTEN     
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN     
tcp6       0      0 [::]:ipp                [::]:*                  LISTEN     
tcp6       0      0 [::]:smtp               [::]:*                  LISTEN     

```

---

### Post by arrrghhh on 2010-12-15
> **rectifiercc said:**
> Yes I wondered about my ISP. I'm using AT&T. I will do a search to see if they block it. Like I said if it were blocked then would I be able to connect at all using port 80 outside my LAN. I guess a good way to check my router would be to connect without it.

Here is my netstat listening info. I see my 3352 listening but I don't see any port 80 listens:

OK, so it would appear your machine is fine - what about your router or any other devices that could potentially have a web interface that are listening on port 80?

---

### Post by rectifiercc on 2010-12-15
Yeah good point. I have 2 security webcams that are on ports 81 and 82. They send images via ftp, samba, and email. They have a web admin interface. I wonder if that's problem. I'll try unpluggin them for now and see if that fixes anything.

thx

---

### Post by rectifiercc on 2010-12-21
OK so the problem is due to my securtiy cams I believe, They are set up for port 81 and 82 but for some reason they're interupting port 80. I don't have a fix yet but at least I know that if I unplug them my http port 80 works perfectly. So weird!

---

### Post by arrrghhh on 2010-12-22
> **rectifiercc said:**
> OK so the problem is due to my securtiy cams I believe, They are set up for port 81 and 82 but for some reason they're interupting port 80. I don't have a fix yet but at least I know that if I unplug them my http port 80 works perfectly. So weird!

They must have some backdoor or something else enabled that's causing them to listen on port 80... Glad you've found it, at least that brings some closure to the issue ;)

If you feel the thread is solved, use the "Thread Tools" drop-down to mark it [SOLVED]!

---

### Post by rectifiercc on 2010-12-22
I will mark as solved since i know what the problem is but I still gotta figure out how to make the webcams behave with apache :-)
thx

---

