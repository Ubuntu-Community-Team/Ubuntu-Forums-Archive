---
title: "Suggestion: How about an easy 'workarounds' system? (if not implemented)"
date: 2008-09-12
forum: The Cafe
---

### Post by tom66 on 2008-09-12
OK, let's say the user comes across a live CD, pops it in, boots Ubuntu. He uses an unsupported wifi card. The idea is that a popup would come up, inform the user of this problem, and have a local set of workarounds (more could be fetched from the 'Net). For example, it could install ndiswrapper to solve the wifi issues (and apply necessary configuration). Of course, it would require a large database but I think it is doable. One thing I can say is that it stumped me for a while on my microphone port on my Dell Inspiron 1300 laptop not working, all that was required was adding a line to a file. Couldn't there be sets of scripts designed just for this purpose?

What does everyone think?

---

### Post by SunnyRabbiera on 2008-09-12
Something like that would be huge though, more then just a CD's worth of info.

---

### Post by tom66 on 2008-09-12
A local set of workarounds for critical things: wifi, display, cpu/motherboard (thermal, fan mostly, not the actual cpu/motherboard, that would be a paradox), modems, keyboards, mice and network/ethernet. Most of these pieces of hardware like the cpu, motherboard, display, mice and keyboards work fine, but there may be a few exceptions, so keep a database of them anyway. Then, once a network connection has been established, grab the full database of workarounds. On boot up or periodically, perhaps on the hour, scan the database and look for possible problems. Store model numbers of affected components and compare them to current hardware.

---

### Post by SunnyRabbiera on 2008-09-12
yes but if there is a wifi issue and you cannot connect wouldnt that defeat the purpose of your idea?

---

### Post by tom66 on 2008-09-12
Local database: critical systems required for getting full database - wifi, network, internal/external modems, motherboard/cpu thermal, keyboards, mice & display (basic VGA settings only).

Full database: non-critical systems, optional features, nice things - sound, pc speaker, 3d graphics, full-color graphics, full wifi (e.g. getting full g/n on an g/n wifi card, instead of just b), password/WEP support on wifi (perhaps this should be in local db?), full motherboard config allowing for things like wifi internet lights, touch screens, full networking speed, full configuration dialogs/GUIs for wifi (if required), and anything else that needs a workaround.

---

### Post by pp. on 2008-09-12
What you are suggesting is that the distro should try and recognize the hardware present in the computer it is being installed on, and that the distro should take the measures needed to make that hardware work with the distro.

That is, in effect, what all distros with hardware detection attempt to do.

In short, if the distro can correctly identify the hardware device, it usually makes it work. 

Ubuntu Linux does it to the extent that it only installs software which is subject to a license model which is consistent with the license of the whole distro.

---

### Post by tom66 on 2008-09-12
ndiswrapper, as far as I know, does not break any local laws... neither does adding a line to the /etc/<something> file. I'm suggesting an easy GUI to install these fixes/workarounds. Alert the user that their hardware may not be fully supported but that it can be fixed with a simple patch.

Linux has fair hardware support but a system like this would easily inform the user that their hardware may not be perfect.

---

### Post by smartboyathome on 2008-09-12
But distributing the drivers which are used with ndiswrapper **is** illegal, at least for Ubuntu. This is why you don't see those included with Ubuntu, as well as why you don't see NVidia's drivers included.

---

### Post by pp. on 2008-09-12
> **tom66 said:**
> I'm suggesting an easy GUI to install these fixes/workarounds. Alert the user that their hardware may not be fully supported but that it can be fixed with a simple patch.

You are presuming that the distribution is able to identify that particular hardware, and that the workaround solution is already established (in the case of the NIC at the time the distro is packaged).

> **tom66 said:**
> ndiswrapper, as far as I know, does not break any local laws... neither does adding a line to the /etc/<something> file. 

What has that to do with anything?

---

### Post by tom66 on 2008-09-12
It was a reference to distributing ndiswrapper, as far as I was aware, was legal. But I'm not sure. Maybe it is. It's definately not illegal to add a line to /etc/<something> (for enabling sound for example, which I had to do to get my microphone working.) I'm suggesting a full, central database of scripts to get things like this working. It's just a suggestion though. It might not be feasible.

---

### Post by pp. on 2008-09-12
Ndiswrapper appears to be a kernel module and can be presumed to be subject to the same license model as the whole distro. However, it is called a 'wrapper' because it 'wraps' another piece of software. That other piece of software is a Windows driver for the NIC, if I understand the procedure correctly. If there are licensing issues, I would presume that they would stem from those windows drivers.

Also, if a distro could reliably detect the exact type of some piece of hardware, and if it was known that a single line in a configuration file would make that hardware usable, I would rather fancy that the distro already included that crucial line upon detecting that piece of hardware.

Hence, I rather suspect that in most cases where such a workaround exist either the hardware can not be detected in a reliable manner or that the workaround was not known in time for it to be included in the distro.

---

### Post by tom66 on 2008-09-12
Okay,

I was talking about how identifying a device and adding a line to a config file to get the device working, was not illegal. In fact, it could be done by identifying the computer model or hardware, which can be done with dmidecode on most computers:

```

...
Handle 0x0A01, DMI type 10, 6 bytes
On Board Device Information
	Type: Sound
	Status: Enabled
	Description: Sigmatel 9200
...

```

With that information in mind, it could search the database for problems with Sigmatel 9200 sound cards in Linux, and alert the user that a fix is available for the microphone port. User says OK, it downloads the full patch (about 1 kb) from the 'net or looks in the local data, then installs it. Painless workaround system for problems with the drivers. I know there is a simple patch for this (for me it was adding a line to identify it as a microphone or something, one liner cut'n'paste), and I'll bet the same holds for many other devices.

Having the line by default is nice, however it could break devices. Hardware-detection and a central database is exactly what I am suggesting. Just notify the user of it. Sorry if this suggestion is a big vague.

---

