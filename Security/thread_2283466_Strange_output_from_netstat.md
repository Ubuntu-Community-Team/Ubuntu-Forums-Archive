---
title: "Strange output from netstat"
date: 2015-06-22
forum: Security
---

### Post by Wtower on 2015-06-22
One one of my ubuntu servers, running netstat shows the following output:

```

wtower@xxx~$ sudo netstat -natp | grep sshd
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      6680/sshd       
tcp        0      0 xx.xxx.xx.xxx:22        43.229.52.15:49460      ESTABLISHED 3382/sshd: root [pr
tcp        0     48 xx.xxx.xx.xxx:22        x.xx.xx.xx:44319        ESTABLISHED 7441/sshd: wtower [
tcp6       0      0 :::22                   :::*                    LISTEN      6680/sshd       
wtower@xxx:~$ sudo netstat -natp | grep sshd
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      6680/sshd       
tcp        0    848 xx.xxx.xx.xxx:22        43.229.52.15:39686      ESTABLISHED 3390/sshd: [accepte
tcp        0      0 xx.xxx.xx.xxx:22        x.xx.xx.xx:44319        ESTABLISHED 7441/sshd: wtower [
tcp6       0      0 :::22                   :::*                    LISTEN      6680/sshd       
wtower@xxx:~$ sudo netstat -natp | grep sshd
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      6680/sshd       
tcp        0      0 xx.xxx.xx.xxx:22        43.229.52.15:39686      ESTABLISHED 3390/sshd: root [pr
tcp        0      0 xx.xxx.xx.xxx:22        x.xx.xx.xx:44319        ESTABLISHED 7441/sshd: wtower [
tcp6       0      0 :::22                   :::*                    LISTEN      6680/sshd       

```

You can notice that a ssh connection as root from 43.229.52.15 (Japan) is constantly changing pids, as root. Also, w shows nothing.

Running ps shows this:

```

root      1134  0.0  0.0  12712   760 tty1     Ss+  May06   0:00 /sbin/getty 38400 console
root      1136  0.0  0.0  12712   764 tty2     Ss+  May06   0:00 /sbin/getty 38400 tty2

```

Running nmap -Pn shows no such open port, besides I am running a hardware firewall on the server.

Rkhunter and chkrootkit are clean.

Questions:


[LIST=1]
[*]Any idea what this is? Possibly some rootkit?
[*]How can this be removed?
[*]Any other considerations?
[/LIST]

Thank you very much!

---

### Post by zero212 on 2015-06-23
Strange indeed. Try running hethogs for a while and monitor what processes are accessing the internet.

```

sudo apt-get install nethogs
sudo nethogs

```

---

### Post by bashiergui on 2015-06-23
Someone has logged in to your ssh server as root from that IP. I show it to be in Hong Kong. The IP is also on several spam and blocklists. This site tracks malicious IPs, and you can see that the IP 43.229.52.15 has been busy brute forcing everyone's ssh server

