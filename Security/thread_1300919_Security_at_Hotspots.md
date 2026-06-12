---
title: "Security at Hotspots"
date: 2009-10-25
forum: Security
---

### Post by Alxl on 2009-10-25
At times I have to use my Eee machine with Ubuntu 9.04 at hotspots and was wandering about security. 
Any recommendations for a VPN ? Should I subscribe to HotSpotVPN or something similar?
What do you think about the  Boingo Wireless network?
Thanks

---

### Post by movieman on 2009-10-25
A random wireless connection can completely fake the whole of DNS, or simply redirect IP addresses to its own fake servers; even if it's not a malicious connection I believe that any machine connected to it can see all traffic to and from every other machine. So there's essentially no security there.
 
To be secure, you need to use something like SSL (as your web browser can verify the identity of the remote site certificate and reject attempts to take it) or a VPN with some kind of authentication (e.g. public key certificate or shared secret key).

---

### Post by update_manager on 2009-10-25
> **Alxl said:**
> At times I have to use my Eee machine with Ubuntu 9.04 at hotspots and was wandering about security. 
Any recommendations for a VPN ? Should I subscribe to HotSpotVPN or something similar?
What do you think about the  Boingo Wireless network?
Thanks

What makes hotspots different than regular Internet connections is that someone within wireless range can 1.) view your traffic 2.) directly attack your computer.

The solution to both is to assume that the attacker has complete access to all of your traffic and network access to your computer. Don't do anything in plain text that you wouldn't want an attacker to get access to. Keep ubuntu updated, enable ufw, actually check SSL certificates.

---

### Post by witeshark17 on 2009-10-25
Firefox has SSL, as does Thunderbird; good security if your pop3 provider supports SSL, and most if not all do.

---

### Post by Lars Noodén on 2009-10-26
You can set up OpenVPN on your home machine, or an ad hoc VPN using OpenSSH.

Or you can set up squid on your home machine and tunnel port 80 (and maybe other ports) to it.  

For your mail, make sure at least that you are using IMAPS.

---

### Post by Sarmacid on 2009-10-26
SSL offers very good security but you can't fully trust anything unless you do it [http://www.thoughtcrime.org/software/sslstrip/](http://www.thoughtcrime.org/software/sslstrip/) My suggestion would be to set up a ssh server and tunnel your traffic through it.

---

### Post by kevdog on 2009-10-26
If you are just using your mobile computer at the hotspots to browse, I would just set up say an ssh server at your house (this could be done through some routers with the openwrt, tomato, or ddwrt firmware installed - or - could just be done through a computer at your house (possibilities could be ubuntu with openssh or even a windows based computer with cygwin installed with openssh), -- create an ssh tunnel, and then make use of the firefox socks proxy ability to tunnel firefox through the socks proxy via the ssh tunnel.  

Yes this might sound really complicated -- but if you have any computer knowledge -- this might take 15 minutes to set up -- less if you don't have to download any programs -- and even less than a minute if you are already running an ssh server.

---

### Post by CharlesA on 2009-10-27
Basically if you SSH to your home net connection, you are using your home connection instead of browsing over wifi correct?

If that's the case, can you just set SSH to tunnel using ports 80 and 443, then set the proxy in FF or IE to 127.0.0.1?

I'm curious since I've been tempted to connect to various hot spots when I am out, but having no security = no way.

---

### Post by kevdog on 2009-10-27
If you're curious about it -- you should try it.  If you do a packet sniff (wireshark) on your own packets -- you will see they are encrypted.

---

### Post by JugglinPhil on 2009-10-27
> **update_manager said:**
> What makes hotspots different than regular Internet connections is that someone within wireless range can 1.) view your traffic 2.) directly attack your computer.

The solution to both is to assume that the attacker has complete access to all of your traffic and network access to your computer. Don't do anything in plain text that you wouldn't want an attacker to get access to. Keep ubuntu updated, enable ufw, actually check SSL certificates.
Wow that's pretty scary, good to know..

---

### Post by kevdog on 2009-10-27
Those quotes are a little bit misleading -- If you are not running any services -- how is your box on a hotspot network going to be compromised?  If no services are running and an established ssh connection is present, I'd say your security risk is just about nil.  Only if you are running services would you then want to employ a firewall or sometype of packet filtering.

