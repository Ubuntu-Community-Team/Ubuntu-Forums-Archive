---
title: "Local server access only"
date: 2018-09-01
forum: Security
---

### Post by webmiester on 2018-09-01
Hi everyone,

Im not a really a specialized IT guy, and know only some basic linux stuff.  I hope you guys dont mind me asking a few questions (Actually Ive asked a lot already on this forums)

I hired a guy to setup and make the software on my server.  The server runs Ubuntu server and Apache.  It is connected to a network with other computers which should act as terminals or kiosks.  However, the network is also connected to the internet.  I am concerned about people from outside my company getting into the server through the internet and hacking the server...

So I talkied to my software developer to about security and he says that the server cannot be seen by people from the outside  He says that the server has global settings and it was set to "local" so that only the local users can view it.  In fact, to update the server, he uses teamviewer to get into one of the terminals and uses that terminal to access the server...

So here are my questions:

1) How do I check if the server is really on this "Local" global settings?
2) How secure is this "local" global settings if it is turned on?  Have we had instances that despite this setting, a server is still accessed from the outside through some sort of backdoor?
3) How secure is this setup that he uses teamviewer to update the server?
4) As additional security, I plan to set up the following:
     A. Set up IP tables on the server so that only the computers of the company with the said IPs can access the server data
     B. Bind the MAC address of the company computers with specific IPs using settings in the DHCP server
     C. Setup a Pfsense firewall (although I dont know what configuration I need to setup to prevent outside intruders), I might replace this with a mikrotik appliance though.  Firewalls running in Ubuntu is welcome but I hvaent found one with both the captive portal and the traffic shaping features I need.

May I have comments and suggestions pls regarding this, specially on the "local" global settings that my IT software guy promises.  I wouldn't want to be shortchanged, so I need to check this myself.  Thank you so much.  I mean I really appreciate all the help Ive been getting from the community.

---

### Post by TheFu on 2018-09-02
> **webmiester said:**
> Hi everyone,

Im not a really a specialized IT guy, and know only some basic linux stuff.  I hope you guys dont mind me asking a few questions (Actually Ive asked a lot already on this forums)

That's why we're here.
> **webmiester said:**
> I hired a guy to setup and make the software on my server.  The server runs Ubuntu server and Apache.  It is connected to a network with other computers which should act as terminals or kiosks.  However, the network is also connected to the internet.  I am concerned about people from outside my company getting into the server through the internet and hacking the server...

So I talkied to my software developer to about security and he says that the server cannot be seen by people from the outside  He says that the server has global settings and it was set to "local" so that only the local users can view it.  In fact, to update the server, he uses teamviewer to get into one of the terminals and uses that terminal to access the server...

So here are my questions:

Either you trust the guy or you don't.  But ... everyone has gaps in their knowledge and everyone misses things.  Ultimately, YOU are responsible. If you want him to be responsible, put it in a written contract, with penalties. It is best to have separation of duties between custom software, server security and network security.

> **webmiester said:**
> 
1) How do I check if the server is really on this "Local" global settings?
He probably dumbed down the answer for you.  There is no "Local global settings"... it is possible for apache to be configured to only answer requests from LAN IPs, or specific IPs, or 1 IP.  I'd guess, and it is only a guess, this is what he's done.  There are many different methods to accomplish something like this, so without details, it is impossible to know.

> **webmiester said:**
> 
2) How secure is this "local" global settings if it is turned on?  Have we had instances that despite this setting, a server is still accessed from the outside through some sort of backdoor?
If I were setting up an internal only server, I'd do the following:
* Not allow any port forwarding from any internet router into it.
* Setup a firewall on the server that only allows LAN access and only to the specific ports necessary for expected local use.

When it comes to security, I like using layers for protection.  At least 2, perhaps 3 different methods to block access.  That way, misconfiguration of 1 doesn't leave the barn door open accidentally.   Router, apache, webapp can all block non-LAN IPs. Use all three.

> **webmiester said:**
> 
3) How secure is this setup that he uses teamviewer to update the server?
IMHO, servers don't have GUIs.  ANY GUI running on a "server" is an attack vector and needless risk factor. He really should be using ssh, with ssh-keys, never passwords.  The router+firewall should allow outside ssh connections only from the specific IP where he comes from, not everywhere in the world.  On the system, brute force attacks should also be blocked after a few attempts, automatically. fail2ban will do that.

