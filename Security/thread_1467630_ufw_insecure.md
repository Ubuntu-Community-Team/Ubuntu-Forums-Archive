---
title: "ufw insecure"
date: 2010-04-30
forum: Security
---

### Post by jasonmchristos on 2010-04-30
I have been using ufw and I found an issue I'm not sure if this is considered a bug or not. Here is the issue:  Say I have an active connection on port 111111  I issue the command 'sudo ufw deny 111111' then 'sudo ufw reload'  I would think this would intercept this port and block the connection. However, using netstat -tau I find that the connection is still active.  If this is not a bug and is the correct operation of ufw let it be noted that I dislike this, so would someone please tell me which command to issue to close the active connection after reloading the firewall?

---

### Post by cariboo on 2010-04-30
What have you got connecting on such a high port? That isn't even a standard port.

---

### Post by bodhi.zazen on 2010-04-30
By default ufw does not manage outbound connections.

You can manage outbound connections if you wish , the syntax is a bit different :

[http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)


If the connection is inbound stop the connection and you will not be able to re-establish it.

This is because UFW blocks NEW connections and your connection is ESTABLISHED

---

### Post by jasonmchristos on 2010-05-01
> **cariboo907 said:**
> What have you got connecting on such a high port? That isn't even a standard port.

 It was hypothetical.

---

### Post by jasonmchristos on 2010-05-01
> **bodhi.zazen said:**
> By default ufw does not manage outbound connections.

You can manage outbound connections if you wish , the syntax is a bit different :

[http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)


If the connection is inbound stop the connection and you will not be able to re-establish it.

This is because UFW blocks NEW connections and your connection is ESTABLISHED

 Thanks for the link I already figured out most of the syntax for ufw and even how to block ping requests which isn't included in the syntax. So you verified that this is not a bug but the correct way ufw functions. I guess if ufw doesnt include blocking ping I shouldn't have expected it to close ESTABLISHED connections that violate rules. Could you please tell me if there is a command to intercept and close an ESTABLISHED connection this way I do not have to bring down my network before the ufw firewall rules will apply.

---

