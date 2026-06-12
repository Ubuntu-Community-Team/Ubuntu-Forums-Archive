---
title: "(Patched)10.04 Security Holes"
date: 2011-03-05
forum: Security
---

### Post by bumder on 2011-03-05
Lucid is in the news (not in a good way :() 
[http://www.dslreports.com/forum/remark,25569097](http://www.dslreports.com/forum/remark,25569097)

After an update, I'm currently at kernel version 2.6.32-29-generic. The article mentions kernel 2.6.35-25-generic. How come this isn't showing up in updates, do I have to add a ppa for this?

Thanks 

:p

---

### Post by uRock on 2011-03-05
> **bumder said:**
> Lucid is in the news (not in a good way :() 
[http://www.dslreports.com/forum/remark,25569097](http://www.dslreports.com/forum/remark,25569097)

After an update, I'm currently at kernel version 2.6.32-29-generic. The article mentions kernel 2.6.35-25-generic. How come this isn't showing up in updates, do I have to add a ppa for this?

Thanks 

:p
You aren't seeing the 2.6.35 kernels because you are not using Ubuntu 10.10. Why not link that article instead of some other forum? If you look at the original article, then you will see that those holes were found over a month ago and the kernel has been patched at least once since then. As for the ZDNet blog, it looks like they were copying the original article and making it look like they found something new. In the reply on the ZDNet you will see the following quote, which explains what to do to keep your system safe.

> This is silly.

Basically if you use Linux kernel 2.6.32 without tracking security  update patches there are a few potential vulnerabilities (few if any  examples of these being used for attacks in the wild) especially when  using non-default system configurations. This has nothing to do with  Ubuntu since all current enterprise server Linux distributions have the  same base kernel version
.
Solution: 1. Keep your security patches up to date; 2. Don't disable  security on your server (apparmor; selinux; ufw; ssh; bad passwords;  etc.); 3. Don't enable services/accounts/capabilities you don't need.

Of course all of these rules apply regardless of the OS, but Linux  distributions are by far the fastest (on average) to release patches  once a potential exploit has been identified. Furthermore, for the truly  paranoid you can use KVM virtualization with one service provided per  VM and even use OpenBSD in your VM if you are less concerned about  scalability then about security.

Using PPA kernels not shipped with the distribution is not recommended.

---

### Post by bumder on 2011-03-05
Okay, the current default 2.6.32-**29** has been patched already anyway? I take it that is the '29th' patch of the 2.6.32 lucid kernel.

---

### Post by cariboo on 2011-03-05
If you want to check security updates, have a look [here]("http://www.ubuntu.com/usn").

---

### Post by Hector23 on 2011-03-05
[QUOTE=uRock;10525485]You aren't seeing the 2.6.35 kernels because you are not using Ubuntu 10.10.

"Almost 40 vulnerabilities, which allow remote and local exploits, have been discovered in the Linux Ubuntu 10.04 Long Term Support (LTS) kernel."

[http://www.zdnet.com.au/ubuntu-peppered-with-holes-339310663.htm](http://www.zdnet.com.au/ubuntu-peppered-with-holes-339310663.htm)

"Almost 40 vulnerabilities have been discovered in the kernel of Linux Ubuntu 10.04, also known as Lucid Lynx, which is a long-term support version of the operating system."

[http://www.zdnet.com/blog/open-source/ubuntu-security-holes-found-holes-fixed/8402](http://www.zdnet.com/blog/open-source/ubuntu-security-holes-found-holes-fixed/8402)

Edit:

According to those two articles the holes are present in 10.04. Only Ubuntu 10.04? No other non-Debian-Ubuntu based distro? I doubt it.

Edit.

I just checked the link provided by Urock:

"A security issue affects the following Ubuntu releases: Ubuntu 10.04 LTS This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu. The problem can be corrected by upgrading your system to the following package versions: Ubuntu 10.04 LTS: linux-image-2.6.35-25-generic 2.6.35-25.44~lucid1"

[http://www.ubuntu.com/usn/usn-1083-1](http://www.ubuntu.com/usn/usn-1083-1)

This new kernel is not available from Update manager (lucid-proposed not enabled). From what I saw at Google's there were problems with this new kernel. Maybe it has been held back until the bugs are fixed?

---

### Post by uRock on 2011-03-05
From reading the replies to the blogs on both sites, I believe all distros using the kernel may have had the vulnerabilities.

There was an update to the 2.6.32 kernel just a couple of days ago and it most likely fixed the holes mentioned in the article. As I have already pointed out, the 2.6.35 kernel is only used in 10.10. Unless you install it yourself, you will not see the 10.10 kernel in 10.04.

---

### Post by Hector23 on 2011-03-05
> **uRock said:**
> From reading the replies to the blogs on both sites, I believe all distros using the kernel may have had the vulnerabilities.

There was an update to the 2.6.32 kernel just a couple of days ago and it most likely fixed the holes mentioned in the article. As I have already pointed out, the 2.6.35 kernel is only used in 10.10. Unless you install it yourself, you will not see the 10.10 kernel in 10.04.

Hi uRock,

I believe the link you provided in your previous post pretty much says it all: the 2.6.35 kernel is needed to fix vulnerabilities in Lucid 10.04 LTS, and it's not presently available unless, maybe, you select lucid-proposed. (I didn't try.)

Many times, vulnerabilities fixed are weighted against bugs a new kernel introduces. Maybe developers are fixing bugs as we speak. I have no idea. It would be really nice if somebody explained what's going on. At first glance -- but I'm far from an expert -- 9 vulnerabilities permitting root access seems a serious concern.

---

### Post by Hector23 on 2011-03-05
When you reread carefully SVN article, you get to this one sentence from Gerry Carr

Or, as Gerry Carr, Head of Platform Marketing for Canonical, Ubuntu’s parent company, put it, “(...) Thirdly it would have effected very few users anyhow as it was a backport kernel not the default kernel."

[http://www.zdnet.com/blog/open-source/ubuntu-security-holes-found-holes-fixed/8402](http://www.zdnet.com/blog/open-source/ubuntu-security-holes-found-holes-fixed/8402)

What's this supposed to mean? Only the people using a certain backported kernel are affected by the 40 security holes? Everybody else is safe? Well, then, how come Ubuntu doesn't provide the number of this kernel, make the headlines with this one sentence and bring the issue to it's real dimension?

Why leave everybody being fed FUD? There certainly is a problem at Ubuntu/Canonical: P.R. is just plain awful.

---

### Post by mikewhatever on 2011-03-05
Hector23, are you seeing something I don't? What I see is Darren Pauli trying to make headlines on znet.com.au by posting nonsense and making a fool of him/her self. What's important is, the vulnerabilities are patched, both in 2.6.32 and 2.6.35. Make sure you install security updates.

---

