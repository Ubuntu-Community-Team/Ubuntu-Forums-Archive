---
title: "LXC Interest..what version Ubuntu?"
date: 2014-06-23
forum: Virtualisation
---

### Post by rayj00 on 2014-06-23
I am interested in learning about LXC.

My question is which version of Ubuntu would I be better off using?
Could I use a Desktop version rather than a server version?

Apparently there is a web app for doing LXC maintenance but server
versions do not come with a desktop.

Thanks,

Ray

---

### Post by rayj00 on 2014-07-02
> **rayj00 said:**
> I am interested in learning about LXC.

My question is which version of Ubuntu would I be better off using?
Could I use a Desktop version rather than a server version?

Apparently there is a web app for doing LXC maintenance but server
versions do not come with a desktop.

Thanks,

Ray

So no one has a comment on what flavor of Ubuntu is the best for running LXC?

---

### Post by TheFu on 2014-07-05
I don't know.  LXC is non-trivial compared to other VM techniques (IMHO). The "cool kids" are playing with Docker these days when KVM, Xen aren't desired.  If you need production ready **containers/jails**, I'd lean towards openvz. It has 4+ yrs of history, production use, lots of companies using it.

If complex firewalls or non-standard networking is needed, I'd avoid jails/containers.  These are not fully separate VMs, regardless of what other people say. I've seen some real marketing statements propagated by developers as if it were the truth.

Lacking all hands-on knowledge about LXC, I'd be inclined to use the most recent LTS release - 14.04.  I know that KVM-Spice is vastly improved in that release.

So ... that isn't the response you wanted.

BTW, a nice how-to for Docker: [http://www.howtoforge.com/manage-linux-containers-with-docker-on-ubuntu](http://www.howtoforge.com/manage-linux-containers-with-docker-on-ubuntu) was just published.

---

