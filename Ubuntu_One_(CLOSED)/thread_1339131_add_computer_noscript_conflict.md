---
title: "add computer noscript conflict"
date: 2009-11-27
forum: Ubuntu One (CLOSED)
---

### Post by feydrutha on 2009-11-27
Just an issue I experienced when setting up ubuntu one on a computer with Firefox and noscript installed. 

When you get to the point of adding your computer to the ubuntu one account, get to the ubuntu one web page for adding the computer, and press the button to add the computer, up-to-date versions of noscript will block the add command even if the ubuntu one website is authorized to run scripts (is whitelisted).

The reason is the ABE tool that is part of noscript, which does not allow the remote website to instruct the browser to access a local website (at localhost, on the port used by ubuntu one). This is a reasonable policy, but we want to allow this in this specific case to get ubuntu one to work.

To do this, just go to the noscript prefernces, ABE tab, and change the system rules from:

# Prevent Internet sites from requesting LAN resources.
Site LOCAL
Accept from LOCAL
Deny

To:

# Prevent Internet sites from requesting LAN resources.
Site LOCAL
Accept from LOCAL
Accept from one.ubuntu.com
Deny

We have basically whitelisted the ubuntu one website with respect to this rule.

Of course, another alternative might be to simply disable the noscript plugin while you are adding the computer, and enable it again later.

---

### Post by wilee-nilee on 2009-11-27
I have to disable the abe to get a redirect at my college to get to the main login once to put it either in bookmarks, but I use the speed dial addon. Noscript is an excellent tool but it takes a bit of working with to understand it. I also use the tooblar buttons add on to put the per-session allow and remove in the FF panel

---

### Post by Rytron on 2010-11-03
Thank you feydrutha. I just encountered this problem. Cheers. :)

---

