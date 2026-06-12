---
title: "Ubuntu 12.04 apt hangs"
date: 2012-06-11
forum: Server Platforms
---

### Post by eoindubh on 2012-06-11
This is a fresh install of Ubuntu 12.04 server. It seemed to install OK and boots fine but when I run "apt-get update" it hangs trying to connect to us.archive.ubuntu.com (91.189.91.30) [Connecting to security

I can't update, upgrade or install anything. I can ping the above IP and get @90ms response  times. 

I have re-installed with no change. I can ping and traceroute to just about anywhere but cannot install even logged in as root.

Is there a base firewall setting in 12.04 that would block this? I am not too up on managing the firewall from the command line but will look at it. I am just not sure what I am looking for.

Thanks in advance for any pointers.

---

### Post by eoindubh on 2012-06-11
I am getting a bit further on. I changed to a fixed IP and checked that DNS is functioning and that nslookup works. When I run an apt-get update now it only hangs for a couple of minutes and then streams errors on each entry the sources.list. For each entry the error says Unable to connect to security.ubuntu.com:http [IP: 91.189.91.80] and when it finishes there is the message "E: Some index files failed to download. They have been ignored, or old ones used instead."

I still cannot install anything.

---

### Post by wojox on 2012-06-11
It's not you it's their server.
```
wojox@wojox-laptop:~$ ping -c 3 91.189.91.80
PING 91.189.91.80 (91.189.91.80) 56(84) bytes of data.

--- 91.189.91.80 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2016ms
```

Give it a few hours and try again.

---

### Post by eoindubh on 2012-06-11
Where does it get the IP from? I have seen several different ones as I have been working on this. The first one 91.189.91.30 is alive and if I plug that into a browser I go directly to the repository.

I added 91.189.91.30 us.archive.ubuntu.com to my hosts file and can ping it easily. But it fails to connect on every repository.

---

### Post by kennethconn on 2012-06-11
Try a different source and see if that works better (ideally closest to your location).

---

### Post by eoindubh on 2012-06-11
I have tried several. I renamed the original sources.list and created a new one with only 2 lines:

deb [http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/) precise main
deb-src [http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/) precise main

I have tried several mirrors and have pinged their IPs to make sure that they are up but get the same errors.

---

### Post by kennethconn on 2012-06-11
Your original post did not mentioned you tried an alternative source, hence the suggestion.
 
Sample sources.list
 
```
 
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how
#to upgrade to newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted

```
 
Note the restricted component and the entry for precise-updates.
 
It seems the ufw is disabled by default but you can check with ```
sudo ufw status
```
 
Check the logfiles for any messages, after that I am out of suggestions, sorry.

---

### Post by eoindubh on 2012-06-11
As a part of trying to troubleshoot this I enabled ufw and port 80 is allow from anywhere as is port 22.

---

### Post by kennethconn on 2012-06-12
That wouldn't make a difference to your issue (but I hope you changed it back as it's a security issue if you don't require it)

---

### Post by mg9189 on 2012-06-12
I am unable to access security.ubuntu.com off and on for the past couple hours.  I have tried from Reno and St. Louis with methods that I know work.
 
I offer this as a possible reason for you not getting this to work, as when I do an apt-get update, it will hang at the same spot for a little bit, then continue with a bunch of errors.
 
I cannot ping the server, nor can I ping the IP addresses I have associated with the server.
 
Well, briefly, I was able to ping it for about 5 minutes.
 
I think Canonical is have some problems with their servers right now.
 
I hope this helps you out.

---

