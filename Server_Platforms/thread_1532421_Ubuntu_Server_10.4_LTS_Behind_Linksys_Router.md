---
title: "Ubuntu Server 10.4 LTS Behind Linksys Router"
date: 2010-07-16
forum: Server Platforms
---

### Post by haydenh on 2010-07-16
Hello all,

I've recently installed Ubuntu Server 10.4 LTS. All I've installed thus far is LAMP and it is working correct on my local network. However, when I try to ping [www.google.com]("http://www.google.com") from the command prompt I am not able to. I've followed the steps to setup DynDNS, again, I am able to use my DynDNS hostname locally, but I am not able to access anything outside my network.

I've enabled port forwarding on my router, setup my web server to static IP as opposed to DHCP but I am still not able to reach outside. I think it has something to do with my router settings but I am having trouble configuring it and I haven't found anything of real use on the web (everything I've found doesn't seem to work).

Does anyone know how to configure their Linksys router and Ubuntu Server 10.4 LTS properly? Help would be greatly appreciated. Thanks in advance!

If screenshots of my setup would be more helpful please let me know and I can provide those as well.

---

### Post by arrrghhh on 2010-07-16
Hrm... Router config help is kinda outside of the scope of this forum.

Can other machines on the same router connect to the internet?

However, can you just reset your router to factory defaults?  You'll have to reconfigure your wireless, but at least you can start fresh.  There should be a pin in the back that you hit labeled "Reset".

Another test would be to skip the router and have your server go straight into your internet connection (DSL/Cable modem, etc) - that way you can ensure that your Ubuntu setup is correct and it is indeed the router that is the problem (which is pretty likely).

---

### Post by haydenh on 2010-07-16
> **arrrghhh said:**
> Hrm... Router config help is kinda outside of the scope of this forum.

Can other machines on the same router connect to the internet?

However, can you just reset your router to factory defaults?  You'll have to reconfigure your wireless, but at least you can start fresh.  There should be a pin in the back that you hit labeled "Reset".

Another test would be to skip the router and have your server go straight into your internet connection (DSL/Cable modem, etc) - that way you can ensure that your Ubuntu setup is correct and it is indeed the router that is the problem (which is pretty likely).

Yes, I understand this is probably outside the scope of this forum but I figured some people might have had issues or have dealt with this issue before.

Yes, other machines on the network can connect to the internet (both hardwired and wireless).

I can switch the router to defaults but haven't done so.

I haven't tried connecting directly to my modem as of yet. I've only been messing around with it for a couple of hours and I haven't done this yet. I agree that this will probably help me determine the cause of my issue and I will do this ASAP.

Thanks for your quick reply!

---

### Post by spynappels on 2010-07-16
You appear to be talking about 2 different things.

Pinging google from the command line - Likely to be a DNS issue. Can you ping 66.102.9.147? That is one of the google IPs. If you can, you need to look at either placing the DNS server addresses in /etc/network/interfaces or in /etc/resolv.conf

Accessing the webserver from outside the LAN requires port forwarding to be set up in the router. If this is what you are trying to do, let me know and I'll give you a step by step with Linksys screenshots.

---

### Post by haydenh on 2010-07-16
> **spynappels said:**
> You appear to be talking about 2 different things.

Pinging google from the command line - Likely to be a DNS issue. Can you ping 66.102.9.147? That is one of the google IPs. If you can, you need to look at either placing the DNS server addresses in /etc/network/interfaces or in /etc/resolv.conf

Accessing the webserver from outside the LAN requires port forwarding to be set up in the router. If this is what you are trying to do, let me know and I'll give you a step by step with Linksys screenshots.


spynappels, you might be correct on the nameserver. To setup the static IP I followed these instructions: [http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/](http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/)

In the resolv.conf there were 3 lines for nameservers each of which had a different IP. I changed all those to the IP (from the ifconfig command).

---

### Post by Insane_Machine on 2010-07-16
Try to change them to OpenDNS nameservers to see if that fixes the issue.

208.67.220.220
208.67.222.222

---

### Post by arrrghhh on 2010-07-16
Yea, I kinda skipped DNS as being the issue.  That's actually much more likely the culprit.  Do what Insane_Machine suggested, those are the DNS servers I use.

Obviously if the server's IP is static, you need to also configure the DNS servers manually as they normally get pulled from DHCP.

---

### Post by haydenh on 2010-07-16
> **Insane_Machine said:**
> Try to change them to OpenDNS nameservers to see if that fixes the issue.

