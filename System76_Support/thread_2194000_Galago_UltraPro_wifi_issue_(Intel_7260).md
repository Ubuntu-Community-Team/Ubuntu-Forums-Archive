---
title: "Galago UltraPro wifi issue (Intel 7260)"
date: 2013-12-15
forum: System76 Support
---

### Post by chirpis7 on 2013-12-15
Hi guys,

I have a Galago UltraPro (galu1) running Ubuntu 13.10. I have Intel 7260 wireless. Sometimes my wifi connection drops and the network to which I was connected disappears from the list of available networks in network manager. The only way to fix it is to disable wifi and re-enable it. It has happened on every network I use for any length of time, but it happens on some networks more than others. I haven't looked into what the pattern may be. Is this a known issue, or does it sound familiar to anyone?

---

### Post by isantop on 2013-12-16
This sounds a bit like a failing wireless card to me (which would be covered under your warranty). Has it happened on G, N, and AC networks, only one or the other, 5GHz vs 2.4 GHZ, etc.?

---

### Post by chirpis7 on 2013-12-16
Hehe, I actually had the most problems with one of the Starbucks "attwifi" networks. The connection would drop every few minutes and disappear, and only reappear if I disabled and re-enabled wifi. I looked around, and no one else seemed to be having any problems. It happens very rarely on my home network. I looked at my router's settings, and it's transmitting in "11b/g/n mixed mode" at 2.4 GHz.

---

### Post by mike-powerthroughwords on 2013-12-17
> **isantop said:**
> This sounds a bit like a failing wireless card to me (which would be covered under your warranty). Has it happened on G, N, and AC networks, only one or the other, 5GHz vs 2.4 GHZ, etc.?

There are problems with the 7260 under linux. There are bugs in the firmware that is currently shipped with Ubuntu (and all other distributions, at the time of writing). See the linux-wireless thread at [http://www.spinics.net/lists/linux-wireless/msg114861.html](http://www.spinics.net/lists/linux-wireless/msg114861.html)

There's an updated firmware available though, see [http://marc.info/?l=linux-wireless&m=138718659005765&w=2](http://marc.info/?l=linux-wireless&m=138718659005765&w=2)

If System76 is shipping this card, you're going to be getting these type of support issues a LOT. I'd suggest updating the firmware manually before you ship out systems with this card, as the new firmware isn't yet packaged in Ubuntu.

---

### Post by mike-powerthroughwords on 2013-12-17
I have filed a bug asking for the firmware to be updated. If you mark the bug as affecting you too, it'll be more likely to get seen and done :)

[https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1261668](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1261668)

---

### Post by chirpis7 on 2013-12-18
Is it difficult to install the updated firmware? I've never done it before.

---

### Post by chirpis7 on 2013-12-18
Just looked at the README file that came with the firmware. I'm definitely going to need help with this.

---

### Post by mike-powerthroughwords on 2013-12-18
No, it's really easy to install the firmware - the README contains loads of details about enabling firmware in the kernel, etc. etc. etc. that Ubuntu has already done for you.

You see there's a file called iwlwifi-7260-7.ucode ? Copy that to /lib/firmware

You'll need to do that from the terminal, so the command would be

    sudo cp iwlwifi-7260-7.ucode /lib/firmware

Once that's done, reboot. And that's it!

---

### Post by chirpis7 on 2013-12-18
Awesome. Just did that, and it seems to be working so far. Thank you so much for the help!

---