---

### Post by mr-woof on 2009-10-27
I'm a bit confused about this, is a hot spot something like the wifi in a starbucks/mcdonalds? 

If I connected with a standard ubuntu build on a laptop with all updates, if someone else connected to the same wifi was using wireshark etc, surely as long as I didn't open any pop3 email accounts, passwords into web sites etc. They'd only be able to see my web browsing packets and not compromise my machine?

Or am I getting this a bit wrong?

---

### Post by EJeanmaire on 2009-10-27
> **mr-woof said:**
> I'm a bit confused about this, is a hot spot something like the wifi in a starbucks/mcdonalds? 

Yes

> **mr-woof said:**
> If I connected with a standard ubuntu build on a laptop with all updates, if someone else connected to the same wifi was using wireshark etc, surely as long as I didn't open any pop3 email accounts, passwords into web sites etc. They'd only be able to see my web browsing packets and not compromise my machine?

Or am I getting this a bit wrong?

Yes they can see your traffic, and depending on what services you run on your machine, and if you have any vulnerable (old) software installed, then yes you could also be compromised.  In fact someone could use up and coming 0day exploits (new exploits without patches from the vendor yet) to compromise your machine on this network as well.  

Your best bet on an open wifi is to reduce the services you are running, and reduce any other information about your system you are leaking making it difficult for an attacker to profile your system.  

In regards to maintaining confidentiality of your internet use, SSL is good but its limited.  You could also set up a VPN at home (with a DDWRT router), which would encrypt all traffic.

---

### Post by CharlesA on 2009-10-28
> **kevdog said:**
> If you're curious about it -- you should try it.  If you do a packet sniff (wireshark) on your own packets -- you will see they are encrypted.

Thanks for the info. I tried using wireshark after setting up an SSH SOCKS proxy, couldn't really tell anything about the packets.
I tested it by using telnet to get into the machine and all traffic was readable.

Guess that means it's working. Thanks. ;)

---

### Post by mr-woof on 2009-10-28
What services would it best to reduce?

---

### Post by Lars Noodén on 2009-10-28
Take away any you don't need.  

If you want to be picky about it, use the alternate install cd to install 'cli' system.  Then add only the packages you use.  

Of the ones that may not be obvious, I'd leave, or add if it's not there, either ntp or openntpd.

---

### Post by PoachedSalmon on 2009-10-28
So how do most of you connect to the Internet when you are away from your home network? Would using a paid subscription, say through Verizon or Boingo, provide the VPN that I would need? 

In other words, what would be the easiest way for a newbie to ensure security while net surfing out in public?


Sorry for the very elementary question, but I just ordered a Starling and will be using wireless networks to connect to the Internet for the first time. I'm reluctant to use public wi-fi networks and would like something more secure but also manageable for a newbie.

---

### Post by __p1n__ on 2009-10-28
> **EJeanmaire said:**
> Yes



Yes they can see your traffic, and depending on what services you run on your machine, and if you have any vulnerable (old) software installed, then yes you could also be compromised.  In fact someone could use up and coming 0day exploits (new exploits without patches from the vendor yet) to compromise your machine on this network as well.  

Your best bet on an open wifi is to reduce the services you are running, and reduce any other information about your system you are leaking making it difficult for an attacker to profile your system.  

In regards to maintaining confidentiality of your internet use, SSL is good but its limited.  You could also set up a VPN at home (with a DDWRT router), which would encrypt all traffic.

If you're not running your home/office wifi traffic through a VPN tunnel then you're just asking to get owned.

Wrt hotspot security you should be aware of another not-quite-so-obvious vector.  There's nothing preventing another user connected to the same AP from monitoring your traffic and spoofing html response traffic. This is a trivial mitm attack in this contet and your browser can be consequently directed anywhere.
 
Here's a link to a fun little app called airpwn that performs exactly this penetration assessment:

