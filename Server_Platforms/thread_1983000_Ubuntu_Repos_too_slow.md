---
title: "Ubuntu Repos too slow"
date: 2012-05-19
forum: Server Platforms
---

### Post by donniezazen on 2012-05-19
Hi,

Yesterday, I did clean install of Ubuntu Server. Ubuntu repository update takes over 15 minutes. Some package download took an hour. Archive repository is specially very slow. I was wondering if it's a temporary problem or how can i get fastest and most up to date repository on Ubuntu Server.

Thanks.

---

### Post by oldfred on 2012-05-19
I use desktop but change Download server using synaptic, download from, other, and select best server. That changes from us to one that is closer. It depends on ping values, so it is not always the fastest. 

You could use liveCD to find best server and then in your server install edit sources.list. Not sure if there is another way.

[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by donniezazen on 2012-05-19
> **oldfred said:**
> I use desktop but change Download server using synaptic, download from, other, and select best server. That changes from us to one that is closer. It depends on ping values, so it is not always the fastest. 

You could use liveCD to find best server and then in your server install edit sources.list. Not sure if there is another way.

[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Is their a direct command line way to update download server? It's a headless server without monitor and CD drive. I will have to move it over to my TV and us USB to update download server. I would like to do that as a last resort.

I was wondering if Canonical severs are under maintenance because i have always used main servers without any problem which are most reliable.

---

### Post by CharlesA on 2012-05-19
sudo sed -i 's/find/replace/g' /etc/apt/sources.list works wonders. ;-)

---

### Post by mode7 on 2012-05-20
I've had the same issue (Using Precise desktop too) for the last couple of days.
It takes about an hour and a half to download the package lists.
I also tried it on another computer when I visited some family, so I know it's not just me.
Since I need to install Xubuntu on here, I was a bit worried that I would be unable to update it or the like.

Anyways, I changed the server using the sources config gui, but I hope the main server become usable again.

@CharlesA, what does that do specifically? Have not used sed myself.

---

### Post by MG&amp;TL on 2012-05-20
> **mode7 said:**
> 
@CharlesA, what does that do specifically? Have not used sed myself.

Sed is a stream editor. It can do all sorts of wonderful things, but the 's' operator finds the first search term ("find"), then replaces it with the second term. ("replace").

I think CharlesA meant that it's easy to upgrade ubuntu version via this method. For instance, replacing oneiric with precise, you could do this:

```
sudo sed -i 's/oneiric/precise/g' /etc/apt/sources.list
```

---

### Post by mode7 on 2012-05-20
Thanks, MG&TL, that makes sense. For some reason I thought the 'find'/'replace' were tokens of some kind, making the man page confusing for me ;)

FWIW, the forums are loading *extremely* slowly as well. Other non-Ubuntu web pages seem to be loading just fine. This is quite annoying. I live in the Pacific Northwest of the US.
Hopefully the speeds go up in the near future. Changing the server helped quite a bit, but it looks like my Gimp 2.8 packages are coming from a Canonical server (Launchpad, I suppose), and going at 2-5 kb/s.

---

### Post by LHammonds on 2012-05-20
I have also noticed that doing aptitude update / aptitude safe-upgrade takes a LONG time to complete in the last 48 hours.

This is the 1st time I've seen it this slow so I assume there are some technical difficulties at the moment.

It just happened to coincide with problems from my ISP and I thought my data line was clogged.  lol...bad timing.

LHammonds

---

### Post by CharlesA on 2012-05-20
> **MG&TL said:**
> Sed is a stream editor. It can do all sorts of wonderful things, but the 's' operator finds the first search term ("find"), then replaces it with the second term. ("replace").

I think CharlesA meant that it's easy to upgrade ubuntu version via this method. For instance, replacing oneiric with precise, you could do this:

```
sudo sed -i 's/oneiric/precise/g' /etc/apt/sources.list
```

Nah, the best way to upgrade is to use update manager and/or do-release-upgrade

I've used sed to change which server you pull updates from by changing the URL.

---

### Post by MG&amp;TL on 2012-05-20
> **CharlesA said:**
> Nah, the best way to upgrade is to use update manager and/or do-release-upgrade

I've used sed to change which server you pull updates from by changing the URL.

...oops, always done it like that. :oops: The only use I can think of for that now is for upgrading to development releases.

---

### Post by dwighteb on 2012-05-20
> **mode7 said:**
> FWIW, the forums are loading *extremely* slowly as well. Other non-Ubuntu web pages seem to be loading just fine. This is quite annoying. I live in the Pacific Northwest of the US.

I'm in the far South East in the US, Comcast residential service as my ISP, and I'm getting extremely slow download speeds from all the Canonical sites that I checked out (Ubuntu forums, launchpad, etc) and main ubuntu repositories - normally, I'd have transfer speeds of 500K - 2M/s, however since 10AM (EST) yesterday, I've had speeds in the 5 - 20K/s.  My speeds to all other sites are normal.

Changing the repo's temporarily might be an option for most use cases, however I wanted to research Ubuntu Orchestra along side of MaaS and JuJu, and I wanted to see a working installation in flight with as few of my own modifications as possible.  (These will use cobbler and squid3, and yes, I could point one of these to an alternate repo, however I'd still have the download issue when it came time for Orchestra to download the mini build ISO's).

