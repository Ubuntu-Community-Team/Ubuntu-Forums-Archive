---
title: "Problemas con Samba y Wine"
date: 2008-10-24
forum: Software
---

### Post by Peter Smile on 2008-10-24
El día de ayer me dí cuenta que tengo un problema con Samba:
Cuando, usando Nautilus, intento listar los equipos de la red no aparece ninguno. Vale decir que todos los demás equipos en la red son equipos Windows.
Pero si intento conectarme a otro equipo usando su IP no encuentro ningún problema.

Me pareció buena idea reconfigurar Samba a mano pero no conseguí ningún avance así que decidí desisntalarlo, borrar la configuración e instalarlo de nuevo (más que nada por miedo a haber hecho alguna macana con la configuración).
Al desinstalarlo apt también desinstaló Wine y Winbind, y al reinstalar los tres paquetes me da el mismo error, el cual no puedo resolver.

```
sudo dpkg --configure samba
[sudo] password for petersmile: 
Configurando samba (3.0.28a-1ubuntu4.5) ...
 * Starting Samba daemons                                                [fail] 
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error al procesar samba (--configure):
 el subproceso post-installation script devolvió el código de salida de error 1
Se encontraron errores al procesar:
 samba

```

El problema original persiste de manera idéntica y ya se me acabaron las ideas. ¿Alguien tiene alguna idea de lo que ocurrió (y cómo resolverlo)?

Gracias por anticipado.

---

