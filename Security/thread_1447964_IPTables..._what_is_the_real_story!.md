---
title: "IPTables... what is the real story!?"
date: 2010-04-06
forum: Security
---

### Post by GodLikeCreature on 2010-04-06
I have read many different versions of how IPTables is setup in Ubuntu.  The more optimistic claim it is there and enabled by default, closing any and all ports, and making Firestarter or UFW mere graphical interfaces that help in setting up rules.  

On the other hand, I have recently read the exact contrary, that Ubuntu is actually an exception in this regard, and that unlike other distros, it has IPTables disabled by default.

Does anybody have actual information from the project or the developers to clarify this?  I am inclined to think IPTables is there and running, but I obviously want to be sure!

Thanks

---

### Post by lisati on 2010-04-06
Moved to "security discussions"

---

### Post by uRock on 2010-04-06
From what I have seen in port scans is that until Firestarter or UFW are enabled, ports will be open, however, an install will have no listening ports by default. Once a file sharing service, such as Samba is installed or a Telnet client such as SSH is installed, ports will be open.  The following three screenshots show the results of a port scan against my ubuntu Lucid netbook. 

In the first scan it shows 100 ports filtered, because that is how many ports the quick scan targets and they are all blocked by the enabled UFW. 

The second and third screenshots show the results of scanning with UFW disabled. 3 ports are open and you will notice that the scanner picked up some other info as well. The three ports are obviously SSH and the two Samba ports.

Cheers,
Ronnie

---

### Post by ajgreeny on 2010-04-06
I believe iRock has got it right.  iptables is running by default, and there is no need to run any firewall configuration application unless you are running a mail or something similar.server 

I run a stand-alone desktop attached to a router but not using a network to other computers and not having any samba or other servers running.  A scan by the website Shields Up [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2) always shows my machine as totally hidden to the web, with all ports stealthed, and that has always been the case.  Attached is a screenshot of a recent scan of ports.

I do not run any firewall configuration application such as firestarter, ufw, gufw, etc etc, and see no reason to do so.

---

### Post by yeleek on 2010-04-06
> On the other hand, I have recently read the exact contrary, that Ubuntu is actually an exception in this regard, and that unlike other distros, it has IPTables disabled by default.

sudo iptables -L

will show you what rules you have currently.

If you've not specified any then you will probably get this

Chain INPUT (policy DROP)
target     prot opt source               destination         

Chain FORWARD (policy DROP)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination   

however - once configured this will be very different.

And irock is spot on

> From what I have seen in port scans is that until Firestarter or UFW are enabled, ports will be open, however, an install will have no listening ports by default.

I would add though - one problem with relying on GRC etc, is that they will test the first firewall they hit on your connection.  Which hopefully will be your routers firewall, not necessarily the firewall on your pc.

If you want to know the real state of your machine, if you've got access to another pc on the same network (i.e. not behind a router etc) then use it to run an nmap scan against your machine or if very brave, turn off firewall on router.  Then use GRC or nmap-online to scan your machine to see the real results - but remember to turn router firewall back on!!!!!

---

### Post by spynappels on 2010-04-06
I have found that sudo iptables -L does not give me all the information relating to my firewall rules, set using Webmin.

Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:https
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:webmin
DROP       tcp  --  anywhere             anywhere            tcp dpt:ssh
ACCEPT     tcp  --  resolver1.opendns.com  anywhere            tcp dpt:domain
ACCEPT     udp  --  resolver1.opendns.com  anywhere            udp dpt:domain
ACCEPT     tcp  --  resolver2.opendns.com  anywhere            tcp dpt:domain
ACCEPT     udp  --  resolver2.opendns.com  anywhere            udp dpt:domain
ACCEPT     all  --  anywhere             anywhere            state ESTABLISHED
ACCEPT     all  --  anywhere             anywhere            state RELATED
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:webcache
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:8100
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

The last 2 accept in the INPUT section actually refer to 2 network interfaces other than eth0, namely lo and tun0. How can I show this info from the terminal?

---

### Post by GodLikeCreature on 2010-04-06
> **iRock said:**
> From what I have seen in port scans is that until Firestarter or UFW are enabled, ports will be open, however, an install will have no listening ports by default. Once a file sharing service, such as Samba is installed or a Telnet client such as SSH is installed, ports will be open.  The following three screenshots show the results of a port scan against my ubuntu Lucid netbook. 

In the first scan it shows 100 ports filtered, because that is how many ports the quick scan targets and they are all blocked by the enabled UFW. 

The second and third screenshots show the results of scanning with UFW disabled. 3 ports are open and you will notice that the scanner picked up some other info as well. The three ports are obviously SSH and the two Samba ports.

Cheers,
Ronnie

Hi, Ronnie,

