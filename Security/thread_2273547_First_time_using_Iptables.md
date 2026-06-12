---
title: "First time using Iptables"
date: 2015-04-13
forum: Security
---

### Post by samer4 on 2015-04-13
I am definitely new to use ubuntu and I am trying to configure my firewall on the server for a group project.

After research I decided to go with whitelisting

so far I have this

iptables &#8211;F                            
           
iptables -P INPUT DROP                 
iptables -P FORWARD DROP
iptables &#8211;P OUTPUT DROP
 
iptables &#8211;L &#8211;n           
 
iptables &#8211;A INPUT &#8211;p tcp --dport ssh &#8211;j ACCEPT
iptables _A INPUT  -p tcp --dport 80 &#8211;j ACCEPT

what else should I add to make sure that my server is secure?

---

### Post by Lars Noodén on 2015-04-14
You'll need to allow DNS out and should allow ping in.  For HTTPS you'll also need port 443.  Try logging blocked packets and watch the logs as you start and begin to use the various services.  You'll see what else to add.

---

### Post by samer4 on 2015-04-14
**What rules can I add to make my iptables more secure?**

---

### Post by Lars Noodén on 2015-04-14
What kind of passwords?  iptables only deals with packets going to or from certain ports not the contents of those packets.

> **samer4 said:**
> iptables -A INPUT -p tcp --dport 80 -m limit --limit 25/minute --limit-burst 100 -j ACCEPT


The INPUT rule with a limit should replace the the original INPUT rule for that port.  Also, you may want one for HTTPS.  

Also, you might want to replace some of the reply rules with ones near the beginning that don't allow new connections but only established (or related) connections.  

```

   iptables -A INPUT -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
   iptables -A OUTPUT -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT

```

Then at the tail end of your INPUT and OUTPUT chains you might want a catchall rule that REJECTs the packets so that you don't get stuck waiting for the timeout on each packet.

---

### Post by HermanAB on 2015-04-14
Just a few general tips:
IPtables does exactly what you tell it to do - no more and no less.
IPtables processes the rules from the top down.
The order of the rules is important 
(If you accept or drop something at the top, then adding more rules about it at the bottom will do nothing)
-I will insert a rule at the top of the list.
-A will insert a rule at the bottom of the list.

Finally, read the iptables man page about ten times.  It will eventually make some sense.

When working on a remote server over SSH, create a little script that will flush all rules in iptables, then make a cron job and set it to run in 1 hour.  When you screw up (not if - when), it will allow you to get back in again.  If you are miraculously done without incident, remember to delete this cron job.

Don't panic, but you should always know where your towel is...

---

