---
title: "Ubuntu Server 23.10 no GUI and PiHole"
date: 2024-01-07
forum: Ubuntu, Linux and OS Chat
---

### Post by kein90 on 2024-01-07
Is PiHole worth while? I currently use brave and other ad blockers, and trying to rearrange my VPN and configure PiHole sounds like something that's gonna eat some time. Once set up is it hard to maintain? Does it require me to update it's blocking list often?

Thanks!

---

### Post by TheFu on 2024-01-07
> **kein90 said:**
> Is PiHole worth while? I currently use brave and other ad blockers, and trying to rearrange my VPN and configure PiHole sounds like something that's gonna eat some time. Once set up is it hard to maintain? Does it require me to update it's blocking list often?

Thanks!

First, if you want the longest time between required maintenance, never, run a server that isn't using an LTS release.  23.10 support ends in June, so you should install 22.04 or plan to wipe and start over in June, a few months after 24.04 is released.  If you aren't 100% certain what an LTS is, look that up, since it matters for desktops and servers.  I don't use non-LTS releases.  They aren't worth my effort due to the very short support period.  Heck, most Ubuntu Desktop LTS flavors only have 3 yrs of support, so basically, most people migrate to a new release (1 upgrade + 1 fresh install) every 2 yrs.  Not for me.  I'm running 20.04-based servers still - actually didn't move of 18.04 until a few months before that standard support ended.  That's enough about LTS vs non-LTS.

I've been using piholes here for a while. I run them inside an LXD managed container. Have 2 of them, specifically to ensure when one if off, maintenance reboots happen about every 3 weeks, so my other systems always have local DNS available.  For me, they are mostly set and forget, unless you really want to block ads from streaming sites. Then it becomes more of a challenge.  I get updated block lists from public sources as part of my weekly patches. Wrote a few scripts to mux those together for one of the lists that wasn't specific to the pihole needs.  

In theory, if you have a local DNS, then you don't need caching DNS on any of your Linux systems.  Sometimes Ubuntu running systemd-resolved gets confused and breaks, so you'll need to understand more about that as well.  I got to the point that I was tired of systemd-resolved breaking and just started purging it and manually setting up the DNS like we did for 20 yrs in the /etc/resolv.conf.  That change really has made life easier.

Every 2 yrs or so, the pihole upgrade/patch process breaks something. It is a really bad day.  Some of those are self-inflicted.  For example, I don't allow any IPv6 traffic on my LAN (security reasons), but the PIhole software supports it.  So, about a year ago, there was a pihole update that assumed IPv6 support existed. Since it didn't on my system, it broke, badly.  I had no DNS and all my systems knew it.  It was ugly.  Setup 1 box to have outside DNS without any blocking do I could research the issue.  Thankfully, because I patch weekly and the issue was introduced earlier in the week, a fix had already been posted, but I had to switch to a specific git branch to get that fix for a few weeks.  Then it broke again and I had to switch to the master branch to get it working again.

Like all software, some level of maintenance is needed. For block lists, you can do as much or as little as you like. Scammers are constantly creating new domains, so don't expect to always have perfect prevention if you don't update, but that it up to you.  

A pihole has a webapp-GUI. I don't use that for patching or updating.  I ssh into the pihole and run a few commands. I've scripted it as part of my weekly patching script used by all systems.  The normal, 
```
sudo apt-get update
sudo apt-get upgrade
If on the pihole,      ssh pihole1 "/home/ubuntu/bin/to-upgrade-pi-hole-sw "
```


$ more /home/ubuntu/bin/to-upgrade-pi-hole-sw
```

# Update pihole software
echo "INFO: Update pihole software"
pihole -up

# Update tracking domain lists
echo "INFO: Update tracking domains "
~/bin/update-trackers

echo "INFO: Update pihole gravity block lists"
# Update gravity block lists
pihole -g
```

Pretty simple. The *update-trackers* script is custom for my needs after pulling some lists from a few different places and massaging those lists.

---

### Post by kein90 on 2024-01-07
Thank you so much for the input - both on the LTS matter and on the Pihole. I'm a mostly Windows user and in my ignorance, I assumed that the latest version was the best to have:o. For now I think I'll keep my current ad blocking setup.


One other aspect. Since I'm on the 23.10 server version due to stop receiving support in June, could I not simply wait for the LTS edtion somewhere in April this year (24.04) and upgrade to that version without losing all my data and setup in the process?

---

### Post by TheFu on 2024-01-07
> **kein90 said:**
> Thank you so much for the input - both on the LTS matter and on the Pihole. I'm a mostly Windows user and in my ignorance, I assumed that the latest version was the best to have:o. For now I think I'll keep my current ad blocking setup.

[https://blog.jdpfu.com/2013/07/19/why-ubuntu-users-should-run-an-lts-release](https://blog.jdpfu.com/2013/07/19/why-ubuntu-users-should-run-an-lts-release)  Why Ubuntu Users should run an LTS is more extensive answer.
Just be aware that most Ubuntu LTS desktop flavors only get 3 yrs of support.  There are actually some subtle things that lose support faster, regardless of flavor or release.

Each Linux distro has a little bit different support plan and since Ubuntu flavors are wide ranging, each has slightly different support.  In general, assuming 3 yrs for LTS is safe except the main "Server" and "Gnome" desktops, which get 5 yrs for the LTS releases.  I mostly use Ubuntu Server LTS, which makes things easier.

---

### Post by #&amp;thj^% on 2024-01-07
@ TheFu just a kind note from your link.
```
ubuntu-support-status &#8212;show-unsupported|more 

```
Has been replaced with:
```
pro security-status

```
Worth a mention. :)

---

### Post by TheFu on 2024-01-07
Things change from 2013.  I don't hide the date my article was initially written, so it should be expected that some things have changed.
The different commands for checking package support seem to constantly change recently.  Even **ubuntu-security-status** is gone in 22.04+.

---

### Post by #&amp;thj^% on 2024-01-07
> **TheFu said:**
>   Even **ubuntu-security-status** is gone in 22.04+.
Almost Gone but yes things change, I know how you like correct wording is all. 
On Noble
```
ubuntu-security-status
This command has been replaced with 'pro security-status'.
2681 packages installed:
     1848 packages from Ubuntu Main/Restricted repository
     804 packages from Ubuntu Universe/Multiverse repository
     26 packages from third parties
     3 packages no longer available for download

To get more information about the packages, run
    pro security-status --help
for a list of available options.

This machine is receiving security patching for Ubuntu Main/Restricted
repository until 2029.
This machine is NOT attached to an Ubuntu Pro subscription.

Ubuntu Pro with 'esm-infra' enabled provides security updates for
Main/Restricted packages until 2034.

Ubuntu Pro with 'esm-apps' enabled provides security updates for
Universe/Multiverse packages until 2034.

Try Ubuntu Pro with a free personal subscription on up to 5 machines.
Learn more at https://ubuntu.com/pro

```
It dose give the user the correction "This command has been replaced with 'pro security-status'."
Just thought you might want to know about it is all. If not just disregard

---

