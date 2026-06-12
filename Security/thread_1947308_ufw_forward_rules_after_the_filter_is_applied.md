---
title: "ufw forward rules after the filter is applied?"
date: 2012-03-26
forum: Security
---

### Post by darkod on 2012-03-26
Hi all.

I am setting up a machine to be router/firewall and bit by bit I am getting there.

However, I noticed one thing today. Even if I delete the allow rule in ufw for port 80, it still opens the website on the webserver behind the router/firewall.

Does this mean the port foward (NAT) rules in ufw are executed before the firewall filter and regardless if I am blocking port 80 for example? Is there a way to execute the port forward after the filter is applied? And where should the rule be in that case?

Most port forward tutorials mention /etc/ufw/before.rules so I have my port forwards there, but does being in before.rules actually means it is applied before the filter? I did a test putting it in after.rules but things didn't change. Or maybe I got the syntax wrong if it needs to be changed to be used in after.rules.

Any ideas? I need this pretty ASAP. Thanks.

---

### Post by Doug S on 2012-03-26
Hi Darkod,
 
I'm not sure, but yes I think your forward rules are effectively by-passing your input chain firewall filters. It is important to know that there are multiple paths through IPTABLES depending on if forwarding or not. There is a good diagram of packet flow that I always have right here at my desk to help me (I'll find and edit in a link later).
 
If you post your iptables, we can know for sure what is going on (although I sometimes have difficulties reading ufw generated tables):```
sudo iptables -x -n -L -v
``````
sudo iptables -t nat -x -n -L -v
```or```
sudo iptables-save -c
```

---

### Post by darkod on 2012-03-26
Thanks. Here you go.

I have also attached the before.rules and after.rules. In before.rules the forward entries are commented out at the moment for my tests.
In after.rules I have added the *nat section after the *filter section as seen on one website but even that latest try didn't change things. The website still opens and there is no entry for port 80 in ufw to allow it.

---

### Post by darkod on 2012-03-26
Better iptables screenshot.

---

### Post by Doug S on 2012-03-26
Thanks for the better screen shot added. I was just about to write and say the prevous one was chopped.
 
You still have bypass rule in your 3rd of 3 screen shots. It says "after rules" but it will be "first" in the prerouting.
 
(sorry for the brief reply, but I am out of time for just now)

---

### Post by darkod on 2012-03-26
Does that mean I need to work with POSTROUTING?

All examples of port forwarding I found said PREROUTING although now that i think about it they might not care if you forward the packet before the firewall filter. I do.

I know I can add a source limitation in PREROUTING with -s but i was hoping the firewall rules to be one more layer of protection. Like this, they seem completely bypassed.

---

### Post by Doug S on 2012-03-26
You might be able to do what you want with rules in the forward chain, I'm not sure.
Wouldn't you do any other filtering or whatever at the destination machine?
I don't know enough about what you are trying to do to be able to comment further. (and I have seen some of your other threads).
 
By the way, the diagram I referred to earlier can be found here: [http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

---

### Post by darkod on 2012-03-26
Well, since you obviously know more than me on this topic, if you feel you can help I can give you the short version. :)

Internet space (fixed public IP) --- server A --- server B

Server B is a webserver (Win 2008 IIS7) that will be connected to the private interface of server A, only private IP. The external interface of server A will have a fixed public IP and gateway, etc....

Server A is the router/firewall server machine I am talking about.

So, for the webserver the router/firewall needs to be the gateway to the internet. For this I did the necessary changes in /etc/default/ufw and /etc/ufw/sysctl.conf and the *nat section in /etc/ufw/before.rules as per google tutorials.

The routing works fine, I can ping outside from server B both with IP and domain names.

