---
title: "HOWTO: Set a custom firewall (iptables) and Tips [Advanced user only]"
date: 2008-01-15
forum: Tutorials
---

### Post by frodon on 2008-01-15
[B][SIZE="3"][COLOR="Red"]Disclaimer : This guide is intended to advanced users, beginners should not try to follow it and prefer the other guide i wrote on the topic which is intended to beginners :
[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)
Please, don't post questions like "which port i need to open for this apps ?" this can be found easily in /etc/services file or using google.[/COLOR][/SIZE][/B]

**[SIZE="3"]1- Introduction[/SIZE]**
Hello, i wrote a first iptables tutorial for beginners but thought that advanced users may have interest in setting a more complex firewall which filter also outgoing traffic which is a little bit more tricky because you need to know almost all the ports you use.
However this firewall will give you a really good level of security.
As another great resource you can have a look at bodhi.zazen iptables page on his website:
[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

**[SIZE="3"]2- Set your firewall script[/SIZE]**

**[SIZE="2"]2.1- Create your standard script[/SIZE]**
First read the first guide i wrote for beginners as you will need the flush script and the init.d script, we will just use another firewall script :
[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)

Once you have created your flush script and init.d script, create your firewall script :
```
sudo gedit /etc/firewall.bash
```Then paste this in it and modify the script to fit your needs :
```
#!/bin/bash

# No spoofing !!!
if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ]
then
for filtre in /proc/sys/net/ipv4/conf/*/rp_filter
do
echo 1 > $filtre
done
fi 

# No icmp
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

modprobe ip_tables
modprobe ip_nat_ftp
modprobe ip_nat_irc
modprobe ip_conntrack_irc
modprobe ip_conntrack_ftp
modprobe iptable_filter
modprobe iptable_nat 

# Remove all rules
iptables -F
iptables -X

# first set the default behaviour => accept connections
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

# New chains
iptables -N FIREWALL
iptables -N TRUSTED

# Log chain
iptables -N LOG_DROP
iptables -A LOG_DROP -j LOG --log-prefix '[IPTABLES DROP] : '
iptables -A LOG_DROP -j DROP

# Allow ESTABLISHED and RELATED incoming connection
iptables -A FIREWALL -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
# Allow self communication
iptables -A FIREWALL -i lo -j ACCEPT
iptables -A FIREWALL -o lo -j ACCEPT
# Send all package to the TRUSTED chain
iptables -A FIREWALL -j TRUSTED
# DROP all other packets
iptables -A FIREWALL -j DROP

# Send all through the FIREWALL chain
iptables -A INPUT -j FIREWALL
iptables -A FORWARD -j DROP
iptables -A OUTPUT -j FIREWALL

# Allow dns
iptables -A TRUSTED -o eth0 -p udp -m udp --dport 53 -j ACCEPT
iptables -A TRUSTED -o eth0 -p tcp -m tcp --dport 53 -j ACCEPT

# Allow http
iptables -A TRUSTED -o eth0 -p tcp -m tcp --dport 80 -m state --state NEW,ESTABLISHED -j ACCEPT

# Allow https
iptables -A TRUSTED -o eth0 -p udp -m udp --dport 443 -j ACCEPT
iptables -A TRUSTED -o eth0 -p tcp -m tcp --dport 443 -j ACCEPT

# Allow amule
iptables -A TRUSTED -i eth0 -p udp -m udp --dport 8249 -j ACCEPT
iptables -A TRUSTED -i eth0 -p udp -m udp --dport 8251 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 8248 -j ACCEPT
iptables -A TRUSTED -o eth0 -p udp -m udp --sport 8249 -j ACCEPT
iptables -A TRUSTED -o eth0 -p udp -m udp --sport 8251 -j ACCEPT
iptables -A TRUSTED -o eth0 -p tcp -m tcp --sport 8248 -j ACCEPT
#  Allow some emule servers
iptables -A TRUSTED -o eth0 -p tcp -m tcp --dport 4242 -j ACCEPT
iptables -A TRUSTED -o eth0 -p tcp -m tcp --dport 4661 -j ACCEPT
iptables -A TRUSTED -o eth0 -p tcp -m tcp --dport 3000 -j ACCEPT

#Allow IRC IDENT & DCC
iptables -A TRUSTED -o eth0 -p tcp -m tcp --dport 6667 -j ACCEPT
iptables -A TRUSTED -o eth0 -p tcp -m tcp --sport 1024:65535 --dport 1024:65535 -m state --state NEW -j ACCEPT

# Allow pop3s
iptables -A TRUSTED -o eth0 -p udp -m udp --dport 995 -j ACCEPT
iptables -A TRUSTED -o eth0 -p tcp -m tcp --dport 995 -j ACCEPT

# Allow imap2
iptables -A TRUSTED -o eth0 -p udp -m udp --dport 143 -j ACCEPT
iptables -A TRUSTED -o eth0 -p tcp -m tcp --dport 143 -j ACCEPT

# Allow imap3
iptables -A TRUSTED -o eth0 -p udp -m udp --dport 220 -j ACCEPT
iptables -A TRUSTED -o eth0 -p tcp -m tcp --dport 220 -j ACCEPT

# Allow newsgroup
iptables -A TRUSTED -o eth0 -p tcp -m tcp --dport 119 -j ACCEPT

# Allow smtp
iptables -A TRUSTED -o eth0 -p tcp -m tcp --dport 25 -j ACCEPT
iptables -A TRUSTED -o eth0 -p tcp -m tcp --dport 465 -j ACCEPT

# Allow ftp
iptables -A TRUSTED -o eth0 -p tcp -m tcp --dport 21 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A TRUSTED -o eth0 -p tcp -m tcp --dport 20 -m state --state ESTABLISHED -j ACCEPT
iptables -A TRUSTED -o eth0 -p tcp -m tcp --sport 1024:65535 --dport 1024:65535 -m state --state ESTABLISHED,RELATED -j ACCEPT

# Allow MSN
iptables -A TRUSTED -o eth0 -p tcp -m tcp --dport 1863 -j ACCEPT

# bittorrent
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 6881:6889 -j ACCEPT
iptables -A TRUSTED -o eth0 -p tcp -m tcp --sport 6881:6889 -j ACCEPT
# azureus
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 64433 -j ACCEPT
iptables -A TRUSTED -i eth0 -p udp -m udp --dport 64433 -j ACCEPT
iptables -A TRUSTED -o eth0 -p tcp -m tcp --dport 64433 -j ACCEPT
iptables -A TRUSTED -o eth0 -p udp -m udp --dport 64433 -j ACCEPT

# STEAM
iptables -A TRUSTED -o eth0 -p tcp -m tcp --dport 27020:27050 -j ACCEPT
iptables -A TRUSTED -o eth0 -p udp -m udp --dport 27000:27015 -j ACCEPT
iptables -A TRUSTED -o eth0 -p udp -m udp --dport 1200 -j ACCEPT

# enemy territory
iptables -A TRUSTED -o eth0 -p udp -m udp --dport 27950:27970 -j ACCEPT

# ekiga
iptables -A TRUSTED -o eth0 -p tcp -m tcp --sport 5000:5061 -j ACCEPT
iptables -A TRUSTED -o eth0 -p udp -m udp --sport 5000:5061 -j ACCEPT
iptables -A TRUSTED -o eth0 -p tcp -m tcp --dport 5060 -j ACCEPT
iptables -A TRUSTED -o eth0 -p udp -m udp --dport 5060 -j ACCEPT
iptables -A TRUSTED -o eth0 -p tcp -m tcp --dport 5061 -j ACCEPT
iptables -A TRUSTED -o eth0 -p udp -m udp --dport 5061 -j ACCEPT

# Teamspeak
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 8767 -j ACCEPT
iptables -A TRUSTED -o eth0 -p tcp -m tcp --dport 8767 -j ACCEPT
iptables -A TRUSTED -i eth0 -p udp -m udp --dport 8767 -j ACCEPT
iptables -A TRUSTED -o eth0 -p udp -m udp --dport 8767 -j ACCEPT

# nicotine
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 2234:2239 -j ACCEPT
iptables -A TRUSTED -o eth0 -p tcp -m tcp --dport 2234:2239 -j ACCEPT


# End message
echo " [End iptables rules setting]" 
```


**[SIZE="2"]2.2- Explanation about the script structure[/SIZE]**
Some of you may be surprised by the structure used for the script so i will explain. Rather than handling the INPUT and OUTPUT chain directly as it is most often done i use two intermediary chains called FIREWALL and TRUSTED.

I'm using this structure in the spirit to separate things and make the script more clear.

The FIREWALL chain allow loopback interface and most common input connections then send all the rest into the TRUSTED chain where you will put your more specific rules and finally drop all packets that have not been allowed by the TRUSTED chain.
So **all you don't allow explicitly in the TRUSTED chain will be dropped**.

In the script all INPUT and OUTPUT packets are sent and handled through the FIREWALL and TRUSTED chain. Because all the INPUT and OUTPUT packets are sent to the FIREWALL and TRUSTED chain i use the "**-i eth0**" command to filter an INPUT packet and the "**-o eth0**" to filter an output packet (type man iptables to get details on this command).

**[SIZE="2"]2.3- Edit the script to fit your needs[/SIZE]**

Basically you will have to open output port for each apps you use, in general this is not hard to find through google or the /etc/services file where all your common ports are listed with their function. 

**When you need to open a port just add your rules in the TRUSTED chain.**

For example if you want to open port for jabber, either you know directly the port to open and how to open it or you can just use google with "jabber iptables" has keyword and find the rules needed. On google you will find these 2 rules :
```
iptables -A INPUT -p tcp --sport 5222 -m state --state ESTABLISHED -j ACCEPT
iptables -A OUTPUT -p tcp --dport 5222 -m state --state NEW,ESTABLISHED -j ACCEPT

```
So to respect the structure of the script you will add your 2 news rules at the end of the TRUSTED chain like that :
```
iptables -A TRUSTED -i eth0 -p tcp --sport 5222 -m state --state ESTABLISHED -j ACCEPT
iptables -A TRUSTED -o eth0 -p tcp --dport 5222 -m state --state NEW,ESTABLISHED -j ACCEPT

```

*-i eth0* allow to apply the rule on the INPUT packets (incoming packet on eth0) and *-o eth0* allow to apply the rule on the OUPUT packets (outgoin packet on eth0)

Once you your script is finished, make your script executable :
```
sudo chmod +x /etc/firewall.bash
```Then make it start on boot :
```
sudo update-rc.d firewall defaults
```

You're done :)

To test your firewall you can consult the following sites :
[http://www.hackerwatch.org/probe/](http://www.hackerwatch.org/probe/)
[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)


**[SIZE="3"]3- Advanced topics[/SIZE]**


**[SIZE="2"]3.1- Create some log[/SIZE]**
To debug your firewall or maybe just if you wish some log here is how to do it using the syslog daemon.

You have surely noticed that in the script i provide a LOG_DROP chain was created, this chain will allow you to LOG the packets you dropped.
First open your syslog.conf file :
```
sudo gedit /etc/syslog.conf
```
Then add the folowing lines at the end of the file :
```
#IPTables logging
kern.debug;kern.info /var/log/firewall
```and restart the daemon :
```
sudo /etc/init.d/sysklogd restart
```Then just use LOG_DROP instead of DROP in your script everywhere you want to log dropped packets. Your log will be in /var/log/firewall.

**[SIZE="2"]3.2- Using more than one network interface[/SIZE]**
If you use more than one interface then you can either duplicate all the rules with "-i eth0" and "-o eth0" using the name of your second network interface or  use the character "+" to apply rule on all devices beginning by "eth" so this would make "-i eth+" and "-o eth+".
I have not tested the second solution, feel free to report that it is working.




This guide is not complete and limited by my own knowledge so please feel free too share your knowledge and own iptables rules so that we can improve this guide together and provide the answer to most common needs.

Hope some find this useful.

---

### Post by MaxVK on 2008-01-17
Hi there. This is an excellent firewall script, and I'm using a slightly edited version of it myself right now.

I don't fully understand 100% why you went with the TRUSTED and FIREWALL chains, but I'm starting to get there. However, I have a question:

If I wanted to deny a specific port any inbound or outbound access what would be the best way to add this?

Thanks

Max

---

### Post by frodon on 2008-01-17
I guessed some would be surprized by this organisation (TRUSTED and FIREWALL chains), the goal is mainly to separate things and keep the script well organized so that you only have to add your additional rules to the TRUSTED CHAIN, the rest is more likely to never change.
That's the idea of these 2 chains.

By default anything you don't allow explicitly in the TRUSTED chain is dropped because all INPUT and OUTPUT packets are sent to the firewall chain and you will see that all is dropped at the end of the FIREWALL chain so if you don't allow a port explicitly in the TRUSTED chain all traffic on it will be dropped.

Hope to have answered your question.

---

### Post by MaxVK on 2008-01-17
Thanks frodon, I thought that was happening but I wanted to be sure.

Yes, the TRUSTED and FIREWALL chains do seem to make sense. The reason I'm having trouble getting used to them is because I'm only just starting out with iptables, and I'm used to the usual INPUT/OUTPUT chains that appear in most of the documentation Iv found, although I think Iv learned more by reading your script that from anywhere else so far!

Great firewall!

Max

---

### Post by frodon on 2008-01-17
Thanks,

The script organisation has its advantages and disadvantages, i did choose that in the spirit to make things more clear. I will try to explain this better in the first post. Thanks for the feedback and for using the script. I'm glad it helps.

EDIT: i have added some more explanations about the structure and an example with a jabber rule, hope the use of the script is more clear now.

---

### Post by MaxVK on 2008-01-17
Sorry to keep pestering you, but I have another question. In the script I see the following:

--dport 
--destination-port
--sport

Are the first two the same thing? Iv Googled 'destination-port' and while Iv found it in a couple of scripts, Iv not found an explanation of what it actually is, whereas Iv found plenty of places that explain dport as the destination port. If they *are* the same thing, was there any particular reason that you wrote them differently?

Similarly Iv also found 'sport' in scripts, although that would appear to be source port.

Thanks

Max

---

### Post by frodon on 2008-01-17
This is explainedman page and alos in my first guide linked in first post. --dport  and --destination-port are 2 ways to use the same command and indeicates a destination port whereas --sport indicates a source port.

---

### Post by shadowtroopers on 2008-02-12
hi frodon,

I would like to add new rule on your existing firewall script based on these articles but don't know how. I'm using the script that you provided on my machine. This is the link for the articles:

[http://www.newartisans.com/blog_files/tricks.with.iptables.php](http://www.newartisans.com/blog_files/tricks.with.iptables.php)

---

### Post by frodon on 2008-02-12
Add them to the TRUSTED chain as explained in 2.3 part of the guide, there's almost nothing to change to include them.
However most of these rules sounds unnecessary to me if you don't run web servers or stuff like that.

---

### Post by gegard on 2008-02-27
I've had a couple of hours working on this and found your explanation very helpful - but I can't quite work out a couple of things for http and https: 
--- + your code
# Allow http
iptables -A TRUSTED -o eth0 -p tcp -m tcp --dport 80 -m state --state NEW,ESTABLISHED -j ACCEPT

# Allow https
iptables -A TRUSTED -o eth0 -p udp -m udp --dport 443 -j ACCEPT
iptables -A TRUSTED -o eth0 -p tcp -m tcp --dport 443 -j ACCEPT
--- - your code

1) Why do the rules for http and https differ? Does http have no udp element?

2) Is the direction incorrect? Your lines don't work for me until I replace -o with -i.

Thanks for any pointers on this.

Regards,
Geoff

---

### Post by frodon on 2008-02-27
1) i can't explain you why but it seems that it is the case as i never needed any udp port for http neither saw any iptables rule opening an UDP port for http.