In any case - it'd be nice to know if it's just a few folks or many having this issue, and if maybe we're all using the same ISP.  Maybe my IP is being throttled from Canonical's perspective for being "abusive"?  Though, I always use an apt-cacher-ng and squid3 to cache their repo's (yes, I know I only _need_ one of those, but some use cases makes having both helpful), so I don't think I've been "unfairly" hitting their servers.  I'm well below Comcast's 250GB (or now 300GB?) cap, and I'd imagine if they were throttling me, all my traffic would suffer, not just the traffic to all the Canonical sites.

Edited to add:  No longer a problem.  Not a few hours after posting this, the issue has apparently resolved itself.

---

### Post by LHammonds on 2012-05-20
Yes, the upgrades are going much faster again. :)

...which makes me wonder if I need to be running some kind of mirror site at my location to avoid such slowdowns when cranking out servers.  Might have to look into that later.

---

### Post by CharlesA on 2012-05-20
> **LHammonds said:**
> Yes, the upgrades are going much faster again. :)

...which makes me wonder if I need to be running some kind of mirror site at my location to avoid such slowdowns when cranking out servers.  Might have to look into that later.
I doubt you'd need a mirror - some of the servers in London were having issues.

---

### Post by LHammonds on 2012-05-20
> **CharlesA said:**
> I doubt you'd need a mirror - some of the servers in London were having issues.
Well, for Windows servers, we have the ability to setup our own WindowsUpdate service which will pull patches from Microsoft as they become available...then all Windows servers pull from the internal server.  That allows us to override any particular updates (like a new version of IE coming through as a critical patch...don't even get me going on that soapbox) as well as only soaking up our Internet bandwidth by only downloading the patches once.

Seems like something I should investigate.  I already have 7 Ubuntu servers and I'm just getting started! :)

---

### Post by CharlesA on 2012-05-20
WSUS is handy. You can probably do the same thing via apt-cacher-ng:
[https://help.ubuntu.com/community/Apt-Cacher-Server](https://help.ubuntu.com/community/Apt-Cacher-Server)

---

### Post by LHammonds on 2012-05-20
> **CharlesA said:**
> WSUS is handy. You can probably do the same thing via apt-cacher-ng:
[https://help.ubuntu.com/community/Apt-Cacher-Server](https://help.ubuntu.com/community/Apt-Cacher-Server)
Sweet!  You saved me a bit of research!  Thanks.

---

### Post by mode7 on 2012-05-20
Yes, the server issues appear to be resolved.. have usable speeds again from the "Main server".

(@dwightweb, I have Comcast as well, also know I can't be at their limit)

---

### Post by CharlesA on 2012-05-20
> **LHammonds said:**
> Sweet!  You saved me a bit of research!  Thanks.
Google is my friend. ;-)

---

### Post by LHammonds on 2012-05-20
> **CharlesA said:**
> Google is my friend. ;-)
He's a good friend of mine too...but I'm a bit wrapped up in the creation of the MySQL server thread.  I keep getting distracted....don't know how that happens.

PS - I'm in Texas (in relation to the slow server issue)

---

### Post by dwighteb on 2012-05-20
A couple of others to consider - apt-cacher-ng:
[http://www.unix-ag.uni-kl.de/~bloch/acng/](http://www.unix-ag.uni-kl.de/~bloch/acng/)

This is a C rewrite of apt-cacher (which was in perl I think?).  I don't think it's much faster, but last time I checked, it was more recently updated.

Another one to consider - squid-deb-proxy:
[http://www.linuxjournal.com/content/presenting-squid-deb-proxy-speed-your-update-downloads](http://www.linuxjournal.com/content/presenting-squid-deb-proxy-speed-your-update-downloads)

---

### Post by james_xxx on 2012-05-27
I have not seen any improvement in this. I am trying to download KDE SC 4.8.3 from the Kubuntu PPA, and averaging 15kB/s down. This is on a GB network.

Apt is estimating the download to take nearly 1.5 hours.

It has been this way here for a few weeks.

---

### Post by Ateo on 2012-07-31
So I nailed the issue... I think...

Repos were super SUPER slow for me. My ISP is Charter and I live in Los Angeles so my area is very well connected. Speed tests are accurate as my network speeds are fast all throughout except with Ubuntu repos..

Anyways, what I did was disable ipv6 and my speeds for updating package list went back to normal....

I created a new file called **/etc/sysctl.d/60-disable-ipv6.conf** and added the following to it:
```
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
```
Afterwards, I restarted networking:
```
/etc/init.d/networking restart
```

Then I ran apt-get update and it was lightening fast.

Hope this helps!

---

### Post by LHammonds on 2012-07-31
> **Ateo said:**
> So I nailed the issue... I think...

That might have fixed your issue but it made no difference on my servers.

The update process takes 23 seconds (fetches 20.2 MB).  After the change and restart of the networking service, it still took 23 seconds.

I have a static IPv4 address so I'm not sure if it was trying to do anything with IPv6 anyway.

LHammonds

---

### Post by CharlesA on 2012-07-31
> **LHammonds said:**
> That might have fixed your issue but it made no difference on my servers.

The update process takes 23 seconds (fetches 20.2 MB).  After the change and restart of the networking service, it still took 23 seconds.

I have a static IPv4 address so I'm not sure if it was trying to do anything with IPv6 anyway.

LHammonds
That is how it is for me too. Static IP4 address on the server, but I have a couple VMs that using DHCP with no problems.

---

