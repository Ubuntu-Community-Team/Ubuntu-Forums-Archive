---
title: "what is the point of having the source code repos enabled by default?"
date: 2010-11-09
forum: The Cafe
---

### Post by user1397 on 2010-11-09
you know, those lines in your /etc/apt/sources.list file that begin with deb-src

how many people actually download source code through the official ubuntu repositories?

[this]("http://ubuntuforums.org/showpost.php?p=10701925&postcount=15") post sums up my views on the subject

the source repos might be useful in certain cases, but for 99% of users it is pointless to be enabled by default. they slow down apt-get updates and put extra pressure on bandwith on the ubuntu servers because most people don't disable them. they can be easily turned on in software sources anyway if you need them for some reason.

click [here]("https://bugs.launchpad.net/ubuntu/+source/apt-setup/+bug/74747") to add yourself to the bug report on this subject

---

### Post by Oxwivi on 2010-11-09
Not me. Why bother downloading the source code, when they can be directly installed?

---

### Post by marshmallow1304 on 2010-11-09
I always disabled them.  If I'm going to compile from distro-supplied sources, I'll just use a source distro, which I do now.

I suppose they could be useful if you wanted to add a patch but still have any Ubuntu patches already applied.

---

### Post by ssj6akshat on 2010-11-09
source repositories are useful for fixing bugs

---

### Post by m4tic on 2010-11-09
I hate the name repositories, whenever i get someone started on Ubuntu, they get lost on that word. i can't even say it without biting my tongue. It would be better just named something simpler or does everything on Linux have to have a geeky name?

---

### Post by matthew.ball on 2010-11-09
Are you serious? You don't know what a [repository]("http://en.wikipedia.org/wiki/Repository") is?

[quote=Define: Repository]A facility where things can be deposited for storage or safekeeping.[/quote]
Hardly a geeky name.

---

### Post by Paqman on 2010-11-09
> **ssj6akshat said:**
> source repositories are useful for fixing bugs

Sure, but why enable them by default? On slow connections, updating the sources can already be quite slow.

---

### Post by koenn on 2010-11-09
> **Paqman said:**
> Sure, but why enable them by default? 
because all (or most) of  the licenses that this software is distributed under, require that the software is distributed with the source code it was build from. Having the src-deb repos enabled is a convenient way to meet that requirement

---

### Post by oldos2er on 2010-11-09
> **Paqman said:**
> Sure, but why enable them by default? On slow connections, updating the sources can already be quite slow.

If you install Nvidia proprietary drivers, you need the source repos enabled so the new kernel can be built.

---

### Post by MarcusW on 2010-11-09
Why shouldn't they be enabled by default? I think it's kinda in the spirit of open source to make it as easy as possible to get the source code of the programs you use. It's not like it's in the way.

---

### Post by FuturePilot on 2010-11-09
> **oldos2er said:**
> If you install Nvidia proprietary drivers, you need the source repos enabled so the new kernel can be built.

No you don't.

---

### Post by user1397 on 2010-11-09
> **MarcusW said:**
> Why shouldn't they be enabled by default? I think it's kinda in the spirit of open source to make it as easy as possible to get the source code of the programs you use. It's not like it's in the way.well technically it can slow you down a little bit when you perform a 'sudo apt-get update', especially if the source repos themselves timeout for a bit, which happens from time to time (as with any other repo).

---

### Post by user1397 on 2011-04-21
i don't think this thread is old enough to the point where i am technically necro'ing it, but i think this issue is yet unresolved and i'd like more input from the cafe on this topic

---

### Post by PriceChild on 2011-04-21
> **ubuntuman001 said:**
> i don't think this thread is old enough to the point where i am technically necro'ing it, but i think this issue is yet unresolved and i'd like more input from the cafe on this topic
Have you tried heading towards the developers on irc/MLs or launchpad?

There is 'wasted' time waiting for the 'apt-get update' to complete with deb-src lines and you're right in that it does make sense to have them disabled by default for the average user. If they aren't then its probably a good idea to do something about it.

---

### Post by gnomeuser on 2011-04-21
> **MarcusW said:**
> Why shouldn't they be enabled by default? I think it's kinda in the spirit of open source to make it as easy as possible to get the source code of the programs you use. It's not like it's in the way.

