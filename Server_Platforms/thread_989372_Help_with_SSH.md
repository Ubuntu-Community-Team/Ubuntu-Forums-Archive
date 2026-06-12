---
title: "Help with SSH"
date: 2008-11-21
forum: Server Platforms
---

### Post by roundhay on 2008-11-21
I have installed Ubuntu Server 8.10 on a machine that I intend to run as a headless server.

I choose to install all of the programs during the installation process except the mail server.

to kick things off I would just like to be able to connect to the machine via SSH from the other PC's in my house.The other PC's all run Ubuntu and I have installed Open-SSH on them. 

I seem to have fallen at the first hurdle and can't log in via SSH.

During the set up of the server I used the following settings:

Hostname = server
User = blue
Username = blue
password = ********

I left the http proxy as blank

I can see the server on the network places/network can access to only windows share the print folder.

I have tried to log in via the command line using:

ssh blue@server

but I get the following error message:

ssh: server: Name or service not known

I have tried using putty and the host name 'server' but nothing.

I ran /etc/init.d/ssh start on both the server and client machine and got the notification that they were running.

Any ideas how I can get this working? I am a bit of a noob

---

### Post by moonpup on 2008-11-21
This sounds like a DNS issue, where it can't resolve the server name. Try using the ipaddress and see if that works. You may want to add the server to the hosts file of the clients.

---

### Post by afzal_du on 2008-11-21
when you log in to the target machine (normally) and open terminal does is show bleu@server ?? I think the target host has a different name other than server. If the terminal shows "blue@green:~$" you should use
ssh blue@green or
ssh blue@your_ipaddress

---

### Post by hrod beraht on 2008-11-21
**Name or service not known** means that the IP address for the *server* name is not known. ssh doesn't connect to names, but to IP addresses, so it has to have some way to translate the name to an IP address. Is *server* defined in your hosts file? (e.g. 192.168.1.123 server)
If it's not, the computer your trying to ssh from simply doesn't know where to look for *server*. So add it to your hosts file, or, alternatively (but more of a pain), use it's actual IP address rather than it's name (e.g. ssh blue@192.168.1.123)

Bob

---

### Post by roundhay on 2008-11-21
Thanks for the suggestions, I assume I am going to have to assign a fixed IP to the server so that I can access it?

---

### Post by hictio on 2008-11-21
> **roundhay said:**
> Thanks for the suggestions, I assume I am going to have to assign a fixed IP to the server so that I can access it?

No need to, and it won't end your problem, because the hostname will be not resolving either, if you can't add it to a DNS server, totally unnecessary for a home LAN, do what hrod beraht told you.
Add that IP address to your /etc/hosts file, you'll have to use sudo to edit the file, it will have to be something like this:

```

blue    ip.address.of.blue.here

```

If you don't have that many boxes to deal with, it is a crude, fast and a PITA to maintain, way of resolving hostnames :D

---

### Post by hrod beraht on 2008-11-21
> **roundhay said:**
> Thanks for the suggestions, I assume I am going to have to assign a fixed IP to the server so that I can access it?

Realistically, yes. You don't absolutely have to, but if you just use DHCP and get a different address after every reboot, it would complicate things tremendously - and unnecessarily so, as creating a fixed IP address isn't difficult and is a one-time thing.

See the [[COLOR="Blue"]Ubuntu Server Guide networking section[/COLOR]]("https://help.ubuntu.com/8.10/serverguide/C/network-configuration.html") if you aren't sure how to do a fixed IP.

Bob

---

### Post by hrod beraht on 2008-11-21
> **hictio said:**
> No need to, and it won't end your problem, because the hostname will be not resolving either, if you can't add it to a DNS server, totally unnecessary for a home LAN, do what hrod beraht told you.

hictio makes an excellent point. I assumed access only from within a home LAN, which may be a bad assumption. Adding a 192.168.1.xxx address to your hosts file isn't going to work outside of your LAN. If you are accessing your server via SSH from outside your LAN, from the internet, you are actually going to be accessing your router, which will in turn forward to your local 192.168.1.xxx address. So outside your LAN you need to use your router IP address. Or, as hictio mentioned you should ideally have your address in DNS so that you can just use *myserver.com* or whatever domain name you may have and have it automatically translate into your IP address at home. If you don't have a domain name and want a quick way to get DNS forwarding, consider using the free service at [[COLOR="Blue"]dyndns.com[/COLOR]]("http://www.dyndns.com/services/dns/dyndns/")

