---
title: "[SOLVED] Server + Internet = no success. Kill me."
date: 2008-12-31
forum: Server Platforms
---

### Post by alienatom on 2008-12-31
Hi.

I have a test server running with Ubuntu 8.04.1

I feel pretty confident about how my local server is set up and I want to see how it pans out being able to access it over other networks (i.e. the internet).

Not too long ago, 4 or 5 months ago, I was able to remotely do this but I decided to hold off for the time being. The problem was, is that I can't really remember how I did it. 

I set up a DynDns account and had a heck of time trying to accomplish getting connected. I have no problem forwarding ports to the proper IP address of my server through my router. I have a static address setup it via the router and not my internet provider. 

Anyhow, 
Here's what happens currently.

I can access my server locally from any computer on the network- which is fine.

When I type in my DynDns IP address on the local network, it will connect to my server as well using the IP address that I get from my internet provider. Again, this all works fine on the local network.

When I am off the network however, I cannot connect to the server at all. Not with the DynDns or the IP address from my provider.

I have forwarded my server IP in the router using port 80.

I also know that this should work because I did it not too long ago which is making me want to stick my head in a microwave.

Also, I don't know if it matters but if I use DynDns to remote access my router Admin that works fine.

I think I remember it having something to do with my hosts file. Something to do with an IP address but I can't seem to figure it out. 

Any insight would be appreciated.

Thanks

---

### Post by Iowan on 2008-12-31
Something doesn't seem right if you can access the server by it's external address from an inside machine.  I suppose a **traceroute** would reveal if the connection goes past the router.

---

### Post by alienatom on 2008-12-31
Yes, I am bewildered myself and thanks for the traceroute tip.

When I use the traceroute command to see where my connection goes - it doesn't go very far. For example, my dyndns address gives me:

1 Displays LAN (i.e. gateway) address and travel time
2 External IP address and travel time

That's about it. I can ping the external address as well.
I don't even know if that is normal for a server. I get a different response if I perform a traceroute for example, to ubuntu.com

It goes long and far.. I also see my internet provider in the list of routes when I trace with the ubuntu.com example.

---

### Post by windependence on 2009-01-01
The whole idea of dynamic DNS is to use the DNS name, NOT the IP of the server. You also should not normally be able to access your server from inside your LAN using the outside IP address unless your router supports NAT reflection which most don't.

On your server you should be running a tiny program that tells your Dynamic DNS provider what your current IP is assigned to you by your ISP. If that changes, the dynamic DNS provider keeps track of it and always points your domain name at the current IP whatever that may be. 

Also, if you have remote access on on your router TURN IT OFF. It's too much of a security risk anyway and if it uses port 80, you will never be able to reach your site because your router will always respond on port 80 for remote access and your web traffic will never get through. Even worse, your web page will be pointing to your router page, and everyone will get a noce chance to hack into your router. Unless there is a really really good reason you would need remote acces to your router, I would highly suggest turning it off.

-Tim

---

### Post by alienatom on 2009-01-01
Those are some great points.

My router does have an auto update feature for using the DynDns service. I have that set up and it works which is why I didn't think of using a software based program within the server itself.

The reason I know it works is because I was able to access my server externally not too long ago but have since "fouled" things up apparently and can't seem to figure out what it happened.

You are right - being able to remotely administer the router is a HUGE security risk. I only temporarily enabled it to make sure I could at least access that from the outside. It has since been disabled. I was trying to narrow down possible areas that might be issues with my setup.

I'll have to look more into the network address translation (NAT) thing. Sounds like a good place as any to start.

I really remember entering in an IP address someplace in the server's network settings that made this work, however. The probelm is, is that I've tried everything I can think of. Host file, interfaces, ports . . . It sucks getting older.

---

### Post by Iowan on 2009-01-01
> **alienatom said:**
> It sucks getting older.Sure beats the alternative... (Sorry, off-topic).

---

### Post by sil3nt on 2009-01-01
This sounds like a problem with the way you have forwarding setup on your home router. When you configured to forward port 80 to your Router did you specify your SSH port correctly for your server ? because if you are forwarding 80 all the way to your server for SSH you wont have much luck ;)

In saying that it would seem strange that you can connect to your Dyndns hostname from your local LAN with your current setup unless you have added your Dyndns hostname to local DNS?

Be interesting to see how you go mate.

Good luck

---

### Post by alienatom on 2009-01-03
Hmmm... SSH... now that might have rung a bell in my head. That I will have to look into later this weekend. Vacation has got the best of me as I am away from my setup. 

I know, I am on vacation and here I am in the Ubuntu forums. 

