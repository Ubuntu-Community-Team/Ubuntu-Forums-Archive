---
title: "I'm being hacked :S"
date: 2012-03-12
forum: Security
---

### Post by jmr423 on 2012-03-12
Ubuntu server 10.04, lamp and shorewall installed.

Hey so i have been leaving my tail -f /var/log/auth.log running in the background and this popped up

```
ar 12 00:44:18 server001 sshd[2168]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=59.60.7.111 
Mar 12 00:44:21 server001 sshd[2168]: Failed password for invalid user cgi-bin from 59.60.7.111 port 52976 ssh2
Mar 12 00:44:21 server001 sshd[2170]: Connection from 59.60.7.111 port 54466
Mar 12 00:44:23 server001 sshd[2170]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=59.60.7.111  user=root
Mar 12 00:44:25 server001 sshd[2170]: Failed password for root from 59.60.7.111 port 54466 ssh2
Mar 12 00:44:25 server001 sshd[2172]: Connection from 59.60.7.111 port 55762
Mar 12 00:44:27 server001 sshd[2172]: Invalid user sbin from 59.60.7.111
Mar 12 00:44:27 server001 sshd[2172]: pam_unix(sshd:auth): check pass; user unknown
Mar 12 00:44:27 server001 sshd[2172]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=59.60.7.111 
Mar 12 00:44:29 server001 sshd[2172]: Failed password for invalid user sbin from 59.60.7.111 port 55762 ssh2
```

It looks like the guy at this ip address tried to brute force my ssh, there are many other reports in it. Can i report this somewhere? Are there any tests i can run on my server to see what i can change to make it more secure? This is the 3rd time today someone has tried to brute force my ssh today and I'm starting to get really worried. 

 Also i was trying to set up the auth key instead of using a password but it does not work, it keeps asking me to enter a password every time i log in. When i disable the password in the ssh config file i am unable to access it.

Im running ubuntu server 10.4 with lamp, and shore wall.

---

### Post by gruntb23 on 2012-03-12
wish I could help you but im suscribing to this so I can learn too.

---

### Post by spynappels on 2012-03-12
I would not be too worried about the logs having lots of entries like this, it is a natural consequence of having port 22 open to the net. This is almost certainly some automated bot trying to bruteforce your password, as long as your password is secure, you are probably ok.

However, I would suggest you try to trouble shoot what is happening with the key based authentication, that is the surest way to protect yourself from these bruteforce attempts. Until that is sorted though, you can use denyhosts ```
sudo apt-get install denyhosts
``` to block the IP after a few failed attempts, this will at least clean up your logs a little.

If you post some detail on the problems you are having with key-based authentication, perhaps we can help with that.

---

### Post by Hungry Man on 2012-03-12
As stated above it's likely a bot. It's kinda just the way it works if you have a server.

---

### Post by cabaro on 2012-03-12
Another package you can use to block ip-address of attacker: fail2ban

[https://help.ubuntu.com/community/Fail2ban]("https://help.ubuntu.com/community/Fail2ban")

---

### Post by jmr423 on 2012-03-12
> **Hungry Man said:**
> As stated above it's likely a bot. It's kinda just the way it works if you have a server.

That is irritating. 



> **spynappels said:**
> I would not be too worried about the logs having lots of entries like this, it is a natural consequence of having port 22 open to the net. This is almost certainly some automated bot trying to bruteforce your password, as long as your password is secure, you are probably ok.

However, I would suggest you try to trouble shoot what is happening with the key based authentication, that is the surest way to protect yourself from these bruteforce attempts. Until that is sorted though, you can use denyhosts ```
sudo apt-get install denyhosts
``` to block the IP after a few failed attempts, this will at least clean up your logs a little.

If you post some detail on the problems you are having with key-based authentication, perhaps we can help with that.

So about my ssh key login, to start off, i am connecting from a mac , lion laptop to my ubuntu 10.04 web server. The mac laptop being the client and the ubuntu server being the host. I am running shore wall on my ubuntu server.

The main issue i am having with the keys is that when i try to log into the host from my laptop after entering this command ```
ssh-copy-id <username>@<host>
```'it still asks for my password. I have tried going into the ssh config file and changed the setting to not allow password login's. After i edit the config file, i am not longer able to access the server via ssh at all.

On my 3rd attempt, I disabled shore wall and tried to delete the keys from previous attempts on my mac laptop and server but i am not sure if i did it correctly. to delete the old files i removed the directory /.ssh that contained the key's with the rm -d command. I disabled shore wall with sudo Shore wall stop.

This is the guide i used for the process. 

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)



