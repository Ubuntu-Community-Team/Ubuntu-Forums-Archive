---
title: "recommendation"
date: 2010-08-27
forum: The Cafe
---

### Post by nathang1392 on 2010-08-27
hi,

i have been using ubuntu on an old emachine. it has 384 mb of ram and a celeron processor. pretty old.

lately ubuntu has just been too heavy for it. just wondering if someone could suggest a light distro.

what i need:
something that makes it somewhat simple to install software, no compiling.

can do light java development.


thats about it really. appreciate any suggestions you guys can make. thanks.

---

### Post by wojox on 2010-08-27
You could try starting out barebones and working your way up [ Modest Spec or Barebones Installation of Ubuntu]("http://www.psychocats.net/ubuntu/minimal")

---

### Post by mamamia88 on 2010-08-27
mint xcfe?

---

### Post by psavva on 2010-08-28
I would highly suggest you try Xubuntu

It's Ubuntu, but lightweight.  

Check it out here : [http://www.xubuntu.org/](http://www.xubuntu.org/)

---

### Post by Austin25 on 2010-08-28
Or Lubuntu.

---

### Post by Dayofswords on 2010-08-28
> **Austin25 said:**
> Or Lubuntu.

This.

the torrent of it [http://people.ubuntu.com/~gilir/lubuntu-10.04.iso.torrent](http://people.ubuntu.com/~gilir/lubuntu-10.04.iso.torrent)

---

### Post by Plumtreed on 2010-08-28
I recommend and use Peppermint Ice, a very lightweight ubuntu fork. Google 'Peppermint OS'

---

### Post by M93 on 2010-08-28
yes i've tried both xubuntu and mint....both are very light but i liked xubuntu more because its more like ubuntu than mint is

---

### Post by nathang1392 on 2010-08-28
can anyone tell me about this peppermint os? it looks really good, does it have any drawbacks i should know about before installing? looks really fresh and something that would be a good alternative to ubuntu. i wanted to just put google chrome os on it, but im having trouble finding a download that i can install to the hard drive.

edit:
-------------------

found a download for chrome os. think i am going to try that for now.

---

### Post by Spice Weasel on 2010-08-28
> **nathang1392 said:**
> found a download for chrome os. think i am going to try that for now.

I thought ChromeOS wasn't released fully yet, and that you can only run it in a VM?

---

### Post by M93 on 2010-08-28
> **Spice Weasel said:**
> I thought ChromeOS wasn't released fully yet, and that you can only run it in a VM?

thats still true.

---

### Post by NightwishFan on 2010-08-28
Try Ubuntu Hardy, it is still supported and very stable. Trust me, you can get Ubuntu to be very trim. I have done a lot of research into it. I managed to have free -m report 13mb used in a command line system, and around 30mb using Xorg. Having a minimal system helps, however you can easily use gnome with more than 256mb.

1. Follow **some** of this guide: [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)  Particularly this section:
```
After installation you may want to blacklist some restricted modules: (if you want to save some memory)
      File /etc/default/linux-restricted-modules-common

DISABLED_MODULES="ath_hal fc fglrx fwlanusb ltm nv"
```

Please note, if you need any of those modules (nv for proprietary nvidia cards), do not add them to disabled modules.

I would advise **not** removing language packs as suggested.


2. Set Virtual Memory Swappiness to 100
```
sudo su
echo 'vm.swappiness=100' >> /etc/sysctl.conf
exit
```

This makes a big difference when using applications such as Firefox, and even on systems with a large amount of memory when running virtual machines.

---

### Post by nathang1392 on 2010-08-28
[http://chromeos.hexxeh.net/](http://chromeos.hexxeh.net/)

these are builds that are intended to be used as a live usb, but you can do this.


Log on to ChromiumOS, then press Ctrl+Alt+T
Execute /usr/sbin/chromeos-install
Follow prompts

you guys should try it. especially in my situation with an old computer. very very light, and very very functional at the same time.

---

### Post by cogar66 on 2010-08-28
Lubuntu is more lightweight than Xubuntu; it would probably suit your needs better.

---

