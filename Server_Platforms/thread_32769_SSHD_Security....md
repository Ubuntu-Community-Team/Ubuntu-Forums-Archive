---
title: "SSHD Security..."
date: 2005-05-09
forum: Server Platforms
---

### Post by dmccarney on 2005-05-09
Hello,

Before I begin, please note that I'm new to linux, and generally not incredibly well versed in computer security.

Recently I installed Ubuntu and the first challenge I decided would be to install SSH so I can connect to my box from work. After a little troube I finally managed to do this. Of course it involved opening and forwarding port 22 on my linksys router. I didn't really think much of this but on Friday my logs show that my SSHD came under attack by what looks to me to be just your run of the mill dictionary attack. My auth.log is full of entries about invalid users and they tried everything from run of the mill names to the names of popular programs and daemons. Fortunately, I don't think they ever got past the username stage and had to attempt to break the password. But this is definately leaving me thinking... What can I do to beef up security on my sshd. My password is hard to guess and would certainly not be broken by a dictionary attack. I also have the attackers IP address in my logs, but I am unsure of what to do with it. The log is also full of "reverse mapping check failures" and in big bold worn of Possible Breakin Attempts. I'm not too sure what it was trying to acomplish with these reverse mapping checks, I assume to locate the opposing ip address, either way it failed. 

I was wondering if there is a way to configure SSHD to refuse connections from an IP after X number of invalid usernames/passwords/etc. 
My current logs show on average about 1 username guess per 1-2 seconds over an extended period. This in no way characterizes my normal use patterns :P I might blunder on a password once or twice but it won't be 200 times in 1 hour.

I guess I could in theory set up some sort of trusted site list and filter my traffic to port 22 based on which ips are on that list, but I am unaware of how to do this myself and would prefer to find a better solution.

Thanks for any help/suggestions/etc you can offer me.

---

### Post by Xerampelinae on 2005-05-09
Yeah, that happens.  You get lots of that kind of stuff especially if you use IRC.

Just edit the /etc/ssh/sshd_config file to your heart's content.  Use "man sshd_config" to see all the options.  You can disable root, only allow X connections at a time, and only allow certain usernames to connect via ssh (disable root via ssh too)... among other things.

---

### Post by LordHunter317 on 2005-05-09
Those attacks are common, ignore them.

You've already done most of what you can to defend against them.

Besides disabling root logins, the only other real measure you can take is to switch to using keypair authentication.

---

### Post by Beernut on 2005-05-13
I was uncomfortable with those login attempts also but they are common.  So I setup keyed authentication like LordHunter317 mentioned it's really pretty easy to do.  I submitted a HowTo: here in the forums or you can get to the one on my site from the link in my sig.

---

### Post by tweter on 2006-09-05
I can't give you specifics because i don't know them but i guy i was in college with had a system set up with a "port knocker" i think thats what it was but basicly you had to hit a certain number of ports in a certain order before the system would even show that there was a port 22 available to use. it was a really intresting demonsration that he gave

i'm not to sure where to start looking for it

-tweter

---

### Post by b0red on 2006-09-06
Add this to /etc/hosts.allow basically it only allows certain IP's to login to your sshd. Stop the buggers at the network level ;)

sshd: host.domain.here 21.158.211.40 192.168.0.0/24 213.128.0.0/24
sshd: ALL: DENY

Then setup no-ip.org or ssh into another server with a static IP first if you don;t already have a static IP.

---

### Post by lesve on 2006-09-06
I'm running a firewall machine with two (three with localhost) and
I wonder if it possible to have different configuration for sshd
on the interface out_in_the_internet world and other interface
which is to local net.

                  Regards

---

### Post by ore on 2006-09-27
I've used an sshd wrapper program for a couple of years that adds rules to iptables after certain failures etc and blocks those ips making those ips. its called sshcop i think. I think the statistics were something like 1300 attempts at gaining root access it allowed only 2 to go through and those would never have gone through if root was disabled. Of course works for normal user accounts as well.

---

### Post by btdown on 2006-09-28
You can apt-get install either the fail2ban package or the denyhosts package. I'm not sure which repo they are in (maybe universe or multiverse). I'm using denyhosts and am happy with it. It does exactly what you are looking for.

---

### Post by pcman1975 on 2007-04-13
You could use the excelent denyhosts: denyhosts.sourceforge.net.

---

### Post by MJN on 2007-04-13
I think denyhosts can become a bit of a pain when you accidentally trip it yourself - trauling through multiple files to rip out your IP is downright annoying.
 
I prefer fail2ban instead. Horses for courses really, however I am a much bigger fan of fail2ban's blocking methodology i.e. temporary blocking (the offending IPs quickly go away so I don't see much point in blocking them for life) rather than denyhosts ever-growing file of bad IPs.
 
Mathew

---