I am after protecting the webserver from smallish attacks (I am aware it will hardly hold any major attacks but we don't expect them :) ). My understanding was that ufw will protect also the traffic passing through, not only the server A machine itself.

Of course, 80 and 443 will need to be open for all, and forwarded to the webserver private IP (lets call it 10.0.0.2). That is easy, you do it with:
-A PREROUTING -i eth0 -p tcp --dport 80 -j DNAT --to 10.0.0.2

Works fine. Of course I opened port 80 in ufw. Only today it occurred to me to test with 80 closed and sure enough, the test website is still available. Which means the forward rule above is executed before any firewall filtering rules.

Which is not what I expected.

Any alternative I tried today to make it block 80 unless it is allowed in the firewall, failed. It either doesn't open if you completely remove the rule to forward 80, which is understandable, or it opens as soon as you configure a rule for the port forward regardless if that rule is in before.rules or after.rules and that port 80 is blocked in ufw.

Of course, the port 80 is not the main issue since it needs to be available to all anyway.

The problem is how to give max protection to the ports used for windows Remote Desktop, and FTP (I will not use the default ones).

The only option I have available as I see it, is something like this in before.rules:
-A PREROUTING -i eth0 -p tcp -s <office public IP> --dport 3389 -j DNAT --to 10.0.0.2

NOTE: Forgot to mention, the servers will be hosted with a hosting provider in another town, hence the office needs to have RD and FTP access. The office has fixed public IPs on its ADSL lines so that can help use the -s option to limit the source IP.

Now, is the above enough?????

I was going to complement it with something like:
ufw allow in on eth0 from <office public IP> port 3389 proto tcp

as additional defense thinking the firewall will block any attempt on port 3389 not coming from the office. Together with the forward rule doing the same, better.

But if the forward happens before the firewall filter, the ufw allow or deny has no meaning. Right?

Sorry about the long post, I tried to explain everything. Any ideas???

PS. In the last few hours I tried to read more about the FORWARD option (chain) but never found anything relating that to port forwarding. Can you suggest some example syntax?

---

### Post by JKyleOKC on 2012-03-26
I'm not surprised that you've been confused -- it's a very murky area.

The oversimplified version, though, is pretty clear. When a packet comes into the machine through the WAN interface, it goes to the INPUT chain if addressed to the local machine, and to the FORWARD chain if not -- but never through both of them.

The prerouting and postrouting rules have nothing to do with firewall filtering. They are part of the **nat** module, and handle routing and redirection.

For the firewall, you need to duplicate your INPUT chain's rules in the FORWARD chain of the **filter** module. That will achieve what you want, and it really won't matter where in the routing sequence of events the filtering happens. I believe it will come as early as possible, since there's no point to doing all the (invisible) NAT bookkeeping on packets that are just going to be thrown away, but I've not tried to verify this by digging through kernel source code.

It's a bit tedious to duplicate all the rules, but it can be done easily by copy-and-paste, then replace INPUT with FORWARD in the second copies...

It may be a bit more difficult with ufw, but you can view the actual rules by doing "sudo iptables-save >$HOME/myrules.txt" and examine them. This may give some hints on what you need to do with the ufw rules...

Hope this helps!

---

### Post by darkod on 2012-03-26
> **JKyleOKC said:**
> I'm not surprised that you've been confused -- it's a very murky area.

The oversimplified version, though, is pretty clear. When a packet comes into the machine through the WAN interface, it goes to the INPUT chain if addressed to the local machine, and to the FORWARD chain if not -- but never through both of them.

The prerouting and postrouting rules have nothing to do with firewall filtering. They are part of the **nat** module, and handle routing and redirection.

For the firewall, you need to duplicate your INPUT chain's rules in the FORWARD chain of the **filter** module. That will achieve what you want, and it really won't matter where in the routing sequence of events the filtering happens. I believe it will come as early as possible, since there's no point to doing all the (invisible) NAT bookkeeping on packets that are just going to be thrown away, but I've not tried to verify this by digging through kernel source code.

It's a bit tedious to duplicate all the rules, but it can be done easily by copy-and-paste, then replace INPUT with FORWARD in the second copies...

Hope this helps!

It does, but does it change things that I have been "handling" the rules with ufw and not iptables directly? If I start with iptables I will get even more lost, and I have no much time to finish this off right now. If I discovered this last week...

ufw sounded like good and simple front of iptables. Can I still do this with ufw only?

---

### Post by darkod on 2012-03-26
I am investigating the before.rules and after.rules on my home server right now (which has nothing to do with my server at work but that's what I can check right now).

So, in before.rules in the chain *filter there are ufw-before-input, -output and -forward, and in after.rules there are ufw-after-input, -output and -forward options.

Does that mean blocking 80 for all would be like:
-A ufw-before-forward --dport 80 -j DROP

Or letting 3389 for IP1 would be:
-A ufw-before-forward -s IP1 --dport 3389 -j ACCEPT

???

---

### Post by JKyleOKC on 2012-03-26
It might! I've no experience at all with ufw, since I learned raw iptables use on my older distribution some 10 years ago and have simply stuck with it. However the easy way would probably be to test it and see. Make backup copies of any file that you modify, so you can undo your changes if they don't work, and you should be perfectly safe...

---

### Post by Doug S on 2012-03-26
Hi darkod,
I had to do something else for a awhile. That reply from JKyleOKC was just excellent.
> Does that mean blocking 80 for all would be like:
-A ufw-before-forward --dport 80 -j DROP
Yes, I think so.> Or letting 3389 for IP1 would be:
-A ufw-before-forward -s IP1 --dport 3389 -j ACCEPT
I don't think you would want to do that, I think you would want something similar to what you posted earlier:> The only option I have available as I see it, is something like this in before.rules:
-A PREROUTING -i eth0 -p tcp -s <office public IP> --dport 3389 -j DNAT --to 10.0.0.2

Please know that I don't acutally use UFW, I only do iptables directly.

---

### Post by darkod on 2012-03-26
The PREROUTING rule is necessary to have the correct port forwarding, I can't avoid that.

The idea with ufw-before-forward with -s option is to additionally strengthen the security by applying a filter during the forward. Yeah, it does sound kind of redundant.

So, in your experience, in this case, should I bother filtering the forward at all or the PREROUTING rule limited to a source IP is doing the job with sufficient protection? I am trying to find the sweet spot between easy configuration and sufficient protection.

In case it is enough, the final verdict would be something like:
1. Use ufw allow rules only to control ssh access to the machine, because that rule would apply to the machine itself.
2. Forward 80 and 443 without any source limiting because you need it available to all.
3. Forward the other necessary ports with the -s source limitation without worrying about any filtering during the forward.

---

### Post by Doug S on 2012-03-26
> The idea with ufw-before-forward with -s option is to additionally strengthen the security by applying a filter during the forward.I don't think it would work, but try it and report back.
> So, in your experience, in this case, should I bother filtering the forward at all or the PREROUTING rule limited to a source IP is doing the job with sufficient protection? I am trying to find the sweet spot between easy configuration and sufficient protection.
I would do some filtering in the forward chain, but for the other packets using that path, not for the ones you are port forwarding. i.e. for your regular nat traffic (which maybe there is none, and you don't have to worry about it). 
> In case it is enough, the final verdict would be something like:
1. Use ufw allow rules only to control ssh access to the machine, because that rule would apply to the machine itself.
2. Forward 80 and 443 without any source limiting because you need it available to all.
3. Forward the other necessary ports with the -s source limitation without worrying about any filtering during the forward.Yes, that is what I would do.

---

### Post by JKyleOKC on 2012-03-26
> **darkod said:**
> The idea with ufw-before-forward with -s option is to additionally strengthen the security by applying a filter during the forward. Yeah, it does sound kind of redundant.

So, in your experience, in this case, should I bother filtering the forward at all or the PREROUTING rule limited to a source IP is doing the job with sufficient protection? I am trying to find the sweet spot between easy configuration and sufficient protection.

In case it is enough, the final verdict would be something like:
1. Use ufw allow rules only to control ssh access to the machine, because that rule would apply to the machine itself.
2. Forward 80 and 443 without any source limiting because you need it available to all.
3. Forward the other necessary ports with the -s source limitation without worrying about any filtering during the forward.A participant in another thread I'm in about gufw and iptables ([http://ubuntuforums.org/showthread.php?t=1708078](http://ubuntuforums.org/showthread.php?t=1708078)) made a very good point: it's much simpler to work with things if you set up the default as "deny" and then whitelist the things you want to let through. That way you need not worry about "what (and where) to block things" but can concentrate on "what am I going to allow?"

If the only thing you want to allow for incoming is the web traffic, then a single before-forward "allow" rule will do so. On the outgoing side you can apply the same logic, or if you trust that nobody will let malware come in via the web interface you can set the default to "allow." 

However it's best to be just as careful with outgoing packets as with the incoming ones. The one and only time I got an actual infection (back in Win95 days, and the event that moved me to Linux for my servers), it was the outgoing block filter that alerted me. I did get invaded once, much more recently, but that happened because I inadvertently ignored not just one but several of the basic rules for security!

---

### Post by collisionystm on 2012-03-26
> However, I noticed one thing today. Even if I delete the allow rule in ufw for port 80, it still opens the website on the webserver behind the router/firewall.

Just curious, but did you

sudo ufw disable
sudo ufw enable

You have to disable and re-enable the firewall for a rule to take place.

---

### Post by darkod on 2012-03-27
> **collisionystm said:**
> Just curious, but did you

sudo ufw disable
sudo ufw enable

You have to disable and re-enable the firewall for a rule to take place.

Definitely. Not only that, i restarted the whole machine, many times.

That is how I figured out that the PREROUTING is done before any filter attempt, because it seems to forward 80 to the webserver even with deny 80 set on the router/firewall machine. I guess that deny only applies to the local port 80 but with the PREROUTING --dport 80 it avoids the firewall filter check.

---

### Post by darkod on 2012-03-27
> **JKyleOKC said:**
> A participant in another thread I'm in about gufw and iptables ([http://ubuntuforums.org/showthread.php?t=1708078](http://ubuntuforums.org/showthread.php?t=1708078)) made a very good point: it's much simpler to work with things if you set up the default as "deny" and then whitelist the things you want to let through. That way you need not worry about "what (and where) to block things" but can concentrate on "what am I going to allow?"

If the only thing you want to allow for incoming is the web traffic, then a single before-forward "allow" rule will do so. On the outgoing side you can apply the same logic, or if you trust that nobody will let malware come in via the web interface you can set the default to "allow." 

However it's best to be just as careful with outgoing packets as with the incoming ones. The one and only time I got an actual infection (back in Win95 days, and the event that moved me to Linux for my servers), it was the outgoing block filter that alerted me. I did get invaded once, much more recently, but that happened because I inadvertently ignored not just one but several of the basic rules for security!

Of course, that is how I started too. Google says when it is enabled first time ufw starts with ALLOW for outgoing traffic and DENY ALL for incoming.
The first thing I configured was the forwarding between eth0 (ext interface) and eth1 (internal interface). Tested that, works fine.
Then configured dns forwarding with dnsmasq, just in case I want to use it as dns forward in future although I will probably use the ISP dns servers configured manually on the internal network (which will have only two servers in fact). Tested, works.

Then the first thing I opened in ufw was the port for SSH. Works fine.

So from that point on, all I need is:
80 and 443 available to all.
For the two servers on the internal network 2 ports for Remote Desktop and 2 ports for FTP.
Few more ports for some services running on the IIS.

That's about it.

I will start testing now and lets see.

---

### Post by darkod on 2012-03-27
I think I got it. :)

Thanks everybody for the help.

So, with my limited knowledge of ufw and my tests, here is what it looks like:
Most tutorials on the web put the *nat section about the routing at the top of before.rules. However, they also mention to enter your port forwarding entries there. Probably not taking into account if you want to filter any of those entries.

In case you DO want to filter, DO NOT put them there!!!

Configure the *nat section as per the routing tutorials at the top of before.rules (see top of first image). But only the commands about the routing, not any port forwarding.

If you want any filters on your forwarded traffic, make ufw-before-forward rules towards the middle of the *filter section (see towards bottom of first image, My Firewall rules section).

Make another *nat for PREROUTING at the bottom of before.rules. DO NOT FORGET to do it at the bottom, AFTER the COMMIT line which is from the *filter section!!! In this *nat section enter your port forward rules.

Don't forget the firewall executes in order first to last. That is why you need to move the port forward rules to bottom if you want them filtered, and create filter rules in the middle of the file.

I first tested with the forward port 80 rule at top, as it was. I created the:
-A ufw-before-forward --dport 80 -j DROP
rule at the middle of the before.rules. Tried it, the website is working. Because the rule to forward is before it even gets to the DROP rule.

After I moved the forward rule at the bottom, Firefox had a wonderful message for me "Can't establish connection to the server"... :)

Then I tried commenting out my DROP rule, the website is working again.

So, with the latest discovery, if you want to filter your port forwards, and in my case I have two static public IP at the office and want to access the servers at the hosting provider, in the middle of before.rules in My Firewall rules section you would enter something like:
-A ufw-before-forward -s IP1 --dport <port> -j ACCEPT
-A ufw-before-forward -s IP2 --dport <port> -j ACCEPT
-A ufw-before-forward --dport <port> -j DROP

Since the first rule to match gets executed, it would accept traffic on this port from the office, and deny from everywhere else.

I think I am on the right track... :)

