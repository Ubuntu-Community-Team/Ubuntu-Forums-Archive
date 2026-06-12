---
title: "Managing a bunch of remote machines?"
date: 2011-10-05
forum: Server Platforms
---

### Post by ShakataGaNai on 2011-10-05
I'm going to be dropping out a bunch of tiny ubuntu servers into the world for an environmental monitoring project. They'll be plugged into whatever internet is available in the area (Wifi, ethernet, aircard, you name it).

I want to be able to remotely manage them (software updates, diagnostics if one breaks, etc).  In testing I deployed OpenVPN but that is A) a lot of overhead for small boxes and B) requires a beefy server to handle potentially hundreds of these little boxes. 

So I'm wondering what else (besides openvpn) people are using to administrate servers on a "call home" basis rather than a "call remote" (Like your standard, SSH to said device)?

---

### Post by Dangertux on 2011-10-05
Personally I would use either a reverse ssh connection or an ssh client to client connection via an always on ssh server. You can do this by utilizing the 

```

ssh -R

```option.

If you need persistant connectivity, you can schedule a cronjob to phone home at a given interval, or you can utilize the client to client method and use nohup to keep the remote machine connected to an ssh tunneling server, than have your administrative client connect to the ssh tunnel as well, all the connections should be forwarded to the appropriate client.

That would imo be the easiest hassle free alternative to a VPN. You could something similar with netcat for even less resource usage if your needs are limited.

---

### Post by SeijiSensei on 2011-10-05
My experiences with OpenVPN are entirely opposite to yours.  I don't think it adds much overhead at all.  The installation image isn't large, the default blowfish cipher is highly efficient, and there's very little extra overhead involved in the encapsulation of the traffic within the UDP transport packets.  I still find it the simplest method for a "phone-home" scenario as you describe it.  I'm dubious that an SSH-based solution will be substantially more "lightweight."

Are all the remote devices going to be sending and receiving data over the links all the time?  If not, I don't think the server needs to be all that "beefy" either.  I'm not running nearly as many tunnels as you, but they all go through an ancient 386 box.  Watching loads via top indicates they're rarely consuming many resources on the server.  If all your remotes are sending continuous, high-bandwidth data in real-time, it might be more of an issue, but then wouldn't it be a better design for them to upload a day's worth of logs each night?

---

### Post by AskTell on 2011-10-05
well first you need a static ip or a cheap domain name that can be used to forward to your changing ip address(s)

write some a scripts to transfer your statistic and security info to your main server and placethe scripts into custom cronjobs to prevent all ur minis from connecting/uploading at the same time, how large are the files your going to be transferring? on a daily/weekly/monthly basis?

look into openNMS and ssh, they're both free

I'm a newb here so my ideas may not (most likely wont) make the cut. Many other people with greater knowledge will soon grace this thread.

---

### Post by ShakataGaNai on 2011-10-05
> **SeijiSensei said:**
> My experiences with OpenVPN are entirely opposite to yours.  I don't think it adds much overhead at all.  The installation image isn't large, the default blowfish cipher is highly efficient, and there's very little extra overhead involved in the encapsulation of the traffic within the UDP transport packets.  I still find it the simplest method for a "phone-home" scenario as you describe it.  I'm dubious that an SSH-based solution will be substantially more "lightweight."

Are all the remote devices going to be sending and receiving data over the links all the time?  If not, I don't think the server needs to be all that "beefy" either.  I'm not running nearly as many tunnels as you, but they all go through an ancient 386 box.  Watching loads via top indicates they're rarely consuming many resources on the server.  If all your remotes are sending continuous, high-bandwidth data in real-time, it might be more of an issue, but then wouldn't it be a better design for them to upload a day's worth of logs each night?

But what about handling hundreds of phone home boxes? Each connection takes up 4 IPs? A few hundred boxes would take an entire Class B?

---

### Post by ShakataGaNai on 2011-10-06
> **AskTell said:**
> well first you need a static ip or a cheap domain name that can be used to forward to your changing ip address(s)

write some a scripts to transfer your statistic and security info to your main server and placethe scripts into custom cronjobs to prevent all ur minis from connecting/uploading at the same time, how large are the files your going to be transferring? on a daily/weekly/monthly basis?

look into openNMS and ssh, they're both free

I'm a newb here so my ideas may not (most likely wont) make the cut. Many other people with greater knowledge will soon grace this thread.


That's the thing, they aren't actually transfering any data via the VPN (or similar).   That is strictly there for my management of the hardware.  The monitoring software talks to a web based API.

---

### Post by Jonathan L on 2011-10-06
> **ShakataGaNai said:**
> I'm going to be dropping out a bunch of tiny ubuntu servers into the world for an environmental monitoring project. They'll be plugged into whatever internet is available in the area (Wifi, ethernet, aircard, you name it).

I want to be able to remotely manage them (software updates, diagnostics if one breaks, etc).  In testing I deployed OpenVPN but that is A) a lot of overhead for small boxes and B) requires a beefy server to handle potentially hundreds of these little boxes. 

So I'm wondering what else (besides openvpn) people are using to administrate servers on a "call home" basis rather than a "call remote" (Like your standard, SSH to said device)?

Hi Shakata

Not sure how many of these apply to your situation, but here's some thoughts.

My first thought, for hundreds of remotes, would be just do logging, with syslog, over the network.  Make sure all the remotes say something every minute/5 minutes/whtaever.  You'll just end up with a nice log in the middle of which machine is on which IP address, that it's working, and some basic statistics.  Then you SSH to the remote if it goes silent or bad.  Very lightweight.  Could use nagios or similar to monitor, and you can get a great master display.

