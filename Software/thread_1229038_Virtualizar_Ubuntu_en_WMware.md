---
title: "Virtualizar Ubuntu en WMware"
date: 2009-08-01
forum: Software
---

### Post by barriobajero on 2009-08-01
Estoy intentando virtualizar ubuntu 9.0.4 en WMware. Pero no consigo instlalar las tools.La maquina real es windows XP.
Me sale un en el escritorio un imagen de un cd y abajo pone WMwareTools le doy doble click y paso los archivos que me salen al escritorio que son estos: VMwareTools-7.8.5-156735.i386.rpm, VMwareTools-7.8.5-156735.tar.gz y manifest.txt.
Despues abro el terminal e intento seguir esta guia por ejemplo: 
# tar xzvf VMwareTools-e.x.p-50460.tar.gz
# cd vmware-tools-distrib/
# sudo ./vmware-install.pl

En el primer comado lo que cambio es que pongo el numero de las tools 7.8.5.156735 y me sale. No se puede open: No existe el fichero ó directorio
tar: El error no es recuperable: salida ahora
tar: Child returned status 2
tar: Salida con error demorada desde errores anteriores

Si lo pongo tal cual con e.x.p-5460 tambien me sale lo mismo No se puede open: No existe el fichero ó directorio
tar: El error no es recuperable: salida ahora
tar: Child returned status 2 		

Tambien he iod dandole doble clcik hasta que me sale un carpeta que dice  vmware-tools-distrib. Le vuelvo a dar doble click y me sale el archivo vmware-install.pl le doy dobel click y no me hace nada.
Lo he intentado como usuario y normal y como superusuario.

---

### Post by sergiom99 on 2009-08-01
fijate si esto te sirve:
[http://www.fafamonge.com/2008/10/como-instalar-vmware-tools-sin-problemas.html](http://www.fafamonge.com/2008/10/como-instalar-vmware-tools-sin-problemas.html)

---

### Post by staar on 2009-08-01
si los archivos los tenés en el escritorio, entonces primero tenés que hacer cd a ese directorio, porque por defecto al abrir la terminal estás en tu home (el símbolo ~ representa el home del usuario logueado)...
```
cd Escritorio (o Desktop, depende)
tar xzvf VMwareTools-7.8.5-156735.tar.gz
cd vmware-tools-distrib/
./vmware-install.pl
``` y si en la guía cada comando está precedido por un #, quiere decir que deben ser ejecutados como super-usuario (o root), usando 'sudo' o haciendo 'su' antes...

saludos

---

### Post by barriobajero on 2009-08-01
Si lo hago como super usuario pero me dice que no existe el directorio y al intentar instalar  el essential-build E: No se pudo bloquear /var/lib/dpkg/lock - open (11 Recurso temporalmente no disponible)
E: Imposible bloquear el directorio de administración (/var/lib/dpkg/), ¿está otro proceso usándolo?
Lo he intentando grabando un cd de ubuntu y montándolo en daemoon tools y me da el mismo error al intentar instalar el essential builds. Y siempre que intento entrar en una carpeta con cd y el nombre de la carpeta me dice que no existe el fichero o directorio.

---

### Post by staar on 2009-08-01
en ubuntu (y en todos los unix) las mayúsculas importan, ponelas correctamente...

si te tira ese error es porque otro proceso está usando apt (el manejador de paquetes), puede ser alguna instancia de Synaptic, el update-manager corriendo en segundo plano, apt-get o aptitude, usá el Monitor del sistema para ver que proceso lo está haciendo, y esperá que termine...

saludos

---

### Post by fmsismo on 2009-08-01
Si seguis los paso que documente acá te tiene que andar.

[http://www.sismonda.com.ar/node/42](http://www.sismonda.com.ar/node/42)

Saludos

---

