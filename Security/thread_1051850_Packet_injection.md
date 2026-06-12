---
title: "Packet injection"
date: 2009-01-27
forum: Security
---

### Post by PrimitiveSix on 2009-01-27
Hey. i need a complete guide to install drivers for intel wifi 4965 agn in order to do packet injection. I have ubuntu 8.10.

---

### Post by The Tronyx on 2009-01-27
Usually I don't say this but don't be lazy.  If you google "intel 4965 packet injection," the first 3 results are exactly what you are looking for.

Generally speaking, it isn't a good idea to be so...well I am not sure what the word is but when it is clear that you haven't looked into this on your own accord and you use words like "need," you don't appear to sincerely need anything since you couldn't bring an intelligent question to a wonderful community in the first place.

I would recommend looking [here]("http://catb.org/~esr/faqs/hacker-howto.html") before you continue any further into what appears to be the path of your security hobby.  Pay close attention to the section in the FAQS, "Will you teach me how to hack?"

By no means is it my intention to come off as crass, but trust me, what I have just said is beneficial to you, albeit rather blunt.

Good luck!

---

### Post by PrimitiveSix on 2009-01-27
i have done this before ;) but the results is for ubuntu 8.04 . when i am trying to install mac80211 drivers i recieve a lot of errors...

---

### Post by Dr Small on 2009-01-27
> **PrimitiveSix said:**
> i have done this before ;) but the results is for ubuntu 8.04 . when i am trying to install mac80211 drivers i recieve a lot of errors...
The error messages explain the situation. Without them, nobody can help you.

---

### Post by PrimitiveSix on 2009-01-27
ok...from [http://airdump.net/packet-injection-wifi-intel-4965/](http://airdump.net/packet-injection-wifi-intel-4965/)
when i am execute this : patch -p1 < iwl4965-injection.patch 
```
root@primitive-notebook:/home/primitive/compat-wireless-2008-06-25# patch -p1 < iwl4965-injection.patch
(Stripping trailing CRs from patch.)
patching file drivers/net/wireless/iwlwifi/iwl-sta.c
Reversed (or previously applied) patch detected!  Assume -R? [n] y
Hunk #1 succeeded at 925 (offset -43 lines).
(Stripping trailing CRs from patch.)
patching file drivers/net/wireless/iwlwifi/iwl-tx.c
Reversed (or previously applied) patch detected!  Assume -R? [n] y
Hunk #2 FAILED at 810.
Hunk #3 FAILED at 822.
2 out of 3 hunks FAILED -- saving rejects to file drivers/net/wireless/iwlwifi/iwl-tx.c.rej
(Stripping trailing CRs from patch.)
patching file drivers/net/wireless/iwlwifi/iwl4965-base.c
Reversed (or previously applied) patch detected!  Assume -R? [n] y
Hunk #1 succeeded at 2830 (offset 150 lines).
root@primitive-notebook:/home/primitive/compat-wireless-2008-06-25#
```

what i am doing wrong ?
the same with the next line...patch -p1 < mac80211_2.6.26-wl_frag.patch
and if i execute make i take these problems 
```
root@primitive-notebook:/home/primitive/compat-wireless-2008-06-25# make
make -C /lib/modules/2.6.27-9-generic/build M=/home/primitive/compat-wireless-2008-06-25 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
/home/primitive/compat-wireless-2008-06-25/config.mk:48: "WARNING: You are running a kernel >= 2.6.23, you should enable in it CONFIG_NETDEVICES_MULTIQUEUE for 802.11[ne] support"
  CC [M]  /home/primitive/compat-wireless-2008-06-25/drivers/net/wireless/ath5k/base.o
/home/primitive/compat-wireless-2008-06-25/drivers/net/wireless/ath5k/base.c: In function &#8216;ath5k_rxbuf_setup&#8217;:
/home/primitive/compat-wireless-2008-06-25/drivers/net/wireless/ath5k/base.c:1256: warning: passing argument 1 of &#8216;pci_dma_mapping_error&#8217; makes pointer from integer without a cast
/home/primitive/compat-wireless-2008-06-25/drivers/net/wireless/ath5k/base.c:1256: error: too few arguments to function &#8216;pci_dma_mapping_error&#8217;
/home/primitive/compat-wireless-2008-06-25/drivers/net/wireless/ath5k/base.c: In function &#8216;ath5k_beacon_setup&#8217;:
/home/primitive/compat-wireless-2008-06-25/drivers/net/wireless/ath5k/base.c:2017: warning: passing argument 1 of &#8216;pci_dma_mapping_error&#8217; makes pointer from integer without a cast
/home/primitive/compat-wireless-2008-06-25/drivers/net/wireless/ath5k/base.c:2017: error: too few arguments to function &#8216;pci_dma_mapping_error&#8217;
make[4]: *** [/home/primitive/compat-wireless-2008-06-25/drivers/net/wireless/ath5k/base.o] Error 1
make[3]: *** [/home/primitive/compat-wireless-2008-06-25/drivers/net/wireless/ath5k] Error 2
make[2]: *** [/home/primitive/compat-wireless-2008-06-25/drivers/net/wireless] Error 2
make[1]: *** [_module_/home/primitive/compat-wireless-2008-06-25] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [modules] Error 2
root@primitive-notebook:/home/primitive/compat-wireless-2008-06-25# 
```

---

