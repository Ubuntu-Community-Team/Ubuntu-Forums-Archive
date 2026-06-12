---
title: "Firestarter receiving lots of random hits?"
date: 2009-11-24
forum: Security
---

### Post by blufindr on 2009-11-24
I installed Firestarter on the advice of a good friend, but have noticed getting lots of hits from random IP addresses, often many in a short period of time (I've once noted close to 100 in a matter of minutes).  By using [this blog post]("http://blog.spikesource.com/fuser_netstat.htm"), I have determined that the ports getting hit aren't being used by any applications.

I noticed this morning, though, that there were a couple of hits for something called "backdoor-g/Subseven".  After doing a little more research, I was alarmed to find that this is actually a trojan!

A couple of things:
1)  Should I be alarmed by the sheer volume of apparently unrelated hits I keep getting?
2)  I share my internet with my tenants.  Is it possible that they are doing something to cause my system to receive so many hits, given that we're all connected to the internet through the same router?  I'm afraid I'm something of a n00b when it comes to networks.

I was going to attach my Firestarter event log, but apparently in the 12 hours that this laptop's been running, I've received enough hits to warrant a log of 165kB.  I can copy-pasta it, though, if anyone wants it.

---

### Post by XCan on 2009-11-24
Subseven is a VERY old piece of nuisance. Firestarter only guess the program name based on the port being scanned. There are millions of zombies out there doing nothing but scanning day in and day out, thus I would not be concerned. If you are not listening to a port, you are fine.

---

### Post by ApEkV2 on 2009-11-24
Make sure tenants can't change settings in the router, and there aren't any ports forwarded or DMZ enabled.
(unless you play games or XBL)

As long as you haven't changed any iptable settings, or have any services running on your computer, you're ok
Close all applications and after a minute run this command in the terminal [color=blue]sudo lsof -n -i -P[/color]
post results

---

### Post by __p1n__ on 2009-11-24
There's no need to run firestarter.  It's main job is to configure the iptables/netfilter firewall built into linux operating systems.  Once that's done the internal firewall does all the work (and logs hits to the syslog per configuration.)

If you do run the firestarter gui continuously then you will see updates as events occur (it monitors/classifies events in parallel with iptables/netfilter) however it does run as root and it is susceptible to external attacks.  This means that simply running firestarter on a continuous basis increases the attack surface of your computer and consequently lessens security.

If you want to track events as they occur just monitor the system log.

edit: if your router is doing DHCP then you're likely reusing the same IP as your tenants from time to time and one or more of them are possibly already infected.

If you're adventurous then you may care to consider running ncat to capture the traffic and have a look at it.

# ncat --listen --recv-only --verbose --output filename portnum

where portnum is the port number from your firestarter log and filename is the capture logfile.

You will need to open the port for this traffic to get past iptables/netfilter through to the ncat client.

---

### Post by blufindr on 2009-11-25
> **ApEkV2 said:**
> Make sure tenants can't change settings in the router, and there aren't any ports forwarded or DMZ enabled.
(unless you play games or XBL)

As long as you haven't changed any iptable settings, or have any services running on your computer, you're ok
Close all applications and after a minute run this command in the terminal [COLOR=blue]sudo lsof -n -i -P[/COLOR]
post results

I've tried lots of times to change the admin password on my (Belkin F5D8636-4v1) router lots of times, and it just doesn't "stick".  I've been keeping an eye on the settings, and there doesn't seem to be any port forwarding, and the DMZ is disabled.

Results:
```
COMMAND    PID   USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
avahi-dae 1021  avahi   14u  IPv4   4687      0t0  UDP *:5353 
avahi-dae 1021  avahi   15u  IPv4   4688      0t0  UDP *:35283 
hddtemp   1289   root    0u  IPv4   5077      0t0  TCP 127.0.0.1:7634 (LISTEN)
cupsd     1424   root    5u  IPv6 378109      0t0  TCP [::1]:631 (LISTEN)
cupsd     1424   root    6u  IPv4 378110      0t0  TCP 127.0.0.1:631 (LISTEN)
gweather- 2024 linnie   19u  IPv4 370762      0t0  TCP 192.168.2.4:50754->140.90.128.70:80 (ESTABLISHED)
gweather- 2024 linnie   20u  IPv4 370763      0t0  TCP 192.168.2.4:34232->210.8.186.60:80 (ESTABLISHED)
dhclient  2054   root    5u  IPv4  11743      0t0  UDP *:68 
```Oh, and I also have no access to the DHCP client list on my router.  I can click on it, but it never loads.  ::grumpy::

