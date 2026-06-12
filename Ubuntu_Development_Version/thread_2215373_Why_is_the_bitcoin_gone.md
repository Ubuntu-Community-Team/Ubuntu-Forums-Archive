---
title: "Why is the bitcoin gone?"
date: 2014-04-06
forum: Ubuntu Development Version
---

### Post by one-9-archmage on 2014-04-06
I just notice that when I would upgrade to 14.04 that my bitcoin client would be removed. Does Trusty didn't have the official Bitcoin-client in it?

---

### Post by grahammechanical on 2014-04-06
The Ubuntu Trusty Software Centre has Electrum Bitcoin Wallet and Bit Ticker. What Bitcoin software do you want? Application such as these are the responsibility of their own developers and not Ubuntu developers.

Regards.

---

### Post by Yellow Pasque on 2014-04-06
The package probably gets removed because of package dependency issues. You just need an updated package...

---

### Post by one-9-archmage on 2014-04-07
I'm talking about the bitcoin-qt package. In 13.10 it is there, but in 14.04 it is missing. Electrum isn't compatible to it and when I try to locate in launchpad I'm reading the status "Superseded" in 14.04.

[https://launchpad.net/ubuntu/+source/bitcoin/0.8.5-1](https://launchpad.net/ubuntu/+source/bitcoin/0.8.5-1)

---

### Post by sandyd on 2014-04-07
Exists on debian still [https://packages.debian.org/search?keywords=bitcoin-qt&searchon=names&suite=unstable&section=all](https://packages.debian.org/search?keywords=bitcoin-qt&searchon=names&suite=unstable&section=all)
Maybe it hasnt synced over yet.

---

### Post by kostkon on 2014-04-07
You can add [their official PPA]("https://launchpad.net/~bitcoin/+archive/bitcoin") and hope they'll add Trusty support soon.
> **one-9-archmage said:**
> I'm talking about the bitcoin-qt package. In 13.10 it is there, but in 14.04 it is missing. Electrum isn't compatible to it and when I try to locate in launchpad I'm reading the status "Superseded" in 14.04.
Superseded by [electrum]("https://electrum.org/") maybe? Which is in the trusty repos.

---

