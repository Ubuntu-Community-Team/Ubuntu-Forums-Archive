---
title: "Ubuntu Sever X64 Firewall, suggestions please"
date: 2010-06-10
forum: Server Platforms
---

### Post by Fred2040 on 2010-06-10
Hi people, I have few questions about how to make my old home pc in a **firewall**
Is athlon 64bit, 512mb, two lan cards, 2hd etc


+ Can I Install an **Antivirus **solution In Ubuntu?, to Detect MS Windows risk, like trojans, etc... **Exits**?
+ **Suppose**:  I have a good external configuration ... but the  hacker can use the internal network ... How to  configure the internet to use it? and Other services like **storage, sharing **[COLOR=#000000]without compromising  the server
+ [/COLOR][COLOR=#000000]Would be possible to  completely block the MAC address?
+[/COLOR] Recommendations for **hardware&software **security (**important**)[COLOR=#000000] Manuals, documentations

[/COLOR]Sorry, but I am newbie in Ubuntu,
any help can be appreciate

---

### Post by arrrghhh on 2010-06-10
Antivirus - [ClamAV](http://www.clamav.net/)

If you have a hacker in your internal network... the only thing you can do is add additional security to your internal network, (similar to your external network) which can be cumbersome for the clients.  MAC auth would probably be the easiest, but spoofing MAC's is also possible.

You can do MAC authentication, certainly.

Check out [Shorewall](http://www.shorewall.net/) - it's insanely configurable.  Not very easy learning curve, I'm afriad...

---

### Post by Fred2040 on 2010-06-11
> **arrrghhh said:**
> Antivirus - [ClamAV]("http://www.clamav.net/")

If you have a hacker in your internal network... the only thing you can do is add additional security to your internal network, (similar to your external network) which can be cumbersome for the clients.  MAC auth would probably be the easiest, but spoofing MAC's is also possible.

You can do MAC authentication, certainly.

Check out [Shorewall]("http://www.shorewall.net/") - it's insanely configurable.  Not very easy learning curve, I'm afriad...



:popcorn: I will test your suggestions...  Thks a lot

---