---

### Post by BkkBonanza on 2009-11-25
Hits on any particular port are only of concern if a vulnerable application is listening on the port. If you are not sharing your printer across your network you might consider disabling "cupsd" - it appears to run as root (handles printer sharing), and increases your attack surface. I think there was vulnerabilities long ago but I don't recall hearing of any lately.

It's pretty common nowadays to get hits from the web. If you're behind a router then it should be filtering that mostly all out. Make sure NAT is active and ports aren't forwarded. If you are still getting stuff showing up then likely people in your building (if they share your lan, sounds like they do) are mucking around trying to find vulnerabilties to exploit. Just because they hit doesn't mean they can get in.

If it really annoys you then you could put another router between you and the building lan. That will filter it out before it hits your machine. But as mentioned above and here, hits don't mean much if nothing is listening.

---

### Post by XCan on 2009-11-25
> **BkkBonaza said:**
> If you are still getting stuff showing up then likely people in your building (if they share your lan, sounds like they do) are mucking around trying to find vulnerabilties to exploit.


It is also highly likely that they're simply infected bots doing their scanning.

---

### Post by bodhi.zazen on 2009-11-25
Honestly, monitoring "hits" on firestarter is of very little use.

They were all blocked and so are of no real consequence.

Now I agree nothing will instill paranoid like watching such tings, but really what are they ?

If you want to monitor your network traffic learn to use a NIDS such as snort or something like wireshark to examine the packets.

If you want to monitor your host to see if you have been cracked take a look at OSSEC.

To be honest, both snort and OSSEC are overkill for most users, but watching your logs for blocked packets is on little to no use whatsoever.

---

### Post by update_manager on 2009-11-26
> **blufindr said:**
> 
A couple of things:
1)  Should I be alarmed by the sheer volume of apparently unrelated hits I keep getting?
2)  I share my internet with my tenants.  Is it possible that they are doing something to cause my system to receive so many hits, given that we're all connected to the internet through the same router?  I'm afraid I'm something of a n00b when it comes to networks.


#1 Yes and no. Any router is going to have a ton of hits on it from RPC type stuff. You should ignore what doesn't matter, which is easier said than done.

#2 Yes.

Try installing fwsnort, it'll give more detailed logs. You also should probably write custom iptables rules.

---

### Post by blufindr on 2009-11-27
> **update_manager said:**
> #1 Yes and no. Any router is going to have a ton of hits on it from RPC type stuff. You should ignore what doesn't matter, which is easier said than done.

#2 Yes.

Try installing fwsnort, it'll give more detailed logs. *You also should probably write custom iptables rules*.

You lost me.  :\

---

### Post by bodhi.zazen on 2009-11-27
> **blufindr said:**
> You lost me.  :\

No offence intended but ...

Networking is complicated as is cracking activity. If you do not understand the basics, what is it about Firestarter and a flashing virtual button that makes you feel more secure ?

Start with the basics, what servers do you have installed ?

What are you wanting a firwall to do for you ?

How much or little do you know about networking ?

How much or little do you know about cracking ?

How much are you willing to learn ?

If you do not wish to learn these things, just use ufw or gufw. You do not need Firestarter and without additional understanding and learning on your part Firestarter, and it's flashing light, does not add to your security.

---

### Post by blufindr on 2009-11-29
> **bodhi.zazen said:**
> No offence intended but ...

Networking is complicated as is cracking activity. If you do not understand the basics, what is it about Firestarter and a flashing virtual button that makes you feel more secure ?

Start with the basics, what servers do you have installed ?

What are you wanting a firwall to do for you ?

How much or little do you know about networking ?

How much or little do you know about cracking ?

How much are you willing to learn ?

If you do not wish to learn these things, just use ufw or gufw. You do not need Firestarter and without additional understanding and learning on your part Firestarter, and it's flashing light, does not add to your security.

Eh, it's okay, I know I'm epic n00b at this.

