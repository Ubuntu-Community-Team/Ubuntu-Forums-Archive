---
title: "SSH Server note letting me in"
date: 2005-01-06
forum: Server Platforms
---

### Post by nder on 2005-01-06
I installed openssh-server last night and everything seemed to be fine.  I could connect to my machine from my home lan.  However, once I try an external connection (I tried connecting back to my box using my external IP address) I get an access denied when I enter my password.  It asks for my username and password (which I have entered correctly) and then I get access denied.

My Router's NAT has been configured to place my computer in the DMZ, so everything gets through to it.  My software firewall (Firestarter) has been configured to allow SSH (on port 22) and the rules have been applied.  When I do a port scan (from work) the port is reported as open (not filtered).

I am trying to connect from work right now on a Windows 2000 box using PuTTY.  When I first attempeted a connection it warned me about the absense of the public key and I told it to get it which it did.  Then I tried login and it failed.

So I've got a couple of questions:

1. Does that fact that it asked me for my key and then prompted me to login mean that I am in fact connecting to my box (i.e. I do not have a firewall issue)

2. If I am in fact connecting to my box, why is my login failing for my user account?  The account I am using the the one I setup when installing.  It has a password, and its the one I sudo from.  I can connect using this account when doing a loopback connection.

3. Do the host files (hosts, hosts.allow, hosts.deny) have anything to do with connecting to the SSH server from outside?  If so, what changes do I need to make to them?

---

### Post by fng on 2005-01-06
reply @ 1 : I guess you are
To be sure :
```
fng@butters:~/var/log $ tail -n 100 /var/log/auth.log | grep sshd
Jan  6 10:52:38 localhost sshd[19191]: Accepted keyboard-interactive/pam for fng from ::ffff:xxx.xxx.xxx.xxx port 40515 ssh2
Jan  6 10:52:38 localhost sshd[19196]: (pam_unix) session opened for user fng by (uid=0)
Jan  6 18:22:18 localhost sshd[19196]: (pam_unix) session closed for user fng
Jan  6 20:00:06 localhost sshd[25584]: Received signal 15; terminating.
Jan  6 20:19:21 localhost sshd[4772]: Server listening on :: port 22.
fng@butters:/var/log $
``` 

If 100 lines arent enough, you can take a bigger number :)
Look for the Accepted Line (the first line in the example). That means you had some sort of connection with your ubuntu-box.

If you can confirm you connected to your box, look in the /var/log/auth.log file beneath the accepted file.  I guess there will be some message why the login failed.      i'm not sure.

---

### Post by nder on 2005-01-06
> **fng]reply @ 1 : I guess you are
To be sure :
```
fng@butters:~/var/log $ tail -n 100 /var/log/auth.log | grep sshd
Jan  6 10:52:38 localhost sshd[19191]: Accepted keyboard-interactive/pam for fng from ::ffff:xxx.xxx.xxx.xxx port 40515 ssh2
Jan  6 10:52:38 localhost sshd[19196]: (pam_unix) session opened for user fng by (uid=0)
Jan  6 18:22:18 localhost sshd[19196]: (pam_unix) session closed for user fng
Jan  6 20:00:06 localhost sshd[25584]: Received signal 15 said:**
> : Server listening on :: port 22.
fng@butters:/var/log $
``` 

If 100 lines arent enough, you can take a bigger number :)
Look for the Accepted Line (the first line in the example). That means you had some sort of connection with your ubuntu-box.

If you can confirm you connected to your box, look in the /var/log/auth.log file beneath the accepted file.  I guess there will be some message why the login failed.      i'm not sure.
 192.6The var/log/auth.log file does not show any external connections whatsoever.  I attempted connecting from a Windows box on my LAN at home and this worked.  And it shoed up in the log.  But when I try connecting using the external IP, it asks for authentication (user name and password) but then reports that access was denied.

I examined my hosts files (both allow and deny) and neither of them has any entires so everything should be coming in.  Just to test this I entered ALL in the allow file.  No change.


A port scan using nmap from work reported that 22 was open.  My machine is in my routers DMZ.  And the ports were set to be forwarded in any case.  So I'm at a loss as to what the problme may be.

---

### Post by nder on 2005-01-07
[QUOTE=nder]192.6The var/log/auth.log file does not show any external connections whatsoever.  I attempted connecting from a Windows box on my LAN at home and this worked.  And it shoed up in the log.  But when I try connecting using the external IP, it asks for authentication (user name and password) but then reports that access was denied.

I examined my hosts files (both allow and deny) and neither of them has any entires so everything should be coming in.  Just to test this I entered ALL in the allow file.  No change.


A port scan using nmap from work reported that 22 was open.  My machine is in my routers DMZ.  And the ports were set to be forwarded in any case.  So I'm at a loss as to what the problme may be.[/QUOTE]
 OK, it turns out that I had an incorrect external IP address.  The IP address reported by sites such as [www.whatismyip.com](www.whatismyip.com) was incorrect.  I got my real external IP from my router's admin page.  I was able to successfuly connect back to my machine using this IP.  I will attempt this connection tomorrow from work.

---

### Post by fng on 2005-01-07
This is what i get when i enter a wrong password :

```
fng@butters:~ $ tail /var/log/auth.log | grep sshd                                                         
Jan  7 10:20:30 localhost sshd[13499]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=pc.ubuntu.org  user=fng
Jan  7 10:20:33 localhost sshd[13495]: error: PAM: Authentication failure for fng from pc.ubuntu.org
Jan  7 10:20:42 localhost sshd[13500]: Accepted keyboard-interactive/pam for fng from ::ffff:xxx.xxx.xxx.xxx port 57009 ssh2
Jan  7 10:20:42 localhost sshd[13505]: (pam_unix) session opened for user fng by (uid=0)
fng@butters:~ $

``` 

If it doensn't show up in /var/log/auth.log, you aren't connecting to your ubuntu-box from an external IP.
Maybe you should check the logs of your router.

---

