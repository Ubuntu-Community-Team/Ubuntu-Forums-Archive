---
title: "Need urgent help setting up Squid proxy server"
date: 2009-11-19
forum: Server Platforms
---

### Post by werner.fletcher on 2009-11-19
Hi guys,
 
I really need your help, I'm so frustrated at the moment I've got no hair left to pull out. My goal is to set up an Ubuntu 9.10 server with Squid proxy with WPAD and DCHP. I've installed 2 NIC's. I've installed Squid, Apache2 and DHCP3. I've followed the following tutorials to no avail:
1. [http://www.howtoforge.com/squid-proxy-server-on-ubuntu-9.04-server-with-dansguardian-clamav-and-wpad-proxy-auto-detection](http://www.howtoforge.com/squid-proxy-server-on-ubuntu-9.04-server-with-dansguardian-clamav-and-wpad-proxy-auto-detection)
2. [https://help.ubuntu.com/community/dhcp3-server](https://help.ubuntu.com/community/dhcp3-server)
 
I need to set up WPAD because I don't want to enter the proxy server details on every single pc in the place, I want to make the ubuntu server the DHCP and Proxy server all in one. I did not install ClamAV and Dansguardian, only Squid, DHCP-Server, Lighttpd and Apache2.
 
I managed to get the DHCP server going, but I cannot get internet access from my client pc even though I got the correct IP, Gateway and DNS details from the DHCP server.
 
Are there any better tutorials available here? I would really like to speak to someone who got this solution working before. I'm really desperate here guys, I'm stuck in a corner! HELP!!! [-o<

---

### Post by helix2301 on 2009-11-19
[http://www.ubuntugeek.com/how-to-setup-transparent-squid-proxy-server-in-ubuntu.html](http://www.ubuntugeek.com/how-to-setup-transparent-squid-proxy-server-in-ubuntu.html)

these are a great set of directions I have not tried them for myself but the information I got from there several times was very reliable.

---

### Post by Drezard on 2009-11-19
Are you using the Squid server as the default gateway on the DHCP settings?

Has the squid server got NAT running on it for one? (Via some kind of firewall)

Has the squid server got an active internet connection?

Regards

Daniel

---

### Post by werner.fletcher on 2009-11-20
**Helix**, ty very much, I see it has a section on HTTP routing wich I will try. :)
 
**Drezard**, yes I've set the second nic's(the dchp server one) gateway to point to the first nic ip wich is connected to the internet router.  I also have disabled DHCP on my ADSL router.  The DNS in "resolv.conf" is also set to the ISP's DNS addresses.

---

### Post by koenn on 2009-11-20
here's a quickstart on dhcp : [http://users.telenet.be/mydotcom/howto/linuxsbs/intro.htm#dhcp](http://users.telenet.be/mydotcom/howto/linuxsbs/intro.htm#dhcp)
and WPAD : [http://users.telenet.be/mydotcom/library/network/pac.htm](http://users.telenet.be/mydotcom/library/network/pac.htm)

mind you that this is different from a "transparent proxy", but both can be used to the same end, i.e. having your hosts using the proxy (pseudo-)automatically.

If you need more help with this, it would be good if you elaborate on what you've done so far, what you try to achieve, and how your network is layed out. There are a couple of inconsistensies and grey areas in your post :

- why do you think you need 2 separate web servers (lighttpd and apache) ? 

- why do you need 2 NIC's - are you planning to use this machine as a router as well ? 

- how did you do this and  and what is it  supposed to accomplish ?
>  I've set the second nic's(the dchp server one) gateway to point to the first nic ip wich is connected to the internet router

- did you have any hair to begin with ? 

> I managed to get the DHCP server going, but I cannot get internet access from my client pc even though I got the correct IP, Gateway and DNS details from the DHCP server.

- does squid show any connections from those PC's  in its logs ?

---

### Post by werner.fletcher on 2009-11-23
Just to clear it up, I am not a linux expert yet, but I'm working hard on it :)
 
2 web servers? OMG sorry, I was just following that first tutorial :P Didn't even realize that!
 
What I basically want is this:
 
1) Proxy server
2) DHCP server
3) 2 NIC's in order to setup second IP range for clients
4) I want clients to work through proxy automatically without putting in proxy details manually.
 
If you think I don't need 2 NIC's and what I want can be done with only one NIC please advise me.  Basically this is going to be used at a hotel.  All client rooms have internet access via DHCP.  I want to put them through a DHCP proxy server to limit bandwidth abuse.
 
I'm going to start from scratch now, I'm going to reload the server and work from there. Thanks for all the replies, really appreciate it.

---

### Post by kewlrichie on 2009-11-23
How about running a transparent proxy ? Then you can use your DHCP server to hand out the proxy address as the gateway to which ever machine you want to use the proxy and they would be forced to use it no matter what. Also I am a big fan of using squid along with dansgaurdian for filtering/antivirus scanning I use it in a production environment and it works very well

---

