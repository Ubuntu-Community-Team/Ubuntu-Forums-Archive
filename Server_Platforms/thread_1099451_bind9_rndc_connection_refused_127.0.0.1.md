---
title: "bind9: rndc: connection refused 127.0.0.1"
date: 2009-03-18
forum: Server Platforms
---

### Post by asimons999 on 2009-03-18
Hello,

I'm getting a message along the lines of
```

rndc: connection refused 127.0.0.1:###   [fail]

```

But still starts bind (I can use it as a cache DNS, but it won't serve the local domain I've setup)

I have successfully setup a DNS on my home PC and is working fine. But doing the same (or very similar thing) at work hasn't produced the same result. Both running Ubuntu Server 8.10

I may have installed bind from the cd on one machine and using apt-get on the other.

**Commentary centred on Possible Solutions**
[LIST]
[*]I don't remember there being permission denied's in the syslog
[*]I thought that I'd already uninstalled AppArmor ( [http://ubuntuforums.org/showthread.php?p=6914743#post6914743](http://ubuntuforums.org/showthread.php?p=6914743#post6914743) ), but I'll check I've done it properly in the morning. In fact it looks like my home server (the one working) has AppArmor installed). 

[/LIST]

---

### Post by asimons999 on 2009-03-18
I haven't fixed it, but it's no longer a problem.

I made a NOOB mistake with thinking ; was a comment character, when I had commented out "forwarders". but switched it back to //

and all working now.

---

