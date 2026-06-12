---
title: "ssh getting hammered by login attempts... is this normal?"
date: 2012-01-02
forum: Security
---

### Post by ouch67 on 2012-01-02
I'm wondering how normal it is for a server to get hammered by login attempts? (kinda comical the amount of different names used...)

Also is there some way to configure linux to just kill the connection after say 3 failed attempts?

would setting up ssh to use some random port help?

Or do I have to resort to blocking everything and white listing only the ip's I use?

thanks for any help, I've used linux for years, but this is my first server with it... quite a pleasant experience except for the damn hackers without a life knocking on the door...

---

### Post by Ms. Daisy on 2012-01-02
Yup, totally normal. There are lots of automated login attempts, too.

Did you read the [security sticky]("http://ubuntuforums.org/showthread.php?t=510812")?  Check out the [SSH ubuntu help page]("https://help.ubuntu.com/community/SSH"), too.

---

### Post by lisati on 2012-01-02
[Fail2ban]("https://help.ubuntu.com/community/Fail2ban") (which is mentioned in the [security sticky]("http://ubuntuforums.org/showthread.php?t=510812")) is easily configured to help block IP addresses which abuse SSH.

---

### Post by Dangertux on 2012-01-02
A third method would be via rate limiting. Which in my opinion is more effective than adding ip's to iptables, which can become extraordinarily cumbersome as the list of blocked IP's increases.

A simple way to rate limit would be the following

```

iptables -A INPUT -i eth0 -p tcp --dport 22 -m conntrack --ctstate NEW -m recent --set 
iptables -A INPUT -i eth0 -p tcp --dport 22 -m conntrack --ctstate NEW -m recent --update --seconds 30 --hitcount 7 -j DROP

```

or alternatively using denyhosts, which is similar to fail2ban however it uses hosts.allow, hosts.deny to filter them thus keeping the  strain off conntrack and allowing netfilter to operate unencumbered.

Hope this helps.

---

### Post by Doug S on 2012-01-02
In addition to the previous very good replies:
 
I have been using the following rules for several years now and quite like it:```
-A INPUT -m recent --update --hitcount 3 --seconds 5400 --name BADGUY_SSH -j DROP
-A INPUT -p tcp -m tcp --dport 22 -m recent --set --name BADGUY_SSH -j ACCEPT

```To work properly, those rules need to go somewhere after this rule:```
-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
```While very rare, I have seen SSH attacks simulataniously with attacks on other ports from the same IP address. Once the BADGUY triigger is set, all packets, not just ones for port 22, are dropped from the IP address. These rules also prevent my log files from becoming clogged with the SSH attack crap. The lockout time is 90 minutes. I am seeing more and more SSH attacks that stop and come back a number of hours later and try again. Once I have seen an attack that actually seemed to figure out my old lockout time and it would come back just after it expired (which is when I increased it to 90 minutes).
You can subsitute REJECT for the DROP, if you prefer (and many knowledgeable forum contributers do).

---

### Post by ouch67 on 2012-01-03
wow thanks, it's certainly better than what I had before! my auth logs are now much smaller ;)

---

### Post by mattxhand on 2012-01-03
I take it that this server sits directly on the web? If so, Fail2Ban is your best option. There are spiders crawling the web constantly running brute force/dictionary attacks on anything they can. I see it at work ALL the time. Have you traced it down to a single IP or are they using multiple?

---

### Post by Ryan Dwyer on 2012-01-04
I find the most effective solution is to block port 22 externally and forward SSH through a different port. Most (all?) scripts attempt to connect on port 22 and if nothing responds they'll move on to a different machine. It's not worth their time to portscan your computer. 99.99% of scripts will never touch an open SSH port on your computer.

Combine this with another option such as firewall rules, fail2ban, or key authentication. And of course don't allow root to log in through SSH.

---

### Post by ouch67 on 2012-01-05
Well what I'm going to is is install the server edition of Ubuntu. I have the desktop edition because I thought it would be easier to set up and maintain. But I'm finding I use the terminal almost exclusively anyway. (network settings is a lot easier with a GUI, but I'll manage)

So I'm going to do that and set up SSH to run on a different port with keys, (I have a sentence length username/password right now) and try to implement Doug S's ipconfig settings, set up fail2ban and apparmor... Then get snort running to double check the traffic...

Should keep the bots out at least... ;)

And if not well I just use this server to compile open source libs/apps that I use at home or at work. I currently run a ftp service (I guess I should make the switch to sftp really...) when I want files and stop it once I have them. It would be kinda funny if someone spent weeks trying to break in only to find it's nothing but free software, a atom processor and an old hard drive, lol.

