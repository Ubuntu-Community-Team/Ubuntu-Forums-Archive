---
title: "Limit SFTP Bandwidth"
date: 2010-06-09
forum: Server Platforms
---

### Post by samurailink3 on 2010-06-09
Howdy! I was wondering if there was any configuration I can set (for instance, in /etc/ssh/sshd_config) that would limit the amount of bandwidth I allow for SFTP. I have a server that gives content to the outside, but when multiple users start pulling through SFTP, it tends to bog down the network a bit (On fiber, a faster network really isn't an option), so I was wondering if there was any built-in way to manage how much upload I dedicate to SFTP. Thanks for the help!!

---

### Post by samurailink3 on 2010-06-09
Deleting cookies and temporary files won't ease your bandwidth usage, if anything, clearing the cache contstantly would raise your bandwidth usage a bit.
The easiest way to explain bandwidth is to use plumbing as an analogy. If your internet connection is very limited on bandwidth, it's similar to having a very small pipe: You get water (data), but at a very slow rate, like a faucet. If you have a very fast (lots of bandwidth) internet connection, its like having a firehose. Lots of water, very quickly. The most similar thing to a firehose the computer world has are fiber connections at the moment, but things are always getting faster! Hope that helped you out.
This article might help you out: [http://simple.wikipedia.org/wiki/Bandwidth_(computing](http://simple.wikipedia.org/wiki/Bandwidth_(computing))

Update to my issue: I'm currently utilizing QOS rules on the router to achieve the desired effect, but I would like to use methods built into SFTP, are there any configuration switches I can set?

---

### Post by anomie on 2010-06-09
[QUOTE=samurailink3]... I was wondering if there was any built-in way to manage how much upload I dedicate to SFTP.[/QUOTE]

AFAIK, there is nothing baked into openssh that would provide this functionality, black mage. :) 

A quick google search turned up this: [http://www.trilug.org/pipermail/trilug/Week-of-Mon-20050307/033356.html](http://www.trilug.org/pipermail/trilug/Week-of-Mon-20050307/033356.html)

The right answer will probably involve the command mentioned there (or some other sysctl MIB tweak), iptables (or an add-on module), or a network device at your perimeter. 

IOW, this sort of feature seems out of the domain of openssh.

---

### Post by arrrghhh on 2010-06-09
Yea, a hardware device that throttles network traffic would probably work much better... There's more advanced ones that can easily do shaping and modeling as well...

---

### Post by paulisdead on 2010-06-09
Check out MySecureShell.  I don't think it's in the repos, and I'm pretty sure I just installed a deb of it on my debian server.  In addition to throttling, you can also chroot accounts into their home directories.

---

### Post by samurailink3 on 2010-06-09
These all sound like wonderful things for me to explore! Thanks!! For now, I'll stick with the QOS on the router, it is doing an alright job at keeping the packets flowing steady. I'm quite interested in TC, so I'll do some research on that command and see exactly how I am going to implement it. As for MySecureShell, I will be checking this out as well, it looks to have a ton of options I am looking for.
Thanks, everyone! You've all been a huge help!

---