My setup is that I have port 80 on the router and the listening port in apache setup as 80. I do have ssh setup so that might have something to do with it. 

Feel free to keep the insights coming till it gets figured out. All theories are welcome.

---

### Post by windependence on 2009-01-03
You have to forward your port 80 to your server or this won't work. This is the NAT feature on your router. Another way would be to put your server in the DMZ if your router has that function, but remember, there is no firewall protection that way.

-Tim

---

### Post by zenmatrix on 2009-01-03
Lots of routers have ddyns settings you have to fill out for the specific provider, I think I had issues before I set that up.

---

### Post by windependence on 2009-01-03
> **zenmatrix said:**
> Lots of routers have ddyns settings you have to fill out for the specific provider, I think I had issues before I set that up.

Yes, but you STILL have to forward port 80 back to the server or you will never be able to reach Apache. 

-Tim

---

### Post by zenmatrix on 2009-01-03
I know thats was just an extra tid bit of infomation as if its not forewarded it doesn't know where to go.

---

### Post by alienatom on 2009-01-04
> **windependence said:**
> You have to forward your port 80 to your server or this won't work. This is the NAT feature on your router. Another way would be to put your server in the DMZ if your router has that function, but remember, there is no firewall protection that way.

-Tim

I have my router forwarding port 80 to my server's internal IP address. That was the first thing I checked because, for reasons you are most likely stating, it is the first overlooked issues when not being able to connect externally. 

I also tried different ports to forward other than 80 just in case and I still had no success. 

I am trying to avoid going the DMZ route because I would like to reduce the security issues as much as possible. So I would consider that as a last resort. However, I might try that just to see if I can actually get a connection -  process of elimination.

Also, in case anyone is wondering, I have tried to connect from another network other than my own for testing. My laptop can connect to the internet but not my server.

Internet over my cell phone laptop connection - 3g or whatever they call it now-a-day. I call it slow *** dial-up.

---

### Post by alienatom on 2009-01-04
> **zenmatrix said:**
> Lots of routers have ddyns settings you have to fill out for the specific provider, I think I had issues before I set that up.

I already have that enabled in my router. I also checked my dyndns account to make sure something "funky" wasn't happening on their end. 

I still have the same issues I posted originally even when I manually enter in my DNS address.

I am still convinced its some setting within the networking of the server itself or in the apache setup.

---

### Post by eldaria on 2009-01-04
Have your ISP perhaps started blocking port 80?
I found out the hard way, after I moved and was forced to change ISP, that they block a whole bunch of ports.
For me thay had blocked port, 21, 25, 80 limiting me so that I could only access the server by SSH (port 22).
And since this is the only ISP in my Area, I'm stuck with them.
It is very simple to test.
First make sure your portforwarding on your router is set up, ssh is usually not blocked by ISP's, so make sure you forwarded this port for testing.
Next remember that you need to run your DynDns on the router not on the Server, otherwise dyndns will get your servers IP.
Check by going from your computer behind the router to a site like [www.whatismyip.com](www.whatismyip.com) this will give your external IP, check if dyndns has that same address registered.
If this is the case.
Go Externally try to connect to your server.

ssh to your server to verify you have connectivity at all.
If you do try to telnet to port 80.

**telnet yourserver 80**

If you get a time out now, your ISP is most probably blocking web traffic.


I had no other choice than to eiter move my server to co-location, or get a VPN.
I picked the last one, basically I have a VPN going to a external, and then tunnel the traffic back into the server.

---

### Post by alienatom on 2009-01-10
Thanks for everyone's help and suggestions. It appears that everything was indeed setup properly on the server end. It did end up being my ISP. The way I ended up finding out was by taking the advice of the fine folks here such as eldaria and tracing it back to my ISP.

I ended up trying a whole bunch of ports to which ones would work and wouldn't. I ended up.. please don't smack me.. installing abyss web server on my windows pc to try some additional eliminating of potential issues. I had the same problems using that windows web server. 

So, with the use of an alternate port other than 80, I can access my server from the external world successfully.

So the important lessons learned here are:

1. Make sure you have a static ip address in your interfaces file setup.

2. Make sure you forward the proper IP address from your router to your server. That is, IP address forwarded must match your router address.

3. Make sure you forward the proper port number from your router to your server. That is, the port number that you forward to your router needs to math the port that Apache listens to in the ports.conf file.

4. Make sure you ISP isn't blocking your ports for home use. If they are, try different ones. If 80 doesn't work try 8080 and so on.

5. If its free its a pain in the butt - however, a great learning experience.

---