208.67.220.220
208.67.222.222


So, these are the nameservers in the resolv.conf file? I apologize, I am very new to Ubuntu Server and Networking. It was my understanding that to use the DynDNS I had to switch from using DHCP to setting a static IP. Is this not the case?

---

### Post by spynappels on 2010-07-16
DynDNS is something completely different, you do not need to worry about that.

Open /etc/resolv.conf for editing 

```
sudo nano /etc/resolv.conf
```

create these two lines

```
nameserver 208.67.220.220
nameserver 208.67.222.222
```

and comment out everything else

save and then restart networking

```
sudo /etc/init.d/networking restart
```

and try pinging google again.

---

### Post by spynappels on 2010-07-16
DynDNS is a method of having your public IP mapped to a URL even if it changes, i.e. you are not on a static Public IP.

This is a useful feature, and will most probably already be supported by the Linksys router you have. If you want more help on this, again, just ask.

---

### Post by Insane_Machine on 2010-07-16
> **haydenh said:**
> So, these are the nameservers in the resolv.conf file? I apologize, I am very new to Ubuntu Server and Networking. It was my understanding that to use the DynDNS I had to switch from using DHCP to setting a static IP. Is this not the case?

I'm using DynDNS on my home server with DHCP (granted it usually stays on so IP doesn't change) I use ddclient to keep the IP the ISP gives you updated. This is probably what was meant by the static IP. The local IP doesn't matter except for keeping the correct ports forwarded.

---

### Post by jman_121 on 2010-07-16
You know, I did a fresh install of Ubuntu 32-bit server. 

Everything worked, so I figured that I would set the network interface for static ip addresses and activate my second nic.

So i do the normal editing procedures. 

Then the server breaks. It can no longer see the outside world. 

No ping. No updates. 

I can still ssh into it from the LAN, or at least I could until I rebooted it. 

After reboot, I no longer get a login prompt. I'm starting to think that Ubuntu does not like my Netgear router.

This one is baffling me to death. It is a much similar problem to yours.

I will let you know what I find out when I get back home after work and play around some more. 

Jeremy

---

### Post by haydenh on 2010-07-17
> **Insane_Machine said:**
> I'm using DynDNS on my home server with DHCP (granted it usually stays on so IP doesn't change) I use ddclient to keep the IP the ISP gives you updated. This is probably what was meant by the static IP. The local IP doesn't matter except for keeping the correct ports forwarded.

Hey Insane, after resetting everything to default (my web server and router) I am able to now access websites on the outside. What would be the best way to setup my port forwarding and DynDNS? I've tried setting up DynDNS but it asks me for an IP and I think I am not putting in the correct IP.

---

### Post by jman_121 on 2010-07-18
> **haydenh said:**
> Hey Insane, after resetting everything to default (my web server and router) I am able to now access websites on the outside. What would be the best way to setup my port forwarding and DynDNS? I've tried setting up DynDNS but it asks me for an IP and I think I am not putting in the correct IP.

When you set up port forwarding in your router, 
You'll want to forward the ports you need to the address of your server on the lan (i.e. - 192.168.1.100 - this address being the ip of your server behind the router)

port 80 is a common one to set. It is used for web traffic.

On your DynDNS account, it wants the your current wan-ip address.
You can use [www.mywanip.com](www.mywanip.com) or a similar method to find it. 

The wan-ip is used as the address for DNS host (A) record. That way the name you created (i.e. - example.dyndns.org) points to your router, then getes forwarded to your server. 

You will need a method of updating your DynDNS account with a new wan-ip, if you have dynamic ip's from your ISP . DynDNS makes a client but there are others available in the repos for ubuntu. Also see [DynamicDNS]("https://help.ubuntu.com/community/DynamicDNS")

ddclient is one package

---

### Post by haydenh on 2010-07-19
Thanks for you response. I've done everything you've said, also installing the ddclient ([https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)) and I still can't get to my web server via the IP or through DynDNS. 

I am not really sure what is going on but this is getting really annoying. I will keep plugging away at it and hopefully will come across a way to get this issue resolved.

---

### Post by spynappels on 2010-07-20
There should be a DynDNS tab in the Router pages somewhere. If you enter your DynDNS account details in here, the router/modem will automatically tell DynDNS what your Public IP is every time it changes.

---

### Post by haydenh on 2010-07-20
> **spynappels said:**
> There should be a DynDNS tab in the Router pages somewhere. If you enter your DynDNS account details in here, the router/modem will automatically tell DynDNS what your Public IP is every time it changes.