---

### Post by darkod on 2012-03-27
I spoke too fast.

The ufw-before-forward rules are tried to be applied, but I think I am getting the syntax wrong. On boot it reports a problem with before.rules.

I thought something like:
-A ufw-before-forward -s IP1 --dport <port> -j ACCEPT

should work. Any thoughts?

EDIT: OK, got it. The --dport and --sport don't work unless you use -p tcp. Only then the modules get loaded. So it should be something like:
-A ufw-before-forward -p tcp -s IP1 --dport <port> -j ACCEPT
-A ufw-before-forward -p tcp --dport <port> -j DROP

---

### Post by collisionystm on 2012-03-27
Be sure to include UDP in there as well

-A ufw-before-forward -p tcp -s IP1 --dport <port> -j ACCEPT
-A ufw-before-forward -p tcp --dport <port> -j DROP
-A ufw-before-forward -p udp -s IP1 --dport <port> -j ACCEPT
-A ufw-before-forward -p udp --dport <port> -j DROP

---

### Post by Doug S on 2012-03-27
> **collisionystm said:**
> Be sure to include UDP in there as well
 
-A ufw-before-forward -p tcp -s IP1 --dport <port> -j ACCEPT
-A ufw-before-forward -p tcp --dport <port> -j DROP
-A ufw-before-forward -p udp -s IP1 --dport <port> -j ACCEPT
-A ufw-before-forward -p udp --dport <port> -j DROP
Only if required. Not needed for web stuff on port 80.

---

### Post by kevdog on 2012-03-27
Not knocking ufw, but I guess I'll just take a cheap shot -- this would have been a lot more straight forward to do directly with just iptables, however I'm very glad you got it working.  There are always multiple ways to skin a cat!

---

