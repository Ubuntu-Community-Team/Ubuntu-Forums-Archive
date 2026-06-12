---
title: "Ubuntu turning into windows?"
date: 2020-09-07
forum: Ubuntu, Linux and OS Chat
---

### Post by lisanels47 on 2020-09-07
I've been running Linux for many years.  The changes I've seen lately make me wonder if the future of Linux stable.

One change I've see is the addition of dnsmasq.  Yes, it can speed up some of the network activity, but it also caused many problems.  Folks have disabled it often.  I like it as an option, but not as part of the normal install.

Another change is snap.  Yet another app manager that is incomplete.  Several things I've tried to install using snap failed, but apt worked fine.  Some apps claim that only snap installs will be available in the future.

Lastly, I just counted the running processes on my system:  lisa@lisa-Legion-Y545-PG0:~$ ps -ef | wc -l   398  Wow... 

As computers have more resources, people tend to not care anymore about inefficient programs... 

Don't get me wrong, I love Linux, but it's advantages over windows is creeping down.

Just wanted to vent a little... No need to scream at me....

---

### Post by SeijiSensei on 2020-09-07
Actually modern versions of Ubuntu have scrapped dnsmasq for systemd-resolved.  It works fine for most people, but if you have issues, you can edit /etc/systemd/resolved.conf and specify things like a DNS server and "Fallback" servers.

I don't use snap or flatpak packages either. So far I haven't suffered from that choice.

A lot of those processes are tiny, and many are likely in swap. I don't know how many processes a running Windows machine has, but given it traditionally had a much less modular architecture than Linux, I'd bet Windows has fewer.  Even my servers, which have no GUIs and run just a few daemons like Apache and sendmail, have about 200 processes.

---

### Post by grahammechanical on 2020-09-07
Which came first, the more powerful hardware or the next version of Microsoft Windows that needed the more powerful hardware? Something similar happened with computer games. Just as gamers were thinking that they finally could buy hardware that allowed them to play a game to its full capacity a new version was released that required even more powerful hardware.

Enough is never sufficient and people rarely refuse a salary increase because they have already acquired everything they need.

Regards

---

### Post by exploder on 2020-09-07
I used Windows 10 for a while, it drove me crazy! Updates that took hours to download, half the time they never would install, duplication of features, what a mess! Ubuntu just works as do many other distros. Everyone has their own experience and opinion on snaps. You aren't forced to use them though and they will get better over time. As far as resource usage goes, why have say 8 GB or RAM installed if you never use it? I prefer lighter resource use but I have Kubuntu running on my son's 16 year old HP desktop and he is able to play some fairly high end games on Steam.

Windows has planned obsolescence built in too. My son's AMD graphics were no longer supported in Windows but work perfectly fine with Kubuntu 20.04. For me there is no comparison, Linux does an all around better job. I like Ubuntu 20.04 on my new laptop and on my personal desktop. I do not see any breakage in Ubuntu like I saw with Microsoft's recent feature update! In my opinion Ubuntu 20.04 far surpasses Windows 10 where it counts! Ubuntu is solid, reliable and looks modern with the new theme.

---

### Post by mastablasta on 2020-09-08
i think snaps can work well in some instances. especially those where user is not tied to the OS. it would be good if they made them more like portable apps though. so user controls app updates and apps work inside specified folder. but you can also save files outside of that folder.

---