[http://airpwn.sourceforge.net/Airpwn.html](http://airpwn.sourceforge.net/Airpwn.html)

Note: do *not* click on the link to the defcon demo pics as they contain extremely objectionable content.

---

### Post by kevdog on 2009-10-29
PoachedSalmon

Although a VPN is an attractive option its not always necessary.

You could easily setup a VPN to your home computer LAN using DDWRT or run an OpenVPN server at home and connecting to this remotely

Additionally if just web surfing -- the poor man's VPN is to use a ssh/socks proxy to your home computer or router and connect via this gateway.

---

### Post by witeshark17 on 2009-10-29
Yeah, but these are so obvious. Wouldn't be easier and less time consuming to just use big name hot spot like at&t (based on SBC group, DSL and cell phone and land line provider) locations? I mean, how hard can that be with the use of simple SSL? Anyone? :popcorn: VPN's, pipelines and proxies are not new enough

---

### Post by styven on 2009-10-29
Are we all vulnerable, irrespective of OS?

[http://news.bbc.co.uk/1/hi/sci/tech/8332689.stm](http://news.bbc.co.uk/1/hi/sci/tech/8332689.stm)

Steve.

---

### Post by CharlesA on 2009-10-29
> **witeshark17 said:**
> Yeah, but these are so obvious. Wouldn't be easier and less time consuming to just use big name hot spot like at&t (based on SBC group, DSL and cell phone and land line provider) locations? I mean, how hard can that be with the use of simple SSL? Anyone? :popcorn: VPN's, pipelines and proxies are not new enough
You mean a T-mobile, or AT&T hotspot at something like Starbucks? That's public and they security isn't really that good since it's a public AP.

If I am connecting to something that isn't secure, I'll just SSH to my home box and run a SOCKS proxy so that it'll encrypt and send the traffic thru my home network.

---

### Post by ApEkV2 on 2009-10-29
No hotspots aren't safe, in that video it was probably a session hijack, or a man in the middle attack (are they the same?)
It's funny you posted this, cause the answer is right.....here
[http://ubuntuforums.org/showthread.php?t=1300919](http://ubuntuforums.org/showthread.php?t=1300919)

---

### Post by PoachedSalmon on 2009-10-29
> **kevdog said:**
> PoachedSalmon

Although a VPN is an attractive option its not always necessary.

You could easily setup a VPN to your home computer LAN using DDWRT or run an OpenVPN server at home and connecting to this remotely

Additionally if just web surfing -- the poor man's VPN is to use a ssh/socks proxy to your home computer or router and connect via this gateway.

    Is there a tutorial/sticky that walks you through the process? Or maybe another thread somewhere that does?

---

### Post by kevdog on 2009-10-30
Although this is applicable to ddwrt with the openvpn flash of the firmware -- this server/client config could possibly be run on any server client:

[http://blog.zenone.org/2008/01/openvpn-and-dd-wrt-on-linksys-wrt54gl.html](http://blog.zenone.org/2008/01/openvpn-and-dd-wrt-on-linksys-wrt54gl.html)

---

### Post by EJeanmaire on 2009-11-02
> **kevdog said:**
> Although this is applicable to ddwrt with the openvpn flash of the firmware -- this server/client config could possibly be run on any server client:

[http://blog.zenone.org/2008/01/openvpn-and-dd-wrt-on-linksys-wrt54gl.html](http://blog.zenone.org/2008/01/openvpn-and-dd-wrt-on-linksys-wrt54gl.html)

Assuming you are not technical enough to set up DD-WRT or you do not own a compatible DD-WRT router, your router currently might have the VPN feature built into it, its a shot in the dark, but check your router configs for the feature.  It should be a fairly easy configuration, run the VPN service on the Router, then setup your NetworkManager Applet in gnome to use VPN.

---

### Post by Alxl on 2009-11-02
> **CharlesA said:**
> You mean a T-mobile, or AT&T hotspot at something like Starbucks? That's public and they security isn't really that good since it's a public AP.

If I am connecting to something that isn't secure, I'll just SSH to my home box and run a SOCKS proxy so that it'll encrypt and send the traffic thru my home network.

  	 	 	 	 	 	  I cannot connect to my home machine - it is usually not on and besides it is shared. 



 What options do I have for trying to securely access my mail at hotspots ? 



Thanks

---

### Post by witeshark17 on 2009-11-02
The [ AT&T wifi website]("http://www.att.com/gen/press-room?pid=1782") has info. If your popmail provider supports SSL, your e-mail client (most if not all do) can be set to it in preferences or similar (Thunderbird > Edit > account settings) Don't forget to check that setting for both outgoing and incoming mail.

---

### Post by Lars Noodén on 2009-11-03
> **witeshark17 said:**
> ... your popmail provider supports SSL...

POP is quite outdated.  

IMAPS if it is available would be recommended.

---

### Post by kevdog on 2009-11-03
> **Alxl said:**
> I cannot connect to my home machine - it is usually not on and besides it is shared. 



 What options do I have for trying to securely access my mail at hotspots ? 



Thanks

This is a tough situation.  You either need a computer somewhere to act as a gateway.  This can be through a work or home computer, or you would have to purchase a commercial product.  Even a windows computer however could act as this gateway however (I believe) through the use of cygwin/ssh

---

### Post by tturrisi on 2009-11-04
FYI, when using an open wlan, only certain things are sent in clear text over http.  FTP and POP and SMTP send clear text usernames and passwords.  HTTPS doesn't.  If someone sniffs your HTTPS logins they will not see the text usernames and passwords, they will only see the encrypted names.

The real risk is if have any sort of file sharing enabled, either through Samba or Windows.  In which case, all one has to do is sniff your traffic to see the Windows netbios requests or Samba requests and then change his workgroup name to the same as yours, and then access your shares.  This is what is inherently insecure about XP Home and similar MS systems that use simple file sharing or passwordless file sharing.

Another risk is P2P apps.  One can easily monitor what another is sending and receiving on messaging apps, multimedia sharing, etc.

---

### Post by EJeanmaire on 2009-11-04
> **tturrisi said:**
> FYI, when using an open wlan, only certain things are sent in clear text over http.  FTP and POP and SMTP send clear text usernames and passwords.  HTTPS doesn't.  If someone sniffs your HTTPS logins they will not see the text usernames and passwords, they will only see the encrypted names.


With ARP spoofing the attacker can change your https requests into http requests, making you send your password via clear text to the attacker who turns around and sends it to the bank or whatever website via https.  Do you diligently check to see that your bank site is being accessed vis https every time you goto it?  I know some bank sites only serve the POST form URL in HTTPS but their entrance page is http, thus you would not even see the fact that they spoofed your https traffic until you already surrendered your credentials.  Hope this all makes sense.  Long story short, its a bigger risk than you think.

---

### Post by Alxl on 2009-11-05
> **EJeanmaire said:**
> With ARP spoofing the attacker can change your https requests into http requests, ............


Would  '** arpON** '    (available free from sourceforge.net)  help prevent ARP spoofing or poisoning or the "middle-man-attack" ? - I am not sure if I got the correct names !

---

### Post by Lars Noodén on 2009-11-06
> **Alxl said:**
> Would  '** arpON** '    (available free from sourceforge.net)  help prevent ARP spoofing or poisoning or the "middle-man-attack" ? - I am not sure if I got the correct names !


No.  DNSSEC, and add-on to IPv4 and part of IPv6, would prevent ARP spoofing.  IIRC IPv6 doesn't use ARP.  However, more than a handful of interests have a lot to lose if network security tightened up.  Using IPv6 would eliminate a number of companies markets and eliminate still others from the market -- albeit both groups deservedly eliminated.  So though debian (ubuntu's foundation) has had IPv6 for years, not much has happened.  

Also not using DHCP would mitigate it a little, as would static ARP tables but since the question is about wireless hotspots, most users are S.O.L.

---

### Post by Alxl on 2009-11-08
[FONT=Verdana][COLOR=#000000]I found a couple of companies providing IPv6  but it is out of the question for me to subscribe (I am not a business!).[/COLOR][/FONT]
[FONT=Verdana][COLOR=#000000]
[/COLOR][/FONT]
 [FONT=Verdana][COLOR=#000000]Anybody using[      HotSpotVPN]("http://hotspotvpn.com/")  or  [Witopia ]("http://www.witopia.net/")?  [/COLOR][/FONT][FONT=Verdana]The prices are about $40 to about $170/yr.  Is it worth the higher price?
 Would you recommend other providers? [/FONT]
Thanks

---

### Post by Jekshadow on 2009-11-08
Network traffic can be snooped via an ARP Cache Poisoning attack, and the OS does not matter. Even an ultra-secure OS like OpenBSD cannot do anything about it. The best way is still to setup a SSH tunnel the minute you connect, then route your traffic through that.

---

### Post by witeshark17 on 2009-11-08
For more [ info](http://www.watchguard.com/infocenter/editorial/135324.asp) Interesting read.

---

### Post by cariboo on 2009-11-09
Merged with the existing thread.

---

### Post by EJeanmaire on 2009-11-09
> **Alxl said:**
> [FONT=Verdana][COLOR=#000000]I found a couple of companies providing IPv6  but it is out of the question for me to subscribe (I am not a business!).[/COLOR][/FONT]
[FONT=Verdana][COLOR=#000000]
[/COLOR][/FONT]
 [FONT=Verdana][COLOR=#000000]Anybody using[      HotSpotVPN]("http://hotspotvpn.com/")  or  [Witopia ]("http://www.witopia.net/")?  [/COLOR][/FONT][FONT=Verdana]The prices are about $40 to about $170/yr.  Is it worth the higher price?
 Would you recommend other providers? [/FONT]
Thanks

I would say just wait to do any confidential web-browsing until you are home; or set-up a home VPN, which is potentially free.  On your Ubuntu box at home set up a VPN service.  Make sure your router has vpn passthrough (tunneling) techs enabled, open VPN port, and set up the router to use a dynamic dns service (ddns) so that you will always know the address of your home machine to dial back to.

---

### Post by mr-woof on 2009-11-09
I've noticed people are mentioned setting up a ssh tunnel the minute you connect, what is the tunnel connecting to? Your home network?

---

### Post by Lars Noodén on 2009-11-10
> **mr-woof said:**
> I've noticed people are mentioned setting up a ssh tunnel the minute you connect, what is the tunnel connecting to? Your home network?

Yes.  Or somewhere else you'd rather surf 'from'

---

### Post by Rayve on 2009-11-11
Okay, so I've got the SSH set up successfully (only with passwords, keys by themselves aren't working yet, boo) with the server on my home desktop and then client on my netbook.  How do I tunnel my internet traffic through there?

Thanks!

---

### Post by The Cog on 2009-11-11
> **Rayve said:**
> Okay, so I've got the SSH set up successfully (only with passwords, keys by themselves aren't working yet, boo) with the server on my home desktop and then client on my netbook.  How do I tunnel my internet traffic through there?

I'm curious to know that, too.

I recommend that you change your SSH listening port from 22 to something high, to avoid being found by the majority of the SSH password-guessing bots. Also make sure all your passwords are secure. Also make getting certificates working a priority.

---

### Post by Alxl on 2009-11-13
[SIZE=3]I have to take the focus from [/SIZE][SIZE=3][COLOR=#000000]installing a SSH Tunnel  for a moment since I cannot do that with my home computer.[/COLOR][/SIZE]
[SIZE=3][COLOR=#000000]
[/COLOR][/SIZE]
[SIZE=3][COLOR=#000000] If nobody here is using HotSpotVPN or Witopia, does anybody know about  ARPWatch ? -  I'd like to learn about this one though so far it looks to be beyond my capabilities. <[/COLOR][/SIZE]
[SIZE=3][COLOR=#000000]
[/COLOR][/SIZE]
 [SIZE=3][COLOR=#000000]How about booting from  a Live USB ?  [/COLOR][/SIZE][SIZE=3]
[/SIZE]
[SIZE=3]Thanks[/SIZE]

---

### Post by update_manager on 2009-11-14
> **The Cog said:**
> I'm curious to know that, too.

I recommend that you change your SSH listening port from 22 to something high, to avoid being found by the majority of the SSH password-guessing bots. Also make sure all your passwords are secure. Also make getting certificates working a priority.

On the client:

ssh -D 9999 <IP> -p <port>
netstat -ln | grep 9999 (should show a server now listening on that port)
configure firefox to use a SOCKS proxy, 127.0.0.1 port 9999, version 4

---

### Post by kevdog on 2009-11-14
Or see this thread if wanting DNS tunneled as well:

[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=723025](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=723025)

---

### Post by The Cog on 2009-11-14
Interesting - thanks.

---

