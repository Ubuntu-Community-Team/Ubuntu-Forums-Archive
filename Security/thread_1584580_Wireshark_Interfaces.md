---
title: "Wireshark Interfaces"
date: 2010-09-29
forum: Security
---

### Post by Guy Sibley on 2010-09-29
I can't get Wireshark to recognize any network interfaces on my Eee pc. Does anyone have any ideas?

---

### Post by uRock on 2010-09-29
You have to set up a user group in order to monitor the interfaces.
To set up permissions and safely run wireshark follow these instructions[B],
[/B]> **Rubi1200 said:**
> Once Wireshark is installed, the correct way to  run it without invoking root privileges (which is extremely dangerous)  can be done like this from the terminal:

```
sudo apt-get install libcap2-bin wireshark
sudo chgrp admin /usr/bin/dumpcap
sudo chmod 750 /usr/bin/dumpcap
sudo setcap cap_net_raw,cap_net_admin+eip /usr/bin/dumpcap
```Run each command separately and then run Wireshark.

Courtesy of forum member cdenley.

Hope this helps.

---

### Post by mr-woof on 2010-09-29
have you tried running wireshark as root, that usually works for me :)

sudo wireshark :)

---

### Post by Rubi1200 on 2010-09-29
> **mr-woof said:**
> have you tried running wireshark as root, that usually works for me :)

sudo wireshark :)
Please, please do NOT run Wireshark as root as you could potentially expose/compromise your whole system!!!

> WIRESHARK CONTAINS OVER ONE POINT FIVE MILLION LINES OF SOURCE CODE. DO NOT RUN THEM AS ROOT.
Source:
[http://packetlife.net/blog/2010/mar/19/sniffing-wireshark-non-root-user/](http://packetlife.net/blog/2010/mar/19/sniffing-wireshark-non-root-user/)

---

### Post by mr-woof on 2010-09-29
ah oops, thanks for telling me. I think I've only used it once or twice like that, whoopsie

---

### Post by Rubi1200 on 2010-09-29
> **mr-woof said:**
> ah oops, thanks for telling me. I think I've only used it once or twice like that, whoopsie
Please use the commands linked above in the post by uRock; then you can run Wireshark and capture interfaces but not as root.

---

