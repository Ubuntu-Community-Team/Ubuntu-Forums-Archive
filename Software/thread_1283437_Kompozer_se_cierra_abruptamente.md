---
title: "Kompozer se cierra abruptamente"
date: 2009-10-05
forum: Software
---

### Post by jandry on 2009-10-05
Amigos del foro: estoy armando una pagina web con kompozer pero a los dos o tres minutos de abrirlo se cierra abruptamente. La unica informacion que obtengo por consola es "segmentation fault". Si alguien puede tirarme una soga lo agradeceria muchisimo.
Abrazo ubuntero

---

### Post by guillermolisi on 2009-10-05
> **jandry said:**
> Amigos del foro: estoy armando una pagina web con kompozer pero a los dos o tres minutos de abrirlo se cierra abruptamente. La unica informacion que obtengo por consola es "segmentation fault". Si alguien puede tirarme una soga lo agradeceria muchisimo.
Abrazo ubuntero
Ale

Que version estas corriendo de Kompozer ?

Estoy usando la 7.10 y no me pasa lo que a vos (bajo KDE 4.3.1 y JJ)

La baje del site de Kompozer porque la de los repos de JJ es anterior (o por lo menos lo era cuando actualice).

---

### Post by sitiomatic on 2009-10-05
A mi me pasa lo mismo y no puedo ni empezar a trabajar, en cuanto toco algo se cierra. Esto me pasa desde que salio jaunty, no me pasaba antes.
Yo no le encontre solucion, por lo tanto uso un kompozer portable con wine y me anda bastante bien.

---

### Post by jandry on 2009-10-06
Solucionado amigos, con la punta que me tiro Guille, mire la version que tenia instalada y es superior a la de la pagina de kompozer, asi que desinstale la que tenia e instale la 7,01 y anda bien. Gracias a todos.
Abrazo ubuntero

---

### Post by jandry on 2009-10-06
quise decir 7,10, se ve que en los repositorios ya hay una nueva version y no es estable.

---

### Post by sitiomatic on 2009-10-06
0.7.10 es la que esta en los repositorios de JJ y es la que tengo yo y se me cierra.
Cuando trabajes graba seguido, no se cierra siempre, solo cuando estas en lo mejor y ya hiciste un monton.:)

---

### Post by jandry on 2009-10-08
nuevamente el mismo problema, se cierra cuando toco un menu desplegable :( 
si alguien tiene alguna solucion....

---

### Post by guillermolisi on 2009-10-08
> **jandry said:**
> nuevamente el mismo problema, se cierra cuando toco un menu desplegable :( 
si alguien tiene alguna solucion....
Para tener mas informacion sobre el sintoma, abri una consola y ejecuta desde ahi Kompozar. Cuando cancele deberias tener en la misma algun detalle de por que cancelo y con eso hasta se podria buscar si es un bug reportado o no.

---

### Post by sitiomatic on 2009-10-08
Lo unico que dice en la consola es "segmentation fault"
Yo ya habia abandonado la idea y usaba el portable con wine pero mirando recien la web de kompozer veo que dice:
"KompoZer 0.7.10 is not compatible with GTK &#8805; 2.14, hence the crashes on some recent Linux distros like Ubuntu 8.10 and 9.04. Please upgrade to KompoZer 0.8 alpha. " :)
Buscando kompozer 0.8 alpha..hay un tar.gz veremos como se instala.

---

### Post by guillermolisi on 2009-10-08
> **sitiomatic said:**
> Lo unico que dice en la consola es "segmentation fault"
Yo ya habia abandonado la idea y usaba el portable con wine pero mirando recien la web de kompozer veo que dice:
"KompoZer 0.7.10 is not compatible with GTK &#8805; 2.14, hence the crashes on some recent Linux distros like Ubuntu 8.10 and 9.04. Please upgrade to KompoZer 0.8 alpha. " :)
Buscando kompozer 0.8 alpha..hay un tar.gz veremos como se instala.
Por eso a mi me funciona bien, uso KDE/Qt :)

---

### Post by sitiomatic on 2009-10-08
Yo trate de instalar kde 4.3.2 ayer en mi jaunty....2 dias de lucha y me quedo un desastre...igual lo deje instalado, algun dia sigo intentando, me gusta mas kde que gnome pero mi instalacion no fue muy grata.

Volviendo al tema
Encontre un repositorio para kompozer, son un poco desordenados estos muchachos, el repositorio lo encontre en una web y la public key en un comentario en bugs.launchpad.net
deb [http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu](http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu](http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu) jaunty main

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 623C928A

Funciona, al menos pude crear una pagina, poner un par de tablas e imagenes y no se colgo. Antes se colgaba al tocar un menu.
Habra que seguir probando.

---

### Post by jandry on 2009-10-12
Atencion!!!! Baje la version 0.8 de sourceforge.net y anda bien sin cerrarse, si alguno lo prueba tambien y verifica que no hay problemas podemos dar por cerrado el hilo con la solucion. Abrazo ubuntero

---

### Post by sitiomatic on 2009-10-12
Funciona sin problemas, hace 3 dias que lo uso intensivamente.

---