2) You shouldn't need to open any input port for https, these rules are working fine for me. What https website give you problems with these rules ? Give me a link so i can test it on my computer since i use the same rules.

---

### Post by gegard on 2008-02-28
Thank you for your reply.

> **frodon said:**
> 1) i can't explain you why but it seems that it is the case as i never needed any udp port for http neither saw any iptables rule opening an UDP port for http.

I can't find the reference now but I think I saw yesterday that https needs udp for some kinds of negotiation - so I now assume that this means http **doesn't** require it, as you say.

However, I still don't really understand why http has the bit '-m state --state NEW,ESTABLISHED' rather than '-m tcp'. What other states are being dropped in http that are not being dropped in https?

> **frodon said:**
> 2) You shouldn't need to open any input port for https, these rules are working fine for me. What https website give you problems with these rules ? Give me a link so i can test it on my computer since i use the same rules.

I haven't got this on an external server yet, but I hope to do so in the next few days. I can confirm that I have had to make both http and https rules into **-i** rather than **-o**.

Regards,
Geoff

---

### Post by frodon on 2008-02-28
> **gegard said:**
> I haven't got this on an external server yet, but I hope to do so in the next few days. I can confirm that I have had to make both http and https rules into **-i** rather than **-o**.

Regards,
GeoffIf you are not hosting webserver you shouldn't need to open anything on INPUT packets for http and https the less input ports you allow the better.
You some things to test regarding this as these rules are pretty common and should work without any problem. 

Did you modify some parts of the script ? 
because the "iptables -A FIREWALL -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT" should already deal with all these input packets without the need of any additional rule at least for http and https.

---

### Post by shadowtroopers on 2008-02-29
hi
just wondering..how am i going to intergrate moblock to the script?

---

### Post by frodon on 2008-02-29
I don't know, it mainly depends how moblocks set rules. Depending of the apps which motivate you to run moblock you have some other alternatives, many apps have plugins to do blocks these IPs at the apps level like the "safepeer" azureus plugin do.
If Moblock don't play well with this script you can still try ipblock :
[http://ubuntuforums.org/showthread.php?t=530183](http://ubuntuforums.org/showthread.php?t=530183)

Anyway if i remember well what users told with my other iptable tutorial for beginners moblock should work if started after the firewall script :
[http://ubuntuforums.org/showpost.php?p=2058230&postcount=79](http://ubuntuforums.org/showpost.php?p=2058230&postcount=79)

---

### Post by shadowtroopers on 2008-03-01
Hi,
Let's say i would like to try another type of firewall for comparison how to completely disable / uninstall this firewall.. My intention just don't want any conflicts on my iptables.

---

### Post by frodon on 2008-03-02
If you want to uninstall the scripts you can just delete the created scripts or if you just want to disable it comment all the lines of the /etc/init.d/firewall script and reboot.

---

### Post by gegard on 2008-03-03
My sceniario is a web server using both HTTP and HTTPS, with an SSL login. I've got a reverse proxy running and various other ports in use that I want to protect using iptables. The only inputs and outputs I want are on 22, 80 and 443. I don't want outputs from other ports to get outside, nor to receive traffic on other ports.

> **frodon said:**
> Did you modify some parts of the script ? 
because the "iptables -A FIREWALL -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT" should already deal with all these input packets without the need of any additional rule at least for http and https.
The more I think about it, the further from understanding I think I become! So I'll read other resources to get a wider view of iptables. Sorry for my increasing (awareness of) ignorance.

Thank you for your replies.

Regards,
Geoff

---

### Post by frodon on 2008-03-03
Ha ok you should have told first that you are using http, https servers as in this case you need indeed to open the port as input too.

You should only need to add a line per port to allow input traffic on the 3 ports you use for your server, for https it would be :
```
iptables -A TRUSTED -i eth0 -p udp -m udp --dport 443 -j ACCEPT
```

---

### Post by gegard on 2008-03-03
> **frodon said:**
> Ha ok you should have told first that you are using http, https servers as in this case you need indeed to open the port as input too.
That explains it! Thank you for your help.

Regards,
Geoff

---

### Post by jimx on 2008-05-29
Hello,
I want to ask if this script can be used with two interfaces:one eth0 internet and another one eth1 lan,so from eth1 other hosts in the lan can 
browse internet and use p2p programs.

Thanks in advance and keep on going helping other people with your knowledge.
Thanks again.

---

### Post by her_meth on 2008-11-05
Actually this a mighty good proposal my friend.
two interfaces is what i also need, have been mesing with it 2 days now, the way of noob is heavy :guitar:

so far i have tried  to add
[HTML]iptables -A FORWARD -o eth1 -i eth0 -j ACCEPT 
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE 
echo 1 > /proc/sys/net/ipv4/ip_forward 
iptables -A FORWARD -j DROP[/HTML]
as well as
```
iptables -A FIREWALL-o eth1 -i eth0 -j ACCEPT 
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE 
echo 1 > /proc/sys/net/ipv4/ip_forward 
iptables -A FIREWALL -j DROP
```

whell forwarding goes trough, but any other roule as http allow and others dont apply 
[HTML]root@triber:~# /etc/init.d/firewall status
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
ACCEPT     all  --  192.168.0.0/24       anywhere            state NEW
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination
MASQUERADE  all  --  anywhere             anywhere

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination[/HTML]

So if OP or iptables guru´s could find time to respond  me and many others would really appreciate  it.

---

### Post by frodon on 2008-11-05
The best in this case if you don't want to forward all is to add a FORWARD rule for each traffic you want to forward then DROP the rest instead of forwarding all with your first forward rule.
Handling forward rules separately looks more clean IMO as your firewall and what you forward are 2 different things.

For ex if you want to  forward web :
```
iptables -A FORWARD -o eth1 -i eth0 --sport 80 --dport 80 -j ACCEPT 
```

---

### Post by her_meth on 2008-11-05
Thanx for quick reply Frodon, will try it today

---

### Post by Samurai- on 2008-11-14
Hello, i ve found this to be wonderfull, i understand chains now and how they work..

I only have one question, for example what does NEW, ESTABLISHED, RELATED actually means, or should i ask how is it handled..

iptables -A FIREWALL -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT

iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 51000 -j ACCEPT


For example, FIREWALL chain allows all connections that are established and related under TRUSTED. Trusted then allows all connections, tcp, on this port..

What i dont understand is how people can still upload from me, that is that they connect on me, shouldnt i add NEW as well, or is torrent connection actually RELATED, and if so, what does that mean? Or torrents, since i need to establish connection with other people with the same file as well, goes under ESTABLISHED so it gets through?

And i would also like to know what this -m tcp means..  Does maybe this -m tcp tells to allow all NEW RELATED AND ESTABLISHED connection?


I would like to know when to add this NEW parameter ... Is new meant for things like -> if an unknown ip connects to your service, and then enters username password, and if sucsess, it is ESTABLISHED?


EDIT: For example i didnt allow input http on 80 port.. So how come i can browse ? I receive input from page as well.. Or does that mean since i asked for a page, like google, i connected and that connection became established, so it gets through ? Or things like browsing goes under OUT only and since i allow all i can send requests and receive data no problems ?

---

### Post by frodon on 2008-11-14
Simple, any connection you open yourself (eg web browser) is allowed thanks to the established and related rules.

Never wondered why you can browse internet behind a NAT router without redirecting port 80 on your computer ?
It's the same principle here browsing a site you open a connection on port 80 and then receive an answer from the website and in the frame you receive you have in the header all the infos telling that the frame is the answer from your request. Once this done you have an ESTABLISHED connection, RELATED connection are connections that may need to be opened from your established connection.

As a general rule you never need to accept input connection except if you are running a service. Because in this case your computer receive an unkown frame and is the service that provide the answer of this request made by a remote computer (eg you run a web server).

---

### Post by Samurai- on 2008-11-14
> **frodon said:**
> Simple, any connection you open yourself (eg web browser) is allowed thanks to the established and related rules.

Never wondered why you can browse internet behind a NAT router without redirecting port 80 on your computer ?
It's the same principle here browsing a site you open a connection on port 80 and then receive an answer from the website and in the frame you receive you have in the header all the infos telling that the frame is the answer from your request. Once this done you have an ESTABLISHED connection, RELATED connection are connections that may need to be opened from your established connection.

As a general rule you never need to accept input connection except if you are running a service. Because in this case your computer receive an unkown frame and is the service that provide the answer of this request made by a remote computer (eg you run a web server).

Holy ****, fast answer..

Thanks, jea, i have just been reading this page, which might help others who dont understand..

[http://www.kalamazoolinux.org/presentations/20010417/conntrack.html](http://www.kalamazoolinux.org/presentations/20010417/conntrack.html)

I understand now perfectly and i agree with > As a general rule you never need to accept input connection except if you are running a service. Because in this case your computer receive an unkown frame and is the service that provide the answer of this request made by a remote computer (eg you run a web server).

one thing left

iptables -A FIREWALL -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT

iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 51000 -j ACCEPT


what does that -m tcp means..  its not under man iptables :/



EDIT:

for example, if i have SSHD server up on 4444 port, and would like to connect from some other machine through SSH to my machine, if i put this

iptables -A TRUSTED -o eth0 -p tcp -m tcp --dport 4444 -m state --state NEW -j ACCEPT


Would that allow incomming connection? 

or would it be blocked here already, since its not established :\

iptables -A FIREWALL -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT

If so, how do i need to write it if wish to have SSHD connectable from outside

---

### Post by frodon on 2008-11-14
It's the mangle table of netfilter (netfilter is the firewall embedded in the kernel iptables being the tool to configure it), i'm not expert of this part.
But in some way it's like defining the protocol used if that could help you to understand.

---

### Post by Samurai- on 2008-11-14
> **Samurai- said:**
> 


EDIT:

for example, if i have SSHD server up on 4444 port, and would like to connect from some other machine through SSH to my machine, if i put this

iptables -A TRUSTED -i eth0 -p tcp -m tcp --sport 4444 -m state --state NEW -j ACCEPT


Would that allow incomming connection? 

or would it be blocked here already, since its not established :\

iptables -A FIREWALL -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT

If so, how do i need to write it if wish to have SSHD connectable from outside

Ok, i think that things would go like this

It would check chain INPUT and would say it wont go through, then it would check input on local and its not right, then it would check TRUSTED chain and since there is NEW specified there on -i , it should allow connection, right?

it wouldnt be droped...


EDIT: jeah i talk to my self, i understand now how this thing works, i only started on iptables today, yesterday  i didnt even know what it is..  Only thing i ll need to test is if i need to add -m -> NEW or i can just accept connections to that port and all are NEW by default..

anyway, great work here>..

---

### Post by xinix on 2008-12-14
So I'm trying to configure a system to accept connections from my laptop's wireless connection.  The problem is that my ip is constantly changing so it's not just a matter of allowing that ip to connect.  I have no way of getting a fixed ip (university network) so I had hoped to find another way to do this.  I thought I could allow/deny by MAC address, and tried this command:
```
iptables -A INPUT --mac-source xx:xx:xx:xx:xx:xx -j ACCEPT
```
I get this error: iptables v1.3.8: Unknown arg `--mac-source'

Any suggestions on how I can do this?

Thanks

---

### Post by stedevil on 2008-12-26
> **xinix said:**
> 
```
iptables -A INPUT --mac-source xx:xx:xx:xx:xx:xx -j ACCEPT
```
I get this error: iptables v1.3.8: Unknown arg `--mac-source'

Any suggestions on how I can do this?

Thanks

try something like
```

iptables -A INPUT -m mac --mac-source xx:xx:xx:xx:xx:xx -j ACCEPT
```

---

### Post by stedevil on 2008-12-26
Thanks for these 2 guides I now have set up in/out filtering and logging... :)

So, now how do I figure out which software is **actually** using/sending/listening to a specific port? Eg I periodically have outgoing packages on port 10694 to various IPs, how do I figure out which software is responsible for doing this? Would be quite helpful in determining what traffic to allow.

---

### Post by kevdog on 2008-12-26
Firewalls do not filter by application.  Possibly netstat may help you.

---

### Post by stedevil on 2008-12-27
Ahh, netstat -tunap seem to do exactly what I was looking for :)
Thanks :)

