---
title: "NetworkManager-wait-online.service Causing Delays - How to Resolve?"
date: 2024-09-21
forum: Virtualisation
---

### Post by mmq93 on 2024-09-21
[COLOR=#000000]Hello everyone,[/COLOR]
[COLOR=#000000]Hello everyone,[/COLOR]
[COLOR=#000000]I'm currently running Ubuntu and experiencing a significant delay during startup due to the **NetworkManager-wait-online.service**, which seems to hang for around 2 minutes waiting for network connectivity. However, I don't need the system to wait for network connections during boot.[/COLOR]
[COLOR=#000000]I've tried disabling the service using the following commands:[/COLOR]
[FONT=Verdana]sudo systemctl [/FONT][FONT=Verdana]disable[/FONT][FONT=Verdana] NetworkManager-wait-online.service[/FONT]
sudo systemctl mask NetworkManager-wait-online.service


[COLOR=#000000]But even after disabling and masking the service, the delay remains when I reboot the system, and the service seems to continue running as if I hadn't disabled it.

Thanks a lot[/COLOR]

---

### Post by Rick St. George on 2024-09-27
What version Ubuntu, Lubuntu, Xubuntu, Zorin, etc.?

Try what solved the issue, here -> [https://ubuntuforums.org/showthread.php?t=2490962]("https://ubuntuforums.org/showthread.php?t=2490962")

---