I did this and last night and got it working perfectly. I powered the server down and turned it back on this morning and it's no longer working outside the network. I have ddclient and DynDns setup and have the proper ports being forwarded in my Router. Trying to access ugavii.ath.cx now gives me a timeout error. I thought the point of having ddclient installed was for it to send DynDns an updated IP (apparently, this isn't working for me).

This is so freaking annoying!

---

### Post by arrrghhh on 2010-07-20
> **haydenh said:**
> I did this and last night and got it working perfectly. I powered the server down and turned it back on this morning and it's no longer working outside the network. I have ddclient and DynDns setup and have the proper ports being forwarded in my Router. Trying to access ugavii.ath.cx now gives me a timeout error. I thought the point of having ddclient installed was for it to send DynDns an updated IP (apparently, this isn't working for me).

This is so freaking annoying!

Take a deep breath, maybe ddclient isn't setup correctly.  Can you verify that ddclient is running?  Is it in your startup scripts?

---

### Post by haydenh on 2010-07-20
> **arrrghhh said:**
> Take a deep breath, maybe ddclient isn't setup correctly.  Can you verify that ddclient is running?  Is it in your startup scripts?

On the way to work this morning I thought the same thing. I will not know the status of ddclient until I get home. Would I create something in the ddclient configuration file to start when the server restarts? Do I have to manually start it every time?

Right now I have the following configuration in ddlcient:

```
use=web, web=checkip.dyndns.com/, web-skip='IP Address' 
```Because I am behind a router should i instead use:

```
use=linksys, fw=linksys, fw-login=admin, fw-password=admin

```Would this make a difference?

I am using DHCP and have assigned my web server to always use 198.168.1.101. Only my server with the correct MAC address can use this internal IP.

---

### Post by arrrghhh on 2010-07-20
Hrm... I don't know why you wouldn't statically configure your server to always use the same IP, but it sounds like you sort it out on the router side.  To each their own, so long as the server ALWAYS has the same IP.

The configuration you have on ddclient looks correct.  You shouldn't need to change it at all.

Have you run ddclient by itself to see if it spits out any errors?

As far as ddclient starting at the server's start, if you installed it from the repo's it *should* have added that for you.  If however you installed it in any other method, it probably did not.

You can check - it should be /etc/init.d/ddclient.

---

### Post by haydenh on 2010-07-20
> **arrrghhh said:**
> Hrm... I don't know why you wouldn't statically configure your server to always use the same IP, but it sounds like you sort it out on the router side.  To each their own, so long as the server ALWAYS has the same IP.

The configuration you have on ddclient looks correct.  You shouldn't need to change it at all.

Have you run ddclient by itself to see if it spits out any errors?

As far as ddclient starting at the server's start, if you installed it from the repo's it *should* have added that for you.  If however you installed it in any other method, it probably did not.

You can check - it should be /etc/init.d/ddclient.


I would assume ddclient works properly because last night (before I physically turned the server off), it worked fine from outside the network. I think it still has something to do with my router. I will check the status of ddclient tonight when I get home. Thanks for your help.

Hmm, I am not really sure why, but it looks like the server is working now. I checked DynDNS and it's using another IP. I am able to access the IP and host from outside the network!

I must not have the configuration set properly? Maybe there is a setting that takes it a while to update the new IP?

I ran ```
sudo /etc/init.d/ddclient status
``` and got the following result:

"Status of Dynamic DNS service update utility: ddclient is running."

---

### Post by arrrghhh on 2010-07-20
Hrm... well you kinda contradict yourself.  You said it did update your IP, but then the command you ran makes it look like there is a startup script for ddclient - but it's not being used.  Perhaps you have ddclient run at an interval via a cron job?

---

### Post by haydenh on 2010-07-20
> **arrrghhh said:**
> Hrm... well you kinda contradict yourself.  You said it did update your IP, but then the command you ran makes it look like there is a startup script for ddclient - but it's not being used.  Perhaps you have ddclient run at an interval via a cron job?

Not that I know of. I installed ddclient per [these]("https://help.ubuntu.com/community/DynamicDNS") instructions.

---

### Post by arrrghhh on 2010-07-20
> **haydenh said:**
> Not that I know of. I installed ddclient per [these]("https://help.ubuntu.com/community/DynamicDNS") instructions.

