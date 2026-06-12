---
title: "ideal settings for ufw"
date: 2012-11-02
forum: Security
---

### Post by jsvidyad on 2012-11-02
Hello,

   I have a question regarding necessary settings for ufw firewall. Is it enough if I set incoming to deny and outgoing to allow? Do I have to do anything different or more than this to make my system as secure as possible? Should I change outgoing also to deny and add rules to allow outgoing access to just certain ports or applications? Please advise.

---

### Post by jerome1232 on 2012-11-02
I, don't configure it at all on my Desktop machine, I have no servers installed anyways so nothing is listening, not to mention I'm behind a decent router, which acts as a sort of hardware firewall.

If you must, go ahead and set it to drop all incoming connections, configuring outbound connections may be more of pain than it is worth, since many of your applications will need to create outbound connections to function.

If your really worried about security, take a look at your browser. What plugins do you use? Java and Flash are the two most commonly exploited things around. Configure a decent apparmor profile for your firefox. Find some decent security related addons, I just use addblock+ and ghostery. One blocks adds, the other prevents cross site scripting.

---

### Post by mike acker on 2012-11-02
> **jerome1232 said:**
> {snip} configuring outbound connections may be more of pain than it is worth, since many of your applications will need to create outbound connections to function.
{snip}

:confused: can I make application related rules in ufw?  it was my understanding I needed to use AppArmor for that

normally we do not want any app to access the net unless it specifically has permission. Basically Firefox and Thunderbird.  anything else we want to know what it's doing.  not everybody "out there" is a good guy.

---

### Post by jerome1232 on 2012-11-02
UFW is really just a user friendly frontend to iptables, which doesn't support application based rules. Since iptables isn't application based you would have to allow outbound traffic on ports 80, 443 and 25 at the very least, probably some more. Since it's not an application based firewall that means *any* application could send traffic out those ports rendering outbound rules like this useless for preventing anything "reporting" to somebody without your knowledge.

If you want to limit what specific applications can do, use apparmor. I highly recomend using an apparmor profile for firefox. I also wanted to note that you are using open source software, anyone can view the source code, it's not likely that it is collecting data and sending it off without a big hub bub being raised and it being widely known.

---

### Post by Ms. Daisy on 2012-11-02
> **jsvidyad said:**
> Hello,

   I have a question regarding necessary settings for ufw firewall. Is it enough if I set incoming to deny and outgoing to allow? Do I have to do anything different or more than this to make my system as secure as possible? Should I change outgoing also to deny and add rules to allow outgoing access to just certain ports or applications? Please advise. The answer totally depends on what you're trying to accomplish and on what services you run on your computer. 

There are people that run no firewall on their computer. There are those that only rely upon their router hardware firewall.

If you have no services (no daemons like ssh, ftp...) running, then you can follow [this guide]("http://ubuntuforums.org/showthread.php?t=1876124") for an above-average security posture.  

You can go paranoid and deny all outgoing & incoming, then add rules for the services you need (like 80, 53, 443).

---

### Post by cariboo on 2012-11-02
> **jerome1232 said:**
> UFW is really just a user friendly frontend to iptables, which doesn't support application based rules. Since iptables isn't application based you would have to allow outbound traffic on ports 80, 443 and 25 at the very least, probably some more. 

Why would you need ports 80, 443 and 25 open, if you aren't running a server. Outbound connections are on random ports, so you don't need to specify any, for outbound connections.

```
chromium- 2387 cariboo  102u  IPv4 164784      0t0  TCP 192.168.0.10:**41961**->173.194.33.3:443 (ESTABLISHED)
chromium- 2387 cariboo  103u  IPv4  15180      0t0  TCP 192.168.0.10:**44350**->173.194.79.125:5222 (ESTABLISHED)
chromium- 2387 cariboo  128u  IPv4 166819      0t0  TCP 192.168.0.10:**38566**->173.194.33.7:443 (ESTABLISHED)
```

I've bolded the three outbound connections on my system, and the ports you mentioned are nowhere to be seen.

---

### Post by jerome1232 on 2012-11-02
> **cariboo907 said:**
> Why would you need ports 80, 443 and 25 open, if you aren't running a server. Outbound connections are on random ports, so you don't need to specify any, for outbound connections.

