---
title: "stupid server noob questions"
date: 2009-05-16
forum: Server Platforms
---

### Post by Screwdriver0815 on 2009-05-16
Hi at all,

I want to re-use my old computer by installing Ubuntu Jaunty Server Edition on it. 

The goal is maybe stupid but somehow useful for me: I want to let it run at home while I am away and I want to have access to the stored files and to store new files on the server-HDD.
The access I want to have is by typing the IP-Adress into the browser of my Laptop and (for security)  username + password. Personally I think, the password would be enough.

So for that I am reading documentations for a week now and the more I read, the more I get confused.

What I have learned:
I need to set up my Router for NAT (network adress translation). So that I can type in one IP-Adress (the one of the server) to get access to the server.
But (thats what I dont understand): what should I type into the menu of the router?
When I go to the NAT-config-menu, I can choose between three options: 

- without
- SUA only
- complete

by default "SUA only" is choosen and when I go into the details-configuration I can choose "first port", "last port", "all ports" and type in an IP-Adress... and finally I can "activate Emule for the following IP-Adress" which is followed by a pulldown menu with IP-Adresses (maybe the ones which are currently in the network).

As I don't want to destroy my internetconnection I would like to ask for some assistance in fillig the options.

But I also have another question: what if I leave my server as it is, with dynamic DHCP and so on? Is there a way to access it by the computername for example? But I do not want to set up this DNS and nameserver stuff (as this is way too much effort for a stupid fileserver)?
Can I maybe access it via SSH and the computername, I gave it during install plus the SSH-key and so on? What do I have to do for that?

Thank you very much in advance for pushing me in the right direction and sorry for these stupid questions

---