[https://www.blocklist.de/en/view.html?ip=43.229.52.15](https://www.blocklist.de/en/view.html?ip=43.229.52.15)

You probably have password authentication enabled for your ssh server. Disable that and allow only key authentication. Also, it looks like you were allowing root logins, that's a bad idea.

The attacker has root actively, right now, on your server. Personally I would format and reinstall, but that assumes you've got backups. I also wouldn't trust much on the server right now, as the attacker could install, create, and modify anything he wants as root.
 
I'm guessing this server is remote from you- the other ssh connection is you?

---

### Post by Wtower on 2015-06-25
> **zero212 said:**
> Strange indeed. Try running hethogs for a while and monitor what processes are accessing the internet.



Thank you @zero212. I have used nethogs, it reports nothing extraordinary. Seemingly valid traffic + a very small footprint from the irregular ssh process as one would expect. I was wondering how I could isolate the specific process in a single command as it seems that it gets respawned. Also I am wondering, if I could purge all ssh programs and libraries and re-install them, all from ssh somehow.. And if this would work. Also, I was wondering if I should report something to the Ubuntu securiy team or if this is result from some well-known exploit which I miss.


> **bashiergui said:**
> Someone has logged in to your ssh server as root from that IP. I show it to be in Hong Kong. The IP is also on several spam and blocklists. This site tracks malicious IPs, and you can see that the IP 43.229.52.15 has been busy brute forcing everyone's ssh server

[https://www.blocklist.de/en/view.html?ip=43.229.52.15](https://www.blocklist.de/en/view.html?ip=43.229.52.15)

You probably have password authentication enabled for your ssh server. Disable that and allow only key authentication. Also, it looks like you were allowing root logins, that's a bad idea.

The attacker has root actively, right now, on your server. Personally I would format and reinstall, but that assumes you've got backups. I also wouldn't trust much on the server right now, as the attacker could install, create, and modify anything he wants as root.
 
I'm guessing this server is remote from you- the other ssh connection is you?

Thank you @bashiergui for your kind response too. Indeed I have found this information about this IP too. Yesterday there was no such activity, but today there is similar activity from another IP from the US, blacklisted too.

Password authentication was indeed on for other customer reasons. Which I disabled it immediately now and restarted sshd. It seems that now netstat output is proper, for which i am very glad. Lessons learned from this is to force customers learn to use keys.

But what strikes me is this: root login is and was disabled:

```
$ cat /etc/ssh/sshd_config | grep Root
PermitRootLogin no

```

Also, root account is properly locked, double checked: 

```
$ sudo passwd -S root
root L 11/28/2013 0 99999 7 -1

```

The server is indeed accessible from ssh only. I of course I understand that format is the way to go, as it usually is with such kind of issues, but until I manage to get everybody involved ready to go under this, I am trying to establish what exactly goes on and the magnitude of the problem, so I thank you all for helping me into this.

---

### Post by Wtower on 2015-06-25
How stupid of me. The only thing that was going on is somebody trying to brute-force his way through ssh as root. This is what the netstat entry was about. This explains why the process kept respawning and was indicating root although root login was off and the account locked. Of course they would not succeed to get in. It also explains why I had an established connection with no valid entry in auth.log. Now I realise that auth.log has entries with the above IP, and still has, but I didn't bother to ckeck as I have thousands of them every day even with password authentication off.

I wonder, is there a way to see all the full line's width from netstat properly? Is is obvious that the description as is in the above output is somehow misleading.

---

### Post by chris137 on 2015-06-25
I also had my auth.log full of those lines a year ago.
Simple solution: Change your ssh-port. This reduced login-attempts on my server to practically zero. I don't even check anymore.
I didn't check my netstat back then but it probably looked similar.
Most brute-force logins are made on port 22.
Just change it and you have no flooded logs, etc anymore.

---

### Post by Wtower on 2015-06-26
Thanks @chris137. Indeed, changing the port sounds a good idea.

I am still buffled on how on earth to make netstat not truncate its output. This doesn't happen with other commands as eg. ps.

---

### Post by bashiergui on 2015-06-26
Netstat has been deprecated in favor of "ss"
[http://manpages.ubuntu.com/manpages/trusty/man8/ss.8.html](http://manpages.ubuntu.com/manpages/trusty/man8/ss.8.html)

However you can us a variety of switches for both ss and netstat to get at what you want.

---

### Post by bashiergui on 2015-06-29
I had a think on this. Netstat and ss are the wrong tools for this. Use auth logs instead.

Netstat and ss report on layer 3 activity. Meaning every time someone tries to brute force the ssh port, netstat and ss will tell you that a TCP handshake occurs. The TCP handshake occurs every auth attempt, both successful and failed. A failed authentication looks the same as a successful authentication on layer 3, except that the failed one ends and the successful one doesn't. You have to look at layer 7 to see who failed and who succeeded. That will be in the auth logs.

Netstat will always be misleading in this regard because it can't see what's happening on layer 7.

---

### Post by Wtower on 2015-06-29
> **bashiergui said:**
> Netstat has been deprecated in favor of "ss"
[http://manpages.ubuntu.com/manpages/trusty/man8/ss.8.html](http://manpages.ubuntu.com/manpages/trusty/man8/ss.8.html)

However you can us a variety of switches for both ss and netstat to get at what you want.

I cannot find how to improve output with netstat, but your recommendation about ss was very good, I was a bit traditionl with my choice of tool.

> **bashiergui said:**
> I had a think on this. Netstat and ss are the wrong tools for this. Use auth logs instead.

Netstat and ss report on layer 3 activity. Meaning every time someone tries to brute force the ssh port, netstat and ss will tell you that a TCP handshake occurs. The TCP handshake occurs every auth attempt, both successful and failed. A failed authentication looks the same as a successful authentication on layer 3, except that the failed one ends and the successful one doesn't. You have to look at layer 7 to see who failed and who succeeded. That will be in the auth logs.

Netstat will always be misleading in this regard because it can't see what's happening on layer 7.

Yes, you are right on this one, this is what mislead me. Of course auth.log may be tampered with, but I hope the 8-hour time frame I have to send a copy of it may be something.

Thanks again @bashiergui for your replies.

---

### Post by limbenjamin on 2015-07-04
> **Wtower said:**
> Thanks @chris137. Indeed, changing the port sounds a good idea.

I am still buffled on how on earth to make netstat not truncate its output. This doesn't happen with other commands as eg. ps.

Apart from changing the port, you might want to look into using fail2ban or a GeoIP filter, assuming that your users are all logging in from the same country.

Changing the port might result in errors with some badly designed applications that expect SSH to run on port 22. Some applications do not give you the option of specifying a different port as a parameter. The other issue that might arise is with firewalls. Some firewalls have already been setup to permit traffic on common ports like 22,80 and 443. Using a non standard port might result in some users not being able to access the server.

---

### Post by ddesanti on 2015-07-05
Hi:
you can use iftop to check real time active connections and bandwidth consumption. Choose the port option to see on which port there is a connection. If you see the same IP address trying to connecto to port 22 or whichever you change it, it's likely that someone is trying brute-force to login into your server. 
You should also check your /etc/ssh/sshd_config file that 
               #PermitRootLogin without-password is comment out
                 PermitRootLogin is set to no
for added security you can add only the users that should be able to login using ssh
                 AllowUsers <UserID>
You can also install UFW with FAIL2BAN to block IP addresses.

---

### Post by Wtower on 2015-07-06
> **limbenjamin said:**
> Apart from changing the port, you might want to look into using fail2ban or a GeoIP filter, assuming that your users are all logging in from the same country.

Changing the port might result in errors with some badly designed applications that expect SSH to run on port 22. Some applications do not give you the option of specifying a different port as a parameter. The other issue that might arise is with firewalls. Some firewalls have already been setup to permit traffic on common ports like 22,80 and 443. Using a non standard port might result in some users not being able to access the server.

Hi limbenjamin, thanks for the suggestions. Both fail2ban and geoip look promising. Your comment about badly designed applications was the reason to leave default in first place. I remember I have taken this decision long way back because I had faced such an issue but I can;t recall the details.

> **ddesanti said:**
> Hi:
you can use iftop to check real time active connections and bandwidth consumption. Choose the port option to see on which port there is a connection. If you see the same IP address trying to connecto to port 22 or whichever you change it, it's likely that someone is trying brute-force to login into your server. 
You should also check your /etc/ssh/sshd_config file that 
               #PermitRootLogin without-password is comment out
                 PermitRootLogin is set to no
for added security you can add only the users that should be able to login using ssh
                 AllowUsers <UserID>
You can also install UFW with FAIL2BAN to block IP addresses.

Hi ddesanti and thanks too. I do use iftop and there was nothing significant out of it. As I mentioned earlier I have concluded that this has been a brute force attack and the sshd settings that you mention were correct.

---

