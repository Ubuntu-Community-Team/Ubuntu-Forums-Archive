---
title: "Wireless bluetooth headphone not default sink after laptop is online."
date: 2021-12-04
forum: Ubuntu/Debian BASED
---

### Post by atvt on 2021-12-04
I use a Lenovo T480s Laptop with Thunderbolt Docking station which is connected to secondary monitor.  I use Sony Wireless headphones & it is connected via bluetooth. 


Now everytime there is a power cut & power comes back my sink & sources are restored to default. 




$pactl list short sinks
2    alsa_output.pci-0000_00_1f.3.analog-stereo    module-alsa-card.c    s16le 2ch 44100Hz    SUSPENDED
3    bluez_sink.00_18_09_A2_FC_4B.a2dp_sink    module-bluez5-device.c    s16le 2ch 44100Hz    SUSPENDED
27    alsa_output.usb-Lenovo_ThinkPad_Thunderbolt_3_Dock_USB_Audio_000000000000-00.analog-stereo    module-alsa-card.c    s16le 2ch 44100Hz    SUSPENDED




$pactl list short sources
3    alsa_output.pci-0000_00_1f.3.analog-stereo.monitor    module-alsa-card.c    s16le 2ch 44100Hz    SUSPENDED
4    alsa_input.pci-0000_00_1f.3.analog-stereo    module-alsa-card.c    s16le 2ch 44100Hz    SUSPENDED
5    bluez_sink.00_18_09_A2_FC_4B.a2dp_sink.monitor    module-bluez5-device.c    s16le 2ch 44100Hz    SUSPENDED
52    alsa_output.usb-Lenovo_ThinkPad_Thunderbolt_3_Dock_USB_Audio_000000000000-00.analog-stereo.monitor    module-alsa-card.c    s16le 2ch 44100Hz    SUSPENDED
53    alsa_input.usb-Lenovo_ThinkPad_Thunderbolt_3_Dock_USB_Audio_000000000000-00.mono-fallback    module-alsa-card.c    s16le 1ch 44100Hz    SUSPENDED


Now everytime there is a powercut, I have setup an alias which fixes this issue.


alias soundfix='pactl set-default-source alsa_input.pci-0000_00_1f.3.analog-stereo ; pactl set-default-sink  bluez_sink.00_18_09_A2_FC_4B.a2dp_sink'




& I am connected to Bluetooth & laptop mic by default.


How can I fix it to have above as default on OS if they are connected. 




Or can this command automatically be run everytime laptop is connected from battery to online power source.

---

