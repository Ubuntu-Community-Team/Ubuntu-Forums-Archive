---
title: "[SOLVED] problemas con openoffice 3.0"
date: 2008-12-13
forum: Software
---

### Post by pachux on 2008-12-13
Hola, Hoy en las actualizaciones me bajé del repositorio el openoffice 3.0 .  El problema es que ninguna de sus aplicaciones llega a levantar nunca. Cuando reintento me aparece la ventana de recuperacion de archivos y después se baja de nuevo.
Ya probé reinstalarlo y nada.

---

### Post by Hei Ku on 2008-12-13
Que te aparece si lo ejecutas desde la terminal? Quizas tira algun mensaje q no aparece en pantalla?

---

### Post by pachux on 2008-12-14
Ahá, lo ejecuté y me tiró esto:


Error: "/var/tmp/kdecache-fabian" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-fabian" is owned by uid 1000 instead of uid 0.
fabian@kia:~$ QPainter::begin: A paint device can only be painted by one painter at a time.
QPainter::setWorldTransform: Painter not active
QPainter::begin: A paint device can only be painted by one painter at a time.
QPainter::setWorldTransform: Painter not active
QPainter::begin: A paint device can only be painted by one painter at a time.
QPainter::setWorldTransform: Painter not active
QPainter::begin: A paint device can only be painted by one painter at a time.
QPainter::setWorldTransform: Painter not active
QPainter::begin: A paint device can only be painted by one painter at a time.
QPainter::setWorldTransform: Painter not active
ASSERT: "slOpt" in file /build/buildd/kde4libs-4.1.3/kdeui/kernel/kstyle.cpp, line 3314
terminate called after throwing an instance of 'com::sun::star::container::NoSuchElementException'
KCrash: Application 'soffice.bin' crashing...
sock_file=/home/fabian/.kde/socket-kia/kdeinit4__0
X IO Error

¿Alguna idea de por donde empezar?

---

### Post by pachux on 2008-12-14
Bueno: vi en otro foro (kubuntu-es):parece que el problema es que openoffice no se integra bien con kde y yo tengo instalado kubuntu.Para el que tenga el mismo problema hay que borrar el paquete openoffice.org-kde. 
Saludos

---

