---
title: "NFBlockD ip blocker"
date: 2008-07-22
forum: Security
---

### Post by konsole on 2008-07-22
> **makovick said:**
> Just for your information, some time ago after trying out MoBlock, I ended up writing my own derivative, which eats much less memory, uses simpler algorithms (rbtrees are a bit overkill) and can also read gzipped ascii blocklists (such as the ones available at Bluetack.co.uk). From the outside, it should work the same way as MoBlock.

Feel free to try it out, any feedback is welcome.

[http://makovick.googlepages.com/nfblockddaemon]("http://makovick.googlepages.com/nfblockddaemon")

Many thanks for your efforts makovick. I recently changed to nfblockd and love using it. It is an easy, uncomplicated install and is currently using a mere 8960K memory on my system doing the same job as moblock previously did.

A couple of things I customized were: changing the cron job to make the blocklist update weekly instead of daily. I also added iptables-save / restore / flush commands to the rc script. Not essential, but they work for me.

Users need a basic knowledge of iptables to build their chains but I'd recommend your software to anyone requiring a secure and very lightweight ip blocker. 

It's exactly what I need. Great work. =D>

---

### Post by alain57 on 2008-07-23
there is an other tool : [http://sourceforge.net/projects/iplist](http://sourceforge.net/projects/iplist)
it has even a graphical user interface an has some paramaters like
update frequence, choosing the list of ip to be blocked
dont block some ports (http for exemple)
i find it even better than peerguardian for windows

---

