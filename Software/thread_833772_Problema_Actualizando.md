---
title: "Problema Actualizando"
date: 2008-06-18
forum: Software
---

### Post by h9005 on 2008-06-18
Hola al correr la actualización de sistema en ubuntu studio 7.10 me salta el siguiente problema: E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
 Hago lo que dice ahi y aparece esto:

Configurando flashplugin-nonfree (9.0.124.0ubuntu1~gutsy1) ...
Downloading...
--23:44:13--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `./install_flash_player_9_linux.tar.gz'
Resolviendo fpdownload.macromedia.com... 72.247.98.70
Conectando a fpdownload.macromedia.com|72.247.98.70|:80... 


falló: Expiró el tiempo de conexión.
Reintentando.

--23:47:23--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
  (intento: 2) => `./install_flash_player_9_linux.tar.gz'
Conectando a fpdownload.macromedia.com|72.247.98.70|:80... falló: Expiró el tiempo de conexión.
Reintentando.

--23:50:34--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
  (intento: 3) => `./install_flash_player_9_linux.tar.gz'
Conectando a fpdownload.macromedia.com|72.247.98.70|:80... dpkg: error al procesar flashplugin-nonfree (--configure):
 el subproceso post-installation script fue terminado por la señal (Interrupción)
Configurando kdelibs-data (4:3.5.8-0ubuntu3.4) ...

Configurando unzip (5.52-10ubuntu1.1) ...
Configurando cupsys (1.3.2-1ubuntu7.7) ...
Reloading AppArmor profiles : done.

Aparentemente trata de instalar el flash pero se cuelga ahi... como hago?

---

### Post by faktorqm on 2008-06-19
Y bueno por algun motivo no tenés internet, o no sabe resolver la dirección, esa direccion funciona. Si no podés probar de bajar el archivo, y ponerlo "a mano" en la carpeta /var/cache/apt/archives/ y ahi ya estaria para completar el proceso. Salu2!

---

### Post by h9005 on 2008-06-19
Internet sí tengo... y la direccion anda, pude bajar el paquete.

---

### Post by h9005 on 2008-06-19
Y no me deja mover el archivo a la carpeta que me decias.

---

### Post by faktorqm on 2008-06-19
hacelo con sudo mv, o sino sudo nautilus. Salu2!

---

