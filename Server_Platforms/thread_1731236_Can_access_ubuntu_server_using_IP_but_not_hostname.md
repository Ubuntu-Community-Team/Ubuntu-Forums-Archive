---
title: "Can access ubuntu server using IP but not hostname"
date: 2011-04-16
forum: Server Platforms
---

### Post by spuddo on 2011-04-16
Hi, I am fairly new to the world of ubuntu.  I have just installed server 10.10 and included; openssh server and Samba.

I have a small home LAN with three windows PCs on a wirless router and wish to use the server for backup, media etc.  The server has a fixed IP from the router.  I can access the server from the Windows PCs using it's IP address but not using it's hostname.  The server does not appear in the windows network.  This seem a common problem on many forums, but after countless hours searching I have not been able to find a solution.  It seems something to do with resolving the hostname?  I an hoping it is just a small oversight.

I can access the server using ssh but agin only by using the IP address.

Thank you in advance for your help.

---

### Post by volkswagner on 2011-04-16
This is a DNS issue.

There are a few things you can do.

You can run a local DNS server.

You can change your ip configuration, using your router vs. static ip in Ubuntu /etc/network/interfaces.  If your router can set the static ip of your server based on its mac address, you can set the Ubuntu-server to DHCP... it will always get the same address from the router.

This may fix your issue, since the router will have the hostname available.

If you have SAMBA server running on the Ubuntu Server, be sure to set the workgroup to the same as your windows machines.  Also list the SMBbios name int smb.conf.

If there are only a few machines you can also edit the host record for each machine which will map the ip address.  For Ubuntu location is /etc/hosts.  For windows clients >Windows\System32\drivers\etc\hosts.

---

### Post by jawilljr on 2011-04-16
Add the server name into the Windows hosts file. In Windows XP it is located in:

```
\Windows\system32\drivers\etc
```Just add an entry to the bottom like this:

```
192.168.1.5 servername
```Of course change the IP and servername to their respective values.

That should work.

Jerry

---

### Post by spuddo on 2011-04-17
Gentlemen, Thank you for your prompt replies.  I am making some progress.  I chose to try editing the Windows host file as a start.  It is easy but will not be a final solution as I want persons who may arrive with laptops to connect via wirless and access the server.  Nevertheless editing the Windows file to include the IP/hostname has now allowed me to ssh into the server using its hostname.  The server now appears in Windows network as "Unknown device".  I can't connect to it except via its IP.

I like the DNS solution but need more specifics please.  My router provides DHCP (I think) i.e it serves IP adresses and I have set it up to always provide the same IP address to the server based on it's MAC address - effectively static.

My server is set to WORKGROUP the same as my Windows PC.

I did not understand this comment* "Also list the SMBbios name int smb.conf"*

Thank you again for your help and patience with a new starter.

I would attach my smb.conf file if I could work out how to do it?

Russell

---

### Post by volkswagner on 2011-04-17
Here is the relative portion from my smb.conf:

```
# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WAGNERHOUSE
   netbios name = Mini
   usershare owner only = false

```

When you log into your router can you see the hostname for your server under the list of DHCP clients. or is it blank "*"?

For running a local dns server you can check the [sticky]("https://help.ubuntu.com/10.04/serverguide/C/dns.html") at the top of this forum.

---

### Post by spuddo on 2011-04-18
When I go into the router I can see my server ubuntu-minerva-server listed as 192.168.1.50.  This is the static IP address I have set up.

The /etc/resolv.conf files shows 

nameserver 192.168.1.1

That is the IP address of my router

I have been doing some reading and was trying to use the /etc/hosts file to map the server/IP address rather than set up a DNS server.

/etc/hosts looks like this before I make any changes.

127.0.0.1       localhost
127.0.1.1       ubuntu-minerva-server

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters


I am not sure what 127.0.1.1 is, but its not the IP of my server.

I will keep researching and experimenting and welcome any ideas.

Russell

---

### Post by Morbius1 on 2011-04-18
Still not sure if your using samba in all this but your machine name is too long:
> ubuntu-minerva-server[COLOR=Blue]It has to be 15 characters or less in length.[/COLOR]

