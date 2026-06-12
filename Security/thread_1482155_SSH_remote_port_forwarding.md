---
title: "SSH remote port forwarding"
date: 2010-05-13
forum: Security
---

### Post by NMFTM on 2010-05-13
I'm trying to SSH into my home computer from a remote location outside of my house's LAN and can't figure out remote port fowarding.

The guide [here]("https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding#Remote%20port-forwarding") says to use the following:
```
ssh -R 5900:localhost:5900 guest@joes-pc
```I've tried connecting to my home computer through many combinations of the syntax listed above, read the man file, and looked online for help. But can't find out the proper syntax or a good guide that isn't written for Windows users using Putty.

Let's assume for the sake of simplicity that the public IP address of my  home SSH server is 123.123.123.123, the private IP address of my home  SSH server is 192.168.1.100, my home SSH port is 2222, and the SSH port  at my current location is is 22. How would I write out the command?

Every time I try to connect I get a "connection times out" error.
[ ]("https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding#Remote%20port-forwarding")

---

### Post by tad1073 on 2010-05-13
you need to set up port forwarding in your router to allow traffic from external port 22 to internal port 2222 to ip 192.168.1.100, then you can do:
```
ssh -R you@123.123.123.123
```
the connection from your modem to your router needs to bridged.

---

### Post by NMFTM on 2010-05-13
That's what I thought. But I thought that there might be a way to forward the ports remotely from my current location rather than having to wait until I get home.

---

### Post by cdenley on 2010-05-13
Are you sure you want remote port forwarding, not local port forwarding? Once the tunnel is established, which system is trying to connect where on port 5900?

---

### Post by mr-woof on 2010-05-13
You need to open up port 22 and forwarded it to 192.168.1.100 from inside your network, you won't be able to do that from the outside.

Once done, if you go [www.grc.com](www.grc.com) and run shields up. It'll show up if port 22, is open (good, ssh running and working), closed (port responding, but ssh is stopped) or stealth (bad, not open at all).

---

### Post by EJeanmaire on 2010-05-13
You need the -L switch not -R

---

### Post by NMFTM on 2010-05-13
> **mr-woof said:**
> You need to open up port 22 and forwarded it to  192.168.1.100 from inside your network, you won't be able to do that  from the outside.
Wouldn't I want to do the opposite and forward port 2222 to port 22 for my computer instead of the opposite? So that people wouldn't see things going to port 22 and instantly know I was running SSH?
> **mr-woof said:**
> Once done, if you go [www.grc.com]("http://www.grc.com/") and run shields up. It'll show up if  port 22, is open (good, ssh running and working), closed (port  responding, but ssh is stopped) or stealth (bad, not open at  all).
Wouldn't open ports be a bad thing, as anyone could use them to access  your computer? I thought that stealth was the optimum rating?

---

### Post by XCan on 2010-05-13
> **NMFTM said:**
> Wouldn't I want to do the opposite and forward port 2222 to port 22 for my computer instead of the opposite? So that people wouldn't see things going to port 22 and instantly know I was running SSH?

Wouldn't open ports be a bad thing, as anyone could use them to access  your computer? I thought that stealth was the optimum rating?

You need to open your ports, or else you will never be able to communicate with your home computer. 

I think what you are currently doing is to try and tunnel traffic from your computer to your home computer and out to the internet, which won't work since you can't communicate with your home computer anyway.

Of course you can go to more advanced methods, such as port knocking, but I doubt that is what you're looking for.

---

### Post by OpSecShellshock on 2010-05-13
> **XCan said:**
> You need to open your ports, or else you will never be able to communicate with your home computer. 

I think what you are currently doing is to try and tunnel traffic from your computer to your home computer and out to the internet, which won't work since you can't communicate with your home computer anyway.

Of course you can go to more advanced methods, such as port knocking, but I doubt that is what you're looking for.

Exactly. If you can SSH from an external location to your home computer, then so can anyone else, provided they're able to authenticate. You can assign a port arbitrarily, though, once you get to your hardware router's admin page. Oh, and you need to set your router up to forward the port, but also need to set your home computer itself up to listen for SSH. Your authentication mechanism should probably be strong as well.

---

### Post by pricetech on 2010-05-13
Unless you have set your router up for remote administration, you won't be able to configure from anywhere but its local network.

You probably won't be able to make it work by by forwarding traffic from one port to another either.  In other words if you want to use 2222 you'll have to set your computer up to respond on that port and forward traffic from your external IP to its internal IP.

I suggest you use something in the dynamic / private range above 49151.

Mine are all in the 50xxx range and they work just fine.

---

### Post by NMFTM on 2010-05-13
> **OpSecShellshock said:**
> Exactly. If you can SSH from an external  location to your home computer, then so can anyone else, provided  they're able to authenticate. You can assign a port arbitrarily, though,  once you get to your hardware router's admin page. Oh, and you need to  set your router up to forward the port, but also need to set your home  computer itself up to listen for SSH. Your authentication mechanism  should probably be strong as well.
I was just thinking that since I disabled password authentication and am using a 4096 bit RSA key that's probably sufficient enough that I could set my SSH back to port 22 and not have to worry about anyone breaking in through it.

