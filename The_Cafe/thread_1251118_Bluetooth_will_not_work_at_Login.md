---
title: "Bluetooth will not work at Login"
date: 2009-08-27
forum: The Cafe
---

### Post by Buschbarber on 2009-08-27
I have a Logitech MX5000 Bluetooth Keyboard and Mouse. When I reach the Ubuntu Login screen, I have to Disconnect and Reconnect the Bluetooth Adapter, before I Login, or it will not work. If I Disconnect and Reconnect the Bluetooth Adapter and then Login, it works fine until I Reboot.

---

### Post by dragos240 on 2009-08-27
Maybe a daemon specifically for a bluetooth device?

---

### Post by Buschbarber on 2009-08-27
> **dragos240 said:**
> Maybe a daemon specifically for a bluetooth device?

I am not sure what you mean. Is the daemon the Cause or is it something I need to Correct the problem?

Thanks!!

---

### Post by dragos240 on 2009-08-27
A daemon is a program usually launched at startup that runs in the background and serves a specific purpous and does a simple task. I am suggesting a bluetooth recoginizing daemon for this issue.

---

### Post by Buschbarber on 2009-08-27
Check out this thread I found. It says that when I Disconnect and Reconnect the Bluetooth Adapter, before Login, I am actually now in USB mode and not in Bluetooth mode.

I checked my Bluetooth icon and sure enouth, there are no Bluetooth Devices listed.

[http://ubuntuforums.org/showthread.php?t=432013](http://ubuntuforums.org/showthread.php?t=432013)

I am not sure what to do next.

---

### Post by dragos240 on 2009-08-27
Hmm....... oh oh! I know!
[Click me!]("http://www.google.com/#hl=en&source=hp&q=bluetooth+ubuntu&aq=0&aqi=g10&oq=bluetooth+ub&fp=fffa6ff748389786")

---

### Post by Buschbarber on 2009-08-27
I went to bluez.org and found that there was a newer version of the Bluetooth software.

Is that something I should install and if so, what is the correct procedure?

I am running Ubuntu Ultimate 2.3 based upon Ubuntu 9.04. The latest Bluez software is V4.32 and the newer version, on the bluez.org site is 4.50

---

### Post by Buschbarber on 2009-08-27
I ran across an applet called Blueman 1.10

[http://www.ubuntugeek.com/blueman-bluetooth-manager-for-ubuntu.html](http://www.ubuntugeek.com/blueman-bluetooth-manager-for-ubuntu.html)

It was easy to Pair the MX5000 Keyboard and MX1000 Mouse.

The icon sits in the top Panel where the other Bluetooth icon used to be.

I rebooted and I had no problems using the Bluetooth Keyboard and Mouse both at the Login screen and after Login, without touching the Bluetooth adapter.

---

