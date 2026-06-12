---
title: "Firewall?"
date: 2010-04-15
forum: Security
---

### Post by HHx66 on 2010-04-15
So I know Linux has iptables, I'm rather new to linux, and I'm wondering, are the stock settings with Ubuntu/Kubuntu safe? Is there anything I need to do make them more secure? I tried adding rules myself for some things but ended up just not being able to do anything so I had to reset back to stock with iptables -F

So any help on this subject? should I be safe running as-is?

---

### Post by rookcifer on 2010-04-15
> **HHx66 said:**
> So I know Linux has iptables, I'm rather new to linux, and I'm wondering, are the stock settings with Ubuntu/Kubuntu safe? Is there anything I need to do make them more secure? I tried adding rules myself for some things but ended up just not being able to do anything so I had to reset back to stock with iptables -F

So any help on this subject? should I be safe running as-is?

The default deny policy that UFW (Ubuntu Firewall) has is good enough.  The only thing you need to do is make sure you install all your software from the repositories.  Don't install random .debs from some website.

If you want advanced security, look into AppArmor.  There is a sticky about it and other security tips at the top of this forum.

---

### Post by uRock on 2010-04-16
Also, if you are using a router, then it should be blocking incoming connections. If you are not doing any file sharing, then you can just run ```
sudo ufw enable
``` and everything will be blocked without any hindrance of you connecting to the great www. AppArmor is a great app. 

Cheers,
Ronnie

---

### Post by HHx66 on 2010-04-17
Thanks for the info, yes I run behind a router, I do some p2p/filesharing (mostly torrents)

---

### Post by uRock on 2010-04-17
They will only be able to connect to the ports you have opened for torrenting. Setting up AppArmor may be helpful in protecting from an intruder making changes. [http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

---

