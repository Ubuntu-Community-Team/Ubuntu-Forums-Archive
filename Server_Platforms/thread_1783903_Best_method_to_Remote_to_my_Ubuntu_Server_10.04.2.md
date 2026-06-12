---
title: "Best method to Remote to my Ubuntu Server 10.04.2"
date: 2011-06-16
forum: Server Platforms
---

### Post by newbuntu007 on 2011-06-16
I'm back. I have a fresh built ubuntu server and I would like to remote to it so I can
run commands and as well restart and do updates away from my house....etc
 
 
What is the fastest and best method?
 
I'm running the server as just a file server, with webmin and created some samba shares for my windows clients[That's it]. Tinkering around with little things here and there as well.
 
I've heard of Telnet/SSH/VNC.[confused] 
 
I downloaded PUTTY as it seems to be a software you use to connect but how does one go about setting it up 
 
1. *Internally[connectin to my server away from my desktop at my house]
 
2. *Externall[connecting to my server from work]
 
Thanks/Sorta new to Linux but learned a lot setting up my RAID5.

---

### Post by Lars Noodén on 2011-06-16
> **newbuntu007 said:**
> 
I downloaded PUTTY as it seems to be a software you use to connect but how does one go about setting it up 

PuTTY provides you with SSH.  SSH is indeed the fastest and best way to manage a remote machine.  It is already set up if you have installed [OpenSSH-server](http://packages.ubuntu.com/natty/openssh-server).   Then just point PuTTY at your server and log in.

---

### Post by Lars Noodén on 2011-06-16
> **newbuntu007 said:**
> 
2. *Externall[connecting to my server from work]


If you are connecting via a modem then you will probably have to set the modem to forward incoming port 22 (SSH) to your server.

---

### Post by newbuntu007 on 2011-06-16
I'm not sure if I have open-ssh installed. If it is a server can I run a net command to see if it's listening? I might have to install it.

How would I install open-ssh?

Edit: I do have openssh installed. I woill only be connecting through ethernet.

Ok I think I got it working.  I set up SSH through Webmin/forwarded port 22 but I would like it to be more secure maybe I can post my ssh.conf setup and someone can help me?

---

### Post by Lars Noodén on 2011-06-16
> **newbuntu007 said:**
> ... I set up SSH... I would like it to be more secure ...

Turn off remote root log in /etc/ssh/sshd_config.  You will find it under the name **PermitRootLogin**.  Set it to "no".  

Otherwise, SSH is very secure and not much can be done.  The only other thing you might do would be to use keys instead of passwords, but that is not necessary.

---

### Post by newbuntu007 on 2011-06-16
Yup it was setup up as default on there as "NO".

How would I connect outside my home to my server?



> **Lars Noodén said:**
> Turn off remote root log in /etc/ssh/sshd_config.  You will find it under the name **PermitRootLogin**.  Set it to "no".  

Otherwise, SSH is very secure and not much can be done.  The only other thing you might do would be to use keys instead of passwords, but that is not necessary.

---

### Post by Lars Noodén on 2011-06-17
Check first to make sure that port 22 is opened on your network.  One tool for that is [canyouseeme](http://canyouseeme.org/).  Once it's open on your modem (assuming you are connecting via ADSL) then have the mode forward port 22 to your server.

---

### Post by egpetrich on 2011-06-18
For clarification, go to [http://www.canyouseeme.org](http://www.canyouseeme.org) from your home computer. This will do two things:
[LIST=1]
[*]Let you see the external IP address of your home's router.
[*]Let you test if port 22 is visible through your home's router.
[/LIST]
As someone said earlier, you need to configure your home's router/DSL modem/cable modem to forward port 22 from the outside world to your Linux server. Usually this will require that your Linux server have a fixed IP address, instead of one assigned automatically via DHCP. The method for forwarding ports is pretty specific to the router you have as well as the firmware installed on it; you will need to consult your own documentation. 

Try to set up port forwarding before you visit canyouseeme.org, or there won't be anything listening and the test will probably fail.

Your home router's IP address is probably not fixed; if it is fixed, you are probably paying extra for it and already know this. For dynamic addresses, you may want to use a dynamic DNS service such as dyndns.com or no-ip.com. This will give you a DNS name that will track your router's IP address. (My own IP address doesn't change very often, so I have skipped this step and simply use the IP address.)

In my case, connecting with PuTTY requires three different profiles:
[LIST]
[*]Inside my home network
[*]Outside my home network, but not at work
[*]At work (in order to use the proxy server)
[/LIST]
I like to use key-based authentication with Pageant (PuTTY's authentication agent), to avoid having to enter my user password each time I connect. Instructions for setting this up are in the PuTTY help documents. Once it's set up, put a shortcut to your *.ppk file in your "Startup" folder. Then Windows will prompt you for your passphrase when it boots, and you'll have automatic authentication thereafter.

---

### Post by craigcrawford114 on 2011-06-19
egpetrich, have you tried PuTTY connection manager? You create a passworded database with your server logins and it then it logs in for you. You must enter the DB password each time it starts up for security though.

---

### Post by crispy_420 on 2011-06-22
So has this info helped and worked out for you?

The basics are: 

1) setup ssh server 
2) reserve server IP on local network
3) setup dynamic dns service
4) forward correct port on router to server
5) test

---

