---
title: "Noobie needs help with server security for remote access"
date: 2009-01-07
forum: Server Platforms
---

### Post by L14UX_1NS1D3 on 2009-01-07
Hello all. 
Recently I setup a ubuntu 8.10 server on an old 700mhz intel III desktop computer with ftp, samba, torrentflux, webmin and of course ssh. So far it's been working like a dream and since I have it sitting in the base I Hardly even know it's there. My intention with setting up a server is making it remotely accessibly from anywhere but, once I setup the server I wasn't sure how secure it might be. I'm sorta a noob when it comes to networking so I wouldn't know what processes to stop or ports. My goal would be to have the server remotely accessibly so I could ssh into the box, check torrents, access the ftp and upload files. I would even want to be able to wakeup the computer via lan from a remote location. for now I can do a WOL though the home network.The setup for the connections at home are as follows: internet via DSL/cable modem running dhcp. The cable modem is connected to a four port wireless router with hidden essid and WEP 64bit wep encrytion. I read some tutorials on how to secure a linux box but I'm not exactly sure how to firewall my box properly to allow the bittorrent protocol.
 I've also been learning about pentesting so I know that everything can be hacked to some to some extent if I'm not careful. I'm going to get a free domain name from dynDNS and create a static ip for the server. I'll tryout different configurations. Any help is appreciated. Also I would need any tips on setting up the server to have a temporary password. So, for example I could upload a file to the server, email a friend with the username/password with the web address and after that session is closed the password will automatically expire. Is that possible?

---

### Post by scorp123 on 2009-01-07
I'd use "denyhosts" and I'd reconfigure it so that it mercilessly blocks any remote access attempts after e.g. 2 incorrect passwords ... rather be safe than sorry.

Please read here (the lower parts about "denyhosts" ... ignore the rest about "root"!):

