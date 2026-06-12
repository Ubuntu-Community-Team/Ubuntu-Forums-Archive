---
title: "OpenVNet, LXC and OpenVirtualSwitch (OVS)"
date: 2015-08-31
forum: Virtualisation
---

### Post by bmullan2 on 2015-08-31
**OpenVNet, OVS and LXC...**

By  default LXC utilizes the lxcbr0 bridge. You can always define your own  bridge if/when you want to work on more advanced networking.  Rather than using a bridge though many people today are working with OpenVirtualSwitch (OVS).

They  are doing so because of many reasons, some include the advantages of a  "switch" versus a "bridge" but also because of SDN (software defined  networking) where a new networking paradigm is becoming increasingly  important.

In SDN the OpenFlow (OF) protocol is utilized along  with an SDN controller such as OpenDayLight (ODL), OpenContrail, etc. to  implement a programmable network using OVS switches.

OVS is also heavily utilized with OpenStack in DataCenter (DC) environments.

This OpenVNet Installation Guide: [https://github.com/axsh/openvnet/blob/develop/docs/content/installation.md](https://github.com/axsh/openvnet/blob/develop/docs/content/installation.md)  provides a very good explanation of how to configure your LXC containers to use OVS.&#65279;

---

