---
title: "Quick OpenVPN question"
date: 2010-06-03
forum: Server Platforms
---

### Post by Dan90 on 2010-06-03
G'day everyone, I would like to ask anyone with the knowledge of setting up VPN a few basic questions.

Firstly I'm just looking at setting up OpenVPN so I connect to my ubuntu server when I'm out. My question is do I want to run the package on the server itself behind the router? or on the router itself? (Asus WL500G running gargoyle 1.0.16)

I have setup a DynDNS hostname to resolve to my IP address and portforwarded the external port on my router to port 22 for ssh as my ISP blocks port 22. I still need to play around with this to get it working when I get home, SSH works fine locally.

Ideally I would like to use VPN just to control my server when I'm say at uni or out and about, my question again comes to should I just use SSH with port forwards? or try to setup VPN. If I try to setup VPN where do I want to install it to? and if i use VPN, which ports would I need to forward to connect into my home network?

Any help or help links would be greatly appreciated.

Cheers

---

### Post by hictio on 2010-06-04
You can install OpenVPN on that router?
Normally the OpenVPN installs on a Linux Server, it can be behind a router, be sure to let pass the traffic for the specific port, which, by default is 1194 UDP, but you can customize that (not only the port, but you can change it to TCP as well).
Be sure to setup your LAN network with a "hard to use" private IP address (and to make just big as you really need it), so there is no problem when you connect to your boxes from the coffee shop that setup its LAN with the default 192.168.x.x.

Take a look at this Ubuntu doc [OpenVPN](https://help.ubuntu.com/community/OpenVPN)

---

### Post by spynappels on 2010-06-04
Yes, you run the OpenVPN server on your server and then use a client on your remote machine (laptop) to connect to the VPN. Clients are available for Windows, Mac and Linux and the latest version of Ubuntu Desktop will allow you to connect to the vpn using the built-in Connection Manager.

---

### Post by Dan90 on 2010-06-04
Thanks guys, that will be the info I need to start me off.

Wasn't sure where to start. It is possible to install OpenVPN on my router as I can ssh into the gateway ip and log in as "root" "<adminpasswordhere>". The only problem is once I install and setup OpenVPN that way I didn't come to a way to make the keys.

I've done some reading through the ubuntu wiki and it looks like the way to go.

Again cheers for the help.

---

### Post by benderisgreat on 2010-06-04
> Ideally I would like to use VPN just to control my server when I'm say at uni or out and about, my question again comes to should I just use SSH with port forwards.

Why do you think ssh would not suffice for your purpose?

---

### Post by HermanAB on 2010-06-04
Howdy,

The standard way to administer remote machines is with SSH.  From Windows, use PuTTY.

BTW, SSH can also do Socks and SSL VPNs.  These are easiest with SSH, since it kinda has a debug terminal built in ;)

---

### Post by Dan90 on 2010-06-06
SSH could most likely do everything I need. Discovering more about how it works here and there. Anyway, I figure VPN 'could' be helpful for grabbing files from home, though it wouldn't be necessary. I'm happy to live an extra few hours and wait till I get home to grab stuff.

---

### Post by benderisgreat on 2010-06-06
the install of ssh server on ubuntu comes standard with sftp and scp for copying files. You could even look into sshfs.

---

### Post by spynappels on 2010-06-07
Setting up an OpenVPN instance is a great way to learn and consolidate a lot of skills including security and SSL, Key generation and management and networking.

While SSH can do much of what the OP wants to do, learning new skills is useful and fun too, so in terms of time spent, it is worth it in my opinion.

---

### Post by Dan90 on 2010-06-09
I can agree trying to learn things is much fun. Haven't had much luck with OpenVPN, did have a little luck with pptpd, but I can't get it working again. 

As mentioned, scp does work, and I'm quite happy with that. It's all a learning curve and I'll get there one day :)

---