Thanks a lot for your reply!

Sorry to insist, but I want to get some solid understanding on this one.  When you say enable, do you mean that once UFW or Firestarter are installed and run once, then you are protected?  I say so because I have firestarter installed in my computer and I can see most ports are closed already, so I am guessing firestarted took care of that during installation and setup.

On a different note, I have done the same portscan on my machine, but I get two ports open by default: ipp and mysql.  

I do have mysql server installed on my machine for developing purposes, so I need it.  As for ipp, I don't print from this computer, but I may in the future.  In short, I wouldn't want to shutdown any of those services in the short term.

My question is...  Is it potential risk to have those ports open?

Thanks!

---

### Post by lovinglinux on 2010-04-06
> **GodLikeCreature said:**
> I have read many different versions of how IPTables is setup in Ubuntu.  The more optimistic claim it is there and enabled by default, closing any and all ports, and making Firestarter or UFW mere graphical interfaces that help in setting up rules. 

It is enabled by default, but all traffic is allowed. Nevertheless, there isn'tt any listening services running by default that could accept remote connections, so all ports are effectively closed, even with iptables allowing all traffic.

Firestarter and **G**ufw are merely graphical interfaces, no matter how iptables is configured by default. UFW is not a graphical interface, it is more like a "facilitator". It is also command-line, but it simplifies the creation of iptables rules with simpler commands. Gufw is the GUI for UFW.

> **GodLikeCreature said:**
> On the other hand, I have recently read the exact contrary, that Ubuntu is actually an exception in this regard, and that unlike other distros, it has IPTables disabled by default.

Nope. As explained above, it is enabled by default, but the default rule is set to ACCEPT all traffic.

---

### Post by lovinglinux on 2010-04-06
> **GodLikeCreature said:**
> Sorry to insist, but I want to get some solid understanding on this one.  When you say enable, do you mean that once UFW or Firestarter are installed and run once, then you are protected?  I say so because I have firestarter installed in my computer and I can see most ports are closed already, so I am guessing firestarted took care of that during installation and setup.

Yes. Once you configure Firestarter or UFW you are protected. You don't even need to run them anymore, ever. You only need to run them if you want to change the firewall rules. Is  not even recommended to run Firestarter at boot, due to security reasons.

> **GodLikeCreature said:**
> On a different note, I have done the same portscan on my machine, but I get two ports open by default: ipp and mysql.  

I do have mysql server installed on my machine for developing purposes, so I need it.  As for ipp, I don't print from this computer, but I may in the future.  In short, I wouldn't want to shutdown any of those services in the short term.

My question is...  Is it potential risk to have those ports open?

Thanks!

If you have a router and don't forward those ports to your machine, then no. Nobody will be able to reach them if you don't forward the ports. You don't even need to setup iptables in this scenario.

If you do forward the ports from the router, so you can access the applications listening to them from your office for example, then there is a risk that depend on the application security flaws and how you set it up. If you want to have access to your local server remotely, but don't want to allow anybody else to reach it, then using iptables is recommended. You can for example allow only the IP of your office computer to reach the open ports.

---

### Post by GodLikeCreature on 2010-04-06
> **lovinglinux said:**
> Yes. Once you configure Firestarter or UFW you are protected. You don't even need to run them anymore, ever. You only need to run them if you want to change the firewall rules. Is  not even recommended to run Firestarter at boot, due to security reasons.



If you have a router and don't forward those ports to your machine, then no. Nobody will be able to reach them if you don't forward the ports. You don't even need to setup iptables in this scenario.

If you do forward the ports from the router, so you can access the applications listening to them from your office for example, then there is a risk that depend on the application security flaws and how you set it up. If you want to have access to your local server remotely, but don't want to allow anybody else to reach it, then using iptables is recommended. You can for example allow only the IP of your office computer to reach the open ports.

That's brilliant!

Thank you for your very clear replies and help!

---

### Post by uRock on 2010-04-06
> **GodLikeCreature said:**
> Hi, Ronnie,

Thanks a lot for your reply!

Sorry to insist, but I want to get some solid understanding on this one.  When you say enable, do you mean that once UFW or Firestarter are installed and run once, then you are protected?  I say so because I have firestarter installed in my computer and I can see most ports are closed already, so I am guessing firestarted took care of that during installation and setup.

On a different note, I have done the same portscan on my machine, but I get two ports open by default: ipp and mysql.  

I do have mysql server installed on my machine for developing purposes, so I need it.  As for ipp, I don't print from this computer, but I may in the future.  In short, I wouldn't want to shutdown any of those services in the short term.

My question is...  Is it potential risk to have those ports open?

Thanks!

By default, I "think" IPtables are not active, but there are also no active listening programs on a default installation.

