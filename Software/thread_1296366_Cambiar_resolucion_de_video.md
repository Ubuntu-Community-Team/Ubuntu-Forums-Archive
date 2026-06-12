---
title: "Cambiar resolucion de video"
date: 2009-10-20
forum: Software
---

### Post by autusgo on 2009-10-20
Listo!
Borré esa linea, supongo que lo único que me queda es esperar.

Ahora sí... Bootié en Recovery Mode arreglé los paquetes rotos (o eso creo), pero ahora cuando reinicié tengo la PC en 800x600 y no pude cambiarlo. Alguna pista? Supongo que desconfiguraron los dirvers de la placa de video o algo... Pero la resolución más alta que me ofrece es 800x600 cuando tengo un monitor de 22'' con DVI... Un desperdicio jeje.
Estuve mirando cosas en internet y tratando de toquetear en System Settings, pero hasta ahora no lo pude cambiar. Cuando vuelva del trabajo sigo probando. Cualquier ayuda es bienvenida.

Gracias!

---

### Post by josecuervo86 on 2009-10-20
Anda a una terminal y escribi esto:
```
gedit /etc/X11/xorg.conf
```

Copia la información que contenga el archivo de texto que se abre y pegala aca, despues vemos como seguimos

---

