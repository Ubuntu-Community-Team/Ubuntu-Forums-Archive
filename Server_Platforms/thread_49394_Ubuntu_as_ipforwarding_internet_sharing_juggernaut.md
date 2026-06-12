---
title: "Ubuntu as ipforwarding internet sharing juggernaut"
date: 2005-07-16
forum: Server Platforms
---

### Post by Spleenie on 2005-07-16
Ok I admit it, I am scared and confused and have not had this difficulty with FreeBSD or Mandrake, which makes me really scared because everything with Ubuntu has been EASIER up until now.

I want to share my ADSL connection. I have eth1 pointing to the adsl modem using ppp0 and all is well, as here I am typing on this page.

I have another NIC, let us call him eth0. he is pointing to a switching hub. To this hub are connected several other computers starved....STARVED...of internet happiness. All is also well with this connection. I am able to happily ping computers on the network from this computer, and they are able to see and log into this computer from there. 

Many, many threads have dealt with the subject of internet connection sharing and IPMasqurading and such, most have recommended firestarter (which I duly installed and ran and it changed nothing).

What I would really like, short of a wonderful ubuntu 5.04 walkthrough on how to make this NIC talk to this other NIC and have internet happiness shared everywhere, is a quick run down on what various files should and should not have in them to ensure success.

Example: 
check that /etc/network/options has ip_forward=yes (which it is btw)
check that both eth0 and eth1 are in ifconfig (which they are) 

and anything else that may be helping/hindering the thing working (eg a rogue firewall somewhere in the system that keeps changing settings or something on rebooting or restarting the network).

Many thanks for reading this far and I hope you are able to help! 

Cheers, Spleenie

---

### Post by geearf on 2005-07-16
Hello,

what line did you use for iptables masquerade ...?

it might be this ?

---

### Post by abood on 2005-07-16
Spleenie,
why u dont go back again to firestarter and im sure it will work 100%, its the easiest and most stable GUI firewall, and plz u had said that "and it changed nothing"
maybe your setting in the firestarter were wrong, plz try it again and i will help you running it correctly and make sure of your internet connection setting in firestarter. another question is your ADSL Dynamic or static and do u got router ?.

---

### Post by Spleenie on 2005-07-16
[QUOTE=geearf]Hello,

what line did you use for iptables masquerade ...?

it might be this ?[/QUOTE]

Which line do you mean and in which file? Do you have an example I could compare my files/lines to?

[QUOTE=abood]Spleenie,
why u dont go back again to firestarter and im sure it will work 100%, its the easiest and most stable GUI firewall, and plz u had said that "and it changed nothing"
maybe your setting in the firestarter were wrong, plz try it again and i will help you running it correctly and make sure of your internet connection setting in firestarter. another question is your ADSL Dynamic or static and do u got router ?.
[/QUOTE]

Yep, running firestarter and getting it to "share internet connection" did nothing. I am usually fearful of changes that GUI's make when they change settings, because I don't know how many settings they change, and what else they are doing. I would rather a CLI mechanism. That being said, if firestarter COULD do it, I wouldn't be too upset. 

Firestarter worked ok as a firewall, recognising both my ppp and eth0 (LAN) interfaces. It just didn't get the sharing thing to work, otherwise it worked fine.

As for type of ADSL, it is static but like I said it is working fine and my computer is directly after the modem, and there is no firmware router involved (ie it isnt one of those 4 port adsl modem router things)

internet -----> ADSL modem ---->(ppp0)  This computer   (eth0)------> switch -----> LAN

---

### Post by geearf on 2005-07-16
hello,

for me this is it : 

more /etc/network/if-up.d/iptables-start
iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE

---

### Post by Spleenie on 2005-07-16
[QUOTE=geearf]hello,

for me this is it : 

more /etc/network/if-up.d/iptables-start
iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE[/QUOTE]

Ok some questions about this file (I don't have it in my if-up.d directory)

1) does this file run at boot? What runs this file? How will it know to look for this file?

2) does the "eth1" in your iptables string refer to the LAN NIC or the ADSL connected NIC?

Thankyou all for your replies so far, they have been much appreciated!

---

### Post by Spleenie on 2005-07-16
[QUOTE=geearf]hello,

for me this is it : 

more /etc/network/if-up.d/iptables-start
iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE[/QUOTE]

Ok some questions about this file (I don't have it in my if-up.d directory)

1) does this file run at boot? What runs this file? How will it know to look for this file?

