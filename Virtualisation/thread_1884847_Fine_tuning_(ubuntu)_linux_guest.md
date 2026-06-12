---
title: "Fine tuning (ubuntu) linux guest"
date: 2011-11-22
forum: Virtualisation
---

### Post by orrorin on 2011-11-22
Hello,

I'm running a Ubuntu 11.10 guest in VirtualBox on a Windows 7 host. I'm looking for any tips on how to fine tune the linux guest for performance in this setup. In particular, I'm looking for information on whether I should allow my machine to maintain high cache memory or drop it (using the drop_cache sysctl). On a related note, should the swappiness be set to a high or low value.

Any tidbits on how VirtualBox virtualizes the RAM for usage by guest would be very useful. It doesn't look like VBox allocates all the RAM configured in the guest VM spec. So, what is the policy for managing the virtual RAM?

Thanks.

---

