---
title: "Problema para actualizar ubuntu"
date: 2011-08-06
forum: Software
---

### Post by Criminel on 2011-08-06
Hola,
Hace varios días que no puedo cargar las actualizaciones.
El gestor las propone, yo las tildo, me pide la contraseña y luego vuelve a la ventana "creando estructuras de datos" sin descargar ni instalar nada.
Usando apt-get update se despliega el listado y cada línea comienza con un "0% ign" o algo así, como si ignorara las actualizaciones.

¿Alguna idea de a qué pueda deberse? 

Corro un 10.04 en PC de escritorio con Sempron AMD 32bits y 2 GB de RAM.
Gracias.

---

### Post by guillermolisi on 2011-08-06
Generalmente sucede cuando el servidor de repositorios que estas utilizando esta fuera de servicio.
Proba cambiando el origen de repositorios que tenes actualmente por el de otro pais.

Hay varios threads en este foro que hablan al respecto.

---

### Post by Criminel on 2011-08-07
Hola.
Hice lo sugerido y cambie varias veces los orígenes de repositorios pero el problema sigue exactamente igual.
¿Alguna otra cosa que me sugieran?

Gracias.

---

### Post by guillermolisi on 2011-08-07
Que pasa cuando en una terminal/consola ejecutas ```
sudo apt-get dist-upgrade
```?

---

### Post by Criminel on 2011-08-07
Pone esto antes de darle ok:

Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Calculando la actualización... Listo
Se actualizarán los siguientes paquetes:
  capplets-data dbus dbus-x11 evolution evolution-common evolution-plugins
  gnome-control-center icedtea-6-jre-cacao libdbus-1-3
  libgnome-window-settings1 libimobiledevice0 libpng12-0 libsmbclient
  libsndfile1 libsoup-gnome2.4-1 libsoup2.4-1 libwbclient0
  linux-headers-2.6.32-33 linux-headers-2.6.32-33-generic
  linux-image-2.6.32-33-generic linux-libc-dev openjdk-6-jre
  openjdk-6-jre-headless openjdk-6-jre-lib samba-common samba-common-bin
  smbclient winbind
28 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.
Necesito descargar 108MB de archivos.
Se utilizarán 4.096B de espacio de disco adicional después de esta operación.
¿Desea continuar [S/n]? ^C


¿le doy OK?

---

### Post by guillermolisi on 2011-08-08
> **Criminel said:**
> Pone esto antes de darle ok:

Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Calculando la actualización... Listo
Se actualizarán los siguientes paquetes:
  capplets-data dbus dbus-x11 evolution evolution-common evolution-plugins
  gnome-control-center icedtea-6-jre-cacao libdbus-1-3
  libgnome-window-settings1 libimobiledevice0 libpng12-0 libsmbclient
  libsndfile1 libsoup-gnome2.4-1 libsoup2.4-1 libwbclient0
  linux-headers-2.6.32-33 linux-headers-2.6.32-33-generic
  linux-image-2.6.32-33-generic linux-libc-dev openjdk-6-jre
  openjdk-6-jre-headless openjdk-6-jre-lib samba-common samba-common-bin
  smbclient winbind
28 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.
Necesito descargar 108MB de archivos.
Se utilizarán 4.096B de espacio de disco adicional después de esta operación.
¿Desea continuar [S/n]? ^C


¿le doy OK?
Si,ingresa "S" y conta como te fue. Te deberia pedir reiniciar ya que hay actualizacion del kernel.

---

### Post by Criminel on 2011-08-09
Bueno, el sistema parece haber actualizado aunque no me pidió reiniciar. Ignoro si esto último es importante o no.
De todos modos muchas gracias por la ayuda.
Por otro lado, sigo sin encontrar solución a esto: [http://ubuntuforums.org/showthread.php?t=1739972](http://ubuntuforums.org/showthread.php?t=1739972)
[http://ubuntuforums.org/showthread.php?t=1703672](http://ubuntuforums.org/showthread.php?t=1703672)

Parece un problema común a unos cuantos usuarios. Si podés orientarme a una solución te lo agradecería.

---

