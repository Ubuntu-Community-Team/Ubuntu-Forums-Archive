---
title: "peculiar security policy"
date: 2008-11-09
forum: Security
---

### Post by thehighhat on 2008-11-09
There are a few things that I do not quite understand about Ubuntu/Debian security approach.  Please post your thoughts on the following....

1.  Many of the security tools, even recommended tools like FireStarter, are not part of the "official" repos.  They appear in community repos.  This means they do not get the same rigorous security updates as those pkgs in security repos.  

Does this not lead to a relatively false sense of security since people are relying upon regular system updates to keep them safe?


2.  Pet peeve...  the flash-nonfree, although in multiverse, is certainly not getting regular updates.  It is well understood that flash is widely deployed on the www.  There have been some serious security issues lately with flash.  

I think a more agressive security policy for pkgs that will likely be installed should be employed.  Of course, one could use backports.  But backports seems kind of out place, especially for LTS releases.


3.  Selinux & Apparmor.  Very odd.  Maybet this is easy to address... but I think it would be a real positive game changer, if "certified" security policies were issued for all network facing applications.  Even better would be a security repo updated set of policies that protect all system pkgs.

It is unsettling to see a pkg like selinux not part of the official distro.  Now I understand the whole community-based model of OSS development.  But since pkgs are not required to be update if not in security repo, this leaves a major gap.


Please share your thoughts.

---

### Post by randy78 on 2008-11-09
Firestarter is very outdated and has not been maintained in quite some time... The preferred firewall app is UFW and its GUI GUFW (ps, if you're behind a router that has a firewall enabled, you really don't need any of these packages)

You are correct, software in the community repository is not officially supported by Canonical and therefore they will not receive the same security updates as packages in the official repo, unless a community member provides the update.

Since Adobe made a .deb file for the flash-player, you are free to visit their site and download it yourself. The repos are sometimes slow to get the newest packages, but again, you are free to install the latest packages yourself.

As far as I know, SELinux has been included in the Linux kernel since 2.6...

---

