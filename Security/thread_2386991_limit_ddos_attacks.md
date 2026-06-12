---
title: "limit ddos attacks"
date: 2018-03-13
forum: Security
---

### Post by delfiler on 2018-03-13
now i have this line of code to prevent DDoS attacks but i and my colleges think it will limit access to the website as well the code is as following:
```
$IPTABLES -A INPUT -p tcp -i eth1 -m multiport --dports 20,21,53,69,80,119,443,8080 -m limit --limit 60/minute --limit-burst 125 -j ACCEPT
```
now we already suspect it might be for too many ports already, but the main concern is that we might block everyone instead of just DDoS attacks

we also have a code to prevent SSH attacks which we know will work since we took that from a LAN network which also provided internet access to the users, the code of it is as following:
```
#trusted SSh IPs
$IPTABLES -N SSH_WHITELIST
$IPTABLES -A SSH_WHITELIST -s <ip of trusted pc> -m recent --remove --name SSH -j ACCEPT
#brute force SSH blocker
$IPTABLES -A INPUT -p tcp --dport 22 -m state --state NEW -m recent --set --name SSH -j ACCEPT
$IPTABLES -A INPUT -p tcp --dport 22 -m state --state NEW -j SSH_WHITELIST
$IPTABLES -A INPUT -p tcp -i eth1 -m multiport --dport 22,220 -m state --state NEW -m recent --update --seconds 60 --hitcount 4 --rttl --name SSH -j DROP
```

we hope you the comunity can help us out with this issue

---

### Post by slickymaster on 2018-03-13
*Thread moved to **Security**.*

---

### Post by #&amp;thj^% on 2018-03-13
DDoS attacks are complex.

There are many different types of DDoS and it&#8217;s close to impossible to maintain **signature-based rules** against all of them.

I love this site to help me, but my needs differ from your's
Others may have more suggestion tips here also.
Have a Look:[https://javapipe.com/ddos/blog/iptables-ddos-protection/](https://javapipe.com/ddos/blog/iptables-ddos-protection/)
Well worth the read. ;)

---

### Post by Doug S on 2018-03-13
> **delfiler said:**
> now i have this line of code to prevent DDoS attacks but i and my colleges think it will limit access to the website as well the code is as following:
```
$IPTABLES -A INPUT -p tcp -i eth1 -m multiport --dports 20,21,53,69,80,119,443,8080 -m limit --limit 60/minute --limit-burst 125 -j ACCEPT
```
now we already suspect it might be for too many ports already, but the main concern is that we might block everyone instead of just DDoS attacks

Yes, that rule, and even though many references suggest it, will have the opposite effect to what is desired. It tends to deny legitimate users as the DDOS sources take all available connections. Why? Because it is connection based and not IP based.

1fallen is correct that there is little you can do, but you could try some mitigation via a recent module based method. You can increase the recent table sizes and length from the defaults and even use a carry out method into another table to increase the limits.

> **delfiler said:**
> we also have a code to prevent SSH attacks which we know will work since we took that from a LAN network which also provided internet access to the users, the code of it is as following:
```
#trusted SSh IPs
$IPTABLES -N SSH_WHITELIST
$IPTABLES -A SSH_WHITELIST -s <ip of trusted pc> -m recent --remove --name SSH -j ACCEPT
#brute force SSH blocker
$IPTABLES -A INPUT -p tcp --dport 22 -m state --state NEW -m recent --set --name SSH -j ACCEPT
$IPTABLES -A INPUT -p tcp --dport 22 -m state --state NEW -j SSH_WHITELIST
$IPTABLES -A INPUT -p tcp -i eth1 -m multiport --dport 22,220 -m state --state NEW -m recent --update --seconds 60 --hitcount 4 --rttl --name SSH -j DROP
```

