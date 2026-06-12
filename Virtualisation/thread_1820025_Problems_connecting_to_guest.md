---
title: "Problems connecting to guest"
date: 2011-08-07
forum: Virtualisation
---

### Post by ennaN on 2011-08-07
I'm trying to get KVM running, but I can't seem to connect to my guests. When installing ubuntu server (11.04) I auto-installed KVM (there is an option in the installer) and haven't changed the settings specifically from the default. Using _[the manual]("https://help.ubuntu.com/community/KVM/Managing")_ I can create guests, and they seem to be able to run. I can't shut them down but that's probably because the guest doesn't have ACPI installed by default: I can probably fix that when I can connect to the guest.

As far as I can tell there are several ways to connect to a running guest:

**Console.**
_[The console manual]("https://help.ubuntu.com/community/KVM/Access")_ starts with 

> First, we need to configure a serial console in the guest

But my problem is I don't have access to the guest. So I've discarded this as an option for now.

**Default ssh**
The problem is that I can't get the network to run. I'd rather get (console) access to run, and check the settings from there on the guest. 

But anyway: the default install set me up with a bridge that I don't really know how to deal with: (`ifconfig`)

>     virbr0    Link encap:Ethernet  HWaddr 00:00:00:00:00:00
              inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0

my normal network runs on `192.168.1` 

If I want direct access to my netwerk, should I somehow connect to this bridge using these options in the builder? (from the manual). I'm not sure what to do with the bridge though. Connecting to my normal network would be great, but that doens't seem to work?

>     ubuntu-vm-builder kvm hardy \
                  --ip 192.168.0.12 \
                  --mask 255.255.255.0 \
                  --net 192.168.0.0 \
                  --bcast 192.168.0.255 \
                  --gw 192.168.0.1 \
                  --dns 192.168.0.1 \

**Using VNC**
I'm running on a headless server, so I can't connect from that machine using some sort of VNC as some FAQ's seem to suggest. I don't know if doing port-forwarding should help, but that only leads to time-out in my case.

Can anyone help me connect to the guest?

---

