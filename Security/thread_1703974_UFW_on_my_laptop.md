---
title: "UFW on my laptop"
date: 2011-03-10
forum: Security
---

### Post by bluegem on 2011-03-10
[LEFT]Hi,

i am still learning on UFW and while my problem definition is very simple I feel I am not getting the right piece and need your help.


i have a newly purchased laptop installed with Ubuntu 10. it have all the required tools i need and i want to do this.


- Block all the incoming traffic
- Allow only web browsing from this laptop.

So I started with gufw and while everything looks fine w.r.t installation, when i enable the firewall (iptables) through gufw my web browsing stops. 

i tried various options and nothing seems to be working. Disabling the firewall (iptables) get everything working.

i just want to add a rule to allow outgoing traffic on port 80 thats it.

Can someone point me to a doc or provide their thoughts on how to do this.

Thanks,
G
[/LEFT]

---

### Post by prshah on 2011-03-10
> **bluegem said:**
> 
- Block all the incoming traffic
- Allow only web browsing from this laptop.

i just want to add a rule to allow outgoing traffic on port 80 thats it.


Browsing requires both incoming and outgoing traffic be allowed on port 80. If you do not allow incoming traffic on port 80, your browser cannot receive any data to display to you.

I would suggest that you delete your current ufw rules, and give these two commands in the terminal```
sudo ufw default deny
sudo ufw allow 80
``` to enable incoming/outgoing browsing (http) traffic and deny all the rest.

Note that this will affect access to mails (pop3/imap), downloads (ftp/torrent) and possibly updates.

---

### Post by bodhi.zazen on 2011-03-10
> **prshah said:**
> Browsing requires both incoming and outgoing traffic be allowed on port 80. If you do not allow incoming traffic on port 80, your browser cannot receive any data to display to you.

I would suggest that you delete your current ufw rules, and give these two commands in the terminal```
sudo ufw default deny
sudo ufw allow 80
``` to enable incoming/outgoing browsing (http) traffic and deny all the rest.

Note that this will affect access to mails (pop3/imap), downloads (ftp/torrent) and possibly updates.

Not exactly.

Port 80 is uses on the server, so allowing port 80 on the client will not help.

You simply need to enable ufw. Then if you wish you can configure outbound connections. You will more likely then not wish to allow traffic on ports 20, 21, 53, 80, and 443.

See also:

	[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)
	[http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)
	[http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)

For information on ports see:

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

The client uses a random high port to connect to port 80 on the server so allowing incoming connections to port 80 on the clinet will do nothing.

---

### Post by prshah on 2011-03-10
> **bodhi.zazen said:**
> The client uses a random high port to connect to port 80 on the server so allowing incoming connections to port 80 on the clinet will do nothing. What a basic mistake. Thanks for pointing that out.

---

### Post by The Cog on 2011-03-11
bodhi.zazen is probably right. 

To be honest, I don't really see any point in blocking other outbound ports, but that's your choice.

For web browsing, as a minimum you need to allow outgoing connections to ports TCP/80 (web) and UDP/53 (DNS name lookup). The others bodhi mentioned are TCP/443 (https web). TCP/20-21 is FTP file transfer.

---

### Post by nrundy on 2011-03-11
for browsing you likely will need to allow outgoing port 80, 443, and 53. You'll also probably need to allow DHCP (ports 67, and 68?) just to get on the internet.

You should BLOCK all incoming connections. If your browser initiates a connection, an incoming will be allowed in this situation. But only if your browser inititiates.

If you do what bodhi said: enable ufw, you'll have a fully operational firewall that blocks all incoming by default.

---

### Post by The Cog on 2011-03-11
> **nrundy said:**
> You'll also probably need to allow DHCP (ports 67, and 68?) just to get on the internet.
Ooh! I never thought of that.

---

### Post by cariboo on 2011-03-11
Am I being dense here, when I am browsing the internet and check which ports have an active connection, I never see port 80 listed anywhere, Firefox or Chromium are always listening on random high ports, where does port 80 come in? Please show me where outgoing port 80 is in the following listing:

