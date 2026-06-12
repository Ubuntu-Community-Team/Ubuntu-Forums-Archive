---
title: "Command-line-based Firewall Recommendations"
date: 2007-01-12
forum: Server Platforms
---

### Post by nick1 on 2007-01-12
Greetings,

I am running a LAMP installation of Ubuntu 6 (no GUI, strictly command line).
I am looking for recommendations on a software-based firewall to use on my system.
No fancy networking is going on with this system.  I would prefer a firewall that is being actively developed and promptly releases security updates if and when a security threat is found in the firewall.

Thank you for your time,

Nick

---

### Post by PetePete on 2007-01-12
iptables ?

installed by default, you just need to configure it... read a good tutorial about that.

---

### Post by az on 2007-01-12
Install shorewall and shorewall-doc.  Read the docs - its fairly well documented and easy to configure.

---

### Post by Brazen on 2007-01-12
All linux "firewalls" use Netfilter (commonly/mistakenly called iptables).  Netfilter is built into the kernel, so it is updated with kernel updates.  Programs like Firestarter are just a front end to configuring Netfilter, but Netfilter does have a native commandline interface (the command is "iptables").

I do not know where the configuration file is though, to save the firewall settings on reboot.  Instead I use Webmin to manage Netfilter.  Shorewall is also very popular for configuring Netfilter.

Also, if you want a gui for Shorewall, the Shorewall website even reccommends Webmin.  Webmin is a web management application (no gui actually on the server, so little to no resource overhead) that lets you configure, well, just about everything.  For the firewall, it has a module for editing the iptables configuration directly, or Webmin has a module for editing the Shorewall configuration files.

I've never used Shorewall, but it basically just translates it's configuration into iptables commands.  I think the advantage of Shorewall, though, is that it is easy to understand for the novice - the iptables commands can be a bit cryptic for doing simple things like NAT or DNAT.

---

### Post by Moldz on 2007-01-12
If you have a simple server that should be providing only SSH and HTTP to the world, you can easily create a simple script with the appropriate rules for Netfilter.  There are a ton of good tutorials online that can help and you could always ask more questions here.

---

### Post by nick1 on 2007-02-01
Thanks to everyone for their input.  I think I am going to suck-it-up and use IPtables.
I've been reading several tutorials and books on IPtables and their starting to ease my fear of the subject.

A couple topics I'm unsure about at this point:

1.)  As my original post says, I'm running Ubuntu 6.06LTS Server (command-line based, no GUI) so I shouldn't need to install any additional software to configure Netfilter, right?  I did a "iptables --list" and a ton of rules were returned, most of which looked like were allowing all inbound and outbound access (which is ok since it's a test server).

2.)  Lets say I set the default policy on all three chains (INPUT, OUTPUT, FORWARD) to DENY and create an INPUT rule that allows HTTP access from anywhere.  When I am done writing my rules, is it true that I need to issue an IPtables save command so that the rules are applied each time the server is rebooted?  If so, I am confused about which save commands to issue.

3.)  Instead of issuing IPtables commands, is there a config file I can directly edit instead?

Any other advice or best-practices are appreciated.  Thank you for your time,

Nick

---

### Post by Brazen on 2007-02-01
> **nick1 said:**
> Thanks to everyone for their input.  I think I am going to suck-it-up and use IPtables.
I've been reading several tutorials and books on IPtables and their starting to ease my fear of the subject.

A couple topics I'm unsure about at this point:

1.)  As my original post says, I'm running Ubuntu 6.06LTS Server (command-line based, no GUI) so I shouldn't need to install any additional software to configure Netfilter, right?  I did a "iptables --list" and a ton of rules were returned, most of which looked like were allowing all inbound and outbound access (which is ok since it's a test server).

2.)  Lets say I set the default policy on all three chains (INPUT, OUTPUT, FORWARD) to DENY and create an INPUT rule that allows HTTP access from anywhere.  When I am done writing my rules, is it true that I need to issue an IPtables save command so that the rules are applied each time the server is rebooted?  If so, I am confused about which save commands to issue.

3.)  Instead of issuing IPtables commands, is there a config file I can directly edit instead?

Any other advice or best-practices are appreciated.  Thank you for your time,

Nick

I really don't know what would be the Ubuntu standard way of saving your iptables rules.  I've always used Webmin to configure the firewall, and I don't know exactly how it saves it's configuration.

---

### Post by tomBorgia on 2007-02-02
Hiya, you can save the rules by putting them in a script then calling the script at boot-time -

e.g.

#!/bin/bash
# flush all chains
iptables -F
#do modprobe stuff
modprobe ip_tables
#rest of moprobes....

# set the default policy for each of the pre-defined chains
iptables -P INPUT DROP
iptables -P OUTPUT ACCEPT
iptables -A FORWARD -j LOG --log-prefix "ForDr "
iptables -P FORWARD DROP