---

### Post by Master One on 2009-01-24
```

iptables -A FIREWALL -j TRUSTED     # Send all package to the TRUSTED chain
iptables -A FIREWALL -j DROP        # DROP all other packets
```
As far as I understand it, the second line with dropping all packets from the FIREWALL chain is never reached, because you send all packets to the TRUSTED chain before that, so there is no dropping of any other packets, because that rule is never reached by any packet.

Or am I wrong with this assumption (I'm just starting with iptables knowledge)?

---

### Post by frodon on 2009-01-26
Packets are sent to the RUSTED chain where they have a chance to get allowed then they are DROPED at the end of the FIREWALL chain.

So you are a bit wrong with your assumption thinking that the DROP line is never reached. You can see this TRUSTED chain as a function or an include in standard programing language.

---

### Post by Master One on 2009-01-26
Oh, I see. Thanks for clarifying, because I indeed was totally wrong, which would have caused a major headache when playing around with my own iptables script.

Somehow I was in the opinion, that once sent to a user defined chain, it would never come back to the parent chain (I must have been confused by some examples working with the -j RETURN target).

Now I also can see the advantage, using your structure with FIREWALL and TRUSTED user defined chains.

---

### Post by akkumaru on 2009-05-06
hi all,

i just start learning iptables and i've found this article is very useful!
thanks, frodon! :)

however, i still don't quite understand how the chain works,
when i write some iptables rules, which rule would be applied first?
is it the first written? or..?

i hope someone can depict this for me,, please,,


at the moment i try to set up a gateway (Internet Connection Sharing) in an Ubuntu box:

[internet]<--->[eth1::gateway::eth0]<--->[clients]

