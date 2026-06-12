---
title: "Help with Setting Up Tunnel Bear VPN in Ubuntu Mate 18.04"
date: 2020-05-24
forum: Security
---

### Post by KenUBF on 2020-05-24
I went to this website [https://www.tunnelbear.com/blog/linux_support/](https://www.tunnelbear.com/blog/linux_support/) to set up everything but since I'm not using vanilla Ubuntu the instructions couldn't be followed. In my network settings I have no VPN option. Though I do have in the drop down menu on the top panel on my networking icon a "VPN Connections" and an "Add a VPN Connection" dialog but it is greyed out (picture below). I don't see any other menus that mention anything about VPN settings so I am a little stuck. I've downloaded the config files for Tunnel Bear. I just need help in getting my system set up. Thank you!

[ATTACH=CONFIG]286000[/ATTACH]

---

### Post by EuclideanCoffee on 2020-05-24
Do you have openvpn installed?

```

sudo apt install network-manager-openvpn-gnome

```

Then restart.

```


sudo systemctl restart network-manager 

```

---

### Post by KenUBF on 2020-05-25
Thanks for the reply. Yes I have openvpn installed. Restarted network manager but still no change. I do have ProtonVPN installed also and it works fine.

---

### Post by EuclideanCoffee on 2020-05-26
These instructions are the same as Proton's. I don't understand the problem then.

[https://protonvpn.com/support/linux-vpn-setup/](https://protonvpn.com/support/linux-vpn-setup/)

[https://www.tunnelbear.com/blog/linux_support/](https://www.tunnelbear.com/blog/linux_support/)

Regardless of vanilla or non-vanilla Ubuntu desktop, if you have network manager you should be able to modify a connection in the same way.

Could you please explain how it is that Proton works but not the other when they are configured the same?

---

### Post by KenUBF on 2020-05-26
I just used the command line set up, as shown here: [https://protonvpn.com/support/linux-vpn-tool/](https://protonvpn.com/support/linux-vpn-tool/)

My question is how do I set up a VPN on MATE when the menus are completely different? There are no VPN options like there is in Gnome. At least one that works. Mine is greyed out for some reason (see pic above). And that's the only VPN related anything that I see in any Settings menu that I've looked at.

---

### Post by EuclideanCoffee on 2020-05-26
Ah. I see. Your question would've been easier to answer if you asked for setting up VPN on a MATE desktop environment forum. :)

It appears it may be recommended to simply install network manager. I didn't realize network manager didn't come with MATE.

[https://support.purevpn.com/setup-your-linux-system-through-mate-desktop-environment](https://support.purevpn.com/setup-your-linux-system-through-mate-desktop-environment)

These menus will be available then through the application. Otherwise I would ask at a MATE specialist forum.

---

### Post by KenUBF on 2020-05-27
Thank you!

---

### Post by KenUBF on 2020-05-27
I tried the settings in the page but that didn't seem to bring up any menus that I could find. I think a MATE specific forum might work better. Thanks for the help!

---

### Post by EuclideanCoffee on 2020-05-27
Makes sense. Good luck. :)

---

