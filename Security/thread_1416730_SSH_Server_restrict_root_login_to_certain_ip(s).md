---
title: "SSH Server restrict root login to certain ip(s)?"
date: 2010-02-26
forum: Security
---

### Post by mokachoka on 2010-02-26
Is it possible to restrict root logons to the SSH server to just a single ip address (or maybe a range?)
 
I have other users connecting to the server daily so restricting ALL access to a single ip i cannot do.
 
I need root enabled (for my own reasons) but want to lock it down a bit more.

---

### Post by bodhi.zazen on 2010-02-26
First, IMO, you should not "need" to ssh in as root, but if you must 

1. I strongly suggest you use keys to do so, potentially with so called forced commands.

2. If that is not possible be sure to use strong passwords and either rules in iptables or a service such as denyhosts or fail2ban.

3. Edit /etc/ssh/sshd_config

> AllowUsers root@111.22.3.44obviously change 11.22.3.44 to the IP address you wish to allow.

---

### Post by cdenley on 2010-02-26
The file is "/etc/ssh/sshd_config".

To allow an entire subnet to login as root:
```

AllowUsers root@192.168.0.?

```
This would allow only root to login from an IP 192.168.0.1-192.168.0.254. When you define any "AllowUsers" patterns, only matching users are able to login. In other words, with only that single rule, you would no longer be able to login as your admin user.

---

### Post by bodhi.zazen on 2010-02-26
> **cdenley said:**
> The file is "/etc/ssh/sshd_config".

To allow an entire subnet to login as root:
```

AllowUsers root@192.168.0.?

```This would allow only root to login from an IP 192.168.0.1-192.168.0.254. When you define any "AllowUsers" patterns, only matching users are able to login. In other words, with only that single rule, you would no longer be able to login as your admin user.

Good point(s), thank you for adding that information.

---

### Post by CharlesA on 2010-02-26
Wouldn't it be safer and simpler to use sudo to access a root shell once you get in?

---

### Post by The Cog on 2010-02-26
> **CharlesA said:**
> Wouldn't it be safer and simpler to use sudo to access a root shell once you get in?

If he wants to use sftp, I don't think sudo is of any help.

---

### Post by Bachstelze on 2010-02-26
> **The Cog said:**
> If he wants to use sftp, I don't think sudo is of any help.

Why would you sftp to somewhere only root can access, though?

---

### Post by CharlesA on 2010-02-26
I use sftp and scp without having to have root access. There is no need to.

---

### Post by SecretCode on 2010-02-27
With sftp or scp and no root access, how do you update/add system files on a remote server?

---

### Post by CharlesA on 2010-02-27
> **SecretCode said:**
> With sftp or scp and no root access, how do you update/add system files on a remote server?
I can speak only for myself, but I usually just transfer files to a folder that I own, then if I need to do updates, I'll SSH into the box with my username *then* use sudo to become root if needed.

In my case, I tend to transfer stuff to/from home and an update is just an apt-get away.

---

### Post by SecretCode on 2010-02-27
I thought so - that's what I would do.

---

### Post by mokachoka on 2010-03-01
Thanks for the replies people it has been of much help. 
 
The reason i need to use root is im running an SFTP server with multiple accounts and need to use root access for easy maintenance and file automation / cron jobs.

---

### Post by mokachoka on 2010-03-01
Now i have just run into another problem. I have enabled root access to a single ip address that needs it use which works just fine. I also have 2 groups (powerusers) and (sftpusers) that do not work even though they are stated in AllowGroups. Im guessing its because AllowUsers now takes priority over AllowGroups... How can i get around this?

---

### Post by mokachoka on 2010-03-01
Hi all,
 
At the moment i have an SSH server and a FTP server running on my ubuntu server box. I have about 20 clients that use the server via either sftp or ftp who are all chrooted to there home directory. 
 
I run a number of scripts each day that require the use of the root account so i have to have this enabled via ssh but i am aware of the security risks.
 
Each day im seeing our server get attacked by brute force against the root account which worries me alot...
 
Today i started looking into it and restricted the root account so only a single ip address was able to login to it which seem to work perfectly at first. I did this using the AllowUsers root@***.***.***.*** then i realised AllowUsers would cancel out the AllowGroups, so the group ftpusers i had now doesnt let anyone login because i have not listed all my FTP users within AllowUsers (as i used a group before). I could add all the accounts manually but i want to use this as a last resort as im sure there will be many more accounts on the server as time goes on.
 
Does anyone know what i can do to secure the root account OTHER THAN disable it altogether as i need to use it.
 
The IP based restrictions i done above were perfect! Its a shame i cannot use them.

---

### Post by Neezer on 2010-03-01
> **mokachoka said:**
> Hi all,
 
At the moment i have an SSH server and a FTP server running on my ubuntu server box. I have about 20 clients that use the server via either sftp or ftp who are all chrooted to there home directory. 
 
