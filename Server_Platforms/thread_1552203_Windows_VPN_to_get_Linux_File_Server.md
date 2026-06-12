---
title: "Windows VPN to get Linux File Server"
date: 2010-08-13
forum: Server Platforms
---

### Post by B-Rock on 2010-08-13
Hey 
   
  So I have tried google but it has been a big old fail on my end to find some info I need. I have been using Linux for a while now at home, and am currently running both Ubuntu Server and Desktop at home. Now because I like Linux so much I am trying to bring it into my work place. 
   
  What I am trying to accomplish, but do not know where to look is to have my Linux File server accessible through a VPN that is currently running on a Windows Server 2003. I have Samba up and running to share, and Likewise-open for AD. 
   
  Any help is great because I am just drawing a blank on how to get it to work right.
   
  Thanks

---

### Post by Sunseeker.ch on 2010-08-13
So you want to connect from the W2k3 Server to your Ubuntu Box?
Are you able to install Software on the W2k3 or not?

If give OpenVPN a try, if not you can use the W2k3 VPN which is able to connect ether l2tp or pptp iirc.
In both cases mind the company it policies! A leaner solution might be WebDAV oder SCP/SFTP.

---

### Post by B-Rock on 2010-08-13
The W2k3 already has the VPN all set up and is using a No-ip service. And my "project" linux box is on the same network as the W2K3 server so I want to be able to access my current linux box shares via the Windows VPN that is up and running when working from home (Other users working for home as well).

I am also wanting to do this cause our W2K3 server sucks and I want to get all our Data shares off it. But i first have to prove it can work, I know it can just don't know how, LOL.

Thanks

---

### Post by YesWeCan on 2010-08-13
Don't be sparing with the info. ;) What is your home PC running? Is it linux, is it Windows? What application on your home PC do you want to use to access the files on the linux PC at work? Which bit of the system are you struggling with? Are you allowed to put new apps on/configure the Windows server?

Why do you want to go "through" the Windows box...you could, instead, set up a direct VPN to the linux server and bypass the Windows machine completely.

---

### Post by B-Rock on 2010-08-13
Oh, how i suck at giving info.

The various home computers that use the VPN (Already in place) are XP, Vista, 7, and Ubuntu 10.04 desktop.

On the W2k3 server side of the VPN is an Exchange server (Can't play with that). As well as accessing shares for work data.

What I want to do is have a single authentication using the w2k3 server that will provide access to Exchange on the server and the shares that I will be moving to the linux ubuntu 10.04 server.

And I can play and change settings on the W2k3 server just don't want to change to much as they do not like "change".

Thanks Again.

---

### Post by TJet1.8 on 2010-08-13
Wow....a bit confusing here...let's give this one a shot shall we? :D

Ok...so what we first need to know is what VPN application you have running on your W2K3 server at work...and what VPN clients your home users are using.

In the interim, why don't you install OpenVPN server on your Test Ubuntu Server at work and open some obscure port in your firewall to allow the OpenVPN client to connect to it over the internet.

Once set up, you will end up with 2 VPN system's at your work (Ubuntu & W2K3) for now....

OpenVPN can act as either a client or a server for both Linux and Windows...so everybody's happy, you just need to google how to configure it.

Once connected, all your home users will have access to your work network...and anything that's running in your work network. 

So...once you provide the VPN information on your W2K3 server at work, we can then determine if we can use it with OpenVPN...or some other VPN application.

I hope this isn't too confusing.

:P

---

### Post by B-Rock on 2010-08-17
OK, so I am back at work..... had a "case of the Mondays"

The VPN right now on 2003 is using PPTP, and since work does not have a static IP we are using the no-ip service. So for me to hookup OpenVPN I don't really see how I would be able to use it/test it.... I am new to VPN's.

Sorry to be a PITA.

---

