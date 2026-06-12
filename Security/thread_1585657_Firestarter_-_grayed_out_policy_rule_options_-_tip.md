---
title: "Firestarter - grayed out policy rule options - tips to beginners"
date: 2010-09-30
forum: Security
---

### Post by Aetixintro on 2010-09-30
I've checked some funny behaviour in Firestarter and Googled it.
Let me clarify:
If you see the policy rule options grayed out/unusable then [SIZE=3]don't panic!
[SIZE=2]Just put your cursor in the fields below and right click then you get the option to apply rules and the rest follow. Ie. the fields of Deny... and Allow...

I must say this is an unnecessary burden to put on the novices even though the experienced users may think it's funny.

Rather, this incredible imposure to demand this curiosity from people, a kind of [SIZE=3]BE INTELLIGENT OR **** OFF[SIZE=2] is really of little help to promote Ubuntu/Linux. While Microsoft Windows is doing all it can for people to be as simple as possible and leave people's workload to their own devices, Ubuntu/Linux [/SIZE][/SIZE]has a lot to pick up on in this area some people can call [SIZE=4]CUSTOMER RESPECT![SIZE=2]

Clearly, if you're an economist or lawyer and want a workable system, purely for doing a computer's work, you choose, logically, the one that's most intuitive and quickest to learn and stable/reliable. Ubuntu/Linux needs to get there as well, simply and uncompromisingly!

However, to finish on a positive note, I must say Lucid Lynx (10.04) is doing great and maintaining many fine respects where Windows is failing on its respects. Ubuntu is doing progress with its latest work and if it adjust slightly to more user-friendly attitudes, it'll beat Windows in no-time! To the future and Ubuntu! :)
[/SIZE][/SIZE] [/SIZE][/SIZE]

---

### Post by holiday on 2010-09-30
Ignore any feeling that people are laughing at you. I have felt that feeling myself and over the years I have learned that the feeling has no import. There are good people here.

Ask your questions simply and clearly, giving as much detail as you can, and if there is a simple answer someone will respond. 