# to allow incoming http / log external requests...
iptables -A INPUT -i $INTIF -p tcp --dport 80 -j ACCEPT
#rest of rules...

Etc...

and as for the file in /etc/init.d -

#!/bin/bash
/etc/firewall/iptables              <-----this is the location of the above script....

Hope this helps, Tom.

---

### Post by Brazen on 2007-02-02
> **tomBorgia said:**
> Hiya, you can save the rules by putting them in a script then calling the script at boot-time -

e.g.

#!/bin/bash
# flush all chains
iptables -F
#do modprobe stuff
modprobe ip_tables
#rest of moprobes....

# set the default policy for each of the pre-defined chains
iptables -P INPUT DROP
iptables -P OUTPUT ACCEPT
iptables -A FORWARD -j LOG --log-prefix "ForDr "
iptables -P FORWARD DROP

# to allow incoming http / log external requests...
iptables -A INPUT -i $INTIF -p tcp --dport 80 -j ACCEPT
#rest of rules...

Etc...

and as for the file in /etc/init.d -

#!/bin/bash
/etc/firewall/iptables              <-----this is the location of the above script....

Hope this helps, Tom.

Another option would be to use the 'iptables-save' command to save your configuration to a file such as /etc/iptables.save.file
and then have your script in /etc/init.d as this```
#!/bin/bash
iptables-restore /etc/iptables.save.file
```

to make it even cooler, you could create a shutdown script of ```
#!/bin/bash
iptables-save /etc/iptables.save.file
```

That way anytime you make changes to the firewall, the changes are saved on shutdown.  Of course, this does not account for if you have a power outage and your shutdown scripts are not executed, but you could always execute the iptables-save command by hand anytime you make changes to be sure they are saved.

BTW, you probably want to double check the syntax on the iptables-save and iptables-restore commands.

---

### Post by nick1 on 2007-02-04
Thanks a lot, guys.  A few questions:

1.) What do the following lines mean and are they necessary for every IPtables script?  I don't understand this modprobe concept.

```
modprobe ip_tables
modprobe ip_conntrack_ftp
```

2.) I've never written a shell script (?) before so I'm confused about how to save this text file full of IPtables rules and how to execute the text file on bootup.

I placed ```
#!/bin/bash
``` at the top of the text file, like this:

```
#!/bin/bash
# Flush active rules and custom tables
IPTABLES --flush
IPTABLES --delete-chain
```
rest of IPtables rules...

Do I need to give the file a different extension?
Also, do I need to give the file any special permissions?

3.) After the previous steps, I then place the script into the /etc/init.d directory?

4.) I've adapted the following IPtables rules from _Linux Server Security_ (2nd Edition) *by Michael D. Bauer*.  I would appreciate criticism about this script:






