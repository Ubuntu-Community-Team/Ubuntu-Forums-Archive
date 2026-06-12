---
title: "Firestarter weirdness."
date: 2010-03-16
forum: Security
---

### Post by [censored] on 2010-03-16
According to Firestarter, I have a mysterious http connection to this IP address: 

[IMG]http://i40.tinypic.com/famvxy.jpg[/IMG]

It's always up, regardless of whether there's any browser happening. The connection also doesn't show up in lsof or netstat. Could it be a bug in Firestarter?

It's all a bit creepy, because my ISP has accused me sending email spam. But I wouldn't be surprised at all if they have made a mistake, especially given that they seem to be a bit vague on the details.

Nevertheless, I've taken the precaution opening firestarter and blocking all smtp and pop connections. I've also made outgoing connections restrictive by default.

I also booted up from a live disk, and ran chkrootkit and rkhunter. chkrootkit came back negative. rkhunter gave me a bit of a scare, by warning that all the files in /usr/bin have "been changed". I assume this is a false positive, because rkhunter, freshly installed on a live distro, couldn't possibly know what the files were before.  *touch wood*

ubuntu 9.04

---

### Post by cdenley on 2010-03-16
It looks like that IP is for an ad server. It doesn't seem to respond to vague requests I send it, so I can't say for sure. Did you have a web browser open? If so, what site were you at? I wouldn't be worried about that.

As for sending spam, were you running an MTA?
```

sudo netstat -tlnp

```

---

### Post by [censored] on 2010-03-16
A Mail Transfer Agent, cdenley? No. Not as far as I know. But I think their inference from the people at my ISP is that it's some clever trojan that installs its own.

---

### Post by teward on 2010-03-16
Not to be annoying, but you can use Firestarter to block the outbound traffic to that IP address.

Under policies (or whatever tab that is), you can select "Outbound Network Policy", select the section that lets you specify a website/IP address, add a rule, and block the outbound traffic to that IP.  It will prevent your system from connecting to it, 100% of the time.

Give that a try, and please report back.

---

### Post by cdenley on 2010-03-16
> **'[censored] said:**
> A Mail Transfer Agent, cdenley? No. Not as far as I know.

The command I posted would list anything listening on SMTP. Sometimes it can get installed as a dependency and people don't realize it. Recently, because of a bug, it became a dependency for the chrome browser.
> **'[censored] said:**
> 
But I think their inference from the people at my ISP is that it's some clever trojan that installs its own.
In the windows world, that is usually the case. I would say most linux systems that send spam are because someone didn't know how to configure their MTA, though.

---

### Post by DawieS on 2010-03-16
My guess is that it is a routing server used by one of those chat programs you are running. They normally have daemons running from boot to shutdown.

If you want to make sure, you could block it, and see which application doesn't work anymore. (Rather block the whole range belonging to the same owner, or else it will just select the next available server):
64.236.0.0/16

Another thing that looks a bit strange, is that secure connection you have with one of the Mozilla Firefox servers. If this was done with Firefox, then "**firefox**" should have been listed under **Program**.

---

### Post by OpSecShellshock on 2010-03-16
64.236.144.228 is allocated to AOL. If one of your chat clients uses AIM, that's probably where that's coming from.

63.245.209.92 is an IP address that Firefox checks in with to see if there are updates for your add-ons.

---

### Post by [censored] on 2010-03-16
cdenley did the netstat as you suggested. Here is the result, seems to show a heap of stuff listening...... 

```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:35714           0.0.0.0:*               LISTEN      2771/python     
tcp        0      0 0.0.0.0:44899           0.0.0.0:*               LISTEN      3215/rpc.mountd 
tcp        0      0 0.0.0.0:9988            0.0.0.0:*               LISTEN      2771/python     
tcp        0      0 0.0.0.0:13000           0.0.0.0:*               LISTEN      3084/bearerbox  
tcp        0      0 0.0.0.0:13002           0.0.0.0:*               LISTEN      3084/bearerbox  
tcp        0      0 0.0.0.0:59051           0.0.0.0:*               LISTEN      2303/rpc.statd  
tcp        0      0 0.0.0.0:41775           0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN      2281/portmap    
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      3725/cupsd      
tcp        0      0 127.0.0.1:42007         0.0.0.0:*               LISTEN      3052/hddtemp    
tcp6       0      0 :::139                  :::*                    LISTEN      3281/smbd       
tcp6       0      0 ::1:631                 :::*                    LISTEN      3725/cupsd      
tcp6       0      0 :::445                  :::*                    LISTEN      3281/smbd 
```

