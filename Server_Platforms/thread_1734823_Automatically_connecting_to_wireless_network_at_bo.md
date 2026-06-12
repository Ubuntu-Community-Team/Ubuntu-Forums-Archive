---
title: "Automatically connecting to wireless network at boot"
date: 2011-04-20
forum: Server Platforms
---

### Post by pyedog on 2011-04-20
I have an Ubuntu minimal install with no desktop (because of only 4GB disk space) and XBMC-live ready to run as a media centre but I need it to connect wirelessly from my living room.

I have set up XBMC using a wired connection and can login through that connection using SSH.

I think that my Atheros card has been recognised by Ubuntu and the relevant drivers are installed; "sudo iwlist scanning" successfully lists my wireless router access point as Cell 02.

I use WPA-2 security.

Is anybody able to tell me what I would need to do to connect to the wireless network from the command line and ideally to set it up to do so automatically at every boot? I'm assuming that iwconfig is a central part of this but there is a lot in the man page which I do not understand.

---

### Post by volkswagner on 2011-04-20
cell 02....

I'm not sure if having a space in your essid will cause issues.  You may want to remove the space.... anyway the following should get you going.


run the following to find the interface with wireless extensions:
```
iwconfig
```

Try to associate with adapter with your access point:
```
sudo iwconfig eth0 essid nameofwifi key xxxxsecuritykeyxxxx
```
Replace eth0, nameofwifi and xxxxsecuritykeyxxxx to match your setup!

Get a dhcp lease:
```
sudo dhclient eth0
```

Hopefully you get an ip address!

If the above is successful, you can create the above on startup by editing your interfaces file.

```
sudo nano /etc/network/interfaces
```

Using the information from above edit and save as follows.

```
auto eth0
iface eth0 inet dhcp
wireless-essid nameofwifi
wireless-key xxxxsecuritykeyxxxx
```

Good luck!

---

### Post by pyedog on 2011-04-21
Thanks for your reply. In the end I used wpa_supplicant since I wasn't sure if iwconfig was going to work with my WPA network.

One problem I was having were some characters in my key that I think the terminal was treating as escape characters, changing my key sorted out this problem.

This howto helped me a lot:

[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

---

### Post by Otiosedodge on 2011-06-24
Hi All,

I'm trying to do the same as pyedog, and ran into some problems when I tried to get a dhcp lease. 

A lot of code was spit out, and I think the last line is the relevant one:

```
[  201.894634] panic occurred, switching back to text console
```

And then the system hangs up at that line.

I realize this may be a hardware failure or a bug, but am not aware of a relatively easy solution.

---

### Post by jpdeaton on 2012-02-01
I am trying to do the opposite. I just did a clean minimal 11.10 install and it connects to the wireless network before I log in. The wireless network in the network manager is not set to connect automatically. Anyone know how to stop this?

---