```
#!/bin/bash
# Flush active rules and custom tables
IPTABLES --flush
IPTABLES --delete-chain
   
# Set default-deny policies for all three default chains
IPTABLES -P INPUT DROP
IPTABLES -P FORWARD DROP
IPTABLES -P OUTPUT DROP
   
# Give free reign to the loopback interfaces, i.e. local processes may connect
# to other processes' listening-ports.
IPTABLES -A INPUT  -i lo -j ACCEPT
IPTABLES -A OUTPUT -o lo -j ACCEPT
   
# Do some rudimentary anti-IP-spoofing drops. The rule of thumb is "drop
# any source IP address which is impossible" (per RFC 1918)
#
# NOTE: If you use RFC 1918 address-space, comment out or edit the appropriate 
# lines below!
#
IPTABLES -A INPUT -s 255.0.0.0/8 -j LOG --log-prefix "Spoofed source IP"
IPTABLES -A INPUT -s 255.0.0.0/8 -j DROP
IPTABLES -A INPUT -s 0.0.0.0/8 -j LOG --log-prefix "Spoofed source IP"
IPTABLES -A INPUT -s 0.0.0.0/8 -j DROP
IPTABLES -A INPUT -s 127.0.0.0/8 -j LOG --log-prefix "Spoofed source IP"
IPTABLES -A INPUT -s 127.0.0.0/8 -j DROP
# IPTABLES -A INPUT -s 192.168.0.0/16 -j LOG --log-prefix "Spoofed source IP"
# IPTABLES -A INPUT -s 192.168.0.0/16 -j DROP 
IPTABLES -A INPUT -s 172.16.0.0/12 -j LOG --log-prefix "Spoofed source IP"
IPTABLES -A INPUT -s 172.16.0.0/12 -j DROP
IPTABLES -A INPUT -s 10.0.0.0/8 -j LOG --log-prefix " Spoofed source IP"
IPTABLES -A INPUT -s 10.0.0.0/8 -j DROP

# NOTE: If you use RFC 1918 address-space in your internal or DMZ networks,
# comment out or edit the appropriate lines below!
# The following will NOT interfere with local inter-process traffic, whose
# packets have the source IP of the local loopback interface, e.g. 127.0.0.1
   
# IPTABLES -A INPUT -s $IP_LOCAL -j LOG --log-prefix "Spoofed source IP"
# IPTABLES -A INPUT -s $IP_LOCAL -j DROP
   
# Tell netfilter that all TCP sessions do indeed begin with SYN
# (There may be some RFC-non-compliant application somewhere which 
# begins its transactions otherwise, but if so I've never heard of it)
   
IPTABLES -A INPUT -p tcp ! --syn -m state --state NEW -j LOG --log-prefix "Stealth scan attempt?"
IPTABLES -A INPUT -p tcp ! --syn -m state --state NEW -j DROP
   
# INBOUND POLICY:

# Accept inbound packets that are part of previously-OK'ed sessions
IPTABLES -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
   
# Accept inbound packets which initiate SSH sessions
IPTABLES -A INPUT -p tcp --dport 22 -m state --state NEW -j ACCEPT

# Accept inbound packets which initiate HTTP sessions
IPTABLES -A INPUT -p tcp --dport 80 -m state --state NEW -j ACCEPT
   
# Log and drop anything not accepted above
# (Obviously we want to log any packet that doesn't match any ACCEPT rule, for
# both security and troubleshooting. Note that the final "DROP" rule is 
# redundant if the default policy is already DROP, but redundant security is
# usually a good thing.)

IPTABLES -A INPUT -j LOG --log-prefix "Dropped by default (INPUT):"
IPTABLES -A INPUT -j DROP
   
# OUTBOUND POLICY:

# (Applies to packets sent to the network interface (NOT loopback)
# from local processes)
   
# If it's part of an approved connection, let it out
IPTABLES -I OUTPUT 1 -m state --state RELATED,ESTABLISHED -j ACCEPT
   
# Allow outbound ping 
# (For testing only! If someone compromises your system they may attempt
# to use ping to identify other active IP addresses on the DMZ. Comment
# this rule out when you don't need to use it yourself!)

# IPTABLES -A OUTPUT -p icmp -j ACCEPT --icmp-type echo-request 
   
# Allow outbound DNS queries, e.g. to resolve IPs in logs
# (Many network applications break or radically slow down if they
# can't use DNS. Although DNS queries usually use UDP 53, they may also use TCP 
# 53. Although TCP 53 is normally used for zone-transfers, DNS queries with 
# replies greater than 512 bytes also use TCP 53, so we'll allow both TCP and UDP 
# 53 here
 
IPTABLES -A OUTPUT -p udp --dport 53 -m state --state NEW -j ACCEPT
IPTABLES -A OUTPUT -p tcp --dport 53 -m state --state NEW -j ACCEPT
   
# Log & drop anything not accepted above; if for no other reason, for troubleshooting

# NOTE: you might consider setting your log-checker (e.g. Swatch) to
# sound an alarm whenever this rule fires; unexpected outbound trans-
# actions are often a sign of intruders!

IPTABLES -A OUTPUT -j LOG --log-prefix "Dropped by default (OUTPUT):"
IPTABLES -A OUTPUT -j DROP
   
# Log & drop ALL incoming packets destined anywhere but here.
# (We already set the default FORWARD policy to DROP. But this is 
# yet another free, reassuring redundancy, so why not throw it in?)

IPTABLES -A FORWARD -j LOG --log-prefix "Attempted FORWARD? Dropped by default:"
IPTABLES -A FORWARD -j DROP
```

---

### Post by nick1 on 2007-02-05
In addition to my previous questions, I would like to know when is the most secure time to load the IPtables script during bootup.  I'm reading about various options:

1.)  place the script in the /etc/init.d directory

2.) modify the /etc/network/interfaces script to apply the rules automatically
( [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo) )

3.) place the script in the /etc/rc3.d, rc4.d, rc5.d directories
( [http://www.linuxquestions.org/questions/showthread.php?p=2617893#post2617893](http://www.linuxquestions.org/questions/showthread.php?p=2617893#post2617893) )

I'm really confused right now and don't know how to proceed from here.  I'm only interested in pursuing the most secure method.  Please advise.

Thank you for your time,

*Nick*

---

### Post by derrick1985 on 2007-02-06
I really don't know how well this would work or not, but you could install webmin and use the shorewall module to perhaps configure your firewall? Just need Webmin from their official site (regretably, not in repositories).

It is a bit weird to intsall, I was able to get it working by:

Download the offical .deb from [http://www.webmin.com](http://www.webmin.com) (do this either on your server with wget or on your own machine)

sudo dpkg -i webmin_version#.deb

dpkg will complain about unmet dependencies, that is where we do:

sudo apt-get install -f

And you are all done. Now you can log in to webmin via your browser pointed at port 10000

[https://yourservernameorip:10000](https://yourservernameorip:10000)

---

