---
title: "libsensors no aparece en paquetes de anjuta"
date: 2008-10-14
forum: Software
---

### Post by MeduZa on 2008-10-14
hola, ¿alguien sabe porque no aparece el libsensors (sensors.h la vercion que sea) en paquetes de anjuta? instale varias librerias que necesito entre ellas sensors y las demas aparecen, pero este en particular no aparece y lo tengo que "linkiar a mano"

creo, que al instalarlo como que no se registra (pero el archivo esta y funciona perfectamente al linkiarlo a mano y poner #include <sensors/sensors.h>)

¿alguien sabe como solucionar esta molestia?

saludos

---

### Post by faktorqm on 2008-10-15
¿No deberia solucionarse cuando pones #include <sensors.h> en el programa y en el makefile, gcc blabla -I /algo/algo/sensors? Salu2!

---

### Post by MeduZa on 2008-10-15
> **faktorqm said:**
> ¿No deberia solucionarse cuando pones #include <sensors.h> en el programa y en el makefile, gcc blabla -I /algo/algo/sensors? Salu2!

si lo soluciono con -lsensors pero la idea es que apareciera aca:
[IMG]http://www.anjuta.org/documents/C/anjuta-manual/figures/project_info.png[/IMG]
[SIZE="2"]**imagen sacada de internet que solo viene al caso de ejemplo y nada tiene que ver con mi proyecto**[/SIZE]

pero bue... tengo miles de dudas y encontrar las respuestas en internet es practicamente imposible :( no se que pasa pero tardo mas buscando informacion que programando y para peor todo es nuevo y no entiendo una goma. ya saldre adelante.

Ahora estoy buscando como hacer que cuando instale me meta los .conf en la carpeta de configuraciones -.- es un maneje eso de autoconf y autotools:confused:

encima en los foros no ayuda mucho buscar, porque o no saben nada o le baten cualquiera!
sobre todo cuando haces preguntas de c++ y te dan respuestas con codigo c -.-

alguno sabe donde puedo sacar un tutorial de [COLOR=Red]c++[/COLOR] como la gente que no de ejemplos de [COLOR=Red]C[/COLOR], sino de [COLOR=Red]c++[/COLOR] y que ademas este basado en linux (mi aplicacion no va a correr en windows porque no es necesario y ademas se basa en otro programa que es de linux)

---

### Post by pendortxo on 2008-10-15
Te fijaste en [http://c.conclase.com/](http://c.conclase.com/) ahi tienen un par de cosas de C++ y esta todo basado en software libre.

---

### Post by faktorqm on 2008-10-15
Ahi en la parte de GTK_FOOBAR (cree un proyecto gtk asi no mas para ver) le pones lmsensors4-dev (por defecto tengo gtk+-2.0 y libglade-2.0) y deberia andar... obviamente tenes que tener instalado lmsensors y el paquete lmsensors4-dev. De c++ lei poco yo... no te se recomendar algo "bueno". Salu2!!

---

### Post by Hei Ku on 2008-10-15
En KDevelop.org tenes tutoriales, pero son obvio para KDE.
Para qué querés C++ si estas usando GNome? No usa C?

---

### Post by MeduZa on 2008-10-16
> **Hei Ku said:**
> En KDevelop.org tenes tutoriales, pero son obvio para KDE.
Para qué querés C++ si estas usando GNome? No usa C?

estoy usando c++ con GTK+

---

### Post by MeduZa on 2008-10-17
> **faktorqm said:**
> Ahi en la parte de GTK_FOOBAR (cree un proyecto gtk asi no mas para ver) le pones lmsensors4-dev (por defecto tengo gtk+-2.0 y libglade-2.0) y deberia andar... obviamente tenes que tener instalado lmsensors y el paquete lmsensors4-dev. De c++ lei poco yo... no te se recomendar algo "bueno". Salu2!!

asi lo tengo que hacer (pero de otra manera, agrego -lsensor al linkier), a mano porque de la manera normal no aparece libsensors en ninguna vercion y lo raro es que librerias que no conoce ni el perro aparecen -.- debe ser problema del paquete libsensoers dev al instalarse

---

