---
title: "ssh:connect to host restart port 22: Connection refused"
date: 2010-02-19
forum: Ubuntu One (CLOSED)
---

### Post by Rambo007 on 2010-02-19
Hi guys I am getting "ssh:connect to host restart port 22: Connection refused" error when trying to start "ssh" in Ubuntu. I uncommented the port 22 in ssh_config, I dont have iptables setup...Did try to check if the port is listening using the netstat -an | grep "LISTEN" & couldnt find. Any solutions pls......

VIJNB

---

### Post by Neezer on 2010-02-19
> **Rambo007 said:**
> Hi guys I am getting "ssh:connect to host restart port 22: Connection refused" error when trying to start "ssh" in Ubuntu. I uncommented the port 22 in ssh_config, I dont have iptables setup...Did try to check if the port is listening using the netstat -an | grep "LISTEN" & couldnt find. Any solutions pls......

VIJNB

when you say that you "uncommented port 22 in ssh_config" was that on the client or the host? you need to use sshd_config on the host, and ssh_config for the client.

you need to make sure that you have the same port for each computer. So the server should have port 22 enabled in the sshd_config file, and the client should have port 22 enabled in ssh_config.

Hope that helps.

---

### Post by Rambo007 on 2010-02-19
> **Neezer said:**
> when you say that you "uncommented port 22 in ssh_config" was that on the client or the host? you need to use sshd_config on the host, and ssh_config for the client.

you need to make sure that you have the same port for each computer. So the server should have port 22 enabled in the sshd_config file, and the client should have port 22 enabled in ssh_config.

Hope that helps.

Hi thanks for your reply, yes did check the port in Ubuntu where I am trying to start the SSH & also in Windows, both have same port 22.....anyother solutions

---

### Post by Neezer on 2010-02-19
> **Rambo007 said:**
> Hi thanks for your reply, yes did check the port in Ubuntu where I am trying to start the SSH & also in Windows, both have same port 22.....anyother solutions

I didn't know that you were trying to connect to a windows machine....I'm not that familliar with connecting to a windows host from an Ubuntu client.

are you trying to do this remotely (from outside of the network that the host is on)? If you're doing it remotely and you are behind a router, you need to forward port 22 to the LAN IP address of the host machine. I have set up a few Linksys routers to forward my ssh port, and it is pretty straight forward.

---

### Post by Rambo007 on 2010-02-19
> **Neezer said:**
> I didn't know that you were trying to connect to a windows machine....I'm not that familliar with connecting to a windows host from an Ubuntu client.

are you trying to do this remotely (from outside of the network that the host is on)? If you're doing it remotely and you are behind a router, you need to forward port 22 to the LAN IP address of the host machine. I have set up a few Linksys routers to forward my ssh port, and it is pretty straight forward.


oops I am sorry, I forgot to tell you, ubuntu is my server & windows is my client. But right now....while I am trying to manually trying to restart the "SSH", I am getting the error "ssh:connect to host restart port 22: Connection refused"

---

### Post by Neezer on 2010-02-19
so you are on the same network with both computers? using Putty on the windows machine? 

can you describe in detail what you are doing, and what you are typing on which computer to log in....just so that I can get in straight in my head.

---

### Post by Rambo007 on 2010-02-19
> **Neezer said:**
> so you are on the same network with both computers? using Putty on the windows machine? 

can you describe in detail what you are doing, and what you are typing on which computer to log in....just so that I can get in straight in my head.

I am trying to start the SSH & wanted to generate a key yo login from windows using the putty using the key.....for testing puposes.......
My step I am trying to do is starting the SSH & I am getting the error.......

---

### Post by Neezer on 2010-02-20
so you are trying to use putty to connect to an ubuntu machine via ssh. I find that it is a bit simpler to set up the connection with using password login first. then set up the key. that way you know all the settings are working, and it isn't a key issue. It just takes out some variables.

it is important to know if both computers are on the same network or not. Are they?

do you have the ssh daemon installed on the ubuntu computer? when you edit the sshd_config file, you need to restart sshd for the changes to take effect.

---

### Post by 2hot6ft2 on 2010-02-20
You should get it working with passwords first, then move onto setting up the keys. One step at a time or you'll be lost trying to figure out what's wrong.

Start with the guides below

