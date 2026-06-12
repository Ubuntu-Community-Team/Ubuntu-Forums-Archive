---
title: "Dual Ubuntu Servers - Data replicaiton over the internet"
date: 2013-03-14
forum: Server Platforms
---

### Post by scudelari on 2013-03-14
Hello everyone,

I have two servers both connected to the internet. Both internet points have dyndns so that the dynamic IP is taken care of.

What I want to have is basically a completely and automatically replicated set of data.  Basically, I'd like to have the same data completely mirrored. What happens on one side happens to the other as well and vice versa.

Is that feasible? Is there an application for such thing in Linux? I am not a noob, therefore I just need the name of such service so that I might get started and go through pages of documentation.

I appreciate your help.

---

### Post by lingpanda on 2013-03-15
> **scudelari said:**
> Hello everyone,

I have two servers both connected to the internet. Both internet points have dyndns so that the dynamic IP is taken care of.

What I want to have is basically a completely and automatically replicated set of data.  Basically, I'd like to have the same data completely mirrored. What happens on one side happens to the other as well and vice versa.

Is that feasible? Is there an application for such thing in Linux? I am not a noob, therefore I just need the name of such service so that I might get started and go through pages of documentation.

I appreciate your help.

[http://rsync.samba.org/](http://rsync.samba.org/)

---

### Post by papibe on 2013-03-16
Hi scudelari. Welcome to the forums.

As lingpanda pointed it out, rsync would help you with that. Take a look at this [tutorial]("https://help.ubuntu.com/community/rsync"), and let us know how it goes.

Regards.

---