2) does the "eth1" in your iptables string refer to the LAN NIC or the ADSL connected NIC?

Thankyou all for your replies so far, they have been much appreciated!

Edit: For those who think Firestarter is the answer, I have maintained using it, and love it as a firewall, but it just doesnt seem to be letting me share the internet connection.

I have a feeling geearf may be on the right track, and I don't have iptables working properly. I do have it installed however. Just so everyone knows, I am running Hoary, a lot of the howtos I have come across concern warty and others, using files and commands that don't seem to be present/apply.

/etc/network/if-up.d/iptables-start

```
#!/bin/sh

PATH=/usr/sbin:/sbin:/bin:/usr/bin

#
# delete all existing rules.
#
iptables -F
iptables -t nat -F
iptables -t mangle -F
iptables -X

# Always accept loopback traffic
iptables -A INPUT -i lo -j ACCEPT


# Allow established connections, and those not coming from the outside
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -m state --state NEW -i ! eth1 -j ACCEPT
iptables -A FORWARD -i eth1 -o eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT

# Allow outgoing connections from the LAN side.
iptables -A FORWARD -i eth0 -o eth1 -j ACCEPT

# Masquerade.
iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE

# Don't forward from the outside to the inside.
iptables -A FORWARD -i eth1 -o eth1 -j REJECT

# Enable routing.
echo 1 > /proc/sys/net/ipv4/ip_forward
``` 

Is it possible that firestarter or something else is overwriting these commands later in the boot process? Is it possible that masquerading is not built into my kernel? (!!) I am not getting error messages at all, or else not in places I am looking for them.

My wife gets really cranky when I deprive her of internet, you understand the state I must be in! :)

---

### Post by geearf on 2005-07-17
1) does this file run at boot? What runs this file? How will it know to look for this file?
IT runs at the boot when the connection goes up.
You just need to do a chmod +x on it, or it will not run.
2) does the "eth1" in your iptables string refer to the LAN NIC or the ADSL connected NIC?
eth1 is my ethernet connect to the net.
It might be pppx for you,
give me the return of : route -n

---

### Post by Spleenie on 2005-07-17
[QUOTE=geearf]1) does this file run at boot? What runs this file? How will it know to look for this file?
IT runs at the boot when the connection goes up.
You just need to do a chmod +x on it, or it will not run.
2) does the "eth1" in your iptables string refer to the LAN NIC or the ADSL connected NIC?
eth1 is my ethernet connect to the net.
It might be pppx for you,
give me the return of : route -n[/QUOTE]

It is executable, so I must assume it is running. I am using ppp0 as the internet connection interface.

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
202.154.95.113  0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         202.154.95.113  0.0.0.0         UG    0      0        0 ppp0
``` 

- Spleenie

---

### Post by geearf on 2005-07-17
right then it should be the same but with pp0

---

### Post by Avatar on 2005-07-18
well, I could set my ubuntu as a server quite easly with firestarter.. 

my problem is that the clients can't open some websites

any suggestion?

---

### Post by abood on 2005-07-18
man sorry for the late reply, but  its 3 am and im so sleepy tomorrow i will continue with u but plz before can u check this if its yes or no on 
/etc/network/options

ip_forward=yes
spoofprotect=yes
syncookies=no
 check this settings plz,
regards,
Abood

---

### Post by Spleenie on 2005-07-19
[QUOTE=abood]man sorry for the late reply, but  its 3 am and im so sleepy tomorrow i will continue with u but plz before can u check this if its yes or no on 
/etc/network/options

ip_forward=yes
spoofprotect=yes
syncookies=no
 check this settings plz,
regards,
Abood[/QUOTE]

Check concluded
settings match

I am getting a nasty feeling that Firestarter itself is stopping the thing working, by the ruleset it is applying.

I am away from my server at the moment. Is there a way to check the ruleset that is being applied without using a GUI?

- Spleenie

---

### Post by geearf on 2005-07-19
more /etc/rc.firewall
and you'll see all,
you can also erase this file, and try the command i gave you.

---

### Post by Spleenie on 2005-07-20
[QUOTE=geearf]more /etc/rc.firewall
and you'll see all,
you can also erase this file, and try the command i gave you.[/QUOTE]

I don't seem to have an rc.firewall file.

:)

---

### Post by geearf on 2005-07-21
oh strange, that is the file guarddog created me, i guessed it was the same with firestarter (also it killed my connection because i did not configure it so i had to erase the file for the moment)

---