### Post by JKyleOKC on 2012-03-28
I absolutely have to agree with you, kevdog. The "uncomplicated" ufw creates 31 user-defined chains in the filter table, most of which actually do nothing at all (they're apparently there to provide for almost any advanced operations a user might want to add). Contrast this with just three that are there in raw iptables. 

I've been attempting to draw up a flow chart of what ufw actually does, in order to better assist folk who want to use it -- but the deeper I dig into it, the less impressed I am with its approach...

---

### Post by darkod on 2012-03-28
While you are both right, I have to say iptables looks scary to a beginner. And I am a total beginner at this, as you can tell.

It might be doing things the complicated way, but in a way the rules look straightforward and understandable in before.rules. Hell, I managed to get it going with almost no clue what I am doing, just logic, and help from the forum.

On the other hand, as opposed to before.rules, when I did iptables -L during one of my tries, I couldn't figure out anything (almost). Which doesn't mean you don't know what is going on with just one look. :)

---

### Post by Ms. Daisy on 2012-03-28
JKyleOKC, I'd be very interested in seeing that flow chart if you get it done.

---

### Post by collisionystm on 2012-03-28
It seems to make a mess of iptables also.

See here it lists my port redirect several times when performing an iptables-save

-A PREROUTING -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 8080
-A PREROUTING -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 8080
-A PREROUTING -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 8080
-A PREROUTING -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 8080
-A PREROUTING -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 8080
-A PREROUTING -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 8080
-A PREROUTING -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 8080
-A PREROUTING -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 8080
-A PREROUTING -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 8080
-A PREROUTING -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 8080
-A PREROUTING -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 8080
-A PREROUTING -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 8080
-A PREROUTING -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 8080
-A PREROUTING -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 8080
-A PREROUTING -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 8080
-A PREROUTING -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 8080
-A PREROUTING -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 8080
-A PREROUTING -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 8080
-A PREROUTING -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 8080
-A PREROUTING -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 8080
-A PREROUTING -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 8080
-A PREROUTING -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 8080
-A PREROUTING -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 8080
-A PREROUTING -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 8080
-A PREROUTING -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 8080
-A PREROUTING -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 8080
-A PREROUTING -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 8080
-A PREROUTING -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 8080
-A PREROUTING -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 8080
-A PREROUTING -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 8080
-A PREROUTING -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 8080
-A PREROUTING -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 8080
-A PREROUTING -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 8080
-A PREROUTING -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 8080
-A PREROUTING -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 8080
-A PREROUTING -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 8080

---

### Post by JKyleOKC on 2012-03-28
> **Ms. Daisy said:**
> JKyleOKC, I'd be very interested in seeing that flow chart if you get it done.I'll definitely pass it along if I ever get it finished. Right now it's only a text file, edited from iptables-restore output to determine the flow route, and already I've found duplication similar to that reported by collisionystm above although not nearly so much.

darkod: Use whatever works for you! I'm glad you did get it figured out, and once you have a configuration that works it ought to stay that way without any need for additional tweaking no matter how you got there.

The documentation in the "man" pages for both iptables and ufw makes them look far more complicated than they really are in practice, mostly because of the huge number of options available. Most of those for iptables are never used in the majority of installations, but front ends such as ufw still have to allow for them. Just keep in mind Einstein's dictum: "Everything should be as simple as possible, but no simpler." Far too many software simplifiers forget that rule and go too far...

---

### Post by darkod on 2012-03-29
While we are on the subject, would something like this work:
[http://www.linode.com/wiki/index.php/Configuring_IPtables_on_ubuntu_server](http://www.linode.com/wiki/index.php/Configuring_IPtables_on_ubuntu_server)

Mainly the part about adding iptables-restore to /etc/network/interfaces. This is another thing confusing about iptables, how come the rules don't load automatically at boot unless you take action yourself?

Also, please look at the sample configuration file in the link in the middle of the article. Does it look OK from syntax point of view? I am not talking about what the actual rules block or accept, only about the syntax.

If you would like to do something like this, can you follow this tutorial?

---

### Post by JKyleOKC on 2012-03-29
> **darkod said:**
> Mainly the part about adding iptables-restore to /etc/network/interfaces. This is another thing confusing about iptables, how come the rules don't load automatically at boot unless you take action yourself?
Here's what I have in my own /etc/network/interfaces (eth0 is my network adapter that faces the LAN, not the one facing the world):```
iface eth0 inet static
	address 192.168.0.2
	netmask 255.255.255.0
	post-up iptables-restore < /etc/iptables.up.rules

auto eth0

```It works perfectly. Note that using /etc/network/interfaces may disable Network Manager. In my case I count that as a good feature since Network Manager caused me nothing but problems, but that was with an older version (as I recall, Fiesty but it may have been Hardy).
> **darkod said:**
> 
Also, please look at the sample configuration file in the link in the middle of the article. Does it look OK from syntax point of view? I am not talking about what the actual rules block or accept, only about the syntax.

If you would like to do something like this, can you follow this tutorial?I'm not at all sure that this is a good sample, although the syntax looks okay. However his first two rules don't look right to me; the second will never be reached because the first accepts everything on the loopback interface "lo" and this makes me suspect the rest of it.

Here's my own ip.tables.rules file for this machine, which serves as the gateway to my LAN (some of the rules of course are highly specific to my own system; for instance, port 7100 is used by a weather app that my wife likes but I don't use so I reject it in the INPUT chain but let the "ESTABLISHED" rule in FORWARD accept it for her machine):```
# Generated by iptables-save v1.3.8 on Mon Nov  2 20:02:30 2009
*filter
:FORWARD ACCEPT [0:0]
:INPUT DROP [0:0]
:LOG_DROP - [0:0]
:OUTPUT ACCEPT [0:0]
-A INPUT -s 202.104.197.118 -j REJECT --reject-with icmp-host-prohibited
-A INPUT -s 67.217.34.238 -j REJECT --reject-with icmp-host-prohibited
-A INPUT -p udp -m udp --dport 7100 -j REJECT --reject-with icmp-host-prohibited
-A INPUT -s 192.168.1.1/16 -j ACCEPT
-A INPUT -i lo -j ACCEPT
# Accept FTP and outgoing mail ports
-A INPUT -p tcp -m tcp --dport 20:21 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 25 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 51200:51299 -j ACCEPT
-A INPUT -p icmp -j ACCEPT
-A INPUT -i eth0 -j ACCEPT
-A INPUT -m state -i eth1 --state RELATED,ESTABLISHED -j ACCEPT
-A INPUT -j LOG_DROP
-A FORWARD -i eth0 -j ACCEPT
-A FORWARD -m state -i eth1 -o eth0 --state RELATED,ESTABLISHED -j ACCEPT
-A FORWARD -p tcp -m tcp -i eth1 --dport 80 -j ACCEPT
-A FORWARD -j LOG_DROP
-A LOG_DROP -j LOG  --log-prefix "[IPTABLES DROP] : " 
-A LOG_DROP -j REJECT --reject-with icmp-host-prohibited
COMMIT
# Completed on Mon Nov  2 20:02:30 2009
# Generated by iptables-save v1.3.8 on Mon Nov  2 20:02:30 2009
*mangle
:PREROUTING ACCEPT [0:0]
:INPUT ACCEPT [0:0]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
:POSTROUTING ACCEPT [0:0]
COMMIT
# Completed on Mon Nov  2 20:02:30 2009
# Generated by iptables-save v1.3.8 on Mon Nov  2 20:02:30 2009
*nat
:PREROUTING ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
:POSTROUTING ACCEPT [0:0]
-A POSTROUTING -o eth1 -j MASQUERADE
-A PREROUTING -p tcp -m tcp -i eth1 --dport 80 -j DNAT --to-destination 192.168.0.4:80
COMMIT
# Completed on Mon Nov  2 20:02:30 2009

```As you can see, the last time I saved it via iptables-save was more than two years ago, although I've edited it with a text editor several times since to add or modify rules. It accepts everything from the LAN but is quite restricted for the outside world. I no longer run the web server at 192.168.0.4:80 but simply have not removed its rules from the filter and nat tables. In fact, 192.168.0.4 isn't even a valid address any more, so incoming traffic to it simply drops into a black hole.

I do run a private FTP server but it's thoroughly locked down so that it's not available for general use. I also open port 25 so that my monitoring tools can send reports to my LAN, but again the mail server here is locked down so that it cannot be used as a relay.

The reason that I have the same file name as the link you cite is that I created my rules initially using "webmin" as a front end, and it created the file for me. I've continued to use it although I dropped the use of webmin several years ago; it's great for setting things up initially, but is a security risk if left installed on a production system.

EDIT: You can see that I didn't follow my own advice in that the policy for FORWARD is set to ACCEPT rather than DROP. However the last actual rule in the chain is an unconditional jump to LOG_DROP, which forces all traffic not accepted by another rule to be rejected, and the policy never comes into force. I really ought to change this...

---

### Post by darkod on 2012-03-29
Can you comment on the difference between pre-up in that article and post-up you have in your /etc/network/interfaces?

I guess it means whether it is executed before or after something, but what? And what difference does it make in real life?

Is post-up better?

---

### Post by JKyleOKC on 2012-03-29
The "something" is the bringing up of the interface itself. I don't think there's a lot of difference in this case; using "pre-up" would assure that the firewall is in place before the interface is able to receive any packets, but "post-up" doesn't create a large window of opportunity for invasion, since the CPU is several orders of magnitude faster than is even a gigabit-speed network. The "post-up" enabling of the firewall will be done before more than one or two bytes of an incoming packet are received.

I copied my "post-up" line from some forum thread; it worked for me so I never explored it in any depth. Before using it, I put the line into /etc/rc.local; that had worked just fine with my old Mandrake system, but in Ubuntu seemed to be a bit flaky. I think that was because of the "upstart" boot sequence, which runs things in parallel rather than serially, possibly causing the restore to be attempted before the interfaces had been fully created.

That's just a guess, but if it's correct, then "post-up" would be preferable since it would guarantee that the interface existed while "pre-up" might attempt to restore before the interface was there.

---

### Post by darkod on 2012-03-29
Thanks. I was assuming it means the interface since it is in that file. Yeah, post-up sounds better because it makes sure the interface is up and the delay is not large enough to offer any possibility of intrusion.

---

### Post by darkod on 2012-03-29
Looking at your iptables config, another question. :)

What is the role of the *mangle section?

---

### Post by Doug S on 2012-03-29
I could use the exact text from JKyleOKC for my own history with iptables. I used to use rc and switched recently to the pre-up method, aftet seeing the method in a Ubuntu forums posting. Since I set some other things up at the same time, I use a script rather than iptable-restore. My interfaces file (Ihave a static IP, but my ISP makes me get it via DHCP):```
# Smythies 2011.11.15 Can I execute my firewall script from here
#          instead of /etc/rc2.d? Add it.
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
[COLOR=red]pre-up /home/doug/init/doug_firewall[/COLOR]
# The primary interface (d-link PCI card)
auto eth1
iface eth1 inet dhcp
# Local network interface (uses built in ethernet port)
auto eth0
iface eth0 inet static
  address 192.168.111.1
  network 192.168.111.0
  netmask 255.255.255.0
  broadcast 192.168.111.255

```
If you are interested, [my iptables script]("http://www.smythies.com/~doug/network/iptables_notes/doug_firewall.current.txt"). (it's a little commented to death, and has some commented out experiments and such.)(And I realize often readers don't like to follow links)

---

### Post by collisionystm on 2012-03-29
> **Doug S said:**
> I could use the exact text from JKyleOKC for my own history with iptables. I used to use rc and switched recently to the pre-up method, aftet seeing the method in a Ubuntu forums posting. Since I set some other things up at the same time, I use a script rather than iptable-restore. My interfaces file (Ihave a static IP, but my ISP makes me get it via DHCP):```
# Smythies 2011.11.15 Can I execute my firewall script from here
#          instead of /etc/rc2.d? Add it.
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
[COLOR=red]pre-up /home/doug/init/doug_firewall[/COLOR]
# The primary interface (d-link PCI card)
auto eth1
iface eth1 inet dhcp
# Local network interface (uses built in ethernet port)
auto eth0
iface eth0 inet static
  address 192.168.111.1
  network 192.168.111.0
  netmask 255.255.255.0
  broadcast 192.168.111.255

```
If you are interested, [my iptables script]("http://www.smythies.com/~doug/network/iptables_notes/doug_firewall.current.txt"). (it's a little commented to death, and has some commented out experiments and such.)(And I realize often readers don't like to follow links)


Adding comments to your work shows good understanding and craftsmanship. Good work!

---

### Post by darkod on 2012-03-29
Doug, you see, this is one more confusion about iptables I have.

Your script is much different than what Kyle posted, and what was included in that link I posted. I am not talking about your comments and rules.

There are other things very different, for example declaring variables with the interfaces, the IPs, etc.

Nothing like that exists in Kyle's post or the sample linked in that tutorial I posted earlier.

So, is it necessary or just something you did in a different way?

The port forwardind for example. I need to configure the "1" in /proc/sys/net/ipv4/ip_forward on every boot? Why can't it simply stay saved?

With ufw you only change it once in /etc/ufw/sysctl.conf and that's it.

---

### Post by JKyleOKC on 2012-03-29
> **darkod said:**
> Doug, you see, this is one more confusion about iptables I have.

Your script is much different than what Kyle posted, and what was included in that link I posted. I am not talking about your comments and rules.

There are other things very different, for example declaring variables with the interfaces, the IPs, etc.

Nothing like that exists in Kyle's post or the sample linked in that tutorial I posted earlier.

So, is it necessary or just something you did in a different way?

Much of the difference is because Doug based his script on one contained in the original iptables "how-to" file at
[http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/index.html](http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/index.html) and that document was written way back in 2005 when iptables was just coming into use to replace the older "ipchains" firewall capability in the kernel. At that time, the kernel modules that it installs were not automatically loaded in most distributions; today, they are, so all of those "depmod" commands are not needed any more. 

The use of variables for the interface names and the ip addresses was to make the published rules much more generic. You only need to change them one time, at the point where they are assigned to the variable, and that change becomes effective throughout the script. It's a very good and quite professional technique when preparing anything for publication, but again not at all necessary for any specific configuration that's not subject to frequent change.

> **darkod said:**
> 
The port forwarding for example. I need to configure the "1" in /proc/sys/net/ipv4/ip_forward on every boot? Why can't it simply stay saved?

With ufw you only change it once in /etc/ufw/sysctl.conf and that's it.And you can set it correctly in /etc/sysctl.conf (which runs before ufw gets loaded) and it **does** stay saved. Again, the script is based on one that was needed when iptables was just coming into acceptance, but that hasn't been necessary for at least five years now.

Using iptables-save to create a permanent rules file, and then using iptables-restore in a "post-up" line in /etc/network/interfaces, separates the rule setting from all the other (no longer necessary) housekeeping steps that appear in the script. This, in turn, keeps the rules a bit simpler and makes it easier to tune them.

The extensive revision history at the front of Doug's script indicates that he's been tuning it for quite a long time, improving it at each step. Staying with what works, rather than switching to something different just for the sake of change, is commendable. I don't mean my comments above, about much of it no longer being necessary, to be critical of his effort -- indeed, staying with a solution that works properly is a good professional practice. "If it ain't broke, don't fix it." Most of my problems for the past several years have been self-generated by attempts to improve matters!

Earlier, you asked about the purpose of the *mangle table. I'm not fully clear on its purpose myself, but I believe it deals with the connection tracking that has to be done for Network Address Translation to work. You probably noted that I didn't define any rules at all for it; it was simply created as part of the default installation which is part of all current *buntu kernels.

I'm currently toying with the idea of trying to write a new mini-how-to about iptables, contrasting it with ufw and showing how simple it can be for a basic installation. If I do, I'll probably use a lot of this thread as input for it!

---

### Post by Doug S on 2012-03-29
I didn't mean to add to confusion by my previous posting, and sorry if I did.
Well, you have caught me in a bit of laziness. I am aware that the depmod stuff is no longer needed, but I wasn't when I started. I just haven't changed the script yet. As for sysctl.conf, I am aware that I can make a permanent change, however I don't on purpose. It is just preference towards trying to minimize the number of changed files I have to track and if I have to rebuild a system from scratch. I also modify the default ip_conntrack_tcp_timeout_close_wait which I didn't figure out how to make permanent, but I didn't try very hard for the same previously stated reason.
The bottom line is, that I was throughly confused with iptables for quite some time, and as JKyleOKC deduced, I just left it and moved on after I got it going well.
Again, I didn't mean to sidetrack the discussion.
By the way I did use the iptables-restore method for several years, on a much much simplier rule set with no NAT such.
Also by the way, I don't have a mangle table, only a nat table.
 
Edit: darkod: Please don't give any thought to my changing the ip_conntrack_tcp_timeout_close_wait time. That is me being a fanatic. The point is/was that I want to do things in a script because I play with stuff outside of iptables, but within the same context (at least for me).

---

### Post by JKyleOKC on 2012-03-29
Doug, I think you made a quite positive contribution, by showing how two completely different techniques could be used to achieve the same goal, and joining the discussion of how they came to be chosen.

There are so many different ways to accomplish the same goal in Linux that it's a major part of the learning curve to discover that no single "correct" way exists. The pragmatic approach, I believe, is usually the best. When it works, leave it alone except for fine-tuning!

---

### Post by kevdog on 2012-03-29
Good work guys 

Wow I guess I went overboard to start my firewall script (similar to what was posted) from a udev script after networking was up.  I'm thinking the preup,postup statements may be better.

---

### Post by darkod on 2012-04-02
OK, this is weird. And worrying. :(

After all the successful tests in the office and after the machine was shipped to the hosting provider, it seems now it is not doing the port forwarding correctly. I haven't touched anything.

From the firewall machine I have ping to the destination web server. From the web server to the firewall too.

But it seems none of the ports are forwarded correctly. I have tried 80, 3389, 990.....

Any ideas?

I am really stuck now and open for ideas to troubleshoot this remotely. I thought everything was done after the tests, seemed perfect.

Help please...

---

### Post by darkod on 2012-04-02
Even though I am using ufw to configure the rules, here is the output of iptables -t nat.

It looks normal right? What the hell is going on? Why isn't any of the ports mentioned forwarded to 10.0.0.22?

---

### Post by JKyleOKC on 2012-04-02
> **darkod said:**
> Even though I am using ufw to configure the rules, here is the output of iptables -t nat.

It looks normal right? What the hell is going on? Why isn't any of the ports mentioned forwarded to 10.0.0.22?There aren't any rules in your screenshot for ports 80 or 990. However you do have two for 3389, and also for ftp and ftp-data (20 and 21).

Doing traceroute instead of ping might show how far along the path the packets are getting.

Also, your screenshot shows up pretty small on my browser; it's still readable but only with difficulty. If you can redirect output into a text file, then copy and paste that file into a post between CODE tags, it'll be much easier for us to assist...

Here's the output of my own listing for comparison: ```
Chain PREROUTING (policy ACCEPT 30193 packets, 2425K bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DNAT       tcp  --  eth1   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:80 to:192.168.0.4:80 

Chain POSTROUTING (policy ACCEPT 253 packets, 18070 bytes)
 pkts bytes target     prot opt in     out     source               destination         
49879 3224K MASQUERADE  all  --  *      eth1    0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy ACCEPT 47034 packets, 3064K bytes)
 pkts bytes target     prot opt in     out     source               destination         

```

---

### Post by darkod on 2012-04-02
The very first rule in prerouting section is for 80. I have it with port number 80 in the forward rule but I don't know why is calls it www in iptables. Can this have anything to do?

See the first rule destination port dpt:www

I'm too much into panic mode right now to export to file. :) Anyway, the screenshot is from a 22" monitor, it shouldn't be that small of an image.

PS EDIT: I don't know why but it seems the services (ports) it can recognize, it is calling by name. Instead of 80 it says www. That's why 990 doesn't show up, it's the ftps-data that is 990. It's with 's' for secure, it's not port 21.

---

### Post by JKyleOKC on 2012-04-02
Okay, I missed the top two. If you add the "-n" option to your command line, it will show all the ports by number. Otherwise it will translate numbers to names wherever it can. The -n option will also cause IP addresses to show as numbers rather than as names.

I do see that it handled six packets for port 80, so the problem might be something as simple as the web server machine refusing to respond to pings, or possibly to any input at all (although I would have expected that to show up during your testing). What do you see in the filter table's FORWARD rules with "iptables -L -n -v"?

The problem with the screen shot is that my browser (Firefox) displays the attached image in a very small frame at the center of a mostly-black screen. I think that's actually due to the forum software scaling it down, not the browser itself. It makes such screen shots almost unreadable!

---

### Post by darkod on 2012-04-02
Wow, I think I made things worse. In my infinite wisdom (and panic), this morning I did:
iptables -P INPUT ACCEPT
iptables -F

even though I am controlling the firewall with ufw. The idea was to start fresh from scratch. Not to mention I only managed to lock myself out. :)

Luckily only a server reboot was necessary so it can load the ufw rules again and let me in.

But now iptables -L -n -v seems to show ACCEPT for INPUT which is very bad, and it seems to be some hybrid between iptables and ufw. It definitely doesn't let everybody in, I tested it. But I am getting worried leaving it like this.

I wonder if I should switch to raw iptables instead of ufw but since the machine is already at hosting I was trying to avoid doing the switch. And possibly locking myself out again. :)

Is this what you were asking for:
```

Chain INPUT (policy ACCEPT 208 packets, 17517 bytes)
 pkts bytes target     prot opt in     out     source               destination
  209 17605 ufw-before-logging-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0
  209 17605 ufw-before-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0
  209 17605 ufw-after-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0
  209 17605 ufw-after-logging-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0
  209 17605 ufw-reject-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0
  209 17605 ufw-track-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0

Chain FORWARD (policy ACCEPT 9 packets, 456 bytes)
 pkts bytes target     prot opt in     out     source               destination
    9   456 ufw-before-logging-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0
    9   456 ufw-before-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0
    9   456 ufw-after-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0
    9   456 ufw-after-logging-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0
    9   456 ufw-reject-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0

```

EDIT: My mistake. I did the above with ufw disabled. I had it disabled for a test and forgot about it. With ufw enabled the INPUT chain policy is DROP. All the rest is as above.

---

### Post by Doug S on 2012-04-02
Hi darkod,
When you say "shipped off to hosting provider", you mean somewhere on your same office network right? The forward address of 10.0.0.22 is only routable within a private network. (note: I did not re-read all the pages of this posting, so sorry if the answer is there.)

---

### Post by darkod on 2012-04-02
> **Doug S said:**
> Hi darkod,
When you say "shipped off to hosting provider", you mean somewhere on your same office network right? The forward address of 10.0.0.22 is only routable within a private network. (note: I did not re-read all the pages of this posting, so sorry if the answer is there.)

Our production servers are at the same provider and we have private VLAN so we have the 10.0.0.0/24 for us. I have ping to the server, and from the server to the firewall machine. I also have from the firewall to the server: telnet 10.0.0.22 80, it opens the connection.

It's the bloody redirection... Argh...

---

### Post by JKyleOKC on 2012-04-02
Yes, that's the listing I asked for, but I had forgotten that ufw obfuscates the rule list horribly. As you can see from the listing, the FORWARD rules only jump to chains that are defined by ufw itself, and many of them will turn out to be empty in most cases. I've not yet managed to work out the exact path through this forest of obfuscation that might apply in your case.

Somewhere in your FORWARD chain or one of the ufw-defined rules called from it, there must be rules that accept the various ports that you are forwarding. Otherwise, either one of those called chains will DROP the packets, or all of them will fall through and the DROP policy for FORWARD will do the dirty work. In any event, without those ACCEPT rules, nothing will get through the firewall.

The six packets processed through the "nat" table as shown in your screen shot tell us that they're at least getting to the filter table, so your redirection appears to be working as expected. The problem, I think, is a lack of rules in the filter table to accept the packets. Unfortunately, troubleshooting this is where the "uncomplicated" ufw makes things very complicated indeed!

Try an iptables-save with output piped to grep and see what it may show:```
sudo iptables-save | grep ACCEPT
```This should display several lines, and tell us which chains of the filter table the display rules are in. We can then take a close look at any "forward" chains that show up to see more clearly what they are doing.

---

### Post by Doug S on 2012-04-02
I have to go off-line for about 3 hours.
The only other input I have now, is to also check that there is a clear return path for the packets. Even though it will be difficult to look through and follow, maybe post everything from```
sudo iptables-save -c
```

---

### Post by darkod on 2012-04-02
Hold on, I am getting confused.

The way I see it:
1. There are no specific filter rules applied to port 80 in the ufw chains. So, the forward should be done with the default policy.
2. The default policy for both FORWARD and OUTPUT is ACCEPT, not DROP.

Doesn't that mean that without any specific DROP rule, it should let port 80 through the forward chain. And the DNAT entry is telling it where to forward it.

---

### Post by JKyleOKC on 2012-04-02
Yes, it should. However it's possible that ufw is putting a DROP rule somewhere in its generated chains. Try the list/grep command from my previous message but with DROP instead of ACCEPT in it, and see what shows up.

EDIT: It's also possible that the server machine's own internal firewall is rejecting everything, or that the IP address as target for the DNAT rules is incorrect...

---

### Post by darkod on 2012-04-02
Sorry for the late reply. I was traveling home from work. Here are both outputs:
```

root@iafwl2:~# iptables-save | grep ACCEPT
:PREROUTING ACCEPT [23:3358]
:POSTROUTING ACCEPT [2:104]
:OUTPUT ACCEPT [18:1215]
:FORWARD ACCEPT [6:304]
:OUTPUT ACCEPT [0:0]
-A ufw-before-input -i lo -j ACCEPT
-A ufw-before-input -m state --state RELATED,ESTABLISHED -j ACCEPT
-A ufw-before-input -s xx.xx.xxx.xxx/32 -p tcp -m tcp --dport 2233 -j ACCEPT
-A ufw-before-input -s xxx.xxx.xxx.xxx/32 -p tcp -m tcp --dport 2233 -j ACCEPT
-A ufw-before-input -p icmp -m icmp --icmp-type 3 -j ACCEPT
-A ufw-before-input -p icmp -m icmp --icmp-type 4 -j ACCEPT
-A ufw-before-input -p icmp -m icmp --icmp-type 11 -j ACCEPT
-A ufw-before-input -p icmp -m icmp --icmp-type 12 -j ACCEPT
-A ufw-before-input -p icmp -m icmp --icmp-type 8 -j ACCEPT
-A ufw-before-input -p udp -m udp --sport 67 --dport 68 -j ACCEPT
-A ufw-before-input -s 224.0.0.0/4 -j ACCEPT
-A ufw-before-input -d 224.0.0.0/4 -j ACCEPT
-A ufw-before-output -o lo -j ACCEPT
-A ufw-before-output -m state --state RELATED,ESTABLISHED -j ACCEPT
-A ufw-skip-to-policy-forward -j ACCEPT
-A ufw-skip-to-policy-output -j ACCEPT
-A ufw-track-output -p tcp -m state --state NEW -j ACCEPT
-A ufw-track-output -p udp -m state --state NEW -j ACCEPT
-A ufw-user-input -d 10.0.0.12/32 -p tcp -m tcp --dport 2233 -j ACCEPT
-A ufw-user-limit-accept -j ACCEPT

root@iafwl2:~# iptables-save | grep DROP
:INPUT DROP [1:60]
-A ufw-before-input -m state --state INVALID -j DROP
-A ufw-not-local -j DROP
-A ufw-skip-to-policy-input -j DROP
```I have a feeling but can't explain it. I think routing might be messed up, in combination with forwarding rules or not. If the packet doesn't get routed through the machine all else is useless. But routing always worked like a charm, right away.

One more thought, looking at iptables so far. Can I try a temporary entry (they don't get saved by default anyway), something like:
iptables -A -t nat PREROUTING -i eth0 -p tcp --dport 80 -j DNAT --to 10.0.0.22

Should that work straight away?

EDIT: One more thing. Can I safely flush the *nat rules without locking myself out? Something like:
iptables -t nat -F

They seem to be adding on top of older rules with all these trials and tests. Flushing the nat should be safe from SSH access point of view, right?

---

### Post by Doug S on 2012-04-02
Myself, I need to see things in context. I do wonder about this:> -A ufw-not-local -j DROP
Darkod: Are your comfortable using a packet sniffer, such as tcpdump, or tshark, or wireshark? At this point, I would be using one to check the packet level traffic to see and know a what is really going on.

---

### Post by darkod on 2012-04-02
First of all, big thanks to all.

OK, big step forward. Maybe it's coincidence, maybe my networking knowledge is more shaky than I thought.

I'm focused on the routing as I said in my last post. Here is what I found out:
Our webserver will have only private IP sitting behind the firewalls. This is the setup I was testing all the time before shipping the firewall machines.
But, right now, our hosting provider has given us a temporary public IP so we can enter the new webserver and do all the configuration we need. So, it has a public interface (which will not be used in the future) with its public gateway. The private interface was only set up with IP and subnet mask, no gateway.

Without a real logical reason, and going on a hunch, failing all else, I deleted the public gateway and set up the firewall (one then the other) as gateway on the private interface (the way it should be in future).
With the firewall2 as gateway, nothing.
With firewall1 as gateway, voila, finally the IIS7 welcome page. Port forward of 80 worked.

Was this the only reason?

Why doesn't it work with firewall2 since it is also set for routing the same way?

I am also interested to get an answer about flushing the -t nat rules, I wanna clean the older ones.

Opinions? Ideas?

---

### Post by Doug S on 2012-04-02
> EDIT: One more thing. Can I safely flush the *nat rules without locking myself out? Something like:
iptables -t nat -F
 
They seem to be adding on top of older rules with all these trials and tests. Flushing the nat should be safe from SSH access point of view, right?
I will not say definitively one way or the other. I will say that it works on my computer, and I can flush the nat table without loosing my current SSH session (my SSH session is from the LAN, not the internet, but I don't expect that to matter).

---

### Post by darkod on 2012-04-02
OK, I am officially the biggest idiot on this forum. :)

It seems it was the gateway configured on the network card all the time.

Since we are still in installation phase we were always working with the temporary public interface with the gateway set there.
It seems it doesn't understand the internal network properly until you configure a gateway (the firewalls) on it.

I did few tests now from home and got the IIS7 welcome page. Looks good so far.

I'll wait to confirm tomorrow and mark this as solved (second time :) ).

As mentioned, I would appreciate opinions about flushing the -t nat since I was doing tests and changing IPs and rules. As long as I don't lock myself out. :)

And any other ideas are welcome. Thanks a lot guys, girls, friends....

---

### Post by JKyleOKC on 2012-04-02
Each time you enable ufw, it automatically flushes ALL the rules, except those entered via ufw since any previous "ufw disable" command. That means you MUST use a sequence that enables your SSH connection just before you enable ufw, if you're working through SSH. There's a book about Ubuntu Server that goes into some detail on this, although it does not deal with your redirection at all...

---

### Post by darkod on 2012-04-02
Not sure about filter rules, but it definitely doesn't flush nat rules. Remember in the middle of this thread one poster posted one same masquerade rule repeated many times.

That's how it gets that way. With -A it literary appends it, but not deleting the previous ones.

Since at one point I tested with 10.0.0.25 on the server to see if it is IP related, after changing it back to 10.0.0.22 and changing the nat rules in ufw, it left both DNAT rules which was easily visible with iptables -t nat -L -n -v.

But I can confirm for anyone interested, that it is safe flushing the -t nat rules. If you are doing loads of changes, testing, troubleshooting, etc, and you notice many "older" DNAT rules existing as ufw leftover, simply do:
iptables -t nat -F
ufw disable && ufw enable

That will flush everything and create only the existing DNAT rules that you have in ufw at that moment.

I think this is not such a problem with filter rules (the leftovers), but in nat it definitely is. Doing the disable/enable didn't delete the old ones and depending on the order, it might try to forward to some IP that you used as a test and doesn't have the service any more.

---

### Post by darkod on 2012-04-04
OK, I think it is safe to say now that it works as expected.

I have only one question more regarding the iptables scripts Kyle and Doug shared with us. Is it a good practice (or maybe bad and dangerous) to have the following at the start of the file containing the rules:
iptables -F
iptables -t nat -F

The idea would be to flush everything in the filter and nat, just in case anything is there, before starting to append your rules.

Or maybe the iptables is empty when the computer boots as a rule?

---

### Post by JKyleOKC on 2012-04-04
If you use the iptables-restore approach to load the rules, the flush will be done automatically by the iptables-restore program itself. If you use a bash script, then yes, you should flush all three chains at the top of the script.

At the initial boot process, the chains are all empty, but it's still a good idea to flush them explicitly in case you later want to use the script (such as after editing it to change or add a rule).

---

### Post by darkod on 2012-04-04
Yeah, I was thinking of the iptables-restore approach. So they are flushed automatically.

And am I correct in thinking that once the machine is booted you can also do something like:
sudo iptables-restore < /path/filename?

---

### Post by JKyleOKC on 2012-04-04
Yes, you are, and it will still do the flush automatically.

---

### Post by darkod on 2012-04-04
Thanks for all the help. ):P

---