```
chromium- 2387 cariboo  102u  IPv4 164784      0t0  TCP 192.168.0.10:**41961**->173.194.33.3:443 (ESTABLISHED)
chromium- 2387 cariboo  103u  IPv4  15180      0t0  TCP 192.168.0.10:**44350**->173.194.79.125:5222 (ESTABLISHED)
chromium- 2387 cariboo  128u  IPv4 166819      0t0  TCP 192.168.0.10:**38566**->173.194.33.7:443 (ESTABLISHED)
```I've bolded the three outbound connections on my system, and the ports you mentioned are nowhere to be seen.

Whoops, I don't ever actually mess with outbound connections and was assuming that if I was talking to a web server on an established connection it would be all going along port 80 etc...

Thanks for pointing out my mistake.

That just makes it more of pita to configure outbound connections.

---

### Post by OpSecShellshock on 2012-11-03
If you default deny outgoing connections and then set up "allow out" rules, then the 80, 443, 53, etc. applies to the destination port and not the source port, so you don't have to individually allow the random high ports for outgoing connections.

But that only applies if outgoing connections are default denied (which will stop any network activity from functioning if left alone).  If you do the traditional deny-in/allow-out, which is what you get with the default deny setting, then you don't need to worry about allowing specific destination ports.

---

### Post by jsvidyad on 2012-12-14
Hello, 

   From the posts in this thread, what I understand is that a secure enough configuration for ufw is to deny incoming connections and allow outgoing connections. Does this advice hold for Gufw too? 

  Is it worthwhile to deny outgoing connections too and let outgoing traffic just on some ports?

---

### Post by chadk5utc on 2012-12-14
> **jsvidyad said:**
> Hello, 

   From the posts in this thread, what I understand is that a secure enough configuration for ufw is to deny incoming connections and allow outgoing connections. Does this advice hold for Gufw too? 

  Is it worthwhile to deny outgoing connections too and let outgoing traffic just on some ports?

Gufw is the graphic version of ufw which is command line and both are easy interfaces for iptables. Deny all and create rules to allow only that which is needed.

---

### Post by Hungry Man on 2012-12-14
I don't really see the point in an outbound firewall. At this point the attacker has control over a program, and if there is any logic in this world it's a program that has internet access - what's an outbound Firewall going to do? If you take serious efforts to isolate programs from each other by using LSM and user/groups and then you create specific network rules in apparmor and firewall rules that rejects ports to specific users etc... then maybe it's going to provide something.

As for inbound, I question the necessity.

On a system like Ubuntu you have no open ports by default except for system services like dhclient.

So... let's imagine we have no firewall: One port open, dhclient running behind it.

Let's imagine we have a firewall: One port open, dhclient running behind it.

Hmmmmm.

Let's say I have a firewall and I add a rule that opens port Y but no service is running behind port Y. Am I less secure? I don't think so - port Y isn't vulnerable, there's nothing to interact with behind it.

I run an inbound Firewall because it doesn't interfere with me and I just assume that I've completely missed something because everyone else seems to think it's important. I recommend you run an inbound firewall as well and that you assume I'm just wrong.

---

### Post by Morbius1 on 2012-12-14
Let me take Hungry Man's logic one step further.

Let's say I have no "firewall" enabled ( I put firewall in quotes because ufw isn't a firewall despite it's name ). As stated above only the dhcpclient port is open. Now I install Samba so I can share files across my home network. When I do that the Samba ports are open and listening for queries. That’s what I want to happen.

OK, so now I read through the forum and everyone is telling me that I have to enable the "firewall" so I do that and now Samba doesn't work. Now what do I do? I have to open the Samba ports. What's the net affect of all this? Nothing except extra work.

If you are running a machine behind your own router you already are running behind a firewall in the form of NAT since no one can see you directly. Here's my current ip address: 192.168.0.100. Try to ping me ;)  If you have a laptop that can be anywhere at any given time or a desktop that connects directly to the internet without the benefit of a router then by all means enable the firewall if it makes you feel better.

What I suggest to folks who make the mistake of asking for my opinion is buy a router even if you have no other machines on your lan so that you can take advantage of its built in inherent firewall capacity ( NAT ). If you have a laptop then enable the "firewall" when you are out and about. When you are behind the safety of your home router disable it.

---

### Post by Ms. Daisy on 2012-12-14
> **Morbius1 said:**
> If you are running a machine behind your own router you already are running behind a firewall in the form of NAT since no one can see you directly. Here's my current ip address: 192.168.0.100. Try to ping me ;)  Good point unless you're on a public network (like at school, starbucks, library, whatever).  If I'm at the same Starbucks as you my IP is 192.168.0.101. If I'm malicious I would try to get access to your Samba shares. 

