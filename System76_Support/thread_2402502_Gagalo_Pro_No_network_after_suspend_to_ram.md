---
title: "Gagalo Pro: No network after suspend to ram"
date: 2018-10-01
forum: System76 Support
---

### Post by diederick2 on 2018-10-01
Hi,

About half of the times I wake up my Galago Pro from standby (suspend to ram) I have no network, even though it was working fine before. The wifi icon isn't there, and plugging a cable doesn't do anything either. I have tried restarting NetworkManager, but the system log show me it won't:

```

Sep 29 19:30:09 m3lvin systemd[1]: Failed to start Network Manager.
Sep 29 19:30:09 m3lvin systemd[1]: NetworkManager.service: Service hold-off time over, scheduling restart.
Sep 29 19:30:09 m3lvin systemd[1]: NetworkManager.service: Scheduled restart job, restart counter is at 2.
Sep 29 19:30:09 m3lvin systemd[1]: Stopped Network Manager.
Sep 29 19:30:09 m3lvin systemd[1]: Starting Network Manager...
Sep 29 19:30:24 m3lvin sudo[14162]: pam_unix(sudo:session): session closed for user root
Sep 29 19:30:29 m3lvin sudo[14198]: diederick : TTY=pts/1 ; PWD=/home/diederick ; USER=root ; COMMAND=/bin/systemctl restart NetworkManager
Sep 29 19:30:29 m3lvin sudo[14198]: pam_unix(sudo:session): session opened for user root by (uid=0)
Sep 29 19:30:29 m3lvin systemd[1]: Stopped Network Manager.
Sep 29 19:30:29 m3lvin systemd[1]: Starting Network Manager...
Sep 29 19:31:59 m3lvin systemd[1]: NetworkManager.service: Start operation timed out. Terminating.
Sep 29 19:31:59 m3lvin systemd[1]: NetworkManager.service: Failed with result 'timeout'.
Sep 29 19:31:59 m3lvin systemd[1]: Failed to start Network Manager.
Sep 29 19:31:59 m3lvin sudo[14198]: pam_unix(sudo:session): session closed for user root
Sep 29 19:32:00 m3lvin systemd[1]: NetworkManager.service: Service hold-off time over, scheduling restart.
Sep 29 19:32:00 m3lvin systemd[1]: NetworkManager.service: Scheduled restart job, restart counter is at 1.
Sep 29 19:32:00 m3lvin systemd[1]: Stopped Network Manager.
Sep 29 19:32:00 m3lvin systemd[1]: Starting Network Manager...
Sep 29 19:33:30 m3lvin systemd[1]: NetworkManager.service: Start operation timed out. Terminating.
Sep 29 19:33:30 m3lvin systemd[1]: NetworkManager.service: Failed with result 'timeout'.
Sep 29 19:33:30 m3lvin systemd[1]: Failed to start Network Manager.
Sep 29 19:33:30 m3lvin systemd[1]: NetworkManager.service: Service hold-off time over, scheduling restart.
Sep 29 19:33:30 m3lvin systemd[1]: NetworkManager.service: Scheduled restart job, restart counter is at 2.
Sep 29 19:33:30 m3lvin systemd[1]: Stopped Network Manager.
Sep 29 19:33:30 m3lvin systemd[1]: Starting Network Manager...
Sep 29 19:35:00 m3lvin systemd[1]: NetworkManager.service: Start operation timed out. Terminating.
Sep 29 19:35:00 m3lvin systemd[1]: NetworkManager.service: Failed with result 'timeout'.
Sep 29 19:35:00 m3lvin systemd[1]: Failed to start Network Manager.
Sep 29 19:35:01 m3lvin systemd[1]: NetworkManager.service: Service hold-off time over, scheduling restart.
Sep 29 19:35:01 m3lvin systemd[1]: NetworkManager.service: Scheduled restart job, restart counter is at 3.
Sep 29 19:35:01 m3lvin systemd[1]: Stopped Network Manager.
Sep 29 19:35:01 m3lvin systemd[1]: Starting Network Manager...
Sep 29 19:36:31 m3lvin systemd[1]: NetworkManager.service: Start operation timed out. Terminating.
Sep 29 19:36:31 m3lvin systemd[1]: NetworkManager.service: Failed with result 'timeout'.
Sep 29 19:36:31 m3lvin systemd[1]: Failed to start Network Manager.
Sep 29 19:36:31 m3lvin systemd[1]: NetworkManager.service: Service hold-off time over, scheduling restart.
Sep 29 19:36:31 m3lvin systemd[1]: NetworkManager.service: Scheduled restart job, restart counter is at 4.
Sep 29 19:36:31 m3lvin systemd[1]: Stopped Network Manager.
Sep 29 19:36:31 m3lvin systemd[1]: Starting Network Manager...

```

