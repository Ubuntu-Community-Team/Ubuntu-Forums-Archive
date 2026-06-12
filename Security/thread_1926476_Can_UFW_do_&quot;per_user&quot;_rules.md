---
title: "Can UFW do &quot;per user&quot; rules?"
date: 2012-02-16
forum: Security
---

### Post by HammerHed on 2012-02-16
I want to setup a per user rule for blocking outgoing traffic for a specific user on Ubuntu 11.04

So basically BLOCK all outgoing traffic only for that user, not main user accout on that machine.

Is this possible using UFW, I cannot find an answer on the web.

---

### Post by Lars Noodén on 2012-02-16
You can do that working with IPTables directly instead.

Here is a general guide:

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

But you'll want to dig around in the [manual page for IP Tables](http://manpages.ubuntu.com/manpages/oneiric/en/man8/iptables.8.html) for details.

---

### Post by HammerHed on 2012-02-16
Tx Lars, I was hoping it could be a bit easier than iptables. [http://ubuntuforums.org/images/smilies/icon_confused.gif](http://ubuntuforums.org/images/smilies/icon_confused.gif)

Will give it a go

---

### Post by Lars Noodén on 2012-02-16
It's not too hard once you figure it out.  It's just that there's a shortage of up to date tutorials and howtos.  Much has changed since the old ones were first written and they are incomplete and out of date.

---

### Post by kevdog on 2012-02-16
Good page using the match directive to filter against uid, username, gid, groupname, mac address etc.
[http://www.cyberciti.biz/tips/block-outgoing-network-access-for-a-single-user-from-my-server-using-iptables.html](http://www.cyberciti.biz/tips/block-outgoing-network-access-for-a-single-user-from-my-server-using-iptables.html)

---

### Post by HammerHed on 2012-02-17
Tx KevDog that looks quite useful.

---

