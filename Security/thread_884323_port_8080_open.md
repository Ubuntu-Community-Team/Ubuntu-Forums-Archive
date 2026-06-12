---
title: "port 8080 open?"
date: 2008-08-08
forum: Security
---

### Post by Ezrah on 2008-08-08
a scan of my friends machine returns: 

jake@cold:~$ nmap -v -sV -PN machine

Starting Nmap 4.53 ( [http://insecure.org](http://insecure.org) ) at 2008-08-08 19:54 CDT
Initiating Parallel DNS resolution of 1 host. at 19:54
Completed Parallel DNS resolution of 1 host. at 19:54, 0.05s elapsed
Initiating Connect Scan at 19:54
Scanning machine (machine) [1714 ports]
Connect Scan Timing: About 8.46% done; ETC: 20:00 (0:05:25 remaining)
Discovered open port 8080/tcp on machine
Connect Scan Timing: About 66.72% done; ETC: 19:56 (0:00:40 remaining)
Completed Connect Scan at 19:56, 123.15s elapsed (1714 total ports)
Initiating Service scan at 19:56
Scanning 1 service on machine (machine)
Completed Service scan at 19:56, 4.97s elapsed (1 service on 1 host)
SCRIPT ENGINE: Initiating script scanning.
Host machine (machine) appears to be up ... good.
Interesting ports on machine (machine):
Not shown: 1713 filtered ports
PORT     STATE SERVICE    VERSION
8080/tcp open  tcpwrapped (tcpwrapped also showed up as http-proxy? on another scan also.)

Read data files from: /usr/share/nmap
Service detection performed. Please report any incorrect results at [http://insecure.org/nmap/submit/](http://insecure.org/nmap/submit/) .
Nmap done: 1 IP address (1 host up) scanned in 128.240 seconds 

i don't think that is good, advice?

---

### Post by Oldsoldier2003 on 2008-08-09
> **Ezrah said:**
> a scan of my friends machine returns: 

jake@cold:~$ nmap -v -sV -PN machine

Starting Nmap 4.53 ( [http://insecure.org](http://insecure.org) ) at 2008-08-08 19:54 CDT
Initiating Parallel DNS resolution of 1 host. at 19:54
Completed Parallel DNS resolution of 1 host. at 19:54, 0.05s elapsed
Initiating Connect Scan at 19:54
Scanning machine (machine) [1714 ports]
Connect Scan Timing: About 8.46% done; ETC: 20:00 (0:05:25 remaining)
Discovered open port 8080/tcp on machine
Connect Scan Timing: About 66.72% done; ETC: 19:56 (0:00:40 remaining)
Completed Connect Scan at 19:56, 123.15s elapsed (1714 total ports)
Initiating Service scan at 19:56
Scanning 1 service on machine (machine)
Completed Service scan at 19:56, 4.97s elapsed (1 service on 1 host)
SCRIPT ENGINE: Initiating script scanning.
Host machine (machine) appears to be up ... good.
Interesting ports on machine (machine):
Not shown: 1713 filtered ports
PORT     STATE SERVICE    VERSION
8080/tcp open  tcpwrapped (tcpwrapped also showed up as http-proxy? on another scan also.)

Read data files from: /usr/share/nmap
Service detection performed. Please report any incorrect results at [http://insecure.org/nmap/submit/](http://insecure.org/nmap/submit/) .
Nmap done: 1 IP address (1 host up) scanned in 128.240 seconds 

i don't think that is good, advice?

Is he running a webserver on :8080?

---

### Post by brian_p on 2008-08-09
> **Ezrah said:**
> a scan of my friends machine returns: 

Was the scanned machine on your network?

> 8080/tcp open  tcpwrapped (tcpwrapped also showed up as http-proxy? on another scan also.)

A little confusing: the bit in brackets is not from netstat.

> i don't think that is good, advice?

If your friend wants to have a service on port 8080 it very good. If he doesn't - turn it off.

---

### Post by Ezrah on 2008-08-09
He has a very basic install of Hardy, and he lacks the experience to set up a server. 


Quote:
Originally Posted by Ezrah View Post
a scan of my friends machine returns:
Was the scanned machine on your network? 

no, that was a scan over the internet. 


Quote:
8080/tcp open tcpwrapped (tcpwrapped also showed up as http-proxy? on another scan also.)
A little confusing: the bit in brackets is not from netstat.
 
sorry, the note was written by me. netstat returned both "tcpwrapper" AND "http-proxy?" as results. 


Quote:
i don't think that is good, advice?
If your friend wants to have a service on port 8080 it very good. If he doesn't - turn it off. 

i am sure he doesn't, mind telling me how to disable that port using UFW?

---

### Post by brian_p on 2008-08-09
> **Ezrah said:**
> 

no, that was a scan over the internet.

So do we assume the computer is connected directly to the internet or does the scan hit a router first?

> netstat returned both "tcpwrapper" AND "http-proxy?" as results. 

I have seen this when a **router** has been scanned. Port 8080 enables the router to be administered remotely .

> 
i am sure he doesn't, mind telling me how to disable that port using UFW?

Using UFW is completely unnecessary.

```
sudo lsof -i :8080
```

to find the name of the service. Then stop and remove the service. That's if the service is really running on the computer. If it is on the router it needs stopping from there.

ADDED LATER:

http://<the_ip_of_your_friend>:8080

would be revealing.

---

