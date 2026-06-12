---
title: "Port Fowrarding - Safe/Unsafe?"
date: 2010-09-08
forum: Security
---

### Post by darms21 on 2010-09-08
Can any1 explain to me the risk I am taking when I apply port forwarding to my router @ home? Is it a risk to every computer on the network or just specifically the server that is involved? Any additional detail above and beyond would be greatly appreciated too!!!!

---

### Post by bodhi.zazen on 2010-09-08
It is a risk to the server involved as you are allowing anyone and everyone to attempt to connect to and crack into the server. The consequence depends on the server (VNC vs ssh vs apache), the competence of the cracker, and your competence as a sysadmin.

Once the server is compromised it can be leveraged against every box on your LAN and/or other boxes on the internet (see bot net).

---

### Post by bilkay on 2010-09-08
> **bodhi.zazen said:**
> It is a risk to the server involved as you are allowing anyone and everyone to attempt to connect to and crack into the server. The consequence depends on the server (VNC vs ssh vs apache), the competence of the cracker, and your competence as a sysadmin.

Once the server is compromised it can be leveraged against every box on your LAN and/or other boxes on the internet (see bot net).
Open the port and the hackers will come.

However, opening port 22 for ssh can be extremely useful. The question, I think, is whether the benefit is worth the risk, and how best to minimize the risk.

---

### Post by bodhi.zazen on 2010-09-08
> **bilkay said:**
> Open the port and the hackers will come.

However, opening port 22 for ssh can be extremely useful. The question, I think, is whether the benefit is worth the risk, and how best to minimize the risk.

For port 22 - Use keys, disable passwords, and use either iptables or denyhosts/fail2ban.

---

### Post by CharlesA on 2010-09-08
> **bodhi.zazen said:**
> For port 22 - Use keys, disable passwords, and use either iptables or denyhosts/fail2ban.

+1.

That's what I do without any problems.

@OP: It depends on the service and how you secure it.

---

### Post by bilkay on 2010-09-08
> **bodhi.zazen said:**
> For port 22 - Use keys, disable passwords, and use either iptables or denyhosts/fail2ban.

The Ubuntu Security sticky suggests using a non-standard port for ssh, but then says this is not recommended (but doesn't say why). One drawback I've found is that I can't figure out how to tell rsync to use the non-standard port for ssh transfers. I thought setting variable SSH_CONNECTION according to the ssh man page might do it but it didn't.

---

### Post by bodhi.zazen on 2010-09-08
> **bilkay said:**
> The Ubuntu Security sticky suggests using a non-standard port for ssh, but then says this is not recommended (but doesn't say why). One drawback I've found is that I can't figure out how to tell rsync to use the non-standard port for ssh transfers. I thought setting variable SSH_CONNECTION according to the ssh man page might do it but it didn't.

That is the downside, you would need to configure your clients to use the non-standard port.

IMO it is much easier to use the default port, 22, and secure it then it is to change the port.

IMO changing the port is security through obscurity and, again IMO, quiets the logs but adds little to security.

---

### Post by scottuss on 2010-09-08
> **bodhi.zazen said:**
> That is the downside, you would need to configure your clients to use the non-standard port.

IMO it is much easier to use the default port, 22, and secure it then it is to change the port.

IMO changing the port is security through obscurity and, again IMO, quiets the logs but adds little to security.

I'd argue that running SSH on a non standard (and high) port *does* makes you more secure. It's not the only solution you should go for, but it does add an additional layer. Looking through logs, automated bots that attempt to crack SSH on port 22 don't bother to go for SSH on much higher ports.

Sure, someone could still do port scans with nmap etc to figure out which port you have SSH on, but that takes longer and most automated systems are set to look for 22, and if it's not there, move on.

I really really don't see why people say there's no benefit to moving from port 22, there is a great benefit. It's not a silver bullet but it sure as hell adds to the overall security strategy. (It might break compatibility with some things, so that's something to keep in mind)

---

### Post by bodhi.zazen on 2010-09-08
> **scottuss said:**
> I'd argue that running SSH on a non standard (and high) port *does* makes you more secure. It's not the only solution you should go for, but it does add an additional layer. Looking through logs, automated bots that attempt to crack SSH on port 22 don't bother to go for SSH on much higher ports.

Sure, someone could still do port scans with nmap etc to figure out which port you have SSH on, but that takes longer and most automated systems are set to look for 22, and if it's not there, move on.

I really really don't see why people say there's no benefit to moving from port 22, there is a great benefit. It's not a silver bullet but it sure as hell adds to the overall security strategy. (It might break compatibility with some things, so that's something to keep in mind)