When and why do I run UFW? I run UFW on my wireless machine when I am not on my home network to protect it from other people on public networks, such as my college.

Loving Linux has a great point, when you are on your home network and said network is secured, then you don't really need a firewall. If your router connection is not password protected(encrypted) then anyone in the neighborhood can connect to it and your systems via the local network.

Cheers,
Ronnie

---

### Post by FuturePilot on 2010-04-06
By default there are no iptables rules but there are also no listening services. So unless you install some type of server there are no open ports and no real need for a firewall.

---

### Post by Objekt on 2010-04-06
I think I may have stumbled upon the solution to a totally different, but related, problem.

Internet connection sharing simply Does Not Work on my Ubuntu 9.10 machine.  It doesn't work because the proper rules don't get set up in iptables, even though I set the second NIC (eth1) as "shared" in the NetworkManager GUI.  I still don't know why that happens.  But, ICS DOES work in an Ubuntu 9.10 Live CD environment.  I simply set eth1 as "shared" in NetworkManager, and iptables magically gets the rules to forward traffic to/from eth1.

Noticing that, I looked at what rules iptables was using in that situation.  That was as far as I got, because I couldn't figure out how to set up those rules in iptables, or have them persist after a reboot.  It sounds like ufw is the way to do what I want.

---

### Post by bodhi.zazen on 2010-04-06
The iptables rabbit hole gets as deep as you would like to go.

iptables is after all a front end for netfilter :lolflag:

In a nut shell, you need to understand first that a default installation of Ubuntu has no significant open ports.

Second you need to understand your network configuration. Do you use a router ?

Third you need to understand how to scan your box for open ports. You can use nmap or ShiledsUp, although if you use shields up you need to connect you box directly to the internet, otherwise you are scanning only your router.

Last we nee dto know if you intend to run a server and if so what kind of access do you wish to allow ? Public ? Private ? LAN only ?

To understand firewalls you will need to be willing to do some reading .

[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)

[http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)

[http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)

---

### Post by Objekt on 2010-04-07
It's definitely the local access config I'm tripping over.  I want to make several shares (NTFS volumes primarily) available to Windows boxes on my LAN, but no one else.  Which I believe is what Samba is supposed to do.

I have a coworker who says he only has about 15 ports open on his home Linux box.  He even runs a cron script to open the time port (I guess that would be port 123 right?) only once a month.

That seems like overkill.  Is there *any* known exploit which uses port 123?  Anyway I have no idea how to set up cron scripts, and certainly no idea how to use them to open/close ports.

---

### Post by uRock on 2010-04-07
> **Objekt said:**
> It's definitely the local access config I'm tripping over.  I want to make several shares (NTFS volumes primarily) available to Windows boxes on my LAN, but no one else.  Which I believe is what Samba is supposed to do.

I have a coworker who says he only has about 15 ports open on his home Linux box.  He even runs a cron script to open the time port (I guess that would be port 123 right?) only once a month.

That seems like overkill.  Is there *any* known exploit which uses port 123?  Anyway I have no idea how to set up cron scripts, and certainly no idea how to use them to open/close ports.

If you are behind a router, then there should be no worries.

---

### Post by cariboo on 2010-04-07
> **Objekt said:**
> It's definitely the local access config I'm tripping over.  I want to make several shares (NTFS volumes primarily) available to Windows boxes on my LAN, but no one else.  Which I believe is what Samba is supposed to do.

I have a coworker who says he only has about 15 ports open on his home Linux box.  He even runs a cron script to open the time port (I guess that would be port 123 right?) only once a month.

That seems like overkill.  Is there *any* known exploit which uses port 123?  Anyway I have no idea how to set up cron scripts, and certainly no idea how to use them to open/close ports.

I think 15 ports open is a bit excesive for a desktop system. My home server only has 6 open ports:

[list]
[*] 22 ssh
[*] 80 http
[*] 111 rpcbind
[*] 138 netbios-ssn
[*] 445 microsoft-ds
[*] 2049 nfs
[/list]

None of them are open to he world. The system is used for sharing files in a mixed network of Windows and Ubuntu. All the Ubuntu system share using nfs, and all the windows systems share using samba.

I don't us iptables on any system but my netbook.

---

### Post by Objekt on 2010-04-07
How do you manage which ports are open?  ufw or something similar?

---

### Post by uRock on 2010-04-07
> **objekt said:**
> how do you manage which ports are open?  Ufw or something similar?

gufw

---

### Post by bodhi.zazen on 2010-04-07
> **Objekt said:**
> How do you manage which ports are open?  ufw or something similar?

Depends on the service. What port is open and what access do you want ?

Port 22 is managed very different then port 80.