i would like to know how do i integrate frodon's firewall script to the ICS script,
so far, this is my script (i found this script from [https://help.ubuntu.com/community/Internet/ConnectionSharing#Gateway%20set%20up]("https://help.ubuntu.com/community/Internet/ConnectionSharing#Gateway%20set%20up")):

```

iptables -A FORWARD -i eth1 -o eth0 -s 192.168.0.0/24 -m state --state NEW -j ACCEPT
iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A POSTROUTING -t nat -j MASQUERADE

```

i wonder if i add the FIREWALL script, then change the word 'ACCEPT' above to word 'FIREWALL',

e.g.
```

..
iptables -A FORWARD -i eth1 -o eth0 -s 192.168.0.0/24 -m state --state NEW -j FIREWALL
..

```

will the firewall script also works for the clients?
if it won't, how should i accomplish this?

thanks,

---

### Post by akkumaru on 2009-05-19
i tried what i suggested before,
well, i can not tell if the clients are firewalled too,,
but their internet access are not blocked,,

---

### Post by frodon on 2009-05-19
I would in your case handle the FORWARD chain directly as you may want to have different rules for the gateway computer itself and for the forwarded internet connection.
Connection sharing is a specific topic so i think it better to handle the FORWARD chain separately to avoid confusing an unexpected behaviour.

---

### Post by Randomperson_1000 on 2009-06-17
typo

"2.2- Explanation about the script structure
Some of you may be surprised by the structure used for the script so i will explain. Rather than handling the INPUT and OUTPUT chain directly as it is most often done i use **tow** intermediary chains called FIREWALL and TRUSTED."

u meant two didnt u? i was initially confused there thinking wtf is tow.

thanks this is a really good script, really helped me applying all the rules.

quick q. how is icmp treated. Does the no icmp bit at the start of the script drop icmp packets or reject.

also this rule: 
iptables -I INPUT -p tcp -m state --state NEW -m limit --limit 30/minute --limit -burst 5 -j ACCEPT

I would include in the script as?:
iptables -I TRUSTED -p tcp -m state --state NEW -m limit --limit 30/minute --limit -burst 5 -j ACCEPT

would it be able to limit acks i know there are scanners out there that can send acks to ports and which reply wich werent expecting one and reply with rest(and the scanner then knows som1 is at the ip address). I think its already implemented in the script or would i have to add --tcp-flags SYN,ACK,RST SYN to most of the rules?

thanks again fo rthis guide ive hit firestarters limitations and this has really helped

---

### Post by frodon on 2009-06-18
Thanks for pointing out my typo :)

Yes the icmp bit deactivate all icmp stuff so you are sure to not accept any icmp traffic.
For your second question i have no answer because i never gave this a thought. But to get an answer the packet would have to be allowed to go through the output filtering which is less likely to happen IMO. Anyway to best way would just be to make some test, maybe nmap could be enough for this purpose.
When adding rules to the TRUSTED chain you must tell if it is applied on input packets (-i eth0) or output packets (-o eth0) if you don't specify it the rule will apply on both.

Anyway if you digg on the question and get a clear answer to your question please share it, i would be pleased to add your contribution to the tutorial.

---

### Post by Randomperson_1000 on 2009-06-18
i guess i should 1st learn the basics for some reason after a day of hair pulling i cant torrent

i want utorrent to use only one port(in wine for some reason it opens up any port it can)
ive set up the rules like this:

iptables -A TRUSTED -i wlan1 -p tcp -m tcp --sport 61224 -j ACCEPT 
iptables -A TRUSTED -o wlan1 -p dup -m udp --sport 61224 -j ACCEPT

this should allow in and out connections on wlan1 where the connections are going in and out from port 61224 but when i do this the port doesnt open nmap shows it as filtered and the port is correctly forwarded on my router everything works fine when i flush the rules or change the policy to default allow out traffic
any suggestions how i would open this port and limit it to send info from just port 61224 i.e listening and sending on that port. Ive even tried the rules u suggested in your script and below where it sys how to open new ports but still the port doesnt open

---

### Post by frodon on 2009-06-19
First if you want to test your config with nma you must do it from another computer it will prevent many common mistakes.

Here is an example of opening port for azureus :
# azureus
> iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 34333 -j ACCEPT
iptables -A TRUSTED -i eth0 -p udp -m udp --dport 34333 -j ACCEPT
iptables -A TRUSTED -o eth0 -p tcp -m tcp --dport 34333 -j ACCEPT
iptables -A TRUSTED -o eth0 -p udp -m udp --dport 34333 -j ACCEPTYou need to open the port you use in tcp and udp, as input and as ouput.

Never use sport for an incoming connection filtering except if you are sure of what you do. In most cases you will only need dport. Allowing incoming connection with sport xxxx means that you accept connection from a distant computer which sent a frame from port xxxx even if the targeted is yyyy. At home i only use sport for some output filtering but never for input filtering.

---

### Post by Randomperson_1000 on 2009-06-19
it still doesnt work for the moment just so i can use torrent i have allowed outgoing traffic by default.

for some reason when i run nmap from my computer it shows that the port is open but on my router it is still filtered. The port has been forwarded correctly. Everything works fine when I allow outgoing by default or even if i use firestarter, do u have any ideas what could be wrong.

I was thinking maybe i have to load some extra modules at the start of the script maybe ipwireless (i think this is another module) im using wireless. Or maybe i have to use another command like PREROUTING an example is here:
[http://www.linuxforums.org/forum/linux-networking/30261-iptables-port-forwarding.html](http://www.linuxforums.org/forum/linux-networking/30261-iptables-port-forwarding.html)

btw thanks for all your help so far

---

### Post by frodon on 2009-06-20
Wait a minute you still have firestarter installed ? If it's the case the behaviour of the firewall may be unpredictable.

As the script allow loopback traffic, nmap results are not trustable if nmap is run from the computer on which the firewall to test is.

I'm 100% sure the lines i gave you for your torrent client works as i used them myself and they have always worked great. If you don't mind post your iptables script so i can have a look at it.

PREROUTING rules are useful for connection sharing otherwise you should not need them.

Anyway don't worry, setting output filtering is always more tricky as you need to know exactly what to allow and why you allow it, however it will give you real knowledge :)

---

### Post by Randomperson_1000 on 2009-06-20
well here it is ive commented out the stuff i dont use. I dont have firestarter running i removed it and the rules of the script are loaded up at startup. Im going to test nmap with another comp. as soon as possible.

#!/bin/bash

# No spoofing !!!
if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ]
then
for filtre in /proc/sys/net/ipv4/conf/*/rp_filter
do
echo 1 > $filtre
done
fi 

# No icmp
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

modprobe ip_tables
modprobe ip_nat_ftp
modprobe ip_nat_irc
modprobe ip_conntrack_irc
modprobe ip_conntrack_ftp
modprobe iptable_filter
modprobe iptable_nat
# added next modprobe for troubleshooting 
modprobe ipwireless
# Remove all rules
iptables -F
iptables -X

# first set the default behaviour => accept connections
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

# New chains
iptables -N FIREWALL
iptables -N TRUSTED

# Log chain
iptables -N LOG_DROP
iptables -A LOG_DROP -j LOG --log-prefix '[IPTABLES DROP] : '
iptables -A LOG_DROP -j DROP

# Allow ESTABLISHED and RELATED incoming connection
iptables -A FIREWALL -i wlan1 -m state --state ESTABLISHED,RELATED -j ACCEPT
# Allow self communication
iptables -A FIREWALL -i lo -j ACCEPT
iptables -A FIREWALL -o lo -j ACCEPT
# Send all package to the TRUSTED chain
iptables -A FIREWALL -j TRUSTED
# DROP all other packets
iptables -A FIREWALL -j DROP

# Send all through the FIREWALL chain
iptables -A INPUT -j FIREWALL
iptables -A FORWARD -j DROP
iptables -A OUTPUT -j FIREWALL

# Allow dns
iptables -A TRUSTED -o wlan1 -p udp -m udp --dport 53 -j ACCEPT
iptables -A TRUSTED -o wlan1 -p tcp -m tcp --dport 53 -j ACCEPT

# Allow http
iptables -A TRUSTED -o wlan1 -p tcp -m tcp --dport 80 -m state --state NEW,ESTABLISHED -j ACCEPT

# Allow https
iptables -A TRUSTED -o wlan1 -p udp -m udp --dport 443 -j ACCEPT
iptables -A TRUSTED -o wlan1 -p tcp -m tcp --dport 443 -j ACCEPT

#Allow IRC IDENT & DCC
iptables -A TRUSTED -o wlan1 -p tcp -m tcp --dport 6667 -j ACCEPT
#iptables -A TRUSTED -o eth0 -p tcp -m tcp --sport 1024:65535 --dport 1024:65535 -m state --state NEW -j ACCEPT

# Allow pop3s
iptables -A TRUSTED -o wlan1 -p udp -m udp --dport 995 -j ACCEPT
iptables -A TRUSTED -o wlan1 -p tcp -m tcp --dport 995 -j ACCEPT

# Allow imap2
#iptables -A TRUSTED -o eth0 -p udp -m udp --dport 143 -j ACCEPT
#iptables -A TRUSTED -o eth0 -p tcp -m tcp --dport 143 -j ACCEPT

# Allow imap3
#iptables -A TRUSTED -o eth0 -p udp -m udp --dport 220 -j ACCEPT
#iptables -A TRUSTED -o eth0 -p tcp -m tcp --dport 220 -j ACCEPT

# Allow newsgroup
#iptables -A TRUSTED -o eth0 -p tcp -m tcp --dport 119 -j ACCEPT

# Allow smtp
#iptables -A TRUSTED -o eth0 -p tcp -m tcp --dport 25 -j ACCEPT
#iptables -A TRUSTED -o eth0 -p tcp -m tcp --dport 465 -j ACCEPT

# Allow ftp
iptables -A TRUSTED -o wlan1 -p tcp -m tcp --dport 21 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A TRUSTED -o wlan1 -p tcp -m tcp --dport 20 -m state --state ESTABLISHED -j ACCEPT
# iptables -A TRUSTED -o wlan1 -p tcp -m tcp --sport 1024:65535 --dport 1024:65535 -m state --state ESTABLISHED,RELATED -j ACCEPT

# Allow MSN
iptables -A TRUSTED -o wlan1 -p tcp -m tcp --dport 1863 -j ACCEPT

# bittorrent
iptables -A TRUSTED -i wlan1 -p tcp -m tcp --dport 52197 -j ACCEPT
iptables -A TRUSTED -i wlan1 -p udp -m udp --dport 52197 -j ACCEPT
iptables -A TRUSTED -o wlan1 -p tcp -m tcp --dport 52197 -j ACCEPT
iptables -A TRUSTED -o wlan1 -p udp -m udp --dport 52197 -j ACCEPT 
# azureus
#iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 64433 -j ACCEPT
#iptables -A TRUSTED -i eth0 -p udp -m udp --dport 64433 -j ACCEPT
#iptables -A TRUSTED -o eth0 -p tcp -m tcp --dport 64433 -j ACCEPT
#iptables -A TRUSTED -o eth0 -p udp -m udp --dport 64433 -j ACCEPT

# STEAM
#iptables -A TRUSTED -o eth0 -p tcp -m tcp --dport 27020:27050 -j ACCEPT
#iptables -A TRUSTED -o eth0 -p udp -m udp --dport 27000:27015 -j ACCEPT
#iptables -A TRUSTED -o eth0 -p udp -m udp --dport 1200 -j ACCEPT

# enemy territory
#iptables -A TRUSTED -o eth0 -p udp -m udp --dport 27950:27970 -j ACCEPT

# ekiga
#iptables -A TRUSTED -o eth0 -p tcp -m tcp --sport 5000:5061 -j ACCEPT
#iptables -A TRUSTED -o eth0 -p udp -m udp --sport 5000:5061 -j ACCEPT
#iptables -A TRUSTED -o eth0 -p tcp -m tcp --dport 5060 -j ACCEPT
#iptables -A TRUSTED -o eth0 -p udp -m udp --dport 5060 -j ACCEPT
#iptables -A TRUSTED -o eth0 -p tcp -m tcp --dport 5061 -j ACCEPT
#iptables -A TRUSTED -o eth0 -p udp -m udp --dport 5061 -j ACCEPT

# Teamspeak
#iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 8767 -j ACCEPT
#iptables -A TRUSTED -o eth0 -p tcp -m tcp --dport 8767 -j ACCEPT
#iptables -A TRUSTED -i eth0 -p udp -m udp --dport 8767 -j ACCEPT
#iptables -A TRUSTED -o eth0 -p udp -m udp --dport 8767 -j ACCEPT

# nicotine
#iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 2234:2239 -j ACCEPT
#iptables -A TRUSTED -o eth0 -p tcp -m tcp --dport 2234:2239 -j ACCEPT

# whois 
iptables -A TRUSTED -o wlan1 -p tcp -m tcp --dport 43 -j ACCEPT

# telnet
iptables -A TRUSTED -o wlan1 -p tcp -m tcp --dport 23 -m state --state NEW,ESTABLISHED -j ACCEPT

# End message
echo " [End iptables rules setting]"

okay just to clarify somethng if i change all output to TRUSTED then everything works fine seems theres some output problems when i run netstat it does ineed say that the port for bitorrent it is listening on.

---

### Post by frodon on 2009-06-20
Hum, all seems fine, your torrent client should work well on port 52197.

As a powerful debug solution you can replace "iptables -A FIREWALL -j DROP" by "iptables -A FIREWALL -j LOG_DROP" to log droped packets (instructions in first post). So that you will be able to see the packets rejected and hopefully understand which port need to be opened.

But once again i find it strange that your torrent client don't work as these are really simple rules.

---

### Post by Randomperson_1000 on 2009-06-20
i think i got it working canyouseeme.org reports so 

well im not sure but all i did was start logging ( i had set up logging b4 but never used it) i included the line u told me and it started working

when i remove that line it stops working weird i think i might disable logging and then see if the script works. 

utorrent still reports the port isnt forwarded but im dl and ul at full speeds. Tried deluge which reports everything is okay. Im getting alot of dropped packets though going to have to investigate. I think im going to switch clients to deluge utorrent seems to be messing up a bit

thanks for all your help iptables dont seem that complicated anymore and thanks for the super fast replies :D

---

### Post by toloykhan on 2010-10-16
hello there , I am new in ubuntu and security and just hit this tutorial,
 this is really interesting and very helpful tutorial .... I have a little question ... Is No spoofing in the following lines is as same functionality as in your script? , If so hope you explain that to me 
# anti spoofing rule
    $IPTABLES -N In_RULE_0
    for i_eth0 in $i_eth0_list
    do
    test -n "$i_eth0" && $IPTABLES -A INPUT  -i eth0   -s $i_eth0   -j In_RULE_0 
    done
    $IPTABLES -A INPUT  -i eth0   -s 192.168.1.1   -j In_RULE_0
    $IPTABLES -A INPUT  -i eth0   -s 192.168.1.0/24   -j In_RULE_0
    for i_eth0 in $i_eth0_list
    do
    test -n "$i_eth0" && $IPTABLES -A FORWARD  -i eth0   -s $i_eth0   -j In_RULE_0 
    done
    $IPTABLES -A FORWARD  -i eth0   -s 192.168.1.1   -j In_RULE_0
    $IPTABLES -A FORWARD  -i eth0   -s 192.168.1.0/24   -j In_RULE_0
    $IPTABLES -A In_RULE_0  -j LOG  --log-level info --log-prefix "RULE 0 -- DENY "
    $IPTABLES -A In_RULE_0  -j DROP

thanx

---

### Post by toloykhan on 2010-10-16
and another question ... I wrote the script and make it executable but nothing change ... the firewall wasn't work successfully ... so I need your help ... another thing that i replace the eth0 with my USB DataCard path which is : /dev/ttyUSB0 ...
can that make any different ...

---

### Post by duesentriebchen on 2012-07-21
Dear Frodon.

Thank you very much for your tutorial!!!
It is hard to find a detailed "howto" like yours, nearly impossible!!!

I do have one question, ergo one proposal.
Why are we dropping all other packets. In order to prevent some badguys from brutforcing, i found this [http://http://blog.zioup.org/2008/iptables_recent/](http://http://blog.zioup.org/2008/iptables_recent/)

Take a look at it, it´s very interesting. I would like to hear your oppinion on this one.

thanks :)

---

### Post by JKyleOKC on 2012-07-21
That link does not work. Attempting to correct it takes me to Google...

Here's the correct one: [http://blog.zioup.org/2008/iptables_recent/](http://blog.zioup.org/2008/iptables_recent/)

---

### Post by duesentriebchen on 2012-07-22
Good morning.

Thank´s :)
It seems, that i was in a hurry

---

### Post by duesentriebchen on 2012-07-28
Dear frodon.

I try to run your script on a small server.
i need the following services
FTP 20/21
SSH 22
HTTP 80
HTTPS 443

If i run your script, i can not connect to the server, neither is the HTTP service reachable. would you be so kind to help me on this 

please find the script in below

cat /etc/firewall.bash
#!/bin/bash

# ftp.service
# No spoofing !!!
if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ]
then
for filtre in /proc/sys/net/ipv4/conf/*/rp_filter
do
echo 1 > $filtre
done
fi 

# No icmp
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

modprobe ip_tables
modprobe ip_nat_ftp
modprobe ip_nat_irc
modprobe ip_conntrack_irc
modprobe ip_conntrack_ftp
modprobe iptable_filter
modprobe iptable_nat 

# Remove all rules
iptables -F
iptables -X

# first set the default behaviour => accept connections
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

# New chains
iptables -N FIREWALL
iptables -N TRUSTED

# Log chain
iptables -N LOG_DROP
iptables -A LOG_DROP -j LOG --log-prefix '[IPTABLES DROP] : '
iptables -A LOG_DROP -j DROP

# Allow ESTABLISHED and RELATED incoming connection
iptables -A FIREWALL -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
# Allow self communication
iptables -A FIREWALL -i lo -j ACCEPT
iptables -A FIREWALL -o lo -j ACCEPT
# Send all package to the TRUSTED chain
iptables -A FIREWALL -j TRUSTED
# DROP all other packets
iptables -A FIREWALL -j DROP

# Send all through the FIREWALL chain
iptables -A INPUT -j FIREWALL
iptables -A FORWARD -j DROP
iptables -A OUTPUT -j FIREWALL

# Allow ssh
iptables -A TRUSTED -i eth0 -p udp -m udp --sport 22 -j ACCEPT
iptables -A TRUSTED -o eth0 -p udp -m udp --dport 22 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --sport 22 -j ACCEPT
iptables -A TRUSTED -o eth0 -p tcp -m tcp --dport 22 -j ACCEPT

# Allow dns
iptables -A TRUSTED -o eth0 -p udp -m udp --dport 53 -j ACCEPT
iptables -A TRUSTED -o eth0 -p tcp -m tcp --dport 53 -j ACCEPT

# Allow http
iptables -A TRUSTED -i eth0 -p tcp -m tcp --sport 80 -j ACCEPT
iptables -A TRUSTED -o eth0 -p tcp -m tcp --dport 80 -m state --state NEW,ESTABLISHED -j ACCEPT

# Allow https
iptables -A TRUSTED -i eth0 -p udp -m udp --sport 443 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --sport 443 -j ACCEPT
iptables -A TRUSTED -o eth0 -p udp -m udp --dport 443 -j ACCEPT
iptables -A TRUSTED -o eth0 -p tcp -m tcp --dport 443 -j ACCEPT

# Allow FTP
iptables -A INPUT -i eth0 -p tcp -m tcp --sport 21 -m state --state ESTABLISHED -j ACCEPT 
iptables -A INPUT -i eth0 -p tcp -m tcp --sport 20 -m state --state ESTABLISHED,RELATED -j ACCEPT 
iptables -A INPUT -i eth0 -p tcp -m tcp --sport 1024:65535 --dport 1024:65535 -m state --state ESTABLISHED -j ACCEPT 
iptables -A OUTPUT -o eth0 -p tcp -m tcp --dport 21 -m state --state NEW,ESTABLISHED -j ACCEPT 
iptables -A OUTPUT -o eth0 -p tcp -m tcp --dport 20 -m state --state ESTABLISHED -j ACCEPT 
iptables -A OUTPUT -o eth0 -p tcp -m tcp --sport 1024:65535 --dport 1024:65535 -m state --state ESTABLISHED,RELATED -j ACCEPT

# End message
echo " [End iptables rules setting]"


_**I got a connection to my server, only with the following configuration**_
iptables -A TRUSTED -i eth0 -p tcp -m tcp --sport 20:65535 -j ACCEPT
iptables -A TRUSTED -o eth0 -p tcp -m tcp --dport 20:65535 -j ACCEPT

Can you please explain me, why a specific port/service configuration does not work?

Kind regards

---

### Post by duesentriebchen on 2012-07-30
Dear Frodon :guitar:

I got my iptables working on a ubuntu 12.04LTS server.
Thank you very much for your inspiration on this topic :popcorn:

I finally do some kind of understand basic iptable configuration :P
I want to share this knowledge in the script down below.

My server is running the following services
FTP 20/21
SSH 22
DNS 53
HTTP 80
HTTPS 443

For the portscan and ssh brute force defense i added the module
```
ipt_recent
```I did not restrict the outbound traffic, due to the use of acting as a relay for TOR and i2p

```
#!/bin/bash

# ftp.service.1
# No spoofing !!!
if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ]
then
for filtre in /proc/sys/net/ipv4/conf/*/rp_filter
do
echo 1 > $filtre
done
fi 

# No icmp
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

modprobe ip_tables
modprobe ip_nat_ftp
modprobe ip_nat_irc
modprobe ip_conntrack_irc
modprobe ip_conntrack_ftp
modprobe iptable_filter
modprobe iptable_nat
modprobe ipt_recent

# Remove all rules
iptables -F
iptables -X

# first set the default behaviour => accept connections
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

# New chains
iptables -N FIREWALL
iptables -N TRUSTED
iptables -N BADGUY

# Log chain
iptables -N LOG_DROP
iptables -A LOG_DROP -j LOG --log-prefix '[IPTABLES DROP] : '
iptables -A LOG_DROP -j DROP

# Block any packet from IP-addresses that are present in the badguys list for one hour - port scan
#iptables -A FIREWALL -i $OUTS -m recent --name badguys --update --seconds 3600 -j LOG_DROP
# Allow NEW, ESTABLISHED and RELATED incoming connection
iptables -A FIREWALL -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
# Allow self communication
iptables -A FIREWALL -i lo -j ACCEPT
iptables -A FIREWALL -o lo -j ACCEPT
# Send all package to the TRUSTED chain
iptables -A FIREWALL -j TRUSTED
# Send all DROP package from FIREWALL chain to the badguys list - port scan
#iptables -A FIREWALL -t filter -i $OUTS -j LOG_DROP -m recent --set --name badguys
# DROP all other packets
iptables -A FIREWALL -j LOG_DROP

# Send all through the FIREWALL chain
iptables -A INPUT -j FIREWALL
iptables -A FORWARD -j LOG_DROP
iptables -A OUTPUT -j FIREWALL

# SSH brute force attacks - verify in /proc/net/ipt_recent files badguys and ssh
#iptables -t filter -I BADGUY -m recent --set --name badguys
#iptables -A FIREWALL -i $OUTS -p tcp --syn --dport 22 -m recent --name ssh --set
#iptables -A FIREWALL -i $OUTS -p tcp --syn --dport 22 -m recent --name ssh --rcheck --seconds 300 --hitcount 6 -j BADGUY
#iptables -A FIREWALL -i $OUTS -p tcp --syn --dport 22 -m recent --name ssh --rcheck --seconds 30 --hitcount 2 -j LOG_DROP

# Block inbound and outbound icmp traffic
iptables -A TRUSTED -i eth0 -p icmp -j LOG_DROP
iptables -A TRUSTED -o eth0 -p icmp -j LOG_DROP

# Allow inbound ssh traffic
iptables -A TRUSTED -i eth0 -p tcp -m multiport --dport 22 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A TRUSTED -i eth0 -p udp -m multiport --dport 22 -m state --state NEW,ESTABLISHED -j ACCEPT

# Allow ftp inbound and outbound traffic
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 21 -m state --state NEW,ESTABLISHED -j ACCEPT 
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 20 -m state --state ESTABLISHED -j ACCEPT 
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 1024:65535 --sport 1024:65535 -m state --state NEW,ESTABLISHED -j ACCEPT 
iptables -A TRUSTED -o eth0 -p tcp -m tcp --sport 21 -m state --state ESTABLISHED -j ACCEPT 
iptables -A TRUSTED -o eth0 -p tcp -m tcp --sport 20 -m state --state ESTABLISHED -j ACCEPT 
iptables -A TRUSTED -o eth0 -p tcp -m tcp --sport 1024:65535 --dport 1024:65535 -m state --state ESTABLISHED -j ACCEPT

# Allow inbound http,https traffic
iptables -A TRUSTED -i eth0 -p tcp -m multiport --dport 80,443 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A TRUSTED -i eth0 -p udp -m multiport --dport 80,443 -m state --state NEW,ESTABLISHED -j ACCEPT

# Allow outbound tcp and udp traffic
iptables -A TRUSTED -o eth0 -p tcp -m tcp -m state --state ESTABLISHED -j ACCEPT
iptables -A TRUSTED -o eth0 -p udp -m udp -m state --state ESTABLISHED -j ACCEPT

# End message
echo " [End iptables rules setting]"
```

---

### Post by JKyleOKC on 2012-07-30
Your ssh rules for the FIREWALL chain won't have any effect, because you're adding them **after** the unconditional jump to DROP that's seven lines above them. You need to move them to come before that "-j DROP" line. Better yet would be to just remove that "drop all other packets" rule, and set the policy for INPUT to DROP instead of ACCEPT, by means of another line that could be made the final line of the script.

Keep in mind that the "-A" action adds the rule after all that are already in the table, and they are executed in strict first-to-last sequence. Having an unconditional "-j DROP" makes any rules added after it unreachable.

Other than that it looks pretty doggone good!

---

### Post by duesentriebchen on 2012-07-30
Hy JKyleOKC :D

Thank´s i´m flattered \\:D/

To the ssh line.
[SIZE=3]In my pimped Script i use[/SIZE]

```
# Allow inbound ssh traffic 
iptables -A TRUSTED -i eth0 -p tcp -m multiport --dport 22 -m state --state NEW,ESTABLISHED -j ACCEPT 
iptables -A TRUSTED -i eth0 -p udp -m multiport --dport 22 -m state --state NEW,ESTABLISHED -j ACCEPT
```[SIZE=3]if i change it to [/SIZE]
```

# Allow inbound ssh traffic 
iptables -A TRUSTED -i eth0 -p tcp -m multiport --dport 22 -m state --state ESTABLISHED -j ACCEPT 
iptables -A TRUSTED -i eth0 -p udp -m multiport --dport 22 -m state --state ESTABLISHED -j ACCEPT
```[SIZE=3]i am blocked out of my server with any connection i try to make.
So in some kind it has to work...[/SIZE] :mrgreen:

---

### Post by JKyleOKC on 2012-07-30
When you removed "NEW," from the two rules, that told it to prohibit any new connections. Thus it's doing exactly what you told it to.

If you know the IP address from which you will be initiating the ssh connection, you can add "-s x.x.x.x" (where the "x"s are replaced by that IP address) to the original two lines. This will accept only connections from the specified address, leaving all other addresses rejected. The 'NEW," though is essential.

Unfortunately this won't work if your IP address varies from time to time. That's when hardening the ssh server itself, to use RSA authentication instead of passwords, comes in handy.

---

### Post by duesentriebchen on 2012-07-31
Hy JKyleOKC
[LIST=1]
Yes, due to the DHCP protocol it is rather difficult for me to define the access via an IP Address. But like you pointed out, i am using autenthication via RSA so the direct issue for brutforcing or the need of a defence should be stable.

[*]No i understand what you meant with the ssh Rules for the Firewall!!!
Sorry for my missunderstanding!!!
So if i change it to this, the Rules should work, what do you think?

```

# Block any packet from IP-addresses that are present in the badguys list for one hour - port scan
#iptables -A FIREWALL -i $OUTS -m recent --name badguys --update --seconds 3600 -j LOG_DROP
# Allow NEW, ESTABLISHED and RELATED incoming connection
iptables -A FIREWALL -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
# Allow self communication
iptables -A FIREWALL -i lo -j ACCEPT
iptables -A FIREWALL -o lo -j ACCEPT
# Send all package to the TRUSTED chain
iptables -A FIREWALL -j TRUSTED
# Send all DROP package from FIREWALL chain to the badguys list - port scan
#iptables -A FIREWALL -t filter -i $OUTS -j LOG_DROP -m recent --set --name badguys

[COLOR="Red"]# SSH brute force attacks - verify in /proc/net/ipt_recent files badguys and ssh
#iptables -t filter -I BADGUY -m recent --set --name badguys
#iptables -A FIREWALL -i $OUTS -p tcp --syn --dport 22 -m recent --name ssh --set
#iptables -A FIREWALL -i $OUTS -p tcp --syn --dport 22 -m recent --name ssh --rcheck --seconds 300 --hitcount 6 -j BADGUY
#iptables -A FIREWALL -i $OUTS -p tcp --syn --dport 22 -m recent --name ssh --rcheck --seconds 30 --hitcount 2 -j LOG_DROP[/COLOR]

[COLOR="SeaGreen"]# DROP all other packets
iptables -A FIREWALL -j LOG_DROP[/COLOR]

# Send all through the FIREWALL chain
iptables -A INPUT -j FIREWALL
iptables -A FORWARD -j LOG_DROP
iptables -A OUTPUT -j FIREWALL

```

[*]Could you be so kind to explain me two things.
_Firstly:_ I can not find, or i am not able to define the search key, how to patch IPTABLES wit the ipt_recent patch in the commandline without using a GUI. Could you give me a link or point out an explanation how to do this? I do not want to mess up anything that touches the KERNEL!!!

_Secondly:_ What is the meaning of ```
**$OUTS**
``` in this lines.
```

iptables -A FIREWALL -i **_$OUTS_** -m recent --name badguys --update --seconds 3600 -j LOG_DROP
iptables -A FIREWALL -t filter -i **_$OUTS_** -j LOG_DROP -m recent --set --name badguys
iptables -A FIREWALL -i **_$OUTS_** -p tcp --syn --dport 22 -m recent --name ssh --set
iptables -A FIREWALL -i **_$OUTS_** -p tcp --syn --dport 22 -m recent --name ssh --rcheck --seconds 300 --hitcount 6 -j BADGUY
iptables -A FIREWALL -i **_$OUTS_** -p tcp --syn --dport 22 -m recent --name ssh --rcheck --seconds 30 --hitcount 2 -j LOG_DROP

```
As far as i did check some other scripts, the ```
**$**
``` is used for symlinks to directories or scripts.
Can i use ```
**eth0**
``` without the ```
**$**
``` instead?
[/LIST]

Thank you very much in advance!!!

---

### Post by JKyleOKC on 2012-07-31
No, it still will not allow new connections. You have ```
# Allow NEW, ESTABLISHED and RELATED incoming connection
iptables -A FIREWALL -i eth0 -m state --state [COLOR="Red"]ESTABLISHED,RELATED[/COLOR] -j ACCEPT

```and until you make it read ```
# Allow NEW, ESTABLISHED and RELATED incoming connection
iptables -A FIREWALL -i eth0 -m state --state [COLOR="Red"]NEW,ESTABLISHED,RELATED[/COLOR] -j ACCEPT

```no new connections will be allowed.

As for the meaning of "$OUTS" this will be replaced by the content of a variable named "OUTS" which I suspect will be defined near the start of the script with a line that looks something like ```
declare OUTS=eth0
```Many script authors do this to make it easy to customize the script by changing the actual value at just one spot. For instance, my outgoing interface is "eth1" so I could just change the "eth0" to "eth1" and the script would work for me. Without using the variable, I would have to change every place that it's used.

The "$" prefix tells the shell to use the value of the following expression, rather than using it literally. While it's similar to the concept of a symlink, it really has no direct connection to them.

I'm not sure what you mean by "the ipt_recent patch" since this is simply a module that is added to your script. Once you have edited the script it makes no difference whether you did so via a GUI or by using the command line; the iptables program will simply follow your list of rules and will include the module along with all the others.

---

### Post by duesentriebchen on 2012-07-31
hy ;)

