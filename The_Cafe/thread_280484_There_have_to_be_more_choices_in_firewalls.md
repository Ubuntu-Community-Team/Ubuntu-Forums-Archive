---
title: "There have to be more choices in firewalls"
date: 2006-10-19
forum: The Cafe
---

### Post by TheRingmaster on 2006-10-19
I would like to say that ubuntu and the like are lacking firewall choices. Is firestarter (iptables frontend) all we have. I know that there is gaurddog (another frontend) for kde, but I couldn't figure that program out (too complicated). Is there a stand-alone program (not iptables based) that we could use? Could we run a windows firewall (comodo) under wine?

just some thoughts,

JP

---

### Post by hkgonra on 2006-10-19
I don't run a firewall on my local machines I always just use a good firewall on the front end and then let all my machines hookup to that. Have you ever considered this option.

---

### Post by Lord Illidan on 2006-10-19
> **jpazindustries said:**
> I would like to say that ubuntu and the like are lacking firewall choices. Is firestarter (iptables frontend) all we have. I know that there is gaurddog (another frontend) for kde, but I couldn't figure that program out (too complicated). Is there a stand-alone program (not iptables based) that we could use? Could we run a windows firewall (comodo) under wine?

just some thoughts,

JP

What other firewalls would you like? What features?

I don't think comodo would be too good under Wine.. try this though : [http://sourceforge.net/projects/xfwall/](http://sourceforge.net/projects/xfwall/)

---

### Post by TheRingmaster on 2006-10-19
I only have one computer so that won't work.

---

### Post by TheRingmaster on 2006-10-19
I would like to see an open-source firewall that is like comodo personal firewall (this is a windows firewall).

---

### Post by TheRingmaster on 2006-10-19
> **Lord Illidan said:**
> What other firewalls would you like? What features?

I don't think comodo would be too good under Wine.. try this though : [http://sourceforge.net/projects/xfwall/](http://sourceforge.net/projects/xfwall/)

that xfwall is a little too much for my taste.

---

### Post by Old Pink on 2006-10-19
Stop with the "it was like this in windows..." "I want it like Windows..." 

[B]UBUNTU IS _NOT_ WINDOWS!

[/B]Personally, I have a firewall on the router I connect to the internet through, and therefore don't need one on Ubuntu. :)

---

### Post by Lord Illidan on 2006-10-19
> **Matt.H said:**
> Stop with the "it was like this in windows..." "I want it like Windows..." 

[B]UBUNTU IS _NOT_ WINDOWS!

[/B]Personally, I have a firewall on the router I connect to the internet through, and therefore don't need one on Ubuntu. :)

All he wants is a firewall, Matt.. be easy on the guy.

I don't know what you want, though. What is bad in firestarter?

---

### Post by PriceChild on 2006-10-19
The iptables built into the kernel IS linux's firewall, i can't see why you want anything else.

Firestarter is pretty simple to use... install it... turn it on... et voila! you have a decent firewall.

If you really wanted... you could hand configure the iptables conf scripts?

---

### Post by TheRingmaster on 2006-10-19
I never said that I wanted ubuntu to be windows. all I am saying is that there needs to be more choices in firewalls. why just iptables? that is what open-source is all about right?

---

### Post by Tomosaur on 2006-10-19
iptables is already very, very good at what it's supposed to do. I guess there's just no incentive for anyone to write an alternative, so must 'firewall' applications are essentially jus GUIs which interact with iptables.

---

### Post by Cyraxzz on 2006-10-19
Why? Firestarter is good enough. And there are other ones like [OSSEC-HIDS]("http://doc.gwos.org/index.php/Setup_OSSEC-HIDS")

---

### Post by Overcast32 on 2006-10-19
In my humble Opinion... 

Hardware Firewalls > All the rest. 

Just keep that 'remote admin' off, lol

---

### Post by Lord Illidan on 2006-10-19
I think Linux being Linux, the propensity is more towards distros being used as firewalls...such as Engarde Linux, and Bastille Linux, and so on.

---

### Post by Michael_aust on 2006-10-19
If you want simple, then there is nothing more simple then lokkit.

Its available in command line version of gui version.  There is absolutly no different, the questions and layout are exactly the same.

It asks you what level of security you want, high, medium or low.  Choose what you want.  I think it asks about two questions relating to networking.  Click apply and you are done.

None of this messing around like with guarddog and firestarter.  Ok it wont give you as good a set up as the previous two.  But it is a good enough configuration for most home users.  As far as I know Lokkit was developed by Redhat.

I personally prefer the Iptables in Linux as a firewall over any windows firewall.  Ok it is not as easy to set up as say norton of mcafee if you are doing advanced things.  But here is the big bonus, I dont have a process running in the background eating up 15% of my my cpu while it is idle.  Iptables is a kernel config so its not any extra overhead on your machine.  Thus freeing this saved cpu time etc for thins that you want to do.

---

### Post by Overcast32 on 2006-10-19
> **Lord Illidan said:**
> I think Linux being Linux, the propensity is more towards distros being used as firewalls...such as Engarde Linux, and Bastille Linux, and so on.


Ahhh, yeah - didn't consider that really. Of course, if it's sole purpose is a firewall, personally I think just a stripped down command line setup would work best. 

But also - how 'new' is Ubuntu? I just found out about it a couple weeks ago - I'm sure that soon enough, we'll see a buncha goodies for it. 

