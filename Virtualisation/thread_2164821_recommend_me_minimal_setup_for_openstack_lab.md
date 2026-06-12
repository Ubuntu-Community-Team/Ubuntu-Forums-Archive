---
title: "recommend me minimal setup for openstack lab"
date: 2013-08-02
forum: Virtualisation
---

### Post by ikki_72 on 2013-08-02
I'd like to learn more on Openstack to broaden my career on opensource virtualization

What i understood that if I were to used Xen hypervisor, i would need at least 2 hosts. If KVM, I would only need 1 host. Anything else that I should be aware of?

---

### Post by TheFu on 2013-08-03
Since nobody else responded ....

There are 2 openstack meetup groups in my metro area.  Whenever I've attended, there is always someone new trying to learn more. The quick answer is to download and play with devstack on a single machine to get started. After you know more, then you can make better decisions about your wants and needs.  I've never bothered to install devstack - didn't have a spare machine with sufficient CPU and RAM to use.  Came into a Core i7 with 6G machine this month - perfect for an initial devstack test - but I can't touch it until the estate and trust are settled in a few months. ;(

Perhaps asking these questions on OpenStack-specific forums would return more informative responses?

---

### Post by tgalati4 on 2013-08-03
I presume that you have read the guides in [http://devstack.org/](http://devstack.org/).  I'm not sure why you need 2 hosts for Xen.  It depends on what you want to do.  The guide recommends 2GB per VM.  If you want to spend time learning Xen and its virtualization framework, then Xen would be an option.  If you want a simpler installation process (and don't really care about what VM you are running) then KVM would be the way to go.  KVM is in the Ubuntu repositories and requires less hand-holding than building a Xen host.

---