### Post by hictio on 2009-05-16
So, you want to access your Ubuntu Server, via SSH, from the Internet? Is that so?
First thing I would say is, if your router supports it, get a [Dyn DNS](http://www.dyndns.com/) account, and setup the router to keep the hostname that you choose update with the IP address that you have at your house.

That way, you'll always use the hostname that you choose to access your machine, that is, you'll type type:

```

ssh the.hostname.that.you.choose.dyndns.org

```

And to actually access the server, you have to do a port forward from your router, to the port 22 of the internal IP address that the Ubuntu Server it is using on your LAN.
It is better practice to have the Ubuntu Server inside your LAN with a fixed IP address, rather than getting a dynamic IP address thru your router's DHCP server. 

What router do you have?

---

### Post by Screwdriver0815 on 2009-05-16
the router is an Zyxel P660HW-T7C.

The ideal way for me to access the server would be:

I install SSH on the server and the Laptop, generate an key-pair and then log in from everywhere in the world.
I also would do the same with my desktop PC (different machine as the server) and log in for storing files and doing all the maintanance on the server.
More ideal would be if I also could use a windowsprogram (if I maybe want to share some directories on the server with some friends who use windows) which also uses SSH, generates their own keys and logs into the server.

But I don't want to create such an DNS account. :confused: what I have learned is that I can use either an IP-adress or a DNS adress. So if I just use the IP-address, this would be fine for me. 

Do I have to type in the IP address of the router then, when I (for example) sit in Canada and want to store some pics on the server?

Thats why I have asked for this NAT-thing. The next difficulty for me is to find out which external IP-address the router has... but thats a different story I think.

But (and this confuses me) when I use the SSH: in all these HowTo's I have read so far, the guys put in the internal IP-Address of the server (inside the LAN). And there is no description how to do this from remote. Why? is it not recommended because of security reasons?

I am really confused so maybe I mix up everything... any help would be very much appreciated!

---

### Post by hictio on 2009-05-16
> 
The next difficulty for me is to find out which external IP-address the router has... but thats a different story I think.


To get your public IP address, from a box inside your LAN, go to: [http://checkip.dyndns.org/](http://checkip.dyndns.org/)

There are other web sites that do that as well.

> 
But I don't want to create such an DNS account.  what I have learned is that I can use either an IP-adress or a DNS adress. So if I just use the IP-address, this would be fine for me.


The thing with the DynDNS hostname is that running one of their clients on your router, if it supports it, it will keep you worry free if your public IP address changes. What type of connection you have to the Internet?  A DSL one? Do you have a fixed IP address?

> 
in all these HowTo's I have read so far, the guys put in the internal IP-Address of the server (inside the LAN). And there is no description how to do this from remote. Why? is it not recommended because of security reasons?


If you are outside your LAN, you'll have to use your external. public IP address; and, unless you have a router that has NAT capabilities many-to-many (and an extra public IP addres for your Ubuntu Server), you'll be using the IP address of the router, that will in turn, route you to the internal IP address of your Ubuntu Server.

> 
More ideal would be if I also could use a windowsprogram (if I maybe want to share some directories on the server with some friends who use windows) which also uses SSH, generates their own keys and logs into the server.


Personally, I would concentrate first on getting connected the plain vanilla way, user/ password, then, when connectivity is not an issue, it is trivial to setup public key auth to your server, specially if you are ssh'ing from another Linux box.

Take a look at your router's setup to make a port forwarding, for port 22, on the router itself, to port 22 for the internal IP address of your Ubuntu Server, all TCP.

Once this is working, you can tight the thing up with brute force attack blockers, and editing the /etc/ssh/sshd_config file.

---

### Post by Screwdriver0815 on 2009-05-16
thank you very much for your answers. 

I have a DSL connection. All the IP-adresses behind the router are dynamic, done with the DHCP. But I have no clue about the external IP. I did not get any IP-information from my ISP. So I think it is maybe dynamic too?

As far as I have seen, the router supports the DNS-stuff. So it looks like it is better to register a DNS then... But this I will sort out later on.

For the first steps just one question reg. the ports: in the router I have a NAT setup which consists of a table with "first port", "last port" and the IP adress, see screenshot. The language is german, so "erste port Nr" means first port number and "letzte port Nr." means last port number. 

and under the table is written "activate settings for the following IP adress". 

What do I have to put in there? Should I put in port 22 into the first port and the last  port and activate this for the IP of the server?

---

### Post by hictio on 2009-05-16
I would say that you have to put on both erste und letzte port ;) the number 22, which is the port that the sshd daemon uses by default, and on the other box, the IP address of the Ubuntu Server has inside your LAN, the private one.

Once you have that going, and that you know your public IP address, the one that the ISP gave you and your router has, then, from a box outside your LAN, test the connection issuing a:

```

telnet your.pub.ip.address.here 22 ENTER

```

You don't need to test this from within a Linux box, a Windows one will do just fine.
If everything went smooth, you'll see something like this:
```

Connected to your.server (xxx.xxx.xxx.xxx).
Escape character is '^]'.
SSH-2.0-OpenSSH_4.3

```

Press ENTER a few times to disconnect.

If it doesn't work, there are a couple of things to consider, one is that your ISP blocks the SSH port, but that can be over ridden using another port; the other is that the port forwarding is not working, and the last one might be that the sshd daemon is not running on the Ubuntu Server.

---

### Post by Screwdriver0815 on 2009-05-16
okay, I have put in the portnumber and the IP forwarding. I also have set up a static IP adress inside the home network for the server using the MAC adress of its ethernet card

the testing will be done in the next time. 

I also have checked if the sshd daemon is running on the server - yes it is, so this is no source for trouble. 

ssh'ing into the server works now, but how do copy files to and from the server? Do I have necessarily to use Samba or NFS?

---

### Post by Cheesemill on 2009-05-16
> **Screwdriver0815 said:**
> ssh'ing into the server works now, but how do copy files to and from the server? Do I have necessarily to use Samba or NFS?

You can use the scp command from Ubuntu, or WinSCP from a Windows box.
Both of these work over SSH so no additional setup is needed.

Cheesemill

---

### Post by hictio on 2009-05-16
> 
ssh'ing into the server works now, but how do copy files to and from the server? Do I have necessarily to use Samba or NFS?


No way in Hell, if you have SSH access, you use [scp](http://en.wikipedia.org/wiki/Secure_copy) and [sftp](http://en.wikipedia.org/wiki/SSH_file_transfer_protocol) to copy files back and forth.
Also, you can use [rsync](http://en.wikipedia.org/wiki/Rsync) over ssh too.

You can use those either from the command line, or with graphical clients on Windows or on Nautilus in Gnome, if that rocks your boat.

---

### Post by Screwdriver0815 on 2009-05-16
great! Thank you for your help.

---

### Post by Screwdriver0815 on 2009-05-17
okay, next problem/ question:

I think I have killed my internet connection by setting the NAT and the static IP-Address to the server (in correlation to its MAC-address).

But this was really strange: first, the connection was up and running for a couple of hours and at some moment everything stopped working. The server was shut down as this happened.

I have done some actions to get it run again but only deleting the NAT-stuff (port 22 and the IP-address of the server) and the static DHCP for the servers MAC address (fixing a static internal IP to the server) fixed the problem and the connection.

Whats that? Can anybody explain what I have done wrong?

thanks in advance

---