Does key size have anything to do with how long it takes to tunnel messages back and fourth? Or does it only make the authentication process take longer? I don't think it does but wanted to make sure.
> **pricetech said:**
> You probably won't be able to make it work by by forwarding traffic from one port to another either.  In other words if you want to use 2222 you'll have to set your computer up to respond on that port and forward traffic from your external IP to its internal IP.
I set the "port" option in my sshd_config file to the unused port that I'm trying to connect to. So, as long as I do that I should be fine right?
> **mr-woof said:**
> Once done, if you go [www.grc.com]("http://www.grc.com/") and run shields up. It'll show up if  port 22, is open (good, ssh running and working), closed (port  responding, but ssh is stopped) or stealth (bad, not open at  all).
Shields-Up tells me that my custom SSH port is open, but port 22 isn't. Does that mean as long as I connect using my custom port I should be fine? Because it forwards 22->custom port. But, wouldn't 22 have to be open for that to happen since it's **forwarding** 22 to my custom port? I also have my custom port opened up on my computer as well.

---

### Post by NMFTM on 2010-05-13
I was just also thinking that it's kind of silly of me to think that I'm attaining any security by obscurity by setting my SSH server to listen to a custom port if I'm going to be connecting to be connecting to it through my SSH client on port 22 and having it forwarded to that port after I get to my router, right?

The odds of someone snooping on my packets seems a lot high over the big bad Internet than someone within my own house. If I really wanted security through obscurity I could set my SSH server to listen on port 22, connect to it remotely from a custom port, and than have my router forward that custom port to my SSH server's custom port.

Is everything I just said correct?

---

### Post by pricetech on 2010-05-13
> **NMFTM said:**
>  and than have my router forward that custom port to my SSH server's custom port.

That's what I was saying earlier.  Whatever port you use on your ssh server should be the port you forward in your router.  I've never been able to get a router to accept incoming traffic on one port and send it to the LAN on another.

I'm not saying it can't be done, it just doesn't work on the routers I've tried it on.

---

### Post by icepic on 2010-05-17
step 1: Open a port on your router to connect to. just forward port 22 through router to your ssh box
 
step 2: on client that will ssh through router, enter in terminal
 
                            ssh -ND 6666 username@homeIPaddress
                      ( note: 6666 can be any port number above 1023, has no affiliation with ports open on router) 

you've just created a socks server. set your application to localhost, port 6666, enjoy.

optionally you can run sshd on a different port and forward that through the router, edit sshd_config

---

### Post by NMFTM on 2010-05-18
I tried your method and when running SSH in verbose mode I get the error "ssh_exchange_identification: connection closed by remote host" right after it checks my id_rsa file in /home/user/.ssh.
 
What's weird is it says "type -1" after the name of the id_rsa file even though key based login is type 2. I've Google'd for some answers and people say it might be something with the known_hosts file on my SSH server. But, I never setup anything on the server to only allow remote access from certain computers.
 
So, it must be something with my RSA key.

---

### Post by NMFTM on 2010-05-26
I get the same "ssh_exchange_identification: connection closed by remote host" error when my computer is turned on as when it's unplugged from the wall. I guess this means that my router is closing my connection and it's never actually reaching my computer.
> **icepic said:**
> ssh -ND 6666 username@homeIPaddress
After looking it up, aparently I need a port number after the homeIPaddress. I put in the remote that my router forwards to my computer. But I just got a "could not resolve hostname homeIPaddress:".

---

### Post by PerfectReign on 2010-05-26
Couple of observations.

1. Does your router in fact have port #### open to the intraweb and forwarded to 19.168.x.x inside your LAN?

2. Here's my port forwarding command I use to ssh into my house and use it as a proxy to tunnel out to the internet from within work and also to remotely control my wife's computer (when she needs help).  

sudo ssh -C2qTnN -D 8080 [email]my_user_name@my.public.ip.addres[/email]s


This forwards port 8080 to that IP address. The ip address is the public one given to me by my ISP.  (I have a static IP, but you can use various options if you have a dynamic one.)

On my browser I have foxyproxy setup. 

For that I use 127.0.0.1 as the proxy and port 8080. 

You can also simply ssh into the remote machine by a simple ssh command such as ssh [email]username@your.public.ip.addres[/email]s  to open a shell.  I even can do this from my blackberry.  :)

---

### Post by NMFTM on 2010-06-01
> **PerfectReign said:**
> 1. Does your router in fact have port #### open to the intraweb and forwarded to 19.168.x.x inside your LAN?
Yes, I set my router to forward pory 48555 to port 48555 for my private IP address.

---

### Post by oshirowanen on 2010-06-01
Don't you need apache to get localhost to work first?  Then you can do ssh -L <port><localhost><port> <user>@<server>

---

