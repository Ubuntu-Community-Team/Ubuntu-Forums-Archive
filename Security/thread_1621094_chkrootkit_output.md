---
title: "chkrootkit output"
date: 2010-11-13
forum: Security
---

### Post by toolmania1 on 2010-11-13
I ran this

sudo chkrootkit -q

I got this asoutput
---------------------------------------
  	 	 	 	p { margin-bottom: 0.08in; }  [SIZE=3]**/usr/lib/pymodules/python2.6/.path**[/SIZE]
[SIZE=3]**/usr/lib/jvm/.java-6-openjdk.jinfo**[/SIZE]
[SIZE=3]**/usr/lib/xulrunner-1.9.2.12/.autoreg**[/SIZE]
[SIZE=3]**/usr/lib/firefox-3.6.12/.autoreg**[/SIZE]


[SIZE=3]**eth0: PACKET SNIFFER(/sbin/dhclient3 (deleted)[893])**[/SIZE]
[SIZE=3]**user tim deleted or never logged from lastlog!**[/SIZE]
------------------------------------


Now, I deleted the dhclient3, so that part of the above looks ok now.  Also, I googled it and other people have said that the statement with dhclient3 is a false positive.


Any ideas on that and the other output above?


I am running Ubuntu 10.10

[SIZE=3][/SIZE]
    	 	 	 	p { margin-bottom: 0.08in;*

---

### Post by brian_p on 2010-11-14
> **toolmania1 said:**
> 

Now, I deleted the dhclient3, so that part of the above looks ok now.  Also, I googled it and other people have said that the statement with dhclient3 is a false positive.

Any ideas on that and the other output above?

Going back a few pages in this forum will get you discusssion on similar topics involving the software you are using. I hope you looked at them.

You are better off not using chkrootkit at all. It will discover nothing of any consequence even if it wasn't inclined to mislead the unwary. Purge it.

---

### Post by Rubi1200 on 2010-11-14
> **brian_p said:**
> Going back a few pages in this forum will get you discusssion on similar topics involving the software you are using. I hope you looked at them.

You are better off not using chkrootkit at all. It will discover nothing of any consequence even if it wasn't inclined to mislead the unwary. Purge it.
+1

Just to add a couple of points:

1. deleting stuff without knowing what you are doing is likely to lead to a corrupted and unstable system

2. if you are interested in keeping your system secure, read the security stickies at the top of the forum

---

### Post by toolmania1 on 2010-11-15
Security Stickies
Wow, those are informative.  I started reading them last night.  Some of them seem to apply to servers for companies.  But, I am learning a few things that I can apply to my pc.  I did install SELinux instead of AppArmor.  I just left defaults.  Until I learn more about both so I can make a decision, I am going to leave them.Or, can both be installed side by side?

---