Thank you for your advice to
```
iptables -A FIREWALL -i eth0 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
```I will do so. Actually i had the "NEW", but i deleted it, because my connection did work without also.

Ok, i understand the meaning of the "$" prefix. Due to my past years in work, i used to tell CNC-machines what to do.
As this "$" prefix used in IT-systems, we did use for example ```
#500=X23.56
``` at the start of the script.

The **_ipt_recent_patch_** is this one. [http://www.snowman.net/projects/ipt_recent/](http://www.snowman.net/projects/ipt_recent/)
I did a check in the ```
:~$ ls /lib/modules/$(uname -r)/kernel/net/ipv4/netfilter/
arptable_filter.ko  iptable_raw.ko     ipt_LOG.ko           nf_defrag_ipv4.ko  nf_nat_proto_dccp.ko
arp_tables.ko        iptable_security.ko  ipt_MASQUERADE.ko     nf_nat_amanda.ko   nf_nat_proto_gre.ko
arpt_mangle.ko        ip_tables.ko     ipt_NETMAP.ko           nf_nat_ftp.ko      nf_nat_proto_sctp.ko
ip_queue.ko        ipt_ah.ko         ipt_REDIRECT.ko       nf_nat_h323.ko      nf_nat_proto_udplite.ko
iptable_filter.ko   ipt_CLUSTERIP.ko     ipt_REJECT.ko           nf_nat_irc.ko      nf_nat_sip.ko
iptable_mangle.ko   ipt_ecn.ko         ipt_ULOG.ko           nf_nat.ko      nf_nat_snmp_basic.ko
iptable_nat.ko        ipt_ECN.ko         nf_conntrack_ipv4.ko  nf_nat_pptp.ko      nf_nat_tftp.ko
:~$ 

``` and i do not have this module compilied. There for i ask for your support on a how to that i do not mess up anything.

Kind regards [-o<

---

### Post by duesentriebchen on 2012-07-31
Hy dear frodon, dear JKyleOKC.

I got it working with your help and your knowledge :popcorn: =D>=D>=D>

I did a seperation on the DROP_LOG´s, to see why the packet is dropped!

_**[SIZE=3]This is really running[/SIZE]**_ :biggrin:

Like you analysed and proposed JKyleOKC, i put the final ```
**-j DROP**
``` to the end of the script.

If i do a ```
**tail -f /var/log/firewall**
```or a ```
**tail -f /var/log/syslog**
```i can see upon the DROP_LOG criteria why the packet is dropped :cool:

This is absoloutely stunning!!! I started with LINUX in February and now i have a almost DIY Firewall on my little server :-\"

The only thing i do not understand, is that upon the modules listed i do not have the ipt_recent module compiled! But it´s running ... ?

Check out the script and let me know what you think about it!
```
#!/bin/bash

# ftp.service.3
# No spoofing !!!
if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ]
then
for filtre in /proc/sys/net/ipv4/conf/*/rp_filter
do
echo 1 > $filtre
done
fi 

# No icmp
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

modprobe ip_tables
modprobe ip_nat_ftp
modprobe ip_nat_irc
modprobe ip_conntrack_irc
modprobe ip_conntrack_ftp
modprobe iptable_filter
modprobe iptable_nat
modprobe ipt_recent

# Remove all rules
iptables -F
iptables -X

# first set the default behaviour => accept connections
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

# New chains
iptables -N FIREWALL
iptables -N TRUSTED
iptables -N BADGUY

# Log chain
iptables -N LOG_DROP
iptables -A LOG_DROP -j LOG --log-prefix '[IPTABLES DROP] : '
iptables -A LOG_DROP -j DROP

iptables -N LOG_DROP_BAD
iptables -A LOG_DROP_BAD -j LOG --log-prefix '[IPTABLES DROP BADGUYS] : '
iptables -A LOG_DROP_BAD -j DROP

iptables -N LOG_DROP_BADEND
iptables -A LOG_DROP_BADEND -j LOG --log-prefix '[IPTABLES DROP BADEND] : '
iptables -A LOG_DROP_BADEND -j DROP

iptables -N LOG_DROP_SSH
iptables -A LOG_DROP_SSH -j LOG --log-prefix '[IPTABLES DROP SSH BRUTEFORCE] : '
iptables -A LOG_DROP_SSH -j DROP

iptables -N LOG_DROP_FWD
iptables -A LOG_DROP_FWD -j LOG --log-prefix '[IPTABLES DROP FORWARD] : '
iptables -A LOG_DROP_FWD -j DROP

iptables -N LOG_DROP_ICMP
iptables -A LOG_DROP_ICMP -j LOG --log-prefix '[IPTABLES DROP ICMP] : '
iptables -A LOG_DROP_ICMP -j DROP

# Block any packet from IP-addresses that are present in the badguys list for one hour - port scan
iptables -A FIREWALL -i eth0 -m recent --name badguys --update --seconds 3600 -j LOG_DROP_BAD
#iptables -A FIREWALL -i eth0 -m recent --name badguys -j LOG_DROP_BAD
# Allow NEW, ESTABLISHED and RELATED incoming connection
iptables -A FIREWALL -i eth0 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
# Allow self communication
iptables -A FIREWALL -i lo -j ACCEPT
iptables -A FIREWALL -o lo -j ACCEPT
# Send all package to the TRUSTED chain
iptables -A FIREWALL -j TRUSTED
# DROP all other packets
#iptables -A FIREWALL -j LOG_DROP

# Send all through the FIREWALL chain
iptables -A INPUT -j FIREWALL
iptables -A FORWARD -j LOG_DROP_FWD
iptables -A OUTPUT -j FIREWALL

# SSH brute force attacks - verify in /proc/net/ipt_recent files badguys and ssh
iptables -t filter -I BADGUY -m recent --set --name badguys
iptables -A FIREWALL -i eth0 -p tcp --syn --dport 22 -m recent --name ssh --set
iptables -A FIREWALL -i eth0 -p tcp --syn --dport 22 -m recent --name ssh --rcheck --seconds 300 --hitcount 6 -j BADGUY
iptables -A FIREWALL -i eth0 -p tcp --syn --dport 22 -m recent --name ssh --rcheck --seconds 30 --hitcount 3 -j LOG_DROP_SSH

# Block inbound and outbound icmp traffic
iptables -A TRUSTED -i eth0 -p icmp -j LOG_DROP_ICMP
iptables -A TRUSTED -o eth0 -p icmp -j LOG_DROP_ICMP

# Allow inbound ssh traffic
iptables -A TRUSTED -i eth0 -p tcp -m multiport --dport 22 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A TRUSTED -i eth0 -p udp -m multiport --dport 22 -m state --state NEW,ESTABLISHED -j ACCEPT

# Allow ftp inbound and outbound traffic
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 21 -m state --state NEW,ESTABLISHED -j ACCEPT 
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 20 -m state --state ESTABLISHED -j ACCEPT 
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 1024:65535 --sport 1024:65535 -m state --state NEW,ESTABLISHED -j ACCEPT 
iptables -A TRUSTED -o eth0 -p tcp -m tcp --sport 21 -m state --state ESTABLISHED -j ACCEPT 
iptables -A TRUSTED -o eth0 -p tcp -m tcp --sport 20 -m state --state ESTABLISHED -j ACCEPT 
iptables -A TRUSTED -o eth0 -p tcp -m tcp --sport 1024:65535 --dport 1024:65535 -m state --state ESTABLISHED -j ACCEPT

# Allow inbound http,https traffic
iptables -A TRUSTED -i eth0 -p tcp -m multiport --dport 80,443 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A TRUSTED -i eth0 -p udp -m multiport --dport 80,443 -m state --state NEW,ESTABLISHED -j ACCEPT

# Allow outbound tcp and udp traffic
iptables -A TRUSTED -o eth0 -p tcp -m tcp -m state --state ESTABLISHED -j ACCEPT
iptables -A TRUSTED -o eth0 -p udp -m udp -m state --state ESTABLISHED -j ACCEPT

# IMPORTANT Send all DROP package from FIREWALL chain to the badguys list - port scan
iptables -A FIREWALL -t filter -i eth0 -j LOG_DROP_BADEND -m recent --set --name badguys

# End message
echo " [End iptables rules setting]"

```Kind regards :-D

---

### Post by JKyleOKC on 2012-07-31
I don't see anything seriously wrong. You do have a few rules that will never match, because rules that will be tested earlier will already deal with any packet that could match them, but it won't hurt anything to leave them in. One of my main policies, always, is to be very careful about making changes once I have something working the way I want!

I'm not sure that your outbound FTP rule for port 21 will allow you to FTP anything INTO the server, such as downloading a software package from some other system, since it still does not have a NEW state specified although the input rule does. However you may not want to be able to initiate an FTP transfer at the server, so this might not be a problem at all.

Congratulations!

EDIT: The ipt-reject module may be compiled into your kernel already; it is in mine. The actual name is ipt-REJECT so the difference in case might be why you aren't finding it. I checked by doing "lsmod|grep ip" on a command line, to find it.

---

### Post by duesentriebchen on 2012-08-01
Dear JKyleOKC

Thank you for your quick reply.

Wich NON-CONSIDERED rules do mean. Could you be so kind to point these out please?

_Considering the FTP-service:_
I did upload, download and delete files. Also create, rename etc. and delete directories using ftp, ftps and sftp.
So the ftp service is working.

ipt-REJECT you say. I will check this. Thank you for pointing out!!!

Best regards :D

---

### Post by JKyleOKC on 2012-08-01
My remark involved the "NEW, ESTABLISHED, RELATED" and "ESTABLISHED,RELATED" clauses in the TRUSTED chain. On closer examination, I may have found a serious error here.

My original reasoning was that since the third rule in your FIREWALL chain accepts any NEW,ESTABLISHED,RELATED packet that the rules in the TRUSTED chain that included similar match conditions would not be reached.

What I've just discovered is that including "NEW," in that third rule makes sure that the TRUSTED chain will never be reached, since the rule that jumps to it appears later in the FIREWALL chain.

I believe that you can remove "NEW," from that third rule of FIREWALL, leaving only "ESTABLISHED,RELATED" as its match conditions, and can then remove all "ESTABLISHED,RELATED" conditions from all the rules in TRUSTED, leaving only NEW as their match condition. Any rule in TRUSTED that does not have a NEW match condition would then be superfluous and could be removed.

What I believe will be the result of those changes is that any new connection will have to pass through the TRUSTED chain to be accepted. Once the packet is accepted by TRUSTED, subsequent packets in that connection will be accepted by the third rule of FIREWALL and never go to TRUSTED for checking again. If TRUSTED rejects the packet, no connection will be established and all subsequent packets from that attempt will also go to TRUSTED and be rejected. At least, that's my intention.

When testing this, I would keep a safe copy of the script as another file, since it does work as written and my analysis just might prevent it from working! When tracing the progress of a packet through the whole set of chains, it's very easy to introduce unwanted side effects.

I hope I'm not leading you astray!

---

### Post by duesentriebchen on 2012-08-01
Hy JKyleOKC

Ok, i think slowly i get an idea of this thing working.
I do understand your topic for processing packets in the tables NEW.
But...
Isn´t any packet forwarded from the FIREWALL chain to the TRUSTED chain if it does not match any rules in the FIREWALL chain. If i understand this, then the packets that do not match any criteria in the FIREWALL chain should be forwarded in the TRUSTED chain.....
Aaahh...now i understand!!! OK!!!
The INPUT chain forwards any packet to the FIREWALL chain.
If it is not dropped in the FIREWALL chain it will be forwarderd to the TRUSTED chain.
If it does not meet any criteria in the TRUSTED chain then it will be finally DROPPED. Is this right?

1.) So if i delete NEW in the first rule down below, then NO NEW packet will be processed in the FIREWALL chain. But what happens to this NEW packet? Is it forwarded to the TRUSTED chain since this NEW packet does not meet any criteria in the FIREWALL chain, or is it dropped in the FIREWALL chain?
```
# Allow NEW, ESTABLISHED and RELATED incoming connection
iptables -A FIREWALL -i eth0 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT# Send all package to the TRUSTED chain
iptables -A FIREWALL -j TRUSTED
```2.) If i leave the NEW in the first rule, and it does not meet any criteria in the FIREWALL chain, is it then forwarded to the TRUSTED chain as a NEW packet or is it dropped by the FIREWALL chain?

