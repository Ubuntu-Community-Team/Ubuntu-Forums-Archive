---
title: "sudo nmcli device set wlan0 managed yes"
date: 2022-11-26
forum: Security
---

### Post by sternaugen on 2022-11-26
Dear, dear Linuxistas.

I have a conundrum. My Xubuntu installation has worked for a couple of years. It even survived a version update and a rsync migration to a new drive. Two weeks ago I did a restart and all of a sudden I could not connect to wifi. The icon said "network not managed". I could connect with ethernet but it did not show up in the UI in the taskbar.

The hell of finding out what was wrong started. Outdated articles from older versions, tangent questions answered and so forth. Nothing worked. network-manager had been changed to NetworkManager, /etc/../interfaces did not exist anymore just if-up, if-down. So I could not get it to work for two weeks. Yesterday evening i just started reading man nmcli and tried every command that seemed to address my problem until I found the last section on

 sudo nmcli device set wlan0 managed yes

which started networkmanager and connected me as usual to my wifi router. Happy days. Until a couple of minutes ago when I started my computer again and there was no connection. I had to run the command again.

1 SO! What happened?
1.1 Did me installing and uninstalling obs-studio via apt change my system settings?
1.2 Was there some package sent out in the last weeks that altered the default settings removing NetworkManager from being auto?

2. How do I do make nmcli do itself automatic at startup again? It worked before, but not now.

LASTLY there needs to be a github for forum questions so that old solutions that are no longer working are not public or have a disclaimer it is outdated. Some sort of version check on the internet. IF package depreciated SIGNAL all forum posts ON internet *I am no longer up to date* Think of it as a fractal, hologram, quantum dot matrix thing of a magix, where versions are connected to forum posts, tags are connected to the developers, everything updated at once like a firestorm of version internet traffic.

---