### Post by werner.fletcher on 2009-11-23
> **kewlrichie said:**
> How about running a transparent proxy ? Then you can use your DHCP server to hand out the proxy address as the gateway to which ever machine you want to use the proxy and they would be forced to use it no matter what.
 
 
That is done by setting the proxy server IP as the "gateway" right?  I did that and it works but only if I put the proxy in manually into the browser.  The pc still says limited connectivity though...  I can't seem to get this thing to work transparrently

---

### Post by werner.fletcher on 2009-11-24
Hello any help here?

The server is working now, but I have to put in the proxy details manually in the browser.  I don't understand why, I did the port redirection, the DHCP server is giving the Squid as gateway.....what the hell?? HELP MEEEEEEEEE!!!

---

### Post by Dr Small on 2009-11-24
> **werner.fletcher said:**
> Hello any help here?

The server is working now, but I have to put in the proxy details manually in the browser.  I don't understand why, I did the port redirection, the DHCP server is giving the Squid as gateway.....what the hell?? HELP MEEEEEEEEE!!!
Here is an example of transparently routing connections, with iptables:
[http://ubuntuforums.org/showthread.php?t=1038761](http://ubuntuforums.org/showthread.php?t=1038761)

---

### Post by werner.fletcher on 2009-11-24
Thanks, but this guys uses dansguardian and some other stuff, it doesn't really solve my problem, but thanks anyway for trying to help.
 
I honestly don't know what I'm doing wrong here........... Do I **have** to set up Dansguardian on this machine??

---

### Post by werner.fletcher on 2009-11-24
I'm asking this again, because nobody is replying to my posts.  Please I really need some help.
 
I've got squid3 installed, DHCP installed and working, giving ppl all the right ip's etc, but I cannot get the proxy server to work transparently. It only works when I put it manually into the browser. I followed all the correct steps, just dont know what could be wrong here. I've got no hair left to pull out, seriously. :D 
 
Another question...... Is it imperative to install Dansguardian together with Squid or will it work without it?
 
Thank you!

---

### Post by koenn on 2009-11-24
transparent proxying requires some (re-)routing / redirection, and requires your clients (PC's) to have the correct gateway set. That(s all stuff that happens at the IP (network) level, so it would help if you draw us a sketch of what you have so far, detailling network ranges, ip addresses of the relevant hosts (server NICs, router, ...), current dhcp options (especially the value for 'default router')



here's an rough sketch of how a proxy server with 1 NIC would work

```

                     (192.168.1.2)
       PC1   PC2        proxy_
        |      |         sever
        |      |          |       
       ------------------------------------> router/firewall ----> internet
                                         192.168.1.1
 
```                                                  
 (think of ------  as a switch, with a patch cable going to your router. Note how the proxy server is simply plugged in to the switch, 1 NIC only)                                                
                                                  
 PC1, PC2  ... + proxy server have 192.168.1.1 as default gateway
 PC1, PC2, ... are configured to use proxy_server as proxy
 in this setup, they could access the internet/web directly (eg by turning the proxy off in their browser preferences), unless you make the firewall block this
 
If the browser is set to "auto-detect proxy settings", the above would also work with WPAD. 
 
 
To make the proxy "transparent", the firewall has to redirect/forward all traffic with a destination port 80/tcp towards the proxy server ( eg. 192.168.1.2:3128 ). Note that this does not say that the default gateway = address of the proxy)



If your current router can't handle the required portforwarding/redirection, you may want to use a linux box as router+firewall (with iptables), and in that case it would make sense to run the proxy server on that machine as well, so you get
something like this
```

                     
       PC1   PC2        
        |      |         
        |      |                        192.168.1.1
       ------------------------------------> Linux box ----> internet
                                             |- routing
                                             |- firewall
                                             |- port fw/redirect
                                             |- http proxy
      
```                                       
in this scenario, your default gateway is 192.168.1.1, and you use iptables to redirect 80/tcp to 3128/tcp, forcing all web traffic to the web proxy. Same principle as the 1st one, different implementation. Here, obviously, your linux box needs to NICs : one towards the LAN, 1 towards the internet.

Give it some thought, tell us what you have in mind, and take it from there.

---

### Post by koenn on 2009-11-24
you're too impatient, 
and this thread lacks the background info from your other thread
this is not going to help much.

---

### Post by cariboo on 2009-11-24
Please don't create multiple threads on the same subject. I have merged your two threads.

---

### Post by kewlrichie on 2009-11-24
Sorry I didn't get back to you faster but here's link of quick run through I posted about setting up squid/dans [http://ubuntuforums.org/showthread.php?t=1317538]("http://ubuntuforums.org/showthread.php?t=1317538")

I'm still in the middle of writing a how to for howtoforge on how to setup squid/dans with antivirus scanning  and going in alittle more into the configuring of dans etc...just been real busy at work

---

### Post by werner.fletcher on 2009-11-25
Sorry about double post, I was just getting desperate ](*,)
 
Kewlrichie, TY very much for your reply, really appreciate it! I have installed the proxy server in the meantime at my client, gave them a "how-to" on setting it up in browser for now.  I will work on this in the coming weeks, hopefully sorting it out once and for all.  I'm thinking that it might just be because I don't have DG installed.  Will get on it and get back to you with the results.  TY again, ur the man! :)

---

