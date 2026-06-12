---
title: "cannot start firewall [firestarter] vmnet1 is not ready"
date: 2008-05-04
forum: Virtualisation
---

### Post by philphil on 2008-05-04
Hi,

I'm getting this error when I try to run Firestarter in Hardy Heron...```
Failed to start the firewall
The device vmnet1 is not ready.  Please check your network device settings and make sure your internet connection is active
```

1.  Yes, my Internet connection is active.  

2.  Which network device settings should I check and how should I check them?

3.  I had VMware installed a while ago (though had to remove it because it wouldn't work with Hardy, no prob, I don't miss it) and I'm 100% sure that this is what installed vmnet1 (as well as vmnet0 and vmnet8) but I don't know how to remove these things (network adapters?)

4.  Please help!

Edit:  I forgot to mention that I already tried to follow the instructions for "Removing a Host-only or NAT Adapter on a Linux Host"  from this site: [http://www.vmware.com/support/gsx25/doc/network_change_disable_rem_gsx.html](http://www.vmware.com/support/gsx25/doc/network_change_disable_rem_gsx.html) which recommends running vmware-config.pl though unfortunately this crashes halfway through before I get to the question about removing vmnet thingies

Edit #2: Ok, I've just unticked the box that says "Enable internet connection sharing" in the preferences of Firestarter and it seems to be running fine but I'd still like to know how to get rid of vmnet1

Thanks!

---

### Post by kansasnoob on 2008-05-04
Well, I don't understand this yet.

DO NOT do what I've done based solely on what I say!

Hardy comes with ufw installed by default, but I think ufw is disabled by default!

I think iptables is still working as always by default (all ports closed).

Now, I must occasionally open ports by choice on my network and since I'm used to the Firestarter gui I "disabled" the ufw cli (do not remove ufw in synaptic because it will remove NEEDED components) and I installed Firestarter, basically giving myself a 7.10 firewall interface.

Suffice it to say I'm dissatisfied and confused by the ufw cli. Out of the box we knew that iptables was working with no action on a basic desktop. Is that still true?

I need to get off my butt and run some tests.

You can enable or disable ufw by simply:

sudo ufw enable

or:

sudo ufw disable

or, if you know what you want to allow, you can:
sudo ufw allow "whatever"

I did at one point figure out how to have ufw log activity, but I still decided to go with Firestarter. I think Ubuntu avoids a gui like Firestarter for fear of users opening ports they shouldn't.

And there's also a reason why it's a bad idea to edit sudoers to have Firestarter start on startup. It's nifty, but not a good idea!

---

