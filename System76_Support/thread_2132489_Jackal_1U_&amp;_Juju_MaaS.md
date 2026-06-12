---
title: "Jackal 1U &amp; Juju MaaS"
date: 2013-04-05
forum: System76 Support
---

### Post by Conzar on 2013-04-05
I am proposing to my company a small Juju/MaaS/Openstack private cloud environment with the option to expand it later.  According to [this]("https://help.ubuntu.com/community/UbuntuCloudInfrastructure") documentation, the minimum required number of "machines" is 6 if using juju-jitsu.  Is this number inclusive for the entire juju/MaaS/Openstack environment?  

So would 6 Jackal 1U's be sufficient for a small private cloud?

Also, we have an IS5K SAN (fibre channel).  Would we need fibre channel cards for all the Jackal's (the Jackal only has 1 expansion slot that is consumed by the LSC card ... seems like that might be a problem)?

---

### Post by isantop on 2013-04-05
6 Jackals would work great for a small private cloud.

As for Fibre channel, you could go with the Jackal Pro, which offers an additional expansion slot over the standard Jackal.

---