I did modify the script. My services are still running and reachable.
The only thing i am missing in the DROP_LOG´s, is that the ssh bruteforce rule does not seem to work. On the other hand nobody is bruteforcing me at the moment beeing :D

But i think i am having problems by building the files ssh and badguys. I also do not believe that the ssh brutforce chain is working...

EDIT: It must be working. The SRC is first dropped by the DROP_LOG_BADEND and aftherwords by DROP_LOG_BADGUYS -> so the list´s are obviousley working!!! I just have to wait for a bruteforce-attack ....
```
Aug  1 20:26:48  kernel: [167587.550598] [IPTABLES DROP BADEND] : IN=eth0 OUT= MAC= SRC=74.120.12.140 DST=xxx.xxx.xxx.xx LEN=626 TOS=0x00 PREC=0x00 TTL=45 ID=39804 DF PROTO=TCP SPT=24517 DPT=9001 WINDOW=16 RES=0x00 ACK URGP=0 
Aug  1 20:26:49 kernel: [167588.007598] [IPTABLES DROP BADGUYS] : IN=eth0 OUT= MAC= SRC=74.120.12.140 DST=xxx.xxx.xxx.xx LEN=576 TOS=0x00 PREC=0x00 TTL=45 ID=39806 DF PROTO=TCP SPT=24517 DPT=9001 WINDOW=16 RES=0x00 ACK URGP=0 
Aug  1 20:26:49 kernel: [167588.691429] [IPTABLES DROP BADGUYS] : IN=eth0 OUT= MAC= SRC=77.106.125.32 DST=xxx.xxx.xxx.xx LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=15137 DF PROTO=TCP SPT=52198 DPT=16906 WINDOW=8192 RES=0x00 SYN URGP=0 
Aug  1 20:26:50 kernel: [167588.931737] [IPTABLES DROP BADGUYS] : IN=eth0 OUT= MAC= SRC=74.120.12.140 DST=xxx.xxx.xxx.xx LEN=576 TOS=0x00 PREC=0x00 TTL=45 ID=39807 DF PROTO=TCP SPT=24517 DPT=9001 WINDOW=16 RES=0x00 ACK URGP=0 

```

