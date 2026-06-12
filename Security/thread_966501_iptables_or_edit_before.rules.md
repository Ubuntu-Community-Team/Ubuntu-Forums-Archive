---
title: "iptables or edit before.rules??"
date: 2008-11-01
forum: Security
---

### Post by Laibcoms on 2008-11-01
I'm trying to understand, or should I say learn more about ufw, firewall, iptables, stuff.  For this one, I am using the ICMP (Ping) Echo request (not that it matters for me, but I just thought it is a good example).. I have some questions however..


Should I use this:
```

sudo iptables -A INPUT -p icmp --icmp-type echo-request -j DROP

```

or should I edit /etc/ufw/before.rules
```

-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT

```

What's the difference?  Isn't the command above "adds" a line to before.rules?

And also, I noticed that commenting the line of code to:
```

#-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT

```

doesn't work as suggested in other forums and ufw tickets (unless I am missing something), if I'm going to use that, should I change it to "DROP"?  (Nope, I wasn't behind a router when I tested this one.)

Thanks ^^

---

### Post by lovinglinux on 2008-11-01
> **Laibcoms said:**
> 
Should I use this:
```

sudo iptables -A INPUT -p icmp --icmp-type echo-request -j DROP

```

or should I edit /etc/ufw/before.rules
```

-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT

```

What's the difference?  Isn't the command above "adds" a line to before.rules?
^

The first command you suggested will add a rule to the iptables INPUT chain while editing /etc/ufw/before.rules will add the rule to ufw-before-input chain.

The iptables has 3 default chains, INPUT, FORWARD and OUTPUT. All traffic passing through your machine network devices will pass through these chains first. The rules inside these chains will decide what to do with every packet received/sent.

When you use the first code above you are creating a rule in the INPUT chain that will drop every icmp echo-request packet. But if you are using ufw, things are different, because ufw create it's own chains and redirect the traffic to them. In this case "ufw-before-input" chain. So to make sure the rule above will work, you should place it above the ufw rules that redirect the traffic. This way, any icmp echo-request packets that arrive to your machine are first filtered by your rule and dropped. Then, if the traffic is not icmp echo-request it will continue in the chain until it reaches the ufw rules that redirect the traffic to ufw chains. If you add your rule to the end of the iptable chain it won't work, because ufw rules will redirect all traffic to it's own chains before the packets reaches your rule.

If you edit the suggested line in /etc/ufw/before.rules instead, the traffic arriving to the INPUT chain will not encounter any rule before the ufw redirection, so all traffic will be redirected to ufw chains. The rules in the ufw chains will determine what to do with each packet. If you edit the icmp line in the /etc/ufw/before.rules to DROP instead of ACCEPT , any icmp echo-request will also be dropped as expected. The difference is the path the packet will follow before reaching the rule that matches it and drop or accept it.

> **Laibcoms said:**
> And also, I noticed that commenting the line of code to:
```

#-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT

```

doesn't work as suggested in other forums and ufw tickets (unless I am missing something), if I'm going to use that, should I change it to "DROP"? 

Commenting this line will only work if you have configured the default behaviour of ufw to deny traffic. So I would recommend replacing ACCEPT with DROP to be safe.

While ufw makes things easier to the user, mixing custom iptable rules with ufw iptable rules can create some confusion and increase the chance of doing something wrong, because of the redirection thing and because ufw uses simplified commands. 

Since you are trying to learn and understand iptables, I would recommend disabling ufw and creating you own rules directly to iptables. Is not that complicated. All you  have to do is create INPUT, FORWARD and OUTPUT rules.

Take a look into these tutorials:

[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

I used them to learn how to create my own iptables scripts a weeks ago. Before that I was using Firestarter, but don't use it anymore. UFW was never enough for me, because it doesn't allow to block outbound traffic.

You can take a look into my rules [[COLOR="Red"]**here**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=957876"). In the first post in that thread I'm still using Firestarter combined with some command-line rules. But you will see that in post #6 I edit all rules by myself.

---

### Post by qrst472 on 2008-11-03
The real evils, indeed, of [wow gold](http://www.wowpowerleveling-wow.com/) Emma's situation were the power of having rather too much her own way, and a disposition to think a little [wow gold](http://www.wow-wowpowerleveling.com/) too well of herself; these were the disadvantages which threatened alloy to her many enjoyments. The danger, however, was at [wow power leveling](http://www.powerleveling-wowgold.com/wow-power-leveling.html) present so unperceived, that they did not by any means rank as misfortunes with her. Sorrow came--a gentle sorrow--but not at all in the shape of any disagreeable consciousness.--Miss Taylor married. It was Miss Taylor's loss which first brought grief. It was on the [wow powerleveling](http://www.wow-wowpowerleveling.com/) wedding-day of this beloved friend that Emma first sat in mournful thought of any continuance. The wedding over, and the bride-people gone, her father and herself were left to dine together, with no prospect of a third to cheer a long evening. Her father composed himself to sleep after dinner, as usual, and she had then only to sit and think of what she had lost.weiwei1978123

---