If you can't SSH in to the remotes for reasons of networking, then have them call out, perhaps periodically, and have the central unit "catch" the connection and keep it up.  Or have a trivial web server which tells which slaves are supposed to call in; slaves fetch [www.example.com/myunitnumber.txt]("http://www.example.com/myunitnumber.txt") which tells them if they have to call in, and where.  (Or of course scp.) Question: do any of them have pay-per-second connections such as dial-up over mobile?  If so, I've had good luck with the remote being equiped with the modem (or mobile).  I've never done it, but I've seen systems where the remote takes action when the remote unit's mobile rings.  It doesn't answer, so you save the price of the call.

Or get remote personnel to send a sick unit back by FedEx?

If you want to keep them all live, but worried about melting the middle, consider having them in batches of perhaps 64   Make sure they're resilient if the centre is down.  Then have a batch of AWS "tiny" instances, one per 64 slaves.  Switch on the apprpriate central unit when you want to speak to things.

IP addressing: don't know where the '4 addresses' comes from, but is there anything wrong in using up lots of 10.0.0.0/8 for your (virtual) network?

 After reading this through, the one which sounds like it might help easiest is  the central server telling the remotes to call in and open up the vpn.   You'd only have the ones you wanted to talk to online.

Hope some of those are interesting and applicable to you.  I'm curious about your application. 

Kind regards,
Jonathan.

---

### Post by Lars Noodén on 2011-10-06
> **Dangertux said:**
> Personally I would use either a reverse ssh connection 

+1

I've managed a small number of machines in the past that way and it works rather well.  I would say that it should scale up fairly well.  Just make a locked-down separate account for the connection and then passwordless keys to create the reverse tunnel.  Use cron to check the connection every 5 minutes or so to create a connection should it be broken.

You can find plenty of tutorials on reverse tunneling.

That way you can avoid having to mess around with VPNs, which add complexity and introduce new problems.

---

### Post by SeijiSensei on 2011-10-06
> **ShakataGaNai said:**
> But what about handling hundreds of phone home boxes? Each connection takes up 4 IPs? A few hundred boxes would take an entire Class B?

I don't know how you get to four IPs.  The server box will have just one common private IP in the VPN space.  The remotes will each have their single unique address.  (I'm assuming we're talking about [static-key]("http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html") connections, right?)  They will all have a public IP as well, of course, but that will be true no matter what method you choose.

A class B has 65K available addresses.  I doubt you'll be filling that any time soon. The 172.16.0.0/22 subnet gives you 1,022 addresses, a /21 has 2,046.

> **Lars Noodén said:**
> That way you can avoid having to mess around with VPNs, which add complexity and introduce new problems.

Lars, have you ever used OpenVPN?  It's about as simple and reliable a technology as you could want.  The config files for a static-key connection are about a dozen lines long.  I have OpenVPN tunnels running every day; they never fall over by themselves.

---

### Post by rubylaser on 2011-10-06
+1 for OpenVPN.  For a few of the businesses and churches that I help out on the side, OpenVPN is a fantastic, and very easy to manage solution.  My church uses OpenVPN to handle ~300 remote users, and this works great from a Pentium 4 box with a couple GBs of RAM.  Certainly not a beefy server by today's standards.

---

### Post by Lars Noodén on 2011-10-06
> **SeijiSensei said:**
> 
Lars, have you ever used OpenVPN?  It's about as simple and reliable a technology as you could want.  The config files for a static-key connection are about a dozen lines long.  I have OpenVPN tunnels running every day; they never fall over by themselves.

I've tested it once.  I'd still say that it's more complex than a plain reverse tunnel, especially since OpenSSH is already installed.  In other contexts, OpenVPN would be the way to go because it is a good package.

---

### Post by Dangertux on 2011-10-06
I only suggested SSH because the OP seems to want an alternative, personally I'm not entirely sure OpenVPN wouldn't work out for the purposes described. I've never had an OpenVPN with that many users however, several posters are saying that they have and it runs fine on very low end hardware. 

I'm also not sure where OP is getting at multiple ip's with either, in terms of public ip's the clients and server would only require 1 each. 

To be honest the more I think about it , the more I think SeijiSensei might be right about the resources as well, I don't really think that if there was any difference in resource usage between SSH tunnel and OpenVPN that it would be anything more than negligible.

---

### Post by ShakataGaNai on 2011-10-06
> **Jonathan L said:**
> Hi Shakata
IP addressing: don't know where the '4 addresses' comes from, but is there anything wrong in using up lots of 10.0.0.0/8 for your (virtual) network?


That bit comes from openVPN's use of a /30 per client as per [the FAQ]("http://openvpn.net/index.php/open-source/faq/77-server/273-qifconfig-poolq-option-use-a-30-subnet-4-private-ip-addresses-per-client-when-used-in-tun-mode.html").  Now that I actually google'd that up, I find there is a way to turn that off.  Honestly, I've never tried to use OpenVPN for anything more than a few dozen users, so I was worried what would happen if I started going over a /24 in IP's (which is only 64 end points at a /30 per).


> **Jonathan L said:**
>  After reading this through, the one which sounds like it might help easiest is  the central server telling the remotes to call in and open up the vpn.   You'd only have the ones you wanted to talk to online.

This is what I'm starting to lean towards also.  The text file idea was smart.

> **rubylaser said:**
> +1 for OpenVPN.  For a few of the businesses and churches that I help out on the side, OpenVPN is a fantastic, and very easy to manage solution.  My church uses OpenVPN to handle ~300 remote users, and this works great from a Pentium 4 box with a couple GBs of RAM.  Certainly not a beefy server by today's standards.

Good to know.  Never tried OpenVPN at any scale like this.

---