I installed Firestarter because my friend told me to, and he was going to DMZ my laptop (no clue why).  There's no network, per se, in my house.  Everyone does connect to the same router, so I dunno if that counts as a network.  I just want something to stop other computers from getting into my computer, if that makes any sense.

I'm willing to learn, as long as someone's willing to teach, and be okayish with my absolute lack of knowledge.

---

### Post by OpSecShellshock on 2009-11-29
Hmm. Not sure what your friend has in mind, but the thing is that  a DMZ is located outside the firewall but still inside the network. Something like that is a bit more important in an enterprise network than in a home network, because sometimes network and security admins want to see what's going on and compare that to what is actually getting through. Point is, if you're concerned about keeping your own personal computer out of an unfiltered stream of shady incoming traffic, the DMZ is not the place to put it. Keep all of the devices behind the hardware firewall.

---

### Post by perspectoff on 2009-11-30
> **__p1n__ said:**
> There's no need to run firestarter.  It's main job is to configure the iptables/netfilter firewall built into linux operating systems.  Once that's done the internal firewall does all the work (and logs hits to the syslog per configuration.)

If you do run the firestarter gui continuously then you will see updates as events occur (it monitors/classifies events in parallel with iptables/netfilter) however it does run as root and it is susceptible to external attacks.  This means that simply running firestarter on a continuous basis increases the attack surface of your computer and consequently lessens security.

If you want to track events as they occur just monitor the system log.

edit: if your router is doing DHCP then you're likely reusing the same IP as your tenants from time to time and one or more of them are possibly already infected.

If you're adventurous then you may care to consider running ncat to capture the traffic and have a look at it.

# ncat --listen --recv-only --verbose --output filename portnum

where portnum is the port number from your firestarter log and filename is the capture logfile.

You will need to open the port for this traffic to get past iptables/netfilter through to the ncat client.


All ports in Ubuntu are open by default, not closed. I don't know where the urban legend that they are closed by default came from. (If all the ports in Ubuntu were closed at installation, you wouldn't be able to access the Internet, perform software installation, or a myriad of other activities.)

Ubuntu is susceptible to a large number of trojans, and the behaviour of Ubuntu users is to install almost any package on the flimsiest of advice (given the other urban legend that there are no viruses or trojans for Linux).

Managing iptables is very difficult for the average user, and Firestarter is one of the easier methods. Monitoring port events is not a bad thing.

If you check your system log, you will see that there are many processes running as root. 

Your assertion that Firestarter is susceptible to external attack is based on what?

If there is such a vulnerability that you have found in the code, please post it, or send it to the Firestarter developers.

Otherwise, don't just post more nonsense in the forums hoping to create more urban legends.

---

### Post by perspectoff on 2009-11-30
> **bodhi.zazen said:**
> Honestly, monitoring "hits" on firestarter is of very little use.

They were all blocked and so are of no real consequence.

Now I agree nothing will instill paranoid like watching such tings, but really what are they ?

If you want to monitor your network traffic learn to use a NIDS such as snort or something like wireshark to examine the packets.

If you want to monitor your host to see if you have been cracked take a look at OSSEC.

To be honest, both snort and OSSEC are overkill for most users, but watching your logs for blocked packets is on little to no use whatsoever.

I can't believe the bad advice in this forum today. The programs you mention are not trivial to install and use. They are for heavy duty geeks and crackers and IT administrators, not for the casual mom-and-pop user.

ufw and gufw are not easy to configure, except for the same type of users.

Firestarter is. And there are many times when it is necessary to open and close ports easily, and then to examine the effects of doing so, using the "flashing lights" telling you when something is trying to use a port.

Here's an example: the gpg keyserver requires port 11371 to be open. Firestarter lets you easily open it, download your key, then close it again.

Recently, I had a bad network slowdown. Using a combination of Etherape (also runs as root) and Firestarter, I was able to pinpoint the culprit: a Pulseaudio network module.

Turning it off cleared up my network.

Yes, eventually I could have figured it out by examining packets, but then I would have had to be a networking expert.

You guys need to tailor your advice, and give correct advice.

---

### Post by __p1n__ on 2009-11-30
> **perspectoff said:**
> 
Your assertion that Firestarter is susceptible to external attack is based on what?

