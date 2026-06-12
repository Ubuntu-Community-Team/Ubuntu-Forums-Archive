---
title: "Error al descargar actualizaciones"
date: 2008-12-14
forum: Software
---

### Post by Danikomdq on 2008-12-14
De golpe cada vez que quiero hacer una actualización, sea de soft instalado y desde el gestor de Synaptics me aparece este mensaje de error (copio textual):


E: dpkg was interrupted, you must manually run `dpkg --configure -a' to current problem.
E:_cache->open()failed, please report.


Aclaro que soy 100% nuevo en linux y 100% inexperto.

Gracias por la ayuda

---

### Post by santiagoward2000 on 2008-12-14
Hola!
Eso significa que hubo un problema con la conexión mientras se bajaba, y como dice, para arreglarlo tenés que abrir una terminal y correr:
```
sudo dpkg --configure -a
```
Suerte!

---

### Post by Danikomdq on 2008-12-14
Gracias, hice lo que me pasaste y me tiro esto:


Configurando libavutil49 (3:0.svn20080206-12ubuntu3) ...

Configurando libgsm1 (1.0.12-1) ...

dpkg: error al procesar libavcodec51 (--configure):
 El paquete está en un estado grave de inconsistencia - debe reinstalarlo
 antes de intentar su configuración.
Procesando activadores para libc6 ...
ldconfig deferred processing now taking place
Se encontraron errores al procesar:
 libavcodec51
daniel@daniel-desktop:~$ 
daniel@daniel-desktop:~$ 


El tema es que ha sido de repente, hace dos o tres dias hice actualizaciones e instale soft nuevo sin problemas

---

### Post by Danikomdq on 2008-12-14
Pasó algo extraño: reseteé la máquina y se solucionó el problema.
Si alguien es capaz de explicarme que paso, más que agradecido

---

### Post by faktorqm on 2008-12-15
Lo mas probable que haya ocurrido es que hayas instalado el paquete sin haber actualizado el indice de paquetes, permitiendotelo instalar pero quedando con dependecias incompletas, fallando en la configuracion del paquete. Cuando reiniciaste, el sistema actualiza la lista de paquetes cada vez que prendes la compu (en realidad esta funcion la cumple el gestor de actualizaciones) entonces se actualiza y resuelve el problema si es que habia alguno. 

Para que no te ocurra mas, por lo general se usa (sobre todo en ambito de servidores) usar lo siguientes comandos:

```
sudo apt-get install -udV <nombre_paquete>
```
```
sudo apt-get install <nombre_paquete>
```

Entonces el primer comando, lo baja pero no lo instala, entonces si hay problemas durante eso te avisa y no rompiste nada del sistema, si bajo bien, lo instalas. Yo en mi casa, en el 99% de los casos nunca tuve drama, pero siempre es una seguridad hacerlo en ambitos "peligrosos" como ser servidores y demases. Salu2!

---