Nothing like reading the logs to instill paranoia :twisted:

Do you wear a parachute and scuba gear in the car because you might drive off a cliff and fall into the ocean ? Certainly that would be safer, after all, you never know.

IMO secured is secured, closed is closed, a system that uses keys only (disabled passwords) is invulnerable to the script kiddies regardless of port. period. nothing further is required and changing the port adds nothing, IMHO, except the hassle of configuring your clients.

But if you prefer to change the port, go for it.

---

### Post by CharlesA on 2010-09-08
> **bodhi.zazen said:**
> That is the downside, you would need to configure your clients to use the non-standard port.

IMO it is much easier to use the default port, 22, and secure it then it is to change the port.

IMO changing the port is security through obscurity and, again IMO, quiets the logs but adds little to security.

Definitely easier to just leave it on the default port and secure it then it is to have to jump thru extra hoops to get stuff to work.

> **scottuss said:**
> I'd argue that running SSH on a non standard (and high) port *does* makes you more secure. It's not the only solution you should go for, but it does add an additional layer. Looking through logs, automated bots that attempt to crack SSH on port 22 don't bother to go for SSH on much higher ports.

Sure, someone could still do port scans with nmap etc to figure out which port you have SSH on, but that takes longer and most automated systems are set to look for 22, and if it's not there, move on.

I really really don't see why people say there's no benefit to moving from port 22, there is a great benefit. It's not a silver bullet but it sure as hell adds to the overall security strategy. (It might break compatibility with some things, so that's something to keep in mind)

If SSH isn't running on port 22, you would probably get less chatter in the logs, but it's still mostly a "security thru obscurity" thing. If someone really wanted to get in, they'd just do a port scan and attack the port that SSH was running on.

It does help filter bots out, but in the time I've had ssh exposed (using keys only and setting iptables to drop any connections from an ip after 8 hits in 60 seconds) I haven't had any problems with being compromised.

---

### Post by OpSecShellshock on 2010-09-08
> **scottuss said:**
> I'd argue that running SSH on a non standard (and high) port *does* makes you more secure. It's not the only solution you should go for, but it does add an additional layer. Looking through logs, automated bots that attempt to crack SSH on port 22 don't bother to go for SSH on much higher ports.

Sure, someone could still do port scans with nmap etc to figure out which port you have SSH on, but that takes longer and most automated systems are set to look for 22, and if it's not there, move on.

I really really don't see why people say there's no benefit to moving from port 22, there is a great benefit. It's not a silver bullet but it sure as hell adds to the overall security strategy. (It might break compatibility with some things, so that's something to keep in mind)

From the perspective of the target server, there's no functional difference between an intruder trying to connect and failing and that same intruder not trying at all because port 22 isn't open.

---

### Post by BkkBonanza on 2010-09-09
To the user trying to get rsync to work on an alternate port, you need to add the -e option, eg.

rsync -e "ssh -p 2121" ...etc or if with other options you can combine,

rsync -vztpre "ssh -p 5432" ...

Also, if this is a "regular" occurence you can append it to the ~/.ssh/config per host,

Host snoogle.com
Port 3456

That a single line of cfg change to accomdate an alternate port - not much hassle.
eg. from the cmd line

**echo -e "Host snoogle.com\nPort 7654" >> .ssh/config;**

After this ssh and commands using ssh like rsync will use that port for that host.

---

### Post by uRock on 2010-09-09
Would nmap find an open ssh port if it were set as a port other than 22? Say we open port 37 as the ssh port, would nmap find it?

I'll have to try this soon.

---

### Post by BkkBonanza on 2010-09-09
Yes, of course. Though it may not identify it's function correctly. It usually lists the service using just "normal assignments". It may be able to fingerprint it but that's less reliable.

The point of setting it on a high port is that most scanners only scan a few known ports because they are eager to scan as many hosts as possible. After all they are looking for the easy, low hanging fruit.

