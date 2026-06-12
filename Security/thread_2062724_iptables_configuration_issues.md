---
title: "iptables configuration issues"
date: 2012-09-25
forum: Security
---

### Post by underdogz on 2012-09-25
Hello,

I have recently setup an installation of ubuntu and have been attempting to set some rules using an iptables.rules file that is loaded upon boot.

The configuration I have allows my ssh connections & will also allow my pc to access via port 80 for my website when pageant is running. However if I reboot my pc or use my apple laptop I am not able to establish a connection when my full iptables configuration is in place. When I disable the iptables setup & reboot the ubuntu installation I can establish a connection so I know for sure it is my configuration that is not correct.

I am a little new to setting up iptables & can not figure out what is wrong here & need some advice from people more experienced. I have allowed port 80 connections but it is still blocking with my current configuration.

Here is what is in my iptables.rules file:
```

*filter
-A INPUT -i lo -p all -j ACCEPT
-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
-A OUTPUT -j ACCEPT
-A INPUT -p tcp --dport 80 -j ACCEPT
-A INPUT -p tcp --dport 443 -j ACCEPT
-A INPUT -p tcp --dport 3306 -j ACCEPT
-A INPUT -p tcp --dport 21 -j ACCEPT
-A INPUT -p tcp -m multiport --dports 8001,8002,8003,8004,8005,8006,8007,8008,8009,8010 -j ACCEPT
-A INPUT -p tcp -m state --state NEW --dport 56325 -j ACCEPT
-A INPUT -p tcp -m state --state NEW --dport 10852 -j ACCEPT
-A INPUT -p icmp -m icmp --icmp-type 8 -j ACCEPT
-A INPUT -j REJECT
-A FORWARD -j REJECT
COMMIT

```Somehow the rule is not being tripped because it just rejects a regular connection. The connection to my site can be established when my pageant is running but that should only be for ssh on the example ports shown above (56325 & 10852) & not anyone's regular connection. Port 22 is disallowed as I use the example 56325 for my terminal.

Any ideas on what I have misconfigured?

Thank you.

---

### Post by chadk5utc on 2012-09-25
Hello there are one or two things I will try to point out to simplify this as much as possible. iptables you have INPUT OUTPUT and FORWARD Chains. In your example you list only INPUT??? network communication generally requires Full Duplex(2 way) so think of your rules the same way you need INPUT and OUTPUT take a look at the 2 rules I have listed below:
iptables -A INPUT -i eth0 -p tcp --dport 80 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A OUTPUT -o eth0 -p tcp --sport 80 -m state --state ESTABLISHED -j ACCEPT

The first rules allows New and Established incoming connections the second allows Established Outgoing connections. I hope this helps 

  Chad

---

### Post by underdogz on 2012-09-25
> **chadk5utc said:**
> Hello there are one or two things I will try to point out to simplify this as much as possible. iptables you have INPUT OUTPUT and FORWARD Chains. In your example you list only INPUT??? network communication generally requires Full Duplex(2 way) so think of your rules the same way you need INPUT and OUTPUT take a look at the 2 rules I have listed below:
iptables -A INPUT -i eth0 -p tcp --dport 80 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A OUTPUT -o eth0 -p tcp --sport 80 -m state --state ESTABLISHED -j ACCEPT

The first rules allows New and Established incoming connections the second allows Established Outgoing connections. I hope this helps 

  Chad

Hello,

Thank you for the assistance.

This part of my rules should allow all output on any port, should it not?
```

-A OUTPUT -j ACCEPT

```

..  you appear to be posting some direct commands for ethernet port (eth0) .. I have no ethernet[0] setup. this is a remote server setup & the commands are being put into a loaded file... but you did give me an idea to try by using something similar for port 80 which I will attempt to find the correct syntax.

---

### Post by chadk5utc on 2012-09-25
Yes -A OUTPUT -j ACCEPT does allow All out, however I would only allow what I need no more no less. Yes I used port 80 as a reference but you should be able to change the port to suit your needs. Even on a remote machine if you type the command ifconfig(as sudo or root) you should see a couple blocks of information and the first line should look like this: eth0      Link encap:Ethernet ...This info would be helpful when creating your rules. I use eth0 as this is default on my server, yours maybe different. Your ethernet device will be the very first thing listed.

---

### Post by underdogz on 2012-09-26
Chadk5utc,

  Thanks again for helping me out btw. 
  It is venet0 for my interface.. Ok I have omitted the rule to allow all outgoing traffic & allowed outgoing traffic on only the ports I am using with tcp established. Should I configure both source & destination for this setting (all used ports)? 

  Also which default ports are normally used for other OS functions? ie. DHCP, DNS, etc.  I am told port 53 is mandatory for DNS .. DHCP is 67, 68 UDP, etc.. I use a different port for ssh other than 22 so should I have a drop command for port 22?

Thank you.

