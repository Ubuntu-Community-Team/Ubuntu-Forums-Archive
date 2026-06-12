---
title: "configuring iptables in ubuntu server using webmin"
date: 2008-10-26
forum: Server Platforms
---

### Post by jennifer.ayag on 2008-10-26
Hello Guys!

I am new here in ubuntu forums. I not that familiar with ubuntu because i just used it since my boss decided to change from windows to ubuntu. My boss told me to set up a firewall for our network.

I made an ubuntu server..installed with webmin, squid. my squid is using port 8000. I'm configuring the iptables right now but i'm having some problems... Can anyone help me please? :(:(:(

[B]this is what my boss wants:

DROP all the incoming packets and start allowing the ports that are only needed by our network.
DROP all the outgoing packets and start allowing the ports that are only needed by our network.
[/B]

---

### Post by lykwydchykyn on 2008-10-27
What's the problem? 
You set default action to drop, then you add rules to allow on ports that you want.

---

### Post by ciscosurfer on 2008-10-27
Hello jennifer.ayag,

I would like to point you to [this IPTables HowTo]("https://help.ubuntu.com/community/IptablesHowTo") that was written by Ubuntu community members.

You can also issue this command in a terminal```
man iptables
```If you'd rather read it online, [you can go here]("http://linux.die.net/man/8/iptables").

Hope this helps get you started.  Good luck!

---

### Post by jennifer.ayag on 2008-10-27
> **lykwydchykyn said:**
> What's the problem? 
You set default action to drop, then you add rules to allow on ports that you want.

should i change the default action of FORWARD AND OUTPUT chain?

---

### Post by jennifer.ayag on 2008-10-27
> **ciscosurfer said:**
> Hello jennifer.ayag,

I would like to point you to [this IPTables HowTo]("https://help.ubuntu.com/community/IptablesHowTo") that was written by Ubuntu community members.

You can also issue this command in a terminal```
man iptables
```If you'd rather read it online, [you can go here]("http://linux.die.net/man/8/iptables").

Hope this helps get you started.  Good luck!

Thank you!i'll read this and will keep you posted on what's the output....Hope i can do it.:)

---

### Post by jennifer.ayag on 2008-10-27
ciscosurfer, i followed the commands in the IPTables HowTo but still i can't browse the net..i can even log in to webmin...is there any HowTo that pertains to use webmin in configuring the IPTables? 

Thanks.

---

### Post by ciscosurfer on 2008-10-27
I don't know much about webmin to be honest.  I suppose you can check the docs on the [webmin website here]("http://www.webmin.com/docs.html").  I noticed there's also a [community page]("http://www.webmin.com/community.html"), and a [webmin forum hosted by sourceforge]("http://sourceforge.net/forum/forum.php?forum_id=600155").  That forum may be your best bet.  At the very least, basic fundamentals of using and manipulating iptables should be learned/known beforehand, imo.

Edit: So I went to the webmin forums hosted by sourceforge, I searched for iptables, sorted the entries by relevance and by date, and came up with a post/thread that [pointed back here]("http://ubuntuforums.org/showthread.php?p=5887413") :-)  Perhaps it will be helpful.  For more data on this topic, you may also want to search Ubuntu Forums in greater depth for other posts relevant to iptables and webmin.

---

