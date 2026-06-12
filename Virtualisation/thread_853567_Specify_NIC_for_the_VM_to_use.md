---
title: "Specify NIC for the VM to use"
date: 2008-07-08
forum: Virtualisation
---

### Post by lyric0n on 2008-07-08
Hello,

I am running Xubuntu w/ KVM to handle my VM sessions. I am able to get the guests I want up and running without an issue, but (due to the configuration of our network), each guest must talk only to a specific NIC in the system. Is this possible to force each guest to only see a specific NIC? How would I go about configuring this?

Thanks,
Chris

---

### Post by igwk on 2008-07-09
I haven't tried doing this myself, but you should be able to setup your VM to use a TAP network interface that is bridged to the actual ethernet NIC on your host.  Then for each VM session, you start it with the appropriate -net tap device.

---

### Post by lyric0n on 2008-07-11
Hi igwk,

That is what I have tried, but I am unable to pass packets from the VM out through the bridge. Does anyone know what I should configure as my IP/gateway/etc for the VM?

Thanks,
Chris

---

