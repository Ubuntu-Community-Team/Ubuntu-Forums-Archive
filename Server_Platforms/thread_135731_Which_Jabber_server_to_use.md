---
title: "Which Jabber server to use?"
date: 2006-02-24
forum: Server Platforms
---

### Post by Scirious on 2006-02-24
Friends, I'm in charge of setting up an internal instant messaging service in my company. From what I've searche I came up with two options, wich are:

[Wildfire](http://www.jivesoftware.org/wildfire/)

[ejabbered](http://ejabberd.jabber.ru/)

Anyone here has experience with any of these? What can you tell me aboute them?

Thanks for your support,
Scirious

---

### Post by earobinson on 2006-02-24
you could run your own jabber server, or just use the google talk one, its really nice IMO

---

### Post by Scirious on 2006-02-24
Here ehre I work all outsider services are blocked. I have to run a server of my own!

Scirious.

---

### Post by majikstreet on 2006-02-24
[QUOTE=earobinson]you could run your own jabber server, or just use the google talk one, its really nice IMO[/QUOTE]
He means which of those two is best... those are packages for jabber servers..

My advice, I would maybe try both? I've heard a little bit about ejabberd being good though.

---

### Post by earobinson on 2006-02-24
It just seems to me like if your doing it for the company you could get them to let u use gtalk or jabber or something.

Also: [http://www.jabber.org/software/servers.shtml](http://www.jabber.org/software/servers.shtml)

---

### Post by KittyChunk on 2006-06-01
Large commercial organisations tend to get pretty bent out of shape about using third-party internet based services for internal communication purposes - sometimes the best way to get around that is simply to run an IM server on the internal network. That way the management retains the illusion of information security and control, and everyone's happy :-)

Scirious, I can recommend the ejabberd server as being particularly easy to set up and administer, provided all you want is jabber. If you want it to do more fancy stuff like MSN etc transports, it can get a little hairy though.

---

### Post by bait on 2006-06-01
[QUOTE=Scirious]Friends, I'm in charge of setting up an internal instant messaging service in my company. From what I've searche I came up with two options, wich are:

[Wildfire](http://www.jivesoftware.org/wildfire/)

[ejabbered](http://ejabberd.jabber.ru/)

Anyone here has experience with any of these? What can you tell me aboute them?

Thanks for your support,
Scirious[/QUOTE]

 Ejabberd has a bit more of a general learning curve, but has better load handling.

 Wildfire is easier to configure and manage, but tends to have higher load.

---

### Post by Randomskk on 2006-06-02
Wildfire has a LOT more funky options and a much better web interface, plus you can get plugins that can generate nice graphs and such for you.
However, the load on my server with it running was waay too high, while eJabberd is fine.
I'd go with Wildfire if the server can handle it.

---

### Post by porque on 2006-06-05
Are these graphs as nice and powerful as these?:
[http://sander.dontexist.org/ejabberd/statsdx.png](http://sander.dontexist.org/ejabberd/statsdx.png)

:cool:

---

