---
title: "firestarter blocked event"
date: 2008-02-18
forum: Security Discussions
---

### Post by dougleduck on 2008-02-18
I've had this address (below) try random ports several times. I dont know if this is harmless or not, but it's random ports so thought I should find out. It's not a port I'd been using for anything previously (like for torrents).


Time: Feb 18 19:56:06 Source: host86-167-24-30.range86-167.btcentralplus.com Destination: my-laptop.config In IF: eth1 Out IF:  Port: 51073 Length: 1500 ToS: 0x00 Protocol: TCP Service: Unknown

---

### Post by randy78 on 2008-02-18
> **dougleduck said:**
> I've had this address (below) try random ports several times. I dont know if this is harmless or not, but it's random ports so thought I should find out. It's not a port I'd been using for anything previously (like for torrents).


Time: Feb 18 19:56:06 Source: host86-167-24-30.range86-167.btcentralplus.com Destination: my-laptop.config In IF: eth1 Out IF:  Port: 51073 Length: 1500 ToS: 0x00 Protocol: TCP Service: Unknown

Are you in the U.K.?

I looked up btcentralplus and it comes back as an ISP... be careful and stay vigilant!

Check out the report here:
[http://www.ripe.net/whois?form_type=simple&full_query_string=&searchtext=86.167.24.30&do_search=Search](http://www.ripe.net/whois?form_type=simple&full_query_string=&searchtext=86.167.24.30&do_search=Search)

---

### Post by p_quarles on 2008-02-19
Bots and scriptkiddies will scan random ports, and there is absolutely nothing you can do about that if you wish to stay networked. Yes, many of them will be malicious, and a tiny minority of them might even be dangerous to *nix systems -- though most of them are scanning for Windows vulnerabilities.

Worrying about individual addresses is a good way to lose sleep without accomplishing anything. The best thing to do is to follow good security practices: 1) Don't run server software unless it's necessary, and if it is necessary, learn how to secure it; 2) Make sure that any and all passwords that grant root access are good.

The sticky threads at the top of this section are both excellent resources for learning more.

---

### Post by dougleduck on 2008-02-19
Don't worry I wont be loosing sleep. I think I'm going to make my $HOME more secure though, for general safety really though.

Thanks for the advice.

---

