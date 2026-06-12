---
title: "call for testing: bitcoin"
date: 2017-03-28
forum: Ubuntu Development Version
---

### Post by elopio on 2017-03-28
Hello,

It has never been easier, snapcraft and profit!

For a couple of weeks we have been figuring out how to confine
bitcoin. This is one of the most important use cases of the snap
security because you don't want any program messing with your digital
wallet. And when there's a vulnerability in the code, all the clients
should be updated as fast as possible to keep the network sane. With
snaps, just push a fixed version and see everybody update without any
work from their side.

We now need help testing the snap before making it public:

$ sudo snap install bitcoin --candidate

Then launch it from the dash or running the bitcoin.qt command.

No testing guide for this one yet, so if anybody wants to help writing
one, that would be very nice.

This was built from the tag of the latest released bitcoin and pushed
to the store, all automatically by travis. But, be warned, you will be
the first users so we might still find unforeseen problems. Use your
bitcoins with caution during the candidate phase, or just test without
any of your money.

Here are the sources for the snap and CI scripts, in case you want to
verify them or build it yourself:
[https://github.com/elopio/blockchain-snaps/blob/master/bitcoin/snap/snapcraft.yaml](https://github.com/elopio/blockchain-snaps/blob/master/bitcoin/snap/snapcraft.yaml)

Another interesting detail is that most of the cryptocurrencies out
there are forks of the bitcoin source code, so they will all need a
similar snapcraft.yaml. The other one we pushed is bitcoin-unlimited,
which is promoting a hard fork of the bitcoin network to remove the
block size limit. You can have both snaps installed to give them a try
and choose the network you want to support, because both will be fully
confined and independent:

$ sudo snap install bitcoin-unlimited --candidate

Of course, this would require twice the time and space to download
both blockchains.

Thanks to Gal Buki (torusJKL) for his help.

Expect more options in the store soon. Hands welcome if you want to
help preparing these other snaps.

pura vida

---

### Post by izznogooood on 2017-04-02
Could you possibly provide more explanation or links as to what this does for us near mortals who have bitcoins, use them, but have no idea what this means ;).

---

### Post by elopio on 2017-04-02
Hello izznogooood,

I wrote about many things, so I'm not sure which ones do you want me to explain further.

If you want to know about snaps, this is the link: [https://snapcraft.io/](https://snapcraft.io/)

Let me know if you have other questions.

pura vida

---

### Post by izznogooood on 2017-04-03
The "[COLOR=#000000]snapcraft and profit!" and profit part. :)[/COLOR]

---

