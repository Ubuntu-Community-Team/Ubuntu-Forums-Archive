---
title: "Troubling auth.log entry"
date: 2014-11-07
forum: Security
---

### Post by andrmou on 2014-11-07
We use fail2ban on a headless Ubuntu v14.04 server hosted by Linode. Today we just had an issue caused by the following entries in auth.log:
[COLOR=#000000][FONT=&quot] Nov  7 05:08:14 localhost sshd[30701]: Invalid user user from <my-external-ip>
Nov  7 05:08:14 localhost sshd[30701]: input_userauth_request: invalid user user [preauth]
Nov  7 05:08:14 localhost sshd[30701]: pam_unix(sshd:auth): check pass; user unknown
Nov  7 05:08:14 localhost sshd[30701]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=<my-full-host-name>
Nov  7 05:08:16 localhost sshd[30701]: Failed password for invalid user user from <my-external-ip> port 59030 ssh2
[/FONT][/COLOR]
These were repeated twice over the next 5 minutes, which then resulted in fail2ban locking the IP. The troubling thing though is the IP that the connections are originating from (and being then banned) _is the server's own external IP_ address!  So as a result of this incident fail2ban ended up locking out connections to itself that used its external address (rather than the loopback address). This did not make our server inaccessible, but it did stop some applications working until we unjailed our IP.

Reviewing our logs, this is the only time in the last month this situation has occurred. I don't know how concerned to be, or what countermeasures to take. My observations / issues are:


[LIST=1]
[*]This incident must have either originated from within our own server, or another machine on our server's subnet that could spoof its address to look like our server. I don't know how feasible the latter is.
[*]I don't really want to whitelist the server's IP in fail2ban, since if there is a problem that would make things easier for any attacker. What counter measures can I take to detect / diagnose / prevent a recurrence?
[*]If this was a genuine attack from within our machine, then it has strange characteristics:
[LIST]
[*]It went for the non-existent user 'user' rather than trying to get root access
[*]It didn't attempt (or retry) using localhost, which would have been a better option if this was originating from our server
[*]It didn't try sudo to get elevated permissions
[*]It seems very isolated - only 3 attempts in the last month, and no recurrence since we unjailed the IP
[*]The server has all patches applied
[/LIST]
[/LIST]

So I'm a little confused, and open to suggestions and theories!

Thanks

- Andrew

---

### Post by Doug S on 2014-11-08
Hi, and welcome to Ubuntu forums.

Your post is very interesting.

> **andrmou said:**
> This incident must have either originated from within our own server,Agreed, and I was able to create the exact same auth.log entries on my system by trying to ssh into itself via the external IP address.> **andrmou said:**
> or another machine on our server's subnet that could spoof its address to look like our server. I don't know how feasible the latter is.I do not think so. SSH uses tcp and needs to be able to communicate both ways, and therefore packets need to be routable back to the source. If the source address was forged then there would not be a return path. However, I would be interested in other peoples opinion on this one.> **andrmou said:**
> What counter measures can I take to detect / [COLOR=#ff0000]diagnose[/COLOR] / prevent a recurrence?I would run tcpdump (or wireshark, if you prefer) on your external interface watching port 22. In the event of recurrence, no captured packets means internal (I tested this), and captured packets means somehow external.```
sudo tcpdump -n -tttt -i eth1 port 22
```I don't know how feasible this is for you. I always have tcpdump running on both my internal and external interfaces and can go back after an event for more in depth diagnosis, if required.

---

### Post by bashiergui on 2014-11-08
+1 to watching packets to port 22.

Other questions that might be worth investigating:
If you've got a router/switch or firewall in front of the ssh server look at those logs.
What else was going on on the server during that timeframe- look at all the other logs
What kind of cron jobs do you have set up? Is this a fubar backup operation?

Random thought- any chance one of your admins tried to ssh from your server to some other server but just typed the wrong IP? What other outgoing traffic did your server have destined to foreign IPs on port 22?

---

### Post by andrmou on 2014-11-10
Thanks for the replies.

Yeah I don't think spoofing should be possible either - but I'm aware there are brighter people than me out there! I'll touch base with our virtual hosting provider and see if they have any thoughts on this being possible on the external i/f. tcpdump is a good idea, as long as the overhead isn't significant.

I did look at cron jobs - the only ones configured seem standard and innocuous. They also weren't running at exactly the time we had this issue. I didn't see any other activity in syslog or auth.log at the time - are there any other logs I should be looking at?

We did have an admin logged in over ssh when this happened, but I think he was dormant wrt the shell. He was doing some experimentation wrt re-configuration of our web-based application at the time via a web UI; our own internal developers can't see that being a cause of the suspect messages.

It's all very strange!

---

### Post by Doug S on 2014-11-10
> **andrmou said:**
> I'll touch base with our virtual hosting provider and see if they have any thoughts on this being possible on the external i/f.Yes, definitely do that. > **andrmou said:**
> tcpdump is a good idea, as long as the overhead isn't significant.Overhead shouldn't be too bad, but then I don't know your system. Since you don't know when, or even if, there will be a recurrence of the issue, I would suggest to run tcpdump such that it writes the data to a file, and changes files every so often. Then you can both remove stale files and only have to look at a smaller chunk of data to follow up on an event. Example with 10 minutes per file:```
sudo tcpdump -i eth1 port 22 -w 'eth1-port22-%F-%H-%M-%S.bin' -G 600
```> **andrmou said:**
> It's all very strange!Yes it is, but also very interesting. Please report back any new information.

---

### Post by andrmou on 2014-11-10
> **Doug S said:**
> Please report back any new information.
Will do - thanks for the suggestions.

I've also just installed auditd on this server so we can track at how things are being executed inside the machine.

This all presumes the issue will recur. Hopefully it will, now we have better tracking in place.

- Andrew

---

### Post by bashiergui on 2014-11-10
Look at the bash history of each user. If you don't see someone sshing to your own IP, you might be able to see what they've been up to that could have caused it.


Also if you haven't already you might want to enable timestamps in bash. Makes cases like this easier to investigate.
[http://askubuntu.com/questions/391082/how-to-see-time-stamps-in-bash-history](http://askubuntu.com/questions/391082/how-to-see-time-stamps-in-bash-history)

Also you asked what logs to look at. If your apps write to any logs then look at those.

---

### Post by Habitual on 2014-11-11
> **andrmou said:**
> 
[LIST=1]
[*]I don't really want to whitelist the server's IP in fail2ban, since if there is a problem that would make things easier for any attacker. What counter measures can I take to detect / diagnose / prevent a recurrence? 
[*]If this was a genuine attack from within our machine, then it has strange characteristics:
[LIST]
[*]It went for the non-existent user 'user' rather than trying to get root access 
[*]It didn't attempt (or retry) using localhost, which would have been a better option if this was originating from our server 
[*]It didn't try sudo to get elevated permissions 
[*]It seems very isolated - only 3 attempts in the last month, and no recurrence since we unjailed the IP 
[*]The server has all patches applied 
[/LIST]
    
[/LIST]

So I'm a little confused, and open to suggestions and theories!

Thanks

- Andrew

If you are hosting "sites" on this server that are not entirely "yours", you may wish to run LMD and scan for "bad things"...
 ```

sudo su -
cd /usr/src
wget [http://www.rfxn.com/downloads/maldetect-current.tar.gz](http://www.rfxn.com/downloads/maldetect-current.tar.gz)

   untar it
cd into it
install.sh


```
example scan using LMD:
 ```
sudo maldet -b -r /path/to/scan/ && tail -f /usr/local/maldetect/event_log
```


and excluding the server's external IP is not a good idea.

---

### Post by andrmou on 2014-11-11
> **bashiergui said:**
> Look at the bash history of each user. If you don't see someone sshing to your own IP, you might be able to see what they've been up to that could have caused it.


Also if you haven't already you might want to enable timestamps in bash. Makes cases like this easier to investigate.
[http://askubuntu.com/questions/391082/how-to-see-time-stamps-in-bash-history](http://askubuntu.com/questions/391082/how-to-see-time-stamps-in-bash-history)

Also you asked what logs to look at. If your apps write to any logs then look at those.

Yeah I'd already looked at our logs and the .bash_history, but found nothing. Thanks for the suggestion of enabling timestamps in history... I've now done that

- ANdrew

---

### Post by andrmou on 2014-11-11
> **Habitual said:**
> If you are hosting "sites" on this server that are not entirely "yours", you may wish to run LMD and scan for "bad things"...
 ```

sudo su -
cd /usr/src
wget [http://www.rfxn.com/downloads/maldetect-current.tar.gz](http://www.rfxn.com/downloads/maldetect-current.tar.gz)

   untar it
cd into it
install.sh


```
example scan using LMD:
 ```
sudo maldet -b -r /path/to/scan/ && tail -f /usr/local/maldetect/event_log
```


I've done as you suggested and am part way through scanning my system. The bad news is the only hit it has found is in the Linux Malware Detect distribution itself: 
```
{MD5}gzbase64.inject.unclassed.533 : /usr/src/maldetect-1.4.2/files/clean/gzbase64.inject.unclassed
```
This potentially means I may now be worse off! So I've suspended doing additional scans until I work out if maldetect is finding a false-positive against itself or whether its done harm in its own right.

- Andrew

---

### Post by HermanAB on 2014-11-12
BTW, this is why I don't recommend fail2ban.

It is better to use a general purpose rate limiting rule in iptables, that will stop ALL brute force attacks without side effects like locking yourself out of your computer.

---

### Post by Doug S on 2014-11-12
> **HermanAB said:**
> It is better to use a general purpose rate limiting rule in iptables, that will stop ALL brute force attacks without side effects like locking yourself out of your computer.I disagree. Once the general purpose rate limiting rules engage they are non-discriminating. Under a sustained attack, the attacker gets any available access windows when the rule dis-engages and the rule re-engages. The result is the good guy typically gets blocked (well, at least that has been my experience with them).

By the way I don't use fail2ban either, because and in my opinion, and as explained on that [other thread]("http://ubuntuforums.org/showthread.php?t=2251760") the other day, there is a much easier and simpler way.

---

### Post by andrmou on 2014-11-12
> **andrmou said:**
> 
     This potentially means I may now be worse off! So I've suspended     doing additional scans until I work out if maldetect is finding a     false-positive against itself or whether its done harm in its own     right.
     
     I couldn't find any other references online to the above file being     a false positive, though it seems likely that's what it is. The file  is copied during LMD installation, and so would be excluded from LMD  scans in its installed location within the LMD directory; if I'd deleted  the temporary .gz extraction directory before running my scan of /usr I'd never  have been tripped up by it! Additionally the file contents are  innocuous in isolation, so if I trust LMD then I should trust this file.

So  getting back to the original issue, the LMD scans were negative across  all directories. I then also installed and ran both chkrootkit and  rkhunter. chkrootkit reported suckit rootkit in one file, but this seems to be an ongoing false positive with chkrootkit. rkhunter didn't find suckit, though it had problems with a few other files, which again analysis suggests are false positives. I've also checked all system logs and  looked through tmp files and checked file attributes for immutable  files. Everything looks OK. 

If it wasn't for fail2ban catching  those auth.log entries, I'd be feeling pretty good about the system. As  it is, I can't say with 100% certainty it's OK. But even if the log  entries do represent an intrusion, then my observations and research  would suggest it was not at elevated permissions. So I feel reasonably comfortable just monitoring the situation and looking for recurrences.

---

