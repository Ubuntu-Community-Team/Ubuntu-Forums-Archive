---
title: "Has not passed the Grc test using Gufw what is wrong?"
date: 2012-01-27
forum: Security
---

### Post by livre1 on 2012-01-27
He says he could contact the machine and know that I'm online (stealth is not working, and maybe sending ping response).


Using Firestater I passed the test.

More than I've been reading and unsafe use Firestarter because it is no longer updated.

I am using Ubuntu 10.04.

---

### Post by Dangertux on 2012-01-27
> **livre1 said:**
> He says he could contact the machine and know that I'm online (stealth is not working, and maybe sending ping response).


Using Firestater I passed the test.

More than I've been reading and unsafe use Firestarter because it is no longer updated.

I am using Ubuntu 10.04.

First off, this is going to seem extremely harsh. However, I'm so tired of hearing about GRC. GRC sucks, and is pretty much a marketing site designed to sell Zone Alarm subscriptions.

#1 There is NO SUCH THING AS "STEALTH" it's a term Steve Gibson (the owner/founder/proliferator of Gibson Research Corporation) made up. It just doesn't work that way, I've explained it dozens of times on this forum so if you're curious, just use the search function or google.

That being said, if for whatever reason you don't have a router between your Ubuntu machine and the Internet and still want to appear "stealth" which again, means NOTHING. You may do the following

```

sudo vi /etc/ufw/before.rules

```or if you prefer a graphical text editor 

```

gksudo gedit /etc/ufw/before.rules

```Find this block of rules.

```

# ok icmp codes
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-input -p icmp --icmp-type source-quench -j ACCEPT
-A ufw-before-input -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-input -p icmp --icmp-type parameter-problem -j ACCEPT
-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT

```Change them to look like this...

```

# ok icmp codes
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-input -p icmp --icmp-type source-quench -j ACCEPT
-A ufw-before-input -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-input -p icmp --icmp-type parameter-problem -j ACCEPT
-A ufw-before-input -p icmp --icmp-type echo-request -j DROP

```Then restart UFW

```

sudo ufw disable && sudo ufw enable 

```Retest on GRC and defeat the silly little port scanner (which still means nothing).

Hope this helps.

---

### Post by livre1 on 2012-01-30
The safety problem or failure that compromises the security to continue using the Firestater?



Thank you.

---

### Post by Dangertux on 2012-02-01
Firestarter is no longer in development , is not supported and conflicts with UFW/GUFW by default. However, if you wish to use Firestarter it does everything UFW/GUFW do.

The choice is yours, however you will have more problems getting support for Firestarter.

Hope this helps.

---

### Post by livre1 on 2012-02-04
Ok, I installed Gufw and I'll stay with him.

Thank you.

---

### Post by haqking on 2012-02-04
> **livre1 said:**
> Ok, I installed Gufw and I'll stay with him.

Thank you.

ahhh good old GRC, nice to see it pop up AGAIN ! LOL

make sure you removed firestarter as if you are using UFW/GUFW  they will cause a conflict.

Cheers

---

### Post by 0011235813 on 2012-02-07
> First off, this is going to seem extremely harsh. However, I'm so tired of hearing about GRC. GRC sucks, and is pretty much a marketing site designed to sell Zone Alarm subscriptions.
The truth doesn't care whether people find it harsh or not, so don't worry about it...

> #1 There is NO SUCH THING AS "STEALTH" it's a term Steve Gibson (the owner/founder/proliferator of Gibson Research Corporation) made up. It just doesn't work that way, I've explained it dozens of times on this forum so if you're curious, just use the search function or google.
Seconded. The job of stealth is down to anonymity proxy servers like tor (is it *sudo apt-get install tor-network-tools* and IP: 127.0.0.1 Port: 9050 ?). A firewall can't convince the server you're accessing you don't exist. 

> That being said, if for whatever reason you don't have a router between your Ubuntu machine and the Internet and still want to appear "stealth" which again, means NOTHING. You may do the following

```

sudo vi /etc/ufw/before.rules

```or if you prefer a graphical text editor 

```

gksudo gedit /etc/ufw/before.rules

```Find this block of rules.

```

# ok icmp codes
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-input -p icmp --icmp-type source-quench -j ACCEPT
-A ufw-before-input -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-input -p icmp --icmp-type parameter-problem -j ACCEPT
-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT

```Change them to look like this...

```

# ok icmp codes
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-input -p icmp --icmp-type source-quench -j ACCEPT
-A ufw-before-input -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-input -p icmp --icmp-type parameter-problem -j ACCEPT
-A ufw-before-input -p icmp --icmp-type echo-request -j DROP

```Then restart UFW

```

sudo ufw disable && sudo ufw enable 

```Retest on GRC and defeat the silly little port scanner (which still means nothing).

Hope this helps.
Note: The computer-wizard above knows what they are talking about. You could do by listening. (Oh and Dangertux is talking about disabling PING requests by the way)

> **livre1 said:**
> The safety problem or failure that compromises the security to continue using the Firestater?



Thank you.
Old, and it disables ufw everytime you re-boot, suspend or hibernate.
> **Dangertux said:**
> Firestarter is no longer in development , is not supported and conflicts with UFW/GUFW by default. However, if you wish to use Firestarter it does everything UFW/GUFW do.