If there is such a vulnerability that you have found in the code, please post it, or send it to the Firestarter developers.

Otherwise, don't just post more nonsense in the forums hoping to create more urban legends.

1. The firestarter gui runs as root and parses the syslog for netfilter logged events.  It's consequently susceptible to any overflow/shellcode attack via that vector.  You can easily parse the syslog with a non-uid=0 process to get that same information.

2. Firestarter hasn't been touched by Tomas Junnonen or any other developer since 2005 so good luck on getting any response on a bug report.

3. The list of user-services and misc-services that are "understood" by the firestarter classifier is very short and is circa 2005.  Firestarter will not flag an "attack" (really just an iptable-logged event) as critical unless the destination port is under 1024.

4. The firestarter "lock" function is misleading as it only refers to the firestarter configuration and not the actual iptables rules which the kernel uses to do the real work.  Of course if you make any manual change to iptables then that will be reverted to the current (locked or not) firestarter configuration when firestarter is restarted.

5. If the original poster wanted to capture the bo traffic then he would clearly need to open that port since he directly stated that he was seeing that event in the firestarter gui which means of course that iptables was logging it and likely dropping it owing to the default firestarter netfilter rules module.  This has nothing to do with port status (actually default service status) on a vanilla ubuntu desktop installation.

I would suggest first understanding what you're attempting to talk about before you post comments such as "nonsense" and "fud" on these forums.

---

### Post by bodhi.zazen on 2009-11-30
@ [perspectoff]("http://ubuntuforums.org/member.php?u=257693") :

First let me say that if you are happy with Firestarter the by all means use it. Firestarter does have some issues and does not work for everyone.

Second, I can see you have some strong opinions, and I am not going to debate them with you, but some things need clarification.

1. GUFW is a graphical interface to ufw. Enabling ufw is a single command and the GUFW interfaces is as easy to install and use as Firestarter.

See my blog entries for details :

[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)

So while you may prefer Friestarter, it is obvious from your post you are completely unfamiliar GUFW.

===

Many of your other claims are off topic, and some are inaccurate. 

2. Open ports. You are confusing the definition of an open port with the default configuration of Ubuntu and your post is thus misleading.

By default there are no significant open ports in Ubuntu.

By default iptables is unconfigured. This is a mixed blessing. For new users, since there are no open ports to firewall, this is probably sufficient and is certainly easier then having new users have to configure their firewalls. For those who aer more security consciouis, or those who run servers, you may wish to configure your firewall.

3. Although there are vulnerabilities in any OS, your post is again misleading. There are simply no active viruses or spyware that affect Ubuntu at this time.

For any who are interested in security , please do not take [perspectoff]("http://ubuntuforums.org/member.php?u=257693") 's posts at face vaule. Please see : [Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") The security sticky is maintained by myself with the assistance of many in the community including the Ubuntu staff and is a much better source of information.

4. Your characterization of packat analysis is way beyond the OP question and is not a feature one normally ascribes to firewalls. ufw , gufw, and firestatrer all log packets and network information , but none of these are considered network monitoring tools. 

Snort is by far the standard NIDS, and if you want to look at packest you need a tool such as wireshark.

Again, ufw has as many features as Firestarter and your post simply shows you have little or no familiarity with either ufw or gufw.

Please do not post in such a hostile fashion.

---

### Post by EJeanmaire on 2009-11-30
> **perspectoff said:**
> All ports in Ubuntu are open by default, not closed. I don't know where the urban legend that they are closed by default came from. (If all the ports in Ubuntu were closed at installation, you wouldn't be able to access the Internet, perform software installation, or a myriad of other activities.)


Let me shine some light on this, traffic can go outbound on a given port, or inbound on a given port.  With that beind said, Ubuntu will let all traffic leave outbound on any port (not a concern, this will let you view websites, etc). 

As for inbound/incoming connections, Ubuntu will allow them all! Whoa scary sounding, right? Wrong.  Unless a 'service' on your computer is listening on that port (ftp server, vnc server, telnet server, ssh server, etc) nothing will happen.  If you are running services like those I mentioned, then yes you have a problem, and thats where a firewall would come in handy.

So in reality, it is not really "wide-open" by default.

---

