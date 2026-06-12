---
title: "SSH Connection refused"
date: 2012-08-06
forum: Server Platforms
---

### Post by rwslippey on 2012-08-06
Hello all, I've just implamented a key authentication system which is working great however after changing the config file to disable password authentication, for obvious security reasons. It refuses all connections...

Any ideas.. Running 12.04

---

### Post by Habitual on 2012-08-06
restore from backup.

---

### Post by rwslippey on 2012-08-06
I think you may miss understand. I can access the system directly but I'm trying to figure out why when I disable password authentication it refuses all connections. So that when I do need to remove access the server via ssh I can, using the key system.

---

### Post by rgeddes on 2012-08-06
I assume you

- created a public/private key pair.
- copied the public key to ~/.ssh/authorized_keys of the other host
- tried to login to the other host with the uid that contains the authorized_keys file
- are not trying to connect as root

you can also troubleshoot the connection attempt by using the -vvv option to see why ssh is not connecting.

---

### Post by rwslippey on 2012-08-06
Just to clear a few things up here is the details of what I was trying to do. I think I may have lacked details in my first post. 


I use putty regularly and would like access from the internet to my server to move files around and other various things. 

What I've accomplished so far is:

I created a key using puttygen. saves it to ~/.ssh/authorized_keys2

tested the connection with the key and connected successfully.

The problem:

Changed in /etc/ssh/sshd_config

#PasswordAuthentication Yes to 


PasswordAuthentication No

Upon changing that setting I get connection refused from anywhere I try to connect. Even with the key. 

I'm just looking to tighten up security by disableing password login because I now have the key.

I've changed this setting back an testing again and everything works fine when I change it back to default. but when this setting is specific to NO it blocks all of my connection attempts.


Also the -vvv option didn't give any other useful information. 
Just says error Connection refused port 22

---

### Post by caaron on 2012-08-06
I have a similar problem with SSH connection refused when trying to connect to SSH on a fresh install.  When the server first boots up I can connect then I'm kicked out and it will not take any more connections.  SSH and OpenSSH-server are both installed and running. I can always connect right after a reboot for about 1-2min then my putty session give an error and I'm kicked out of the server.  I connect to the server VIA IP address so there is no DNS involved. 

I've uninstalled SSH and OpenSSH-server, I tried it with 10.04 and that works fine. I'm at a lost here.

Running netstat gives the following output: $ netstat -ln --tcp -v4 | grep 22
 tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN

---

### Post by rwslippey on 2012-08-06
Ok ... not sure if this makes sense but ti appears that the config file is case sensative...



so PasswordAuthentication No is bad and no (all lowercase is good and seems to work)


More testing to do...

thanks for the replies

Rob

---

### Post by rwslippey on 2012-08-06
> **caaron said:**
> I have a similar problem with SSH connection refused when trying to connect to SSH on a fresh install.  When the server first boots up I can connect then I'm kicked out and it will not take any more connections.  SSH and OpenSSH-server are both installed and running. I can always connect right after a reboot for about 1-2min then my putty session give an error and I'm kicked out of the server.  I connect to the server VIA IP address so there is no DNS involved. 

I've uninstalled SSH and OpenSSH-server, I tried it with 10.04 and that works fine. I'm at a lost here.

Running netstat gives the following output: $ netstat -ln --tcp -v4 | grep 22
 tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN


No expert to be honest but it sounds like that may be a network issue not a server issue. Check to see if you have an IP conflict somewhere... same IP address for 2 machines ect...

---

### Post by caaron on 2012-08-06
The server was 10.04 before using the same IP address without any issues.  So I don't think it's network related as stated if I reinstall 10.04 everything works fine.  I can ssh to the server without any issues.

---

### Post by caaron on 2012-08-06
OK did some more digging and it seems the issue was being caused by the ufw..... was this not used in 10.04?  I found a document on enabling SSH port... that seems to have resolved my issue.

---

### Post by rwslippey on 2012-08-06
> **caaron said:**
> OK did some more digging and it seems the issue was being caused by the ufw..... was this not used in 10.04?  I found a document on enabling SSH port... that seems to have resolved my issue.



UFW? like I said not an expert, I believe that eases firewall configurtion.... that'd explain not being able to connect but not the randomness you explained...  I'm honestly lost on this. I wish I could help more

---

### Post by markbl on 2012-08-06
To diagnose these kind of problems make sure you check /var/log/auth.log on your sshd server. In this case you may not have found it even seeing the connection so that implies a network/firewall issue. Also, the file is ~/.ssh/authorized_keys, not .._keys2. That "2" file has been depreciated for about 10 years (although probably still works).

---

