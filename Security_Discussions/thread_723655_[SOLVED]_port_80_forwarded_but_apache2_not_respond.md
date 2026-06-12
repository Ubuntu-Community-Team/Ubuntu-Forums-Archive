---
title: "[SOLVED] port 80 forwarded but apache2 not responding"
date: 2008-03-13
forum: Security Discussions
---

### Post by abalone on 2008-03-13
Years ago I was playing with mod_php... thought I'd have a go again.

I don't plan to make my apache accessible from outside the LAN, but I do want to know why it isn't accessible from the internet even when I want it to. 

I can reach the apache-default page by visiting [http://localhost](http://localhost), 192.168.0.2., 127.0.0.1, but not my internet-facing IP address.

I did log in to the router, forwarded port 80 for this machine here. The "Shields Up" website also reports port 80 as open.

I haven't touched anything under /var/www or /etc/apache2 yet. 

It also doesn't run php scripts although I installed libapache2-mod-php5. That never happened before. (edit: server restart fixed *that* at least... I'm an idiot)

I just want to know what's going on... just for a change :confused:

---

### Post by Dr Small on 2008-03-13
While port 80 may be open on your router, did you point it to 192.168.0.2 ?

---

### Post by abalone on 2008-03-13
> **Dr Small said:**
> While port 80 may be open on your router, did you point it to 192.168.0.2 ?
Yes, 192.168.0.2 is designated the "server" for this port in the router config

---

### Post by Dr Small on 2008-03-13
Hmm. I must say that is rather strange.

Lemme look at it.
Outsider > Your XIP (Port 80 open) > 192.168.0.2 > Port 80 > (Check for services listening on port 80) Apache2 > /var/www


Hmm. Is port 80 open on your server? If so, have you tried restarting the router?

Dr Small

---

### Post by abalone on 2008-03-14
Yes, I've restarted the router now... no difference (apart from the new IP address)

Server is working - Apache/2.2.4 (Ubuntu) mod_python/3.3.1 Python/2.5.1 PHP/5.2.3-1ubuntu6.3 mod_perl/2.0.2 Perl/v5.8.8 Server at 192.168.0.2 Port 80

The /var/www & PHP test within it are also readable to "everyone"

But from "outside":

Unable to connect

Firefox can't establish a connection to the server at (IP addr).

    *   The site could be temporarily unavailable or too busy. Try again in a few
          moments.

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web.

---