However:

1) By default nothing needs the source repos
2) It adds the amount of data a user is required to fetch to even check for updates
3) As a result of 2, it increases the amount of data needing to be pushed adding pressure to our servers and kind mirrors without a real need.

We can save time, bandwidth and thus money by disabling the source repos.. off with the head!

I don't think it is in the spirit of Open Source to deliberately wasting resources for the sake of it.

---

### Post by user1397 on 2011-04-21
should we file a bug report on launchpad?

---

### Post by gnomeuser on 2011-04-21
> **ubuntuman001 said:**
> should we file a bug report on launchpad?

probably

---

### Post by user1397 on 2011-04-21
bug report already filed [here]("https://bugs.launchpad.net/ubuntu/+source/apt-setup/+bug/74747")

---

### Post by Grenage on 2011-04-21
> **ubuntuman001 said:**
> bug report already filed [here]("https://bugs.launchpad.net/ubuntu/+source/apt-setup/+bug/74747")

I added myself; while it's handy to have and shouldn't be removed, I can see no reason why it need be enabled by default.

---

### Post by user1397 on 2011-04-21
> **Grenage said:**
> I added myself; while it's handy to have and shouldn't be removed, I can see no reason why it need be enabled by default.

ditto

---

### Post by juancarlospaco on 2011-04-22
Mmmm, to say something related, i dont understand why we need a TCP protocol to transfer the .DEB's
Since the .DEB's have their own CRC to check its sanity, it can be transported via an UDP protocol,
like TFTP which is faster and uses less bandwith than HTTP or FTP or any other TCP transport.

I think is possible im wrong, but i want to know the technical reason.

---

### Post by jerenept on 2011-04-22
> **juancarlospaco said:**
> Mmmm, to say something related, i dont understand why we need a TCP protocol to transfer the .DEB's
Since the .DEB's have their own CRC to check its sanity, it can be transported via an UDP protocol,
like TFTP which is faster and uses less bandwith than HTTP or FTP or any other TCP transport.

I think is possible im wrong, but i want to know the technical reason.

Firewalls might block UDP traffic (to get in the way of torrenters probably). Anyway, what server do you know of that is as efficient, reliable and secure as nginx, Apache, lighttpd, or VSFTP that can serve files over a UDP connection? No seriously, I'd like to take it for a spin.

<ontopic> What about using dpkg-diff to reduce download times and amounts?

---

### Post by juancarlospaco on 2011-04-22
> **jerenept said:**
> Firewalls might block UDP traffic (to get in the way of torrenters probably). Anyway, what server do you know of that is as efficient, reliable and secure as nginx, Apache, lighttpd, or VSFTP that can serve files over a UDP connection? No seriously, I'd like to take it for a spin.
<ontopic> What about using dpkg-diff to reduce download times and amounts?

I talking seriously..., 
you mentioned HTTP/HTTPS servers, those protocols use TCP, you are confused.

Yes, a lot of people say that Firewalls might block a lot of things, included FTP, 
which is a lot faster than HTTP, thats why is not used by default, 
but the true is that in a lot of places Firewalls dont block such things, 
so can be a great **optional** enhacement, faster with less bandwith, sounds good.

Nowadays Firewalls are configured differently, with Layer 7 plugins, and Shaping,
almost any modern application can use Random ports, so no more block this port and ready.

TFTP dont have any Authentication or Cryptography, 
but we dont need it anyways if we are moving open source debs;
and if you think we need it, well HTTPS is hackable nowadays like man-in-the-middle too.

Im not pointing any server particularly but the protocol is pretty simple.

It is a different thing than Deltas, or dpkg-diffs

---

### Post by wizard10000 on 2011-04-22
I think this is a great discussion.

Someone please correct me if I'm wrong but I think GPL says the source has to be available, not that it has to be provided by default.  

Coming from a support background, I imagine thousands of users trash their machines every year trying to install from source without having a reasonably firm grasp or the process - or a good backout plan if the process fails.  Back in the day when you pretty much *had to* roll your own kernel if you wanted all your hardware supported I broke quite a few machines  :)

Also agree it'd decrease server load and client wait time if the source repos were disabled by default.

---

