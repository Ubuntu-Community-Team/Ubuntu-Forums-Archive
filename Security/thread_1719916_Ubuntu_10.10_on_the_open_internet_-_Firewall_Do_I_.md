---
title: "Ubuntu 10.10 on the open internet - Firewall: Do I need it?"
date: 2011-04-02
forum: Security
---

### Post by chowno on 2011-04-02
So the title pretty much says it all.  I have my computer on the open internet and I am wondering if I need to install a firewall monitor or anything similar.  I'm assuming IPtables is doing its job but still better safe than sorry.  If the default settings from installation aren't good enough then what programs do you recommend using and further what rules would you recommend employing - I'm not intending on using this computer as a gateway/router or a remote access server but just a regular PC so total lock-down is good but I would still like to use the internet and such.  I remember using gufw to open up the ports to do windows filesharing back when I had other MS comps on my network but now its just my buntu-box so I don't need those ports anymore.  Any help would be greatly appreciated.  Thanks!

---

### Post by cariboo on 2011-04-02
If you are connected directly to the internet, not through a router, you can use one of the many port scanning web sites to check if you have anything open. If you are behind a router, just relax and enjoy your system.

---

### Post by brian_p on 2011-04-02
The default settings are splendid for your purposes. Use and enjoy.

---

### Post by chowno on 2011-04-02
Okay great! I had the feeling that was the case.  I am having trouble finding a site to scan my ip but oh well I might just get nmap and do it my self.  Thanks for your quick responses!

---

### Post by donato roque on 2011-04-02
you can visit grc.com. they have excellent port scans. if the goal is to discover open ports and such and to test just one machine then this site is for you. 

[Link here.]("https://www.grc.com/x/ne.dll?bh0bkyd2")

---

### Post by tgm4883 on 2011-04-02
> **brian_p said:**
> The default settings are splendid for your purposes. Use and enjoy.

This is only true if he doesn't install any additional software

---

### Post by brian_p on 2011-04-02
> **tgm4883 said:**
> This is only true if he doesn't install any additional software

I cannot recollect the default settings of any package I've installed giving cause for concern with respect to security.

---

### Post by tgm4883 on 2011-04-03
> **brian_p said:**
> I cannot recollect the default settings of any package I've installed giving cause for concern with respect to security.

Then you either 

A) Didn't install any additional software (that was network aware)
B) Already run a firewall
or
C) Didn't look to see what the applications were doing

The premise behind running a firewall is so nothing outside of your machine can connect to running software on your machine that is listening for connections. The reason that the default Ubuntu installation doesn't need a firewall is that no default software is listening for connections (which happens to be the same reason that default Windows installations need a firewall, because by default they are listening for connections). As soon as you start installing non default software the better the chance that something is now listening for connections.

---

### Post by The Cog on 2011-04-03
If I were direct on the internet, I would probably not be happy with the default settings. I don't have a default install here to look at right now, but from memory there are two applications listening:

* dhcp client remains listening (UDP port 68 or 69) if you are configuring your IP address with DHCP. Why it doesn't close the port after getting an address is a mystery to me, but it sits there with an open port.

* avahi-daemon (High UDP port number) [http://avahi.org/](http://avahi.org/). I have yet to discover anything useful that this piece of software does. But it is there in a default install, listening for incoming requests.

Use the command```
sudo netstat -plantu
```to see a list of listening ports. You can ignore ports listening on 127.0.0.1 or ::1 because these are the IPv4 and IPv6 loopback ports which are not reachable from external connections.

P.S.
I meant to add: You can enable the firewall to block all incoming connections with the command
```
sudo ufw enable
```
but then you will have to do more work allowing incoming connections through the firewall if you do choose to install a server such as SSH or a web server.

---

### Post by brian_p on 2011-04-03
> **tgm4883 said:**
> Then you either 

A) Didn't install any additional software (that was network aware)
B) Already run a firewall
or
C) Didn't look to see what the applications were doing

0/3. My installation of a service is always preceded by copious reading and my use of netfilter is not security orientated.

