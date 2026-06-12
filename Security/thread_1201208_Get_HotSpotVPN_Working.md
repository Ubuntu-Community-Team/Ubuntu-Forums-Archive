---
title: "Get HotSpotVPN Working"
date: 2009-06-30
forum: Security
---

### Post by Futurian on 2009-06-30
I just bought the 256 bit version of HotSpotVPN (having been very satisfied with the Mac version in my now-waning Mac days). It turns out that Linux requires some manual work, and the installation instructions that come with the personalized download are rpm oriented, rather than debian oriented.

I had some difficulty with the instructions at first, but found that two very simple (and simplifying) changes got it working. So, in case anyone else buys HotSpotVPN and can use this information, here goes.

1. Step 1 indicates, in effect, that those not on Red Hat or Fedora systems should recompile the source code (blessed open source), and gives scant instructions for doing so. 
Instead, ignore the source, and install openvpn via Synaptic. Much simpler and faster.

2.  Step 6 says to type
sudo /usr/local/sbin/openvpn ~/hotspotvpn2/hotspotvpn2.ovpn 
in order to start encryption.
But Synaptic puts openvpn into /usr/sbin, not /usr/local/sbin.
So, instead, enter
sudo /usr/sbin/openvpn ~/hotspotvpn2/hotspotvpn2.ovpn

In only a few seconds, 256 bit encryption was running on this 64 bit 9.04 system.

Hope this helps someone.

---

