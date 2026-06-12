---
title: "SSH blocked on every port?!?"
date: 2009-04-09
forum: Server Platforms
---

### Post by jigglywiggly on 2009-04-09
So I go to this place and it's pretty advanced. Anyway when I try to ssh my server on port 8080 it can't connect. So I tried port 21 which does work on their computers(random ftp) So then I tried port 25 still didnt work. I tried port 23 and tried telneting didn't work either?! It works on any other conneciton. How are they blocking ssh like that? Is there a way to get around it?
Oh and I was using myentunnel to connect.

---

### Post by jowilkin on 2009-04-09
I don't entirely understand your question.  SSH is normally run on port 22, have you tried that port?  You cannot try to connect to any old port for SSH, the server will generally be listening for SSH traffic on only one port and the default is normally port 22.

Are you able to setup the tunnel successfully with myentunnel?  Is the problem that after you setup the tunnel you cannot use other ports for things other than SSH?

---

### Post by jigglywiggly on 2009-04-09
I told the server to listen on port 8080, it used to be port 22 but I changed that for security reasons. And port 22 didn't work over there either. I can connect on port 8080 using any other internet connections though.

---

### Post by jowilkin on 2009-04-09
Is the machine behind some kind of firewall?  That would explain things.  Although most firewalls will at least allow port 22.

---

### Post by MrWES on 2009-04-09
> **jigglywiggly said:**
> I told the server to listen on port 8080, it used to be port 22 but I changed that for security reasons. And port 22 didn't work over there either. I can connect on port 8080 using any other internet connections though.

If you're behind a router you'll need to forward port 8080. Also, what port did you put in /etc/ssh/sshd_config ?

Bill

---

### Post by BkkBonanza on 2009-04-09
Port 8080 is a fairly common port. So if you're wanting to change your ssh port in the hopes of gaining a smidgen of security by oscurity then use an uncommon port. Unless you give dtails about how the machine is connected to the net, via a router or isp, lan etc. it will be hard for anyone to guess what may be blocking your port. Use the command,

sudo netstat -lnptu 

to see that ssh is listening. If it is then you need to look at what else is between you and the port.

---

### Post by daboroe on 2009-04-09
> **jigglywiggly said:**
> I told the server to listen on port 8080, it used to be port 22 but I changed that for security reasons. And port 22 didn't work over there either. I can connect on port 8080 using any other internet connections though.

If Behind:

Router: You need to forward your port. Please go to [http://portforward.com/](http://portforward.com/) and check out your router that is listed to make sure you are properly forwarding ports

Firewall: Create a rule in the firewall ACL to allow traffic in and out of the firewall through that port.

If you are using UFW which is really easy to set up run the following:

# ufw logging on 
# ufw allow|deny [service]

$ sudo ufw allow 8080/tcp
$ sudo ufw allow 8080/


$ sudo ufw delete allow 53

Allow port 80

$ sudo ufw allow 80/tcp

Delete Allow port 80

$ sudo ufw delete allow 80/tcp


see if that fixes your issue.

---

### Post by jigglywiggly on 2009-04-09
I know how to port forward, the server is port port forwarded on 8080. I can connect to it from my iphone, and any random connection I can find, even wireless ones it will connect, no port forwarding needed on the client. So I am confused what you guys want me to do D: I mean the place I go to I don't have any admin privs. They have like cisco routers n shiz. They also have iprism that might have anything to do with it?

---

### Post by BkkBonanza on 2009-04-09
If you want to solve your problem then look at it step by step. I gave you the first step. Check that ssh is listening on the port you want. Then do a shields up port scan from outside your network to see that the port is open. If you cannot forward a port because it's not your router then you are hooped. You cannot listen on a port that you don't have forwarded out of your network - not from the internet anyway.

Shields up here,
[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

If you cannot get to the port due to lack of control of the router then you have to look at alternatives. One alternative is to use a reverse tunnel. That will allow ssh to listen on a port on some other machine on the net instead of the one it's running on. You can then connect to that machine and be forwarded to your machine. For this you need a machine on the net with a static ip since it can't follow a dynamic one (not without a lot of config).

---

### Post by FrankT-Qc on 2009-04-09
Well, there are a few places out there that do packet inspection to avoid people to establish tunnels through their firewall... could it be such a situation ?

Go to starbuck and try to ssh in... If you can't... "man ssh"

---

### Post by jigglywiggly on 2009-04-10
> **BkkBonaza said:**
> If you want to solve your problem then look at it step by step. I gave you the first step. Check that ssh is listening on the port you want. Then do a shields up port scan from outside your network to see that the port is open. If you cannot forward a port because it's not your router then you are hooped. You cannot listen on a port that you don't have forwarded out of your network - not from the internet anyway.

Shields up here,
[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

If you cannot get to the port due to lack of control of the router then you have to look at alternatives. One alternative is to use a reverse tunnel. That will allow ssh to listen on a port on some other machine on the net instead of the one it's running on. You can then connect to that machine and be forwarded to your machine. For this you need a machine on the net with a static ip since it can't follow a dynamic one (not without a lot of config).

My home's adress is a static ip thankfully. What you are telling me is it just a way to check if that port is open or something? Cuase I know 8080 is open, I spoke with home though he told me ssh might be blocked, he said I blocked telnet on any port. I was like D: I think he is ok with SSH if I ask him again though. I think he was using packet inspection stuff.

---

### Post by windependence on 2009-04-10
> **jigglywiggly said:**
> I know how to port forward, the server is port port forwarded on 8080. I can connect to it from my iphone, and any random connection I can find, even wireless ones it will connect, no port forwarding needed on the client. So I am confused what you guys want me to do D: I mean the place I go to I don't have any admin privs. They have like cisco routers n shiz. They also have iprism that might have anything to do with it?

They're probably using something like Mickey$oft ISA server. Set up your ssh to listen on port 443. Most likely they HAVE to have that open anyway, and they can't inspect the encrypted traffic. That's how I used to access my servers from work. Once in, you can ssh to any other machine on your network.

-Tim

---

### Post by jigglywiggly on 2009-04-10
Port 443 huh? Sounds like it would work, I should test it out. However unfortunately I am using that port for my https file transfer server D: hmm, I'd need another ip from my ISP which is totally possible to be arranged. I'll ask him again if he can  allow it on port 22 or 8080 or something(or a random port like 25353 I wouldn't care. But I mean does it really make a difference what port I use, I mean you can still port scan.

---

### Post by BkkBonanza on 2009-04-10
Sounds like you're trying to bypass someones legit security. That's a very different question than what you started with on this post. And personally I'm not party to helping here any more.

---

