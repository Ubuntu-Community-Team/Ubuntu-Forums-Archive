---
title: "problema con el gestor de paqutes"
date: 2009-11-21
forum: Software
---

### Post by german6522 on 2009-11-21
tratando de instalar cualquier paquete:

paula@ubuntu:~$ sudo apt-get install gparted
E: dpkg se interrumpió, debe ejecutar manualmente «sudo dpkg --configure -a» para corregir el problema.

paula@ubuntu:~$ sudo dpkg --configure -a
dpkg: error en el análisis, en archivo «/var/lib/dpkg/updates/0027» línea cercana 0:
 nueva línea dentro del nombre del campo `#padding'

alguien tiene idea??desde ya muchas gracias

---

### Post by guillermolisi on 2009-11-23
Abri una consola/terminal y ejecuta exactamente lo que te recomienda el mensaje: > sudo dpkg --configure -a

---

### Post by granjero on 2009-11-23
me parece que ya ejecutó ese comando y obtuvo esta respuesta!

```
paula@ubuntu:~$ sudo dpkg --configure -a
dpkg: error en el análisis, en archivo «/var/lib/dpkg/updates/0027» línea cercana 0:
nueva línea dentro del nombre del campo `#padding'
```

salud!

---

### Post by guillermolisi on 2009-11-23
> **granjero said:**
> me parece que ya ejecutó ese comando y obtuvo esta respuesta!

```
paula@ubuntu:~$ sudo dpkg --configure -a
dpkg: error en el análisis, en archivo «/var/lib/dpkg/updates/0027» línea cercana 0:
nueva línea dentro del nombre del campo `#padding'
```salud!
:D Si, eso me pasa por responder cuando todavia no estoy despierto.

Entonces, seria conveniente revisar el contenido de "/etc/apt/sources.list" y de "/etc/apt/sources.list.d" para verificar que no haya repositorios fuera de version.

---

### Post by Mauro22 on 2009-11-23
Podes fijarte en synaptic en la parte de 'Paquetes Rotos' a ver que hay. Tambien se me ocurre purgar la carpeta /var/lib/dpkg/updates; y hacer un update.

---

