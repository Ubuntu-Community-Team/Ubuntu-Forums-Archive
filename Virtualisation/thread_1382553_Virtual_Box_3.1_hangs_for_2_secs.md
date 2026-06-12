---
title: "Virtual Box 3.1 hangs for 2 secs"
date: 2010-01-16
forum: Virtualisation
---

### Post by fernandoch on 2010-01-16
Hello,

I have installed Virtual Box 3.1. When I have a virtual machine running, it hangs for 2 secs every 30 or 40 secs.

Any clues about what could be wrong?

---

### Post by fouadatmeh on 2010-01-16
Hello,
-Are the guest additions installed?
-Are you using more than onc cpu for the guest? also make sure that VT-x/AMD-V and Nested paging are enabled.
-Try disabling extra devices for the guest machine (audio, network.. etc) and see if this makes any difference.

---

### Post by fernandoch on 2010-03-27
I am still having the same problem. I am using Karmic as host and guest. I am not able to use the guest as it hangs every 10 seconds or so.

I tried Lucyd beta1 as guest and it works well even without the virtualbox addons. I would like to make Karmic as a guest work too :(

I found this ticket

[http://www.virtualbox.org/ticket/5501](http://www.virtualbox.org/ticket/5501)

But I am not sure of that because it is working fine with Lucyd.

Any clues?

---

### Post by fernandoch on 2010-03-27
Right now I am having the same problem with Lucyd beta1 as a guest :(

---

