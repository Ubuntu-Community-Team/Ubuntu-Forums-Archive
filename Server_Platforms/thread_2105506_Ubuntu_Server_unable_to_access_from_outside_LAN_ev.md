---
title: "Ubuntu Server: unable to access from outside LAN even after forwarding the 22 port"
date: 2013-01-16
forum: Server Platforms
---

### Post by fabriciobr on 2013-01-16
Dears, I am posting yet another thread on issues to access Ubuntu Server from outside the Local Network.

I've installed a Ubuntu Server 2.10 64bits in an Oracle Virtual Machine. Both my internet modem and my router were blocking port 22, but I already forwarded it to local machine LAN IP in both devices. As I am installing the server only to run R-studio for statistical analysis, I do not need complex server aplications, Apache or any other platform (so I do not have to care with other ports such as the 80, and so on).

Within the LAN, I can access the server in any browser by using the host computer LAN-IP (in my case, 192.168.1.4). If I use the external network IP (in my case 187.x.xxx.xxx), I go directly to my modem's configuration page-system. Outside the LAN, of course I can only use this 187.x.xxx.xxx IP and it does not work at all: I only get a error page stating a load time out error.

In what regards the port 22, with the command nmap I can confirm that is not closed anymore, but filtered/forwarded. I can to pretty much any web address, including my network's 187.x.xxx.xxx IP. But I can not ssh it (or even other websites).

Could you please help have any new insight on this issue? I've been reading for many hours and trying many things, with no sucess so far. As I am quite a noob here, any advice will be very much apreciated and I thank you in advancei for it!
Evetn though, although I can access the server from any computer within  the LAN, I still can't do it from any one outside the LAN. 
I've been looking for answers and reading material for hours, but sill wasn't able to

---

### Post by darkod on 2013-01-16
When you say you are receiving load time out error from outside, it sounds like you are trying in a browser. You can't expect to open anything from the server in the internet browser unless you have port 80 forwarded and a service listening on it.

Do you plan to access the server by SSH? I assume so, because you forwarded only port 22.

In that case it depends whether you will be accessing from linux or windows machine. For windows, you can use the free Putty program which can open SSH sessions. You will just need to enter the public IP address and that's it. It will ask you for your username and password inside the session.

From linux machine from terminal, you access with:
ssh username@IP

It will ask you for the password during establishing the session.

---

### Post by The Cog on 2013-01-16
There are three requirements I can think of for this to work.

1: The port 22 must be open and listening on the server. It is not clear from your post whether this is true yet. Accessing the server from a browser proves nothing because browsers use port 80. A good test might be to try to telnet to the port with a command like this, from another computer on the local LAN:
```
telnet 192.168.1.4 22
```
You should see the SSH server announce itself when you connect, with a message like:
SSH-2.0-OpenSSH_6.0p1 Debian-3ubuntu1

2: The server must know how to reply to any clients that connect to it from the internet. This would normally involve using a default route that points to your internet router. If you can browse the internet from the server then that proves that th default route is in place and is correct. If you're not sure, then the command 
```
route -n
```
will print the routing table - check that destination 0.0.0.0 is listed and that its gateway is correct.

3: Packets from the internet clients must reach the server. This is the difficult one. The internet router must have port 22 forwarded to your server. The only way you can sensibly prove that this is working is to run a trace on the server as someone on the internet tries to connect. This command on the server will print out any SSH packets in or out on eth0:
```
sudo tcpdump -i eth0 tcp port 22
```

---

### Post by darkod on 2013-01-16
Also, even though it should work with the default VM network setting as NAT, I think involving NAT between the host and the guest OS is unnecessary complication. It might even be the problem.

Open the VM settings and in the network options set it to Bridged. But that would involve setting up the ubuntu server eth0 interface with a static IP from your LAN subnet, 192.168.1.x. Then on your internet router you will forward port 22 directly to this IP instead of the IP of the host OS.

---

### Post by alexii on 2013-01-16
+1 for darkod's suggestion- vbox nat is an unnecessary complication.

If you still have issues, maybe tell us more about your forwarding on the modem *and* router that you mentioned. Forwarding on both implies that both are NATing, which strikes me as odd if you're on a small network.

---

### Post by SeijiSensei on 2013-01-16
You might try forwarding a different port back to the server, say 2222, and see if that works.

---

### Post by haqking on 2013-01-16
I might be reading the OP question wrong here.

But isnt the server they want to SSH to in a VM ?

And they said they have forwarded it to the IP of the Host.

If they want to SSH into the VM then they need to SSH into the IP of the VM.

Bridge mode the VM give the VM a static IP on your LAN and then forward port 22 to that not to the host IP

A server should "really" have a static IP 

