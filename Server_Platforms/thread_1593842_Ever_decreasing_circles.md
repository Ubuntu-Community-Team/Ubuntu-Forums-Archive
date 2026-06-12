---
title: "Ever decreasing circles"
date: 2010-10-11
forum: Server Platforms
---

### Post by Trunkles on 2010-10-11
[SIZE=2]Hi folks.

Ok... I admit it... I'm lost. I've been trying to get a working server installation with little success. Wailing and gnashing of teeth has occurred. Auto-cranialdepilation (pulling my hair out) is in full swing and the intravenous caffeine is running out.

My target is a running Ubuntu server with an e-mail server, Samba and the ability to host a few domains for friends and a couple of volunteer organisiations. All non-profit stuff. For the hosting I need something like cpanel but not actual cpanel; you seen the price of it!

I've installed postfix from the tutorial at [http://www.postfix-tutorial.com/](http://www.postfix-tutorial.com/). I think I've got ssh working, in as much as I can putty into the server. BTW, the server is physically next to my desk.

Can I get email or webmin working? Can I hell! Arrrgh! :cry:

So... is there any kind soul out there who knows what they're doing who would be prepared to spend a bit of time puttyed in to the server helping me set the freaking thing up?

Oh yes. I'm a sort of noob old hand. I still have a copy of the first edition of K&R and I had the pleasure of owning a Sun 3/260 for some years; wonderful machine! So I can ```
rm -rf /*
```[/SIZE][SIZE=2] quite happily and know that xnix doesn't know how to make love. Trouble is... SunOS 4.1.1 and Solaris 1 are more my era. :biggrin:

Thank you all for reading my overly verbose request and I'll be eternally grateful if someone can help me.

Pleading on knees and licking boots here. :redface:

Simon.
[/SIZE]

---

### Post by tgalati4 on 2010-10-11
What is the hardware that you are running?  I would recommend Hardy server edition to start with.  It is a long term support (LTS) release and should get security updates for the next five years.

For admin chores, simply use ssh to log into your box and perform whatever maintenance is required.  Webmin is OK, but it is not as secure as using ssh with shared keys for remote admin.  With an appropriate router/firewall, I suppose webmin would be OK for LAN use.

What specific problems are you having?

---

### Post by Trunkles on 2010-10-11
The hardware is a fairly basic PC. It doesn't really need much more. Pentium 2.8, 1DB and a 40GB disk.

The version I have installed is 10.4.1 - Lucid Lynx which has LTS until 2015. Hardy LTS ceases in Apr 2013 so I'd sorta rather stick with Lucid.

My problem is more getting things to work. Postfix, Apache  and Courier are installed and, I think, configured. Or, more to the point *mis*-configured. :)

The need for webmin is so that people have control of their own domain/email. Of course, it doesn't have to be webmin. Plenty of others but I don't know which would be the one to go for. I know one of them (can't remember which) will work but *not* for me on the local network.

As I said, I'm not without knowledge, just that the knowledge is ancient now. I selected Ubuntu 'cos others recommended it and I didn't want to self-infect with *Redmonditis Insipidus*. :mrgreen:

Simon.

---

### Post by hkphooey on 2010-10-12
Sounds as though you might like to use this kind of thing
       [http://www.ispconfig.org/](http://www.ispconfig.org/)

And here's an article which steps you through the setup
       [http://www.howtoforge.com/perfect-server-debian-lenny-ispconfig3](http://www.howtoforge.com/perfect-server-debian-lenny-ispconfig3)

I'd actually uninstall webmail, apache postfix etc before you start and step through from the beginning, so that your previous config doesn't break things.

---

