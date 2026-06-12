---
title: "server 14.04.1 Noob"
date: 2014-09-17
forum: Server Platforms
---

### Post by alex260 on 2014-09-17
I'm following one of the many available tutorials for creating an Ubuntu media server for the purposes of streaming content as well as a file serving.  The end goal is to incorporate an LDAP server to allow for creation and management of users with access to this resource.

Most of my server experience is in Microsoft, with my linux experience being limited to desktop environments, so this is quite a learning experience.

That being said, I'm trying to get off on the right foot so when I push into production, I have a smooth deployment.

My current problem is:

When installing server on a physical machine, it will not recognize the ESSID of the wireless network available, nor will it autoconfigure when bridged with another PC.  (Wireless is not ideal, but for the testing environment it's all that's available).  The SSID of the network is "Judy's House" and is wpa2-Personal.  Settings are correct, just says the network doesn't exist.  

Question #2:
If I have 2 3TB hdd's on the physical device, when partitioning them the [guide]("https://help.ubuntu.com/12.04/serverguide/advanced-installation.html") (formatting) says to select disk partition #1 under #0 as swap and then #1 again below #1, which I believe may be a typo.  If I only have two partitions and the only options are #0 and #1, how do I proceed with the formatting steps?

Preemptive thanks, and my apologies if this is poorly described.  I will try to clarify where necessary.

---

### Post by irv on 2014-09-17
I am answering your thread because I want to keep myself in the loop. I am doing the same thing you are doing, setting up a ubutnu server using only the command prompt from a terminal on my laptop via ssh.
I might not be much help seeing I am a noob in this area, but I found that in the past setting up a desktop where I could not get a wireless connection working I needed to get on a wire connection to get the right drivers for my wireless card. I had to dell computer that I had to do this on.
This sound like this might be your problem. Knowing all the information on your wireless card might help to see what driver you might need.
Hope this point you in the right direction.

---

### Post by alex260 on 2014-09-18
> **irv said:**
> I am answering your thread because I want to keep myself in the loop. I am doing the same thing you are doing, setting up a ubutnu server using only the command prompt from a terminal on my laptop via ssh.
I might not be much help seeing I am a noob in this area, but I found that in the past setting up a desktop where I could not get a wireless connection working I needed to get on a wire connection to get the right drivers for my wireless card. I had to dell computer that I had to do this on.
This sound like this might be your problem. Knowing all the information on your wireless card might help to see what driver you might need.
Hope this point you in the right direction.

Good suggestion.  That is likely my next course of action.  This test environment is at home and not exactly supported by the best networking infrastructure.  Hauling a monitor, keyboard, and mouse around was something I was hoping to avoid.  But at least I might be able to get it installed and along far enough to just remotely manage it.

---

### Post by dudumomo on 2014-09-19
Hi Alex,

Usually to configure the wireless connection on a server, the easiest is to complete the info in /etc/network/interfaces
```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.101
netmask 255.255.255.0
gateway 192.168.1.1
wpa-ssid <your_network>
wpa-psk <your key>
dns-nameservers 192.168.1.1 8.8.8.8
```
Then restart the interface
```
sudo ifdown wlan0 && sudo ifup wlan0
```
[http://ubuntuforums.org/showthread.php?t=2125242](http://ubuntuforums.org/showthread.php?t=2125242)

Does it work?

---

