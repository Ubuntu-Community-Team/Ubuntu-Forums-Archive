---
title: "ssh sever / tunneling?"
date: 2008-08-04
forum: Server Platforms
---

### Post by jdm2 on 2008-08-04
I'm going off to college in a few weeks.  So I wanted to turn my ubuntu 7.04 desktop that I'm leaving at home into a sever.  There are a few things I want to be able to do.  First off I want to be able to retrieve/put files on it.  I also want to use it for a connection.  What I mean by a connection is that I want all my internet traffic to run through it so people can't monitor what I'm doing.  I found this article, but I don't really know if this is what I want and what I need to do.  I know that I need to install ssh, but other than that I'm kinda lost.  Any suggestion/advice/feedback would be welcome and appreciated.  Thanks
-jdm2

[http://ubuntu.wordpress.com/2006/12/08/ssh-tunnel-socks-proxy-forwarding-secure-browsing/](http://ubuntu.wordpress.com/2006/12/08/ssh-tunnel-socks-proxy-forwarding-secure-browsing/)

---

### Post by windependence on 2008-08-04
If you want, you could run a private proxy, using something like squid, and then just put your proxy IP in your browser settings at school. Since you are surfing out through your machine, that is the only IP anyone would see. Works great. 

[https://help.ubuntu.com/7.10/server/C/squid.html](https://help.ubuntu.com/7.10/server/C/squid.html)

[http://ubuntuforums.org/showthread.php?t=95527&page=13](http://ubuntuforums.org/showthread.php?t=95527&page=13)

-Tim

---

### Post by ChumleyEX on 2008-08-04
I use that method almost every day and it's handy to have. Tunneling is pretty cool stuff.

---

### Post by jdm2 on 2008-08-04
Thanks for the suggestion windependence.  I will check it out.  Also thanks for your input ChumleyEX.  If I go with your way ChumleyEX where would you start?  Thanks for the help.  I'm going to research your thought windependence and get back to you on it.  Thanks again.

---

### Post by MJN on 2008-08-05
The problem with Squid is that whilst all HTTP traffic will be going via your server it is still in the clear hence easily sniffable on the college network (particularly so on unswitched segments of dorm networks etc). It is for this reason that I ditched Squid some time ago in favour of a more secure alternative.
 
I would suggest continuing down the SOCKS tunnelling over SSH route - I use this on my laptop (a Vista machine, using Putty as the SSH client) in order to protect all my browsing whilst away in hotels and on public WiFi hotspots etc.
 
The other advantage is that when not in use there's no server-side process sat unused, and authentication is handled automatically whereas with Squid this can easily become a pig when your IP address keeps changing.
 
Mathew

---

### Post by Dr Small on 2008-08-05
MJN, I was going to mention the same thing.
Having Squid is fine if you don't mind the traffic unencrypted, but if you need to encrypt it through a tunnel all the way out, then it would be better to setup a SSH session to the server and tunnel your applications through the SOCKS proxy.

---

### Post by jdm2 on 2008-08-05
K, thanks for the help and advice.  It sounds like doing the tunnel is the best thing to do for me.  I'm using ubuntu 7.04 desktop and I have just installed ssh.  I was wondering what else I need to do to for it/more secure.  I know that I need to disable root login for it for one thing.  I have read about it a little, but not much yet.  There is something with public/private keys.  I'm going to be connecting from a college network with a macbook pro running leopard.  Thanks for the help and advice.  I really appreciate it.  

P.S.  I have my machine on a home network.  Do I need to change it to a static ip?  Thanks

---

### Post by y@w on 2008-08-05
Yeah, most likely you'll want to set it on a static IP. For the external IP I'd suggest dyndns or no-ip.

---

### Post by dannyboy79 on 2008-08-05
i use PortableApps on a 1GB thumb stick. It's got putty on it, winscp, firefox and all that. I use putty to create a secure tunnel to my ssh server at home, then tell firefox to use a SOCKSv5 proxy server and the IP is 127.0.0.1. I do this from work, so all they see is a bunch of encrypted stuff going back and forth. I can go to any website I want. They blocked tons here at work. Transferring files quickly, I use winscp. I can upload screen grabs of putty settings as well as firefox settings but there are plenty of tutorials out there on this.

---

### Post by jdm2 on 2008-08-05
Thanks for the advice.  I will look into that.  Is there anything I need to do to the sever side of it though.  I know I need to change the port and put no to root long it, but is there anything else I need to do for this to work/more secure.  I have seen some stuff on public/private keys, but I still don't fully understand it.  Let me see if I get it right.  The keys take the place of the password right?  Does the public key go on the sever?  Thanks for the help.

---

### Post by dannyboy79 on 2008-08-05
> **jdm2 said:**
> Thanks for the advice.  I will look into that.  Is there anything I need to do to the sever side of it though.  I know I need to change the port and put no to root long it, but is there anything else I need to do for this to work/more secure.  I have seen some stuff on public/private keys, but I still don't fully understand it.  Let me see if I get it right.  The keys take the place of the password right?  Does the public key go on the sever?  Thanks for the help.
i always get this confussed as well but I would think that you would have the public key on the server and private key stays with you on a usb stick with portableapps. unless you'll have you're own commputer, then you don't need portableapps. the reason I use portableapps is because all the apps work right off the usb stick without having to install anything on the machine you're sitting at. once you get your private key, you'll have to use puttygen to import the private authorized_keys2 file that you made with your ubuntu computer so that putty can then use that private key to log onto the ssh server. I used the windows version of puttygen. Here's a site for creating the public private key files and what to put where and so on.

[http://www.debuntu.org/ssh-key-based-authentication](http://www.debuntu.org/ssh-key-based-authentication)

---

### Post by y@w on 2008-08-05
Be sure to put a good password on your private key, especially if you're going to be walking around with it on a USB stick. If you lose the stick I would immediately delete the public key out of the authorized_keys file on your "server".

---

### Post by jdm2 on 2008-08-05
Thanks for the help and advice.  K, I think I understand it a little bit better.  Let me see though, the key takes the place of your password right?  Anything else on the side of the sever part?  Thanks

---

### Post by y@w on 2008-08-05
The key does not take the place of your password. It is an authentication method.. But if you don't have the key you can still use the password unless you've disabled it in your /etc/ssh/sshd_config file. I can't stress enough.. put a password on your private key and protect it. If someone gets ahold of your private key on a flash drive with no password on it, they hold the key to your system.. literally.

---

### Post by jdm2 on 2008-08-05
K, will do.  In the next day or so I'm going try and get it up and running and let you guys know.  I know I need to disable root, change ports, do the keys, and set it up with a static ip, and do port forwarding with the router.  Any other suggestoins?  Thanks

---

### Post by MJN on 2008-08-06
> **y@w said:**
> The key does not take the place of your password. It is an authentication method.. But if you don't have the key you can still use the password unless you've disabled it in your /etc/ssh/sshd_config file. 
 
If you're allowing fallback to password authentication then you may as well dump the key method as this is a classic case of security being only as strong as the weakest link. You gain nothing by moving to key-based entry and still allowing passwords.
 
Mathew

---

### Post by dannyboy79 on 2008-08-06
MJN is right, you'll want to do this in the sshd_config file.
Also, when you create the key pairs, use a passphrase (they've been referring to it as a password) but this passphrase can be a whole sentence if you want. the longer the more secure!

change this line from:

#PasswordAuthentication yes

to

PasswordAuthentication no

and also add a line that looks like this:

allowusers *put users names here that you want to be able to log in*
example:
allowusers matt

also, I would suggest installing denyhosts. this will add people's ip that are pounding away at your ssh server's door after so many unsuccessful attempts.

---

### Post by moonpup on 2008-08-06
> **MJN said:**
> The problem with Squid is that whilst all HTTP traffic will be going via your server it is still in the clear hence easily sniffable on the college network (particularly so on unswitched segments of dorm networks etc). It is for this reason that I ditched Squid some time ago in favour of a more secure alternative.


If you open up an ssh tunnel first that will port forward 3128 from the localhost to your home ssh server running squid, it will be encrypted just fine. Just make sure you configure your browswer properly in the proxy section.

In fact to make it more secure, use firefox and in the about:config section change the below line to true so that dns lookups happen on your server and not on the schools dns servers.

network.proxy.socks_remote_dns;true

Hope this helps...

oops, one more thing... look at the ssh -D flag for using socks

---

### Post by MJN on 2008-08-06
> **moonpup said:**
> If you open up an ssh tunnel first that will port forward 3128 from the localhost to your home ssh server running squid, it will be encrypted just fine. Just make sure you configure your browswer properly in the proxy section.
 
Well obviously! But if you're putting the mechanism in place to establish an SSH tunnel then what's the point of using Squid? You may as well use the native SOCKS support that the tunnel provides.
 
I appreciate that Squid can provide other benefits such as local caching however the requirement here was simply to secure (anonymise) web access from college for a single user hence caching is likely to be of little benefit.
 
Mathew

---

### Post by moonpup on 2008-08-06
I was just saying there is more than one way to accomplish the same goal. Neither of us are wrong, we are just using different methods / approaches. Note my comment of using ssh -D

and don't forget, if your dns lookups are happening on the schools dns servers, your not as secure/hidden as you think...

---

### Post by dannyboy79 on 2008-08-06
> **moonpup said:**
> In fact to make it more secure, use firefox and in the about:config section change the below line to true so that dns lookups happen on your server and not on the schools dns servers.

network.proxy.socks_remote_dns;true


I was unaware of this, are you sure that dns lookups are done through the local machines network, how? if firefox is using my home server as a proxy (through a putty tunnel) then how could it. Anyway, i made the about:config change anyway just in case. thanks

---

### Post by Dougie187 on 2008-08-06
he is right about the dns lookups. Typically with a Socks connection the dns lookups are done on the client side, and then the traffic is passed through the tunnel. But if you switch that flag then the dns lookups are done on the server and passed through the tunnel. Then all of your web traffic is encrypted.

One question I have for everyone here, I am not sure how to do this, but does anyone know of a way to tunnel synaptic or apt-get across a socks tunnel? I want to be able to install apps at work, without them complaining about it..

The Socks tunnel for firefox is really easy, there is also a plugin for firefox called "foxyproxy" and it just gives you a little thing in the bottom right where you can click and enable the use of a proxy (Tunnel to home) then you can make a simple launcher on your desktop or taskbar that launches a terminal with the ssh command built in, then just run the tunnel app, and switch the proxy, and your good to go. It is really easy to use and it works great, i use it for web traffic from work all the time.

---

### Post by dannyboy79 on 2008-08-06
> **Dougie187 said:**
> 

One question I have for everyone here, I am not sure how to do this, but does anyone know of a way to tunnel synaptic or apt-get across a socks tunnel? I want to be able to install apps at work, without them complaining about it..


not sure what you mean? you run ubuntu at work and want to install apps at work but have the traffic go through your home ubuntu server? doesn't synaptic use port 80 anyway? couldn't you just create a tunnel to your home server using an ssh client in ubuntu at work, then tunnel back into your ubuntu machine at work? I may be way off here.

---

### Post by Dougie187 on 2008-08-06
I don't know if your last idea would work, but i guess the main problem, is for synaptic, if you go into the proxy settings area, you can't specifiy a socks proxy. So i didn't know if it was possible or not.

---

### Post by ChumleyEX on 2008-08-06
I use IE at work and other places and I've never been able to get web access without squid.

---

### Post by MJN on 2008-08-06
> **dannyboy79 said:**
> I was unaware of this, are you sure that dns lookups are done through the local machines network, how? if firefox is using my home server as a proxy (through a putty tunnel) then how could it. Anyway, i made the about:config change anyway just in case. thanks

By default, Firefox only uses a proxy for the HTTP portion of the connection i.e. it only kicks in once the destination IP is known and an HTTP request is ready to be sent. One of the reasons for defaulting to this is that SOCKS4 doesn't support UDP (and hence DNS).

[quote=ChumleyEX]I use IE at work and other places and I've never been able to get web access without squid.[/quote]

Your options depend on what the company firewall will allow through - it is entirely likely yours only allows port 80/8080/443 HTTP/S traffic. Native SOCKS uses port 1080 however in these scenarios we are talking about wrapping it inside an SSH tunnel hence it uses port 22.

Mathew

---

### Post by jdm2 on 2008-08-06
Thank you for all the help and advice/thoughts.  I think I'm going with an ssh sever using the kys.  Then I will ssh/tunnel into it and do the proxy/dns stuff in firefox.  I'm going to try and get it up and running the the next week.  I will let you know how it is going.  I should be back on with a few more questions later if I'm having trouble, but hopefully it will all go good.  What I'm saying, does it make sense?  Thanks gain.
-jd

---

### Post by Dougie187 on 2008-08-06
> **MJN said:**
> By default, Firefox only uses a proxy for the HTTP portion of the connection i.e. it only kicks in once the destination IP is known and an HTTP request is ready to be sent. One of the reasons for defaulting to this is that SOCKS4 doesn't support UDP (and hence DNS).



Your options depend on what the company firewall will allow through - it is entirely likely yours only allows port 80/8080/443 HTTP/S traffic. Native SOCKS uses port 1080 however in these scenarios we are talking about wrapping it inside an SSH tunnel hence it uses port 22.

Mathew

Also, as far as i know IE doesn't support socks. So using the SSH forwarding wouldn't work if you wanted to use IE.

---

### Post by jdm2 on 2008-08-06
Thanks for that info, but my client laptop is a mac.  So I will be using firefox.  Thanks again.

---

### Post by skunkbad on 2008-08-07
I use a tunnel to connect to my phpmyadmin. I enter:

ssh -N -p 2222 -c 3des [email]skunkbad@mydomain.com[/email] -L 1234/localhost/80

...Enter password...

I then head over to Firefox's connection settings, and enter localhost:1234 into the manual proxy.

I then access phpmyadmin through firefox, and it works fine.

...Ctrl-C to kill the connection...

Can this be easily modified to do what the OP wanted?

I've done it with Putty too. I find GUI more confusing.

---

### Post by MJN on 2008-08-07
> **Dougie187 said:**
> Also, as far as i know IE doesn't support socks.

It does - under Internet Connections > LAN Settings > Advanced (same place as you'd configure an HTTP proxy)

Mathew

---

### Post by Dougie187 on 2008-08-07
Hmm.. I don't use IE too much, but maybe at work they removed that option. For some reason I don't have the option to select SOCKS at work on my computer, at least in IE. I just use my laptop anyways.

---

### Post by ChumleyEX on 2008-08-07
Me neither. 


 I still suggest squid for those times that your stuck without firefox, but thats me, I'm just getting used to ubuntu.

---

### Post by jimv on 2008-08-07
> **Dougie187 said:**
> Hmm.. I don't use IE too much, but maybe at work they removed that option. For some reason I don't have the option to select SOCKS at work on my computer, at least in IE. I just use my laptop anyways.

If you're using Windows, you can use a program called Proxifier.  What you do is use Putty to create a ssh tunnel, and then open Proxifier and set it to use the ssh tunnel as a socks5 proxy.  Any program that you use once Proxifier is running will automatically get all its network traffic sent through the tunnel.

[http://www.proxifier.com/](http://www.proxifier.com/)

---

### Post by Dougie187 on 2008-08-08
Sounds like its similar to tsocks for ubuntu.

[http://tsocks.sourceforge.net/](http://tsocks.sourceforge.net/)

---

### Post by vivgrn on 2008-10-17
Hi
I am a student of a university where we have an http proxy server that requires authentication.
I was trying to use the following command :

> ssh -ND 1080 username@server_address

and then in firefox preferences i am using the proxy to be 127.0.0.1:1080

I am not able to access any of the websites.
It does not show connection time out as well.

waiting for a reply
thanks

---