This is the best Linux community I have come across. There are some people who will righteously RTFM at you (like where is it and - uhm what is it saying? - I'm with your there), but that's life. 

I use Firestarter and have not had that problem. There are other iptables interfaces that you may find easier. 

Maybe some good Ubuntu person will post the apt-get.

---

### Post by Paqman on 2010-09-30
> **holiday said:**
> 
I use Firestarter

You should both consider switching to a more up-to-date app if you need a tool to configure your firewall. Firestarter is no longer maintained by anyone, which is not good for a security-related app.

I'd suggest GUFW as a good Ubuntu firewall configuring tool.

---

### Post by uRock on 2010-09-30
Moved to Security Discussions.

You do not need a GUI for the firewall unless your are running server applications. To turn on ubuntu's firewall just run the following command in a terminal.
```
sudo ufw enable
```

To learn more about ufw check out this link. [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

### Post by CharlesA on 2010-09-30
> **Paqman said:**
> You should both consider switching to a more up-to-date app if you need a tool to configure your firewall. Firestarter is no longer maintained by anyone, which is not good for a security-related app.

I'd suggest GUFW as a good Ubuntu firewall configuring tool.

> **uRock said:**
> Moved to Security Discussions.

You do not need a GUI for the firewall unless your are running server applications. To turn on ubuntu's firewall just run the following command in a terminal.
```
sudo ufw enable
```

To learn more about ufw check out this link. [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

+1 to both of those. Firestarter is no longer under development and there are better (imo) ones to use then it (ufw and gufw come to mind).

---

### Post by holiday on 2010-10-01
> **Paqman said:**
> You should both consider switching to a more up-to-date app if you need a tool to configure your firewall. Firestarter is no longer maintained by anyone, which is not good for a security-related app.

I'd suggest GUFW as a good Ubuntu firewall configuring tool.

I can't remember the last time I even looked at firestarter.My firewall's up and seems to be working fine. 

I'd like to script my own iptable rules. Now that would be cool.

---

### Post by uRock on 2010-10-01
> **holiday said:**
> I can't remember the last time I even looked at firestarter.My firewall's up and seems to be working fine. 

I'd like to script my own iptable rules. Now that would be cool.
This should be helpful. [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

### Post by CharlesA on 2010-10-01
> **holiday said:**
> I can't remember the last time I even looked at firestarter.My firewall's up and seems to be working fine. 

I'd like to script my own iptable rules. Now that would be cool.

I just use iptables.

Check this out [here]("http://bodhizazen.net/Tutorials/iptables/").

---

### Post by Aetixintro on 2010-10-01
I just like to note that it's fully possible to run _both_ Firestarter and GUFW. They seem good, both of them. Their underlying program is indeed Iptables as has been noted several places when you search for information on Firestarter and GUFW. Alright. :)

---

### Post by uRock on 2010-10-01
> **Aetixintro said:**
> I just like to note that it's fully possible to run _both_ Firestarter and GUFW. They seem good, both of them. Their underlying program is indeed Iptables as has been noted several places when you search for information on Firestarter and GUFW. Alright. :)
That can cause problems if both have different settings. 

I used to use firestarter. It has a nice GUI and it is nice to be able to see the connections being made. After running port scans against ubuntu with the default UFW enabled I gained the confidence needed to no longer feel it necessary to monitor every port opened by TCP/IP. Whenever I feel the need to see what is going on with the network, I fire up Wireshark and see what connections are being made, which usually proves to be a waste of time.

---

### Post by bodhi.zazen on 2010-10-01
> **Aetixintro said:**
> I just like to note that it's fully possible to run _both_ Firestarter and GUFW. 

No it is not possible to do that. Both tools are front ends for iptables and if you run both they will conflict. In this case, in general, firestarter will overwrite changes you make with ufw. You can see this bu checking your iptables rule set and rebooting (you have to reboot as these tools set your rules when you reboot) or if you start and stop these tools / disable the firewall / etc.

I am not sure what would happen if you try to configure your firewall with both tools at the same time, you would have to try and watch the rules in iptables as you make changes.

```
sudo iptables -L -v -n
```

---

### Post by cariboo on 2010-10-01
> **Aetixintro said:**
> I just like to note that it's fully possible to run _both_ Firestarter and GUFW. They seem good, both of them. Their underlying program is indeed Iptables as has been noted several places when you search for information on Firestarter and GUFW. Alright. :)

I would check your firewall rules, if you are using both, as both setup different default rules, and there could be some conflict between the two. Rules are read in order, so some rules could be nullified by using both.

The reason most of use don't like Firestarter, is that new users tend to leave it running on the desktop to monitor connections. Firestarter needs to be run as root, which could put your system at risk.

---

### Post by Aetixintro on 2010-10-02
First, is there a page option with IP-tables, like the ones one had with the DOS help pages some 20 years back? :)

So here is some of my output from ```
sudo iptables -L -v -n
```
```

#It's also unknown under what heading this is under, ie. request for "-p" option to IP-tables. These are added by Firestarter alone and I think it's working great!! Funny that one Ubuntuforums staffer thinks that it's of no more use. My GUFW is indeed faulty in comparison.#
#I have several of these bastards:#
    0     0 DROP       all  --  *      *       82.83.247.90         [0.0.0.0/0]("http://0.0.0.0/0")           
    0     0 DROP       all  --  *      *       218.87.232.200       [0.0.0.0/0]("http://0.0.0.0/0")           
    0     0 DROP       all  --  *      *       222.35.5.8           [0.0.0.0/0]("http://0.0.0.0/0")           
    0     0 DROP       all  --  *      *       218.87.232.200       [0.0.0.0/0]("http://0.0.0.0/0")           
(for example, they attempt hacks so I put the IP out here...)

Chain LSI (2 references)
 pkts bytes target     prot opt in     out     source               destination       
    1    90 LOG_FILTER  all  --  *      *       [0.0.0.0/0]("http://0.0.0.0/0")            [0.0.0.0/0]("http://0.0.0.0/0")           
    0     0 LOG        tcp  --  *      *       [0.0.0.0/0]("http://0.0.0.0/0")            [0.0.0.0/0]("http://0.0.0.0/0")           tcp flags:0x17/0x02 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
    0     0 DROP       tcp  --  *      *       [0.0.0.0/0]("http://0.0.0.0/0")            [0.0.0.0/0]("http://0.0.0.0/0")           tcp flags:0x17/0x02 
    0     0 LOG        tcp  --  *      *       [0.0.0.0/0]("http://0.0.0.0/0")            [0.0.0.0/0]("http://0.0.0.0/0")           tcp flags:0x17/0x04 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
    0     0 DROP       tcp  --  *      *       [0.0.0.0/0]("http://0.0.0.0/0")            [0.0.0.0/0]("http://0.0.0.0/0")           tcp flags:0x17/0x04 
    0     0 LOG        icmp --  *      *       [0.0.0.0/0]("http://0.0.0.0/0") ...
(for example)

Chain LSO (1 references)
 pkts bytes target     prot opt in     out     source               destination  
    0     0 LOG_FILTER  all  --  *      *       [0.0.0.0/0]("http://0.0.0.0/0")            [0.0.0.0/0]("http://0.0.0.0/0")           
    0     0 LOG        all  --  *      *       [0.0.0.0/0]("http://0.0.0.0/0")            [0.0.0.0/0]("http://0.0.0.0/0")           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Outbound ' 
    0     0 REJECT     all  --  *      *       [0.0.0.0/0]("http://0.0.0.0/0")            [0.0.0.0/0]("http://0.0.0.0/0")
(for example)

Chain OUTBOUND (1 references)
 pkts bytes target     prot opt in     out     source               destination
   0     0 ACCEPT     tcp  --  *      *       62.16.x.x        [0.0.0.0/0]("http://0.0.0.0/0")           tcp dpts:67:68 
    0     0 ACCEPT     udp  --  *      *       62.16.x.x        [0.0.0.0/0]("http://0.0.0.0/0")           udp dpts:67:68 
    0     0 ACCEPT     tcp  --  *      *       62.16.x.x        [0.0.0.0/0]("http://0.0.0.0/0")           tcp dpt:53 
    0     0 ACCEPT     udp  --  *      *       62.16.x.x        [0.0.0.0/0]("http://0.0.0.0/0")           udp dpt:53 
    0     0 ACCEPT     tcp  --  *      *       62.16.x.x        [0.0.0.0/0]("http://0.0.0.0/0")           tcp dpt:465 
    0     0 ACCEPT     udp  --  *      *       62.16.x.x        [0.0.0.0/0]("http://0.0.0.0/0")           udp dpt:465 
(for example)

```Cheers! :)
Anything more definite than this has to wait!!

---

### Post by CharlesA on 2010-10-02
[Man pages are always fun.]("http://linux.die.net/man/8/iptables") ;)

---

### Post by Aetixintro on 2010-10-02
Thanks, [COLOR=Black][COLOR=#d40000]**[COLOR=black]CharlesA[/COLOR]**[COLOR=black]. I have actually downloaded a bunch of IP-tables documentation already. People can also visit[/COLOR][/COLOR][/COLOR][http://www.netfilter.org/index.html](http://www.netfilter.org/index.html). Also, please don't forget your IP6tables installation. There's a certain trick with installing IP6tables in Ubuntu. I can't remember it at the moment, but I mention it so that you don't forget! Cheers! :)[URL="http://www.netfilter.org/index.html"]
[/URL]

---

### Post by holiday on 2010-10-02
> **uRock said:**
> This should be helpful. [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

> **CharlesA said:**
> I just use iptables.

Check this out [here]("http://bodhizazen.net/Tutorials/iptables/").


Thanks for these tutorials, guys. I might just give iptable scripting another try.

---

### Post by bodhi.zazen on 2010-10-02
> **holiday said:**
> Thanks for these tutorials, guys. I might just give iptable scripting another try.

Scripting iptables makes it more complicated then it needs to be, IMHO at least.

Try 

```
sudo iptabels-save > /etc/iptables.save
```

Then restore with iptables-restore or iptables-apply

You can then edit /etc/iptables.save

You can then call iptables-restore from /etc/rc.local or from your network scripts (post-up).

---

### Post by Aetixintro on 2010-10-02
Question: how do you apply the equivalent of Lockdown of Connection by Firestarter, fx., in fx. Iptables (because I believe you don't have an easy solution there)? :)

---

### Post by OpSecShellshock on 2010-10-02
Put the mouse pointer on the networking icon in the panel, then right-click and deselect "Enable Networking."

---

### Post by Aetixintro on 2010-10-02
To OpSecShellshock

There are important differences between going off-line and locking your connections down. First, that online conn.s are readily available to you in the Lockdown mode. Your adversaries will know that you are off-line and draw conclusions while being in Lockdown-mode, you are disguised from this. At least, this is the most important that I find... Cheers! :)

---

### Post by bodhi.zazen on 2010-10-02
> **Aetixintro said:**
> To OpSecShellshock

There are important differences between going off-line and locking your connections down. First, that online conn.s are readily available to you in the Lockdown mode. Your adversaries will know that you are off-line and draw conclusions while being in Lockdown-mode, you are disguised from this. At least, this is the most important that I find... Cheers! :)

Since firestarter is nothing more then a front end for iptables, there is nothing you can do in firestarter that can not be done in iptables.

Better questions are :

1. What, if anything, do you want to know about iptables ?

2. What is it you want from a "Lockdown mode" ? I have idea from your post what you mean by "Lockdown". 

When you click the little "lock" button in firestarter, all connections are blocked, it is the same as if you disable your networking, as described by OpSecShellshock or same as if you physically disconnected the cable.

If there is some specific traffic you are concerned with you will need to  post a lot more information. What is allowed in or out of your firewall is dependent on the rules you write, that is what it means to configure your firewall. From your posts I have no idea of your configuration or what question you have.

3. As with most things, I think you are confusing familiarity with easy. I can easily configure iptables to do what ever I wish as I am familiar with how it works. YMMV, but debating "easy" is almost always pointless. A better question is what are you wanting and what are you willing to learn.

If you are happy with firestarter, use firestarter. If you want to learn iptables you will have to be willing to put in the time and effort, same as learning anything new.

---

### Post by Aetixintro on 2010-10-03
I think it's obvious that being in "Lockdown state", having the connections BLOCKED either way, takes an iptables script to accomplish. This is clearly automated by the GUI of Firestarter that works directly with iptables. And I think the switching between lockdown state and active internet conn. makes you less vulnerable too, at least theoretically. That's it. Cheers! :)

---

### Post by uRock on 2010-10-03
GUFW can do this very easily. Just click deny on both incoming and outgoing.

---

### Post by Aetixintro on 2010-10-05
What I'm thinking about here is that GUFW will keep the old rules if you make new rules of DENYing both incoming and outgoing. I certainly think this can be amended by a little programming and some benevolence toward the Lockdown mode. What is so wrong to think in terms of Lockdown AND disabling the connection (conjunction thinking)? Let's say you have set up fine rules and you make the program remember these rules when you apply the DENY on both incom. and outgo. Come on... :)

