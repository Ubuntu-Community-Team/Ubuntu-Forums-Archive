---
title: "Teclado y Wifi en una MSI Wind"
date: 2010-05-31
forum: Software
---

### Post by jorgito on 2010-05-31
Hola a todos, 

En una netbook MSI Wind U100, con una instalación limpia de Lucid, estoy viendo que cada rato se bloquea el teclado o se corta la conexion wifi.

Aca va un extracto del resutado de dmesg:

```


[   12.617918] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[   12.621390] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[   12.621401] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[   13.805835] composite sync not supported
[   13.941815] composite sync not supported
[   14.077803] composite sync not supported
[   14.958228] usb-storage: device scan complete
[   14.960454] scsi 2:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[   14.965772] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   14.970921] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   16.065603] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[   16.065619] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[   16.069408] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[   16.069416] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[   16.772149] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 212
[   17.636066] ERROR!!! RTMPCancelTimer failed, Timer hasn't been initialize!
[   22.068043] wlan0: no IPv6 routers present
[   24.905887] composite sync not supported
[   25.054013] composite sync not supported
[   25.189965] composite sync not supported
[   26.782388] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[   26.782398] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[   26.785880] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[   26.785891] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[   30.559036] composite sync not supported
[   32.192840] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 212
[   32.193451] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
[   67.284165] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 212
[  107.285149] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 212
[  167.290465] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 212
[  247.284154] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 212
[  296.311157] ERROR!!! RTMPCancelTimer failed, Timer hasn't been initialize!
[  301.420125] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 212
[  347.288223] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 212
[  467.289148] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 212


```

El aviso de rt_ioctl_giwscan se repite seguido. El error mas esporadicamente pero sigue. Lo mismo con el cuento del composite sync not supported.


Aca extracto de Xorg.0.log

```

(II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
(II) intel(0): EDID vendor "HSD", prod id 1001
(II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)


```

Alguien tiene una idea si algo de esto puede tener que ver con los cuelgues de teclado y wifi?

Saludos y desde ya muchas gracias!

---

