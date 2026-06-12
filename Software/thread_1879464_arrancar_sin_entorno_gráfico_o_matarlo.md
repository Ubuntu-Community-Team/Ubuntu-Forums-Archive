---
title: "arrancar sin entorno gráfico o matarlo"
date: 2011-11-11
forum: Software
---

### Post by asterix77 on 2011-11-11
¿alguien sabe como arrancar sin el entorno gráfico en Oneiric para usar solo la terminal, o en su defecto matarlo?

Saludos

---

### Post by mama21mama on 2011-11-11
```
sudo /etc/init.d/gdm stop
```
para parar la X

o forever
```
update-rc.d -f gdm remove
```

---

### Post by asterix77 on 2011-11-15
Al ejecutar el comando, me aparece lo siguiente:

$ sudo /etc/init.d/gdm stop
[sudo] password for xxxxx: 
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service gdm stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop gdm

$service gdm stop
stop: Unknown instance:
$

Al intentarlo con sudo:

$sudo service gdm stop
[sudo] password for xxxxx: 
stop: Unknown instance:
$


Saludos y gracias por la respuesta

---

### Post by guillermolisi on 2011-11-15
> **asterix77 said:**
> Al ejecutar el comando, me aparece lo siguiente:

$ sudo /etc/init.d/gdm stop
[sudo] password for xxxxx: 
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service gdm stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop gdm

$service gdm stop
stop: Unknown instance:
$

Al intentarlo con sudo:

$sudo service gdm stop
[sudo] password for xxxxx: 
stop: Unknown instance:
$


Saludos y gracias por la respuesta

Si corriste los comandos invocando "service" despues de haber detenido GDM via /etc/init.d es logico que te devuelva "Unknown instance" porque el servicio ya esta parado.

Volvelo a iniciar con "sudo service gdm start" y fijate que te cide.

---

### Post by asterix77 on 2011-11-16
mmm...  no había pensado en eso; pero cualquiera sea el caso, el asunto es que sigo viendo el entorno gráfico, con el escritorio y todo (haciendo lo anterior).

Lo ideal es que Oneiric me arranque en modo consola; o en su defecto si me arranca en forma gráfica, matar la interfaz gráfica.

Saludos

---

### Post by EnriqueK on 2011-11-16
Primero tenés que entrar a tty mediante
**Alt+Ctrl+F1**
Luego de logearte , ejecutá
**stop gdm**
Ojo, esta sentencia varía de acuerdo a la versión de Ubuntu, stop gdm corresponde usar en la 10.04, no uso Oneiric, por lo que no te puedo dar certezas.
Otra cosa que podés intentar en que al momento de iniciar sesión y al momento de logearte , podés elegir entre los escritorios que temes instalado, en mi caso al menos tengo la posibilidad de elegir iniciar sesión en "xterm" que supongo será para iniciar sesión en terminsl , nunca lo usé

---

### Post by gmunioz on 2011-11-16
Prueba:

1- Edita el archivo /etc/default/grub, para que al iniciar se vea al presionar mayúsculas el menu del grub.

sudo su
nano /etc/defaul/grub

**GRUB_HIDDEN_TIMEOUT=5**

Guarda el cambio y ejecuta
update-grub

2- Al reiniciar pulsa mayúsculas para ver el menu
En el menu del Grub edita cualquiera de las entradas 
(pulsando la tecla e sobre ella)
Selecciona la entrada de un kernel
y al final de la línea cambia el parámetro
**ro**
por
**rw init=/bin/bash**
Pulsa la tecla enter para aceptar los cambios
Pulsa la tecla b para que arranque el sistema con los nuevos parámetros.

---

