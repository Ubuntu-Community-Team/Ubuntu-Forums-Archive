---
title: "how to get qlogic hba firmware update?"
date: 2017-07-18
forum: Server Platforms
---

### Post by tmsundaram on 2017-07-18
I need to have updated firmware for my Qloic qle2562 FC card on Ubuntu 14.04 server. The hardware vendor does not providing firmware for Ubuntu. Can any one help to get it ?

---

### Post by darkod on 2017-07-18
Usually FW is not OS related. Are you sure you need to link this to ubuntu?

The safest way would be do it with a usb stick in something like DOS mode, not from within any OS. Have you explored that possibility?

---

### Post by tmsundaram on 2017-07-19
Flashing from DOS mode does flash update hardware firmware. But i am looking for firmware which used by kernel to talk to HBA. It is located in /lib/firmware. Currently it has 7.x version. I need an 8.x version. Just to know does updating linux-firmware package would help?

---