The listening software which comes with an initial intallation (yes, there is some) is configured safely. CUPS, for example. My experience of non-default services (exim4, sshd, unbound and dovecot among others) is that they too have default configurations which are conservative and safe. And of course they will listen for connections when started because that is what services do.

If there is a service which is unsafe in its default state perhaps you would name it.

---

### Post by brian_p on 2011-04-03
> **The Cog said:**
> 

* avahi-daemon (High UDP port number) [http://avahi.org/](http://avahi.org/). I have yet to discover anything useful that this piece of software does. But it is there in a default install, listening for incoming requests.

You might find the discussion [[COLOR="Blue"]here[/COLOR]]("http://lists.debian.org/debian-devel/2011/03/msg00093.html") interesting.

---

### Post by chowno on 2011-04-03
Oh wow I never imagined such a wave of responses.  Cool!  Anyway, I tried the ufw command and the service is telling me that it is enabled and is active on startup - so I guess I'm covered now.  If I need services to be allowed past the firewall I'll just download Gufw and add the rule.  Thanks for the vibrant discussion!

---

### Post by steevven1 on 2011-04-03
I'm a little bit surprised at the responses here. All I'm hearing is, "Make sure no programs are listening for connections, and if they are, block them!"

There are lots of programs that need to listen in order to do what they do (sshd, apache, etc). What advice can be given to people who use these sorts of programs?

---

### Post by Irihapeti on 2011-04-03
> **steevven1 said:**
> I'm a little bit surprised at the responses here. All I'm hearing is, "Make sure no programs are listening for connections, and if they are, block them!"

There are lots of programs that need to listen in order to do what they do (sshd, apache, etc). What advice can be given to people who use these sorts of programs?

Yes, you will need a firewall if you are running any of those.

You would also to read up thoroughly on how to secure them. There's more to it than just having a firewall. If you look around these forums, you'll find that most people who have been "owned" have been running one of these programs - usually sshd or vnc - and not set it up properly.

---

### Post by cjsteele on 2011-04-03
Even out of the box, I find there are things running that I'd never have turned-on on an internet accessible box (e.g. portmapper, and others.)  That said, any time I turn-up a new ubuntu box, my first step (after install gets done slip-streaming updates) is to turn-off unnecessary services and light-up the firewall.  There's no good reason not to run a firewall, and millions of possible reasons (e.g. every IP on the Internet) to enable it.

Just my $0.02.

-C

---

### Post by tgm4883 on 2011-04-03
> **brian_p said:**
> 0/3. My installation of a service is always preceded by copious reading and my use of netfilter is not security orientated.

The listening software which comes with an initial intallation (yes, there is some) is configured safely. CUPS, for example. My experience of non-default services (exim4, sshd, unbound and dovecot among others) is that they too have default configurations which are conservative and safe. And of course they will listen for connections when started because that is what services do.

If there is a service which is unsafe in its default state perhaps you would name it.

Anything that listens for connections. In a regular installation, why would you want ANYTHING listening for connections while you are on a public network?

---

### Post by bodhi.zazen on 2011-04-04
> **chowno said:**
> So the title pretty much says it all.  I have my computer on the open internet and I am wondering if I need to install a firewall monitor or anything similar.  I'm assuming IPtables is doing its job but still better safe than sorry.  If the default settings from installation aren't good enough then what programs do you recommend using and further what rules would you recommend employing - I'm not intending on using this computer as a gateway/router or a remote access server but just a regular PC so total lock-down is good but I would still like to use the internet and such.  I remember using gufw to open up the ports to do windows filesharing back when I had other MS comps on my network but now its just my buntu-box so I don't need those ports anymore.  Any help would be greatly appreciated.  Thanks!

The short and easy solution is to simply enable your firewall.

```
sudo ufw enable
```

The longer answer is you do not need to run a firewall so long as you are not running any services. You mentioned file sharing (samba) in your post, are you still running samba ?

If you disable (remove) any server software you can go without a firewall.

So the question is then how much or little do you know about your system and how much time do you want to spend ? And how paranoid are you ?

If it were my system I would disable all listening services and firewall it, YMMV and while you can listen to the various opinions of others only you can decide the best solution for yourself.

---