Clearly, I have no problem with GUFW or Firestarter as long as they deliver! Cheers! :)

PS: I've also found that it is possible to disallow the Connection (typ. eth0) to other users by the network manager. Does this mean increased security against hackers/intruders? I'm just wondering.

PS2: Is it also possible to get the Lockdown mode on start-up, ie. Lockdown-mode is in effect _before_ the connection is established?

---

### Post by CharlesA on 2010-10-05
> **Aetixintro said:**
> PS: I've also found that it is possible to disallow the Connection (typ. eth0) to other users by the network manager. Does this mean increased security against hackers/intruders? I'm just wondering.

How would that help? If you are blocking all incoming connections, how exactly is someone going to get connected in the first place?

If they have physical access, disabling eth0 isn't going to do jack to prevent them from using the machine.

> PS2: Is it also possible to get the Lockdown mode on start-up, ie. Lockdown-mode is in effect _before_ the connection is established?

Whatever rules that were in effect at time of shutdown/reboot will be in effect when you reboot.

I don't really see the usefulness of a "lockdown mode" tbh. Just block incoming connections and you'll be fine.

---

### Post by Aetixintro on 2010-10-05
I'm thinking that the user might download (and execute) a program that carries a an agent-program that sets itself up on a generated user account. This kind of program would be blocked by this.

Physical access is not in question.

Just in case, and you allow some incoming, you may want FULL control and this can be achieved by the Lockdown-mode on start-up. This is merely a suggestion for future programming (and it doesn't hurt anyone :) ).

---

### Post by uRock on 2010-10-05
> **Aetixintro said:**
> I'm thinking that the user might download (and execute) a program that carries a an agent-program that sets itself up on a generated user account. This kind of program would be blocked by this.

Physical access is not in question.

Just in case, and you allow some incoming, you may want FULL control and this can be achieved by the Lockdown-mode on start-up. This is merely a suggestion for future programming (and it doesn't hurt anyone :) ).
I'd be interested in knowing what program would install and run in such a manner. I have installed quite a few programs and not one of them has created a new user account, on Windows or Linux.

Also, If I were to install an application that I felt needed to be quarantined from the network, then it would get uninstalled just as fast as I installed it.

---