Bob

---

### Post by roundhay on 2008-11-21
I have looked at this and it worries me.....

I have changed the DHCP rage in my router and plan to use 192.168.1.*** as the IP address for the server.

If I amend the /etc/network/interfaces file how should it look? I know the address and netmask but what is the gateway? Is this the IP of the router?

iface eth1 inet static
	address 192.168.1.***
	netmask 255.255.255.0
	gateway ????????

After doing this do I really need to amend the /etc/resolv.conf file? This is the part I am not comfortable with?

I've struggled with fixed IP's in the past

---

### Post by hrod beraht on 2008-11-21
[QUOTE=roundhay]...what is the gateway? Is this the IP of the router?[/QUOTE]
Yep. It's probably 192.168.1.1 To check, you can always just try going to [http://192.168.1.1](http://192.168.1.1) in your browser and see if you get your router's login.

[QUOTE=roundhay]I've struggled with fixed IP's in the past[/QUOTE]
Step 1: give your server a static IP as you've started to do below.

iface eth1 inet static
	address 192.168.1.***
	netmask 255.255.255.0
	gateway ????????

*** IF YOUR SERVER ISN'T GOING TO BE AVAILABLE ON THE INTERNET, BUT ONLY ON YOUR LOCAL LAN, IGNORE THE STUFF BELOW ***

Step 2: go into your router setup (usually by going to [http://192.168.1.1](http://192.168.1.1) in your browser) and forward the appropriate ports. For example, for SSH and HTTP you want to forward ports 22 and 80. Forward them to whatever address your server is, e.g. 192.168.1.xxx

That's it. Your server is now available on the internet.
Basically it goes like this:
Assumptions:
-- your server's internal IP address is 192.168.1.123
-- your actual IP address to your router (from you service provider) is 123.456.789.0
-- you forwarded both ports 22 and 80 in your router to point to 192.168.1.123

If the above is true, you can - from the internet - type **ssh blue@123.456.789.0** and it will go to your router, which will forward it to 192.168.1.123 and voila! your server will ask for your ssh password.

You could also type into your browser **[http://123.456.789.0](http://123.456.789.0)** and your router would forward that http request to 192.168.1.123 and it would be served by your web server (assuming you have one running).

The DNS part that hictio was mentioning is that if you have a domain name, such as *server.com* or whatever, you can have that point to 123.456.789.0 in the DNS server world, which would allow you to simply type **ssh [email]blue@server.com[/email]** or **[http://server.com](http://server.com)** and the DNS servers would then translate the *server.com* part to 123.456.789.0 and then it would go to your router and as before your router would forward the request to 192.168.1.123

It's really pretty simple :P Hopefully that helps clear things up rather than makes it more confusing.

Bob

---

### Post by roundhay on 2008-11-21
Your explanation was perfect can now ssh to my server over the LAN. I will try and set up for external access tomorrow.

Thanks! :grin:

---

### Post by hrod beraht on 2008-11-21
Glad you got it working.

Let me anticipate your next question: *How can I move files back and forth from my server with ssh?*

Two ways:

1) using scp (secure copy), as in:
```
scp somefile me@myserver:
```

Or use the -r (recursive) option to move whole directory.

```
scp -r somedirectory me@myserver:
```

2) mount the server using sshfs (secure shell file system):
```
sshfs me@myserver:/home/me /media/server
```

Mounting the server via sshfs then allows you to use your file manager to drag and drop. See this [[COLOR="Blue"]SSHFS overview[/COLOR]]("https://help.ubuntu.com/community/SSHFS") for more detail.

Bob

---

### Post by hictio on 2008-11-21
> **hrod beraht said:**
> Glad you got it working.

Let me anticipate your next question: *How can I move files back and forth from my server with ssh?*

Two ways:

1) using scp (secure copy), as in:
```
scp somefile me@myserver:
```

Or use the -r (recursive) option to move whole directory.

```
scp -r somedirectory me@myserver:
```

2) mount the server using sshfs (secure shell file system):
```
sshfs me@myserver:/home/me /media/server
```

