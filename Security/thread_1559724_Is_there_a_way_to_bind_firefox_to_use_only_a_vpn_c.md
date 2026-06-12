---
title: "Is there a way to bind firefox to use only a vpn connection?"
date: 2010-08-23
forum: Security
---

### Post by dogdo on 2010-08-23
I basically have a vpn that i use to browse the net but it sometime goes down-is there a way to stop my real ip address from being used during that downtime?

---

### Post by wacky_sung on 2010-08-24
Since you using a FREE services and why you don't go for free web based proxy.Below are a few links for you.

[https://launchwebs.org/](https://launchwebs.org/)
[https://twolulu.com/](https://twolulu.com/)
[https://2unblocksites.com/](https://2unblocksites.com/)
[https://freesslproxy.com/](https://freesslproxy.com/)

FYI there is no such thing known as anonymous but those VPN / Proxy services only protect your privacy.

---

### Post by Agent ME on 2010-08-24
Who said he was using a free service? Would that even make a difference if he was? A web proxy may work for him, but maybe he already has a good vpn service or uses it for other stuff too.

I'm kind of curious about this issue too.

---

### Post by BkkBonanza on 2010-08-24
If you set FF to use a proxy when that proxy fails it won't switch back to another connection.

I usually use ssh as a SOCKS5 proxy with FF and it works very well. It's secure, very easy to do and ssh is already installed anyway. To use it you need a remote ssh server that you can connect to. Often people already have access to that but if not then it's not to hard to work something out. Another nice thing about this method is you can use it for many things like email, torrents etc.

I would expect since you are using vpn then at the remote end you may have use of a ssh server anyway. There are free ssh (shell) accounts around but often they are intermittent or flaky. I've always just used my vps server account but I've also experimented with others. 

For example, it's fairly easy to use Amazon EC2 as a on demand ssh server. It works well and costs around 3 cents/hour using spot pricing. Useful if you don't need a lot of hours, eg. if you sometimes need to browse at a web cafe and need more security.

---

