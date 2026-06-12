---
title: "System76-dev/stable/ubuntu/dists/precise/  etc Not Found"
date: 2014-01-05
forum: System76 Support
---

### Post by watchpocket on 2014-01-05
How can I make it so I don't see these lines every time I do a 'sudo apt-get update'?


W: Failed to fetch [http://ppa.launchpad.net/system76-dev/stable/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/system76-dev/stable/ubuntu/dists/precise/main/source/Sources)  404  Not Found
W: Failed to fetch [http://ppa.launchpad.net/system76-dev/stable/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/system76-dev/stable/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found
W: Failed to fetch [http://ppa.launchpad.net/system76-dev/stable/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/system76-dev/stable/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

---

### Post by Dave_L on 2014-01-05
In synaptic, in Settings >> Repositories >> Other Software, uncheck:
[http://ppa.launchpad.net/system76-dev/stable/ubuntu](http://ppa.launchpad.net/system76-dev/stable/ubuntu) precise main

---

### Post by watchpocket on 2014-01-06
Thank you, I will do that.  Does this means Sys76 has no repository for 12.04?

---

### Post by Dave_L on 2014-01-06
> **watchpocket said:**
> Thank you, I will do that.  Does this means Sys76 has no repository for 12.04?

See [http://ubuntuforums.org/showthread.php?t=2165676](http://ubuntuforums.org/showthread.php?t=2165676)

---

### Post by watchpocket on 2014-01-06
*Wow*.  I don't think I'll be giving up on System76 but this is not encouraging.  Particularly after I just installed 12.04 and wasted a week on Unity before finally vaulting over its pink-dungeon prison walls back to Gnome Basic.  

There is a clear split between the mindset of the hardware/software seller ( as exemplified here -- and from which this PPS policy springs -- [http://carlrichell.com/post/44549453930/lts-should-die](http://carlrichell.com/post/44549453930/lts-should-die)   ) and that of users of heavily customized setups who don't want to upgrade regularly only to find the nightmare of a Unity (and bugs, and new-feature bloat they have no use for) lying in wait with every new version.

I really don't want to re-build my environment every six months, but Mr. Richell thinks users like me don't exist.

---

### Post by Dave_L on 2014-01-06
I agree.  Insisting on an unending stream of new features is deranged. I use my computer to get things done. If it works satisfactorily at that, why change it?

---

### Post by houstonbofh on 2014-01-11
I used to be System76s biggest fan.  I purchased SEVERAL Eland Pro servers from them.  (One of which that was not even going to run Linux)  I knew that my Lemur was a Clevo, and my Eland was a Intel SC based server, but they provided good hardware at a good price, supported Linux, and the support was some of the best I had seen in the industry. (And I have been in it over 20 years)

Well, things change...  Support went way down.  There is not even any e-mail based support anymore.  Then the hatred of LTS.  Guess what?  Your niche is Linux support.  By making decisions on what you will and will not support, you are cutting up your own niche.  And the odd thing is that you offer 12.04 on servers.  I guess you know that server admins won't put up with this crap.  But guess what?  Server admins also have laptops...

Also, there is competition.  Zareason offers and supports 12.04. (and Mint and Susi, and Debina, and Fedora...)

And frankly, that post from Carl Richell was just insulting.  It sounds like something Microsoft would say about XP.

---