we hope you the comunity can help us out with this issueWhat you are doing there doesn't make sense to me. If you have a whitelist check it first, and never add the IP to the SSH list in the first place. Also, 60 seconds is way way to short, because they tend to come back. I use one day. In the last few years, China in particular, once blocked, just comes back using the different IP address on the same sub-net, so consider to use a sub-net mask. The only other suggestion that once someone gets on you SSH badguy list, why not block them from everything, not just SSH?
Example (without the sub-net stuff):
```
# Dynamic Badguy List. Detect and DROP Bad IPs that do password attacks on SSH.
# Once they are on the BADGUY list then DROP all packets from them.
# Sometimes make the lock time very long. Typically to try to get rid of coordinated attacks from China.
$IPTABLES -A INPUT -i $EXTIF -m recent --update --hitcount 3 --seconds 90000 --name BADGUY_SSH -j LOG --log-prefix "SSH BAD:" --log-level info
$IPTABLES -A INPUT -i $EXTIF -m recent --update --hitcount 3 --seconds 90000 --name BADGUY_SSH -j DROP
$IPTABLES -A INPUT -i $EXTIF -p tcp -m tcp --dport 22 -m recent --set --name BADGUY_SSH -j ACCEPT

```
Oh, I would also suggest to change the default number of authorization attempts in sshd_config:
```
#Limit the number of bad passwords per connection to 2. Default is 6.
#Then the iptables connection counter will kick in sooner to drop
#password attack hackers.
MaxAuthTries 2

```

EDIT: You can also review some iptables scripts I did for someone on [askubuntu.com]("https://askubuntu.com/questions/869205/how-to-stop-the-synattack/870032#870032") one time.

---

### Post by delfiler on 2018-03-14
> **Doug S said:**
> Yes, that rule, and even though many references suggest it, will have the opposite effect to what is desired. It tends to deny legitimate users as the DDOS sources take all available connections. Why? Because it is connection based and not IP based.
well isn't that just a bummer, so that will be removed for my script now i know it does the opposite of what i desired

> **Doug S said:**
> 1fallen is correct that there is little you can do, but you could try some mitigation via a recent module based method. You can increase the recent table sizes and length from the defaults and even use a carry out method into another table to increase the limits.
well i will look into it, i am more then glad enough to limit the DOS attacks, that in the case that we are hit, that it can't just eat our bandwidth (which i asume it will for some percentage) completely and that we can just flick it off and block it for the time being as DOS attack is mostly done by unknown victims of infected pc's, at least that is what is told to me on my school 

> **Doug S said:**
> What you are doing there doesn't make sense to me. If you have a whitelist check it first, and never add the IP to the SSH list in the first place. Also, 60 seconds is way way to short, because they tend to come back. I use one day. In the last few years, China in particular, once blocked, just comes back using the different IP address on the same sub-net, so consider to use a sub-net mask. The only other suggestion that once someone gets on you SSH badguy list, why not block them from everything, not just SSH?
Example (without the sub-net stuff):
```
# Dynamic Badguy List. Detect and DROP Bad IPs that do password attacks on SSH.
# Once they are on the BADGUY list then DROP all packets from them.
# Sometimes make the lock time very long. Typically to try to get rid of coordinated attacks from China.
$IPTABLES -A INPUT -i $EXTIF -m recent --update --hitcount 3 --seconds 90000 --name BADGUY_SSH -j LOG --log-prefix "SSH BAD:" --log-level info
$IPTABLES -A INPUT -i $EXTIF -m recent --update --hitcount 3 --seconds 90000 --name BADGUY_SSH -j DROP
$IPTABLES -A INPUT -i $EXTIF -p tcp -m tcp --dport 22 -m recent --set --name BADGUY_SSH -j ACCEPT

```
okay will make use of your sugestion to see how it works out, but i do have a question before i implement it. what if, by total accident, me or my colleges lock ourselves out? we don't want to be locked out all day, is there a way to let us on sooner? i know it might be obvious to you but i am a recent hire and i worked just a few times with ubuntu and iptables. what i am guessing is that i have to remove myself from the, as you name it, "SSH BAD" log file to grant myself acces again

