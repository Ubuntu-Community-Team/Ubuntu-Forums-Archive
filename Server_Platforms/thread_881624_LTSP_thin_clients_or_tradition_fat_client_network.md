---
title: "LTSP thin clients or tradition fat client network?"
date: 2008-08-06
forum: Server Platforms
---

### Post by anhhung on 2008-08-06
Hi,

I'm working on a proposal that tries to build a computer lab for disadvantaged children in my city. I realize that Edubuntu is the way to go as I'm a Ubuntu user and an open source advocate.

When talking on #hardware at freenode, someone suggested I should not go with thin clients because of the following reasons:

- Kids cannot tweak the OS at all.

- old PCs are more versatile 

- the network may experience sluggishness

However, as far as know, if we invest in a good server, sluggishness can be avoided. And it seems to me that most people would go with thin clients when it comes to setting up such a network.

Some of the benefits of a thin client network I know of are:

- Simpler maintenance.

- lower costs of setup

- resources maximization

- clients can share the power of the server

I haven't seen anyone actually doing this so it is good to learn from your experience.

Thanks.

---

### Post by Aearenda on 2008-08-06
You may get a better response if you pose your questions on the edubuntu-users list at lists.ubuntu.com ([https://lists.ubuntu.com/mailman/listinfo/edubuntu-users](https://lists.ubuntu.com/mailman/listinfo/edubuntu-users)). I'd also suggest looking at the [email]k12osn@redhat.com[/email] list, which is officially about the K12LTSP distro but in practice will be helpful anyway. See the archives and details at [https://www.redhat.com/mailman/listinfo/k12osn](https://www.redhat.com/mailman/listinfo/k12osn).

> - Kids cannot tweak the OS at all.
Surely this is a good thing, unless you are teaching systems management!

> - old PCs are more versatileThere are some things terminals (or old PCs used as terminals) cannot do well - particularly sound recording, and video-intensive activities such as multimedia.

> - the network may experience sluggishness
If you use 1Gbit network cards in the servers and on the uplink from the terminal switch, you should not encounter this unless you try heavy multimedia apps.

> - Simpler maintenance.
- lower costs of setup
- resources maximization
- clients can share the power of the server
I look after three small edubuntu setups (10 terminals each) and can vouch for the truth of these points. There are others on the lists with much larger installations.

---

### Post by anhhung on 2008-08-06
thanks, I'm heading for the mailing list. It's good to know from a real example :)

---