> **cabaro said:**
> Another package you can use to block ip-address of attacker: fail2ban

[https://help.ubuntu.com/community/Fail2ban]("https://help.ubuntu.com/community/Fail2ban")

Thank you for the info, il check it out tomorrow.

---

### Post by prshah on 2012-03-12
> **jmr423 said:**
> 
Mar 12 00:44:21 server001 sshd[2168]: Failed password for invalid user cgi-bin from 59.60.7.111 port 52976 ssh2

You can look up the location of the ip address using a free service such as ip2location.com

For example, the result of the lookup for the address above reveals it to be a hotel in China (XIAMEN HAIJINGHOTEL FUJIAN PROVINCE); maybe you could think about complaining to them, with your logs attached, though I can't see how it will help in any fashion.

I know this is not helpful to your problem directly, just thought I'd share.

---

### Post by Lars Noodén on 2012-03-12
As mentioned those are just scripts trying to crack your system by guessing passwords and usernames.  You can use [iptables](http://manpages.ubuntu.com/manpages/oneiric/en/man8/iptables.8.html) as one method of restricting their attempts:

```

  ip6tables -I INPUT -p TCP --dport 22 -m state --state NEW -m limit --limit 5/minute --limit-burst 6 -j ACCEPT
  iptables  -I INPUT -p TCP --dport 22 -m state --state NEW -m limit --limit 5/minute --limit-burst 6 -j ACCEPT

```

---

### Post by kevdog on 2012-03-12
Although its a security through obscurity mechanism, Id move my listening ssh port of port 22.

---

### Post by Cheesemill on 2012-03-12
> **jmr423 said:**
> This is the 3rd time today someone has tried to brute force my ssh today and I'm starting to get really worried. 

You're lucky.

If I don't move SSH to a different port and set up rate limiting I get thousands of brute force attempts per day :)

---

### Post by Ms. Daisy on 2012-03-12
> **kevdog said:**
> Although its a security through obscurity mechanism, Id move my listening ssh port of port 22.
Do I smell sarcasm or typos?
LOL

---

### Post by jmr423 on 2012-03-12
SSH key authentication works =D i ended up having to copy and past the key onto my server. 


Does anyone know how to get shore wall to allow ssh connection through port 2222 from the web? I do not want to allow any connects to port 22. I know how to change this in my ssh config file however i can't seem to get shore wall to allow the connection. I have tried a few different things but nothing seems to work :S

---

### Post by kevdog on 2012-03-12
Moving to port 2222 is very easy.

sshd_config

Change the Port line to
Port 2222

Restart the server:
sudo service sshd restart

As far as shorewall -- I'm not sure.  You could accomplish this via using ufw or iptables.  I've never used shorewall but it has to be doable.

---

### Post by bernied on 2012-03-12
my /etc/shorewall/rules file has this:
```
ACCEPT          net             fw              tcp     ssh

```but you can change it to this:
```
ACCEPT          net             fw              tcp     21212

```or choose any high port number

I also get hundreds of brute force attempts every day. Let them knock on the door I say.

---

### Post by jmr423 on 2012-03-13
> **bernied said:**
> my /etc/shorewall/rules file has this:
```
ACCEPT          net             fw              tcp     ssh

```but you can change it to this:
```
ACCEPT          net             fw              tcp     21212

```or choose any high port number

I also get hundreds of brute force attempts every day. Let them knock on the door I say.

> **kevdog said:**
> Moving to port 2222 is very easy.

sshd_config

Change the Port line to
Port 2222

Restart the server:
sudo service sshd restart

As far as shorewall -- I'm not sure.  You could accomplish this via using ufw or iptables.  I've never used shorewall but it has to be doable.




So i added the shore wall rule and changed the port in ssh and it will not let me connect...

---

### Post by kevdog on 2012-03-13
A couple of things

The post that recommended: 
ACCEPT          net             fw              tcp     21212

is incorrect since the port number is wrong.

Can you post:
sudo iptables -L

---

### Post by jmr423 on 2012-03-13
The issue has been resolved. My router was not correctly forwarding my ports.

and of course i changed the ports so they match...

> **kevdog said:**
> A couple of things

The post that recommended: 
ACCEPT          net             fw              tcp     21212

is incorrect since the port number is wrong.

Can you post:
sudo iptables -L

---

### Post by youngunix on 2012-03-14
I think any ubuntu user should bookmark and keep an eye on this link [http://www.ubuntu.com/usn](http://www.ubuntu.com/usn). Just in case you need to know what's vulnerable on your ubuntu box.

---

