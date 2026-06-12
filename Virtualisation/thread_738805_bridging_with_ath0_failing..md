---
title: "bridging with ath0 failing."
date: 2008-03-29
forum: Virtualisation
---

### Post by survient on 2008-03-29
I am having issues with getting networking enabled on my XP virtual machine. As many others have gotten:
```

bridge-ath0: enabling the bridge
bridge-ath0: can't bridge with ath0, bad header length 88
bridge-ath0: interface ath0 is not a valid Ethernet interface
bridge-ath0: can't bridge with ath0, bad header length 88

```
I tried commenting out a few lines:
```

#ifdef USE_HEADERLEN_RESV
        dev->hard_header_len += sizeof(struct ieee80211_qosframe) +
                                sizeof(struct llc) +
                                IEEE80211_ADDR_LEN +
                                IEEE80211_WEP_IVLEN +
                                IEEE80211_WEP_KIDLEN;
#ifdef ATH_SUPERG_FF
        dev->hard_header_len += ATH_FF_MAX_HDR;
#endif
#endif

```
as others had suggested and compiling a custom version of the madwifi drivers, which allowed me to get into the vmware server, and add a bridged connection for my XP VM, however as stated by others:
> 
I got the new drivers and modified the code as above, recompiled. Still no joy.

DHCP on the XP guest doesn't work.
If I manually assign an IP address, I can ping the native Ubuntu ath0 IP and vice-versa.

However, I still can't ping the gateway from the XP guest.

I see there is a patch here: [http://madwifi.org/ticket/407](http://madwifi.org/ticket/407) but I have no idea how to apply it to the code(it's been awhile since I last applied a patch to source code). I tried compiling the latest drivers with those lines commented out, however it failed to compile. The version I chose to fall back on was r3362-20080224. I'm trying the latest version right now as is to see if it fixes the issue. Any help on this would be appreciated, I was wondering if there was a way to trick the VMware server into thinking ath0 was eth0, and doing it in a way that resolved the issue, though I may be SOL. Thanks.

---

