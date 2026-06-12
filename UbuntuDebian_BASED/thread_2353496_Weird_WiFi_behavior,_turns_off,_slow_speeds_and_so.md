---
title: "Weird WiFi behavior, turns off, slow speeds and some other things"
date: 2017-02-22
forum: Ubuntu/Debian BASED
---

### Post by fox_Rother on 2017-02-22
Distribution: elementaryOS 0.4 Loki (Ubuntu 16.04.2-based)
Notebook model: [HP Pavilion 14-n030br]("http://support.hp.com/us-en/product/HP-Pavilion-14-n000-Notebook-PC-series/5401217/model/6463635/document/c04025622/") (full specs on link)
Kernel version: 4.4.0-63-generic
WiFi card: RT3290 Wireless 802.11n 1T/1R PCIe
WiFi default driver: rt2800pci (generic)
WiFi driver[SIZE=2] I'm using[/SIZE]: modified version of rt3290sta from [this]("http://askubuntu.com/a/557427") link.

Okay, so let's get into trouble:
I have just installed and updated elementaryOS without any proprietary drivers.
The default WiFi driver behaves *very* weird. Just as I login, connection speeds reach ~35 Mbps (vs 50 Mbps+ on Windows). A few moments later it drops to less than 12 Mpbs and starts to disconnect all the time. Signal is always very weak during these tests.
I knew it was odd and checked my HW and drivers, then googled about it. Turns out the only "fix" available is a patched driver on the web. Okay, sure: download, compile and install. Signal strength improves a bit, connection speeds reach ~18 Mbps. Sometimes, however, it seems the card turns itself off. Then I try this:
```
sudo ifconfig reanmeX up
sudo service network-manager restart
```
Aaaaaaaand nothing happens. The only solution is to restart machine > turn card off > switch WiFi driver module > turn it back up > restart network-manager and get back to studies...

That's it. I'd just like to hear from more experienced users. Thanks! :o

---

### Post by wildmanne39 on 2017-02-22
Click on the wireless script in my signature and follow the directions for running it and posting the file it creates here using code tags.

---

### Post by fox_Rother on 2017-02-22
> **wildmanne39 said:**
> Click on the wireless script in my signature and follow the directions for running it and posting the file it creates here using code tags.

[ATTACH]273835[/ATTACH]

Here's another weird behavior: if I switch to rt2800pci and then back to rt3290sta, WiFi will work again. Also, when switching to rt2800pci, the card gets rfkilled.
I don't know if this other bit of information is relevant, but it seems rt2800pci can function on N mode, but takes a while to actually connect, as opposed to rt3290sta, which connects pretty much instantly on g or a mode (I guess)...

Maybe that's inaccurate, just trying to figure it out. Thank you! :P

---

### Post by wildmanne39 on 2017-02-22
There are several things that I see that can be changed to improve your connection, the rt2800 driver should work good with Ubuntu but it needs a parameter and it also works best with N speed disabled to the best of my knowledge.

For now do:
```
sudo apt-get purge bcmwl-kernel-source
```
Reboot, it looks like the rt3290sta driver you are using is old, then do:
```
sudo modprobe -rv rt3290sta
echo "options rt2800pci nohwcrypt=y" | sudo tee /etc/modprobe.d/rt2800pci.conf
sudo modprobe -v rt2800pci

```

Set your network settings in the network manager to match the screenshots:

Your country code needs to be set, please do:
```
sudo iw reg set BR
sudo sed -i 's/^REG.*=$/&BR/' /etc/default/crda
sudo  systemctl restart NetworkManager.service
```

---

### Post by fox_Rother on 2017-02-22
> **wildmanne39 said:**
> There are several things that I see that can be changed to improve your connection, the rt2800 driver should work good with Ubuntu but it needs a parameter and it also works best with N speed disabled to the best of my knowledge.

For now do:
```
sudo apt-get purge bcmwl-kernel-source
```
Reboot, it looks like the rt3290sta driver you are using is old, then do:
```
sudo modprobe -rv rt3290sta
echo "options rt2800pci nohwcrypt=y" | sudo tee /etc/modprobe.d/rt2800pci.conf
sudo modprobe -v rt2800pci

```

Set your network settings in the network manager to match the screenshots:

Your country code needs to be set, please do:
```
sudo iw reg set BR
sudo sed -i 's/^REG.*=$/&BR/' /etc/default/crda
sudo  systemctl restart NetworkManager.service
```

HECK YE, MAH MANG. Reaching ~40 Mbps after following your instructions and turning power management off. [SIZE=3]**Thank you very much! :D**[/SIZE]
There's only one thing that is making me a bit worried: Tx excessive retries. Goes 70 retries up every fast.com test. Any clues?

---

### Post by wildmanne39 on 2017-02-22
Please run the wireless script again now that you have made the changes so we can see what else we can change to improve performance.
Thanks

---

### Post by fox_Rother on 2017-02-23
> **wildmanne39 said:**
> Please run the wireless script again now that you have made the changes so we can see what else we can change to improve performance.
Thanks
Sure! Here it is :P
[ATTACH]273865[/ATTACH]

Edit: I have changed Channel to 6 and Channel Width to 20Mhz on my router, too. Still getting some (~20) Excessive retries per Fast.com run, though

---

### Post by wildmanne39 on 2017-02-23
The only thing that night help is to set your channel to a fixed setting of 6 in the router. 

Everything else is looking good.

---

### Post by wildmanne39 on 2017-02-23
I think that is most likely related to your link quality/signal strength, how far are you from the router? walls or floors maybe closed doors between the computer and router?

You could get a wifi extender and that will most likely help, signal is at 50 percent and that is about the lowest you can go and make a connection that has working internet.

---