Still a good thread, if any coders were looking for a project I suppose.. Coding's a big time sink I've never really been able to devote time to. Silly ol' Video Games anyway!!

---

### Post by PriceChild on 2006-10-19
> **Overcast32 said:**
> Ahhh, yeah - didn't consider that really. Of course, if it's sole purpose is a firewall, personally I think just a stripped down command line setup would work best. 

But also - how 'new' is Ubuntu? I just found out about it a couple weeks ago - I'm sure that soon enough, we'll see a buncha goodies for it. 

Still a good thread, if any coders were looking for a project I suppose.. Coding's a big time sink I've never really been able to devote time to. Silly ol' Video Games anyway!!
First release was october 2004: [http://www.ubuntu.com/ubuntu/releases](http://www.ubuntu.com/ubuntu/releases)

I really don't see the need for a replacement for iptables.

---

### Post by skymt on 2006-10-19
There's no reason to have anything but iptables. It's simply the name for the packet filtering features in the Linux kernel, and the tools to control them. To make another system would be worthless duplication of effort, when we already have something that does the job very well. "Why don't we have more graphics systems? Why just Xorg?" Because that's all we need!

I'm pretty sure Windows has a similar (probably inferior) kernel interface that all the GUI firewalls over there interface with. It's just less visible, since ZoneAlarm doesn't advertise their product as a "front-end for Windows BlockPackets", or whatever it's called.

If you want more front-ends, there are plenty on the command line. Firestarter is the only major GUI one, because the "fool new users into a sense of security" field in Ubuntu is fairly small, unlike in Windows. If Symantec started marketing security tools for Linux, I'm sure the field would expand greatly. :rolleyes:

---

### Post by Charles Hand on 2006-10-19
It's been said before: iptables is complete and sufficient for any firewall application. I think Jpazindustries is really looking for a variety of front-ends. Maybe someone will write him a front-end that works the way he wants.

I would also encourage Jpazindustries to give the existing front-ends a fair try, if he hasn't already.

---

### Post by TheRingmaster on 2006-10-19
thanks for the extra information fellas, it was helpful. I love to learn about these sorts of things.

---

### Post by NoTiG on 2006-10-19
I see alot of windows users coming over to linux demanding firewalls and such. I think the widespread virus infection in windows has lead to widespread paranoia and a misunderstanding of what a firewall actually is.

On a base installation, ubuntu comes with all ports closed, which means you are not running any services. All a firewall does is moderate what traffic comes in , and what goes out. Since you are not running any services by default, traffic that is coming in is ignored since the ports are closed. As far as traffic going out, the only useful time to have a firewall then is if you have a trojan on your computer... but then your security is already comprised anyway and it doesn't matter. If you do open up a port (such as for uploading on a p2p network), then the proper security procedure would be to keep whatever program it is your running on that port up to date with security patches... not a firewall.

The only time you need a firewall is for special routing tables. Like you want to block certain ports on your network for whatever internal reasons.

---

### Post by maniacmusician on 2006-10-19
i dont really see the need for another firewall system, but I don't see anything wrong with this thread either. The OP just wanted to explore his options and was wondering why there was only one backend. the thread is fine.

I'll admit, I don't even have a firewall running. Well, my router is running one so I guess that counts. 

BTW, i have ports forwarded from my router...if ubuntu comes with all ports blocked, does that mean that the port forwarding is not working?

---

### Post by NoTiG on 2006-10-19
> **maniacmusician said:**
> i dont really see the need for another firewall system, but I don't see anything wrong with this thread either. The OP just wanted to explore his options and was wondering why there was only one backend. the thread is fine.

I'll admit, I don't even have a firewall running. Well, my router is running one so I guess that counts. 

BTW, i have ports forwarded from my router...if ubuntu comes with all ports blocked, does that mean that the port forwarding is not working?

The ports arent blocked, it's just that theres no services by default running on them.

I didn't mean to sound harsh or anything.

---

### Post by maniacmusician on 2006-10-19
> **NoTiG said:**
> The ports arent blocked, it's just that theres no services by default running on them.

I didn't mean to sound harsh or anything.
okay, thanks for clearing that up.

don't worry about it, it's the internet; hard to convey tone and whatnot. happens all the time

---

### Post by TheRingmaster on 2006-10-20
I am only talking about firewalls. not viruses.

---

### Post by slimdog360 on 2006-10-20
take a look on the guarddog website. There is a very simple start up guide which will block most everything but what you want to use.

handbook
[http://www.simonzone.com/software/guarddog/manual2/]("http://www.simonzone.com/software/guarddog/manual2/")

here for a basic setup
[http://www.simonzone.com/software/guarddog/manual2/using-guarddog.html#tutorial-basic]("http://www.simonzone.com/software/guarddog/manual2/using-guarddog.html#tutorial-basic")

---

### Post by ssam on 2006-10-20
there is also [IP filter]("http://en.wikipedia.org/wiki/IPFilter"). but i don't think it is very commonly used on linux.

i think pretty much everything can be done with iptables. sometimes people complain that you can't filter by application, but apparently that just give a false sense of security. if you let firefox connect to the web then a bad extension would not be blocked. If wget (a command line tool used in lots of scripts) is allowed to connect, then any program could use that for downloading or sending info to a remote site (with a HTTP POST request).

---