if you want to use NAT then read here [http://www.virtualbox.org/manual/ch06.html#network_nat](http://www.virtualbox.org/manual/ch06.html#network_nat)

To be honest I might of misread the OP though as for some reason I am not processing it

but i think post #4 is in agreement with me

---

### Post by spynappels on 2013-01-16
> **haqking said:**
> I might be reading the OP question wrong here.

But isnt the server they want to SSH to in a VM ?

And they said they have forwarded it to the IP of the Host.

If they want to SSH into the VM then they need to SSH into the IP of the VM.

Bridge mode the VM give the VM a static IP on your LAN and then forward port 22 to that not to the host IP

A server should "really" have a static IP 



This is how I read it as well...

---

### Post by fabriciobr on 2013-01-16
Thank you guys for the very fast replies!

First, 3 general comments I forgot to mention: 1) I am using VM in  Bridge mode, not NAT (although testing with NAT gives me similar issue);  2) my final aim is to have web browsers accessing my server from other  Operational Systems using the internet connection IP 187.x.xxx.xxx to access the website and 187.x.xxx.xxx:8787 to access R-Studio aplication; 3) I created a no-ip domain for testing pourposes that redirects to the actual and updated dynamic Internet IP of the Ubuntu server. It is fabricio01.no-ip.org for the website and fabricio01.no-ip.org:8787 for using R-Studio.

After following some of your suggestions as I will mention bellow, I  am able to access the server from within the LAN using both the  Local-Host IP (192.168.1.4 or 192.168.1.4:8787) and now also the Internet external IP  (187.x.xxx.xxx or 187.x.xxx.xxx:8787 or the no-ip equivalents). Yet, nothing from computers or devices outside the LAN.

Now, let me move on to some of your specific insights:

> **darkod said:**
> From linux machine from terminal, you access with:
 ssh username@IP
You are right, this procedure works. I can access trough ssh within LAN.

> Do you plan to access the server by SSH? I assume so, because you forwarded only port 22.Bingo, you got me. Not necessarily by SSH. I need web browsers from  other OS to access websites and R-Studio application host in the Ubuntu  server.

> When you say you are receiving load time out error from outside,  it  sounds like you are trying in a browser. You can't expect to open  anything from the server in the internet browser unless you have port 80  forwarded and a service listening on it.I understand that this  may be a veeery noob comment, but I think by service listening you mean  an opened (or forwarded) port, such as I tested using the:
telnet 192.168.1.4 22? In what regards port 80, I followed your suggestion and forwarded it. As I said above, now I can access the webiste in the server using both Local Host IP and Internet connection IP witha computer within the LAN. Still, not in a computer outside the LAN.

 > **The Cog said:**
> 1: The port 22 must be open and listening on the server. It is not clear  from your post whether this is true yet. Accessing the server from a  browser proves nothing because browsers use port 80. A good test might  be to try to telnet to the port with a command like this, from another  computer on the local LAN:
Ok, I followed your first test. Port 22 is now working properly.

> 2: The server must know how to reply to any clients that connect to it  from the internet. This would normally involve using a default route  that points to your internet router. If you can browse the internet from  the server then that proves that th default route is in place and is  correct. If you're not sure, then the commandI also followed this. Everything here seems to be working: 0.0.0.0 is  listed and its Gateway is the Modem IP: 192.168.1.1 (coment: my Router  IP is different, it is 192.168.1.2).

> 3: Packets from the internet clients must reach the server. This is the  difficult one. The internet router must have port 22 forwarded to your  server. The only way you can sensibly prove that this is working is to  run a trace on the server as someone on the internet tries to connect.  This command on the server will print out any SSH packets in or out on  eth0: Also followed you here and packets seem to be reaching the server.

> **darkod said:**
> Open the VM settings and in the network options set it to Bridged. But  that would involve setting up the ubuntu server eth0 interface with a  static IP from your LAN subnet, 192.168.1.x. Then on your internet  router you will forward port 22 directly to this IP instead of the IP of  the host OS.
> **haqking said:**
> Bridge mode the VM give the VM a static IP on  your LAN and then forward port 22 to that not to the host IP
 A server should "really" have a static IP
Hmm, as I only clarified in this reply, I am using a VM in Bridge mode  set with DHCP plus no-ip package as I don't have static IP in my  connection. So, my primary network interface shows iface eth0 inet dhcp. Should I do some workaround in this?

> **alexii said:**
> If you still have issues, maybe tell us more about your forwarding on  the modem *and* router that you mentioned. Forwarding on both implies  that both are NATing, which strikes me as odd if you're on a small  network.
Hmm, which info should I give here? It also sounded odd to me, but both  modem and router have the port forwarding possibilities and I set the  followin port-forwarding in both: ports 20, 21, 22, 2222, 80 and 8787 (I  need this for R-Studio application) redirected to the Local Host IP  (192.168.1.4).

> **SeijiSensei said:**
> You might try forwarding a different port back to the server, say 2222, and see if that works.
Unfortunatelly, nothing happens. =/

