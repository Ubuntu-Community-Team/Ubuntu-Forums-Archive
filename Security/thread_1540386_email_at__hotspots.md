---
title: "email at  hotspots"
date: 2010-07-27
forum: Security
---

### Post by sysone on 2010-07-27
Sometimes I have to check my email at public hotspots and am concerned about security. I use Ubuntu with all security  updates and have set my gmail to use https. 
  But I have no way to connect to my home computer (it is usually not on or used by somebody else) .   
  Is there any way to foil somebody getting into my computer and stealing the passwords? .
 What do they use to connect to my box? 
  Is there any way to see if somebody has made a connection? 
  Thanks

---

### Post by Bachstelze on 2010-07-27
I don't quite understand what you're asking.  What do you mean by "getting into my computer" and "connetc to my box"?

---

### Post by sysone on 2010-07-27
> **Bachstelze said:**
> I don't quite understand what you're asking.  What do you mean by &quot;getting into my computer&quot; and &quot;connetc to my box&quot;?

 

   Sorry Bachstelze for not using the correct terminology - I just don't know enough. 

  What i mean is the process an attacker would use to read my mail and steal passwords while I am using a laptop at a hotspot.  In order to do so he would have to use some application to see what I see on my screen or more likely the application would tell him what my user name is and what password was used.

   I do hope that you understand now.  And I also hope that there is some suggestion for protection (aside from connecting through  my home computer which I cannot do).

   Thanks

---

### Post by kevinatkins on 2010-07-27
Hello,

OK I think I appreciate what you're saying - basically, you're connecting to the net via open wireless connections at public hotspots and you're concerned about security. I am absolutely not a security expert but I think the issue here is that anything you transmit over that open wireless connection is ripe for 'eavesdropping' so you need to bear that in mind. Using HTTPS for your Gmail is a good idea. As for others breaking into your machine, well in that instance, I don't think the risks are necessarily amplified by the fact you're using a public hotspot. If you're connecting directly to *any* public network (including, say, mobile broadband, where you're not protected behind a router's NAT firewall), it's possibly a good idea to have some sort of firewalling in place (eg, UFW), but you probably need to be aware of what services are running on your machine. If no 'risky' services are running, you're probably safe enough. For example, if you've set up Windows file sharing (via Samba), I'd be inclined to firewall, but if you're running vanilla Ubuntu, its default configuration is inherently quite secure... I'd be interested in others' opinions here!

---

### Post by Bachstelze on 2010-07-27
> **sysone said:**
> 
  What i mean is the process an attacker would use to read my mail and steal passwords while I am using a laptop at a hotspot.  In order to do so he would have to use some application to see what I see on my screen or more likely the application would tell him what my user name is and what password was used.


If you're concerned that someone can read your screen over your shoulder, well, there's not much you can do about thet.  As for an "application" that would "tell him your user name and password", it is technically possible for someone to install it on your laptop, for example if you leave it unsupervized while you go get a drink or something.  Never leave your laptop unsupervized and you should be fine.

---

### Post by bodhi.zazen on 2010-07-27
> **sysone said:**
> Sometimes I have to check my email at public hotspots and am concerned about security. I use Ubuntu with all security  updates and have set my gmail to use https. 
  But I have no way to connect to my home computer (it is usually not on or used by somebody else) .   
  Is there any way to foil somebody getting into my computer and stealing the passwords? .
 What do they use to connect to my box? 
  Is there any way to see if somebody has made a connection? 
  Thanks

You should be fine as by default there are no listening services in Ubuntu.

If you wish, enable your firewall. I do on my netbook on untrusted networks.

```
sudo ufw enable
sudo default deny
```

If you wish , you can tunnel web traffic over ssh, use your home computer to connect to and tunnel over :

[Proxy Firefox through a SSH tunnel "how to" @ Calomel.org - Open Source Research and Reference]("https://calomel.org/firefox_ssh_proxy.html") 

Just be sure to secure the ssh server (use keys, disable password logins, and use a service such as denyhosts).

---

### Post by OpSecShellshock on 2010-07-27
> **sysone said:**
> Sorry Bachstelze for not using the correct terminology - I just don't know enough. 

  What i mean is the process an attacker would use to read my mail and steal passwords while I am using a laptop at a hotspot.  In order to do so he would have to use some application to see what I see on my screen or more likely the application would tell him what my user name is and what password was used.

   I do hope that you understand now.  And I also hope that there is some suggestion for protection (aside from connecting through  my home computer which I cannot do).

   Thanks

The risks on such networks vary as widely as the networks themselves do. The main thing to consider when passing potentially sensitive information over the air is that most public hotspots are going to put compatibility and ease-of-use first, which means no encryption between the computer and the access point. Someone sniffing could get it there if they wanted to.

On a public hotspot I'd be a bit more concerned about the configuration of the access point itself. Since people using it are all inside the LAN, they may be able to access the administrative page where they can take control of DNS. Another possibility is that there's a device with a DNS-changing trojan that is able to mess with the cache and affect everyone else as well. Who knows how often public connections are audited and maintained?

I don't know; even with ufw running I wouldn't do anything on the network that involves a password (at least not inside a browser). The risks aren't very likely to actually be an issue, but without knowing/being in control of the network I'd rather not deal with it unless it's for something really important.

---

### Post by CharlesA on 2010-07-27
If I use a hotspot, even if it uses encryption, I will use a ssh tunnel set up as a SOCKS proxy for all web traffic.

Works for me. :)

---

