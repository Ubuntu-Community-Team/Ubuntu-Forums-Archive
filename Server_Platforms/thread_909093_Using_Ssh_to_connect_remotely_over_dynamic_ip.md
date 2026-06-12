---
title: "Using Ssh to connect remotely over dynamic ip"
date: 2008-09-03
forum: Server Platforms
---

### Post by marcon00 on 2008-09-03
I guess this is the place for this thread :)

I've installed Linux (ubuntu) over couple computers at home , the thing is my family isn't that much friendly with it yet.
Since im using Wireless/Lan over my home network, use of openssh was a prefect solution for quick maintenance without disturbing their work.

Now im goin back to my university and i will be gone for good 4 months,
my question is, how can i remotely connect to my network *that is connected to internet through pppoe connection* using ssh :) or is there any other alternative ?
thanks in advance.

---

### Post by windependence on 2008-09-03
Get yourself a free domian account with no-ip.com. Then you can ssh via your domain, and a tiny app on your server keeps your ip updated to no-ip. Works great.

-Tim

---

### Post by marcon00 on 2008-09-03
yeah i did that .. but i got it from [www.dlinkddns.com](www.dlinkddns.com) ... i set it up n all.. now my router automatically sends it .. but now, assuming im out.. how can i connect to my home ?  i tried doin this :

$ssh myhost.dlinkddns.com .. it says connection refused .. :) suggestions ? :P

---

### Post by annatar on 2008-09-03
hmm...
There are 2 things that you may check...

1. Is your router really setup to rely the connection to the correct computer behind it? Check the router's firewall / port forwarding settings...etc

2. *Maybe* Ubuntu's ufw firewall is blocking the connection.
Try executing this command?

```
sudo ufw allow ssh
``` to open port 22 for ssh connections

---

### Post by Vivaldi Gloria on 2008-09-03
I've never used dlinkddns.com but let's cover the basics first. Can you ssh your home computer directly (i.e. without using dlinkddns.com) from outside of your home lan?

---

### Post by marcon00 on 2008-09-03
annatar: i can make local ssh .. 

Vivaldi Gloria: 

its the same as dyndns.com , i can't connect directly from outside of my lan,my ISP does not allow me *i assuming* . I can easily connect localy using ssh.Router is set up properly to update wit dyndns.com.

:)

---

### Post by windependence on 2008-09-03
OK from INSIDE your network, go to [www.canyouseeme.org](www.canyouseeme.org) and test port 22 to see if it's open. It will also tell you what your external IP address is. Then, like Vivaldi suggested, try to access your server from OUTSIDE your LAN using the external IP address: ssh [email]user@xxx.xxx.xxx.xxx[/email] and see if you can do it that way. If so, there is a problem with your dynamic host configuration. If not, you have other problems on the server.

-Tim

---

### Post by marcon00 on 2008-09-03
Success: I can see your service on xx.xx.xx.xx on port (22)
Your ISP is not blocking port 22

well i was wrong :p no one is blocking it :)

alright, i just need to find an outside connection .. that will take a while :S

but is it okay if i got a router ?? i mean doing [email]user@xxx.xxx.xxx.xxx[/email] doesnt specify which local computer i want to connect to .. i got 3 local computers

---

### Post by windependence on 2008-09-03
Well, aparently you have the port forwarded to SOMETHING that is listening on that port, so I would say you have it set up properly. When you ssh to the box, do an ifconfig to see what box you landed on from the outside. If it's the wrong one, you'll have to change the port forwarding on your router to the correct box.

-Tim

---

### Post by marcon00 on 2008-09-03
well.. i didnt forward any ports, maybe that is why im getting connection refused ?

then again, i shouldnt be trying to * ssh myhost.dlinkddns.com * from within the local network to see if it works, but im still getting connection refused :\

i know its simple idea behind porting and all, but somehow i never realy needed that .. i can help you with meds :D