Mounting the server via sshfs then allows you to use your file manager to drag and drop. See this [[COLOR="Blue"]SSHFS overview[/COLOR]]("https://help.ubuntu.com/community/SSHFS") for more detail.

Bob

Also, and if you are going to connect to your Ubuntu server from a Windows box, to copy files you have:

**With GUI**:
[WinSCP](http://winscp.net/eng/index.php)
[FileZilla](http://filezilla-project.org/)

**Without GUI**:
[pscp](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html) (From the same people that brought you PuTTY! ;) )

All of these programs are free, and in the case of Filezilla, it can also work on a Linux box as well.

---

### Post by roundhay on 2008-11-22
Yes sharing files and folders was one of my next questions but the next part I want to get working is access over the web.

I have set up a DynDNS account and have forwarded ports 22 SSH and 80 http from my router to my server

An example of my DynDNS host name is:

iam.boldlygoingnowhere.org

When I put [http://iam.boldlygoingnowhere.org](http://iam.boldlygoingnowhere.org) into my browser I get a message saying 'It Works!'
Not sure what I can achieve using the browser, possibly one to worry about later?

When I type ssh iam.boldlygoingnowhere.org into a terminal of a PC on my Lan I get a password request but when I enter the password for my server I get:

Permission denied, please try again.

Now sure why this is happening think I might need to change the /etc/hosts/ file on my server but I'm not sure?

I have also installed ddclient and have edited the ddclient.conf file as detailed in the various tutorials I have found and it seems to be OK, no errors after running sudo /etc/init.d/ddclient restart

---

### Post by roundhay on 2008-11-22
Ignore the post above, I was not putting the user name in!

using [email]username@iam.boldlygoingnowhere.org[/email] works a treat!

---

### Post by roundhay on 2008-11-26
OK I have managed to set up SSH to authenticate using keys and have turned of the password access. 

I can access my server over my LAN my my desktop PC using:

SSH username@servername 

and can access using keys from a puppy linux USB O/S plugged into my work laptop over my LAN using:

ssh [email]username@iam.boldlygoingnowhere.org[/email]

I tried to access from my office today over the web using the same ssh command but did not get any connection, I didn't even get an error message. How long does ssh take to connect over the web? I assume it would be quick in which case my ssh command must not have found the server. Will I have to work on my DNS settings?

I could access the 'It Works!' apache server page from work by typing:

[http://iam.boldlygoingnowhere.org](http://iam.boldlygoingnowhere.org)

---

### Post by hictio on 2008-11-26
From your work, I suggest a network test before.
Type, from either a Linux or Windows (from a CMD window):

```

telnet your.public.IP 22 (ENTER)

```

If nothing happens in, say, 2 minutes, you have a problem reaching the SSH port, perhaps it is not forwarded correctly -doubt full, since you can reach Apache-, or there is a firewall blocking access, on your Ubuntu Server from the IP address from your work?
Or your work has a firewall enabled that blocks outgoing SSH?
You can test the port forwarding within your LAN using the same commando from above.

---

### Post by roundhay on 2008-11-26
The telnet command seemed to work over the LAN
Trying **.*.***.***...
Connected to **.*.***.***.
Escape character is '^]'.
SSH-2.0-OpenSSH_5.1p1 Debian-3ubuntu1
Connection closed by foreign host.

I'll try this tomorrow from work and see if it works.

If it does not can I assume that port 22 SSH connects are being block?

If yes then it looks like I'll be stopping at McDonalds on the way home to try over their wifi!

---

### Post by hictio on 2008-11-26
> **roundhay said:**
> The telnet command seemed to work over the LAN
Trying **.*.***.***...
Connected to **.*.***.***.
Escape character is '^]'.
SSH-2.0-OpenSSH_5.1p1 Debian-3ubuntu1
Connection closed by foreign host.

I'll try this tomorrow from work and see if it works.

If it does not can I assume that port 22 SSH connects are being block?

If yes then it looks like I'll be stopping at McDonalds on the way home to try over their wifi!

On your LAN it has work, since you can connect to your Ubuntu Server from other boxes.
If you can, from your own LAN, try connecting to the public IP as well.
The test from the Mc Donalds seems good.
Are you sure you don't have any internal firewall on your Ubuntu server limiting connections to the network range of your LAN?

---

