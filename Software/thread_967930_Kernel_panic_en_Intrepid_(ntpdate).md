---
title: "Kernel panic en Intrepid (ntpdate)"
date: 2008-11-02
forum: Software
---

### Post by Marcos on 2008-11-02
Hola a todos :)
Hace dos días realicé una instalación limpia de Intrepid en mi DD. Todo funciona perfecto, incluso a detectado parte de mi hardware que en versiones anteriores no detectaba.

El problema es que tras cierto tiempo funcionando (indeterminado), aparece el temido kernel panic en forma de luces :biggrin: (parpadean las luces de las teclas Bloq mayús y despl), con el respectivo bloqueo del computador que me obliga a reiniciar.

En un momento pensé que podía ser mi tarjeta de red d-link, que ya presentó errores en Gutsy de la misma manera (incluso [consulté]("http://ubuntuforums.org/showthread.php?t=638876") sobre ello), por lo cual la desactivé. No tuvo resultados porque el problema persiste.

Ahora, mirando en /var/log/syslog encontré lo siguiente:
> Nov  2 10:57:35 escalier NetworkManager: <info>  (eth0): device state change: 7 -> 8 
Nov  2 10:57:35 escalier NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
Nov  2 10:57:35 escalier NetworkManager: <info>  Activation (eth0) successful, device activated. 
Nov  2 10:57:35 escalier NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Nov  2 10:57:36 escalier **ntpdate[5557]: adjust time server 91.189.94.4 offset 0.310566 sec**


Nov  2 12:32:08 escalier NetworkManager: <info>  (eth0): device state change: 7 -> 8 
Nov  2 12:32:08 escalier NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
Nov  2 12:32:08 escalier NetworkManager: <info>  Activation (eth0) successful, device activated. 
Nov  2 12:32:08 escalier NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Nov  2 12:32:08 escalier kernel: [   27.024027] wlan0: associate with AP 00:1c:f9:2f:4b:e0
Nov  2 12:32:08 escalier kernel: [   27.224026] wlan0: associate with AP 00:1c:f9:2f:4b:e0
Nov  2 12:32:08 escalier kernel: [   27.424040] wlan0: association with AP 00:1c:f9:2f:4b:e0 timed out
Nov  2 12:32:09 escalier **ntpdate[5530]: adjust time server 91.189.94.4 offset 0.402837 sec**
Destaco en negrita el ntpdate, que por tiempo, al parecer es la última acción antes del kernel panic. Se repite más de una vez y siempre es lo último antes de reiniciar.

Busqué en Launchpad y en Ubuntu Forums pero no encuentro errores muy relacionados (salvo el bug #[176844]("https://bugs.launchpad.net/ubuntu/+source/ntp/+bug/176844"), pero no estoy tan seguro si es lo mismo).

Saludos y de antemano gracias por leer :).

---

### Post by hictio on 2008-11-02
Solo por descartar... Pero probaste de hacer un 'sudo ntpdate 91.189.94.4' manualmente?
Digo, por esa infima casualidad que se te cuelgue...
Yo lo probe con mi Ibex y no me dio problemas.

Otra cosa, solo por chequear, descartaste totalmente algun problema de hardware? Agregaste algo nuevo, como por ejemplo, RAM?

---

### Post by Marcos on 2008-11-02
Hice un sudo ntpdate 91.189.94.4 y efectivamente, no es ese el error.

No he instalado ningún hardware nuevo, la máquina sigue igual que antes. Aún así me entró la curiosidad de si es un problema de hardware y esperé el último kernel panic y registré bien el momento en que ocurrió. Y me arrojó lo siguiente:
> Nov  2 18:31:10 escalier kernel: [ 3744.000080] usb 5-5: reset high speed USB device using ehci_hcd and address 4
Nov  2 18:37:00 escalier kernel: [ 4094.000066] usb 5-5: reset high speed USB device using ehci_hcd and address 4
Nov  2 18:40:12 escalier kernel: [ 4286.000078] usb 5-5: reset high speed USB device using ehci_hcd and address 4
Nov  2 18:41:29 escalier syslogd 1.5.0#2ubuntu6: restart.

Así que realicé un *lsusb*:
> Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 03f0:0604 Hewlett-Packard DeskJet 840c
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Un *dmesg | grep usb*, donde nuevamente aparece la misma sentencia:
> [  910.804025] usb 5-5: reset high speed USB device using ehci_hcd and address 3

Como dije en mi primer post, con Intrepid estaba contento porque había detectado parte de mi hardware que en versiones anteriores no detectaba. Uno de ellos es el Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External). Esto parece que es lo que está creando problemas... lástima :(

---

