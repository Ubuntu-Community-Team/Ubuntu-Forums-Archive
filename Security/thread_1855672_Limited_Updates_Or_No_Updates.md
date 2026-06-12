---
title: "Limited Updates Or No Updates"
date: 2011-10-06
forum: Security
---

### Post by KBD47 on 2011-10-06
OK, I expect to be told I'm crazy, but based upon not only my own negative experiences with updates, but the many posts I see in the forum: My Wireless Quit Working After Update--Help!
  And other such posts, I'm wondering what the real danger is in not updating, or only selectively updating, such as just updating Internet Browsers and Email Programs? If it is working, why fix/bork it? 
  
KBD47

---

### Post by ajgreeny on 2011-10-06
I have always accepted all updates on my systems, but if I were to limit them in any way it would be to accept just the security updates and not all the recommended updates.  That way you should stay secure, but would not get all the bug fixes and application updates etc etc that come with the others offered.

---

### Post by KBD47 on 2011-10-06
Security Updates are a good idea. 
Thanks.
KBD47

---

### Post by KBD47 on 2011-10-23
I keep finding myself thinking---if Ubuntu is working, don't 'fix it' with an update:

Here’s where it gets crazy, though. I asked if they used this distro (CentOS, version 5.6) anywhere else in their organization.

“Yes,” I was told. “On lots of machines. But we don’t ever run updates. Once it’s installed, we leave it alone.”
[http://paper.li/LinuxHQ/1315868351](http://paper.li/LinuxHQ/1315868351)

---

### Post by dfarrell07 on 2011-10-24
If you have everything working nicely, I think it is very reasonable not to do a dist upgrade, and just keep up with security updates. Dist upgrades almost always break things for me, that I eventually get working again, and then in 4-5 more months the next one comes along and the cycle repeats. Note: To be fair, they also fix things, but that is not relevant if you have a fully working system.

---

### Post by KBD47 on 2011-10-25
I moved up from 11.04 which was working great to 11.10 and it broke my video. I ended up moving back to 11.04. I generally like new features and newer software, but it sometimes seems a choice between older and working or brand new and broken.
KBD47

---

### Post by HermanAB on 2011-10-25
Of course, on these forums, you will see all the problems - that is the reason detre of the fora!

As always, it depends on what you are doing with your machine:

If you are running a plain vanilla home use system, then doing automatic updates may be a good idea.  Most users fall into this category.
If you compile some software from source yourself, then doing updates could be a bad idea, since an update may break your software.
If you are running a business critical machine, then doing updates is a bad idea.  In this case, you should have a duplicate system (usually a VM) where you test any updates before applying them to your business server.

You could consider automatically applying security patches to your business machines, but even that could break some things.

Since I compile things from source, and use my machines for business, I never do updates.  Once a year or three, I re-install the whole system from scratch instead.

Hope that helps!

---

### Post by tubbygweilo on 2011-10-25
> If you are running a business critical machine, then doing updates is a bad idea. In this case, you should have a duplicate system (usually a VM) where you test any updates before applying them to your business server.

You could consider automatically applying security patches to your business machines, but even that could break some things.


Users of critical systems or those that supply income are well advised to follow the above advice, it is suprising just how many do not realise an overhead is attached to disaster recovery and a sound system testing environment.

If something works then change as little as possible and you will have a high chance of it still working after any alteration / update.

---

### Post by vasa1 on 2011-10-25
> **HermanAB said:**
> Of course, on these forums, you will see all the problems - that is the reason detre of the fora!

As always, it depends on what you are doing with your machine:

If you are running a plain vanilla home use system, then doing automatic updates may be a good idea.  Most users fall into this category...
I, a plain vanilla home user, accept all updates and haven't yet encountered problems.

---

### Post by KBD47 on 2011-10-25
Interesting idea about running a second OS in a virtual machine to test updates, I hadn't thought of that.

---