It takes much, much longer to scan thousands of high ports especially when they are in stealth mode and the scanner has to timeout. Also the chances of a user having key auth or tighter security once they change to an alternate port is much higher too. So it's a losing game - they just scan the easy stuff.

Now, of course, if someone targets you specifically they will scan all 65536 ports to find you and they will find it. It's not security per se, it's obscurity. It simply cuts out the continuous noise out there - which is more annoying than threatening.

---

### Post by scottuss on 2010-09-09
Just to clarify: I never said you would be less likely to be compromised if someone really wanted to get in to your system by running on a port other than 22, but you certainly would be able to notice a "legitimate" hack attempt in your logs as opposed to the hundreds of bot attempts you would see with the service running on port 22. 

So in essence, actually, it does add some security, albeit through obscurity. There's nothing at all wrong with that, as long as it isn't the only thing you rely on.

---

### Post by scottuss on 2010-09-09
> **uRock said:**
> Would nmap find an open ssh port if it were set as a port other than 22? Say we open port 37 as the ssh port, would nmap find it?

I'll have to try this soon.

Indeed it would, and fairly quickly. However, set it to a really high port, and although it would still find it, it would take much longer and any casual cracker would probably give up and move on to the next host. You'd also see in your logs if he/she found the port and attempted to access the service, whereas if the service was on port 22, the attempt would be muddled in with hundreds of other attempts by people who assume it's on 22, and by automated bots that assume port 22.

Again, it's not a magic super security blanket that will save the world, but I advise changing, that's just my view.

---

### Post by Bachstelze on 2010-09-09
> **bodhi.zazen said:**
> 
IMO secured is secured, closed is closed

Oh, boy, no. Never take security for granted, ever. Always expect the unexpected. Even if somethng is perfectly secure at time t does not mean it will be secure at time t+1.

---

### Post by Grenage on 2010-09-09
While moving the port is security through obscurity, I do always change the port.  It's no real effort to specify the port during an ssh command.

---

### Post by CharlesA on 2010-09-09
> **Bachstelze said:**
> Oh, boy, no. Never take security for granted, ever. Always expect the unexpected. Even if somethng is perfectly secure at time t does not mean it will be secure at time t+1.

I suppose that's true. If you are only allowing something like SSH with keys only, the only way for it to get compromised via SSH is if someone had yer private key. I suppose that could happen, but it's unlikely. Hopefully you have a strong passphrase on the private key.

If you've got something like Apache open, then you could get royally screwed if a new exploit was discovered.

---

### Post by cj.surrusco on 2010-09-09
I use two ports for my ssh server. Port 22 and a very high one. I use port 22 for all of the connections inside the network, because it is easier to configure, and I have the higher port opened on my router for access to the internet. I just have a strong password on it, because in my opinion, keys are are a hassle, especially when you ssh from a bunch of different locations.

---

### Post by bodhi.zazen on 2010-09-09
> **Bachstelze said:**
> Oh, boy, no. Never take security for granted, ever. Always expect the unexpected. Even if somethng is perfectly secure at time t does not mean it will be secure at time t+1.

While I agree with that statement, I think you are taking my comments out of context. IMO changing the port for ssh does so little to increase security that I would not advise using it at all.

What I have advocated is :

1. Keys only, disable passwords.

2. Using iptables or a service such as denyhosts or fail2ban.

If a cracker can get through those security features, changing the port will not help.

---

### Post by bilkay on 2010-09-09
I think it's safe to say that you're much more likely to have your network broken into by someone stealing your laptop than by someone hacking your ssh keys.

---

### Post by bilkay on 2010-09-09
> **CharlesA said:**
> Definitely easier to just leave it on the default port and secure it then it is to have to jump thru extra hoops to get stuff to work.



If SSH isn't running on port 22, you would probably get less chatter in the logs, but it's still mostly a "security thru obscurity" thing. If someone really wanted to get in, they'd just do a port scan and attack the port that SSH was running on.

It does help filter bots out, but in the time I've had ssh exposed (using keys only and setting iptables to drop any connections from an ip after 8 hits in 60 seconds) I haven't had any problems with being compromised.
What's the ufw command? And why 8 hits? Why not a lower number?

Good discussion!

---

