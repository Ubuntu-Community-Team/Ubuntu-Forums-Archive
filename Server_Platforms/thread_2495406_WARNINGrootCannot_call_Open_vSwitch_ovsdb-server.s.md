---
title: "WARNING:root:Cannot call Open vSwitch: ovsdb-server.service is not running."
date: 2024-02-17
forum: Server Platforms
---

### Post by Heeter on 2024-02-17
Hi all,


getting this error when doing a netplan apply command:
```

WARNING:root:Cannot call Open vSwitch: ovsdb-server.service is not running.

```

Seeing so many different results on internet searches for this, thought that i would ask here for a better solution or Ubuntu22LTS

Regards

---

### Post by MAFoElffen on 2024-02-17
It's just a warning that can be ignored. We reported it as a bug... not resolved (yet). But like I said, can be ignored.

They are still working on the patch: [https://bugs.launchpad.net/ubuntu/+source/netplan.io/+bug/2041727](https://bugs.launchpad.net/ubuntu/+source/netplan.io/+bug/2041727)

Maybe you could please go there and add yourself to the Bug Report via: (Link in Upper Left) "Does this affect you?" > "Yes It Affects Me"... Doing that helps add weight to it showing them there are multiple users that are affected, and it still needs to be resolved.

---

### Post by anjogu254 on 2024-05-08
I got the error on my Ubuntu 22.04 server when configuring a static IP to it.

This is a bug which has already been posted here([https://bugs.launchpad.net/ubuntu/+source/netplan.io/+bug/2041727](https://bugs.launchpad.net/ubuntu/+source/netplan.io/+bug/2041727)). However in as much as it is a Warning!, ignoring it was not sufficient.

To do solve the issue on my end, I did a system upgrade;


  ***sudo apt upgrade***


after this I installed openvswitch-switch-dpdk 

[B][I]
    sudo apt install openvswitch-switch-dpdk[/I][/B]


after I applied the netplan configuration using;


   ***sudo netplan apply***


and the issue was resolved. Hope this solution works for you!
If it does drop me a vote

---

### Post by MAFoElffen on 2024-05-08
Welcome to Ubuntu Forums!

LOL. Did you read my Post#2, and check the date of it? It was answered back 3 months ago... 

Be a bit careful that the Mod's might give you a warning about resurrecting 'old threads' that have been answered long ago... I appreciatively will take this as "an update", that the Bug Report I referred to (back then) has been resolved now.

Thank you for the update... I applaud you chipping in to help other Users. That is how we contribute to the community. Looking forward to hearing more from you, helping others. Keep up the good work.

---

### Post by j0nny55555 on 2024-05-25
I might be worth mentioning, that a much smaller install of
`apt install openvswitch-switch`

Gets rid of the error message as well, bug or no bug

---

### Post by MAFoElffen on 2024-05-25
Even though a dead thread, I feel compelled to answer what you just did... Un-needingly. And your advice to others on correcting that.

But that warning is not needed if you don't use openvswitch. That is what that bug report is all about and the point of that when we filed it... That "warning" gives the user a false sense that something is wrong with their system, when in reality, there isn't...

Openvswitch allows hypervisors to virtualize the networking layer. You don't need that if you don't have a KVM based hypervisor and are not virtualizing network layers... 

That gets rid of the warning, but the code shouldn't be asking for that, if not installed. Should only give that warning it installed and the service cannot be restarted... It is not installed as a default. The code should have *first* looked if the service was there & enabled before even trying to restart the non-existing service (that was not there), that triggered that warning. There was a bigger underlying problem. Not just that the warning would come up.

Otherwise, by installing it (just to not be bothered by the warning),  you are running a service that is taking up resources, that is not being  used, and is doing nothing.

Did you join the Bug Report as "Also Affected"? That would push the maintainers that it is still coming up, and that they need to correct it... Make sense? Until then, just ignore it as harmless until it is corrected in the underlying code.

---