My /var/log/firewall looks like this
```
Aug  1 19:35:09 xxxxxxx kernel: [164488.550780] [IPTABLES DROP BADEND] : IN=eth0 OUT= MAC=xx:Xx:xx:Xx:XX:XX:xx:xx:XX:xx SRC=93.182.175.141 DST=xxx.xxx.xx.xxx LEN=76 TOS=0x00 PREC=0x00 TTL=107 ID=9425 PROTO=UDP SPT=13501 DPT=16906 LEN=56 
Aug  1 19:35:10 xxxxxxx kernel: [164489.102976] [IPTABLES DROP BADGUYS] : IN=eth0 OUT= MAC=xx:Xx:xx:Xx:XX:XX:xx:xx:XX:xx  SRC=81.206.158.42 DST=xxx.xxx.xx.xxx LEN=40 TOS=0x00 PREC=0x00 TTL=115 ID=24627 DF PROTO=TCP SPT=56270 DPT=9030 WINDOW=0 RES=0x00 ACK RST URGP=0 
Aug  1 19:43:13 xxxxxxx kernel: [164972.054903] [IPTABLES DROP ICMP] : IN=eth0 OUT= MAC=xx:Xx:xx:Xx:XX:XX:xx:xx:XX:xx SRC=94.245.252.128 DST=xxx.xxx.xx.xxx LEN=84 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=ICMP TYPE=8 CODE=0 ID=43017 SEQ=1 

```My script looks like this at the moment.

_**EDIT: **_I do some experimental logging with the NEW filter in the FIREWALL chain below. If i leave it there my logging/dropping decreases. If i remove it my logging/dropping increases. WHAT does this in conclusion mean?
```
# Allow NEW, ESTABLISHED and RELATED incoming connection
iptables -A FIREWALL -i eth0 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT

``````

#!/bin/bash

# ftp.service.4
# No spoofing !!!
if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ]
then
for filtre in /proc/sys/net/ipv4/conf/*/rp_filter
do
echo 1 > $filtre
done
fi 

# No icmp
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

modprobe ip_tables
modprobe ip_nat_ftp
modprobe ip_nat_irc
modprobe ip_conntrack_irc
modprobe ip_conntrack_ftp
modprobe iptable_filter
modprobe iptable_nat
modprobe ipt_REJECT
modprobe ipt_recent

# Remove all rules
iptables -F
iptables -X

# first set the default behaviour => accept connections
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

# New chains
iptables -N FIREWALL
iptables -N TRUSTED
iptables -N BADGUY

# Log chain
iptables -N LOG_DROP
iptables -A LOG_DROP -j LOG --log-prefix '[IPTABLES DROP] : '
iptables -A LOG_DROP -j DROP

iptables -N LOG_DROP_BAD
iptables -A LOG_DROP_BAD -j LOG --log-prefix '[IPTABLES DROP BADGUYS] : '
iptables -A LOG_DROP_BAD -j DROP

iptables -N LOG_DROP_BADEND
iptables -A LOG_DROP_BADEND -j LOG --log-prefix '[IPTABLES DROP BADEND] : '
iptables -A LOG_DROP_BADEND -j DROP

iptables -N LOG_DROP_SSH
iptables -A LOG_DROP_SSH -j LOG --log-prefix '[IPTABLES DROP SSH BRUTEFORCE] : '
iptables -A LOG_DROP_SSH -j DROP

iptables -N LOG_DROP_FWD
iptables -A LOG_DROP_FWD -j LOG --log-prefix '[IPTABLES DROP FORWARD] : '
iptables -A LOG_DROP_FWD -j DROP

iptables -N LOG_DROP_ICMP
iptables -A LOG_DROP_ICMP -j LOG --log-prefix '[IPTABLES DROP ICMP] : '
iptables -A LOG_DROP_ICMP -j DROP

iptables -N LOG_DROP_HTTP
iptables -A LOG_DROP_HTTP -j LOG --log-prefix '[IPTABLES DROP HTTP] : '
iptables -A LOG_DROP_HTTP -j DROP

# Block any packet from IP-addresses that are present in the badguys list for one hour - port scan
iptables -A FIREWALL -i eth0 -m recent --name badguys --update --seconds 3600 -j LOG_DROP_BAD

# Allow NEW, ESTABLISHED and RELATED incoming connection
iptables -A FIREWALL -i eth0 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT

# Block any packet from IP-addresses that are present in the badguys list for one hour - port scan
#iptables -A FIREWALL -i eth0 -m recent --name badguys --update --seconds 3600 -j LOG_DROP_BAD

# SSH brute force attacks - verify in /proc/net/files badguys and ssh
iptables -t filter -I BADGUY -m recent --set --name badguys
iptables -A FIREWALL -i eth0 -p tcp --syn --dport 22 -m recent --name ssh --set
iptables -A FIREWALL -i eth0 -p tcp --syn --dport 22 -m recent --name ssh --rcheck --seconds 300 --hitcount 6 -j BADGUY
iptables -A FIREWALL -i eth0 -p tcp --syn --dport 22 -m recent --name ssh --rcheck --seconds 30 --hitcount 3 -j LOG_DROP_SSH

# HTTP attacks - verify in /proc/net/ipt_recent files badguys and http
iptables -t filter -I BADGUY -m recent --set --name badguys
iptables -A FIREWALL -i eth0 -p tcp --syn --dport 80 -m recent --name http --set
iptables -A FIREWALL -i eth0 -p tcp --syn --dport 80 -m recent --name http --rcheck --seconds 300 --hitcount 6 -j BADGUY
iptables -A FIREWALL -i eth0 -p tcp --syn --dport 80 -m recent --name http --rcheck --seconds 30 --hitcount 3 -j LOG_DROP_HTTP

# Block inbound and outbound icmp traffic
iptables -A FIREWALL -i eth0 -p icmp -j LOG_DROP_ICMP
iptables -A FIREWALL -o eth0 -p icmp -j LOG_DROP_ICMP

# Allow self communication
iptables -A FIREWALL -i lo -j ACCEPT
iptables -A FIREWALL -o lo -j ACCEPT

# IMPORTANT Send all DROP package from FIREWALL chain to the badguys list - port scan
#iptables -A FIREWALL -t filter -i eth0 -j LOG_DROP_BADEND -m recent --set --name badguys

# Send all package to the TRUSTED chain
iptables -A FIREWALL -j TRUSTED

# Send all through the FIREWALL chain
iptables -A INPUT -j FIREWALL
iptables -A FORWARD -j LOG_DROP_FWD
iptables -A OUTPUT -j FIREWALL

# IMPORTANT Send all DROP package from FIREWALL chain to the badguys list - port scan
iptables -A FIREWALL -t filter -i eth0 -j LOG_DROP_BADEND -m recent --set --name badguys

# Allow inbound ssh traffic
iptables -A TRUSTED -i eth0 -p tcp -m multiport --dport 22 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A TRUSTED -i eth0 -p udp -m multiport --dport 22 -m state --state NEW,ESTABLISHED -j ACCEPT

# Allow ftp inbound and outbound traffic
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 21 -m state --state NEW,ESTABLISHED -j ACCEPT 
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 20 -m state --state ESTABLISHED -j ACCEPT 
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 1024:65535 --sport 1024:65535 -m state --state NEW,ESTABLISHED -j ACCEPT 
iptables -A TRUSTED -o eth0 -p tcp -m tcp --sport 21 -m state --state NEW,ESTABLISHED -j ACCEPT 
iptables -A TRUSTED -o eth0 -p tcp -m tcp --sport 20 -m state --state ESTABLISHED -j ACCEPT 
iptables -A TRUSTED -o eth0 -p tcp -m tcp --sport 1024:65535 --dport 1024:65535 -m state --state ESTABLISHED,RELATED -j ACCEPT

# Allow inbound http,https traffic
iptables -A TRUSTED -i eth0 -p tcp -m multiport --dport 80,443 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A TRUSTED -i eth0 -p udp -m multiport --dport 80,443 -m state --state NEW,ESTABLISHED -j ACCEPT

# Allow outbound tcp and udp traffic
iptables -A TRUSTED -o eth0 -p tcp -m tcp -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A TRUSTED -o eth0 -p udp -m udp -m state --state NEW,ESTABLISHED -j ACCEPT

# IMPORTANT Send all DROP package from FIREWALL chain to the badguys list - port scan
#iptables -A FIREWALL -t filter -i eth0 -j LOG_DROP_BADEND -m recent --set --name badguys

# End message
echo " [End iptables rules setting]"

```