What you could easily do is deny all incoming on your firewall. You could disable it at home but when you went on a public network you would enable it, thus preventing malicious folks like me from seeing your Samba shares.

---

### Post by haqking on 2012-12-14
> **Ms. Daisy said:**
> Good point unless you're on a public network (like at school, starbucks, library, whatever).  If I'm at the same Starbucks as you my IP is 192.168.0.101. If I'm malicious I would try to get access to your Samba shares. 

What you could easily do is deny all incoming on your firewall. You could disable it at home but when you went on a public network you would enable it, thus preventing malicious folks like me from seeing your Samba shares.

Starbucks use WPA dont they from T-Mobile ?

WPA isolates you on the network, thats why hotspots use WPA even though the key is public

Not to say its not possible though, but to get around that the attacker will likely not give a plop about your firewall either ;-)

---

### Post by Ms. Daisy on 2012-12-14
> **haqking said:**
> Starbucks use WPA dont they from T-Mobile ?

WPA isolates you on the network, thats why hotspots use WPA even though the key is public

Not to say its not possible though, but to get around that the attacker will likely not give a plop about your firewall either ;-)You'd be isolated if the wifi network were set up that way. But is that standard practice now? Maybe I'm the only one that doesn't trust the 17-year-olds working at McDonald's to ensure the wifi is configured properly. Hmm.  I'll have to run a quick nmap next time I'm on free wifi, see what's visible.

---

### Post by haqking on 2012-12-14
> **Ms. Daisy said:**
> You'd be isolated if the wifi network were set up that way. But is that standard practice now? Maybe I'm the only one that doesn't trust the 17-year-olds working at McDonald's to ensure the wifi is configured properly. Hmm.  I'll have to run a quick nmap next time I'm on free wifi, see what's visible.

last few starbucks i were in were using WPA, I am pretty sure since the google sniff they changed corporate policy, but who knows.

My post wasnt really important to the thread ;-)

---

### Post by Ms. Daisy on 2012-12-14
> **haqking said:**
> My post wasnt really important to the thread ;-)
Then what are you posting for? :P

No actually I'm interested in knowing whether it matters to have a firewall.  I guess the firewall on a public wifi network will prevent the vast majority of the population from seeing your Samba shares.  

Now if I were on the same subnet as, say, haqking, I would definitely want a few extra layers of security on my  laptop (and have damn good backups at home ;) )  I think it's been said a lot- there's not much you can do to protect yourself against a targeted attack.  But surely enabling the firewall on a public network isn't a waste of time.

---

### Post by haqking on 2012-12-14
> **Ms. Daisy said:**
> Then what are you posting for? :P

No actually I'm interested in knowing whether it matters to have a firewall.  I guess the firewall on a public wifi network will prevent the vast majority of the population from seeing your Samba shares.  

Now if I were on the same subnet as, say, haqking, I would definitely want a few extra layers of security on my  laptop (and have damn good backups at home ;) )  I think it's been said a lot- there's not much you can do to protect yourself against a targeted attack.  But surely enabling the firewall on a public network isn't a waste of time.

I never mentioned not enabling the firewall, it should always be enabled and with tight inbound and outbound rules IMO, i was merely mentioning about you being in starbucks doing a scan that was all ;-) which was a pointless post by me really as some starbucks isolate and some dont im sure.

---

### Post by Hungry Man on 2012-12-14
Startbucks doesn't use WPA. Even if they did it's a shared key that everyone uses, I don't think it would matter.

> 
No actually I'm interested in knowing whether it matters to have a firewall. I guess the firewall on a public wifi network will prevent the vast majority of the population from seeing your Samba shares. 

If you have a Firewall and you use Samba you're going to allow incoming on the ports. Going to a different network you then have two options:

1) Turn off the samba sharing
2) Use your firewall

Both are valid, I suppose. I'd just rather disable the listening service, but either will do.

---

### Post by haqking on 2012-12-14
> **Hungry Man said:**
> Startbucks doesn't use WPA. Even if they did it's a shared key that everyone uses, I don't think it would matter.


If you have a Firewall and you use Samba you're going to allow incoming on the ports. Going to a different network you then have two options:

1) Turn off the samba sharing
2) Use your firewall

Both are valid, I suppose. I'd just rather disable the listening service, but either will do.

some starbucks use WPA, it depends on the provider, some of them use T-Mobile which enforce WPA for the hotspots.

