---
title: "LXC/LXD Help"
date: 2017-06-01
forum: Virtualisation
---

### Post by scojopa on 2017-06-01
I have been going through this for a week now and things are a mess. I have blown away the server numerous times. I need help

Trying to get some containers w/ static IP setup on ubuntu 16.04

I have bridge-utils and zfsutils-linux installed
I configure br0 for bridge no problem. 

run sudo lxd init
assign zfs pool to /dev/sda8
configre networking to use br0

I edited /etc/default/lxd-bridge to add a lxd_dnsmasq.conf file to assign static ip. dhcp-host=container_name,ipv4 address
I sent use_lxd_bridge to "true"
and confirm it is using "br0" as the bridge. 

I run -> sudo service lxd-bridge stop && sudo service lxd-bridge start

ssh connection to my server dies, cant start new ssh tunnel. Have to physically restart machine

I reboot and all looks good. 

I run sudo lxc init ubuntu: *newcontainer*
It pulls down an image and sets it up. 

I check to see if any static ip information has been assinged -> nope

I run sudo lxc info --show-log container and my ssh dies. I have to reboot server. 

And I still cannot get the container to grab the static I assigned in dnsmasq.config file. 

can someone please assist?

---

### Post by scojopa on 2017-06-01
I got the container running w/ static IP. 

But now I cannot ping or ssh to the host. 

I shutdown the container but still cannot connect to host over the network. All the correct ip information is reported back in ifconfig. 

Any clues on what to check for?

---

### Post by simosx on 2017-06-06
Personally I would start off with using the defaults.
The default LXD installation uses "dnsmasq" to assign IPs to the containers, however it remembers those IP assignments so in effect you have static IPs without extra work.
If you can tear everything down and start over, it might clear everything up.
If you want more specialized help, see also [https://discuss.linuxcontainers.org/](https://discuss.linuxcontainers.org/)

---