It all looks good.  I'd try restarting the server...  Check to see if ddclient is running - ```
ps -A |grep ddclient
``` If it is, it was started manually.  Kill the process, and start it from the init script - or reboot the server to see if it starts on its own.

---

### Post by spynappels on 2010-07-20
You should not need to run ddclient, that is what the router DynDNS client is supposed to do. Can you ping your URL from outside the LAN? What IP does it tell you? Your public IP is very unlikely to change unless you reboot your modem/router. I have the same setup running on a Linksys ADSL modem/router for the past 5 years without any difficulties. 

Could ddclient be conflicting with the Linksys DynDNS client?

---

### Post by arrrghhh on 2010-07-20
Perhaps I wasn't understanding the OP - are you running a DynDNS client on your router?  That may be the easiest option.  If you are, there is no need for two things updating your WAN IP...

---

### Post by spynappels on 2010-07-20
> **arrrghhh said:**
> Perhaps I wasn't understanding the OP - are you running a DynDNS client on your router?  That may be the easiest option.  If you are, there is no need for two things updating your WAN IP...

Most Linksys routers have this functionality built in. Perhaps if the OP mentioned the model, we could check?

---

### Post by arrrghhh on 2010-07-20
> **spynappels said:**
> Most Linksys routers have this functionality built in. Perhaps if the OP mentioned the model, we could check?

True enough, but if he doesn't have it enabled on the router...

Either way, it probably would be easiest to setup DynDNS updating thru the router.  It's certainly possible thru linux, but the router method is by far the 'preferred' method IMHO.

---

### Post by haydenh on 2010-07-20
> **arrrghhh said:**
> True enough, but if he doesn't have it enabled on the router...

Either way, it probably would be easiest to setup DynDNS updating thru the router.  It's certainly possible thru linux, but the router method is by far the 'preferred' method IMHO.

Thanks for all the quick replies. I have ddclient, as well as DynDNS (through my router). I think they work together because when setting up ddclient it asks for my DynDNS account information. 

You are saying I don't need both because I am setting it though my router? Should I just delete one of the other? Why is using the router method preferred? I am using the WRT310N router. I also have an older Linksys router that has similar options.

---

### Post by haydenh on 2010-07-20
> **arrrghhh said:**
> It all looks good.  I'd try restarting the server...  Check to see if ddclient is running - ```
ps -A |grep ddclient
``` If it is, it was started manually.  Kill the process, and start it from the init script - or reboot the server to see if it starts on its own.

Running this command gives me the following result:

707 ? 00:00:00 ddclient

Should I stop and start ddclient via sudo /etc/init.d/ddclient stop and start?

---

### Post by arrrghhh on 2010-07-21
> **haydenh said:**
> Thanks for all the quick replies. I have ddclient, as well as DynDNS (through my router). I think they work together because when setting up ddclient it asks for my DynDNS account information. 

You are saying I don't need both because I am setting it though my router? Should I just delete one of the other? Why is using the router method preferred? I am using the WRT310N router. I also have an older Linksys router that has similar options.

You should only be sending information to DynDNS from one location.  It's redundant to have both the router AND your server sending update information to DynDNS.  I say the router is 'preferred' because it's a built-in feature of the router.  Plus, it's one less thing to worry about on the server.

> **haydenh said:**
> Running this command gives me the following result:

707 ? 00:00:00 ddclient

Should I stop and start ddclient via sudo /etc/init.d/ddclient stop and start?

So it looks like it is running.  Yes, that's how you start and stop ddclient from what is called the 'init' script.  Basically all the scripts here are what run when your machine starts.  (Well, technically they are ran from the /etc/rc.X/ folders... but those are for the different run levels).  It's a little odd how they do things with symlinks in that manner, just how it is.

All of that rambling aside, I would just setup DynDNS updates on your router and be done with it.  I would just remove ddclient from your server as well!

---

### Post by haydenh on 2010-07-22
> **arrrghhh said:**
> You should only be sending information to DynDNS from one location.  It's redundant to have both the router AND your server sending update information to DynDNS.  I say the router is 'preferred' because it's a built-in feature of the router.  Plus, it's one less thing to worry about on the server.



So it looks like it is running.  Yes, that's how you start and stop ddclient from what is called the 'init' script.  Basically all the scripts here are what run when your machine starts.  (Well, technically they are ran from the /etc/rc.X/ folders... but those are for the different run levels).  It's a little odd how they do things with symlinks in that manner, just how it is.

All of that rambling aside, I would just setup DynDNS updates on your router and be done with it.  I would just remove ddclient from your server as well!

Will try this. Thanks so much for the guidance and advice everyone!

---

