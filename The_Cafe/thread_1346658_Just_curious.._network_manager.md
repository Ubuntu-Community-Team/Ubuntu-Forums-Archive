---
title: "Just curious.. network manager"
date: 2009-12-05
forum: The Cafe
---

### Post by hvymtlsteve on 2009-12-05
Why is it that the results vary so much between wifi-radar, wicd, and the stock gnome network manager?

I'm staying at a hotel where I observed that the wireless router on my floor is directly outside my room, and for some reason I couldn't get connected with network manager. So, I went ahead and removed it, and installed wicd from the deb, and it worked like a charm (didn't spend too much time mulling this over, I have seen the same thing in the past).

Shouldn't these be functionally equivalent?

---

### Post by subdivision on 2009-12-05
My own experience in Arch with those two programs has been that wicd is far and away the better of the two.  I don't think I've ever even managed to get network manager to work.

They SHOULD be functionally equivalent, but in practice it doesn't seem to work that way.

---

### Post by doorknob60 on 2009-12-05
That's why I use the console for connecting to wireless. All I need is iwconfig, iwlist, and dhclient :) (and WPAsupplicant sometimes). I do use WIcd on my Arch laptop though, and it works good.

---

### Post by cariboo on 2009-12-05
I've experienced exactly the opposite, network-manger works much better than wicd on my HP laptop. Wifi-radar and network-manager see most of the networks in the neighbourhood, while wicd barely sees my own access points.

---

### Post by dragos240 on 2009-12-05
I use this:

ifconfig wlan0 up
iwconfig wlan0 essid "linksys"
iwconfig wlan0 mode Managed
dhcpcd

And then I'm connected.

---

### Post by Giant Speck on 2009-12-05
> **dragos240 said:**
> I use this:

ifconfig wlan0 up
iwconfig wlan0 essid "linksys"
iwconfig wlan0 mode Managed
dhcpcd

And then I'm connected.

When I grow up, I want to be as 1337 as you.

---

### Post by dragos240 on 2009-12-05
> **Giant Speck said:**
> When I grow up, I want to be as 1337 as you.

ww. No, only for my server. Which is not going to be up until the 26th. I use this script here. I set it as a startup application.

---

### Post by myusername on 2009-12-05
> **dragos240 said:**
> ww. No, only for my server. Which is not going to be up until the 26th. I use this script here. I set it as a startup application.

never thought about using a script

---

### Post by dragos240 on 2009-12-05
> **myusername said:**
> never thought about using a script

What do you use then?

---

### Post by phrostbyte on 2009-12-05
> **dragos240 said:**
> I use this:

ifconfig wlan0 up
iwconfig wlan0 essid "linksys"
iwconfig wlan0 mode Managed
dhcpcd

And then I'm connected.

Do you know if there is a command which scans for wireless networks and returns their SSIDs?

---

### Post by dragos240 on 2009-12-05
> **phrostbyte said:**
> Do you know if there is a command which scans for wireless networks and returns their SSIDs?

Yes! iwlist wlan0 scanning

I am assuming your wireless is wlan0. Also use it with sudo if using it normally doesn't work.

---

### Post by Xbehave on 2009-12-05
Network-manager does what it says on the tin, it managed networks and it wors pretty well, it's extensible (supports VPNs, etc), runs sciprts and exports over dbus to make it pretty powerful

Wicd/wifi-radar are alternatives to networkManager but AFAIK it doesn't offer support for VPNs, doesn't export info over dbus and has a different scripting setup.

doing it manually may be L33T but unless your running a server its unneeded when there are nice GUI alternatives about (i think NetworkManager even has a CLI now)

---

### Post by cariboo on 2009-12-05
The Ubuntu server doesn't have a gui, so everything has to be done on the command line.

I don't understand why you'd want to use wireless on a sever. I had to transfer 47GB of files to my server yesterday, it took about one hour and forty-five minutes, on my 100Mbps network, using wireless would have taken 4 times as long. The best transfer rate I've ever seen using wireless is 2Mbps, while my wired connection averages 9.7Mbps.

---

### Post by dragos240 on 2009-12-05
> **cariboo907 said:**
> The Ubuntu server doesn't have a gui, so everything has to be done on the command line.

I don't understand why you'd want to use wireless on a sever. I had to transfer 47GB of files to my server yesterday, it took about one hour and forty-five minutes, on my 100Mbps network, using wireless would have taken 4 times as long. The best transfer rate I've ever seen using wireless is 2Mbps, while my wired connection averages 9.7Mbps.

Yes it does. If you install it manually ;)

---

### Post by t0p on 2009-12-05
> **phrostbyte said:**
> Do you know if there is a command which scans for wireless networks and returns their SSIDs?

Have a look at *iwlist*.

```
man iwlist
```

I expect its *scan* parameter will help you.

---

### Post by dragos240 on 2009-12-05
> **t0p said:**
> Have a look at *iwlist*.

```
man iwlist
```I expect its *scan* parameter will help you.

I beat you to it.

---