### Post by thehighhat on 2008-11-09
[http://www.tgdaily.com/content/view/40098/108/](http://www.tgdaily.com/content/view/40098/108/)

yes, i agree that an option is to use the vendor pkgs directly.

i guess, i am thinking about how easy it is for a user to turn on automatic updates and believe everything is going to be maintained.

but clearly, most of the thousands of pkgs are not part of the security repos.  this is not obvious to a typical user.  

btw, i am sure it was already address... but the security repo is not enabled by default on 8.04 disk amd64... mute point now that 8.04.1 is out.. but yikes.

do ubuntu developers read the forums?

(yes, i know launchpad is monitored)

---

### Post by cariboo on 2008-11-10
The only place I've seen any devs is in XXXXXX Testing and Discussion, where XXXXXX is the next version of Ubuntu, currently it is Jaunty Jackalope.
Once in a while I see them in the Community Cafe.

Jim

---

### Post by ciscosurfer on 2008-11-10
> **thehighhat said:**
> ...
2.  Pet peeve...  the flash-nonfree, although in multiverse, is certainly not getting regular updates.  It is well understood that flash is widely deployed on the www.  There have been some serious security issues lately with flash.  
...I'm running with the Ibex and my flashplugin-nonfree (which is downloaded from Adobe and auto-updated on my box) is at version 10.0.12.36ubuntu1 and the latest version for release on Adobe's site is also version 10...am I missing something?  The only distro suffering a slight setback at the moment looks to be Solaris @ v9.0.151.0

---

### Post by hyper_ch on 2008-11-10
> **thehighhat said:**
> 1.  Many of the security tools, even recommended tools like FireStarter, are not part of the "official" repos.
Firestarter is not a "security" tool. It's just a frontend for configurating the underlaying iptables - or rather for messing up iptables as it does change all rules when yuo download it. But you are free to name other "security tools" that are not in the main repos.  

> **thehighhat said:**
> 2.  Pet peeve...  the flash-nonfree, although in multiverse, is certainly not getting regular updates.  It is well understood that flash is widely deployed on the www.  There have been some serious security issues lately with flash.
You don't get versioning updates during a release. Only bugfixes and security fixes.

> **thehighhat said:**
> 3.  Selinux & Apparmor.  Very odd.  Maybet this is easy to address... but I think it would be a real positive game changer, if "certified" security policies were issued for all network facing applications.  Even better would be a security repo updated set of policies that protect all system pkgs.
Isn't Apparmor installed by default? And do not selinux and apparmor work together?

---

### Post by thehighhat on 2008-11-10
> **ciscosurfer said:**
> I'm running with the Ibex and my flashplugin-nonfree (which is downloaded from Adobe and auto-updated on my box) is at version 10.0.12.36ubuntu1 and the latest version for release on Adobe's site is also version 10...am I missing something?  The only distro suffering a slight setback at the moment looks to be Solaris @ v9.0.151.0

Hardy is LTS.  The flash-nonfree is in multiverse. It has version 9.0.124.  See [http://packages.ubuntu.com/hardy/flashplugin-nonfree](http://packages.ubuntu.com/hardy/flashplugin-nonfree) 

This problem is compounded by the version number (Adobe has officially recommended a move to 10 to avoid attacks, even 0-day exploits), and by its proprietary code (developers cannot maintain it directly.)

---

### Post by thehighhat on 2008-11-10
> **hyper_ch said:**
> Firestarter is not a "security" tool. It's just a frontend for configurating the underlaying iptables - or rather for messing up iptables as it does change all rules when yuo download it. But you are free to name other "security tools" that are not in the main repos.  


You don't get versioning updates during a release. Only bugfixes and security fixes.


Isn't Apparmor installed by default? And do not selinux and apparmor work together?


Please do not misunderstand.  I am an ardent supporter of linux, even Ubuntu.  It has been my primary OS for a decade.  

But now that I see things that make me wonder why Shuttlesworth is harping on better eye candy, when he can make a real difference in the underlying OSS model itself.  This would bring business users, which in turn bring home users.  The eye can route, ala OSX, only worked because of their killer app == iTunes + iPod + DRM monopoly + uber marketing campaign... but those are side points.  To address the above:

--> some layered network models do require a firewall on each host, not just www facing. in most cases, the router firewall is sufficient.  but in some (actually quite few) the need for gatekeeping still exists.  easy use case:  a university campus wifi network is a very hostile environment.

--> yes, ufw, firestarter, etc. are frontend to iptables.  but if they are not part of security updates then there is not even an implied guarantee that they will be maintained.  this is ok for normal users.  but how to move to corporate support?  it is non-trivial for one of these applications to make a mistake with rules and leave system open.  not ids will notice.  no messages.  

--> Abobe msgs are not so much about versioning as they are about security holes in LTS version.  Of course, one can turn it off.  However, when online service providers forcing on everyone, there is little choice to simply avoid it.  Even M$ is keenly aware of this, hence the whole Silverlight push.  Flash was more than adequate, but they see that (www) world is running on it and there is money to be made via an alternative.  Bring on the Moonlight!  Sorry... got carried away... the point is that such an "important" app should be part of security repos.

--> yes, apparmor is on by default.  but there are no profiles by default.  selinx is not on by default, which is ok.  selinux profiles are also not part of security repos.  no, they do not work simultaneouly.

so here is a great security tool, that does not actually protect by default.  the available profiles are few.  i think canonical should invest here and provide a large set of profiles.  value added distro.  it is not hard to profile most application since the behaviour is known.

same for selinux... but less so since it can be a bear to maintain.  

point is that the profiles that actually make these tools work are not part of security.  so a user that expects a system to be protected because of highly-touted apparmor is mistaken.

---

### Post by thehighhat on 2008-11-10
> **hyper_ch said:**
>  But you are free to name other "security tools" that are not in the main repos.  

A wide search for security/community/hardy lists: 

[http://packages.ubuntu.com/search?keywords=security&searchon=all&suite=hardy&section=universe](http://packages.ubuntu.com/search?keywords=security&searchon=all&suite=hardy&section=universe)


But on a more narrow inspection, consider these security related tools.  Arguably, these are pkgs thats users trust to protect their systems.  None of which are in the security repo....

nessus components
bastille  ( a fantastic tool btw )
apparmor-profiles
harden* ( good for initial lock down too ) 
anything related to selinux (except libselinux I think)
rkhunter
snort
etc..

Just read the very excellent security guide above (sticky).  

Even tools listed there are not themselves guaranteed to receive security updates, yikes.

---

### Post by ciscosurfer on 2008-11-10
> **thehighhat said:**
> Hardy is LTS.  The flash-nonfree is in multiverse. It has version 9.0.124.  See [http://packages.ubuntu.com/hardy/flashplugin-nonfree](http://packages.ubuntu.com/hardy/flashplugin-nonfree) 

This problem is compounded by the version number (Adobe has officially recommended a move to 10 to avoid attacks, even 0-day exploits), and by its proprietary code (developers cannot maintain it directly.)First, thanks for taking my call. 

Don't be led blindly.  Take some initiative.  Don't rely on others to secure your network.  Whether Hardy is LTS is immaterial.  And whether the backports and proposed repos seem out of place to you, there are reasons they are there.  If you're so concerned about the security implications of running an outdated version of Flash, then upgrade the package.  Or quite simply, don't use it!  No one forces you to use Flash, btw.  Flash is not an "important" app; you can get your news and giggles elsewhere.  And just because it's proprietary doesn't make it evil.  Also, reliance on frontend apps to do your backend bidding seems foolish.  Any competant systems or network administrator should understand how an application functions, from the ground up, not the other way around.  And you know what they say about those who assume...

Thank you, and I'll take my comments off the air :-D

---

### Post by koenn on 2008-11-10
> **thehighhat said:**
> A wide search for security/community/hardy lists: 

[http://packages.ubuntu.com/search?keywords=security&searchon=all&suite=hardy&section=universe](http://packages.ubuntu.com/search?keywords=security&searchon=all&suite=hardy&section=universe)


But on a more narrow inspection, consider these security related tools.  Arguably, these are pkgs thats users trust to protect their systems.  None of which are in the security repo....

nessus components
bastille  ( a fantastic tool btw )
apparmor-profiles
harden* ( good for initial lock down too ) 
anything related to selinux (except libselinux I think)
rkhunter
snort
etc..

Just read the very excellent security guide above (sticky).  

Even tools listed there are not themselves guaranteed to receive security updates, yikes.

Ubuntu targets the non-technical user.
Most of the tools you list here are rather advanced in that they either need to be configured correctly, or monitored, or both, to be of any use.
That's probably beyond most Ubuntu users, and that would explain why they are not in the main repo.

But I do agree there's something weird about Ubuntu/canonical's repo policy ; universe/multiverse/... are not officially supported, while the main repo is rather limited, and installing from 3th party sources is discouraged. It boils down to 'use what we can put on 1 CD, and nothing else'.

---

### Post by thehighhat on 2008-11-10
> **ciscosurfer said:**
> First, thanks for taking my call. 

Don't be led blindly.  Take some initiative.  Don't rely on others to secure your network.  Whether Hardy is LTS is immaterial.  And whether the backports and proposed repos seem out of place to you, there are reasons they are there.  If you're so concerned about the security implications of running an outdated version of Flash, then upgrade the package.  Or quite simply, don't use it!  No one forces you to use Flash, btw.  Flash is not an "important" app; you can get your news and giggles elsewhere.  And just because it's proprietary doesn't make it evil.  Also, reliance on frontend apps to do your backend bidding seems foolish.  Any competant systems or network administrator should understand how an application functions, from the ground up, not the other way around.  And you know what they say about those who assume...

Thank you, and I'll take my comments off the air :-D


:)  My posts are not meant to be or cause derision.  I think this is a good product.  Off to the races....

I am taking initiative...  this is why I am asking for opinions from the security forums (and possible Ubuntu security devs) w/o making nebulous bug reports.

The network is very aggressively secured and there is an active security policy in place for users.

Being LTS is quite significant.  It provides a stable (ABI/API) platform for ISVs/etc to standardize products.  I personally enjoy testing new distro releases.  But this does not work well for normal people and for business people.  Security and reliability are hallmarks of success.

I understand the value of the split repos.  I do not question their existence.  However, I do think security applications, network accessing, & heavily deployed applications (firefox for example) should be part of the security updates. 

I know how to use sw safely.  This is not an issue for me.  But normal users and non-sysadmin business users believe they are safe by virtue of using linux.  There is little notice of security implications of pkg/repo decisions.

Yes, philosophically flash is not important.  In reality, it is a high profile critical app.  (like FF).  It is easy to disable and not use.  But this is about the deeply penetrated market share of flash on linux, and it not being part of security repos.  Negotiate w/Adobe Canonical ... top down leadership I say.
 
Whoa now partner... I have nothing against FOSS or proprietary sw.  There is a place for everything.  My comments only meant that it is not trivial for a developer like me to fix.  

Frontend apps need to be just as high quality and secure as cmd line variants.  Just because it can be clicked does not mean it should be neglected.  Bring on a good GUI.  And don't cripple the prompt either.  This is very reasonable.  Personally, I like my eye candy with my meat and potatoes.


I do not know what the comment about assuming something means.  I do know that Solaris is not the only product w/outdated flash.  (Ugh.. this discussion was supposed to be about more than just flash, oh well)  I do know that LTS relies on upstream.  Upstream is extra funky about proprietary codes.  Ubuntu is more sensible.  But, LTS exposes users to security problems in very peculiar ways.

---

### Post by cariboo on 2008-11-10
I think you might find more of what you want in the for pay support from Canonical have a look here:

[http://www.canonical.com/services/support](http://www.canonical.com/services/support)

Jim

---

### Post by ciscosurfer on 2008-11-10
> **thehighhat said:**
> :)  My posts are not meant to be or cause derision.  I think this is a good product.  Off to the races....

I am taking initiative...  this is why I am asking for opinions from the security forums (and possible Ubuntu security devs) w/o making nebulous bug reports.

The network is very aggressively secured and there is an active security policy in place for users.

Being LTS is quite significant.  It provides a stable (ABI/API) platform for ISVs/etc to standardize products.  I personally enjoy testing new distro releases.  But this does not work well for normal people and for business people.  Security and reliability are hallmarks of success.

I understand the value of the split repos.  I do not question their existence.  However, I do think security applications, network accessing, & heavily deployed applications (firefox for example) should be part of the security updates.  

I know how to use sw safely.  This is not an issue for me.  But normal users and non-sysadmin business users believe they are safe by virtue of using linux.  There is little notice of security implications of pkg/repo decisions.

Yes, philosophically flash is not important.  In reality, it is a high profile critical app.  (like FF).  It is easy to disable and not use.  But this is about the deeply penetrated market share of flash on linux, and it not being part of security repos.  Negotiate w/Adobe Canonical ... top down leadership I say.
 
Whoa now partner... I have nothing against FOSS or proprietary sw.  There is a place for everything.  My comments only meant that it is not trivial for a developer like me to fix.  

Frontend apps need to be just as high quality and secure as cmd line variants.  Just because it can be clicked does not mean it should be neglected.  Bring on a good GUI.  And don't cripple the prompt either.  This is very reasonable.  Personally, I like my eye candy with my meat and potatoes.


I do not know what the comment about assuming something means.  I do know that Solaris is not the only product w/outdated flash.  (Ugh.. this discussion was supposed to be about more than just flash, oh well)  I do know that LTS relies on upstream.  Upstream is extra funky about proprietary codes.  Ubuntu is more sensible.  But, LTS exposes users to security problems in very peculiar ways.So here's the thing: I actually agree with the majority of your statements so far.  However, playing Devil's advocate is sometimes a good way to further the conversation.  I could have (should have) phrased things a bit differently so as to not stir the pot unnecessarily.  Let's (the community) continue to have these debates/discussions in the hope that fair-minded people will heed the warnings, the issues, and the call for possible change.

Security is tricky business.  Educating the end user is also a daunting task at times, especially when they are only accustomed to one way of thinking.  Our job is to make them aware of certain pitfalls, keep them abreast of changes, and ultimately to keep them safe.  Timely upstream releases, though, should really get more attention.  Agreed.
>  But normal users and non-sysadmin business users believe they are safe by virtue of using linux.Which is a fallacy, of course. Normal/Business types need to be educated about new and different environments that seem foreign to them (just as you and I were). Some may like being educated. Some will scoff. From a security standpoint, protections need to be in place regardless of proper education to the end user. So it would seem that again we agree here. :-D

There *is* something screwy about an LTS release not being more "on the ball".  But what we can do in the meantime is exactly what we've mentioned already: block it, upgrade it, put the kibosh on it altogether.  Will this detract newcomers (businesses, commercial entities, end users) to the Linux scene?  Perhaps.  But remember change takes time.  And in a world right now with more Windows exploits than you can shake a stick at, over time, the convincing may get easier [cue: Apple commercials]. :) 

Frontend / Backend argument: We're on the same page.  Attention should be given to each in their own right.

Proposed / Backports / Split Repo's argument: We're on the same page.

On security vulnerabilities: Any app this is heavily used by the community as a whole should be held in higher regard.

On taking initiative: I'm sure you do, as do I.  My comments were intended to speak to a larger audience than just as a retort to your original post.  Sometimes it's not good to be a sheep and just follow the herd (again, a comment on the community at large--I'm not calling you a sheep...baahhhhh.  Sorry, couldn't resist)

On derision and assumptions: I was the one who certainly took a derisive tone.  But my beef wasn't necessarily with you, rather it was a comment on how self-content folks become in their daily routine.  And that's not always a great thing.  Viva la FOSS!

---

