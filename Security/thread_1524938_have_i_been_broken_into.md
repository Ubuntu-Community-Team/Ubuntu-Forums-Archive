---
title: "have i been broken into?"
date: 2010-07-06
forum: Security
---

### Post by jonny.milano on 2010-07-06
well, i'm a noob. i thought that i had been careful.. i thought that i knew what i was doing. i installed fail2ban... thing is, i'm still learning. i don't keep ANY important information on my hobby server but still, i like to think it's secure. i need your help. does this look like a security break?

```

Jul  4 07:35:04 XXXX sudo:     root : TTY=unknown ; PWD=/ ; USER=XXXX ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/use_http_proxy
Jul  4 07:35:04 XXXX sudo: pam_unix(sudo:session): session opened for user XXXX by (uid=0)
Jul  4 07:35:04 XXXX sudo: pam_unix(sudo:session): session closed for user XXXX
Jul  4 07:35:04 XXXX sudo:     root : TTY=unknown ; PWD=/ ; USER=XXXX ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/host
Jul  4 07:35:04 XXXX sudo: pam_unix(sudo:session): session opened for user XXXX by (uid=0)
Jul  4 07:35:04 XXXX sudo: pam_unix(sudo:session): session closed for user XXXX
Jul  4 07:35:04 XXXX sudo:     root : TTY=unknown ; PWD=/ ; USER=XXXX ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port
Jul  4 07:35:04 XXXX sudo: pam_unix(sudo:session): session opened for user XXXX by (uid=0)
Jul  4 07:35:04 XXXX sudo: pam_unix(sudo:session): session closed for user XXXX
Jul  4 07:39:01 XXXX CRON[11379]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul  4 07:39:01 XXXX CRON[11379]: pam_unix(cron:session): session closed for user root
Jul  4 08:09:01 XXXX CRON[12736]: pam_unix(cron:session): session opened for user root by (uid=0)

```

or this....?

```

Jul  5 12:22:45 XXXX sshd[5552]: Server listening on :: port 22.
Jul  5 12:22:46 XXXX sshd[5552]: error: Bind to port 22 on 0.0.0.0 failed: Address already in use.
Jul  5 12:23:11 XXXX gdm[6354]: pam_unix(gdm-autologin:session): session opened for user XXXX by (uid=0)
Jul  5 12:28:00 XXXX sudo: pam_unix(sudo:auth): authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=  user=XXXX
Jul  5 20:05:52 XXXX sshd[5557]: Server listening on :: port 22.
Jul  5 20:05:52 XXXX sshd[5557]: error: Bind to port 22 on 0.0.0.0 failed: Address already in use.
Jul  5 20:06:17 XXXX gdm[6370]: pam_unix(gdm-autologin:session): session opened for user XXXX by (uid=0)
Jul  5 20:09:01 XXXX CRON[7195]: pam_unix(cron:session): session opened for user root by (uid=0)

```

i really am grateful for ubuntu forums. thank you in advance for your help.

---

### Post by clrg on 2010-07-06
The authentication messages indicate that someone is using sudo, most likely you.

```
Jul  4 07:35:04 XXXX sudo: pam_unix(**sudo**:session): session opened for user XXXX by (uid=0)
```The port error messages indicates that a service wants to listen on port 22 of your machine, but that port is already taken. Did you configure anything besides SSH to listen on that port? Or did you try to start another instance of SSH on the same port? That might be an explanation.

Based on this, I don't think your security has been compromised. If you want to make sure, change your passwords and check for running services not started by you (for example, a telnet server listening on a high port). To check who's logged in, just type "who" in the terminal.

---

### Post by Rubi1200 on 2010-07-06
Hi,
you could also look at the output from the following commands:

```
lastlog
```

```
sudo lsof -i -n -P
```

---

### Post by cdenley on 2010-07-06
> **clrg said:**
> The authentication messages indicate that someone is using sudo, most likely you.

Actually, that is the update manager checking his proxy settings. I see nothing suspicious, except maybe the fact you seem to have two servers trying to listen on the same port.
```

sudo netstat -tlnp

```

---

### Post by FuturePilot on 2010-07-06
> **cdenley said:**
> Actually, that is the update manager checking his proxy settings. I see nothing suspicious, except maybe the fact you seem to have two servers trying to listen on the same port.
```

sudo netstat -tlnp

```

I agree. That command that is being run is part of update-manager. I don't see anything suspicious either. Though you might want to figure out what other thing you have trying to run on port 22.

---

### Post by jonny.milano on 2010-07-06
clrg - Thank you so much! I didn't know I could type "who" into a terminal!! Also, I did not configure anything to extra to run on port 22... I find this strange. Im new, so I wouldn't even know how to check.. But THANK YOU!! :) 

Rubi1200 - I will try these commands but it will have to wait until I am back home as I closed port 22 (ssh) on my router. I will do this at the actual machine. 

