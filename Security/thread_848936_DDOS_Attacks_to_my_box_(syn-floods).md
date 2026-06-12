---
title: "DDOS Attacks to my box (syn-floods)"
date: 2008-07-04
forum: Security
---

### Post by Salmus on 2008-07-04
Hello,

I'm a webhosting service provider, and I chouse Ubuntu to rule my servers ... very easy to maintain and a very stable distribution in my opinion.

I have some problems regarding Ddos Attacks, some weeks ago I received a phone call from an suspicios person - and he said that he will flood me - until I pay him to let me down.

Now, almost everyday I get syn-floods (ddos attacks) I've tried to use Ddos Deflate, but with no succes - I wrote my own bash script who limit the connections over X - again ... no succes - activated syn cookies - no luck :( 

My graphs are like this :

[IMG]http://www.hdimages.org/images/ekaoh6miv3ie3hyuvk9.png[/IMG]
[IMG]http://www.hdimages.org/images/6ql4n5mzkvptn5kt5il7.png[/IMG]
[IMG]http://www.hdimages.org/images/35dadr8vaekx9k1p3au.png[/IMG]
[IMG]http://www.hdimages.org/images/kkpm1mtb4xp96pkklf9a.png[/IMG]
[IMG]http://www.hdimages.org/images/hfhmus9ungplamcvmlmb.png[/IMG]
[IMG]http://www.hdimages.org/images/2ynzniczysa9dhi9dlfn.png[/IMG]


Please ... help ! :(

---

### Post by kevdog on 2008-07-04
Are the DDOS attacks coming from one ip address or a group of known ip addresses or are they seemingly random?  You have tried using iptables setting up limits to accepting incoming connections?

---

### Post by Salmus on 2008-07-04
> **kevdog said:**
> Are the DDOS attacks coming from one ip address or a group of known ip addresses or are they seemingly random?  You have tried using iptables setting up limits to accepting incoming connections?


They'r comming from different IP's sometimes ...

I've tried:

iptables -N SYN_FLOOD
iptables -A SYN_FLOOD -p tcp --syn -j SYN_FLOOD
iptables -A SYN_FLOOD -m limit --limit 5/s --limit-burst 100 -j RETURN
iptables -A SYN_FLOOD -j LOG --log-prefix "IPT SYN_FLOOD: "
iptables -A SYN_FLOOD -j DROP

No luck

Also:
iptables -I INPUT -p tcp --dport 22 -i eth0 -m state --state NEW -m recent \
  --set

iptables -I INPUT -p tcp --dport 22 -i eth0 -m state --state NEW -m recent \
  --update --seconds 15 --hitcount 100 -j DROP


No luck :(

---

### Post by kevdog on 2008-07-04
Not meaning to insult you, but are you passing packets from the INPUT chain to the SYN_FLOOD chain?  Is your kern.log showing anything being logged?

---

### Post by Salmus on 2008-07-04
Yes, with:

iptables -I INPUT -j SYN_FLOOD

Isn't good?

system just hangs ... going to 100% wait

```

Jul  4 08:42:07 Webhosting-Node1 kernel: [ 8688.603685] possible SYN flooding on port 80. Sending cookies.
Jul  4 08:44:41 Webhosting-Node1 kernel: [ 8842.379628] possible SYN flooding on port 80. Sending cookies.
Jul  4 08:45:42 Webhosting-Node1 kernel: [ 8903.996507] possible SYN flooding on port 80. Sending cookies.
Jul  4 08:52:40 Webhosting-Node1 kernel: [ 9321.617772] possible SYN flooding on port 80. Sending cookies.
Jul  4 08:53:56 Webhosting-Node1 kernel: [ 9396.745260] possible SYN flooding on port 80. Sending cookies.
Jul  4 08:58:53 Webhosting-Node1 kernel: [ 9694.057767] possible SYN flooding on port 80. Sending cookies.
Jul  4 09:02:00 Webhosting-Node1 kernel: [ 9880.878989] possible SYN flooding on port 80. Sending cookies.
Jul  4 09:03:02 Webhosting-Node1 kernel: [ 9940.853721] possible SYN flooding on port 80. Sending cookies.
Jul  4 09:20:18 Webhosting-Node1 kernel: [10977.513728] possible SYN flooding on port 80. Sending cookies.
Jul  4 09:21:19 Webhosting-Node1 kernel: [11038.624777] possible SYN flooding on port 80. Sending cookies.

```



I have a rooter before Webhosting servers, and I've tried:

```

iptables -N FLOOD_PROTECTION
iptables -I FORWARD -d 89.165.150.251 -j FLOOD_PROTECTION

iptables -A FLOOD_PROTECTION -p tcp --syn
iptables -A FLOOD_PROTECTION -p tcp -m state --state NEW -m recent --set
iptables -A FLOOD_PROTECTION -p tcp -m state --state NEW -m recent --update --seconds 15 --hitcount 100 -j DROP

iptables -A FLOOD_PROTECTION -m limit --limit 3/s --limit-burst 100 -j DROP

```


Also with no luck :(


I have a windows software and I use it to flood my servers - to test security.

---

### Post by kevdog on 2008-07-04
Are you loading the rules from a script?

Also excuse my syntax stalwartness, but is this correct:
iptables -I INPUT -j SYN_FLOOD

I looked at the manual:
Command	-I, --insert
Example	iptables -I INPUT 1 --dport 80 -j ACCEPT
Explanation	Insert a rule somewhere in a chain. The rule is inserted as the actual number that we specify. In other words, the above example would be inserted as rule 1 in the INPUT chain, and hence from now on it would be the very first rule in the chain.

Usually the syntax is:
iptables -A INPUT -j SYN_FLOOD


I also dont get these rules, there is no action or target associated with the match statement:
iptables -A FLOOD_PROTECTION -p tcp --syn
iptables -A FLOOD_PROTECTION -p tcp -m state --state NEW -m recent --set

---

### Post by Salmus on 2008-07-04
I was trying to limit num of connections per IP address, like tutorial here: [http://www.debian-administration.org/articles/187](http://www.debian-administration.org/articles/187)

With: -m limit --limit 3/s --limit-burst 100 -j DROP | I limit num of connections GLOBAL, not per IP address. 

Finally, I put iptables -I INPUT to insert the line 1st in the firewall structure, and yes ... I'm using a bash script to define my iptables rules (wrote by hand)

---

### Post by kevdog on 2008-07-04
Ok, I didn't know about the set, update flags -- that was interesting.

However this line by itself doesn't seem to do anything:
iptables -A FLOOD_PROTECTION -p tcp --syn

Finally if you could post your script it would probably be helpful.

Also I'm reading about the concept of recent matches here:
[http://iptables-tutorial.frozentux.net/iptables-tutorial.html#RECENTMATCH](http://iptables-tutorial.frozentux.net/iptables-tutorial.html#RECENTMATCH)

It seems like it might be slightly more complex than the example provided on the debian admin page.

---