### Post by faktorqm on 2008-10-24
Primero, probaria ```
sudo apt-get install -f
``` para ver si no quedo algun paquete roto. Si todo esta ok, deberias leer aca: [http://ubuntuforums.org/showpost.php?p=4343317&postcount=3](http://ubuntuforums.org/showpost.php?p=4343317&postcount=3) y armarte tu propia configuracion. Salu2!!

---

### Post by Peter Smile on 2008-10-24
Gracias por responderme tan pronto.

Hice lo que me sugeriste y me dio la siguiente respuesta:```
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
0 actualizados, 0 se instalarán, 0 para eliminar y 1 no actualizados.
1 no instalados del todo o eliminados.
Se utilizarán 0B de espacio de disco adicional después de desempaquetar.
Configurando samba (3.0.28a-1ubuntu4.5) ...
 * Starting Samba daemons                                                [fail] 
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error al procesar samba (--configure):
 el subproceso post-installation script devolvió el código de salida de error 1
Se encontraron errores al procesar:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Con respecto a la configuración "a mano", ni siquiera tengo un directorio "/etc/samba". ¿Qué hago? ¿Creo el directorio y el archivo smb.conf?

---

### Post by faktorqm on 2008-10-24
No, tenes algun drama con el paquete en si. Vamos por partes, primero hace ```
sudo apt-get update
``` para actualizar la lista de paquetes, una vez terminado eso, hace ```
sudo apt-get remove samba --purge
``` y desinstalalo. Esta parte es fundamental que termine bien, cualquier cosa si te tiro error aca postea la salida y no hagas lo que sigue. Si termino bien, hace ```
sudo apt-get autoremove
```, luego ```
sudo apt-get clean
```, luego ```
sudo apt-get update
``` de vuelta. No es necesario reiniciar en el 99% de los casos en gnu/linux, pero para estar seguro hacelo.
Con la pc reiniciada, ahi hace ```
sudo aptitude install samba
```.
Espero que te funcione. Salu2!!!

---

### Post by sebastianabate on 2008-10-24
Muy probablemente tengas algún paquete descargado corrupto, y por eso falla al tratar de instalarlo. Para purgar todos los paquetes descargados tenés que hacer
```
sudo apt-get clean
```y después volvé a ejecutar
```
sudo apt-get install -f
```Va a volver a descargar los paquetes que no se instalaron correctamente y va a tratar de instalarlos y configurarlos.

NOTA: No te asustes que "sudo apt-get clean" lo único que hace es borrar los archivos .deb que se descargan cuando instalás algo con "apt-get install", y no los programas instalados en sí. Concretamente lo que hace es limpiar el directorio /var/cache/apt/archive. Yo lo ejecuto cada tanto para liberar espacio en disco.

---

### Post by Peter Smile on 2008-10-24
**faktorqm**:
Hice lo que me sugeriste y lamentablemente no ha funcionado. ```
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Paquetes sugeridos:
  openbsd-inetd inet-superserver smbldap-tools
Se instalarán los siguientes paquetes NUEVOS:
  samba
0 actualizados, 1 se instalarán, 0 para eliminar y 25 no actualizados.
Necesito descargar 4194kB de archivos.
Se utilizarán 10,1MB de espacio de disco adicional después de desempaquetar.
Des:1 http://ar.archive.ubuntu.com hardy-updates/main samba 3.0.28a-1ubuntu4.5 [4194kB]
Descargados 4194kB en 51s (81,5kB/s)                                           
Preconfigurando paquetes ...
Seleccionando el paquete samba previamente no seleccionado.
(Leyendo la base de datos ...  
224174 ficheros y directorios instalados actualmente.)
Desempaquetando samba (de .../samba_3.0.28a-1ubuntu4.5_amd64.deb) ...
Configurando samba (3.0.28a-1ubuntu4.5) ...
Generating /etc/default/samba...
 * Starting Samba daemons                                                [fail] 
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error al procesar samba (--configure):
 el subproceso post-installation script devolvió el código de salida de error 1
Se encontraron errores al procesar:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

**sebastianabate**:
Tampoco ha sido exitoso. O como diría nuestro vice "el resultado no es postivo", hasta ahora.
```
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
0 actualizados, 0 se instalarán, 0 para eliminar y 1 no actualizados.
1 no instalados del todo o eliminados.
Se utilizarán 0B de espacio de disco adicional después de desempaquetar.
Configurando samba (3.0.28a-1ubuntu4.5) ...
 * Starting Samba daemons                                                [fail] 
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error al procesar samba (--configure):
 el subproceso post-installation script devolvió el código de salida de error 1
Se encontraron errores al procesar:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Peter Smile on 2008-10-24
Me he quedado pensando en "cuándo comenzó todo" y no lo puedo asegurar como fuente, pero he estado jugando con vmware, y como parte de la instalación el software agrega un módulo de red al kernel. ¿Puede haber algún tipo de conflicto?

A mí, en primera medida no me parece que sea así, pero por las dudas se los comento.

Gracias por intentarlo.

---

### Post by faktorqm on 2008-10-24
Busque en google y hay mil que tuvieron el mismo problema, uno dice que lo soluciono haciendo 

```
sudo apt-get remove samba-common
sudo apt-get install samba
```

Probalo. Salu2!

---

### Post by Peter Smile on 2008-10-24
Muchachos, siguiendo el consejo de **faktorqm** hice un archivo de configuración, y ¡arrancó el demonio!.

Pero el problema persiste, sigo sin poder ver las otras máquinas en la red; aunque poniendo su dirección de ip no tengo problemas al conectarme.

---

### Post by faktorqm on 2008-10-24
Si, el problema era ese al final. HAce 

```
sudo apt-get purge samba
```

que supuestamente te borra tambien el archivo de configuracion, sino a mano podes hacer 

```
sudo rm /etc/samba/*
```

Me alegro mucho de que haya servido. Salu2!!!

---

### Post by Peter Smile on 2008-10-24
Bueno, aunque ya no da problemas el demonio par arrancar sigo con el mismo inconveniente.

**No lista los equipos windows conectados a la red**; ni siquiera a mi mismo equipo.

Lo que más me desconcierta es el hecho de que conecte sin problemas al poner la IP del equipo. Si a alguien se le ocurre alguna solución lo agradeceré.

PD: Wine ahora corre sin problemas (desde que dejó de dar error el demonio de samba).

---

