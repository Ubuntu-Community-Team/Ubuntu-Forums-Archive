---
title: "Ubuntu 9.04 Instalació - Amd64"
date: 2009-06-18
forum: Software
---

### Post by Fistandantilus on 2009-06-18
Hola a Todos!, 

Ayer a la noche trate de migrar de Ubuntu 7.04 a 9.04, pero antes lo quise ver directamente desde live-cd...

Al tratar de iniciar el sistema desde live-cd me salio un error en el kernel en módulo powernow-k8, por lo que no pudo continuar el iniciado del sistema.

El error que me tiro es el siguiente: [B]powernow-k8: BIOS error - no PSB or ACPI _PSS objects

[/B]No me salio en conjunto con ningun otro error, unicamente ese...

Googleando unicamente pude encontrar este thread que le susede lo mas parecido que me pasa ami ([http://ubuntuforums.org/showthread.php?p=7241155](http://ubuntuforums.org/showthread.php?p=7241155)), al resto le saltaba este error al hibernar o en otro momento....

Al parecer susede al tener conectado distintos tipos de dispositivos de almacenamiento(en el caso del link anterior le pasaba al tener un hdd ATA y otro SATA), en mi caso es un hdd IDE y una grabadora de dvd SATA.

Probe de quitarle la alimentación al disco rigido y ver si asi al menos me iniciaba el live-cd, pero me sigue tirando el mismo error...

Si alguien tiene alguna info al respecto, de como solucionar este tema o de como(si se puede) deshabilitar ese modulo(onda -nolapic) para poder instalarlo, se lo agradecería!

Mi Maquina:
Mother: ASUS K8V-MX(o A8V-MX, no me acuerdo bien y estoy en el laburo)
Micro:   AMD Athlon 64 3200+
Ram:    2 x 1Gb DDR
Video:  ATI Radeon 9600Pro 256Mb

Desde ya muchas gracias!

---

### Post by staar on 2009-06-18
probá esto: al iniciar con el live cd, en la primera pantalla, apretá F6 para seleccionar las opciones avanzadas, y entre ellas seleccioná la que dice 'noacpi', e iniciá así (con enter)

saludos

---

### Post by Fistandantilus on 2009-06-18
Probe todas las combinaciones y deshabilitando todo...

Nada funco...

Voy a probar cuado llegue a casa de iniciar el live-cd de Ubuntu 7.04 que ya lo tengo instalado y funcionando pero cuando lo instale tenia todo IDE, despues me compre la grabadora SATA... 
Quiero chequear si es un problema q esta pasando ahora o viene desde hace rato...


Saludos

---

### Post by Fistandantilus on 2009-06-18
Acabo de probar con los live-cd de Ubuntu 7.04 y 7.10 y no tienen ningun problema...

Nose si es un problema especificamente de 9.04 o se viene arrastrando desde las versiones 8.04 en adelante...

Alguien tiene alguna idea como solucionar esto??

---

### Post by pablo.s on 2009-06-18
Con un disco de la version
Alternate, hace lo mismo?

---

### Post by Fistandantilus on 2009-06-18
No probe con alternate, ya no me kedan CD para quemar y probarlo...

Por otro lado capaz si me deje instalarlo con el alternate pero a la hora de iniciar el sistema calculo q me terminara tirando el mismo error... y de porsi ya en ese momento ya perdi la instalacion del 7.04 que tengo configurada, cosa q no me gustaria arriesgarme tanto. Quiero ver 1ero si puedo levantar el live-cd, al menos de alguna manera....

Saludos

---

### Post by Fistandantilus on 2009-06-18
Ahora mismo les estoy escribiendo desde live-cd del 9.04!!!! :D

Los problemas que me pasaron por lo visto sucede en muchas ASUS(principalmente en la mia), asi q lo explico para q si alguien tiene el mismo problema ya sabe como solucionarlo.

1) Chequear que este habilitado el "Cool&Quiet" desde el bios(yo no lo tenia habilitado), con eso se soluciona el problema del módulo powernow-k8
2) Agregar el parámetro "pci=nomsi" al nucleo(este es un problema con algunos bios de ASUS, con lo q no detecta los dispositivos S/ATA y no puede continuar con la ejecución del live-cd).

Gracias a los contestaron y me dieron ideas.

Saludos!

---

### Post by girelaine on 2012-01-04
> **Fistandantilus said:**
> 2) Agregar el parámetro "pci=nomsi" al nucleo(este es un problema con algunos bios de ASUS, con lo q no detecta los dispositivos S/ATA y no puede continuar con la ejecución del live-cd).

puff estoy al borde la locura, al parecer hay el mismo problema para ubuntu 11.10
Tengo también un ASUS K8V-MX con procesador AMD Athlon 64 3200+, no tengo mucha experiencia con ubuntu. El paso 1) ya lo he hecho, pero para el 2) ¿puede alguien decirme de manera sencilla o pasos a seguir para agregar ese parámetro "pci=nomsi"? no sé exáctamente donde tengo que escribirlo. ¿alguna captura de pantalla?

Gracias.

---

### Post by EnriqueK on 2012-01-05
No estoy seguro, pero creo recordar que si pulsás cualquier tecla al momento de arrancar el Live CD, te ba a mostrar una tabla de opciones.

---

