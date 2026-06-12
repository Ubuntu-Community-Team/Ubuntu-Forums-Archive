---
title: "Multisesion en K3B"
date: 2011-04-26
forum: Software
---

### Post by Criminel on 2011-04-26
Hola,
Después de varios posteos en inglés aún no consigo solución para el problema que K3b y los demás softwares tienen en ubuntu 10.04 con las capacidades de multisesión.
Ninguno de los cd's o dvd's hechos en multisesión con Windows o Ubuntu 8.04 pueden leerse ahora en mi PC.
Alguien conoce una solución definitiva a esto?

Gracias.

---

### Post by guillermolisi on 2011-08-10
Si grabas un CD/DVD multisesion con 10.04, despues podes leerlos bien tanto en Linux como en Windows o directamente no te permite grabar ?

---

### Post by Criminel on 2011-08-10
Hola,gracias por la atención.

Directamente no me permite grabar. Es como si la multisesión no existiese en absoluto (aunque la opción aparezca en los soft).

---

### Post by guillermolisi on 2011-08-11
Te permite grabar con una unica sesion cerrada ?

---

### Post by Criminel on 2011-08-12
Sí, no importa el soft que use (Brasero, k3b, Nero for Linux) sólo graba como una única sesión cerrada,

---

### Post by guillermolisi on 2011-08-12
Que version de K3B estas usando ?

Tengo la 2.0.2 funcionando con KDE 4.7 y una unidad SATA LG supermulti y no tengo ese inconveniente.

---

### Post by Criminel on 2011-08-12
La versión es 1.91.0

---

### Post by guillermolisi on 2011-08-13
> **Criminel said:**
> La versión es 1.91.0
Proba actualizarlo de la siguiente forma > sudo add-apt-repository ppa:ferramroberto/linuxfreedomlucid && sudo apt-get update 
sudo apt-get install k3b
si queres mas info lee este thread [http://foro-ubuntu-guia.963965.n3.nabble.com/k3b-version-2-0-1-td1876969.html](http://foro-ubuntu-guia.963965.n3.nabble.com/k3b-version-2-0-1-td1876969.html)

---

### Post by Criminel on 2011-08-15
Gracias. El programa se actualizó (si entendí bien me lo hiciste cargar un repositorio que no tenía). El tema es que aun así los discos multisesión siguen sin poder montarse. 
Todavía no probé grabar nada. Hago un test y posteo el resultado.
Gracias otra vez.

---

### Post by guillermolisi on 2011-08-15
Asi es. Es un repositorio personal de alguien que se tomo el trabajo de empaquetar para Debian/Ubuntu la nueva version de K3b.

---

### Post by Criminel on 2011-08-16
Resultado de tratar de hacer una multisesión:

El soft graba una primera sesión sin problemas aparentes (poniendo de manera manual Start Multisession).
Al intentar cargar otros ficheros para hacer una segunda y última sesión en el disco el soft reconoce el CD, ve los archivos anteriores (es decir, reconoce la sesión abierta anterior) , carga los nuevos pero al darle la orden de grabar salta un cartel que pide un cd "appendable" como si el que está en la lectora no existiese.

¿alguna sugerencia?

---

### Post by Criminel on 2011-09-18
Hola. Sólo para decir que el problema sigue igual. Después de haber intentando grabar multisesión puedo decirles que aunque el soft parece reconocer la multi lo que sucede en realidad es que el disco se cierra en la primer sesión.
Ignoro a que pueda deberse.

Gracias por la atención dada mi requerimiento (G. Lisi, gracias) aunque el problema no esté resuelto.

---

### Post by guillermolisi on 2011-09-18
Un detalle que se me paso por alto desde el principio: Estas grabando datos o audio (CDA) ?

Si grabas audio (CDA) no es posible hacerlo multisesion. Obligatoriamente son de sesion unica y cerrada.

---

### Post by Criminel on 2011-09-19
Son siempre discos de datos unicamente.

---

### Post by EnriqueK on 2011-09-19
Te comento mi experiencia respecto a los DVDs.
Antes podía grabar multisesión en DVD-R usando K3b, ahora ya no puedo, solo me la acepta si uso regrabables DVD+RW , tampoco puedo con los DVD-RW
En definitiva, va a depender también del tipo y seguramente de la marca del disco que se use.
En base a lo anterior, si querés grabar DVD grabables, posiblemente pueda hacerlo en los DVD+R , no lo se por que nunca tuve la oportunidad.
Lo que hago y recomiendo es grabar  multisesión en DVD+RW y cuando se llene, volcarlo a un DVD-R  en usa sola sesión.

---

### Post by guillermolisi on 2011-09-19
> **EnriqueK said:**
> Te comento mi experiencia respecto a los DVDs.
Antes podía grabar multisesión en DVD-R usando K3b, ahora ya no puedo, solo me la acepta si uso regrabables DVD+RW , tampoco puedo con los DVD-RW
En definitiva, va a depender también del tipo y seguramente de la marca del disco que se use.
En base a lo anterior, si querés grabar DVD grabables, posiblemente pueda hacerlo en los DVD+R , no lo se por que nunca tuve la oportunidad.
Lo que hago y recomiendo es grabar  multisesión en DVD+RW y cuando se llene, volcarlo a un DVD-R  en usa sola sesión.
La funcionalidad de la unidad optica respecto de discos -r/-rw o +r/+rw depende exclusivamente del hardware que tenga la misma.
Algunas pueden trabajar indistintamente con ambas alternativas, otras en cambio solo con una de ellas.

Quise ver las caracteristicas de la unidad que tengo en esta maquina, con lshw y me arrojo esto:

> *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GH22NS50
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/dvd1
                logical name: /dev/dvdrw1
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: TN00
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom1
Al parecer no especifica si es compatible con la norma - o con la + pero no se me ocurre otro lugar donde consultar, ademas del manual de la unidad.

---

### Post by EnriqueK on 2011-09-19
> **guillermolisi said:**
> La funcionalidad de la unidad optica respecto de discos -r/-rw o +r/+rw depende exclusivamente del hardware que tenga la misma.
Algunas pueden trabajar indistintamente con ambas alternativas, otras en cambio solo con una de ellas.

El caso es que con el mismo equipo en una versión anterior de Ubuntu y misma marca de discos, si podía grabar DVD-R en multisesión, ahora con la 10.04 no puedo.
Tengo dos grabadoras, una LG antigua IDE y otra LiTE-ON SATA y en ambas presenta el mismo problema.
Tal vez sea cuestión de recompilar el kernel, pero ni idea de cual opción poner.
De todas maneras, no es buena idea grabar multisesión en DVD-R , solo es aceptable en los regrabables

---

### Post by Criminel on 2011-09-19
Gracias de nuevo por la info adicional. Sigo sin solución pero sí me gustaría comentar que el problema original se suscita tanto con DVD's como con CD's multisesión, (no importa si son RW, + o - R, siempre es el mismo inconveniente).

---