### Post by Doug S on 2015-04-14
I'll throw in my 2 cents worth on this one:> **samer4 said:**
> iptables –A INPUT –p tcp --dport ssh –j ACCEPTI would never do that. I have used this for many years now (and posted it on these forums many times):```
# Secure Shell on port 22.
#
# Dynamic Badguy List. Detect and DROP Bad IPs that do password attacks on SSH.
# Once they are on the BADGUY list then DROP all packets from them.
#$IPTABLES -A INPUT -i $EXTIF -m recent --update --hitcount 3 --seconds 5400 --name BADGUY_SSH -j LOG --log-prefix "SSH BAD:" --log-level info
#$IPTABLES -A INPUT -i $EXTIF -m recent --update --hitcount 3 --seconds 5400 --name BADGUY_SSH -j DROP
# Sometimes make the lock time very long. Typically to try to get rid of coordinated attacks from China.
$IPTABLES -A INPUT -i $EXTIF -m recent --update --hitcount 3 --seconds 90000 --name BADGUY_SSH -j LOG --log-prefix "SSH BAD:" --log-level info
$IPTABLES -A INPUT -i $EXTIF -m recent --update --hitcount 3 --seconds 90000 --name BADGUY_SSH -j DROP
$IPTABLES -A INPUT -i $EXTIF -p tcp -m tcp --dport 22 -m recent --set --name BADGUY_SSH -j ACCEPT
```> **samer4 said:**
> iptables -A OUTPUT -p icmp --icmp-type echo-request -j ACCEPT
iptables -A INPUT -p icmp --icmp-type echo-reply -j ACCEPTAt times ping can be a very useful debugging tool, I would allow it in, but  I use a trick to get rid of most of the unwanted stuff, I only allow it if the payload length is long enough.```
#
# Generic ICMP echo request DROP if the packet total length is not >= 128 bytes (rev 1.13 256 bytes)
# ... 0 & 0XFF80 = 0" in this case the third part, the total length check mask gives < any 128 bytes will be TRUE for test condition.
#
#$IPTABLES -A INPUT -i $EXTIF -m u32 --u32 "6 & 0xFF = 1 && 0 >> 22 & 0x3C @ 0 >> 24 = 8 && 0 & 0XFF80 = 0" -j DROP
$IPTABLES -A INPUT -i $EXTIF -m u32 --u32 "6 & 0xFF = 1 && 0 >> 22 & 0x3C @ 0 >> 24 = 8 && 0 & 0XFF00 = 0" -j DROP
# Drop ICMP ICMP time stamp query.
$IPTABLES -A INPUT -i $EXTIF -m u32 --u32 "6 & 0xFF = 1 && 0 >> 22 & 0x3C @ 0 >> 24 = 13" -j DROP
# external interface, from any source, for any remaining ICMP traffic is valid
$IPTABLES -A INPUT -i $EXTIF -p ICMP -s $UNIVERSE -d $EXTIP -j ACCEPT
```> **samer4 said:**
> P**revent DOS attack**
iptables -A INPUT -p tcp --dport 80 -m limit --limit 25/minute --limit-burst 100 -j ACCEPTEven though one sees that rule everywhere, I can not begin to stress how deeply I hate it. Why? Because if your server does come under a DOS attack, or even just a site copy bot, the rule will tend to block the real visitors, whereas the attacker or bot will tend to get any newly available connections and re-trip the rule. While it is somewhat complicated. I use a method, that identifies and punishes the bad buy, while leaving the good guys alone. Interested readers can find my entire iptables rule set at:
double u double u double u dot smythies dot com /~doug/network/iptables_notes/doug_firewall.current.txt

References:
[http://www.thatsgeeky.com/2011/02/escalating-consequences-with-iptables/](http://www.thatsgeeky.com/2011/02/escalating-consequences-with-iptables/)

---

### Post by HermanAB on 2015-04-14
> Prevent DOS attack
iptables -A INPUT -p tcp --dport 80 -m limit --limit 25/minute --limit-burst 100 -j ACCEPT

That doesn't prevent a DOS attack, since modern DOS attacks are almost always distributed attacks.  However, it does work against all password guessing attacks I have seen, but for that, you should not limit it to port 80.  Leave it open to any port, then it will protect all of your SSH, Web and Mail servers against password brute forcers.

---

### Post by samer4 on 2015-04-15
I appreciate all replies but like I said I am new to this and all these replies went over my head. I just wanted to know simple rules that I should add to my existing iptables to make it more secure. I edited my other post in case my classmates are on here!

---

### Post by HermanAB on 2015-04-15
If it went over your head, then first of all, read the the iptables man page at least ten times.  Seriously.  That is how everybody starts with iptables.  It is not easy, but it will eventually make sense.

---

### Post by Lars Noodén on 2015-04-16
As for getting started, keep in mind that each chain is a sequence of if-then statements that the packet is checked against.  On the way in, this is the INPUT chain and the way out it is the OUTPUT chain.

After at least skimming the manual pages for [iptables](http://manpages.ubuntu.com/manpages/trusty/en/man8/iptables.8.html), I'd look at the online [Iptables Tutorial](https://www.frozentux.net/documents/iptables-tutorial/) by Oskar Andreasson.  It's a bit old, so for details, I'd check the manual page for [iptables-extensions](http://manpages.ubuntu.com/manpages/trusty/en/man8/iptables-extensions.8.html) for the latest.  But for the intro parts, it's fine.  Read at least the first parts.

---