```

*filter
-A INPUT -p tcp -m tcp --dport 22 -j DROP
-A INPUT -p tcp -m tcp -m multiport -j ACCEPT --dports 80,443,8089
-A OUTPUT -p udp -m udp -m multiport -j ACCEPT --dports 67,68
-A INPUT -p tcp -m tcp --dport 53 --sport 53 -j ACCEPT
-A INPUT -p udp -m udp --dport 53 --sport 53 -j ACCEPT
-A OUTPUT -p tcp -m tcp --dport 53 --sport 53 -j ACCEPT
-A OUTPUT -p udp -m udp --dport 53 --sport 53 -j ACCEPT
-A INPUT -p tcp -m tcp -m multiport -m state --state NEW,ESTABLISHED -j ACCEPT --dports 10852,56325
-A OUTPUT -p tcp -m tcp -m multiport -m state -m physdev --state ESTABLISHED -j ACCEPT --dports 80,443,3306,8089,10852,56325 --physdev-out venet0
-A OUTPUT -j REJECT
-A INPUT -j REJECT
COMMIT

```

---

### Post by chadk5utc on 2012-09-26
ok heres what I do with my own rules. First I change the default policy 
# Set Default policy
iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT DROP
This is the recommended way and I believe the most secure way. Then add your rules to ALLOW only the services and ports your need. Keep in mind I would test these on a local machine before they go on a remote machine that you do not have easy access to because if you make a simple mistake you can lock yourself out. If you do not use port 22 for SSH, either remove that rule or simply change the port number to the one you do use. Its good to use non standard port for SSH it really helps cut down on the number of break in attempts. Doing your rules this way you keep it simple and if its not Allowed in your rules its denied by default.

---

### Post by underdogz on 2012-09-26
chadk5utc,

  The first set of commands you gave me worked perfectly by supplementing my interface. Outputs are now specific including lo .. everything is working as it should.

  The recommended way that I have read on the ubuntu website is to save it to a file where it can be tested first & then initiated. It can be optionally loaded at boot when the configuration for at least the ssh terminal & perhaps port 80 are tested as correct. Commands are entered reverse of direct inputs as any accept rules have to be be prior to the final *reject/drop all* commands.
 
Thanks for the help.

---

### Post by chadk5utc on 2012-09-27
Yes your correct you can save all your rules and load them at boot. There are a number of ways to do that. I use scripts when testing rules so that I can load them or unload them as I need to. What else are you having trouble with?

---

### Post by underdogz on 2012-09-27
> **chadk5utc said:**
> Yes your correct you can save all your rules and load them at boot. There are a number of ways to do that. I use scripts when testing rules so that I can load them or unload them as I need to. What else are you having trouble with?

chadk5utc,

  I am not having any troubles with the iptables atm. I want to add logging but I can probably figure it out with various examples I have seen .. that will be another day.

  The next thing I need to figure out is how to get pypmyadmin to function via ssh. Currently I have it tunneled on a specific port to the lo (127.0.0.X) but I have yet to figure out how to get it working properly via ssh. My ssh is a private key file for the moment btw & not registered. Webmin & PuTTY were easy to configure for ssh using a key file but phpmyadmin not so much  (yet).

Thanks.

---

### Post by chadk5utc on 2012-09-27
Ok good what I would do then is go ahead and mark this topic as Solved. and start a new one for SSH tunnel and phpmyadmin as this thread is for security.
Good luck

 Chad

---

### Post by underdogz on 2012-09-27
> **chadk5utc said:**
> Ok good what I would do then is go ahead and mark this topic as Solved. and start a new one for SSH tunnel and phpmyadmin as this thread is for security.
Good luck

 Chad

chadk5utc,

  I figure ssh encryption is a security issue. However I may start a thread on sourceforge if what I have seen on the sourceforge phpmyadmin thread does not work for me.  

To others having connection issues with iptables configuration,
  
  I actually had another issue with establishing connections where it would work at times & then it would have issues other times. It was not consistent until I decided to poke around in my files & imo figured out what was causing the problem.

  The command *sudo ifconfig* only showed 1 interface ( in my case venet0 ) but when I took a look at file: /etc/network/interfaces I saw some logic that changed 3 other interfaces + lo (<-- lo at a specific internal ip) to venet0.
So I had a total of 4 interfaces that I could see it using & therefore made matching rules for all 4 interfaces & also lo (<- 127.0.0.X). 
  This seems to be working for me thus far while testing the connection from different sources. Perhaps this info will help others.

---

### Post by underdogz on 2012-09-27
Actually I will have to flag this thread as unsolved again. It works for a while & then let's say I go away from the computer & come back after 2 hours.. It does not work yet again. This goes for using sites that are made to test the connection from various sources. I just do not get it at all.. If I disable the iptables rules then it works without issue.  What could be happening over time that would stop it from establishing a connection? This seems to only apply to port 80. Atm I am bewildered.

Perhaps established connections is working but not new ones. Putting NEW state makes no difference.

---

