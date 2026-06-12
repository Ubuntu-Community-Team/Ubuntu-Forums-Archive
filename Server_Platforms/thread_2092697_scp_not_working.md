---
title: "scp not working"
date: 2012-12-08
forum: Server Platforms
---

### Post by schnimmy on 2012-12-08
I have connected to a Ubuntu 12.04 server via ssh from a laptop running Ubuntu 12.04. So far so good, on the server I tried to send a file back to the laptop using scp  ```
user@host$ scp file1 user@ip-address:Desktop/ 

ssh: connect to host <ip-address> port 22: Connection timed out 
lost connection
``` 

From the server I tried to see if port 22 was open on the laptop using netcat ```
user@host$ nc -zv <ip-address> 22 

nc: connect to <ip-address> port 22 (tcp) failed: Connection timed out 
```

Any help or suggestions would be appreciated, thanks

---

### Post by spynappels on 2012-12-08
Do you have SSH server running on the laptop, or just a SSH client?

---

### Post by schnimmy on 2012-12-08
I have connected to a Ubuntu 12.04 server via ssh from a laptop running Ubuntu 12.04. So far so good, on the server I tried to send a file back to the laptop using scp  ```
user@host$ scp file1 user@ip-address:Desktop/ 

ssh: connect to host <ip-address> port 22: Connection timed out 
lost connection
``` 

From the server I tried to see if port 22 was open on the laptop using netcat ```
user@host$ nc -zv <ip-address> 22 

nc: connect to <ip-address> port 22 (tcp) failed: Connection timed out 
```

Any help or suggestions would be appreciated, thanks

---

