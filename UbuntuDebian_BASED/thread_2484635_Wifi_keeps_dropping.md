---
title: "Wifi keeps dropping"
date: 2023-03-04
forum: Ubuntu/Debian BASED
---

### Post by defenestrator-go-yeet on 2023-03-04
I've been running Ubuntu 22.04 for a while without major issues, but over the past couple weeks my wifi has started to just cut out seemingly at random. From what I could find, this was the result of the kernel reading the IPv6 method for the adapter being active, even though the adapter's IPv6 method was unactive. I tried to fix this by
```
sudo nmcli device modify ADAPTERID ipv6.method disabled
```
but my internet is still cutting out randomly. Sometimes I can go all day without ever losing connexion, other times I get maybe 15 minutes before I lose it. Until today it was just a minor annoyance since I could just reset the connexion with
```
sudo systemctl restart NetworkManager
```
At first that reset the wifi adapter which would then reconnect to my home network, then a few days ago my computer stopped being able to detect my home network in its scans, and now it can't find any of the networks in my apartment building at all! I have to reboot the entire system for it to start working, and I do not have the time to be doing that every half-hour. None of the other devices in my home are having this issue, so it's not the router. Here's the output from the logs after the most recent disconnect:

```

sudo journalctl -fu NetworkManager

Mar 04 19:28:59 pop-os NetworkManager[1027]: <info>  [1677976139.7853] manager: NetworkManager state is now CONNECTED_LOCAL
Mar 04 19:28:59 pop-os NetworkManager[1027]: <warn>  [1677976139.7857] device ADAPTERID: Activation: failed for connection '[NETWORK NAME]'
Mar 04 19:28:59 pop-os NetworkManager[1027]: <info>  [1677976139.7861] device ADAPTERID: state change: failed -> disconnected (reason 'none', sys-iface-state: 'managed')
Mar 04 19:28:59 pop-os NetworkManager[1027]: <info>  [1677976139.8194] dhcp4 ADAPTERID: canceled DHCP transaction
Mar 04 19:28:59 pop-os NetworkManager[1027]: <info>  [1677976139.8194] dhcp4 ADAPTERID: activation: beginning transaction (timeout in 45 seconds)
Mar 04 19:28:59 pop-os NetworkManager[1027]: <info>  [1677976139.8195] dhcp4 ADAPTERID: state changed no lease
Mar 04 19:29:14 pop-os NetworkManager[1027]: <info>  [1677976154.6875] device ADAPTERID: supplicant interface state: scanning -> disconnected
Mar 04 19:29:14 pop-os NetworkManager[1027]: <info>  [1677976154.6876] device p2p-dev-ADAPTERID: supplicant management interface state: scanning -> disconnected
Mar 04 19:29:14 pop-os NetworkManager[1027]: <info>  [1677976154.7571] device ADAPTERID: supplicant interface state: disconnected -> inactive
Mar 04 19:29:14 pop-os NetworkManager[1027]: <info>  [1677976154.7571] device p2p-dev-ADAPTERID: supplicant management interface state: disconnected -> inactive

```

 If anyone has any ideas what's causing this or how to fix it, please let me know!

---

### Post by him610 on 2023-03-04
Don't know where all of the network gurus are; maybe they are all out on a wild weekend. Meanwhile,....
Please refer to the suggestions found here: [https://ubuntuforums.org/showthread.php?t=370108]("https://ubuntuforums.org/showthread.php?t=370108")
After that, please post the resulting wireless-info.txt. It will help the network gurus diagnose your issue and provide recommendations.

---

### Post by defenestrator-go-yeet on 2023-03-04
Output is posted here: [https://pastebin.com/N2877jjz](https://pastebin.com/N2877jjz)

From what I'm seeing on the recommended devices, the company that makes I'm using (RealTek RTL8812) doesn't have a great track record with Linux compatibility. Wouldn't explain why this has suddenly become an issue though, as I've had this adapter for over a year.

---

### Post by chili555 on 2023-03-05
> I've been running Ubuntu 22.04 for a whileYour paste, however, clearly says: > Description:	Pop!_OS 22.04 LTS
Your wireless may be dropping because there are two wireless access points with the same name and password. This is typical when you have a 2.4 gHz segment and a 5 gHz segment of the same router. Your wireless may be roaming, looking for a better connection. I suggest that you rename the access points; something like myrouter2.4 and myrouter5.

After making these changes, reboot the router.

---

### Post by QIII on 2023-03-05
Moved to Ubuntu/Debian BASED

---

