---
title: "KVM Audio Passthrough"
date: 2018-06-11
forum: Virtualisation
---

### Post by combinedeffort2 on 2018-06-11
[Background]
I have a kvm guest that runs as my audio server. I'm using snapcast to push audio around the house to raspberry pi/hifiberry nodes, specifically using the librespot plug-in. I'm now trying to add Google Cast support in the form of a Chromecast Audio plugged into the line-in of my host motherboard.
[/Background]

I've tried doing a PCI passthrough on my in-built soundcard, but I don't think my motherboard supports such a thing as virt-manager complained bitterly. I next briefly looked into getting a USB soundcard w/ line-in I could passthrough, but this seemed to be a minefield of compatibility issues just to get one working against the host, let alone the guest. I thought I'd finally solved it by using [https://github.com/b-fitzpatrick/cpiped](https://github.com/b-fitzpatrick/cpiped) to capture line-in audio on the host and redirect the results to a fifo pipe the guest listened to using 9p and trans=virtio, however, it appears named pipes aren't supported on 9p using virtio as I wasn't seeing any data appear at the guest end of the pipe.

So... does anyone have any ideas what my options are regarding getting line-in audio to a virtualised guest? It feels like this should be able to work using KVM and pipes but my KVM-fu just isn't good enough!

---

### Post by KillerKelvUK on 2018-06-11
Not a virtualisation solution but would Pulseaudio redirection of the source over IP not work?

---

### Post by combinedeffort2 on 2018-06-11
Ah, interesting, something like this? [https://wiki.archlinux.org/index.php/PulseAudio/Examples#PulseAudio_over_network](https://wiki.archlinux.org/index.php/PulseAudio/Examples#PulseAudio_over_network)

---

### Post by KillerKelvUK on 2018-06-11
Yup that's the one, I remember playing around with this on my pi3 with the Alexa API and a AirPlay receiver cept the mic and speakers were connected to my main workstation. Was fiddly and I recall the Avahi implementation on the pi was buggy but I had this stable and responsive...was redirecting the audio in from my usb webcam as the mic source for the Alexa Daemon on the pi...was pretty cool.

---

### Post by TheFu on 2018-06-12
I don't do much audio.  Just simple DLNA streaming or local (via NFS) playback using cmus or clementine or kodi.

Hardware passthru doesn't allow sharing with the host.  It is exclusively provided access only to the specific client.  The host has ZERO access.   So, if you want USB passthru to work, the device gets passed through and the guest VM needs to have the drivers. The host doesn't touch that USB device.
 For PCI passthru to work, the motherboard needs to support VT-d and the guest OS needs to have the correct drivers for the PCI device passed through.

You probably already knew this, but some lurkers may not.

---

### Post by combinedeffort2 on 2018-06-16
Thanks for all the replies. Whilst idly browsing whether I could use an SP/DIF input rather than line-in (I like to make life difficult), I came across this article ([https://linuxmusicians.com/viewtopic.php?t=10271](https://linuxmusicians.com/viewtopic.php?t=10271)) mentioning the StarTech 7.1 external sound card, which seems to work under linux. It has both linein and SP/DIF in and can hopefully be passed though to the guest via USB passthrough.

I'll update this post with my findings for visitors from the future.

---

### Post by combinedeffort2 on 2018-06-17
OK, the [COLOR=#000000]StarTech 7.1 external sound card passes through nicely, and I was able to attach a Google Chromecast Audio to it via the SP/DIF input and use cpiped to push audio from there to a FIFO pipe for snapserver to consume.[/COLOR]

---