> **webmiester said:**
> 
4) As additional security, I plan to set up the following:
     A. Set up IP tables on the server so that only the computers of the company with the said IPs can access the server data
     B. Bind the MAC address of the company computers with specific IPs using settings in the DHCP server
     C. Setup a Pfsense firewall (although I dont know what configuration I need to setup to prevent outside intruders), I might replace this with a mikrotik appliance though.  Firewalls running in Ubuntu is welcome but I hvaent found one with both the captive portal and the traffic shaping features I need.
a. He should have done that already - well, with any front-end to the kernel firewall. iptables is just a front-end. The WAN router should also be blocking any unknown/unwanted attempts. Always have 2 layers blocking what you don't want.
b. Ok.  I'd just use static IPs on all servers myself.  I use DHCP reservations for portable devices only. Changing a MAC is trivial, BTW and every ethernet packet includes the MAC, unencrypted. This is how layer-2 networking works.
c. A solid firewall/router is always a good choice.  I find captive portals to be a hassle.  Traffic shaping on pfSense is better than any Linux-based router, IMHO.  Learning pfSense / OpenSense is a different sort of router than the Linux-based ones. Packets are blocked on the way in on any interface, not on the way out of the router. You'll probably want to buy the book to learn pf.
> **webmiester said:**
> May I have comments and suggestions pls regarding this, specially on the "local" global settings that my IT software guy promises.  I wouldn't want to be shortchanged, so I need to check this myself.  Thank you so much.  I mean I really appreciate all the help Ive been getting from the community.

I have a issue with teamviewer, but many people don't.  I don't like trusting 3rd parties, especially if they are providing free services without a written, signed, contract. TeamViewer clients have had their credentials stolen in the past. Also, if TeamViewer corporate has a bad apple, what prevents that person from connecting into thousands of free-accounts and accessing the systems? Nothing that we can trust. TeamViewer has 1 redeeming quality, it allows remote access without opening any firewall ports.  Personally, I'd prefer to have a high-port open with ssh access or setup a full VPN, since both of those don't rely on some 3rd party, don't need DNS and use PKI where I control both sides.  I know how to secure ssh.  I don't think I can secure TeamViewer, ever.

Asking a software developer to be a Unix admin is probably going too far.  Those are different skills and seldom really mix.  I've done both, the thought process for each position is very different.

You can also engage someone to perform penetration testing of your network from outside and inside. I suspect there are  open attack vectors, because there always are.  Someone certified with a CISSP would be a good beginning, but there are other, more specialized, certificates for white-hat hackers. Look for "Offensive Security" certs from SANS.

Since you are using Kiosks, I'd think you'd want the OFSEC testing. Kiosks have many attack vectors that most people don't know.

---

### Post by webmiester on 2018-09-02
Thank you so much.  

You are very right about trusting people. 
 Some people will make lots of promises, but in the end, we ar the ones who will be in trouble for their lapses.  That's why I want to see what they are telling me about with my own eyes.


Yes first off, the server doesnt have teamviewer nor a GUI.  He uses teamviewer to enter into one of my stations which has the GUI, and then he uses SSH from that station to enter the server.

I tried asking my developer about that "local" settings thing, and he just says its a setting.  Ill go ask him if the setting is at Ubuntu server setting or if it is an apache setting.

I asked him about the IPTables.  He says it is secure but it will be a big hassle to maintain he says.  When a computer gets destroyed, setting up a new one will be the headache.  I figured, what Ill do is to purchase a few spare computers and have those MAC addresses already programmed into the system so we have spare computers ready.

Yeah, the firewall is supposedly good.  But when I talked to another guy (He was the first I hired before this current one), he told me that pfsense only protects our computers from accessing the internet or certain sites on the internet, it wont prevent computers from the internet to access our server.  Well I lost trust in that other guy.  So is there any particular feature that I should look for in a firewall which should protect my server from attack?

I think it will be useful for me to understand first how a computer from outside our network can access our server.  I mean, in my LAN I just type in 192.123.123.231 and I get into our web based system...  But if I go to my friends' house and I type the same address, it wont work.  So how does a person on the internet theoretically reach my server?

