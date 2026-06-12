---
title: "Ubuntu Server 8.04.2, can't login to ssh from internet, server in lan, frezzes."
date: 2009-02-24
forum: Server Platforms
---

### Post by Aleks` on 2009-02-24
Hi all. I set up a local server in my school today and on the main router I port forwarder port 22 to it so I can access it via the internet. From LAN I can access it on ssh but when I try to login on ssh from the internet (right now I'm at home and I can't login on it) as soon as I enter the correct password it freezes and eventually it says 

```
Read from remote host REMOTEIP: Connection timed out
```

What puzzles me is that whenever I enter a wrong password it says to me 

```
Permission denied, please try again.
```

What do you think it might be wrong ?

I installed Ubuntu server 8.04.1 today and I did an upgrade & dist-update today.

---

### Post by freerkkalsbeek on 2009-02-24
Looks like a firewall issue.
Try using tcpdump/wireshark to see if packets are returned at all.

Freerk

---

### Post by Aleks` on 2009-03-02
Packets are not returned anymore after I successefuly login on some box. The problem still presists.

Now I noticed another BIG problem. Whenever I want to ssh to some box from that school server (I'm on it right now) its the same problem. What could be wrong? The trafic also freezes after succesefull login but in the LAN it work perfect both ways.

---

### Post by Yashiro on 2009-03-03
Add the ip of the computer you ssh from to the hosts file.

Might work, there is an old bug similar to the issue you're experiencing. I don't think the name matters you just need the ip there.

---

### Post by Aleks` on 2009-03-04
I've installed putty on the server now and it works, I can ssh to any box I want. I'll try ssh'ing to the server with putty from home maybe it will work as well... But why the hell does putty work and openssh-client/server doesn't ?

I've read up on Reverse DNS problems, I have UseDNS NO in my sshd_config but still no results. 

Someone tolled me to add the routers DNS server to my resolv.conf insted of my 4.2.2.2 dns servers, still no result.

---

### Post by matey3 on 2009-03-04
I think this is because PuTTY asks for usernam and ssh defaults to root.
if you have not seup a root account/password on the receiving box that can happen but most of the times on certain systems the root is denied access via ssh?! 
so you have to do ssh -lanother_username YourIP_Address
you can leave no space between the l (L) and the username.
Also before when I had problem it was the known_hosts file, I just renamed it and I then could ssh to it.

---

### Post by Aleks` on 2009-03-04
Ofcourse I have another user on that system. I've tried ssh'ing to that server again now using putty with no luck.

---

