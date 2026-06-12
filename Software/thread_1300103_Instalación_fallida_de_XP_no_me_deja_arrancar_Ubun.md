---
title: "Instalación fallida de XP no me deja arrancar Ubuntu"
date: 2009-10-24
forum: Software
---

### Post by Hadso on 2009-10-24
Estimados, tengo el gusto de tener instalado Ubuntu en mi PC. 
Por razones que escapan a mi control, necesitaba instalar XP.
Tengo un disco de 80GB. 70 son de Ubuntu. 10, estaban sin formato. 
La cuestión es que me dió error la instalación de Windows. 
Ahora cuando arrancaría el GRUB, no arranca, trata de arrancar el supuesto Windows que quedó trunco. 
El mensaje que me aparece es el siguiente:
```
Falta NTLDR
CTRL ALT SUPR para reiniciar
```

Bueno, que tengo que hacer para volver a arrancar desde el GRUB?
Muchas gracias!

---

### Post by gmunioz on 2009-10-24
Hola had....:

Tal como te informan mùltiples post en el foro

Windows sobre escribe el mbr y borra el Grub.

Debes reinstalar el Grub, hay infinitos post

en el foro y en google.

---

### Post by igorin on 2009-10-26
iniciá con algún Live-CD, una vez cargado en ram:
Abrís un Terminal y tecleás:
#grub
>root (hdX,Y)
>setup(hdX)
>quit

Donde 'X' es el número de disco donde está instalado el grub (Si es el master debéis poner 0), y 'Y' es la partición donde tenéis instalado Linux. (Grub numera las particiones a partir de 0, así que si tenés linux instalado en la segunda partición, 'Y' deberá ser 1)

Una vez seguidos estos pasos, al reiniciar retirando el live-cd, verás que tenés la misma configuración de Grub que tenías antes de realizar la instalación del wintendo.

otra es descargar el [Super Grub Disk]("http://www.supergrubdisk.org/") que es un live para este tipo de operaciones pero con muchas más posibilidades.

Al iniciar elegis: Arreglar el arranque de Linux (GRUB) Fix boot of linux
luego de elegir la versión de grub a restaurar, te confirma el resultado positivo y luego a reiniciar sin el disco para comprobar el resultado.

---

### Post by Hadso on 2009-11-04
Funcionó! Muchas gracias!

---

