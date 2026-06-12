---
title: "VMWare server 2"
date: 2009-04-20
forum: Software
---

### Post by NickCis on 2009-04-20
Bueno, ayer instale VMWare server 2. Usando el tutorial de este thread: [http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)

Tengo un par de preguntas. 
El VMWare se abre solo cuando prendo la pc?. Como puedo evitar que esto pase?.

Saludos.

---

### Post by josecuervo86 on 2009-04-20
Sacalo de la lsita de programas de inicio. Anda a **Sistema > Preferencias > Sesiones** y en la solapa **Programas de inicio** seleccionalo y desmarcalo o apreta en quitar

Se tendria que solucionar

---

### Post by NickCis on 2009-04-20
No aparece ahi. Osea, no estoy seguro si se abre solo.

El VMWare server 2 solo tiene interfaz web. Sin nececitar ejecutar al comnando o programa, entro a la pagina para administrar el VMWare( [https://127.0.0.1:8333](https://127.0.0.1:8333) ) y me aparece la pantalla para conexion. Por eso creo qeu se abre solo, y como lo estoy usando de vez en cuando para probar distros, no qiero un programa que me consuma ram.

Saludos.

---

### Post by guillermolisi on 2009-04-20
> **NickCis said:**
> No aparece ahi. Osea, no estoy seguro si se abre solo.

El VMWare server 2 solo tiene interfaz web. Sin nececitar ejecutar al comnando o programa, entro a la pagina para administrar el VMWare( [https://127.0.0.1:8333](https://127.0.0.1:8333) ) y me aparece la pantalla para conexion. Por eso creo qeu se abre solo, y como lo estoy usando de vez en cuando para probar distros, no qiero un programa que me consuma ram.

Saludos.
Una vez instalado el software de virtualizacion tendras cantidad de servicios corriendo en memoria para soportar la consola de administracion web o la ejecucion directa de una VM (esto se peude creando accesos directos a la VM que no es ni mas ni menso que una Url larguisima que abre una ventana con la VM que queres correr.

Para que suceda lo que vos pretendes podes parar los procesos/servicios de VMware (son varios y hay un orden para iniciarlos y pararlos) y cuando queres usar alguna VM primero los inicias y luego cargas la consola de administracion o el acceso directo.

No tengo una maquina con Ubuntu y Vmware hasta el fin de semana, pero si indagas en /etc/init.d deberias encontrar referencias a vmware y sus servicios.

---

### Post by sergiom99 on 2009-04-20
tiene que ser algo del estilo de:
/etc/init.d/vmware stop    (start para iniciarlo)

En CentOS es:
service vmware stop

---

### Post by NickCis on 2009-04-20
===========================================
EDIT: Problema solucionado al ejecutar el comando con privilegios de administrador (sudo).
Muchas gracias por toda la ayuda :D
===========================================
```
newpc@ubuntu-newpc:~$ /etc/init.d/vmware stop
Stopping VMware autostart virtual machines:
   Virtual machines                                                    done
Stopping VMware management services:
   VMware Virtual Infrastructure Web Access
   VMware Server Host Agent                                            done
Stopping VMware services:
   VMware Authentication Daemon                                       failed
   VM communication interface socket family:                          failed
   Virtual machine communication interface                            failed
   Virtual machine monitor                                            failed
   Bridged networking on /dev/vmnet0                                   done
   Host network detection                                              done
   DHCP server on /dev/vmnet1                                         failed
   Host-only networking on /dev/vmnet1                                failed
   DHCP server on /dev/vmnet8                                         failed
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                failed
   Virtual ethernet                                                   failed
newpc@ubuntu-newpc:~$ 

```

Ejecuto eso en consola. Pero parece que no cierra del todo el VMWare parte del mismo sigue en ejecucion.
Por que si entro a [https://127.0.0.1:8333](https://127.0.0.1:8333) en vez de darme la pantalla de "Falla de conexión" o de que la pagina no existe, me dice "503 Service Unavailable".

Lo que estoy buscando es que no consuma ram, creo que con lo que me dijeron el consumo disminuye. Pero no hay forma de cerrar totalmente el VMWare, que no quede nada de el abierto ?.

Saludos, y muchas gracias :P

---

### Post by fmsismo on 2009-04-20
Tenees que ejecutar el siguiente comando 

sudo /etc/init.d/vmware stop

Es un servicio, tenes que ser root para poder pararlo (por eso usas el sudo).

Saludos

---

### Post by NickCis on 2009-04-22
Recien me di cuenta, que al prender la computadora el servicio arranca automaticamente, no importa si la pc fue apagada con ese servicio parado (en "stop").

Como puedo evitar que este servicio arranque automaticamente?.

Saludos.

---

### Post by fmsismo on 2009-04-22
> **NickCis said:**
> Recien me di cuenta, que al prender la computadora el servicio arranca automaticamente, no importa si la pc fue apagada con ese servicio parado (en "stop").

Como puedo evitar que este servicio arranque automaticamente?.

Saludos.

[INDENT]sudo update-rc.d -f vmware remove[/INDENT]

Saludos

---

### Post by NickCis on 2009-04-23
Muchas gracias :P

---

