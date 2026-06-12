---
title: "Lost Wireless with 10.04 to 12.04 LTS upgrade"
date: 2012-11-21
forum: System76 Support
---

### Post by Manolicious on 2012-11-21
I'm using a Starling Notbook, Realtek RLT8101E/RLT8102.  Downloaded the System 76 driver and clicked install but it still won't turn on the wireless function.

---

### Post by gamerchick02 on 2012-11-23
Is the physical wireless button on?

Have you accidentally turned off the wireless with the function buttons?

This perplexed me for a while too with my Starling.

Check those and I hope it fixes it.

Amy

---

### Post by Manolicious on 2012-11-24
>Is the physical wireless button on?

Is it the weird flip switch on the bottom right side?  It's not a button, but a slide switch that retracts after you slide it.  From what I remember, if the wireless light wasn't on you were supposed to slide this switch and restart the Starling.  So far I've done that and the wireless light is still off and there is no sign ubuntu 12.04 is even attempting to look for a wireless connection.

>Have you accidentally turned off the wireless with the function buttons?

Where would these be?  I am highly annoyed with 12.04 because they've gutted the more advanced system access programs like even a hardware utitlity to even recognize what hardware I have and how to enable it.  Bash still works fine and tells me there's a wireless card, but as for ubuntu getting it to work I've had no dice.

---

### Post by kurt18947 on 2012-11-24
There may be a couple things you can try.  Both require terminal usage.  One would be to check what rfkill tells you about your network adapters:

When I type this command:

```
rfkill list  
```I get this result:

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

If Hard Blocked said "yes", it's likely a physical switch is in the off position.

I doubt you'll get any result from this but you can try:

```
iwconfig
```Mine looks like this:

```
 iwconfig
wlan2     IEEE 802.11bgn  ESSID:"essid"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:26:62:7C:B1:5B   
          Bit Rate=65 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=57/70  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4  Invalid misc:417   Missed beacon:0
```

I suspect that 'rfkill' will be the most informative.  Hope this helps.

---

### Post by Manolicious on 2012-11-25
Well when I type ```
rfkill list
``` in bash I get nothing, when I type iwconfig I get the following readout.
```

lo        no wireless extensions.
eth0      no wireless extensions.

```

---

