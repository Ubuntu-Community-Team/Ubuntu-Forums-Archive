---
title: "Starling (star1) will not connect wirelessly"
date: 2010-12-29
forum: System76 Support
---

### Post by david12 on 2010-12-29
[FONT=Verdana]At some point along the way I hit the Fn F2 combination to turn off the wireless card.  I cannot now restart it.

I am using 10.04. The network manager icon in the panel bar has reported two things: 
1. Wireless networks are disconnected.   This is the most common notification.
2. Something to the effect that the wireless card is disabled. I've only seen this once in restart after restart.

 Pressing Fn F2 does not turn the wireless card back on.
I have checked the User status. (There is only one user on this machine.) 'Connect to wireless and ethernet networks' is checked. (I checked it, it had been unchecked. Then I restarted.)

[/FONT][FONT=Verdana]/etc/network/interfaces reads as it should, to wit:
auto lo
iface lo inet loopbackh
There is nothing else written in the [/FONT][FONT=Verdana]/etc/network/interfaces[/FONT][FONT=Verdana] file.

Finally, when I try to start the connection using 'Connect to Hidden Wireless Network...' dialog, my connection info shows up from previous connection sessions, but I still can't connect. (The network to which I want to connect is not hidden, by the way.)

The problem is that I just don't seem to be able to restart the wireless card. 

I'd appreciate any help.  Thanks.

[/FONT]

---

### Post by isantop on 2010-12-29
What is the status of your wireless indicator light? It's near the front right edge of the computer. It should be lit orange. If it isn't, try pressing the switch on the front-right edge to the right once, then reboot to see if it comes up.

---

### Post by david12 on 2010-12-29
Thanks, that was it.  This isn't my computer and I didn't know the button was there.  Sheesh.

Much appreciated.

---