### Post by Vaphell on 2012-12-08
does *scp user@server:/dir/file1 Desktop/* executed on your laptop work?

---

### Post by schnimmy on 2012-12-08
I just tried scp file1 user@server from the laptop and it worked. 

To scp from server back to the laptop does ssh-server have to be installed on laptop?

---

### Post by schnimmy on 2012-12-08
just the client, do i need to install ssh server?

---

### Post by rnerwein on 2012-12-08
> **schnimmy said:**
> I just tried scp file1 user@server from the laptop and it worked. 

To scp from server back to the laptop does ssh-server have to be installed on laptop?
yes - you need the sshd
sudo apt-get install openssh-server

---

### Post by lisati on 2012-12-08
Threads merged. Please do not start multiple threads for the same support request, it dilutes the community's ability to help.

---

### Post by schnimmy on 2012-12-08
okay thanks, I've installed the ssh server on the laptop, still can't seem to ssh from server to laptop. Do any directives in /etc/ssh/sshd_config need altering? I've tried changing PermitRootLogin to yes and ChallengeResponseAuthentication to yes and PasswordAuthentication to yes, makes no difference. 

Suggestions please

---

### Post by schnimmy on 2012-12-08
the ssh server on the laptop is listening on port 22, the command netstat -an | grep LISTEN shows that it is

---

### Post by rnerwein on 2012-12-09
> **schnimmy said:**
> the ssh server on the laptop is listening on port 22, the command netstat -an | grep LISTEN shows that it is
please a little bit more information.
1. do you get an error message or just a timeout (try ssh -v  you@laptop)
2. do you have a .ssh in your ~/
3. can you ping the server from your laptop
4. why you edit the /etc/ssh/sshd_config it's not a good idea to allow root login from   
    remote destinations. even the root login is blocked in ubuntu if you haven't changed 
   something.

---

### Post by schnimmy on 2012-12-09
1. no error message, the connection times out.
2. yeah there is a .ssh folder in my home directory, and a known hosts file in there
3. i cant ping the laptop from the server but the other way around works, which makes sense, basically if i can ssh into i can ping it and if i cant ssh i cant ping it, if that makes sense.
4. i'm really not sure why, was just trying different things... I backed up the original and its now being used

I'm new to this so thanks for your patience and help...

---

### Post by spynappels on 2012-12-09
> **schnimmy said:**
> 1. no error message, the connection times out.
2. yeah there is a .ssh folder in my home directory, and a known hosts file in there
3. i cant ping the laptop from the server but the other way around works, which makes sense, basically if i can ssh into i can ping it and if i cant ssh i cant ping it, if that makes sense.
4. i'm really not sure why, was just trying different things... I backed up the original and its now being used

I'm new to this so thanks for your patience and help...

Have you enabled a firewall on your laptop like UFW or something which blocks all inbound connections? The fact that you cannot ping from the server to the laptop suggests this might be the case...

---

### Post by volkswagner on 2012-12-09
Can you ping other addresses from the server such as google.com or 74.125.228.32?

How did you setup the ip address for the server?  Is it static?  

Can you post contents of /etc/network/interfaces

```
cat /etc/network/interfaces
```

---

### Post by schnimmy on 2012-12-09
nope, i havent enabled any firewalls, to the best of my knowledge ubuntu doesnt come with one enabled?

could it be my home router? do i need to manually open a port on it? because the ssh service is defo running and listening on port 22 on the laptop, but i can't ping or netcat from the server to the laptop...

---

### Post by schnimmy on 2012-12-09
yes i can ping other addresses, google.com or 8.8.8.8 etc all work and yes there is a static ip address.

---

### Post by volkswagner on 2012-12-09
> **schnimmy said:**
> yes i can ping other addresses, google.com or 8.8.8.8 etc all work and yes there is a static ip address.


Please post your /etc/network/interfaces

---

### Post by schnimmy on 2012-12-09
/etc/network/interfaces file for the server is as follows
```

auto lo
iface lo inet loopback
auto eth1
iface eth1 inet static
             address x.x.x.x
             netmask 255.255.255.248
             gateway x.x.x.x
auto eth1:197
iface eth1:197 inet static
             address x.x.x.x
             netmask 255.255.255.248
auto eth1:198
iface eth1:198 inet static
             address x.x.x.x
             netmask 255.255.255.248             
             


```

---

### Post by volkswagner on 2012-12-09
Well I cant really help with all those x's.  I'm not sure why you would need to mask a private address on this forum.  Is your gateway address an internal address or do you have a public ip on the server?

Can you ssh using localhost on the laptop?

```
ssh user@localhost
```

If you can ssh localhost on the laptop, my money is on misconfigured network settings on the server.

To see if the problem was misconfigured network settings, we would need the output of ifconfig on both machines and the actual output of "cat /etc/network/interfaces" on the server.

---

### Post by schnimmy on 2012-12-09
/etc/network/interfaces on the laptop is as follows

auto lo
iface lo inet loopback

---

### Post by schnimmy on 2012-12-09
Sorry I'm not trying to be difficult but they're public ip's and i've been asked not to share them by people i'm working with. Yeah the gateway is a public ip.

ssh user@localhost works on the laptop.

If ssh has been misconfigured on the server how come I can ssh into it with out any issues?

Thanks for your help...

---

### Post by volkswagner on 2012-12-09
> **schnimmy said:**
> Sorry I'm not trying to be difficult but they're public ip's and i've been asked not to share them by people i'm working with. Yeah the gateway is a public ip.

ssh user@localhost works on the laptop.

If ssh has been misconfigured on the server how come I can ssh into it with out any issues?

Thanks for your help...

I never said ssh was misconfigured.  I did suggest your network settings were misconfigured.

We are trying to help you.  If you don't give what we ask, we can't help.  That is good/fine you are not offering your public ip, you should not mask private ip info.

You will need to explain in detail your network topology (LAN, WAN, number of interfaces, router, etc.).  Unless otherwise detailed we will assume both machines are on the same LAN and behind the same router.

From the limited information you have offered it appears perhaps your server and laptop are not on the same LAN.  Is your laptop behind a router?

You still have not provide the output of ifconfig.

---

### Post by schnimmy on 2012-12-09
Problem solved! configured port forwarding on my home router and assigned a static ip to the laptop.

My first time on the forum, thanks everyone for helping, in particular thanks volkswagner for pointing me in the right direction!

---

### Post by volkswagner on 2012-12-09
Glad you got it sorted.

You can mark the thread as solved by clicking on the "thread tools" at the top of the thread.

---

