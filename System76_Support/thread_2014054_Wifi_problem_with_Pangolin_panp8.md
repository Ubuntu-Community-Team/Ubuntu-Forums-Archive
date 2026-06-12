---
title: "Wifi problem with Pangolin panp8"
date: 2012-07-01
forum: System76 Support
---

### Post by tvdog12345 on 2012-07-01
I have a Pangolin panp8. I have upgraded to Ubuntu 12.04 LTS. At the time of the upgrade, I installed Windows XP as well, in a separate partition.

I cannot connect to most wifi networks with Ubuntu. I can, however, connect to the same networks with the Windows XP Zero Configuration Manager. If I connect with Windows, I can reboot into Ubuntu and stay connected to the network. The problem is not universal, either - I have a Virgin Mobile "mifi" hub, and Ubuntu connects to that just fine (the mifi hub is normally just a few feet away, so the signal is very strong, if that matters). Occasionally I can connect to other (public) wifi networks with Ubuntu, but usually not - usually I need to connect with Windows and reboot, as I said before.

I had problems with wifi before upgrading to Ubuntu 12.04 (probably the same problem), but back then I didn't have Windows in a separate partition, so I didn't know whether the problem was hardware, software, or whatnot. Now that I can run Windows on this same machine, I know that it is some kind of issue with Ubuntu.

I would like to just connect to public wifi networks with Ubuntu, rather than connecting with Windows and rebooting. What would you recommend I do to troubleshoot this problem?

---

### Post by isantop on 2012-07-02
> **tvdog12345 said:**
> I have a Pangolin panp8. I have upgraded to Ubuntu 12.04 LTS. At the time of the upgrade, I installed Windows XP as well, in a separate partition.

I cannot connect to most wifi networks with Ubuntu. I can, however, connect to the same networks with the Windows XP Zero Configuration Manager. If I connect with Windows, I can reboot into Ubuntu and stay connected to the network. The problem is not universal, either - I have a Virgin Mobile "mifi" hub, and Ubuntu connects to that just fine (the mifi hub is normally just a few feet away, so the signal is very strong, if that matters). Occasionally I can connect to other (public) wifi networks with Ubuntu, but usually not - usually I need to connect with Windows and reboot, as I said before.

I had problems with wifi before upgrading to Ubuntu 12.04 (probably the same problem), but back then I didn't have Windows in a separate partition, so I didn't know whether the problem was hardware, software, or whatnot. Now that I can run Windows on this same machine, I know that it is some kind of issue with Ubuntu.

I would like to just connect to public wifi networks with Ubuntu, rather than connecting with Windows and rebooting. What would you recommend I do to troubleshoot this problem?

When you upgraded to 12.04, did you perform a fresh installation or did you use the upgrade tool from 11.10?

I think a good first step would be to try running your laptop from a LiveCD of Ubuntu 12.04. That will tell me if there is something wrong with your installation, or if it's something with hardware.

---

### Post by CaptSaltyJack on 2012-07-05
There is a known issue in the Linux kernel that is causing this problem. I don't know if it's fixed as of the latest Ubuntu 12.04 kernel. If not, I'm hoping System76 can offer a patch through their own drivers.

---