### Post by blur xc on 2010-09-09
> **bodhi.zazen said:**
> While I agree with that statement, I think you are taking my comments out of context. IMO changing the port for ssh does so little to increase security that I would not advise using it at all.

What I have advocated is :

1. Keys only, disable passwords.

2. Using iptables or a service such as denyhosts or fail2ban.

If a cracker can get through those security features, changing the port will not help.

I read somewhere when I was first learning about ssh that some institutions block port 22 (schools, hotels, public wifi hotspots) but there's a better chance that the higher ports would be open.  So, if you need to ssh in form a location that blocks port 22, using something else might still work.  dunno if it's true- I've only ever ssh'd from my inside of my home network.

Also - do you have any tutorials on how to forward a port and set up those security measures?  I would like to ssh into my home pc from the outside, but I'm networking challenged.  And if security depends on my competence as a sysadmin, then I'm setting myself up for getting hosed.

Thanks,
BM

---

### Post by bodhi.zazen on 2010-09-09
> **bilkay said:**
> What's the ufw command? And why 8 hits? Why not a lower number?

Good discussion!

If you  use scp or if you use svn+ssh , the scp protocol uses one "hit" per file , thus a number such as 8.

Each "hit" will give you (by default) 5 attempts at a password. With a decent password, 40 attempts is trivial, with keys it does not matter.

in terms of iptables a "hit" is a new connection (as opposed to established).

---

### Post by bodhi.zazen on 2010-09-09
> **blur xc said:**
> I read somewhere when I was first learning about ssh that some institutions block port 22 (schools, hotels, public wifi hotspots) but there's a better chance that the higher ports would be open.  So, if you need to ssh in form a location that blocks port 22, using something else might still work.  dunno if it's true- I've only ever ssh'd from my inside of my home network.

Also - do you have any tutorials on how to forward a port and set up those security measures?  I would like to ssh into my home pc from the outside, but I'm networking challenged.  And if security depends on my competence as a sysadmin, then I'm setting myself up for getting hosed.

Thanks,
BM

That would be a valid reason to change the default port, as would the desire to quiet the logs.

For information see :

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

For "port forwarding" see your router documentation or

[http://portforward.com/](http://portforward.com/)

For port forwarding client side , what port ? http ? vnc ?

[Proxy Firefox through a SSH tunnel "how to" @ Calomel.org - Open Source Research and Reference]("https://calomel.org/firefox_ssh_proxy.html") 

[http://martybugs.net/smoothwall/puttyvnc.cgi](http://martybugs.net/smoothwall/puttyvnc.cgi)

---

### Post by CharlesA on 2010-09-09
> **bilkay said:**
> I think it's safe to say that you're much more likely to have your network broken into by someone stealing your laptop than by someone hacking your ssh keys.

That's why you have a strong passphrase on yer private key. Also, if yer laptop was stolen, I would hope recreating your keypair would be a priority.

> **bilkay said:**
> What's the ufw command? And why 8 hits? Why not a lower number?

Good discussion!

I had it set for 4 hits originally, but it kept locking me out when using scp, or tweaking tunnel configuration.

I don't know how to set it in ufw, but the command for iptables is this:

```
sudo iptables -A INPUT -p tcp --dport 22 -m state --state NEW -m recent --set --name  SSH --rsource
sudo iptables -A INPUT -m recent --update --seconds 600 --hitcount 4 --rttl --name SSH  --rsource -j DROP

```

Note: That counts ***all*** connections, not just failed ones.

> **blur xc said:**
> I read somewhere when I was first learning about ssh that some institutions block port 22 (schools, hotels, public wifi hotspots) but there's a better chance that the higher ports would be open.  So, if you need to ssh in form a location that blocks port 22, using something else might still work.  dunno if it's true- I've only ever ssh'd from my inside of my home network.

Also - do you have any tutorials on how to forward a port and set up those security measures?  I would like to ssh into my home pc from the outside, but I'm networking challenged.  And if security depends on my competence as a sysadmin, then I'm setting myself up for getting hosed.

Thanks,
BM

There's a good tutorial for iptables [here]("http://bodhizazen.net/Tutorials/iptables/"). Also check out the SSH docs [here]("https://help.ubuntu.com/community/SSH"). As for port forwarding, you might want to check out the site [here]("http://portforward.com/"), as it has a lot of info about port forwarding.

---