Easiest way to fix this is to use samba itself. Go back to volkswagner's suggestion and change the netbios name to say ...
```
netbios name = minerva-server
```Then restart samba:
```
sudo service smbd restart
```

---

### Post by volkswagner on 2011-04-18
```
127.0.0.1 localhost
127.0.1.1 ubuntu-minerva-server
```

The above should be fine for the server to know it's own name.  You can confirm the server "knows's" it's own name by ssh'ing into itself using the hostname.

I thought the issue was just so the Windows machines could access the server via the hostname.  All you should need is the windows machines hosts file edited to show the server.  

Your server's hostname is a little long and may be causing some issue if the Windows hosts file is not binding the name to the address.  I think the limit is 15 characters for NetBios name in MS Windows world.

---

### Post by iponeverything on 2011-04-18
Name resolution can be done though SMB, DNS or the local host file.

Your best bet would would be to setup a DNS server and have your DHCP server hand out that address to the clients for name resolution - But

Seeing as how you are unfamiliar with the loopback address, I think that you first need to get some networking basics under your belt before you tackle installing a nameserver. For your needs just using the ip address might be your bet. 

This might be a good place to start if you decide you want to go the DNS route:

[http://www.wlug.org.nz/BindVsTinyDNS](http://www.wlug.org.nz/BindVsTinyDNS)

---

### Post by collisionystm on 2011-04-18
On your ubuntu server, take a look at the file /etc/resolv.conf

make sure namesever xxx.xxx.xxx is the ip address of your router ( dns server)
 I.E.  nameserver 192.168.1.1

check the file, /etc/network/interfaces  | nano /etc/network/interfaces

iface eth0 inet static
        address xxx.xxx.xxx
        netmask xxx.xxx.xxx
        broadcast xxx.xxx.xxx
        gateway xxx.xxx.xxx

make sure you have a gateway listed in there for eth0 ( should once again be the ip of your router)
gateway 192.168.1.1

decide on a name for your server and assign it by typing hostname <hostname>
I.E. hostname oscar

I see you have installed samba, nano /etc/samba/smb.conf and check your host name in there.

now run /etc/init.d/networking restart

Your server should register with the DNS router. You can now go to your Windows box, go to command prompt and type ipconfig /flushdns 

Wait a min and type ping <hostnameofserver>

and see if you get replies.

---

### Post by collisionystm on 2011-04-18
Oh and when your in nano, to save your work and exit, just hit CTRL + X and then press y to save N to NOT SAVE and exit

---

### Post by Sirkyuubi on 2011-04-18
> **collisionystm said:**
> 
Your server should register with the DNS router. You can now go to your Windows box, go to command prompt and type ipconfig /flushdns 


Im pretty sure you need to open the command prompt as administrator to get these commands to work right. goto start / programs / accessories / system tools. Right click on command prompt and click run as administrator.

Also after you flush the dns on the windows box you will need to re register the dns too.

ipconfig /registerdns

---

### Post by collisionystm on 2011-04-18
> **Sirkyuubi said:**
> Im pretty sure you need to open the command prompt as administrator to get these commands to work right. goto start / programs / accessories / system tools. Right click on command prompt and click run as administrator.

Also after you flush the dns on the windows box you will need to re register the dns too.

ipconfig /registerdns


You only need to do this right click on Windows Vista and 7 =)

And flushing DNS only flushes the workstations resolve cache. When you do a registerdns, you are forcing the box to communicate with the dns server and register its host record so others may find it. Or so I have come to find.... ;)

But none the less. hopefully this solves this guys problem, eh?

---

### Post by spuddo on 2011-04-19
SOLVED :Reducing the hostname length to less that 15 characters has fixed everything.  I can now ssh using the hostname and can connect to the Samba shares using the hostname.  The ubuntu server now appears in the Windows network and I can browse folders.

Such a simple issue that would never have been rersolved without your help.

Thank you all for your kind help and expert advice.  I will continue to read and explore more about networking so that I can be less reliant on everybody.

Russell

---

### Post by wardevour on 2012-11-02
i fixed this same problem by making my ip address static. i guess this should have gone without saying, but i didnt think it mattered if the ip never changed.

---

