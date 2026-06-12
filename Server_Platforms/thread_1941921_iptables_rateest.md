---
title: "iptables rateest"
date: 2012-03-16
forum: Server Platforms
---

### Post by mad hamish on 2012-03-16
Hi,

I am having difficulty with the rate estimation module (rateest) from iptables. More specifically, when i try to implement the example in the man page, the following occurs

```

~$ sudo iptables -t mangle -A POSTROUTING -o  eth0  -j  RATEEST  --rateest-name eth0 --rateest-interval 250ms --rateest-ewma 0.5s
/lib/xtables/libxt_RATEEST.so: /lib/xtables/libxt_RATEEST.so: undefined symbol: log
iptables v1.4.10: unknown option `--rateest-name'
Try `iptables -h' or 'iptables --help' for more information.

```

My web searches upto now indicate that i might need to patch iptables or something like that? Any assistance would be greatly appreciated.

---

### Post by mad hamish on 2012-03-16
filed a bug report on launchpad

[https://bugs.launchpad.net/ubuntu/+bug/957247](https://bugs.launchpad.net/ubuntu/+bug/957247)

---

