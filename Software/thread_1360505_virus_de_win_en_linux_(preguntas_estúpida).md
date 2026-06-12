---
title: "virus de win en linux (preguntas estúpida)"
date: 2009-12-21
forum: Software
---

### Post by drazhe on 2009-12-21
es una duda existencial que no me esta dejando dormir y supongo que cae en la categoría de preguntas estúpidas que uno siempre quiso saber y por miedo nunca se atrevió a preguntar.

Yo se que Linux es un Sistema Operativo extremadamente estable y confiable sin mayores amenazas y que los virus de windows solo funcionan en windows, así ejectute el archivo **virus.exe** en mi Ubuntu 

La pregunta que quiero hacer es que pasaría si ejecuto ese archivo **virus.exe** teniendo el WINE instalado...

---

### Post by Psicolonia on 2009-12-21
if the virus runs on wine, and you didn't stop it, yes, it could stay running.

---

### Post by Kabezon on 2009-12-21
Yo supongo, reitero, SUPONGO, que puede ocurrir, pero que sólo afectaría a la carpeta .wine, y por ende a todas las aplicaciones de Windows que tengas instaladas. Quizás también, en el caso que tengas una partición con Windows instalada en ella, la afecte al estar montada en el momento que el virus esté activo. 

De todas formas, si es como me lo imagino, con un simple rm -rf ~/.wine sería suficiente para deshacerse del problema. Para arreglar la partición con Windows, y bueno... A reinstalar, de todas formas, era obvio que tarde o temprano ibas a tener que hacerlo :lolflag:

-EDITO-
Ahora que lo pienso... Wine haría que el virus piense que /home/ es Mis Documentos, así que quizás se te infecte todo eso, si bien a uno no le causaría molestias, me imagino que le afectaría a terceros, usuarios de Windows, que de una forma u otra reciban tus archivos :O

P.D: Palabra mágica: **_[COLOR="Red"]SUPONGO[/COLOR]_** :P

---

### Post by drazhe on 2009-12-21
si es lo que me imaginaba, leyendo por Internet, por todos lados dicen que en Linux, no hacen falta antivirus y que los que hay tienen como única función detener al virus para no reenviarlo a los contactos que usan win, ya que a nosotros no nos puede hacer nada... 
no tengo instalada wine y mucho menos win, pero se del programa y tenia esa duda, gracias a todos por las respuestas!

---

### Post by pol666 on 2009-12-21
> -EDITO-
Ahora que lo pienso... Wine haría que el virus piense que /home/ es Mis Documentos, así que quizás se te infecte todo eso, si bien a uno no le causaría molestias, me imagino que le afectaría a terceros, usuarios de Windows, que de una forma u otra reciban tus archivos :O


No, Wine labura dentro de /home/usuario/.wine solamente, ahí adentro recien estaria C:. Tampoco creo que sea posible que el archivo "escape" de ese directorio.

---

### Post by guillermolisi on 2009-12-21
> **pol666 said:**
> No, Wine labura dentro de /home/usuario/.wine solamente, ahí adentro recien estaria C:. Tampoco creo que sea posible que el archivo "escape" de ese directorio.
Considerar que hay virus que solo necesitan contar con paquetes de red (TCP) para propagarse y si hay una maquina con Win en la misma red, seguro que se infecta.

Por eso se hace especial mencion a la seguridad centralizada y a la periferica tambien.

Justo el viernes pasado hablabamos sobre Wine y su funcionamiento tan bien logrado que parece que hasta los virus corren muy bien, como si estuvieran en un entorno realmente nativo Win.

---

### Post by Kabezon on 2009-12-21
> **pol666 said:**
> No, Wine labura dentro de /home/usuario/.wine solamente, ahí adentro recien estaria C:. Tampoco creo que sea posible que el archivo "escape" de ese directorio.
Sí, pero fijate que Wine usa Home como Mis Documentos, Si estás usando algún programa con Wine y navegás a Mis Documentos terminás en Home. De hecho, si vas a .wine/drive_c/users/~/Escritorio, Mi música, Mis documentos, Mis imágenes y Mis vídeos, todos redirigen a su respectiva carpeta en Home.

---

