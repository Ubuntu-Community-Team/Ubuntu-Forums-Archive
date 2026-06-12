---
title: "KIba dock ubuntu 64 bits"
date: 2008-07-16
forum: Software
---

### Post by ramiro_md on 2008-07-16
AMigos llevo dias tratando de instalar este dock en mi gusty 64 bits, y aun nada..he visto muchos tutoriales que me hacen agregar al sources.list estas paginas:

deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

pero al lanzar apt-get update me sale esto al temrinar:

Des:11 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Sources [37B]
Descargados 234kB en 3s (59,9kB/s)
Leyendo lista de paquetes... Hecho
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 2D6CFB44DD800CD9
W: Tal vez quiera ejecutar 'apt-get update' para corregir estos problemas


Estoy fregadisimo =(...me gustaria usar esa dock...un saludo y epsero q me den una mano =)

---

### Post by marianom on 2008-07-16
Tenes que agregar su llave para que queden validados. Si mal no recuerdo, [esta pequeña guía]("http://ubuntuforums.org/showthread.php?p=1653773#post1653773") debería servirte (aunque realmente no estoy seguro si ese era el mensaje de error al cual aplica esta solución).


For the record: en la medida de lo posible no se vayan **NUNCA** muy lejos de los repositorios oficiales de ubuntu y traten de agregar _la menor cantidad de repositorios externos_ y _solo aquellos que realmente les den seguridad_ (e.g. los repos de los desarrolladores si es que existen y les gusta jugar con el bleeding edge). 


De otra forma están abriendo una de las 7 puertas del infierno (¿soné muy apocalíptico? Mucho Lucio Fulci este pasado fin de semana)

---

### Post by lega on 2008-07-16
Pregunta de ignorante nomas, por ahí habría que poner esto en las preguntontas, pero decís que tenes gutsy, y ese repositorio, es para feisty, esta bien lo que estas haciendo?

---

### Post by ramiro_md on 2008-07-16
> **lega said:**
> Pregunta de ignorante nomas, por ahí habría que poner esto en las preguntontas, pero decís que tenes gutsy, y ese repositorio, es para feisty, esta bien lo que estas haciendo?

LOs programas suelen funcionar en versiones mas nuevas, por ejemplo yo he corrido programas de gusty en hardy..(pero no se si sera recomendable)

---

### Post by marianom on 2008-07-16
Y... estás rifando la estabilidad un poco.

---

### Post by ramiro_md on 2008-07-16
ERa de imaginarse eso de la estabilidad..no es lo mismo un gato montes q un gato...que bueno...Por otor lado sigo sin conseguir el maldito kiba !!! he bajado un .deb pero al instalarlo y ejecutar kiba no pasa nada =S

---

### Post by Hernán-Amaya on 2008-07-16
proba acá [http://ubuntuforums.org/showthread.php?t=554127&highlight=kiba+dock+](http://ubuntuforums.org/showthread.php?t=554127&highlight=kiba+dock+)

suerte!

---

### Post by ramiro_md on 2008-07-16
> **Hernán-Amaya said:**
> proba acá [http://ubuntuforums.org/showthread.php?t=554127&highlight=kiba+dock+](http://ubuntuforums.org/showthread.php?t=554127&highlight=kiba+dock+)

suerte!


GRacias hernan !, lo probe pero en el ultimo make install de la guia de 64 bits me slae lo siguiente:
"make: *** No hay ninguna regla para construir el objetivo `install'.  Alto." :confused:
Y se ve que le falto es teta para ser vaca xq cuando quiero correr kiba con "kiba-dock" en la consola me dice "bash: kiba-dock: orden no encontrada" :(

---

### Post by Hei Ku on 2008-07-16
corriste el configure?

o lo bajaste directo de un CVS o SVN, y te falta correr el make -f

---

### Post by joyondo on 2009-06-30
Estoy en la misma situación ayuda , encontraste solución? 
Saludos

---

### Post by Hei Ku on 2009-06-30
Misma pregunta. De donde lo bajaste y que instrucciones seguiste para instalarlo? Igual tene en cuenta que el Kiba Dock es viejito. Te conviene algo mas como el Cairo dock2 o similar.

---

### Post by santiagoward2000 on 2009-06-30
> **joyondo said:**
> Estoy en la misma situación ayuda , encontraste solución? 
Saludos

Yo dejé de usar Kiba-Dock desde Intrepid porque no pude hacer que ande durante 5 minutos si crashear. Como dijo Hei-Ku, el proyecto está "viejito" (hace un año el desarrollador principal dijo que el proyecto se congelaba por lo menos por 6 meses).
Si querés probar Cairo-Dock 2, fijate en este thread cómo instalarla:
[http://ubuntuforums.org/showthread.php?t=1196318]("http://ubuntuforums.org/showthread.php?t=1196318")
Saludos!

PS:
Todo muy lindo Cairo-Dock 2, pero yo todavía extraño **Akamaru** :(

---

