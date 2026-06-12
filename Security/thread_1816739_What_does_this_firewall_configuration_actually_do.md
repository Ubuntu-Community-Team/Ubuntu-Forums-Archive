---
title: "What does this firewall configuration actually do?"
date: 2011-08-02
forum: Security
---

### Post by arroy_0209 on 2011-08-02
In my ubuntu 10.04 LTS I have set these firewall options:  Firewall enabled Incoming: Deny Outgoing: Allow Preferences: Log option: Enable ufw, gufw logging, set level: low I have not added any rule  Can anybody please explain which incoming matter is actually denied by this firewall and which outgoing matter is being allowed? If everything incoming is denied, then how come I am able to access some website? some "incoming" signal from some other server must reach my computer so that I can see the corresponding webpage. So that kind of thing is not denied, right?  second, is it better to set level to high/full? (low is the default preference.)

---

### Post by bodhi.zazen on 2011-08-02
Those are broad questions and you have some reading ahead of you.

I doubt anyone is going to post detailed explanations to your questions, I suggest you start with :

	[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)
	[http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)
	[http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)

From there you can 

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

Those links should answer your questions. If after reviewing all that you have additional questions, please ask.

---

