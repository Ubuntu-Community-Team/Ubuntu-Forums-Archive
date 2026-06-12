---
title: "seLinux default setup access denies in Ubuntu Desktop 20.04"
date: 2022-04-20
forum: Security
---

### Post by hoza2 on 2022-04-20
Hello!

I am learning ways to harden a Linux system, specifically with seLinux and access control mechanisms it implements.
Following this guide (with remarks for Ubuntu):

[URL="https://wiki.debian.org/SELinux"]https://wiki.debian.org/SELinux
[/URL]
I have managed to setup seLinux in permissive mode.
However,  looking at the audit logs for AVC entries shows that there are lots of  denials after system booting, e.g. from accountsd_t, avahi_t,  NetworkManager_t, and loots other source context types.
There are  3499 access denies in total, so I guess the system will fail to boot the  userland if seLinux mode is switched to enforcing.

Before  digging any further, I wanted to figure out if seLinux in Ubuntu  requires some different setup procedure (different packages installed  than those on that wiki or whatever) or if it is not maintained.
Has anyone tried to setup seLinux in enforcing mode on Ubuntu LTS successfully?

---

### Post by DuckHook on 2022-04-20
You have good instincts looking into system hardening platforms like seLinux. However, seLinux has a big learning curve. And, just as you have already experienced, getting some profiles wrong will lead to system breakage.

Alternatively, Ubuntu already comes with a similar system hardening platform by default. It is called Apparmor. I don't know how familiar you are with it but, if you are not, then I would advise the following:

[LIST=1]
[*]Before tackling seLinux, first get used to Apparmor.
[*]Apparmor profiles are already included and active for many apps. The problem with these profiles—if it can even be called a problem—is that they are too permissive.
[*]The devs did this for good reason: if they were any more restrictive, general users would run into roadblocks while trying to use the more obscure features of an app. So, the devs have decided to err on the side of usability over super hardened security.
[*]But because Apparmor is already installed and already has basic profiles, it is much easier to learn than a non&#8209;native platform like seLinux.
[*]Therefore, I would advise that you try hardening your Apparmor profiles first. This will not only increase your security right away and with the least amount of pain, but it will reduce the learning curve should you eventually decide to install seLinux too.
[/LIST]
Speaking only personally, I do not use seLinux. I find Apparmor to be quite sufficient.

I do harden Apparmor beyond its default configurations though. As an example, Firefox has an Apparmor profile that is active by default. However, it is very permissive and allows (among other things) access to my camera and microphone. Since I never use FF for interactive media, I have restricted FF from camera, microphone or, indeed, any USB access at all. It's not a big learning curve because tweaking an existing profile is far easier than building one from scratch.

---

### Post by hoza2 on 2022-04-21
Thanks for the quick reply, DuckHook!

I can see that seLinux is a rather complex beast, but my understanding is that it is also kind of complete solution for several major access control models/approaches in mind, that made it through 80s and 90s (MAC, UBAC, RBAC).
All other access control LSM's AFAIU are kind of simplification based on seLinux usage experience, but not without their drawbacks. AFAIU AppArmor can be susceptible to some kinds of vulnerabilities caused be the fact that objects on FS can be changed maliciously by links manipulation and AppArmor cannot detect that as its objects are identified by FS paths and not labels. So I believe it is not only administration effort made easy with those newer LSM's.
So, AFAIU after mastering seLinux one would also understand why/when more simple access control systems do (or do not) make sense in certain environments.

I was also thinking at first, if seLinux became some kind of obsolete due to its complexity without bringing more security value, but it does not seem to be the case.
It is used (at least) in Fedora and Android, and in Fedora the enforcing mode works out of the box.
Not in Debian/Ubuntu however.

---

### Post by DuckHook on 2022-04-21
I'm not going to pretend to any knowledge as in&#8209;depth as that required to answer your detailed query. For all I know, what you have stated is dead&#8209;on accurate. But what my personal experience has shown me is that, in chasing security, a lot of people miss the forest for the trees.

Speaking in general terms, security is a layering exercise. There is no one element that stands heads and shoulders above the others. Therefore, the important thing is not to focus on any single element, but to methodically implement a whole suite of safeguards so that bad guys must surmount multiple barriers before they can penetrate your screen of defences.

I have no knowledge of your other measures, but we frequently get queries on these forums where security conscious people with admirable intentions emphasize one tool at the expense of the rest. For example, they will waste scads of time wrestling with false positives after installing Snort while neglecting UFW. Snort is esoteric, arcane, obscure, cussed, requires a steep learning curve and must be installed/configured/painstakingly tweaked, whereas UFW is comparatively simple, straightforward, well&#8209;documented and is already part of Ubuntu in every default install.

It is pretty obvious which one should be learned, implemented and hardened first: UFW. There are tons of additional and far simpler measures that should precede Snort including the aforementioned Apparmor, sandboxing (using VMs, containers and FireJail), versioned backups, proper log reviews, auto system alerts, LAN segmentation, high entropy passphrases, enforcing keys and certificates, data directory encryption, minimal privileges, 2FA&#8212;the list is as long as my arm. In fact, in my opinion, Snort is so far down the list that it doesn't much matter whether it is implemented at all.

In your case, I'm not suggesting that you forego seLinux; only that you start with Apparmor and go from there. By learning Apparmor and hardening it further, seLinux will not be as intimidating. There's nothing wrong with having both Apparmor and seLinux installed at the same time, but after Apparmor, the seLinux learning curve will be significantly lower.

---