And what makes you think you have ports open ? How did you determine you have open ports ? What services are you running ? What access do you wish to allow or restrict ?

---

### Post by GodLikeCreature on 2010-04-07
> **yeleek said:**
> sudo iptables -L

will show you what rules you have currently.

If you've not specified any then you will probably get this

Chain INPUT (policy DROP)
target     prot opt source               destination         

Chain FORWARD (policy DROP)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

Hey, I have been using this and zenmap as tests and I am bit confused.  Out of curiosity, I wanted to find out what my machine looked like before I manually started firestarter.

When I start a new session, 

iptables -L

returns all three input, forward and output as ACCEPT.  However, zenmap tells me I only have those two ports open.  As soon as I start firestarter, though, all three input, forward and output change to DROP, but zenmap returns the same.

It just sounds confusing to me that ports remain equally closed while iptables -L returns apparently opposite results before and after firestarter is there?

Any ideas?

---

### Post by CharlesA on 2010-04-07
> **cariboo907 said:**
> I think 15 ports open is a bit excesive for a desktop system. My home server only has 6 open ports:

[list]
[*] 22 ssh
[*] 80 http
[*] 111 rpcbind
[*] 138 netbios-ssn
[*] 445 microsoft-ds
[*] 2049 nfs
[/list]

None of them are open to he world. The system is used for sharing files in a mixed network of Windows and Ubuntu. All the Ubuntu system share using nfs, and all the windows systems share using samba.

I don't us iptables on any system but my netbook.

15 open ports sounds a bit excessive to me as well.

Mine only has 5 open ports:

22 - SSH
139 - Netbios
445 - Samba
7402 - raid management
10000 - webmin

The only one that is allowed access to the internet is SSH.

> **GodLikeCreature said:**
> Hey, I have been using this and zenmap as tests and I am bit confused.  Out of curiosity, I wanted to find out what my machine looked like before I manually started firestarter.

When I start a new session, 

iptables -L

returns all three input, forward and output as ACCEPT.  However, zenmap tells me I only have those two ports open.  As soon as I start firestarter, though, all three input, forward and output change to DROP, but zenmap returns the same.

It just sounds confusing to me that ports remain equally closed while iptables -L returns apparently opposite results before and after firestarter is there?

Any ideas?

Which ports do it say are open?

I did an nmap scan on my netbook running Ubuntu 9.10 with default iptables policies in place (accept all).
No ports were open, since nothing are listening by default.

---

### Post by _GoRDoN_ on 2010-04-07
> **GodLikeCreature said:**
> Hey, I have been using this and zenmap as tests and I am bit confused.  Out of curiosity, I wanted to find out what my machine looked like before I manually started firestarter.

When I start a new session, 

iptables -L

returns all three input, forward and output as ACCEPT.  However, zenmap tells me I only have those two ports open.  As soon as I start firestarter, though, all three input, forward and output change to DROP, but zenmap returns the same.

It just sounds confusing to me that ports remain equally closed while iptables -L returns apparently opposite results before and after firestarter is there?

Any ideas?

AFAIK if you test firewall on same computer you are running zenmap on you won't get accurate results. You should run it from another computer.

---

### Post by Objekt on 2010-04-07
> **CharlesA said:**
> 15 open ports sounds a bit excessive to me as well.

Mine only has 5 open ports:

22 - SSH
139 - Netbios
445 - Samba
7402 - raid management
10000 - webmin

The only one that is allowed access to the internet is SSH.


Uh - what about port 80?  Since you are posting to a Web forum, you must have that one open as well, right?

---

### Post by bodhi.zazen on 2010-04-07
> **Objekt said:**
> Uh - what about port 80?  Since you are posting to a Web forum, you must have that one open as well, right?

No, that is not how it works.

See the first part of this :

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

---

### Post by uRock on 2010-04-07
> **Objekt said:**
> Uh - what about port 80?  Since you are posting to a Web forum, you must have that one open as well, right?

To fully understand how port filtering works you need to know how your machine makes the TCP connection.

If you scan my system, it will not respond to the port scan. However, if I go to youtube.com my system establishes the connection with that site and though the port is now open for youtube.com, it will still ignore the port scan, unless the person running the scan gets one of the packets and starts creating his own packets with a spoofed IP matching that of youtube.com along with similar sequence numbers of the packets being exchanged between my system and youtube.com. During the TCP exchange my system and youtube.com will agree on what port to open for the UDP streaming to start. 

Though the ports are open, it would be really hard for a third person to interrupt the transmission and take over the port.

I hope this helps. It is a lot to take in.

Cheers,
Ronnie

---

### Post by OpSecShellshock on 2010-04-08
Yeah, in http traffic port 80 is listening and used on the server side, but the client will use whatever port is handy to initiate the connection.

---

