---
title: "security risk with tor browser"
date: 2016-10-26
forum: Security
---

### Post by bijaydeyp on 2016-10-26
Hi fellows! 
I want to use tor browser on my ubuntu 14.04 lts but
is it advisable to use tor browser since it is not in official ubuntu repository?
I want to keep  my system clean from any security threat.could there be any risk? and what precausion should I take before installing that?

---

### Post by TheFu on 2016-10-26
TOR when used correctly can hide your location.
TOR when improperly used marks your connection as someone trying to hide and doesn't actually provide any location hiding.
TOR exit nodes see all the traffic. Is the exit node you are using trustworthy?  Many are run by different intelligency agencies around the world.
If you use the same browser with and without TOR, expect _*some*_ identifying data to be leaked.  Incognito mode isn't 100%. There have been bugs and there are likely hundreds of other bugs remaining.

Any code you load onto your machine should come from trusted sources.  That can be Canonical or any other trusted source ... that YOU trust.  We cannot say which sources YOU should trust since we all have different levels of trust. This applies to any PPA or .deb file or source code.

Many people using TOR are there to hide and believe doing illegal things isn't morally wrong.  
[http://www.techworm.net/2016/05/tor-vpn-users-labeled-criminals-hacked-spied-fbi-new-law.html](http://www.techworm.net/2016/05/tor-vpn-users-labeled-criminals-hacked-spied-fbi-new-law.html)
[http://thehackernews.com/2016/04/tor-unmask-malware.html](http://thehackernews.com/2016/04/tor-unmask-malware.html)
[http://www.theregister.co.uk/2016/08/10/linux_tor_users_open_corrupted_communications/](http://www.theregister.co.uk/2016/08/10/linux_tor_users_open_corrupted_communications/)
[http://www.securityweek.com/dns-data-can-help-attackers-deanonymize-tor-users](http://www.securityweek.com/dns-data-can-help-attackers-deanonymize-tor-users)
but there is hope: [http://www.makeuseof.com/tag/really-private-browsing-an-unofficial-users-guide-to-tor/](http://www.makeuseof.com/tag/really-private-browsing-an-unofficial-users-guide-to-tor/)

I don't use TOR on my daily desktop.  Running a VM just for TOR use is pretty easy these days and keeps things segmented.
Be careful out there and watch out for .onion sites. They often aren't just hobbyists, but organizations doing bad things.

---

### Post by bijaydeyp on 2016-11-02
Hi TheFu 
Thanks for the reply. 
 
You talked about Virtualisation and I also read your  comments on other threads similar to this issue. I decided to go for Firejail. But unlucky, It is not available in repo for Trusty(14.04) Kernel 4.2.0-35 generic.  
what should I do now? any suggestions, info, tweaks???

---

### Post by TheFu on 2016-11-02
Run 16.04?  Is this a trick question?  You don't have to use firejail - actually, firejail isn't a VM.  Install qemu-kvm, virt-manager and bridge-utils, if you want a VM host on Linux.

---

### Post by kevdog on 2016-11-02
I'd just dowload something like VirtualBox and install Ubuntu or whatever OS in that and run Tor.

---

