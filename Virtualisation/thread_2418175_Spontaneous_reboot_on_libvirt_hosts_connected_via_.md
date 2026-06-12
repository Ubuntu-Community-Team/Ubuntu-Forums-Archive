---
title: "Spontaneous reboot on libvirt hosts connected via ssh to virt-manager."
date: 2019-05-02
forum: Virtualisation
---

### Post by tdsherman on 2019-05-02
We rely heavily on ubuntu libvirt hosts and had a massive failure today I'm attempting to analyze.

At approximately 11:15 this morning, users lost connection to all production virtual machines. Virt-manager simultaneously lost its connection to all production vm hosts. Attempting to reconnect via virt-manager produced a connection error and the servers were then physically verified to be on. An ssh connection to one of the failed servers was successful at which point it became apparent that they had rebooted, and sshd had not yet started on earlier virt-manager connection attempts. Subsequent attempts to connect virt-manager were successful and all virtual machines were restarted.

We have vm hosts on multiple networks, with different accounts and passwords used to access them. Other systems on the same breakers and universal power supplies as the affected systems were unaffected. Critically, our test system, which runs virt-manager itself, was unaffected. We have systems running both 18.04 and 16.04, both were affected.

The only common factor in the failed systems is that they had an active ssh connection to virt-manager on a different system. auth.log showed no other active connections at the time and no anomalous connections going back as far as we keep logs (90 days). System logs only show routine messages and a normal reboot, though our logging is largely set to defaults levels of verbosity.

Does anyone know of any bugs in virt-manage that might cause something like this? Failing that, what logging needs to be enabled / increased in verbosity to better capture the failure should it happen again?

Thanks,
Terry

---

### Post by tdsherman on 2019-05-03
It must be power related - further checking reveals a couple of other systems suffered a reboot simultaneously - they're non critical so their failure went unnoticed at first. Said systems are unrelated to our virtualization environments and don't have any software in common.

Sorry for the intrusion. Y'all have a good day.

---