As for shared key, the key is irrelevant in the instance as WPA itself isolates the user on the network (for the casual hacker that is), hotspots use WPA for that purpose to prevent sniffing not to prevent people connecting (an example would be firesheep)

---

### Post by Ms. Daisy on 2012-12-14
> **Hungry Man said:**
> ...I run an inbound Firewall because it doesn't interfere with me and I just assume that I've completely missed something because everyone else seems to think it's important. I recommend you run an inbound firewall as well and that you assume I'm just wrong.
oh btw thank you for that- it thoroughly amused me. How uncharacteristically humble of you :P

It's layers, Hungry Man. 
More layers ==> warmer, fuzzier feeling in my tummy.

---

### Post by Ms. Daisy on 2012-12-14
> **haqking said:**
> some starbucks use WPA, it depends on the provider, some of them use T-Mobile which enforce WPA for the hotspots.

As for shared key, the key is irrelevant in the instance as WPA itself isolates the user on the network, hotspots use WPA for that purpose to prevent sniffing not to prevent people connecting Just for the record Starbucks uses AT&T in the states. 

WPA gives you the ability to isolate users on the network, but it doesn't require isolation. Am I wrong there?

---

### Post by haqking on 2012-12-14
> **Ms. Daisy said:**
> Just for the record Starbucks uses AT&T in the states. 

WPA gives you the ability to isolate users on the network, but it doesn't require isolation. Am I wrong there?

I know they do, thats why i said "some", and i dont understand what you mean by require ?

The reason some hotspots use WPA even though everyone has the key and anyone can connect is to stop the casual surfer from sniffing others traffic with tools such as firesheep etc

---

### Post by haqking on 2012-12-14
as an addition for those who use Starbucks in the USA, AT&T hotspots dont use any type of encryption LOL


From [http://secure.sbc.com/support/faq.adp](http://secure.sbc.com/support/faq.adp)

> AT&T does not enable WEP (Wired Equivalency Protection) or WPA  (Wi-Fi Protected Access) on any of the wireless equipment used in its  public Wi-Fi networks.I believe in the UK they use T-Mobile who enforce WPA or at least do in some of the ones I have been in, which makes casual sniffing and machine access harder even though the key is public access

but now i have taken the thread off topic so im gonna shut up now ;-)

---

### Post by Ms. Daisy on 2012-12-14
Sure, makes sense. 

Your previous posts made it sound like WPA isolates them in this sense: > Enable Wireless Isolation If checked, the wireless client under this  SSID can only access internet and it can&#8216;t access other wireless clients  even under the same SSID, Ethernet clients or this device. Other  clients can&#8216;t access the wireless client, either. So isolation is an option but it's not the default for any given router.

---

### Post by haqking on 2012-12-14
> **Ms. Daisy said:**
> Sure, makes sense. 

Your previous posts made it sound like WPA isolates them in this sense:  So isolation is an option but it's not the default for any given router.

that is seperate, WPA by design segments the machine to a degree which prevents casual sniffing, the Wireless Isolation mode on routers which is a check box can offer isolation even if its WEP or non encrypted  network, but router dependant

For example WPA wont prevent you from contacting wired machines such as the router itself, if you enable Wireless isolation it will or should prevent you from accessing the router aswell

---

### Post by Hungry Man on 2012-12-14
> oh btw thank you for that- it thoroughly amused me. How uncharacteristically humble of you 
I have moments.
> 
It's layers, Hungry Man. 
More layers ==> warmer, fuzzier feeling in my tummy.
hmmm, I think I've got something for this!

"There's a big difference between layered security and a pile of security apps."

[Firewalls are code. Code is attack surface.]("https://technet.microsoft.com/en-us/security/bulletin/ms11-083")

Still. I think the benefits (which I don't know, but I assume they're there) are likely more than the downsides.

---

### Post by JKyleOKC on 2012-12-15
> **Hungry Man said:**
> I don't really see the point in an outbound firewall. At this point the attacker has control over a program, and if there is any logic in this world it's a program that has internet access - what's an outbound Firewall going to do? If you take serious efforts to isolate programs from each other by using LSM and user/groups and then you create specific network rules in apparmor and firewall rules that rejects ports to specific users etc... then maybe it's going to provide something.The one and only time that my LAN was actually infected by a virus -- the "Chernobyl" one that had the ability to destroy motherboards -- it was an outbound firewall that alerted me to the situation. The virus tried immediately to call home, and the firewall asked my permission to let its packets through.

