---
title: "Neutron Networking is Not Properly Configuring by Conjure-Up"
date: 2017-11-03
forum: Ubuntu Cloud and Juju
---

### Post by muthu883 on 2017-11-03
Hi All,

I am creating the Openstack Private Cloud using MAAS, Juju on Ubuntu 16.04.03. 

I Created two Setups before using Ubuntu Autopilot , that was successful. Autopilot automatically detected the networks( private & public ) from neutron node and successfully allocated floating ips from public networks.

But now canonical removed "landscape" spell from conjure-up ( I am not able to see "landscape" spell ). So I am deploying using "conjure-up openstack" with NovaKVM. But this time it's not detecting the networks from neutron gateway which is having two networks connected( one for private and another for public) . It's creating it's own network ( some 10.x for private and public ) which we did not have.

It's creating networks using the shellscript "/snap/conjure-up/current/spells/openstack-base/steps/share/neutron.sh"

How to make to use our network into the openstack setup?

Could anyone gone through the same issue ?

Where to edit the networks ( which is really we have in our neutron gateway node )?

Thanks

---

### Post by muthu883 on 2017-11-08
Hi All,

Please anyone reply to my post.

Thanks

---

