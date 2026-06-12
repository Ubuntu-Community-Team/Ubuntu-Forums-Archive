---
title: "NSA B Gone?"
date: 2016-12-09
forum: Security
---

### Post by TheFu on 2016-12-09
Anyone played with this [https://github.com/tobykurien/NSA_b_gone](https://github.com/tobykurien/NSA_b_gone) yet? 

Interesting ideas. Each process mush be in a specific group to have internet access.  Guessing it would be a hassle to setup initially.

---

### Post by HermanAB on 2016-12-09
It will probably be more hassle than it is worth.  

On a Linux machine you can always look at your traffic and log files if you are paranoid and keep things under control with iptables.

---

### Post by TheFu on 2016-12-09
> **HermanAB said:**
> It will probably be more hassle than it is worth.  

On a Linux machine you can always look at your traffic and log files if you are paranoid and keep things under control with iptables.

For an average desktop user, I'd agree, though a sophisticated attacker would clean up local log files.  It is basically a script that default denies in and out traffic except for members/processes running with the "internet" effective  groupid.  I'm not thrilled with some of the default assumptions - like assuming people use network-manager or have IPv6 enabled.  I do like that MACs and hostnames are randomized.  There are lots of inconsistencies in the script, but it is still interesting.

For folks running high-risk services, perhaps preventing normal tools from having internet access will slow down the attackers?  

Imagine you are an attacker.  What you'd do if curl, wget, ftp, ssh-client, nc, perl, python didn't have network access?  All the hacking scripts would probably fail.  Just run the high-risk service with networking allowed.

---

### Post by #&amp;thj^% on 2016-12-09
I have just been playing around with it...for about an hour now. Guess I was bored.
Yep it is a big headache with VPNs...Have not found a way to do this yet. (Successfully Connect)
I too like that MACs and hostnames are randomized. But as you have already pointed out there are lots of inconsistencies in the script.
But once you get everything set-up I guess it might be worth some more testing.
Glad you brought this to our Attention. For security as we know or "not know" now is an everyday learning curve.
But overall I will first depend on my own good sensibility and safe browsing habits and a trusted VPN provider.
Regards

---

### Post by cogset on 2016-12-13
Interesting, but if one has to fiddle with this script to somehow selectively grant privileges and limit internet access, wouldn't for instance QubesOS take this concept (networking in an unprivileged virtual machine, isolated from other domains) to its full potential?

 OTOH, if that script were a ready to use, relatively user-friendly application like Firejail it could be worth a try.

---

### Post by TheFu on 2016-12-13
I'm not seeing this for use on a desktop.
Only on servers where we want to make only 1 or 2 processes have internet access. All others are blocked.  

Think like a hacker.  apache and ssh work, but nothing else does.  None of your 500 scripts to capture system data or create a reverse proxy work.  What next?  If the machine doesn't report back to C&C ... probably nothing.  Mission accomplished.

Automate this through a devops tool FTW!

This script is really an example of using [netfilter]("https://www.netfilter.org/") limited by groups for internet access. We can all do that today, but based on the number of currently hacked php webapps out there, it seems very few admins do. If they can't point-n-click a solution, it doesn't get used. ;(

I like firejail and use it, but really don't _trust it_ like I trust netfilter.

Qubes is a different animal and very interesting for desktop-on-desktop virtualization. Don't do much of that.

---