I know this might take time to explain, If this is too much, I would appreciate even just a link to read or even just some keywords for me to look up.  I know everyone is busy, and I really appreciate your time.

---

### Post by TheFu on 2018-09-02
Yes, it is too much to explain.  You need to understand basic IPv4 networking before you begin.  Search for "Security Now" ep 25,26, ... to get a basic explanation - I think it is called "How the internet works".  Useful for noobs and clearly explains why 192.168.5.350 isn't possible.
BTW, I hope the IP you posted was made up.  That is a public IP and I suspect your server has a private IP that doesn't get routed over the internet. That is also a key security control.

Also, be certain to disable all IPv6 networking on all your systems until you are ready to secure it.  IPv6 can be used as an attack vector that IPv4 routers and firewalls ignore.  Disable it everywhere.

People who are trustworthy should know the limits of their knowledge and say it when it counts.  The guy who said pfsense doesn't do X, didn't know what he was talking about. Don't use him again, if you are positive that is what he said. I suspect that you might have simplified what he said, however, losing the true meaning.

Anyone who things iptables is a hassle is doing system configuration wrong. Professionals will use a devops tool for configuration or at least have scripts to do it. If someone it spending hours typing commands, they aren't a system administrator.  Developers think differently than admins.  For simple firewall configs, there is also ufw.  It is another interface into the kernel firewall, but much easier to configure.  It doesn't support all the options that iptables does, but if you don't need those, it is fine.

All routers/firewalls have the features you need.  Some have a few nice-to-have features that you might grow into.  As long as you stay away from "consumer" routers and keep wifi and storage off the router, you should be fine.  pfsense, ubiquiti and MikroTik are reputable.  I've seen all 3 deployed and know that each has a history of providing patches in a timely way for years. Out of all of them, pfsense gives you the most control over upgrades.  I run a pfsense WAN router and have deployed Ubiquiti wifi APs and pfsense routers at customer sites (back when I worked).

---

### Post by webmiester on 2018-09-02
Hi TheFU,

Thank you so much.

Yeah the IP I posted is made up.   I dont know so much but I at least know not to post my server IP on a public forum, hehehe.  I dont even want to email passwords or send them through messenger.

Well, here is one question regarding the IP addresses and my system's access:

All public websites have IP addresses right?  So if I like if enter the IP address of ubuntuforums into my browser address bar, Ill should get to ubuuntu forums just like if I were to enter ubuntuforums.org in browser right (Please correct me if I am wrong).  Now, if my server address like if it was 192.123.123.321 happened to have an IP address similar to one on the internet, what makes my stations connect to my server and not to the one on the internet?

Now if I reverse my question.  Let's say I did post my real server IP in this forum, how is someone outside my network supposed to find it (or hack it)?  Since I made up the IP on my DHCP server, there could be loads of other computers out there with their administrator coming up with the same IP.  I wouldnt be surprised if a software developer were to setup the same local IP address for all his clients (this makes them easier to setup, maintain, and remember).  My personal sense thinks it is dangerous, but I dont yet understand what the process would be for someone to simply find it.

Thanks so much about the iPv6.  Ill make sure they are turned off.