---

### Post by marcon00 on 2008-09-03
im on something ...
i ported to specific Ip in my router .. im not getting anymore Connection Refused.. but it just freeeses there and doesnt do anything further.. just stays there like if wants something but doesnt ask for it !

EDIT / UPDATE :

# ssh -vv -p yy [email]user@host.dlinkddns.com[/email] 
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to host.dlinkddns.com [xxx.xxx.xxx.xxx] port yy.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file /username/.ssh/identity type -1
debug1: identity file /username/.ssh/id_rsa type -1
debug1: identity file /username/.ssh/id_dsa type -1
ssh_exchange_identification: Connection closed by remote host


n what is that ?

i played around a bit more n i got this :
additionally 

# ssh -vv -p yy [email]user@host.dlinkddns.com[/email] 
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to host.dlinkddns.com [xxx.xxx.xxx.xxx] port yy.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file /username/.ssh/identity type -1
debug1: identity file /username/.ssh/id_rsa type -1
debug1: identity file /username/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.7p1 Debian-8ubuntu1.2
debug1: match: OpenSSH_4.7p1 Debian-8ubuntu1.2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
Connection closed by myip

---

### Post by marcon00 on 2008-09-03
Well i checked with my friend, he has totally different ISP and everything.. he reached the part with password ! so i guess its working after all ! :p ... still need to check it personally

---

### Post by HermanAB on 2008-09-03
Note that dynamic DNS doesn't actually change very often.  When I had a home system on dynamic address, I used to set up a cron job that would email me the IP address every morning and found that it changed about once in 3 months.  So I just stuck the IP into my own BIND server and updated it when it happened to change, which wasn't all that frequent.

---

### Post by baggins on 2008-09-03
**Edit: **[I]Argh ignore this post. Didn't mean to post this after all, it's obsolete by now. 
I wrote the message, but forgot to post. Just came back to the computer now and manage to hit send... And there isn't a delete buttoon is there :)[/I]

> **marcon00 said:**
> well.. i didnt forward any ports, maybe that is why im getting connection refused ?

Yes that would probably be it :) Unless you have some kind of forwarding set up you will be trying to ssh your router, most routers don't really do the ssh thing :)
I have my router at home set up to forward all ssh to my headless (and passively cooled :) ) server. From there I ssh to whatever machine I really need to contact.

> **marcon00 said:**
> 
then again, i shouldnt be trying to * ssh myhost.dlinkddns.com * from within the local network to see if it works, but im still getting connection refused :\

Don't see why that would not work, as long as the forwarding is set up correctly. When you use myhost.dlinkddns.com you are accessing the router from the outside, *not* the local net. So again if forwarding is not setup correctly you will get an error.
 Or maybe I don't understand what you mean?

-- Jon

---

### Post by marcon00 on 2008-09-03
well thats what i ment baggins .. but it doesnt work from within my network, but seems that it does from outside of my local network .. hmmm .. i will keep u posted when i have access to a different connection to try it properly myself :)

---

### Post by windependence on 2008-09-04
It WON'T work from inside your network unless your router does NAT loopback. To access from inside your network you will have to use the internal IP address or add an alias to your hosts file to access the server by name.

-Tim

---

### Post by annatar on 2008-09-04
Or add the computer running the ssh server to DMZ - if your router provides this feature

---

### Post by marcon00 on 2008-09-04
hmm.. possiible :) still didnt get an external connecetion..  :p probably tonight or by tomorrow :)

---

### Post by marcon00 on 2008-09-07
it worked after all :D

---

### Post by marcon00 on 2008-10-13
So i made it work smoothl and all .. now since i traveled .. i try to ssh, it connects fine BUT, it says i typed wrong password ! :S:S:S::S i reinstalled openssh-server on the server and removed host list from client .. changed password on server , and still nothing.tried with couple of usernames tat are on server ... still nothing.. suggestions ?

---