Installing OpenSSH
[http://help.ubuntu.com/9.10/serverguide/C/openssh-server.html](http://help.ubuntu.com/9.10/serverguide/C/openssh-server.html)

I wanted stronger keys so I followed this for the keys
[http://help.ubuntu.com/community/SSH/OpenSSH/Keys](http://help.ubuntu.com/community/SSH/OpenSSH/Keys)

Strong Passwords
[http://help.ubuntu.com/community/StrongPasswords](http://help.ubuntu.com/community/StrongPasswords)

Or there's the How To in my sig to go step by step, but I did it with 2 ubuntu pc's of course there's freenx client for windows too so that's up to you if you would prefer PuTTy.

I found out earlier today as a matter of fact that if I set the "Listen Address #" in sshd I couldn't connect to the server. I got the dreaded **Connection refused** message. Not that I needed to set the listen address.

I'm using a 4096 bit RSA key for SSH and a DSA key on top of that for FreeNX.

Password login disabled naturally and a non standard port.

---

### Post by Rambo007 on 2010-02-20
> **Neezer said:**
> so you are trying to use putty to connect to an ubuntu machine via ssh. I find that it is a bit simpler to set up the connection with using password login first. then set up the key. that way you know all the settings are working, and it isn't a key issue. It just takes out some variables.

it is important to know if both computers are on the same network or not. Are they?

do you have the ssh daemon installed on the ubuntu computer? when you edit the sshd_config file, you need to restart sshd for the changes to take effect.

My main thing is that I should not use the password authentication, but through the key..... I have installed the openssh-server installed & when I restarted the ssh, I am getting the error........

---

### Post by Rambo007 on 2010-02-20
> **2hot6ft2 said:**
> You should get it working with passwords first, then move onto setting up the keys. One step at a time or you'll be lost trying to figure out what's wrong.

Start with the guides below

Installing OpenSSH
[http://help.ubuntu.com/9.10/serverguide/C/openssh-server.html](http://help.ubuntu.com/9.10/serverguide/C/openssh-server.html)

I wanted stronger keys so I followed this for the keys
[http://help.ubuntu.com/community/SSH/OpenSSH/Keys](http://help.ubuntu.com/community/SSH/OpenSSH/Keys)

Strong Passwords
[http://help.ubuntu.com/community/StrongPasswords](http://help.ubuntu.com/community/StrongPasswords)

Or there's the How To in my sig to go step by step, but I did it with 2 ubuntu pc's of course there's freenx client for windows too so that's up to you if you would prefer PuTTy.

I found out earlier today as a matter of fact that if I set the "Listen Address #" in sshd I couldn't connect to the server. I got the dreaded **Connection refused** message. Not that I needed to set the listen address.

I'm using a 4096 bit RSA key for SSH and a DSA key on top of that for FreeNX.

Password login disabled naturally and a non standard port.


>>any try after that, did you make that to work??

---

### Post by 2hot6ft2 on 2010-02-20
> **Rambo007 said:**
> >>any try after that, did you make that to work??
Yeah, it works great. That's why I made the How To. So others could benefit from what I went thru and all the different places I found useful info that went into the setup. Now I can transfer files back and forth, and browse the web using the servers browser so if I'm away and on an insecure network my browsing is still private.

Also just the other day I was looking thru the node.conf file for freenx and found that it's capable of doing a lot more.

I suspect it's the firewall (iptables stopping you, see next post)

PuTTy would be setup pretty similar to setting up freenx.

---

### Post by 2hot6ft2 on 2010-02-20
> **Rambo007 said:**
> Hi guys I am getting "ssh:connect to host restart port 22: Connection refused" error when trying to start "ssh" in Ubuntu. I uncommented the port 22 in ssh_config, I dont have iptables setup...Did try to check if the port is listening using the netstat -an | grep "LISTEN" & couldnt find. Any solutions pls......

VIJNB
Also you say you didn't do anything with the iptables. iptables are essentially the firewall which are set to block incoming connection attempts by default so you need to open the port on the server.

Firestarter is just a GUI (Graphical User Interface) to work with the iptables.
Firestarter is real simple and should already be installed under:
System > Administration > Firestarter
If it's not you can install it with
```
sudo apt-get install firestarter
```
Once you go thru the simple 3 or 4 step setup.
> Firewall, Opening a port

A rule should be added to the servers firewall to allow connections to the servers port. I'm using firestarter, if you're using something else the see the documentation for the one you're using. If using Firestarter open it.
System > Administration > Firestarter

The Staus tab should show it as active
Click on the Policy tab, then left click in the bottom box, then on the + sign.
Here you can enter a Name or use the drop down
Change the port # to the one you setup SSH to use.
And choose who can connect to it. You can choose from Everyone, LAN only, a specific IP Address, or IP Addresses.
You can set it to the IP Address of your client for now (if you want) while configuring things and change it later so you'll be able to connect to it from anywhere.
Click Add, then the Check mark to apply the settings then you can close it. (Once the rule is set closing it does not remove the changes you've made it simply closes the GUI, the changes were saved to the iptables).
Then try to connect

Also restarting the ssh server works like this
> -----
How to start/stop/restart the SSH Server
sudo /etc/init.d/ssh stop

(Replace stop with start for starting it again)
-----

---

### Post by duindain on 2010-06-17
Hi was hoping someone could help with the same issue

I have a ubuntu server with ssh running on it

from a remote host on a different network im trying to use putty to ssh into the server
I have been doing this for years with no issues
all of a sudden im getting a connection refused message
the firewall on the server still has port 22 forwarded
the router has port 22 forwarded to the server

I can ftp and http to the server fine with the same setup really via server and router remotely and locally so its not blocking everything the firewall is definatly allowing ssh traffic in as another pc on the local network can ssh in ok

i can ssh to the server from the local network

Just not remotely anymore

---