That was back in the days of Win95, before I had switched to Linux as my main tool, and the firewall was Kerio's "Tiny Personal Firewall." However it made me a firm believer in the value of an outbound firewall, especially one that (like Kerio's program then) associates its rules with specific programs.

Unfortunately I've not found a way to make such association via iptables, and as a result my set of rules does allow all outbound traffic to the WAN interface. However that doesn't mean that controlling outbound isn't every bit as important as controlling inbound...

EDIT: Perhaps "apparmor" can provide the program association I've been missing; I'll have to dig into it a bit more deeply to see what it can do in this respect.

---

### Post by Morbius1 on 2012-12-15
> **Ms. Daisy said:**
> > Originally Posted by **Morbius1**                     [[IMG]http://ubuntuforums.org/images/rebrand/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=12404243#post12404243")                 
                 *If you are running a machine behind  your own router you already are running behind a firewall in the form of  NAT since no one can see you directly. Here's my current ip address:  192.168.0.100. Try to ping me :wink:*
Good point unless you're on a public network (like at school, starbucks, library, whatever).  If I'm at the same Starbucks as you my IP is 192.168.0.101. If I'm malicious I would try to get access to your Samba shares. 

What you could easily do is deny all incoming on your firewall. You could disable it at home but when you went on a public network you would enable it, thus preventing malicious folks like me from seeing your Samba shares.
Is there any reason why you didn't read all the way to the end of my post - it was just 3 more sentences:
> If you have a laptop then enable the "firewall" when you are out and  about. When you are behind the safety of your home router disable it.     

---

### Post by Ms. Daisy on 2012-12-15
> **Morbius1 said:**
> Is there any reason why you didn't read all the way to the end of my post - it was just 3 more sentences:
Unless total laziness is a reason, then no. Whoops!

[QUOTE=Hungry Man]"There's a big difference between layered security and a pile of security apps."[/QUOTE]
Gee, seems like that would make a great signature. :P

---

### Post by offgridguy on 2012-12-15
> **Ms. Daisy said:**
> The answer totally depends on what you're trying to accomplish and on what services you run on your computer. 

There are people that run no firewall on their computer. There are those that only rely upon their router hardware firewall.

If you have no services (no daemons like ssh, ftp...) running, then you can follow [this guide]("http://ubuntuforums.org/showthread.php?t=1876124") for an above-average security posture.  

You can go paranoid and deny all outgoing & incoming, then add rules for the services you need (like 80, 53, 443).
Thank you; Ms. Daisy for the link.

---

### Post by JKyleOKC on 2012-12-15
> **Ms. Daisy said:**
> Gee, seems like that would make a great signature. :PI like the one you already use!

---

### Post by Hungry Man on 2012-12-15
> Gee, seems like that would make a great signature. 

Yeah, I thought you might like it =P

---

### Post by Ms. Daisy on 2012-12-16
> **haqking said:**
> Starbucks use WPA dont they from T-Mobile ?

WPA isolates you on the network, thats why hotspots use WPA even though the key is public

Not to say its not possible though, but to get around that the attacker will likely not give a plop about your firewall either ;-)FWIW I ran nmap today on a few free wifi networks. Starbucks actually had me isolated (I hate it when haqking is right) :P But the other two networks, Five Guys and Moe's, didn't- I could see a bunch of other nodes.  Moral of the story: you might be isolated on a free wifi network, you may not.  It's not a terrible idea to check when you attach (with your computer or your phone).

---

### Post by Hungry Man on 2012-12-16
Pretty sure ettercap and sslstrip will work fine in a starbucks unless things have changed recently.

---

### Post by haqking on 2012-12-16
> **Hungry Man said:**
> Pretty sure ettercap and sslstrip will work fine in a starbucks unless things have changed recently.

I was talking about the casual sniffer/skiddie using tools like firesheep etc.

There are a ton of ways to circumvent the isolation, I was just saying the cursory config of WPA isolates.

---

### Post by Ms. Daisy on 2012-12-16
> **Hungry Man said:**
> Pretty sure ettercap and sslstrip will work fine in a starbucks unless things have changed recently.
I'm sure someone who knows what they're doing can get around isolation pretty easily. But being isolated on a public wifi network would probably protect you from the vast majority of the casual surfers in the world.  I was pleased to see I was isolated on the Starbuck's network. I think it's the least a provider can do to protect their customers.

---