[http://ubuntuforums.org/showpost.php?p=6505892&postcount=4](http://ubuntuforums.org/showpost.php?p=6505892&postcount=4)

---

### Post by scorp123 on 2009-01-07
> **L14UX_1NS1D3 said:**
> I could upload a file to the server, email a friend with the username/password with the web address and after that session is closed the password will automatically expire. Is that possible? You mean one-time passwords? Read here ... :
[http://www.cl.cam.ac.uk/~mgk25/otpw.html](http://www.cl.cam.ac.uk/~mgk25/otpw.html)

... maybe this will give you some ideas about the direction you could take.

EDIT:

German magazine "Heise" posted a nice tutorial in English:
[http://www.heise-online.co.uk/security/One-time-passwords-for-home-users--/features/88570](http://www.heise-online.co.uk/security/One-time-passwords-for-home-users--/features/88570)

The idea here is that you'd configure the "one-time" mechanism and then give your friends one and one password only. After they have used the one password you gave them they can't login again unless you give them their next one-time password ....

I'd guess this is pretty much what you want?

---

### Post by HermanAB on 2009-01-07
For secure remote access, install OpenSSH-Server and forward port 22 TCP in your firewall to the server.  A server without SSH is like a car without a steering wheel.

Cheers,

Herman

---

### Post by scorp123 on 2009-01-07
> **HermanAB said:**
> For secure remote access, install OpenSSH-Server ...  He already wrote that in the first sentence ... 
[INDENT]"Recently I setup a ubuntu 8.10 server on an old 700mhz intel III desktop computer with ftp, samba, torrentflux, webmin and of course [COLOR="Red"]ssh[/COLOR]."[/INDENT]

You didn't really read what OP wrote, right? :D

---

### Post by cryogen on 2009-01-08
Well, what you do depends heavily on how you're planning on connecting and who you're allowing.  But no matter how you're connecting, the first thing I'd do is lock down everything *very* hard (denyhosts, key based ssh authentication, default deny on the firewall, using ossec, etc., etc.).

If you're the only one connecting, such as via ssh, as an *extra* layer I'd strongly suggest closing the ssh port too and using [fwknop]("http://www.cipherdyne.org/fwknop/") to open the port dynamically only when the proper cryptographically signed packet is received.  (There are non-ubuntized packages in debian unstable, and alien works on the rpm file from the developer.)

If you're planning on doing things like uploading files remotely, I would strongly suggest using something like openvpn.  You can bind most daemons to specific IP addresses, so you can force them to listen only on the secure channel.  But this only works if you're somewhat in control of the clients.

If you're allowing anyone in the world to connect, get to know ossec and as scorp123 posted, one time passwords.

FYI, if you do try openvpn, make sure you use:
```

dev tap
tls-auth /path/to/keys/ta.key 0

```
in the server config.  Samba needs an ethernet type interface to bind to (the tap device), and the tls-auth keeps the vpn server completely silent until the client has sent the proper information.

---

### Post by windependence on 2009-01-08
You guys are really really anal about this stuff. As Hermann suggested, ssh is fine is properly configured and you can do all kinds of stuff with it, tunnel things through it like vnc, etc. You could also use NX which uses an ssh tunnel by default. 

Really, as a consultant I have been doing this for years in real live environments and have never been broken into. I don't use denyhosts. I guess if you don't want to SEE all the attempts and it makes you nervous then it's good but most of the crackers out there will just use another IP in their endless Chinese or Romanian IP block or they will spoof their IP so that you now are blocking legitimate traffic. Do you really want to do that on your web server?

-Tim

---

### Post by scorp123 on 2009-01-08
> **windependence said:**
> You guys are really really anal about this stuff ... I'd rather be "really really anal" than sorry :D

> **windependence said:**
>  I don't use denyhosts.  You should. Honestly: it's very useful.

> **windependence said:**
>  I guess if you don't want to SEE all the attempts and it makes you nervous then it's good  I don't care about SEEing their attempts. What really bothers me is the sheer mass of automated attacks originating from certain network blocks. One weak key, a stupid password somewhere somehow ... naaah, thanks but no thanks. Why worry? So I use "denyhosts" and/or "fail2ban", and voila, less things to worry about.

> **windependence said:**
>  but most of the crackers out there will just use another IP in their endless Chinese or Romanian IP block  I don't conduct any business with those countries so I don't really care one little bit about blocking their IP ranges. :D

---

### Post by L14UX_1NS1D3 on 2009-01-08
Wow, this makes my head spin just just thinking about it! This is so helpful, getting advice from the pros! So after all these good suggestions I'm going with denyhosts and I'll try my hand at configuring fwknop. I'm also going to create a scripts that automates the process of setting strong passwords with pwgen. In conjunction with this cron I'll have a script generate a new password, apply it and then have the new password sent to my email. Thank you all l33t replies!

---

### Post by cryogen on 2009-01-08
> **windependence said:**
> You guys are really really anal about this stuff.

I guess it depends on the network.  In the network I manage we have to allow windows clients to connect to the internal network.  I consider windows in any form to be a big gaping security hole with flashing neon signs saying "Hack me! Please!"  Unfortunately I can't throw them out the third story window (employers tend to not like that sort of thing).  So, instead it was deemed better to lock everything down as hard as possible so just in case we do get compromised the security measures will minimize damage.

That's just my two cents (unadjusted for inflation).

---

### Post by cryogen on 2009-01-08
One handy tool I forgot: have a look at bastille.  It helps automate a lot of common security tasks such as finding suid programs.  To use it run InteractiveBastille as root at the terminal.

---

### Post by scorp123 on 2009-01-08
> **cryogen said:**
> I consider windows in any form to be a big gaping security hole with flashing neon signs saying "Hack me! Please!"  Unfortunately I can't throw them out the third story window (employers tend to not like that sort of thing).  So, instead it was deemed better to lock everything down as hard as possible so just in case we do get compromised the security measures will minimize damage. +1 !!  Perfectly worded! :)

---

### Post by scorp123 on 2009-01-08
... double-post ... :)

---

### Post by windependence on 2009-01-08
> **scorp123 said:**
> I'd rather be "really really anal" than sorry :D

 I don't conduct any business with those countries so I don't really care one little bit about blocking their IP ranges. :D

You're missing the point here, really. If they don't use their own IP block, they spoof perfectly good IP's here in the states shich you just banned. It's just useless to try to block all those failed attempts, it takes lots of CPU cycles, and that traffic should be stopped at the firewall which should NOT be your production box. Mine are behind several layers of security including a wonderful pfsense box. I know it makes people feel good not to see the failed attempts but think about  this - they are STILL there, you just don't see them. 

The biggest site I run gets 13,000 page views a day and over 5 million hits per month. I see the failed attempts in the logs every day, but I don't get excited. Those attempts are at my firewall box, and they are just that - attempts, not successes. Not once in over four years. I could be even more anal about it if I installed intrusion detection at the firewall level, but I don't feel it necessary.

Think about this. If you run all your protection on your production box, an attacker could overwhelm your CPU just by sending millions of packets from different zombies all over the world. If those packets are dropped at the firewall, that will never happen. They don't have to get in to bring you down, they can simply flood your protection and bring your box to its knees. I don't run ANY firewall on my prod boxes. They sit behind multiple layers of protection and I don't use "password" for my passwords. :D

Something to think about.

-Tim

---

### Post by HermanAB on 2009-01-08
Note that it is easy to stop all DOS and brute force attacks with a single iptables rate limiting rule:

# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit
-burst 5 -j ACCEPT

Cheers,

Herman

---

### Post by scorp123 on 2009-01-08
> **windependence said:**
> they spoof perfectly good IP's here in the states shich you just banned. Only few hackers are able to do that. 99% of the other attackers are hacker-wannabe's, script kiddies and 1000's of owned zombie PC's that run automated attackes. So 99% of all attacks will likely be non-spoofed.

Besides that in the case of "denyhosts" only SSH attempts are blocked, other protocols would still be possible. Programs such as "fail2ban" (and some others) generate firewall rules though and they might shut out a network range completely for all protocols. Depends on what one wants.

But "denyhosts" definitely isn't such a big problem as you make it to be. ;)

> **windependence said:**
>   It's just useless to try to block all those failed attempts, it takes lots of CPU cycles, Nonsense. In the case of "denyhosts" a "hosts.deny" is automatically written and if any of the entries matches, the SSH connection is cut. And it definitely takes less CPU cycles than to answer each SSH connection attempt. That stuff is going to wear your server down: the sheer flood of connections and connection attempts that it all of a sudden might be exposed to. A simple check if a certain IP address or range matches /etc/deny.hosts is easy-peasy compared to that.

> **windependence said:**
>  and that traffic should be stopped at the firewall which should NOT be your production box.  I agree to that. But see OP's posting again: neither does he appear to be a professional who'd know such things, and neither can he predict where the IP traffic of his buddies will originate from. In a professional scenario where you have e.g. certain customers and certain partners which absolutely must be able to login to your box ... yes: you'd use a separate firewall that lets their connections in but drops the rest. But in OP's case with buddies connecting from all over the planet e.g. for the purpose of networked gaming ...? You can't do that here, unless you use e.g. "fail2ban" and lockout those who tried funny stuff with the SSH login.

> **windependence said:**
>  Think about this. If you run all your protection on your production box, an attacker could overwhelm your CPU just by sending millions of packets from different zombies all over the world.  I fully agree to that. But see my comment further above. We're talking about OP here ... not about what you and me would do if we were given such tasks on our jobs. ;)

.
.
.
.

---

### Post by scorp123 on 2009-01-08
> **HermanAB said:**
> Note that it is easy to stop all DOS and brute force attacks with a single iptables rate limiting rule:

# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit
-burst 5 -j ACCEPT Yeap. Good idea too.

---

### Post by HighCommander540 on 2009-01-09
> **windependence said:**
> You guys are really really anal about this stuff. As Hermann suggested, ssh is fine is properly configured and you can do all kinds of stuff with it, tunnel things through it like vnc, etc. You could also use NX which uses an ssh tunnel by default. 

Really, as a consultant I have been doing this for years in real live environments and have never been broken into. I don't use denyhosts. I guess if you don't want to SEE all the attempts and it makes you nervous then it's good but most of the crackers out there will just use another IP in their endless Chinese or Romanian IP block or they will spoof their IP so that you now are blocking legitimate traffic. Do you really want to do that on your web server?

-Tim

Actually, what Tim is saying here is right. There is no need to be that anal especially behind a router. The whole point of the matter is. That since he is behind a router, nothing but the ports that he forwards can even be attacked at all.

So as long as you only open up your SSH ports and maybe an SFTP port, which uses SSh encryption to protect your passwords you are going to be fine. Also, SSH uses the same encryption on your passwords so you are totally find as long as you don't forward all of you inbound ports to the server.

All the other stuff is just gong to take RAM and processing power away, no mind you not much but still some.

---

### Post by BlakeM on 2009-01-09
I'd just like to say I worship everyone in this thread. Please tell me you all went to university to study System Building or something like that. I mean, I like to think I'm good at computers, but you guys are on a whole different level.

My goal for this month is to learn what your posts actually mean :|.

---

### Post by Light821 on 2009-01-09
[http://www.kolotibablo.com/?ref=422881](http://www.kolotibablo.com/?ref=422881) good money be sure !

---

### Post by flatline on 2009-01-09
Denyhosts doesn't seem to be too popular in this thread, but for the sake of simplicity I am trying to get it running on my home server.  The only connections I forward to this box are bittorrent and SSH.  I am running 8.04 server x64 and installed denyhosts from the repositories.  however, it doesn't look like any of the config files (sample or otherwise) are installed when using apt-get.  As I am SSH'ed into the box currently, from work, I would prefer not to have to nano each line in by hand.  Are there any updated guides to configuring/using denyhosts from the repos?

I'm not sure if the daemon is running, if I just type 'denyhosts' I get:
```

me@myserver:/usr/share/denyhosts$ denyhosts
DenyHosts could not obtain lock (pid: 16416)
[Errno 17] File exists: '/var/run/denyhosts.pid'
```

Thanks.

---