cdenley - Same as above: I will try these commands but it will have to wait until I am back home as I closed port 22 (ssh) on my router. I will do this at the actual machine.

FuturePilot - Do you know how I could find out what is trying to run on the same port as SSH?

ALL - I have a Desktop installed on this machine as it performs other functions (playing videos, etc.). One thing that concerns me are the instances of gconftool and gdm, such as:

"Jul  5 12:23:11 XXXX gdm[6354]: pam_unix(gdm-autologin:session): session opened for user XXXX by (uid=0)"

Does gdm not stand for Gnome Desktop Manager? This would lead me to believe someone is trying to break in via Remote Desktop.. Or, am I paranoid?? 

Again, thank you all and thank you UbuntuForums - have saved me so many times!! I hope one day to give back... JM

---

### Post by cdenley on 2010-07-06
> **jonny.milano said:**
> 
FuturePilot - Do you know how I could find out what is trying to run on the same port as SSH?

You were already given two different commands to accomplish this.

> **jonny.milano said:**
> 
ALL - I have a Desktop installed on this machine as it performs other functions (playing videos, etc.). One thing that concerns me are the instances of gconftool and gdm, such as:

"Jul  5 12:23:11 XXXX gdm[6354]: pam_unix(gdm-autologin:session): session opened for user XXXX by (uid=0)"

Does gdm not stand for Gnome Desktop Manager? This would lead me to believe someone is trying to break in via Remote Desktop.. Or, am I paranoid?? 


GDM is the default login manager for people locally logging in. That looks like you enabled auto-login as user XXXX, so GDM must have been started at that time. GDM is not related to "Remote Desktop".

---

### Post by jonny.milano on 2010-07-07
Again, thank you guys so much. This has helped my learning. If there's anything I can do for you, let me know! I see only one instance of port 22:

sudo netstat -tlnp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:49152           0.0.0.0:*               LISTEN      5977/mediatomb  
tcp        0      0 0.0.0.0:47840           0.0.0.0:*               LISTEN      4920/rpc.statd  
tcp        0      0 0.0.0.0:49251           0.0.0.0:*               LISTEN      20440/python2.4 
tcp        0      0 127.0.0.1:8100          0.0.0.0:*               LISTEN      7305/soffice.bin
tcp        0      0 0.0.0.0:49256           0.0.0.0:*               LISTEN      20401/python2.4 
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      5705/mysqld     
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      6047/smbd       
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN      4902/portmap    
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      6512/apache2    
tcp        0      0 0.0.0.0:51413           0.0.0.0:*               LISTEN      7079/transmission
tcp        0      0 192.168.1.57:53         0.0.0.0:*               LISTEN      5531/named      
tcp        0      0 192.168.1.101:53        0.0.0.0:*               LISTEN      5531/named      
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      5531/named      
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      5828/cupsd      
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN      5531/named      
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      6047/smbd       
tcp6       0      0 :::52387                :::*                    LISTEN      5792/java       
tcp6       0      0 :::50500                :::*                    LISTEN      5792/java       
tcp6       0      0 127.0.0.1:8005          :::*                    LISTEN      5792/java       
tcp6       0      0 :::50501                :::*                    LISTEN      5792/java       
tcp6       0      0 :::50502                :::*                    LISTEN      5792/java       
tcp6       0      0 :::50503                :::*                    LISTEN      5792/java       
tcp6       0      0 :::50504                :::*                    LISTEN      5792/java       
tcp6       0      0 :::50505                :::*                    LISTEN      5792/java       
tcp6       0      0 :::50506                :::*                    LISTEN      5792/java       
tcp6       0      0 :::50507                :::*                    LISTEN      5792/java       
tcp6       0      0 :::59661                :::*                    LISTEN      5792/java       
tcp6       0      0 :::50510                :::*                    LISTEN      6062/java       
tcp6       0      0 :::44687                :::*                    LISTEN      6062/java       
tcp6       0      0 :::8080                 :::*                    LISTEN      5792/java       
tcp6       0      0 :::8180                 :::*                    LISTEN      6062/java       
tcp6       0      0 :::21                   :::*                    LISTEN      6423/proftpd: (acce
tcp6       0      0 :::53                   :::*                    LISTEN      5531/named      
tcp6       0      0 :::22                   :::*                    LISTEN      5557/sshd       
tcp6       0      0 ::1:953                 :::*                    LISTEN      5531/named

---

### Post by cdenley on 2010-07-07
That output shows sshd is already running. Someone or something was trying to run another instance of it. Did you run the "sshd" command by any chance? Servers you install should be started automatically, and should be stopped, started, or restarted using the "service" command in ubuntu 10.04.

---

### Post by jonny.milano on 2010-07-07
Hmmm... I rebooted and got this output. I'm going to put my paranoia to rest now. Although, it is strange.. I don't want to take up any more of your time. I really appriciate the help and I will give back to the forums when I have more to offer.

---

### Post by Rubi1200 on 2010-07-07
If you have not done so already, this makes for essential reading:

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

