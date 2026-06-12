---
title: "pcmcia RME soundcard not reconized"
date: 2014-04-21
forum: Ubuntu Studio
---

### Post by sylvain-mavon on 2014-04-21
Hello !

I have a problem trying to install a new soundcard to my computer under ubuntu studio 12.04 : a Dell latitude E6410.
The card is a RME Hammefall Multiface I and it's linked to the PC with a daughterboard express card (pcmcia) RME HDSPe.

I have taken a method for forums but without success...

I have loaded snd-hdsp module to the kernel,
installed alsa-tools ans alsa-firmware-loaders,
downloaded the specific alsa-firmware fot their website ans ran ./configure, make and make install,
I have modified the /etc/modprobe.d/alsa-base.conf file to put my internal soundcard to index 1 and to let sdn-hdsp to the index 0...

But hdsploader doesn't work :
```
sphere-Studio:~$ hdsploader 
hdsploader - firmware loader for RME Hammerfall DSP cards
Looking for HDSP + Multiface or Digiface cards :
Card 1 : HDA Intel at 0xf6a60000 irq 44
```

The RME soundcard is not seen : 
```
sphere-Studio:~$ cat /proc/asound/cards
 1 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf6a60000 irq 44
```

Maybe it's a problem with pcmcia card, it seems than this laptop may have problem with pcmcia (i updated BIOS to the latest version)
I use dmesg to give you an idea of what happend when I unplug and plug the pcmcia card :
unplug : ```
[  266.535687] pcmcia_socket pcmcia_socket0: pccard: card ejected from slot 0
[  266.535693] ohci_hcd 0000:04:00.0: HC died; cleaning up
[  266.535704] ehci_hcd 0000:04:00.1: HC died; cleaning up
[  266.566461] ohci_hcd 0000:04:00.0: PME# disabled
[  266.575356] ohci_hcd 0000:04:00.0: remove, state 0
[  266.575366] usb usb3: USB disconnect, device number 1
[  266.575665] ohci_hcd 0000:04:00.0: USB bus 3 deregistered
[  266.575779] ohci_hcd 0000:04:00.0: PCI INT A disabled
[  266.575815] ehci_hcd 0000:04:00.1: PME# disabled
[  266.582303] ehci_hcd 0000:04:00.1: remove, state 4
[  266.582315] usb usb4: USB disconnect, device number 1
[  266.582601] ehci_hcd 0000:04:00.1: USB bus 4 deregistered
[  266.582727] ehci_hcd 0000:04:00.1: PCI INT A disabled
```
plug
```
[  270.782831] pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0
[  270.782866] pci 0000:04:00.0: [1033:0035] type 0 class 0x000c03
[  270.782907] pci 0000:04:00.0: reg 10: [mem 0x00000000-0x00000fff]
[  270.783074] pci 0000:04:00.0: supports D1 D2
[  270.783078] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot
[  270.783087] pci 0000:04:00.0: PME# disabled
[  270.783125] pci 0000:04:00.1: [1033:00e0] type 0 class 0x000c03
[  270.783162] pci 0000:04:00.1: reg 10: [mem 0x00000000-0x000000ff]
[  270.783327] pci 0000:04:00.1: supports D1 D2
[  270.783330] pci 0000:04:00.1: PME# supported from D0 D1 D2 D3hot
[  270.783338] pci 0000:04:00.1: PME# disabled
[  270.783376] pci 0000:04:00.0: BAR 0: assigned [mem 0xf1c00000-0xf1c00fff]
[  270.783386] pci 0000:04:00.0: BAR 0: error updating (0xf1c00000 != 0xc00000)
[  270.783391] pci 0000:04:00.0: BAR 0: set to [mem 0xf1c00000-0xf1c00fff] (PCI address [0xf1c00000-0xf1c00fff])
[  270.783396] pci 0000:04:00.1: BAR 0: assigned [mem 0xf1c01000-0xf1c010ff]
[  270.783405] pci 0000:04:00.1: BAR 0: error updating (0xf1c01000 != 0xc01000)
[  270.783409] pci 0000:04:00.1: BAR 0: set to [mem 0xf1c01000-0xf1c010ff] (PCI address [0xf1c01000-0xf1c010ff])
[  270.783560] ohci_hcd 0000:04:00.0: enabling device (0000 -> 0002)
[  270.783578] ohci_hcd 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[  270.783764] ohci_hcd 0000:04:00.0: setting latency timer to 64
[  270.783774] ohci_hcd 0000:04:00.0: OHCI Host Controller
[  270.783899] ohci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 3
[  276.272759] ohci_hcd 0000:04:00.0: USB HC takeover failed!  (BIOS/SMM bug)
[  276.272768] ohci_hcd 0000:04:00.0: can't setup
[  276.272777] ohci_hcd 0000:04:00.0: USB bus 3 deregistered
[  276.273003] ohci_hcd 0000:04:00.0: PCI INT A disabled
[  276.273009] ohci_hcd 0000:04:00.0: init 0000:04:00.0 fail, -16
[  276.273019] ohci_hcd: probe of 0000:04:00.0 failed with error -16
[  276.273202] ehci_hcd 0000:04:00.1: enabling device (0000 -> 0002)
[  276.273217] ehci_hcd 0000:04:00.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[  276.273291] ehci_hcd 0000:04:00.1: EHCI Host Controller
[  276.273754] ehci_hcd 0000:04:00.1: new USB bus registered, assigned bus number 3
[  276.294947] ehci_hcd 0000:04:00.1: irq 18, io mem 0xf1c01000
[  276.294970] ehci_hcd 0000:04:00.1: startup error -19
[  276.295038] ehci_hcd 0000:04:00.1: USB bus 3 deregistered
[  276.295165] ehci_hcd 0000:04:00.1: PCI INT A disabled
[  276.295169] ehci_hcd 0000:04:00.1: init 0000:04:00.1 fail, -19
```

For me I suspect an hardware problem with the pcmcia card... I have seen than this laptop may have pcmcia issues.
It makes one week I work onto this issue and I don't know what to try now...

Can you help me to try make this work ???
Thank you

Sylvain

---

### Post by rafraccuia on 2014-06-18
Hi,
did you solve your problem?
I had big issues with my Expresscard HDSPe, and solved it updating the expresscard firmware. Download flash update tool for PCI/Cardbus from RME website:
[http://www.rme-audio.de/en_downloads.php?page=content/downloads/en_downloads_driver&subpage=content/downloads/en_downloads_driver_hdspe](http://www.rme-audio.de/en_downloads.php?page=content/downloads/en_downloads_driver&subpage=content/downloads/en_downloads_driver_hdspe)

I did it with Windows, but I thing it's possible with Wine (I did it years ago, but don't remember how).
good luck and enjoy your Multiface: when working, as stable as a mountain, and really great converters!

---

