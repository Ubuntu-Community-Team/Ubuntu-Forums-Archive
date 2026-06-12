---
title: "wifi configuration questions"
date: 2011-03-24
forum: System76 Support
---

### Post by gitana on 2011-03-24
I've got a lemur, running 10.10, and I'm having issues figuring out how to configure my wifi.

1) When I boot up, wifi is always disabled.  Optimally, I'd like it to keep the state it had at shutdown, or if that's not possible, I'd like it to default to on.

2) When the computer is on battery power and the lid is shut, wifi turns off.  This means that if the power blinks when I'm remoted into the machine, I'm knocked off until I can physically get in front of it and re-enable wifi.  I'd like it to only turn off if it goes below a certain battery level.  I'd also like it to pop up a message with a timer and a cancel, so if I'm remoted in, I have warning and some control.

3) One of my wifi networks does not broadcast a SSID.  My mobile devices handle it just fine - once they've been introduced, they'll join without any action on my part.  But this machine has to be re-introduced every time.  How can I make it join without prompting?

---

### Post by Ebonwumon on 2011-03-24
In regards to the first question, I had the same issue and IIRC I fixed it by doing the wifi on keyboard shortcut right as my computer was booting (the BIOS stage). Then it remembered the state for future boots.

---

### Post by isantop on 2011-03-24
> **gitana said:**
> 2) When the computer is on battery power and the lid is shut, wifi turns off.  This means that if the power blinks when I'm remoted into the machine, I'm knocked off until I can physically get in front of it and re-enable wifi.  I'd like it to only turn off if it goes below a certain battery level.  I'd also like it to pop up a message with a timer and a cancel, so if I'm remoted in, I have warning and some control.

3) One of my wifi networks does not broadcast a SSID.  My mobile devices handle it just fine - once they've been introduced, they'll join without any action on my part.  But this machine has to be re-introduced every time.  How can I make it join without prompting?

The second question is a limitation of Ubuntu at the software level, though you can set it to hibernate when the battery gets too low. You can also disable the Sleep on Lid close behavior by going to System > Preferences > Power Management.

How are you connecting to your wireless network? Are you using the Network Menu in the upper panel, and selecting "Connect to Hidden Wireless network"?

---

### Post by gitana on 2011-03-25
> **isantop said:**
> How are you connecting to your wireless network? Are you using the Network Menu in the upper panel, and selecting "Connect to Hidden Wireless network"?

I am.  If I look at the Wireless tab on Network Connections, my network is listed, with Last Used as never (though I'm currently connected), and when I edit it, Connect automatically is checked.

Thanks for the advice on power management - it worked.

---

### Post by isantop on 2011-03-25
I've done some research on this issue, and it turns out Ubuntu doesn't automatically connect to a hidden network because of power management and security issues. Mac OS X and Windows *should* have similar behavior. Here's a link with a better explanation:

[http://superuser.com/questions/43836/automatically-connecting-to-hidden-ssid-wifi-network](http://superuser.com/questions/43836/automatically-connecting-to-hidden-ssid-wifi-network)

Basically, it forces the computer to always ask if the network is close by, even if it isn't, which broadcasts your SSID publicly. Furthermore, it can cause this to happen even if you're already connected. Also, since the computer has to actively probe for the network, it uses more data, and therefore battery power, to configure the wireless like that. If you need to have the computer automatically connect, it's better to broadcast the SSID. If you need security, it's better to use encryption like WPA.

---

