---
title: "No puedo desistalar netbeans..."
date: 2009-07-14
forum: Software
---

### Post by Just64 on 2009-07-14
Me baje el IDE Netbeans 6.7 y lo quiero desinstlar pero no puedo.
Desde synaptic no me aparece. 
Sudo aptitude remove tampoco me aparece.
¿Como puedo hacer? Lo instale bajandolo desde la pagina oficial.

---

### Post by Hei Ku on 2009-07-14
Podes detallar los pasos que seguiste para instalarlo?

---

### Post by Just64 on 2009-07-14
Me baje el xxxx.sh desde la pagina oficial, y despues desde la consola hice un
$ sudo sh xxxx.sh

---

### Post by Hei Ku on 2009-07-14
Fijate si no te dejo un README que diga cómo desinstalarlo.

También fijate si en la carpeta donde lo instalaste no hay un archivo que se llame uninstaller.

---

### Post by Just64 on 2009-07-15
No tengo ni idea donde lo instalo :$, hice un $ whereis uninstaller y solo me salio el del wine :S

---

### Post by Hei Ku on 2009-07-15
Dónde lo instalaste? Te fijaste en /opt?

---

### Post by euzkoarima on 2009-07-16
Yo instalé también Netbeans "a mano" y me agregó un lanzador en:
Aplicaciones -> Programación -> Netbeans IDE

Si te fijas en la propiedades te va a mostrar (en comando) algo como:

/bin/sh "/ruta/a/donde/lo-puso/bin/netbeans"

Entonces en /ruta/a/donde/lo-puso está el uninstall.sh que buscás.

Saludos,
Eduardo

---