---

### Post by [censored] on 2010-03-16
Finally, after a day, I managed to get through to the technical services guy at my ISP. The spamming did occur, but they had the wrong account.

---

### Post by uRock on 2010-03-16
System> Admin> Network Tools is your friend.

---

### Post by cdenley on 2010-03-17
> **'[censored] said:**
> cdenley did the netstat as you suggested. Here is the result, seems to show a heap of stuff listening...... 

```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
**tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN      -          **     
**tcp        0      0 0.0.0.0:35714           0.0.0.0:*               LISTEN      2771/python   **  
tcp        0      0 0.0.0.0:44899           0.0.0.0:*               LISTEN      3215/rpc.mountd 
**tcp        0      0 0.0.0.0:9988            0.0.0.0:*               LISTEN      2771/python     **
tcp        0      0 0.0.0.0:13000           0.0.0.0:*               LISTEN      3084/bearerbox  
tcp        0      0 0.0.0.0:13002           0.0.0.0:*               LISTEN      3084/bearerbox  
tcp        0      0 0.0.0.0:59051           0.0.0.0:*               LISTEN      2303/rpc.statd  
**tcp        0      0 0.0.0.0:41775           0.0.0.0:*               LISTEN      -               **
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN      2281/portmap    
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      3725/cupsd      
tcp        0      0 127.0.0.1:42007         0.0.0.0:*               LISTEN      3052/hddtemp    
tcp6       0      0 :::139                  :::*                    LISTEN      3281/smbd       
tcp6       0      0 ::1:631                 :::*                    LISTEN      3725/cupsd      
tcp6       0      0 :::445                  :::*                    LISTEN      3281/smbd 
```

A few of those look a little suspicious. Also, you should make bearerbox and NFS aren't accessible from the web. No smtp server, though, so if you are sending spam, which apparently isn't the case, it is because of some malware.

---

### Post by teward on 2010-03-17
there's a few suspicious things there.

Python's listening on two ports (suspicious), for one, so kill that process.

---

### Post by [censored] on 2010-03-17
cdenley and TrekCaptainUSA hi I killed the python processes. Also what is bearerbox? 

I have NFS enabled in Firestarter, but it should only be enabled for my other computer (192.168.1.101).

---

### Post by cdenley on 2010-03-17
> **'[censored] said:**
> 
Also what is bearerbox?

I never heard of it. Apparently it is a component of kannel, which I have also not heard of.
[http://packages.ubuntu.com/karmic/kannel](http://packages.ubuntu.com/karmic/kannel)

---

### Post by OpSecShellshock on 2010-03-17
> **cdenley said:**
> I never heard of it. Apparently it is a component of kannel, which I have also not heard of.
[http://packages.ubuntu.com/karmic/kannel](http://packages.ubuntu.com/karmic/kannel)

Wait, so this computer is being used to translate web pages for use in mobile phones? That's a pretty specific type of server that I'd think would require a fairly intense skill set. Might be a good idea to read up on any available documentation for the kannel project and see if there's a way to check for successful connections to mobile phones. It's possible that the server is installed and listening, but nothing is actually able to connect to it. Not sure I'd be satisfied with that, though.

If you didn't install it, and don't intend to be routing web traffic to people's mobile phone browsers, there might be something odd afoot after all.

---

### Post by [censored] on 2010-03-18
> **cdenley said:**
> I never heard of it. Apparently it is a component of kannel, which I have also not heard of.
[http://packages.ubuntu.com/karmic/kannel](http://packages.ubuntu.com/karmic/kannel)

Ah yes. From memory, I think I installed that as a dependency for some utility that was supposed to be able to help me send sms. 

Removed it.

---

