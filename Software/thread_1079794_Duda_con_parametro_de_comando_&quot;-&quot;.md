---
title: "Duda con parametro de comando &quot;-&quot;"
date: 2009-02-24
forum: Software
---

### Post by Mauro22 on 2009-02-24
Hola!

Tengo una duda existencial.

Que diferencia hace el - (guion) al final de un comando?

Ejemplo:


cat musica.mp3 | mpg123

y

cat musica.mp3 | mpg123 -


Porque el primero no anda y el segundo si? En que modifica el - ??



Gracias al que responda!


PD:

Ese comando sirve para hacer streaming por ssh :d o sea que lo manda como "texto" y se lo pasa a mpg123 formando stream. Increible pero funciona!

---

### Post by guillermolisi on 2009-02-24
> **Mauro22 said:**
> Hola!

Tengo una duda existencial.

Que diferencia hace el - (guion) al final de un comando?

Ejemplo:


cat musica.mp3 | mpg123

y

cat musica.mp3 | mpg123 -


Porque el primero no anda y el segundo si? En que modifica el - ??



Gracias al que responda!


PD:

Ese comando sirve para hacer streaming por ssh :d o sea que lo manda como "texto" y se lo pasa a mpg123 formando stream. Increible pero funciona!
La respuesta esta en tu maquina y empieza por este texto:
> mpg123(1)                                                            mpg123(1)

NAME
       mpg123 - play audio MPEG 1.0/2.0/2.5 stream (layers 1, 2 and 3)

SYNOPSIS
       mpg123 [ options ] file ... | URL ... | -

DESCRIPTION
       mpg123  reads  one  or more files ([B]or standard input if ‘‘-’’ is speci&#8208;
       fied[/B]) or URLs and plays them on the audio device (default)  or  outputs
       them to stdout.  file/URL is assumed to be an MPEG audio bit stream.

OPERANDS
       The following operands are supported:

       file(s) The  path  name(s)  of  one  or more input files.  They must be
               valid MPEG-1.0/2.0/2.5 audio layer 1, 2 or 3 bit streams.  If a
               dash  ‘‘-’’ is specified, MPEG data will be read from the stan&#8208;
               dard input.  Furthermore, any name starting with ‘‘[http://’’]("http://%E2%80%99%E2%80%99") is
               recognized as URL (see next section).extractado de ```
man mpg123
```

---

### Post by Mauro22 on 2009-02-24
No te lo puedo creer...


:sad:


Perdon, fue el unico lugar donde no busque... no se me ocurrio ni se me paso por la cabeza.



Gracias! Aunque sacaron las medallitas... Hay algun lugar donde quejarse?

---

### Post by guillermolisi on 2009-02-25
> **Mauro22 said:**
> No te lo puedo creer...


:sad:


Perdon, fue el unico lugar donde no busque... no se me ocurrio ni se me paso por la cabeza.



Gracias! Aunque sacaron las medallitas... Hay algun lugar donde quejarse?
Nada para preocuparse. Son cosas que pasan. Lo importante es recordar que despues de google existe man :mad:.

Lo busque ahi porque me sono a parametro/opcion del mpg123 ese guion al final.

Lo de las medallitas era cotillon. Nada como las propias palabras del interesado para saber que esta agradecido.

Eso si, marca el thread como Solved (cosa que parece ha quedado totalmente en desuso aunque la funcion aun esta disponible).

---