I'm glad this forum is here though, I was looking at my old logs and I was astonished to find that the very day I forwarded ports on my router the server was attacked.

Also most of the IP's seem to orgininate from china. Is hacking not illegal there or are there just a lot of compromised systems being used as a bot net?

---

### Post by Lars Noodén on 2012-01-05
As was pointed out to me recently, you can do the rate limiting in one line now:

```

   ip6tables -I INPUT -p TCP --dport 22 -m state --state NEW -m limit --limit 4/minute --limit-burst 5 -j ACCEPT
   iptables  -I INPUT -p TCP --dport 22 -m state --state NEW -m limit --limit 4/minute --limit-burst 5 -j ACCEPT

```

---

### Post by Ms. Daisy on 2012-01-05
> **ouch67 said:**
> Also most of the IP's seem to orgininate from china. Is hacking not illegal there or are there just a lot of compromised systems being used as a bot net?
If you know what you're doing, you can make your IP address look like it's coming from anywhere.

---

### Post by Dangertux on 2012-01-05
> **Ms. Daisy said:**
> If you know what you're doing, you can make your IP address look like it's coming from anywhere.

Umm... What?

Yes and no... It's easy to spoof an ip address. Extremely easy, that being said don't expect to actually complete a connection. If you're talking about proxying sure, but that's not making your ip look like anything, that's proxying through another interface, your IP is still yours.

So I guess I'm not really sure what you're saying here.

---

### Post by Ms. Daisy on 2012-01-05
LOL- clearly I'm saying I don't know!  So what would the bad guy's IP address look like on my log if a bad guy spoofs one and then cracks me?

---

### Post by Dangertux on 2012-01-05
> **Ms. Daisy said:**
> LOL- clearly I'm saying I don't know!  So what would the bad guy's IP address look like on my log if a bad guy spoofs one and then cracks me?

A bad guy wouldn't spoof an IP and then crack a user account on SSH with it. This is inherently not possible due to the way TCP/IP works.

The following explanation will consult this diagram of a packet header: [http://www.postfixvirtual.net/ip.header.png](http://www.postfixvirtual.net/ip.header.png)

Note the source address, when an IP address is spoofed this is forged, normally a packet sent from your machine to another would have a legitimate source IP address, yours. When a spoofed IP is used this area is forged to be something else. 

Now let's look at the TCP connection sequence. (see here for more info [http://en.wikipedia.org/wiki/Transmission_Control_Protocol](http://en.wikipedia.org/wiki/Transmission_Control_Protocol))

Anyways so first we need to SYNchronize our connection when we do this the server we are SYNcrhonizing with will send us an ACKnowledgement, we will then return SYNchronize and ACKnowledge, once this is complete we have established a connection. This is the three way hand shake.  Now if we're spoofing our address the return ACKnowledgement will never make it to us (it's using our source ip from our packet header). Since this doesn't happen we can never send SYNchronize/ACKnowledge thus a connection will not be created.

Thus we compromise a middle man machine. Likely another weak SSH service, then use that to brute force additional machines. Since it is proxying our connection the IP will appear as it is this machine. However, because it will still receive packets, since it is the actual source of the traffic the connection will be successfully created.

Hope this was helpful.

---

### Post by Ms. Daisy on 2012-01-05
> **Dangertux said:**
> 

Hope this was helpful.
Immensely. Thanks

---

### Post by jramshu on 2012-01-05
+1 DT. Well explained.

They shell a server, upload a proxy, then use that to crack boxes. 
It's a quite effective way to become anonymous.

As usual Mods:
If what I post is inappropriate, delete it.

---

### Post by Ms. Daisy on 2012-01-06
> **jramshu said:**
> +1 DT. Well explained.

They shell a server, upload a proxy, then use that to crack boxes. 
It's a quite effective way to become anonymous.

As usual Mods:
If what I post is inappropriate, delete it.
I think if you explain that in extreme detail so that I could actually DO that, then the mods could be keen to delete you.  As your post stands now, the servers of the world are all quite safe from Ms. Daisy :P

---

### Post by Dangertux on 2012-01-06
> **jramshu said:**
> +1 DT. Well explained.

They shell a server, upload a proxy, then use that to crack boxes. 
It's a quite effective way to become anonymous.

As usual Mods:
If what I post is inappropriate, delete it.

The nifty thing about compromising an SSH service is you don't even have to upload a proxy, you have one right there for you.

:-/

---

### Post by d3v1150m471c on 2012-01-06
i've always been a fan of port knocking. btw, if you only need access to ssh on a specific address space, like on a LAN or a VPN, you can edit the settings in the conf file.

---