```
sudo lsof -i -P -n
[sudo] password for cariboo: 
COMMAND    PID    USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
portmap    786  daemon    4u  IPv4   8093      0t0  UDP *:111 
portmap    786  daemon    5u  IPv4   8094      0t0  TCP *:111 (LISTEN)
avahi-dae  893   avahi   13r  IPv4   8374      0t0  UDP *:5353 
avahi-dae  893   avahi   14u  IPv6   8375      0t0  UDP *:5353 
avahi-dae  893   avahi   15u  IPv4   8376      0t0  UDP *:43550 
avahi-dae  893   avahi   16u  IPv6   8377      0t0  UDP *:46497 
rpc.statd  925   statd    5r  IPv4   8347      0t0  UDP *:677 
rpc.statd  925   statd    7u  IPv4   8355      0t0  UDP *:47530 
rpc.statd  925   statd    8r  IPv4   8358      0t0  TCP *:51928 (LISTEN)
cupsd     1275    root    5u  IPv6   9399      0t0  TCP [::1]:631 (LISTEN)
cupsd     1275    root    6u  IPv4   9400      0t0  TCP 127.0.0.1:631 (LISTEN)
chromium- 1721 cariboo   92u  IPv4  16176      0t0  TCP 192.168.1.215:56246->74.125.53.125:5222 (ESTABLISHED)
chromium- 1721 cariboo  103u  IPv4  51111      0t0  TCP 192.168.1.215:36566->72.14.213.138:80 (ESTABLISHED)
ssh       2063 cariboo    3r  IPv4  21365      0t0  TCP 192.168.1.215:53570->192.168.1.235:22 (ESTABLISHED)
thunderbi 4188 cariboo   52u  IPv4  30734      0t0  TCP 192.168.1.215:33040->74.125.53.16:993 (ESTABLISHED)
thunderbi 4188 cariboo   57u  IPv4  30735      0t0  TCP 192.168.1.215:33041->74.125.53.16:993 (ESTABLISHED)
thunderbi 4188 cariboo   67u  IPv4  30798      0t0  TCP 192.168.1.215:33051->74.125.53.16:993 (ESTABLISHED)
thunderbi 4188 cariboo   71u  IPv4  33258      0t0  TCP 192.168.1.215:33239->74.125.155.16:993 (ESTABLISHED)
thunderbi 4188 cariboo   76r  IPv4  47542      0t0  TCP 192.168.1.215:59664->74.125.155.16:993 (ESTABLISHED)
thunderbi 4188 cariboo   80u  IPv4  47571      0t0  TCP 192.168.1.215:59668->74.125.155.16:993 (ESTABLISHED)
thunderbi 4188 cariboo   82u  IPv4  33281      0t0  TCP 192.168.1.215:33242->74.125.155.16:993 (ESTABLISHED)
```

---

### Post by The Cog on 2011-03-11
Web servers listen on port 80. When you connect to a web server, your browser uses a random high port to make the outgoing connection to port 80 on the server. Port 80 is a "well known port" - the port number on which you would expect to find a web service. There are lots of well known port numbers and you can see lots of them named in /etc/services. There is one connection to a web server in the list you posted:
TCP 192.168.1.215:36566->72.14.213.138:80
and according to /etc/services, all those connections from thunderbird to port 993 are IMAP over SSL - encrypted mail.

Picking a random high port when making outgoing connections is the normal thing to do. Having servers listen on well known ports means that you know which port to connect to - [http://www.google.com](http://www.google.com) doesn't have to say [http://www.google.com:80](http://www.google.com:80) - the 80 is implicit because it's www. https is implicitly 443. Etc.

---

### Post by cariboo on 2011-03-11
Why should you have to unblock outgoing port 80 on your laptop/home system if Firefox/Chromium use a random high port for an outgoing connection?

You know I'm being obtuse here :)

---

### Post by The Cog on 2011-03-12
I'll play the game.

You need to unlbock outgoing **to** port 80. Unblocking outgoing **from** port 80 won't make any difference to your ablility to surf the web.

It's different when you are configuring the server. You need to unblock incoming **to** port 80 so that people can connect to the web service.

Now for the reverse direction:
In firewalls, it is normal to configure the firewall to do stateful connection tracking, which means that once it has seen (and allowed) a packet creating a new connection, it automatically starts allowing packets in the other direction for that conversation. For example, your firewall may block all incoming packets, and all outgoing packets except connecting to web servers (outgoing to port 80). Upon allowing that connection, it will note the source port (e.g. 12345) and then start allowing incoming packets from port 80 on the webserver to port 12345 locally so that you can receive the replies. This behaviour in iptables comes from permitting ESTABLISHED packets. The firewall will revoke the established connection permission if it sees the connection being closed (FIN packet), or if it doesn't see any packets at all on that connection for a long time.

For firewalls that don't do connection tracking, such as access-lists on routers, you may have to explicitly allow packets in both firections in the configuration. For example, on your web server, you might have to allow incoming packets from anywhere to port 80, but also allow outgoing packets from port 80 to anywhere.

---

### Post by bluegem on 2011-03-17
Thank You all for this. While i was doing all what you discussed here and was not doing anything different it is working now.

i never thought that Linux works like Windows and need restart, however to my surprise it worked after a restart. 

i am going to try this again to prove myself wrong, for now its working and i am happy.

-G

---

### Post by cariboo on 2011-03-17
In most cases you don't need to reboot, you can just restart the service you made changes to. In your case you could have just restarted ufw, or just reloaded the rules. The commands would look like this:

```
[LIST]
[*]sudo ufw disable
[*]sudo ufw enable
[*]sudo ufw reload
[/LIST]
```

---