The choice is yours, however you will have more problems getting support for Firestarter.

Hope this helps.

> **livre1 said:**
> Ok, I installed Gufw and I'll stay with him.

Thank you.
I personally prefer ufw, it's faster using a CLI and honestly, I find remembering a few simple commands much easier than navigating a complex GUI.
> **haqking said:**
> ahhh good old GRC, nice to see it pop up AGAIN ! LOL

make sure you removed firestarter as if you are using UFW/GUFW  they will cause a conflict.

Cheers

Somebody should report that site....

---

### Post by CharlesA on 2012-02-07
> **0011235813 said:**
> 
Somebody should report that site....

Wouldn't really do much good. It's fairly useful, but you just need to know that there is no such thing as "stealth" and that closed = "stealth" for all intents and purposes.

Stealth is just a marketing term so they can sell you stuff.

---

### Post by OpSecShellshock on 2012-02-08
And there's also [this]("http://attrition.org/errata/charlatan/steve_gibson/").

---

### Post by haqking on 2012-02-08
> **OpSecShellshock said:**
> And there's also [this]("http://attrition.org/errata/charlatan/steve_gibson/").

ha ha sums it up nicely.

nice link ;-)

---

### Post by Ms. Daisy on 2012-02-08
> **OpSecShellshock said:**
> And there's also [this]("http://attrition.org/errata/charlatan/steve_gibson/").
Wow. Someone is truly dedicated to debunking Steve Gibson. 

>  If you are on a laptop or a using a reduced window to browse the web, these pages may be fugly. Deal with it. 

attrition.org staff, system and respective pets are **NOT** upbeat people. Deal.

Oh, I'm bookmarking this one.

---

### Post by JKyleOKC on 2012-02-12
> **CharlesA said:**
> Stealth is just a marketing term so they can sell you stuff.There's another point that we should probably emphasize in these discussions of "stealth" versus "closed." That's the different effect they have on communications.

The tcp/ip protocols are designed to deal with noisy networks in which single packets may well get dropped. When that happens, the receiving end fails to acknowledge receipt, so the sending end sends the packet again after waiting for some specified period of time (the timeout value, set by the sender's administrators).

If the receiver is configured for "stealth" operation, that's the same as a dropped packet so far as the sender can tell, so it will be re-transmitted. Probably several times. This can "clog your pipe" and make the circuit slower; I've seen the speed rating cut in half by high packet loss.

If the receiver is configured for "closed" instead, the sender will be notified that the packet arrived but was rejected. Most sites will stop at that point and move on to someone else.

Bottom line: using REJECT rather than DROP actually improves performance of one's system, and in these days the bad guys really don't care whether the addresses they use are valid or not so there's no need to try to hide the fact that you are on line.

---

### Post by Ms. Daisy on 2012-02-12
JKyleOKC- that was a very clear and simple explanation.  Thanks!

---

### Post by CharlesA on 2012-02-12
> **JKyleOKC said:**
> 
Bottom line: using REJECT rather than DROP actually improves performance of one's system, and in these days the bad guys really don't care whether the addresses they use are valid or not so there's no need to try to hide the fact that you are on line.

Nice post. I switched from using drop to using reject a while ago. I think it does something like reject the packet with a error of "no route to host" or some such thing.

Helps with diagnostics too.

---

### Post by Dangertux on 2012-02-12
> **CharlesA said:**
> Nice post. I switched from using drop to using reject a while ago. I think it does something like reject the packet with a error of "no route to host" or some such thing.

Helps with diagnostics too.

You can change the behavior netfilter exhibits when rejecting a packet as well, making it the best choice for troubleshooting and packet control

For instance

```

iptables -A INPUT -j REJECT --reject-with tcp-reset

```

Will reject a packet with a simple RST packet (note this only applies to tcp connections)

Where..

```

iptables -A INPUT -j REJECT --reject-with icmp-host-unreachable

```

Will generate behavior more closely associated with "stealthed ports"

Hope this helps.

---

### Post by CharlesA on 2012-02-12
Thanks DT. I think the CentOS box I played with used the --reject-with icmp-host-unreachable setting.

---

### Post by JKyleOKC on 2012-02-12
> **CharlesA said:**
> I switched from using drop to using reject a while ago. I think it does something like reject the packet with a error of "no route to host" or some such thing.

Helps with diagnostics too.Here's what the man page for iptables says about the REJECT target:

> REJECT

This is used to send back an error packet in response to the matched packet: otherwise it is equivalent to DROP so it is a terminating TARGET, ending rule traversal. This target is only valid in the INPUT, FORWARD and OUTPUT chains, and user-defined chains which are only called from those chains. The following option controls the nature of the error packet returned:

--reject-with *type*
  The *type* given can be  **icmp-net-unreachable,  icmp-host-unreachable, icmp-port-unreachable, icmp-proto-unreachable, icmp-net-prohibited, icmp-host-prohibited** or **icmp-admin-prohibited** which return the appropriate ICMP error message (**port-unreachable** is the default). The option **tcp-reset** can be used on rules which only match the TCP protocol: this causes a TCP RST packet to be sent back. This is mainly useful for blocking ident (113/tcp) probes which frequently occur when sending mail to broken mail hosts (which won't accept your mail otherwise).

---

### Post by CharlesA on 2012-02-12
Thanks, that clears it up.

---

