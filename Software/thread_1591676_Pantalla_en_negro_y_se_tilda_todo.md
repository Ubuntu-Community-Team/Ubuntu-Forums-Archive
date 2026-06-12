---
title: "Pantalla en negro y se tilda todo"
date: 2010-10-09
forum: Software
---

### Post by Applelnx on 2010-10-09
Hola ultimamente estoy teniendo el problema de que mientras uso mi laptop, en un momento se pone la pantalla negra y se tilda todo el sistema (no responde nada, ni el teclado). Puede ser que sea un problema de temperatura?

Me fije en /var/log/syslog y estos son los ultimos segundos registrados antes de que se detenga todo. Segun veo dice algo de que el kernel dejo de funcionar (si quieren puedo poner todo el log).

```
Oct  9 17:37:19 guille-laptop NetworkManager: <info>  Activation (wlan0) successful, device activated.
Oct  9 17:37:19 guille-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Oct  9 17:37:22 guille-laptop ntpdate[1793]: step time server 91.189.94.4 offset -0.627751 sec
Oct  9 17:37:22 guille-laptop kernel: [   54.021157] wlan0: no IPv6 routers present
Oct  9 17:37:49 guille-laptop kernel: [   80.557409] usb 1-3: USB disconnect, address 3
Oct  9 17:37:59 guille-laptop kernel: [   90.200148] wlan0: deauthenticating from 00:25:9c:46:c5:7b by local choice (reason=3)
Oct  9 17:37:59 guille-laptop kernel: Kernel logging (proc) stopped.
```

Alguno me podria dar una mano con este problema? Desde ya les agradezco que esten leyendo esto.

Saludos

PD: estuve teniendo problemas con el Power Manager y la duracion de bateria ([http://ubuntuforums.org/showthread.php?t=1563894](http://ubuntuforums.org/showthread.php?t=1563894))

---

### Post by guillermolisi on 2010-10-09
El mensaje dice que se detuvo el proceso que registra el log del kernel.

Recordando tu caso, para mi es significativo esto respecto del problema con la administracion de energia luego de que la maquina entre en modo suspendido.

---

### Post by Applelnx on 2010-10-10
Ok, vamos a ver si en unos dias cuando instale el Ubuntu 10.10 tengo alguna mejora. Gracias Guillermo. Saludos!

---

