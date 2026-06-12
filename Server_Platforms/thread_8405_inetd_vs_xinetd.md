---
title: "inetd vs xinetd"
date: 2004-12-17
forum: Server Platforms
---

### Post by luboshiq on 2004-12-17
Why ububtu uses inetd? I think xinetd is newer, much easier to configure. Is there a way how to replace inetd with xinetd?

---

### Post by kimes on 2005-07-16
[QUOTE=luboshiq]Why ububtu uses inetd? I think xinetd is newer, much easier to configure. Is there a way how to replace inetd with xinetd?[/QUOTE]
 I also want to know this..
any ideas?

---

### Post by luxxing2000 on 2005-10-19
ubuntu has both of them.
You can choose what you want to install

---

### Post by JLuc_yvr on 2008-03-25
I kinda agree with the OP and I've run into the inetd vs xinetd when trying to configure Samba.

When trying to figure out the reason for not having xinetd I then found this post, and I don't think the answers were very useful.  

Yes, xinetd is in synaptic and yes, both can be installed, but why was inetd installed in the first place, instead of xinetd?  Technical reason like stability?


FWIW, here's a post on a thread that seems to indicate a licensing issue.

[https://lists.ubuntu.com/archives/ubuntu-motu/2007-June/001776.html](https://lists.ubuntu.com/archives/ubuntu-motu/2007-June/001776.html)

I got no idea if the license issue is for real or not, just adding a bit of background info to the OP's question.

I'll get Samba set up on inetd first and will then switch to xinetd instead because I do like xinetd option like limiting allowed IPs.

---

