---
title: "Feature Request: Interactive firewall (like Fireflier, or Kerio)"
date: 2007-04-03
forum: Server Platforms
---

### Post by przemjaskier on 2007-04-03
Why there are no moves in adding such a functionality? I see some blueprints on creating static FW rules editors. But such static approach to packet filtering is not very agile and to primitive for a desktop machine. Look on functionality provided by Linux's Fireflier (a project that became dead recently) or Window's Kerio Personal Firewall. You can made deny/allow decisions in the runtime, based on app name etc., persisting some of the rules. 

Basically, you know what is happening with you Linux box...

P.S. I couldn't find a place to post Feature Request for (K)Ubuntu...

---

### Post by Jussi Kukkonen on 2007-04-03
packet filtering  maybe primitive, but at least they're fairly effective. Per-process filtering that's non-trivial to by-pass, on the other hand, is quite difficult to do... Maybe that's a reason it's missing? See e.g. [http://www.securityfocus.com/infocus/1839](http://www.securityfocus.com/infocus/1839) for details (the examples are for Windows, but the principle works on linux too).

---

### Post by huygens on 2007-04-03
A firewall like those on windows that warn the user each time an application tries to connect to the internet is not good either. I ended up with "do you want svchost.exe to connect to internet" which was meant for the dynamic IP request (DHCP), then another popup for the same process for some service I had not clue of, etc. In the end, I end up authorising most of the outgoing traffic, because I simply did not know.
And as I was smart enough to avoid viruses and worms, I did not worry to much for something that would try to reach out.
If you have a firewall that block unexpected incoming traffic, you have some security systems, rules (like updating regularly your system for correcting new vulnerabilities) and you are careful. Then, you do not need an interactive firewall.

So I do not think that this interactive firewall will last long, they will on the opposite decline/disappear. User do not want to be bothered with such info (just like the UAC of Vista). They want to be protected, and that's it. It is up to the security systems to find out what to do in each case.
And if your firewall is set-up correctly so that nothing should go in, then nothing unexpected will try to go out! And if in a business environment you want to limit some external services access, it is always possible to do it statically.

The only real risk would be for a server where an attacker manage to install a rootkit or something similar through a breach in one of the service advertised. But then, no one is sitting in front of a server to verify outgoing connection. SELinux, IDS, etc. are good solution for this type of problems.

Read this interesting article (and also comment number 6): [http://www.baekdal.com/articles/Usability/security-threats/](http://www.baekdal.com/articles/Usability/security-threats/)
(I'm not the author)

---

### Post by przemjaskier on 2007-04-04
Worms, troyans etc. is only the one aspect of the traffic that I would be glad to control. 

The other class of applications are those fully legal, that simply get online too often, sometimes compromising your privacy, or i.e. try to validate against online TDDs/Schema, when you simply don't want it. Other case are situations like with some eclipse/maven plugins, that get online and put a lot of poo in your local repositories without even single warning given.

When I want to PROTECT my network I create a static iptables firewall. Here I'm talking about INSPECTING/AUDITING what's happening to your linux box. I mean it as a power-user auditing and alarming tool, not a way to create firewalls. I simply cannot believe that you all trust that every single application in your box should have unaudited online access...

P.S. Where can I fill Feature Request for Ubuntu?

---

### Post by huygens on 2007-04-04
For feature request, you can use [launchpad]("http://launchpad.net") blue prints :-)

As for the auditing of a desktop computer... hmm I'm not sure of the usefulness for a desktop user. Nessus is not part of the standard Ubuntu installation ;-) not Snort!
For a power user? Hmm could be... But those tools for auditing are clearly necessary for servers or computers that act like servers or are connected almost full time to internet/intranet, etc.
As a power user, I wanted to have control of everything going on in my computer :twisted:. Now, I recognise that it was a waste of my time, and I simply want things to work. As a newer power user, I just want to work the most efficiently with my computer, anything that is here to disturb me (like "do you want to grant access to blabla") is an annoyance and a waste of my time. At least that is my new opinion :-)

Anyway, if an application does something you think is incorrect, you should report a bug. As a circumvent, you could write a firewall rule, but this is not the best way ;-)

---

