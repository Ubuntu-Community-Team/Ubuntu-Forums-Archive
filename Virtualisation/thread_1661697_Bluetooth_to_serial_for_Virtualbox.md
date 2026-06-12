---
title: "Bluetooth to serial for Virtualbox"
date: 2011-01-07
forum: Virtualisation
---

### Post by vidtek on 2011-01-07
After lots of head-scratching and searching through forums to get my Linksys USB Bluetooth adaptor talking to my swimming pool controller, I found a very easy and simple solution.

1) ensure it works in a basic Windoze system so you know the hardware is ok.
2) don't run any bluetooth stuff in Ubuntu
3) ensure the bluetooth USB adaptor is set up in virtualbox
4) In virtualbox (I use W7 64-bit, but also tried in XP mediacentre 2005) run the Linksys installation utility
5) Run the programme, it just works.
6 gradually re-enable all ubuntu bluetooth stuff until you find something that breaks it.

This is a very easy way to run serial over bluetooth, It also works for my HTC Desire software.

Some el cheapo bluetooth USB dongles give trouble, after trying many I have found Linksys to work where others don't.  You get what you pay for I suppose.

Tony.

---

