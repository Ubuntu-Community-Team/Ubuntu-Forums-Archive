---
title: "ssh is running but port 22 not open"
date: 2010-07-10
forum: Server Platforms
---

### Post by ldt on 2010-07-10
I have two computers on a LAN. (This is history not a Bazaar question, although I have one of those too) One of them (Ubuntu 9.04) I’m using as a Bazaar repository over sftp. It’s been working fine for about a year. Then we had a thunderstorm that knocked out our Internet service for a  couple of days. When it came back up everything is working fine accept I could no longer “commit” to the server. A little detective work showed that ssh was not running on the server. I started it and Bazaar then couldn’t find the repository files. I still suspected an ssh problem, but port scans from both computers showed port 22 open on the server and I could do a ssh login from the client ok. Then I started fiddling with ssh on the server and now I have ssh problems on top of the Bazaar problems.
   
  On the server I deleted then regenerated the ssh keys. I’ve done 
  sudo /etc/init.d/ssh reload
  sudo /etc/init.d/ssh start
   
  I get a normal starting message and
  ps –ef |grep ssh
   
  shows /usr/sbin/sshd running. But the port scan does not show 22 open and I get “connection refused” at the client.
   
  I’ve combed through all the forums I could find on Google and tried all of the suggestions. But, alas, I don’t find a solution anywhere.
   
  Ideas?

---

### Post by nemilar on 2010-07-10
A few things that might push you in the right direction:


Is sshd listening?  On the right port?

```
[jdeprizi@pioneer ~]$ sudo lsof -i | grep ssh
[sudo] password for jdeprizi: 
sshd      1170     root    3u  IPv4  11962      0t0  TCP *:ssh (LISTEN)
sshd      1170     root    4u  IPv6  11966      0t0  TCP *:ssh (LISTEN)

```

```
[jdeprizi@pioneer ~]$ netstat -l --numeric-ports | grep 22
tcp        0      0 *:22                        *:*                         LISTEN      
tcp        0      0 *:22                        *:*                         LISTEN     
```


Is the firewall running?  Check if it is blocking port 22.

```
sudo /etc/init.d/iptables status
```

---

### Post by ldt on 2010-07-10
Thanks for the quick reply. Yes to first two questions, sshd is listening on port 22. But for
sudo /etc/init.d/iptables
I get "command not found". 

Since posting I've noticed that may be the wrong forum. I'm not running the Ubuntu Server Edition.

---

### Post by nemilar on 2010-07-10
Does "ssh localhost" work on the machine running sshd?

---

### Post by ldt on 2010-07-10
Yep, ssh localhost on the server running sshd seems to work fine. But still no open port 22 is scanned from client or server either one.

---

### Post by nemilar on 2010-07-10
You're sure there's no firewall between the machines?

I gave you a bad command before (gave you the Fedora version).  Can you try:

```
sudo iptables --list
```

---

### Post by ldt on 2010-07-10
OK, iptables --list
<code>
...:/etc/ssh$ sudo  iptables --list
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  
</code>

I'm not sure what this means but I would guess it is ok. Also, from the client scan port 80 is open and I can get web pages from the Apache http server. Don't know if that helps.

---

### Post by CharlesA on 2010-07-10
Firewall looks good.

If you are using keys, see if you can boot off a livecd on another machine and then access the other machine via ssh.

If that doesn't work, do you have denyhosts or something installed?

---

### Post by ldt on 2010-07-10
If by "using keys" you mean ssh does not require a password, no.
I have ssh server running on another machine on the LAN. From the problem machine I can see port 22 with a scan and I can do a ssh login. But from the other machine I can't see port 22 or do ssh login on the problem machine.

Not running anything like "denyhosts" that I know of. As I mentioned, all was working before the power outage.

I'm thinking of doing and apt-get purge and then reinstall ssh? Does that sound reasonable at this point?

---

### Post by ldt on 2010-07-11
Let's call the two machines G for good and P for problem. This morning the first thing I did was turn off all machines on my LAN, the hub and the router. I then rebooted everything in the reverse sequence - cable modem, router, hub, and then the computers. 

Then I reinstalled ssh on both machines G and P.

sudo apt-get purge openssh-server openssh-client
 sudo apt-get install openssh-server openssh-client
 

 sshd in now running and port 22 shows on both machines. However -  
 

 from P

 ssh G (check)
 ls (check – shows home directory of G)
 

 from G

 ssh P (check)
 ls (HERE IS THE PROBLEM – shows the home directory of G not P)
 

 The only good news here is that it answers my original Bazaar “file not found” problem. It is obviously an ssh problem. But I am baffled and out of ideas.

---

### Post by CharlesA on 2010-07-11
Check dns and/or /etc/hosts

---

### Post by wyverndany on 2012-01-14
Hi, I was looking at this problem since I'm having the same problem and can't seem to fix it. I went through the openSSH documentation to configure my server ( Ubuntu 10.04 ) but still I can't get it fixed.
I tried the code below suggested by nemilar:


```
$ sudo lsof -i | grep ssh
sshd       7294       root    3r  IPv6  746486      0t0  TCP *:ssh (LISTEN)

$ netstat -l --numeric-ports | grep 22
tcp        0      0 127.0.0.1:54322         0.0.0.0:*               LISTEN     
tcp6       0      0 :::22                   :::*                    LISTEN     
```


I noticed that my results are similar but not the same as you showed. Can this be the cause ? or does anyone have a suggestion ?

Thanks

---

### Post by CharlesA on 2012-01-14
Hi,

This thread is from 2010 and the OP hasn't responded since the last post, so you'd be better off starting a new thread.

In your case, ssh is listening on the loopback address on port 54322, for some reason. It sounds like you changed the listen address and port in /etc/ssh/sshd_config

---

### Post by KMPSJHS on 2012-08-29
> **nemilar said:**
> A few things that might push you in the right direction:


Is sshd listening?  On the right port?

```
[jdeprizi@pioneer ~]$ sudo lsof -i | grep ssh
[sudo] password for jdeprizi: 
sshd      1170     root    3u  IPv4  11962      0t0  TCP *:ssh (LISTEN)
sshd      1170     root    4u  IPv6  11966      0t0  TCP *:ssh (LISTEN)

``````
[jdeprizi@pioneer ~]$ netstat -l --numeric-ports | grep 22
tcp        0      0 *:22                        *:*                         LISTEN      
tcp        0      0 *:22                        *:*                         LISTEN     
```Is the firewall running?  Check if it is blocking port 22.

```
sudo /etc/init.d/iptables status
```


For whether ssh is listening or not,I have to use the above code ah?
But I dont find ssh file in the location /etc/init.d/ssh but i have a file ssh_config in /etc/ssh.

I have typed this code sudo lsof -i | grep ssh.I was asked for password.But nothing displayed me as you show.

While I use the code ssh localhost . the port 22 connection refused message is coming.How do I correct it.Please help me.Thank you.

---

### Post by CharlesA on 2012-08-29
If you don't have an a file in /etc/ssh/sshd_config, you do not have openssh-server installed.

---

