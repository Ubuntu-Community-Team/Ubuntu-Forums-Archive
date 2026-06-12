---
title: "Alguien sabe como sincronizar hora en red"
date: 2009-06-29
forum: Software
---

### Post by KaKuS on 2009-06-29
Bueno tengo una pequeña red con servidores y clientes, dicha red no tiene conexión a internet ni va a tenerla pero por una razón técnica del sistema que estoy corriendo tengo que tener todos los relojes sincronizados.

Tengo un equipo que se conecta a una antena GPS, levanta la hora exacta y la tira en la red en el protocolo que yo quiera. Este equipo es bastante pasivo en el sentido de que no tiene sistema operativo es todo electrónica, te da para configurarle IP y GMT.

Ahora que los puse en tema.... ¿Como hago para que todos mis equipos se pongan en hora con ese equipo?

vale aclarar que el 90% de los equipos de mi red tienen ubuntu desktop y server 9.10, los equipos tienen todos una dirección estática y también configure un DNS.

Gracias de antemano y disculpen mi ignorancia

---

### Post by gmunioz on 2009-06-29
Hola kak....:

Una posibilidad sería:

Hacer que  cron ejecute periódicamente el comando  ntpdate

mediante un script que contenga las líneas

```
#!/bin/bash 
/usr/sbin/ntpdate -u la-ip-de-tu-servidor
 
```

---

### Post by sergiom99 on 2009-06-29
Exactamente como dijo Gabriel.

Asi hago yo, salvo que lo hago contra un servidor externo.

---

### Post by KaKuS on 2009-06-30
> **gmunioz said:**
> Hola kak....:

Una posibilidad sería:

Hacer que  cron ejecute periódicamente el comando  ntpdate

mediante un script que contenga las líneas

```
#!/bin/bash 
/usr/sbin/ntpdate -u la-ip-de-tu-servidor
 
```

Muchas gracias... probando ;)

---

### Post by faktorqm on 2009-06-30
Hola, yo lo quise hacer contra los servidores externos (creo que use ntp.debian.org o algo parecido) por que estaban en la pagina del ntp y no se si por error mio (99,99% de probabilidad) o por que no me andaba, es decir, no sincronizaba nada. Lo hice segun el tuto publicado en el sitio del maestro sismo ([http://www.sismonda.com.ar/node/49](http://www.sismonda.com.ar/node/49)) que aunque es para server lei un poquito mas en la pagina oficial de ntp ([http://www.ntp.org/;](http://www.ntp.org/;) por cierto la pagina mas vieja que vi en años...) para hacerlo cliente. Obviamente no anduvo. ¿Como hacen ustedes? Gracias por todo y saludos!

---

### Post by biale on 2009-07-01
Faktorqm: No parece haber mucha ciencia: ¿Port udp 123 bloqueado?

Una estación de trabajo debería sincronizar en forma automática durante el arranque frío, no estoy muy seguro de que lo estuviera haciendo.

Siempre en mi estación de trabajo, directamente instale el paquete para sincronización ntp por servicio. La otra opción hubiera sido ejecutar un comando "croneado" como ya dijeron.

Saludos!

---

### Post by sergiom99 on 2009-07-01
Martín, yo uso este script en una desktop viejita que le atrasa el reloj. Primero lo sincronizo contra un ntp argentino y despues le paso esa hora al reloj del BIOS.

```
#! /bin/bash
ntpdate time.sinectis.com
hwclock --systohc

```

---

