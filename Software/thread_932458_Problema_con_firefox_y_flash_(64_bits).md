---
title: "Problema con firefox y flash (64 bits)"
date: 2008-09-28
forum: Software
---

### Post by sartrejp on 2008-09-28
Hace un par de días que no puedo reproducir videos en flash. Los carga bien, pero reproduce 2 segundos y se queda quieto, si lo avanzo manualmente, reproduce 2 segundos más y se vuelve a parar. Alguien sabe que puede ser? no se si será a causa de alguna actualización o por otra cosa; si alguien tiene la respuesta.... gracias

---

### Post by leo_rockway on 2008-09-28
> **sartrejp said:**
> Hace un par de días que no puedo reproducir videos en flash. Los carga bien, pero reproduce 2 segundos y se queda quieto, si lo avanzo manualmente, reproduce 2 segundos más y se vuelve a parar. Alguien sabe que puede ser? no se si será a causa de alguna actualización o por otra cosa; si alguien tiene la respuesta.... gracias

Primero que nada tendrías que aclarar qué plugin de flash estás usando y en que versión.

---

### Post by guisheca on 2008-09-29
En un problema del flash, no se como se arregla, pero se que es del flash porque la laptop de mi hermana, que tiene winxp, tiene el mismo problema.
Saludos.

---

### Post by sartrejp on 2008-09-29
desinstalé todo, lo volví a instalar, saqué el pluigin flashnonfree, instalé el gnash, lo saqué, instalé y eliminé 10 veces el nspluginmwrapper que me daba errores hasta que en una de esas arrancó. No descarto que sea del flash el problema y me haya pasado la tarde del domingo paveando con plugins y leyendo sobre flash en 64 bits.
Gracias por la atención Igual

---

### Post by otiuq on 2008-09-29
Hola, pienso que navegando tambien se te cuelgan asi que trata de probar esto:

   1. Instalar Firefox 3.0.3 (última versión estable a fecha de hoy)
   2. Instalar Flash Plugin 10.0.12.10 (última versión disponible, aún en modo Release Candidate)
   3. Tienes el acceso directo en el blog de Adobe para Linux.
      [http://blogs.adobe.com/penguin.swf/](http://blogs.adobe.com/penguin.swf/)
   4. Una vez descargado, descomprimir con tar -xvzf flashplayer10_install_linux_091508.tar.gz -C /tmp
   5. Cambiar al directorio recién creado: cd /tmp/install_flash_player_10_linux
   6. Como root: ./flashplayer-installer
   7. Responder que sí a todo, salvo cuando pregunte por la ruta de instalación del navegador.
   8. Ahí indicarle: /usr/lib/firefox-3.0.3/


Via: [http://linuxhispano.net/portal/noticia/%C2%BFcuelgues-sitios-flash-firefox](http://linuxhispano.net/portal/noticia/%C2%BFcuelgues-sitios-flash-firefox)


Espero que esto te pueda ayudar:D

---

### Post by sartrejp on 2008-09-29
Voy a probarlo, la verdad es que una vez que adobe se digna a sacar una versión para linux 64, mejor probarlo, usarlo, para que siga desarrollando.
Había escuchado que anunciaban una posible versión de flash 10 para linux amd 64.
Después cuento que tal.
Gracias

---

### Post by leo_rockway on 2008-09-29
Yo vengo usando swfdec que funciona bastante bien y tiene versión nativa 64b.

---

### Post by sartrejp on 2008-09-29
Bajé la versión 10 de adobe flash, la descomprimí, pero manualmente llevé el libflashplayer.so a la carpeta de plugins de firefox y mozilla (que es lo que hace el instalador).
La verdad que funciona muy bien (hasta ahora al menos)
Desgraciadamente, es para 32 bits, aun no han cumplido con lo dicho, pero al menos anda.

---

