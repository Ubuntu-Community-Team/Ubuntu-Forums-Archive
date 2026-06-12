---
title: "HP Zbook sudden shutdowns on low battery"
date: 2021-09-18
forum: Ubuntu/Debian BASED
---

### Post by optmed on 2021-09-18
hi everyone, 

I have this HP Zbook G2 15 with Pop Linux OS 20.04 on it (it had but currently has no Windows on it). Everything works great (both on battery and A/C power), etc, except for a rather annoying glitch: on battery power, as soon as the battery goes lower than 40%, and I'm on a resource-hungry app (like Darktable or Gimp, e.g.), the HP shuts itself down with no warning. You hear a sharp click and it's gone. This doesn't happen if I'm on "light" apps such as Firefox and/or Thunderbird and/or using LibreOffice and/or using a music client. 

A couple of things that might be relevant: the battery is new, the HP has new thermal paste, and it's very clean inside. It has been checked by HP and - in terms of hardware, everything is in good conditions. Overheating isn't an issue - the PC's overall temperature prior to shutdown-without-warning constantly remains in the region of 40 to 44 C (the Nvidia X thermal settings normally indicate a temperature of around 48 C). In other words, prior to shut-down-without-warning, usually there's hardly any fan activity. Perhaps more importantly, it's not possible to replicate the problem in Windows 10 on this HP - on the other hand, the problem persists on Ubuntu, Linux Mint, and Kubuntu. By the way, in each of these Linux OS I disabled every power management option related to low battery, like automatic suspend or hybernate or shutdown, to no avail. 

I know very little about operating systems, etc, but I have this sneaking feeling that Ubuntu (or Pop Linux OS) seems to think that it is too risky to run power-hungry apps on a 40%- battery charge on this HP, and prefers to shut it down altogether. I just don't understand why it does it and why it does it so no prior warning or why it doesn't simply slow down the GPU, for instance (like it does on Windows? as far as I can see...). If my theory is not totally bonkers, is there a configuration file in Ubuntu that - if modified - can prevent the OS from shutting down the PC, all of a sudden and without prior warning? and if there is such a file, could you please tell me how/where to locate it and how to modify it?

thanks!

---

### Post by Frogs Hair on 2021-09-18
Moved to *Ubuntu/Debian Based.*

---

### Post by optmed on 2021-09-19
I'd like to add the following (if relevant): 

- switching from "Nvidia graphics" to "Hybrid graphics" doesn't seem to help;
- while using "light apps" (see my initial post), if the battery goes below 20%, it's not possible to re-boot the PC: it goes as far as the log-in password screen and then you hear a "click" sound and the PC turns itself off; 
- I've installed "tlp" and "powertop", but that hasn't improved anything.

---

### Post by DuckHook on 2021-09-21
[LIST=1]
[*]Do your logs tell you anything useful?
[*]Have you tried running the HW on a default install using LiveUSB? If so, do the same issues crop up?
[*]I'm afraid that I'm out of my element with PopOS and NVidia, but have you installed the most recent NVidia driver? Please note that I have no idea which NVidia driver PopOS wants for your specific HW setup.
[/LIST]

---

### Post by optmed on 2021-09-22
thanx DuckHook for your post. 

1. Log: the only command I know is *last -x | grep shutdown | less *(it does show a list of shutdowns between the 19th Sept and today. I can't see anything interesting there. If you know of a better command, can you please give it to me: i'll trigger a sudden shutdown and post the result here. 

2. running the HW on a default install using LiveUSB: I'm not sure I understand what this means. When I installed Pop Linux OS, the PC's power cord was plugged in, i.e., it wasn't running on battery. Are you referring to a test I can do using the LiveUSB?

3. Nvidia drivers: i downloaded and installed the Pop OS version that includes the Nvdia drivers. As far as I can see, all the drivers are installed and work correctly - if you know of test i can do to verify this, can you please let me know. 

Apologies for having to point this out again: I understand that Ubuntu and Pop OS are different, etc. On the other hand, I installed Ubuntu 20.04 on this HP a couple of weeks ago, and I had exactly the same problem: same circumstances, same behaviour, same everything. I tried Mint after that, no difference. Kubuntu, ditto. It didn't happen on Windows, though.

---

### Post by optmed on 2021-09-22
I'll replace Pop LInux OS with Ubuntu 20.04 shortly. Will then reproduce the issue and create a new post.

---

### Post by DuckHook on 2021-09-23
> **optmed said:**
> thanx DuckHook for your post.
Sorry for the late response. Life got in the way of a faster response:
> 1. Log: the only command I know is *last -x | grep shutdown | less *(it does show a list of shutdowns between the 19th Sept and today. I can't see anything interesting there. If you know of a better command, can you please give it to me: i'll trigger a sudden shutdown and post the result here.
The standard logs to look at are syslog and dmesg, but ever since systemd, the newest gambit is journald. A good intro to understanding logs (and Linux in general) is: [https://linuxjourney.com/](https://linuxjourney.com/)
journald is a bit more involved, but try: [https://www.certdepot.net/rhel7-get-started-systemd/](https://www.certdepot.net/rhel7-get-started-systemd/) especially the section dealing with journalctl
> 2. running the HW on a default install using LiveUSB: I'm not sure I understand what this means. When I installed Pop Linux OS, the PC's power cord was plugged in, i.e., it wasn't running on battery. Are you referring to a test I can do using the LiveUSB?
Yes. Again, I am hampered by PopOS. I don't know if PopOS comes with a LiveUSB, or can be run that way.

On further reading your info below, it appears that you have tried other OSes in the past and experienced the same problem.
> 3. Nvidia drivers: i downloaded and installed the Pop OS version that includes the Nvdia drivers. As far as I can see, all the drivers are installed and work correctly - if you know of test i can do to verify this, can you please let me know. 
In light of your plans to try Ubuntu again, perhaps you can forego further testing until you get the new OS installed. The only suggestion I would make would be to run the LiveUSB first. No point in installing a system that the LiveUSB already indicates will be problematic.

Also, start with the LTS. If that has same problems as above, then go to latest standard release. We don't know your HW, but if it is too new, sometimes you need the latest release.

---

### Post by optmed on 2021-09-27
excellent, many thanks DuckHook for your patiences and help. I'll get back to the forum on this as soon as I have Ubuntu up & running. 

kind regards

---

