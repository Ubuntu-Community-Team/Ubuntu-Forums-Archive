---
title: "Places =&gt; Connect to server"
date: 2009-12-06
forum: Server Platforms
---

### Post by Imoen on 2009-12-06
I posted this in another area and didn't get much help so maybe I can get more here.

I have been using Ubuntu for about a year and use the Places => Connect to server to connect to my hosting site that I use to run some sites from.

Recently I have gotten a friend to install Ubuntu on his computer. I have many photos and mp3's on my external hard drive which I would like to allow him to access the way I access my host site from. I am figuring that I can do it by using a ftp server setup on my computer but I am really lost on how to set that up.

I have installed vsftp with the directions [here]("http://www.wikihow.com/Set-up-an-FTP-Server-in-Ubuntu-Linux") has but I am not sure what to tell him to put for the connection settings. What would his username and password be and what is the server address? I tried just putting ftp@myipaddress but that doesn't work. I was thinking that maybe I am suppose to set up some kind of account on my computer for him to connect but I'm not sure where I do that. 

Also I want him to be able to connect to my /media/The_Garage/shared folder and all of it's subfolders with the ability to view/use the files in there and also to add new ones if he wants but not to delete ones that are there instead of him having his own file on my internal drive. 

I also would like to have my my family be able to connect to the same folder but I'm not sure how to do that. Many of them use different versions of Windows.

I see many articles that talk about how to set up VPN, Cisco, PPtP, OpenVPN, Samba, etc. but I really am lost to what those options are and what would be the best choice for me to use to meet my needs. 

Can anyone give me some help on this? I am more of a programmer then a network person so when it comes to this I am clueless.

---

### Post by Iowan on 2009-12-06
> **Imoen said:**
>  What would his username and password be and what is the server address?  That's probably the tricky part... Unless you have a static IP address from your ISP, you will need a service like [dyndns.com]("http://www.dyndns.com/") or [no-ip.com]("http://www.no-ip.com/"), then you'll need to forward the appropriate ports through your router.

---

### Post by Imoen on 2009-12-07
I believe I have a static ip, it's been the same for 3 years now.

---

### Post by Iowan on 2009-12-07
Is it a public or private IP address. ([http://en.wikipedia.org/wiki/Private_IP_address]("http://en.wikipedia.org/wiki/Private_IP_address")) A private IP address won't be directly accessible from Internet (that's where the port forwarding comes in).

---

### Post by diablo75 on 2009-12-07
If you're connecting to the Internet through a router, then that means your computers IP address is different than your Internet IP address because of Network Address Translation.  In other words, the router's "outside" IP is seperated from the internal LAN's IP network address range.  If someone tried to connect to your computer by entering the WAN (outside) IP address of the router/modem, the router would recieve the request but unless you have port forwarding configured, it will drop the packet as it doesn't know where to forward it (what PC to send it on to).  So first things first is to setup port-forwarding on your router (if you have one) to forward traffic (on a particular port number) on to your PC (which might appear to have a static IP, but you should set it manually just so you can be 100% certain it will never change, and to do this on all PCs on your LAN so that you can be confident there will never be an address conflict).  The port number depends on the protocol you intend to use; SSH, for example, is port 22 by default (and that can be modified if you need it to be different for some reason).

Next you'll want to see what kind of DDNS (Dynamic DNS redirection) your router is capable of using.  There are websites, such as [www.dyndns.com](www.dyndns.com) that you can sign up with for free and get a hostname that your friend can use to connect to your network.  The router logs into this website and tells it what your WAN IP address is.  Then all they have to do is type something like [http://johnsawesomeharddrive.net](http://johnsawesomeharddrive.net) and they'll never have to worry about checking to see if your IP address has changed; the dyndns service takes care of that for you.

Next you'll want to probably setup an account on your computer that has limited privilages so your friend is only allowed to access certain folders.  I can't really expand on that here but you can ask in other sub-forums here about the best way to go about doing that.  Once it's setup, he'll be able to setup a "Conect to server" shortcut with a target address like:  sftp://joesawesomeharddrive.net:22/home/joesfriend/share/  or whatever you want.

---

### Post by Imoen on 2009-12-10
> **Iowan said:**
> Is it a public or private IP address. ([http://en.wikipedia.org/wiki/Private_IP_address]("http://en.wikipedia.org/wiki/Private_IP_address")) A private IP address won't be directly accessible from Internet (that's where the port forwarding comes in).

I really have no idea and don't really understand that article very well.

[http://67.48.250.151/](http://67.48.250.151/) will get to my index page I made in my var/www folder and my friend can download the files I put in there. It would be better if he could just use the files directly though, his hard drive is small. I would also prefer that he could access my external drive rather then me moving files to that folder all the time, my internal drive is also much smaller then my external.

This is what I get when I do ipconfig -a in terminal

eth0      Link encap:Ethernet  HWaddr 00:13:20:2f:a3:03  
          inet addr:67.48.250.151  Bcast:255.255.255.255  Mask:255.255.248.0
          inet6 addr: fe80::213:20ff:fe2f:a303/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9137653 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5569381 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12174793 (12.1 MB)  TX bytes:330106551 (330.1 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:80377 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80377 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9693333 (9.6 MB)  TX bytes:9693333 (9.6 MB)

I have no idea if that means I have to set up something in the router, I have a [Linksys PSUS4](http://www.linksysbycisco.com/US/en/products/PSUS4), which is a PrintServer for USB with 4-Port Switch. All the computers plugged into it have different ip addresses and for p2p programs there's no port forwarding setup needed.

---

### Post by Iowan on 2009-12-10
FYI: That address looks like a public address (which I can access, BTW).

---