Why is NetworkManager having trouble restarting?

---

### Post by aaronhoneycutt on 2018-10-01
Hello,

What happens if you issue this command in a terminal?:

sudo systemctl restart NetworkManager.service

Is this on Ubuntu 16.04 or Ubuntu 18.04?

---

### Post by diederick2 on 2018-10-01
Hi, thanks for the reply. You can see in the log that I posted what happened after that command (see 19:30:29): NetworkManager tries to restart but fails repeatedly. I see these in the logs. 

My About window shows Pop!_OS 18.04 LTS.

---

### Post by aaronhoneycutt on 2018-10-01
Let's reinstall the NetworkManager:

sudo apt install --reinstall NetworkManager

We also have an article for wireless we may want to look at as well:

[https://support.system76.com/articles/wireless/](https://support.system76.com/articles/wireless/)

---

### Post by wildmanne39 on 2018-10-01
Hello, I do not know much about Pop!_OS except it is based on Ubuntu but it may help people to diagnose your wifi issue if you click on the wireless script in my signature and post the results for review.

Thanks

---

### Post by aaronhoneycutt on 2018-10-01
> **wildmanne39 said:**
> Hello, I do not know much about Pop!_OS except it is based on Ubuntu but it may help people to diagnose your wifi issue if you click on the wireless script in my signature and post the results for review.

Thanks

You should update that script as it uses gksudo and kdesudo which are both packages that are old and I think both are not in the Ubuntu repository any longer.

---

### Post by wildmanne39 on 2018-10-01
> **aaronhoneycutt said:**
> You should update that script as it uses gksudo and kdesudo which are both packages that are old and I think both are not in the Ubuntu repository any longer.
Thanks aaronhoneycutt, I am in the process of updating it right now with a few new commands so I will make those changes as well.

---

### Post by diederick2 on 2018-10-02
> **aaronhoneycutt said:**
> Let's reinstall the NetworkManager:

sudo apt install --reinstall NetworkManager

We also have an article for wireless we may want to look at as well:

[https://support.system76.com/articles/wireless/](https://support.system76.com/articles/wireless/)

This is a brand new Galago Pro, so I can you tell me what reinstalling NetworkManager would accomplish?

---

### Post by diederick2 on 2018-10-02
> **wildmanne39 said:**
> Thanks aaronhoneycutt, I am in the process of updating it right now with a few new commands so I will make those changes as well.


The script ran without problem, recognised everything. The wifi card is a Intel Corporation Wireless 8265 / 8275, which I didn't find in the [list of supported cards]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported"), but I can't believe System76 would build a Linux laptop with a WiFi card that is not supported.

What do I look for in that output? It said its too big to paste here, but you can find it [here]("https://diederickdevries.net/goodies/wireless-info.txt").

And [here]("https://diederickdevries.net/goodies/wireless-info-nowifi.txt") is the output of the script when the problem occurred,just in case that is relevant.

---

### Post by wildmanne39 on 2018-10-02
There are a few things that I see that can be tweaked but lets see if turning off power management will help fix the issue.
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```

Thanks

---

### Post by diederick2 on 2018-10-03
> **wildmanne39 said:**
> There are a few things that I see that can be tweaked but lets see if turning off power management will help fix the issue.
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```

After making that change and restarting the laptop the issue appears to have gone away. 

BTW In [the documentation]("https://developer.gnome.org/NetworkManager/stable/nm-settings-ifcfg-rh.html") I only read about values default, ignore, enable and disable. Which of these is "2"?

---

### Post by wildmanne39 on 2018-10-03
I have never seen an explanation of exactly what 2 is but I am pretty sure it is just disable. If you are satisfied that your issue is resolved please use thread tools at the top of the page to mark the thread solved.

Thanks

---

### Post by diederick2 on 2018-10-03
Sigh. I cried success too early. This evening the problem was there again after a longer suspend to ram. What now?

---

