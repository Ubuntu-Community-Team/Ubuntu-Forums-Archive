---
title: "Apache en Ubuntu Desktop 12.04?"
date: 2012-11-18
forum: Software
---

### Post by biale on 2012-11-18
Durante una actualización observo que Ubuntu Desktop 12.04 viene con un servidor Apache instalado. Y compruebo que lo mismo pasa con Mint 13.

Alguien tiene idea para que lo necesita/ utiliza?

---

### Post by hictio on 2012-11-18
Estás seguro? Qué versión de Precise Pangolin? y cuál de Mint 13?
Yo no lo veo instalado en ninguno de los dos, tengo Linux Mint 13 MATE.

---

### Post by guillermolisi on 2012-11-18
Para algun programa que hayas incluido en la instalacion y que requiera de un web server local.

Tengo 12.04 (Xubuntu) y no tengo Apache2 activado ni instalado.

---

### Post by biale on 2012-11-19
@ictio: Me rectifico parcialmente: Mint 13 Cinnamon no tiene el apache instalado. Fué un mareo con los discos montados, estaba viendo la "/" del Ubuntu 12.04 bajo Vbox.

@Guillermo: Por ahora llego a la conclusión que se auto-instaló como paquete sugerido durante la instalación manual de synaptic. Del log de apt:

```

Start-Date: 2012-05-12  21:07:30
Commandline: aptdaemon role='role-commit-packages' sender=':1.67'
Install: menu:i386 (2.1.46ubuntu1), apache2-utils:i386 (2.2.22-1ubuntu1, automatic), libfile-ncopy-perl:i386 (0.36-1, automatic), libmime-types-perl:i386 (1.32-1, automatic), libaprutil1-dbd-sqlite3:i386 (1.3.12+dfsg-3, automatic), libept1.4.12:i386 (1.0.6~exp1ubuntu1, automatic), swish++:i386 (6.1.5-2.1, automatic), apache2.2-bin:i386 (2.2.22-1ubuntu1, automatic), docbook-xml:i386 (4.5-7ubuntu1, automatic), rarian-compat:i386 (0.8.1-5, automatic), libapr1:i386 (1.4.6-1, automatic), libaprutil1-ldap:i386 (1.3.12+dfsg-3, automatic), apache2:i386 (2.2.22-1ubuntu1, automatic), apache2.2-common:i386 (2.2.22-1ubuntu1, automatic), deborphan:i386 (1.7.28.5), libvte9:i386 (0.28.2-3ubuntu2, automatic), librarian0:i386 (0.8.1-5, automatic), dctrl-tools:i386 (2.18ubuntu1, automatic), info2www:i386 (1.2.2.9-24, automatic),

---------- Mirar aqui: ----------
 dwww:i386 (1.11.7), synaptic:i386 (0.75.9ubuntu1), apache2-mpm-worker:i386 (2.2.22-1ubuntu1, automatic), dialog:i386 (1.1-20111020-1, automatic), sgml-data:i386 (2.0.6, automatic), libvte-common:i386 (0.28.2-3ubuntu2, automatic), libaprutil1:i386 (1.3.12+dfsg-3, automatic), dlocate:i386 (1.02, automatic)
End-Date: 2012-05-12  21:07:48


```

Sucede que dwww es un paquete sugerido y lo selecciono en forma automatica:

```


dwww (Sugerencia de synaptic)

Toda la documentación en línea instalada se servirá mediante un servidor
HTTP local. Cuando sea posible, dwww convierte la documentación a HTML.
Necesita instalar un servidor de HTTP que pueda usar CGI y un navegador
web para leer la documentación.


```

¿Como sigo? !

Creo que la idea pasa por borrar a dwww y su apache2. No parece una buena idea tener un puerto abierto innecesariamente. Y el comando "ps" informa que el servicio esta activo. 

Guillermo: tenés synaptic instalado en Xubuntu?


OT/ Ubuntu 12.04 (Gnome-3) y Mint 13 no estan en producción. Solo estoy probando un poco las nuevas interfaces de usuario bajo VirtualBox /OT

---

### Post by guillermolisi on 2012-11-19
Si, tengo Synaptic instalado pero nunca sugirio, siquiera, instalar ese paquete opcional.

Te diria que pruebes desinstalar dwww via Synaptics, siempre que no indique que junto con ese paquete se iran otros que son utiles y/o importantes.

---

### Post by biale on 2012-11-20
Borrando primero a dwww y luego a apache2* todo queda como debiera y hasta ahora no han aparecido problemas...

---

