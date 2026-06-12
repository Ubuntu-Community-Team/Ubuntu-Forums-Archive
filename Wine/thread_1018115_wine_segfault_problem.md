---
title: "wine segfault problem"
date: 2008-12-21
forum: Wine
---

### Post by fetal on 2008-12-21
Hello,

rather new to linux, just intalled Ubuntu, latest version as well as wine.

Started this all yesterday so I know at least those are up to date.

Trying to install World of Warcraft, I followed instructions on the wow install page, copied over my WOW Folder from my other computer via network.

When I run wine Wow.exe I get ```
ghettorogue@ghettorogue-desktop:~/.wine/drive_c/Program Files/wow$ wine wow.exe
err:wineboot:pendingRename couldn't get file attributes (2)
Segmentation fault
ghettorogue@ghettorogue-desktop:~/.wine/drive_c/Program Files/wow$ 

```

```
ghettorogue@ghettorogue-desktop:~/AOE$ wine age2_x1.exe 
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on Logitech USB Headset, disabling mixer
fixme:system:SystemParametersInfoW Unimplemented action: 110 (SPI_GETSHOWIMEUI)
Segmentation fault
ghettorogue@ghettorogue-desktop:~/AOE$ 

```

That one goes to a black screen for a second before returning me back to the Segment Fault.

Further investigation proved that it could be a driver problem? However I downloaded and install the latest Nvidia drivers for my card. 177.82

Computer specs are as follows
Nforce 4 EVGA 131-K8-NF44-XX
CPU AMD Athlon FX 57 2.8 Mghtz
3 gigs ram
Nvidia GeForce GTX 280 1gb

The drivers I downloaded were [http://us.download.nvidia.com/XFree86/Linux-x86_64/177.82/NVIDIA-Linux-x86_64-177.82-pkg2.run]("http://us.download.nvidia.com/XFree86/Linux-x86_64/177.82/NVIDIA-Linux-x86_64-177.82-pkg2.run")
right off the Nvidia website.

Thanks.

---

### Post by fetal on 2008-12-22
bump

---