EDIT: to clarafy i am going to use this ^ code but is that supose to run in cojunction with my code? this one:
```
#trusted SSH IPs
$IPTABLES -N SSH_WHITELIST
$IPTABLES -A SSH_WHITELIST -s 192.168.1.105 -m recent --remove --name SSH -j ACCEPT

$IPTABLES -A INPUT -p tcp -i eth1 -m multiport --dport 22 -m state --state NEW -m recent --set --name SSH -j ACCEPT
$IPTABLES -A INPUT -p tcp -i eth1 -m multiport --dport 22 -m state --state NEW -j SSH_WHITELIST
$IPTABLES -A INPUT -p tcp -i eth1 -m multiport --dport 22 -m state --state NEW -m recent --update --seconds 60 --hitcount 4 --rttl --name SSH -j ULOG --ulog-prefix "SSH_brute_force"
$IPTABLES -A INPUT -p tcp -i eth1 -m multiport --dport 22 -m state --state NEW -m recent --update --seconds 60 --hitcount 4 --rttl --name SSH -j DROP
```
EDIT3: **scrap that ^ this allows other pc's aswell which isn't the meaning, but your code is fine except for the problems below this text**


EDIT2: well seems like the code you suggested doesn't want to work cause i get this back when i update/run the script, with your added lines of code:
Bad argument `recent'
Bad argument `recent'
Bad argument `tcp'

> **Doug S said:**
> 
Oh, I would also suggest to change the default number of authorization attempts in sshd_config:
```
#Limit the number of bad passwords per connection to 2. Default is 6.
#Then the iptables connection counter will kick in sooner to drop
#password attack hackers.
MaxAuthTries 2

```
way ahead of you on that one, also made a time limit to fill in the password

---

### Post by Doug S on 2018-03-14
> **delfiler said:**
> EDIT2: well seems like the code you suggested doesn't want to work cause i get this back when i update/run the script, with your added lines of code:
Bad argument `recent'
Bad argument `recent'
Bad argument `tcp'
Hmmm... I copied that directly from my own iptables script. However, I forgot to show the definitions:```
# The location of the iptables program
#
IPTABLES=/sbin/iptables

#Setting the EXTERNAL and INTERNAL interfaces and addresses for the network
#
EXTIF="enp4s0"
INTIF="enp2s0"
EXTIP="XXX.YYY.ZZZ.AAA"
INTNET="192.168.111.0/24"
INTIP="192.168.111.1/32"
UNIVERSE="0.0.0.0/0"

```Otherwise post your version of the code.

If you are interested I'll PM you a link to my entire iptables script. (while available from my web site, I don't advertise the link)

---

### Post by Doug S on 2018-03-14
Opps, I forgot to answer your other question:

> **delfiler said:**
> okay will make use of your sugestion to see how it works out, but i do have a question before i implement it. what if, by total accident, me or my colleges lock ourselves out? we don't want to be locked out all day, is there a way to let us on sooner? i know it might be obvious to you but i am a recent hire and i worked just a few times with ubuntu and iptables. what i am guessing is that i have to remove myself from the, as you name it, "SSH BAD" log file to grant myself acces again

Yes, you have to be careful, or you can lock yourself out. I no longer travel for business, but I did lock myself out once while away, and had to wait a day. For me the trade-off was worth it. For you it might not be.

---

### Post by delfiler on 2018-03-14
> **Doug S said:**
> [COLOR=#000000]Yes, you have to be careful, or you can lock yourself out. I no longer travel for business, but I did lock myself out once while away, and had to wait a day. [/COLOR]For me the trade-off was worth it. For you it might not be.
haha what i meant indeed and for now my pc (as we are still testing on a test server) is the only one with acces to the system, we do have a monitor and such hanging on the server itself, so you could call it a walk of shame when you lock yourself out and need to give yourself acces again

---

### Post by delfiler on 2018-03-14
> **Doug S said:**
> Otherwise post your version of the code.
how do you mean that? like my entire code/script i wrote in iptables (i do have to warn you it is a lot!)

> **Doug S said:**
> If you are interested I'll PM you a link to my entire iptables script. (while available from my web site, I don't advertise the link)
yeah sure might snip somethings out of it to use in my code, i do that all the time with my current colleges, sometimes it is just the tiniest difference that can help

---