I run a number of scripts each day that require the use of the root account so i have to have this enabled via ssh but i am aware of the security risks.
 
Each day im seeing our server get attacked by brute force against the root account which worries me alot...
 
Today i started looking into it and restricted the root account so only a single ip address was able to login to it which seem to work perfectly at first. I did this using the AllowUsers root@***.***.***.*** then i realised AllowUsers would cancel out the AllowGroups, so the group ftpusers i had now doesnt let anyone login because i have not listed all my FTP users within AllowUsers (as i used a group before). I could add all the accounts manually but i want to use this as a last resort as im sure there will be many more accounts on the server as time goes on.
 
Does anyone know what i can do to secure the root account OTHER THAN disable it altogether as i need to use it.
 
The IP based restrictions i done above were perfect! Its a shame i cannot use them.


I'm sorry I can't help you with your allow groups issue, but I have a ssh server at home, and I have done a few security things that have worked well for me. First of all, make sure you are using a key for authentication and not a password. It might be a bit of a pain to get each person who logs into your machine an RSA key, but for security, I would go through the trouble.

Also, when I first started up my server it was listening on the standard port 22. I was getting LOTS of failed login attempts. I switched to port 2222 and all was well. Again, might be a pain to switch all the clients over to a non-standard ssh port, but for me it was worth it.

Finally, google fail2ban. It allows you to set up an ip ban on any ip address that fails to log in a set number of times. you can specify how long the ban lasts, and how many failed login attempts you'll accept before the IP is banned. It spits out a log file that you can read as well..I found it quite helpful.

---

### Post by cdenley on 2010-03-01
> **mokachoka said:**
> Now i have just run into another problem. I have enabled root access to a single ip address that needs it use which works just fine. I also have 2 groups (powerusers) and (sftpusers) that do not work even though they are stated in AllowGroups. Im guessing its because AllowUsers now takes priority over AllowGroups... How can i get around this?
Well, you can forget about AllowUsers and stick to AllowGroups. The only member of the group "root" is the root user.

```

AllowGroups powerusers sftpusers root@xxx.xxx.xxx.xxx

```

---

### Post by mokachoka on 2010-03-01
> **cdenley said:**
> Well, you can forget about AllowUsers and stick to AllowGroups. The only member of the group "root" is the root user.
 
```

AllowGroups powerusers,sftpusers,root@xxx.xxx.xxx.xxx

```
 
Hi mate, i tried your suggestion but it doesnt seem to work. I am testing it using my local ip and its not allowing me to connect. Can you even do this for AllowGroups?

---

### Post by cdenley on 2010-03-01
Sorry, they're supposed to be seperated by spaces. Also, if you have an entry for the client's IP in /etc/hosts, I think you must use the hostname.

---

### Post by mokachoka on 2010-03-01
This still doesnt seem to be working? I am using spaces, have tried it with just the IP, have tried adding the IP to the hosts file and using the hostname but its still will not give me access. Any ideas?

---

### Post by bodhi.zazen on 2010-03-01
> **mokachoka said:**
> Hi all,
 
At the moment i have an SSH server and a FTP server running on my ubuntu server box. I have about 20 clients that use the server via either sftp or ftp who are all chrooted to there home directory. 
 
I run a number of scripts each day that require the use of the root account so i have to have this enabled via ssh but i am aware of the security risks.
 
Each day im seeing our server get attacked by brute force against the root account which worries me alot...
 
Today i started looking into it and restricted the root account so only a single ip address was able to login to it which seem to work perfectly at first. I did this using the AllowUsers root@***.***.***.*** then i realised AllowUsers would cancel out the AllowGroups, so the group ftpusers i had now doesnt let anyone login because i have not listed all my FTP users within AllowUsers (as i used a group before). I could add all the accounts manually but i want to use this as a last resort as im sure there will be many more accounts on the server as time goes on.
 
Does anyone know what i can do to secure the root account OTHER THAN disable it altogether as i need to use it.
 
The IP based restrictions i done above were perfect! Its a shame i cannot use them.

I merged your two threads. Please do not create multiple threads on the same question as it leads to both duplication of effort and confusion.

---

### Post by mokachoka on 2010-03-01
> **bodhi.zazen said:**
> I merged your two threads. Please do not create multiple threads on the same question as it leads to both duplication of effort and confusion.

Sorry!

Can anyone confirm to me if this is infact a possible way to configure SSHD? My attempts seem to have failed and my googling has got me no where.. :)

---

### Post by bodhi.zazen on 2010-03-01
You may configure sshd BUT

AllowGroups does not allow you to specify an ip address

So you may list your users in AllowUsers

AllowUsers root@ip_address user1 user2 user3 ...

Your other option is to use ssh keys (and lock the root account).

---