I do plan to use the ufw to configure the iptables.  I actually have a post on another thread asking about the command lines for it.  Ubuntu mate 16.04 comes with a firewall in its GUI.  What was terrible was that I set it up with a whitelist for my server and a blacklist everywhere else.  Then when I ran firefox, I was still able to visit any site :(
What did I do wrong?  I also made sure it was turned on.  Do firewalls behave differently when accessing local IPs and IPs on the internet?  This was done on a Raspberry pi 3 running on Ubuntu Mate 16.04.  I was wondering if the distribution I got had a bug that prevented the firewall from working.

Anyway, I got rid of that other IT guy.  He was a scammer.  I requested that my server be an ubuntu server... then he bought a DELL that had windows, telling me that windows comes with it but we will reformat it for linux later on.  Then when his software was installed he just placed it in windows, and tells me "Well since Windows is already there we might as well use it.  It will be a waste not to use it".  There were so many other things that really showed me he was lying and really not worth it.  This included his statements on PFsense which he promised to setup but never did.  I bet he really didnt know anything about linux and just pretended to know so he can get the contract.  Anyway, he isnt supposed to be part of my post, but I appreciate being able to vent it out every now and then.

This new guy knows a bit more, and also I've worked with him for many years in another field (we were musicians together before he went into programming) and I know he is honest.  I put honesty at a premium more than skill.  We can all learn skill, but a dishonest person doesnt come with honesty.

---

### Post by webmiester on 2018-09-02
So Im having a little chat with my IP guy and this is what he says:

"In order for my server to be seen by people outside the network, we should have port forwarding.  Must be global ip then should point to partcular local ip with a web server listening to a particular port"

It sounds to me like these settings is with the router rather with the server or apache...

Ok, so with this, I think I need to put additional layers of security.  Ill add the ufw IPtables.

What can I add with Apache to protect it?

---

### Post by webmiester on 2018-09-02
OK, he also tells me that the second layer of protection would be the user password of ubuntu server...

Does that sound lame or does it sound alright?  It also runs on mySQL, what can I add to MySQL to protect it?

Thanks.

---

### Post by TheFu on 2018-09-02
Too many questions.

iptables is an interface to the kernel firewall.
ufw is an interface to the kernel firewall.  
Both programs serve similar purposes.  Pick one and use it. Don't mix.

Your understanding of IP isn't at a point where I can help. Find that podcast and listen/read to those episodes until you gain the necessary understanding.  Sharing some IPs is fine. 192.168.x.x or 172.16.x.x- 172.32.x.x and 10.x.x.x are all fine to share over the internet.  These are private internet addresses. Unroutable over the internet.

I don't use apache or mysql.  BTW, you should be careful asking specific questions when you haven't shared the entire setup. Answers change based on what is being done.  For example, I would never run a DBMS inside the same machine that is running a website or a webapp.  The risk profiles for those are different and the DBMS needs to be much more protected.  But that is me and I haven't a clue about your setup or situation.

In general, a server should run only those services required to do the job. Nothing more.  
Access to those services should be limited to only the clients which require access. No others.  
My take on server security: [http://blog.jdpfu.com/2016/10/04/lamp-server-security](http://blog.jdpfu.com/2016/10/04/lamp-server-security) .
Passwords are a security failure. Use keys whenever possible.

---

### Post by webmiester on 2018-09-02
Thank you so much.  I'll look up keys as well.  Btw, why shouldnt we use Apache and MySQL?  Are they very bad for security?

---

### Post by TheFu on 2018-09-02
> **webmiester said:**
> Thank you so much.  I'll look up keys as well.  Btw, why shouldnt we use Apache and MySQL?  Are they very bad for security?

I never said you shouldn't use them.  I don't know your specific setup. But ....

For me, not using mysql is more about avoiding Oracle and using a solution I consider better, postgres.  MariaDB is a replacement for MySQL that avoids Oracle, but behaves like MySQL.  The original mysql team left oracle for well-published reasons and made MariaDB.  Call it politics, if you like.

Apache is an "everything + kitchen sink" solution in my mind. If you need that, great, use it.  There are lighter, faster, more secure solutions, if you don't need everything AND the kitchen sink in your solution.  It just depends on your architecture what could be better.

Read the links and find those podcasts.

---

### Post by webmiester on 2018-09-03
Thank you TheFU,

I really appreciate your time and replies.

---

### Post by webmiester on 2018-09-03
Thank you.  I read a little bit about MariaSQL after you posted it.  Yeah, I was a bit curious about MariaSQL too before.  I cant rememebr where I read it.  I think it was an option when I installed my ubuntu server, there was a checkbox for MariaSQL and PostgreSQL.

I agree with you about the kitchen sink part.  Some people might like including the kitchen sink because it might come in handy in the future.  However, the kitchen sink may have vulnerabilities that might be exploited too.  The more rooms, and sinks we have, the more possibilities for backdoors.  I do hope I got the analogy right.

---

### Post by SeijiSensei on 2018-09-03
I use PostgreSQL for everything except applications that demand MySQL/MariaDB like WordPress.  Back when I first started building servers for clients, PostgreSQL was the only relational DB solution that was completely free.  I've never looked back.

---