---------

Again, thanks a ton guys for those first insights!

---

### Post by volkswagner on 2013-01-16
From any machine inside your LAN to go to canyouseeme.org.

This will check your ports.  If canyouseeme.org says "cannot see your service" this means either your isp is blocking that port or your router is not properly forwarding to the ip address which is listening.

In order for you to get a success three things must be in place:
[LIST=1]
[*]You have a service listening on the port.
[*]Your isp is not blocking the port.
[*]Your router is properly forwarding to the ip which is listening.
[/LIST]

---

### Post by The Cog on 2013-01-16
> **fabriciobr said:**
> 
Everything here seems to be working: 0.0.0.0 is  listed and its Gateway is the Modem IP: 192.168.1.1 (coment: my Router  IP is different, it is 192.168.1.2).

This worries me. I would expect the router to be the default gateway. Can your server access the internet? Does the command ```
ping 8.8.8.8
``` get any response? It should list lots of responses, one per second.
> 
 Also followed you here and packets seem to be reaching the server.

That's good - it means that all your port forwarding is working. Do you see your server sending response packets back to the internet client as soon as it recieves a packet?

---

### Post by fabriciobr on 2013-01-17
> **volkswagner said:**
> From any machine inside your LAN to go to canyouseeme.org.This will check your ports. If canyouseeme.org says "cannot see your service" this means either your isp is blocking that port or your router is not properly forwarding to the ip address which is listening.
I'd configured a forward of port 80 to my server IP in therouter (it is a TP-Link Wr941nd). Even though, I receive different status readings: using canyouseeme.org, it seems that my port 80 is not opened when I access their website trough the computer 192.168.1.1 in my network.  If use the terminal in the 192.168.1.4 device (which is the server) and run nmap command or on the internet connection IP (187.x.xxx.xxx), it says the port 80 is opened. Also, using ShieldsUP website, it is shown that port 80 is stealth, as the others, not closed.

Additionaly, I tried using a No-IP port 80 redirecting to test and it still does not work, i.e. using the webbrowser outside the LAN to access my router IP does not work. I still do not get the "It works" default webpage. I did additional tests on port 80, please keep reading the following

> **The Cog said:**
> This worries me. I would expect the router to be the default gateway. Can your server access the internet? Does the command 
As it worried you, I reinstalled modem and router, using modem in bridge mode and puting the router in a PPoE connection as the default gateway. Now, address 0.0.0.0 has the router IP as its Default Gateway, as you were expecting.

Also, using the ping 8.8.8.8 shows me that there is proper response.
Additionnaly, now for the first time I can SSH the 187.x.xxx.xxx internet IP trough the server terminal (at least, it goes to [EMAIL="root@187.x.xxx.xxx"]root@187.x.xxx.xxx[/EMAIL], but I do not know which password to give, as my only server password seems not to work in here) o through any terminal in other LAN devices. But only with the router firewall disabled.

What I still can not do is to access the server 187.x.xxx.xxx trough a web browser outside the LAN, i.e. I do not get the "It works" default webpage of the server, only a internet usual error page.

> **The Cog said:**
> That's good - it means that all your port forwarding is working. Do you see your server sending response packets back to the internet client as soon as it recieves a packet?I also tried listening on port 80 with the command ```
sudo tcpdump -i eth0 tcp port 80
``` and I only receive packages when trying to access the server trough web browser inside the LAN. Trying this outside the LAN does not seem to get listened. Port 80 is also forwarded in the router but appears as opened using nmap, closed in canyouseeme website and stealth in the ShieldsUp website.

What is interesting is the following. If I try to navigate to 187.x.xxx.xxx in a browser outside the LAN (with a Windows 7) to see the website, it does not work. I get the internet time out error. But if I navigate to 187.x.xxx.xxx:8787, also outside the LAN (in Windows 7 as well) to use the web-base application R-Studio I had installed in my Ubuntu server, it does work.

---

### Post by darkod on 2013-01-17
You can't try root@187.x.x.x. The root username is disabled by default in ubuntu and you need to use your username. For system command you put sudo in front of the command for root permissions.

So, try with your username something like username@187.x.x.x.

As for port 80, if canyouseeme says it's not open, that it seems it's not. nmap might be checking it locally not from the outside, because you are trying from within your LAN. Try nmap from the outside and see what it says. When I say outside I don't mean just using the public IP, I mean from a computer outside your home/LAN.

---

### Post by The Cog on 2013-01-18
So if I understand this right, you can connect to the server from the internet on ports 22 and 8787, but not port 80. But all 3 have been configured for port forwarding in the router. At this point, I am beginning to think that your ISP might be blocking port 80. Some ISPs do that, although I don't see how they can get away with doing it and still claim to provide internet connectivity - seems like fraud to me.

---