### Post by Mobiplayer on 2008-03-14
The problem is that you cannot access your LAN using your WAN IP address if you are inside your LAN :(

When you ask for your WAN IP in firefox, you are really going to your router and it isn't doing NAT because you are IN your LAN.

Hope this helps.

---

### Post by Dr Small on 2008-03-14
That really isn't so, as I have accessed my WAN IP from within my LAN with no problems. But if you feel this could be a problem, have a friend connect to your WAN IP or install Tor and connect in from the outside.

Dr Small

---

### Post by abalone on 2008-03-14
Ah...? Ok... so if I could find somebody to check it "from the outside", they might get the webpage through that IP address, right? If there's no other problem, that is.

But... shouldn't I be able to access my own WAN IP?

I was wondering if it's something to do with my ADSL modem (Speedport), which is in fact *another* router, but with just one ethernet port - too few for my purposes. My "real"  router (Netgear), into which the PCs are plugged,  uses the Speedport as a mere ADSL modem thanks to the latter's PPPoE passthrough feature. 

**(PCs <--> Netgear router (knows login/password for ISP) <--> Speedport modem/router (only connects if told to by Netgear router) <--> ISP)**

I've been playing with the Speedport's more routerly and firewallish functions, but have configured it back to as plain as possible a modem now (no NAT, no firewall, just a bridge between the Netgear and the phone jack in the wall). 

I'm network semi-illiterate so I'm not sure I'm not doing the exact wrong things...

**Here're some of the Speedport's more relevant settings** (to even reach the Speedport's config webpage I have to connect it directly to the PC, taking the Netgear out of the whole thing... annoying)

**Internet service provider, username, password, etc.:** left blank, since the Netgear "knows" this stuff and thus uses the Speedport as a modem
**Permanent connection:** off (I'm still always online, is it because the Netgear reconnects all the time? But then my IP address would change every 45 seconds...?)
**Connect automatically:** on (probably irrelevant, yes?)
**Disconnect automatically after:** 45 seconds (goes up to 60 minutes only... *shrug* irrelevant? )

**DHCP Sever:** on (it makes my PC be 192.168.2.32 when connected directly to it - normally it's the Netgear that's connected to the Speedport's single LAN port, the Netgear has its own DHCP server of course, I don't know if this conflicts...)
**Lease time:** 4 days 
**Start/End IP:** 192.168.2.32- 192.168.2.63 

**PPPoE Pass-Through:** On (this circumvents the Speedport's firewall but enables it to be used from "behind" it as a modem)

**NAT:** Off (was On, but I can't tell if it makes a difference, there's only the Netgear router behind this one, not the LAN PCs)
**Standard Server:** Off
**IP Address:** 192.168.2.__ (not set)
**Port Forwarding rules:** None active. **Should I turn NAT back on and add a Port Forwarding rule for port 80 for the Netgear (attached to the Speedport's LAN port) - kind of like passing it along down the routers?** (Uhm)

**IP Address Gateway:** 192.168.2.1 (address of Speedport)
**Subnet Mask:** 255.255.255.0 (only last digit can be set)

Thanks for your help

_______________________________________________

Is there something I need to do to the apache config? The directive for the document root dir says "Allow from all"... there's no .htaccess... "Firefox can't establish a connection to the server at 91.17.125.168"... "telnet: Unable to connect to remote host: Connection refused"

---

### Post by abalone on 2008-03-14
(continued from previous post)

So I went back into the Speedport modem(+router)'s config 

And I made the Speedport do NAT again 

I couldn't enable port-forwarding to(from?) the Netgear (behind the Speedport) because it would have to be connected to the Speedport in order for the latter to recognise it (its MAC address)

But I made the first LAN IP given out by the Speedport the "standard server". This IP should now be the Netgear router's (in the direction of the Speedport modem/router) since it's back on the Speedport's LAN port (which is why I can post this...)

But that didn't change a thing, of course. Still exactly the same. Port 80 open at my WAN IP address, says [http://www.grc.com/x/ne.dll?rh1dkyd2](http://www.grc.com/x/ne.dll?rh1dkyd2), but I can't get to my "website" using the same IP address (not even an Apache "forbidden" page, just a browser unable-to-establish-connection type error)

---

### Post by abalone on 2008-03-14
Dr. Small ~ maybe Mobiplayer is right? 

You know those web translator toys like English to Valley Speak, English to Leetspeak, etc. ...they can show me my apache page!

And Babelish can't do it... it just goes into some strange reload loop without ever showing any part of my page (it's just the index, the "It works!" page, and a PHP test.) And it works fine with, say, cnn.com

---

### Post by Dr Small on 2008-03-14
It could also be that your ISP blocks port 80 inbound. If that is so, you would have to set your router up to forward port 8080 (or whatever) to you server on port 80.

You can send me you IP (if you don't mind) via PM and I'll test it out for you.

Dr Small

---

### Post by abalone on 2008-03-14
> **Dr Small said:**
> It could also be that your ISP blocks port 80 inbound. If that is so, you would have to set your router up to forward port 8080 (or whatever) to you server on port 80.

You can send me you IP (if you don't mind) via PM and I'll test it out for you.

Dr Small

If my ISP blocked it, how would some valley speak generator get to my page... and grc.com says it's open

I've currently ruined my configuration even for that purpose, though; if I can get at least that bit of functionality back I'll let you take a look, thanks for the offer

---

### Post by Dr Small on 2008-03-14
No problem. Just get it back to proper funtionality and I'll see if it works or not.

---

### Post by abalone on 2008-03-14
Did you take a look at the infodump on the previous page? It's a huge mess but maybe you can spot something. It's a bit much for me

---

### Post by Dr Small on 2008-03-14
I think we are complicating things far worse than what it actually is. I have setup port forwarding multiple times and it is not that hard. So let's go through the basic steps of setting up port forwarding to the internet.

First off, let's forward port 80 to 192.168.0.2 on your router.
(I am pretty sure you know how to do this, but this site here explains how to do it for each router:
[http://www.portforward.com/routers.htm](http://www.portforward.com/routers.htm)
Simply find your router and follow the instructions.)

Second off, after port 80 has been forwarded in your router, go to your server and make sure port 80 is open to receive all traffic.

Now, try to access it from within the LAN, and without (if that is possible), to see if everything has been forwarded correctly, and all ports are open.

Dr Small

---

### Post by abalone on 2008-03-14
The apache works, on port 80, and from the Internet (I just called somebody to test it). Just not from "in here". Given the sometimes-success with [http://degraeve.com/translator.php](http://degraeve.com/translator.php) it had apparently been working before, too. I'm calling it a "sometimes-success" because that doesn't work anymore now...no more pig latin. And Babelfish didn't work even once.

I've now removed the Netgear router to make the setup as simple as possible (so it's only PC <-> Speedport modem/router <-> Internet now). I've reconfigured the Speedport to connect by itself and set it up to forward port 80 for the apache-running PC (now 192.168.2.32 instead of 192.168.0.1 as per the Netgear's DHCP server).

---

### Post by Dr Small on 2008-03-14
What is your upload speed? I know that mine is very low and generally most of the time I get a connection reset from outside the LAN because the upload speed is so horrible.

---

### Post by abalone on 2008-03-14
1024 kbit/s (16000 kbit/s downstream)

Anyway... I've reconfigured both routers so that I can now access the Netgear's and Speedport's respective config pages at the same time (if I re-plug the latter into a LAN port on the former rather than its WAN port) so if this work now I'll be happy. Caught someone on AIM and she can see my apache. So... yay, I think

---

### Post by Mobiplayer on 2008-03-15
Hi!

You can't acces your own WAN IP because it's not yours, it's from your router :)

But you can access the Internet with many pc's because the routers does NAT.

:KS

---