---

### Post by JKyleOKC on 2012-08-02
I have to be a bit brief this time but will go over your full script later.

For your first question, if you leave out NEW from the FIREWALL chain then the packet will go to TRUSTED to be checked since there's no DROP between the third rule and the jump to TRUSTED. Actually you don't need a DROP action in FIREWALL at all, and if the jump to TRUSTED were its last rule then TRUSTED would not need a DROP either. A bad packet would come into INPUT, go to FIREWALL and not be accepted, then go to TRUSTED and not be accepted there either, then "fall off the end" of TRUSTED to return to FIREWALL, there do the same to return to INPUT, and finally at INPUT be dropped, either by an explicit rule or by policy. This would lose your detailed logging scheme, however, so I would leave those DROP actions in TRUSTED and FIREWALL.

For question two, if you leave NEW in firewall then any new connection will be accepted without ever going to TRUSTED to be checked. This is also why you see fewer drops in this case per your final question; bad connections get through unquestioned.

I'll go through the full script later today.

---

### Post by duesentriebchen on 2012-08-02
Dera JKyleOKC

Thank you very much for your exlpanation!!! I did not know, that there is a loop in the chains. So thanks to your effort i did understand this and implementet, or tried to, your knowledge in the script. I tried to clean it, so it is more understandable. The LOG_DROP´s help me to understand what is dropped, why it is dropped, and which chain did DROP.

I also did find the badguys and ssh list in /proc/net/xt_recent :D

I hope you are not to deeply investigating my previous script, and getting a headache because of me!!!!
I can proudly present a running script :biggrin:

```

#!/bin/bash

# ftp.service.final
# No spoofing !!!
if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ]
then
for filtre in /proc/sys/net/ipv4/conf/*/rp_filter
do
echo 1 > $filtre
done
fi 

# No icmp
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

modprobe ip_tables
modprobe ip_nat_ftp
modprobe ip_nat_irc
modprobe ip_conntrack_irc
modprobe ip_conntrack_ftp
modprobe iptable_filter
modprobe iptable_nat
modprobe ipt_REJECT
modprobe ipt_recent

# Remove all rules
iptables -F
iptables -X

# first set the default behaviour => accept connections
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

# New chains
iptables -N FIREWALL
iptables -N TRUSTED
iptables -N BADGUY

# Log chain
iptables -N LOG_DROP
iptables -A LOG_DROP -j LOG --log-prefix '[DROP INPUT] : '
iptables -A LOG_DROP -j DROP

iptables -N LOG_DROP_BAD1
iptables -A LOG_DROP_BAD1 -j LOG --log-prefix '[DROP BADGUYS FIREWALL] : '
iptables -A LOG_DROP_BAD1 -j DROP

iptables -N LOG_DROP_BAD2
iptables -A LOG_DROP_BAD2 -j LOG --log-prefix '[DROP BADGUYS TRUSTED] : '
iptables -A LOG_DROP_BAD2 -j DROP

iptables -N LOG_DROP_BADEND1
iptables -A LOG_DROP_BADEND1 -j LOG --log-prefix '[DROP BADEND FIREWALL] : '
iptables -A LOG_DROP_BADEND1 -j DROP

iptables -N LOG_DROP_BADEND2
iptables -A LOG_DROP_BADEND2 -j LOG --log-prefix '[DROP BADEND TRUSTED] : '
iptables -A LOG_DROP_BADEND2 -j DROP

iptables -N LOG_DROP_SSH
iptables -A LOG_DROP_SSH -j LOG --log-prefix '[DROP SSH BRUTEFORCE] : '
iptables -A LOG_DROP_SSH -j DROP

iptables -N LOG_DROP_FTP
iptables -A LOG_DROP_FTP -j LOG --log-prefix '[DROP FTP BRUTEFORCE] : '
iptables -A LOG_DROP_FTP -j DROP

iptables -N LOG_DROP_FWD
iptables -A LOG_DROP_FWD -j LOG --log-prefix '[DROP FORWARD] : '
iptables -A LOG_DROP_FWD -j DROP

iptables -N LOG_DROP_ICMP1
iptables -A LOG_DROP_ICMP1 -j LOG --log-prefix '[DROP ICMP FIREWALL] : '
iptables -A LOG_DROP_ICMP1 -j DROP

iptables -N LOG_DROP_ICMP2
iptables -A LOG_DROP_ICMP2 -j LOG --log-prefix '[DROP ICMP TRUSTED] : '
iptables -A LOG_DROP_ICMP2 -j DROP

# -----------------------------------------------------------------------------------------------------------------------

# Block any packet from IP´s that are present in the badguys list verify in /proc/net/xt_recent/files badguys and ssh
iptables -t filter -I BADGUY -m recent --set --name badguys
iptables -A FIREWALL -i eth0 -m recent --name badguys --update --seconds 3600 -j LOG_DROP_BAD1

# Allow ESTABLISHED and RELATED incoming connection
iptables -A FIREWALL -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT

# Allow self communication
iptables -A FIREWALL -i lo -j ACCEPT
iptables -A FIREWALL -o lo -j ACCEPT

# Block inbound and outbound icmp traffic
iptables -A FIREWALL -i eth0 -p icmp -j LOG_DROP_ICMP1
iptables -A FIREWALL -o eth0 -p icmp -j LOG_DROP_ICMP1

# Send all package to the TRUSTED chain
iptables -A FIREWALL -j TRUSTED

# IMPORTANT Send all DROP package from FIREWALL chain to the badguys list - port scan
iptables -A FIREWALL -t filter -i eth0 -j LOG_DROP_BADEND1 -m recent --set --name badguys

# Send all through the FIREWALL chain
iptables -A INPUT -j FIREWALL
iptables -A FORWARD -j LOG_DROP_FWD
iptables -A OUTPUT -j FIREWALL

# -----------------------------------------------------------------------------------------------------------------------

# Block any packet from IP´s that are present in the badguys list verify in /proc/net/xt_recent/files badguys and ssh
iptables -A TRUSTED -i eth0 -m recent --name badguys --update --seconds 3600 -j LOG_DROP_BAD2

# SSH brute force attacks - verify in /proc/net/xt_recent/file ssh
iptables -A TRUSTED -i eth0 -p tcp --syn --dport ssh -m recent --name ssh --set
iptables -A TRUSTED -i eth0 -p tcp --syn --dport ssh -m recent --name ssh --rcheck --seconds 300 --hitcount 6 -j BADGUY
iptables -A TRUSTED -i eth0 -p tcp --syn --dport ssh -m recent --name ssh --rcheck --seconds 30 --hitcount 3 -j LOG_DROP_SSH

# FTP brute force attacks - verify in /proc/net/xt_recent/file ftp
iptables -A TRUSTED -i eth0 -p tcp -m multiport --dport 20,21 --syn -m recent --name ftp --set
iptables -A TRUSTED -i eth0 -p tcp -m multiport --dport 20,21 --syn -m recent --name ftp --rcheck --seconds 300 --hitcount 6 -j BADGUY
iptables -A TRUSTED -i eth0 -p tcp -m multiport --dport 20,21 --syn -m recent --name ftp --rcheck --seconds 30 --hitcount 3 -j LOG_DROP_FTP

# Block inbound and outbound icmp traffic
iptables -A TRUSTED -i eth0 -p icmp -j LOG_DROP_ICMP2
iptables -A TRUSTED -o eth0 -p icmp -j LOG_DROP_ICMP2

# Allow inbound ssh traffic
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 22 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A TRUSTED -i eth0 -p udp -m udp --dport 22 -m state --state NEW,ESTABLISHED -j ACCEPT

# Allow ftp inbound and outbound traffic
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 21 -m state --state NEW,ESTABLISHED -j ACCEPT 
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 20 -m state --state ESTABLISHED -j ACCEPT 
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 1024:65535 --sport 1024:65535 -m state --state NEW,ESTABLISHED -j ACCEPT 
iptables -A TRUSTED -o eth0 -p tcp -m tcp --sport 21 -m state --state NEW,ESTABLISHED -j ACCEPT 
iptables -A TRUSTED -o eth0 -p tcp -m tcp --sport 20 -m state --state ESTABLISHED -j ACCEPT 
iptables -A TRUSTED -o eth0 -p tcp -m tcp --sport 1024:65535 --dport 1024:65535 -m state --state ESTABLISHED,RELATED -j ACCEPT

# Allow inbound http,https traffic
iptables -A TRUSTED -i eth0 -p tcp -m multiport --dport 80,443 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A TRUSTED -i eth0 -p udp -m multiport --dport 80,443 -m state --state NEW,ESTABLISHED -j ACCEPT

# Allow outbound tcp and udp traffic
iptables -A TRUSTED -o eth0 -p tcp -m tcp -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A TRUSTED -o eth0 -p udp -m udp -m state --state NEW,ESTABLISHED -j ACCEPT

# IMPORTANT Send all DROP package from TRUSTED chain to the badguys list - port scan
iptables -A TRUSTED -t filter -i eth0 -j LOG_DROP_BADEND2 -m recent --set --name badguys

# -----------------------------------------------------------------------------------------------------------------------

iptables -A INPUT -j LOG_DROP

# End message
echo " [End iptables rules setting]"

```[B][SIZE=4]

I want to thank you all very, very, very much for hanging me trough the last days and nights!
THANK YOU VERY MUCH!!!!
It would not have been possible without you!!!
Thank you!!!

[/SIZE][/B][SIZE=4][SIZE=2]Kindest regards from Austria,
Duesentriebchen[/SIZE][/SIZE][B][SIZE=4] ):P
[/SIZE][/B]

---

