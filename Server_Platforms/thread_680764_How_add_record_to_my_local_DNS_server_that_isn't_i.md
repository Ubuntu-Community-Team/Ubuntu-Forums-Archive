---
title: "How add record to my local DNS server that isn't in my zone?"
date: 2008-01-28
forum: Server Platforms
---

### Post by frankabel on 2008-01-28
Hi all,

I don't know much about DNS, and have one ;)

My DNS servers names in a zone (i.e. cujae.edu.cu) to all local PC and it forwards all the request to names in others  zones  to an external DNS.

What I want is make that some domain name (archive.ubuntu.com) point to a local server. What can I do to accomplish that? How I avoid that my DNS forward just few request outside the internal zone to the external DNS server?

Salute
Frank Abel

---

### Post by rickyjones on 2008-01-28
On your DNS server just create a new domain zone for the domain that you wish to serve requests for. Add entries in this new zone.

For example, on my network at work. We have a domain "domain.local" which hosts internal names for our computers. We also have an external website, "domain.com", which I want local clients to get DNS for locally. So I add that zone to my dns server. Now, the domain "domain.com" is served locally AND externally by the rest of the internet.

I hope that it helps.

-Richard

---

### Post by frankabel on 2008-01-28
Thanks,

The problem is that I don't want serve all the .ubuntu.com zone, just the name archive.ubuntu.com because in case that I add a .ubuntu.com zone I must add too all the records in that zone and that will add lots of maintenance work for me.

The final goal of all this is that my local users don't change at all its configuration to use my local mirrors (archive.ubuntu.com, archive.canonical.com and packages.medibuntu.org) when they are in my network.

May be I'm wrong, just don't get this DNS thing clear.

Salute
Frank Abel

---

### Post by rickyjones on 2008-01-28
If I remember my DNS then it is all the way or none of the way, unfortunately.

I could also be wrong - might want to keep watching for a DNS veteran to answer.

-Richard

---

### Post by frankabel on 2008-01-30
Buzz!

Any DNS guru there:confused:

---

### Post by ubnuturero on 2008-01-30
Get the IP address for those 3 servers  and in your
external router, firewall or proxy  redirect the trafic from those IPS to your server

or   set  those 3 IP address on your server as virtual interfaces and then tell your router that those IPS are on the real ip of your server

---

### Post by ubnuturero on 2008-01-30
I Forgot 

WHAT ABOUT security updates ??
You need to update  that too

You can maybe  use   apt-proxy

With that  you can set you apt-proxy server with allthe updates that get downloaded but YOU need to set the config  in every client ..

---

### Post by frankabel on 2008-01-30
Thanks for your reply ubnuturero,

I really dislike any solution related to IPs, because repo IPs (archive.ubuntu.com have three right now) can change or worth, be sharing for other service that with such solution will be unaviable for my clients, beside I don't want carry out with such maintenance problem, I wish a clean solution (if exist ;))

I want mirror repo because more than 1000 machine will be using my local repo and don't want they waste time downloading a packages from any internet repo in case that the package  never haven't downloaded before (that  how I think that work apt-proxy). My current setup update the mirror in the night (our internet connection in the day get slow) so the client can updated computers again our local repo in the day.

About security repo, read this post pls [http://ubuntuforums.org/showthread.php?t=680182](http://ubuntuforums.org/showthread.php?t=680182)

Salute
Frank Abel

---

### Post by frankabel on 2008-01-30
Kind of outoreply ;)

Seen like this dnsmasq package can help here:

Dnsmasq will serve names from the /etc/hosts file on the firewall machine: If the names of local machines are there, then they can all be addressed without having to maintain /etc/hosts on each machine.

Anybody know if I can put on a Bind server a kind of hosts file? so each time it verify if an entry is there before forward the request?

Salute
Frank Abel

---

### Post by Yhetti on 2008-01-30
> **frankabel said:**
> Thanks,

The problem is that I don't want serve all the .ubuntu.com zone, just the name archive.ubuntu.com because in case that I add a .ubuntu.com zone I must add too all the records in that zone and that will add lots of maintenance work for me.

The final goal of all this is that my local users don't change at all its configuration to use my local mirrors (archive.ubuntu.com, archive.canonical.com and packages.medibuntu.org) when they are in my network.

May be I'm wrong, just don't get this DNS thing clear.

Salute
Frank Abel

You can create a zone that is *just* archive.ubuntu.com, or any subdomain thereof, via a  

zone "archive.ubuntu.com" { type master; file "db.archive.ubuntu.com"; } and then override as you see fit.  The likelihood of any of your people needing to get to archive.* is much less.

You will have problems with the mirror server trying to reach it, so you can do some fancy ACL stuff so that the fake version is only fed to clients who are supposed to get it.  Or you cna make life easy and just put the real IP in /etc/hosts on the mirroring machine.

---

### Post by koenn on 2008-01-31
You're abusing DNS to get a sollution for your repo problem, and I'm afraid workarounds like these will come back and bite you sooner or later.

What you probably should do is
- run your own repository under its own name in your domain
- let your DNS resolve that name, the way DNS is supposed to work
- point all the clients to your repo server in stead of to the default servers

you can actually specify a mirror server during setup, so new systems can be set up correctly from the start.
For existing hosts, you might be able to remotely copy (scp, rsync, ...) a custom sources.list, or (remotely;, eg with ssh) have them run a script that does a find-and-replace in their sources.list, or makes them download (wget ?) a sources.list from a web server, etc. - but that depends a bit on how you manage those (eg do you have admin priviliges on those hosts ?)

---

### Post by frankabel on 2008-01-31
Can you explain what you say "I'm afraid workarounds like these will come back and bite you sooner or later."?

I know that the solution that you describe is viable (that is what I'm using right now), but I think that for new and unexperienced users is better just select the country during installation (ant then resolve the country mirror and the original mirror locally) than enter the local mirror url, I just want make the most  straightway Ubuntu deployment, believe me that this little different can save lots of support time in a scenario of thousands of users that are afraid and not interesting on Linux

Salute and thanks for your reply.
Frank Abel

---

### Post by koenn on 2008-01-31
It's rather unusual to let users install their OS from scratch in a managed environment - I think you should look into automated installs that you can customize (eg with preseed files) so that your systems get a correct sources.list without ugly network hacks. 

> 
Can you explain what you say "I'm afraid workarounds like these will come back and bite you sooner or later."?
How about this : 
at some point in the future (monts/years from now), you have a project on your hands  ...  (could be anything: a software roll-out, something that requires rearranging your netork, ...). In the course of that project, you begin to encounter random bugs, occasional trouble, hard to replicate erroneous behaviour, ... There's no direct, clear indication that they're caused or influenced by your network hack - so it takes you days / weeks before you even think about those unusual modifications in your DNS (or worse : you're gone, and the guy who's in charge of the network by then has to figure it all out by himself). 
Finally, you find that that DNS trick plays a role in the problems you're facing, and you end up with 2 problems to solve : you have to solve the original problem that made you do the DNS hack in a way that doesn't interfere with your current project, and you have to troubleshoot the hosts that experience those random; occasional, hard to replicate bugs.

I know this all sounds vague and abstract, but that's mainly because I don't know your environment well enough to think of concrete examples. Its this sort of scenarios that make KISS (Keep It Simple, ..) such a popular concept in IT.

---

