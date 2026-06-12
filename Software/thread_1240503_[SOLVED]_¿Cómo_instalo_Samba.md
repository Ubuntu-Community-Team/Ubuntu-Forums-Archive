---
title: "[SOLVED] ¿Cómo instalo Samba?"
date: 2009-08-14
forum: Software
---

### Post by GerryEastwood on 2009-08-14
Seguramente soy un salame, pero no entiendo nada :oops:

Bajé el samba, busqué en el foro y lo que encuentro es cómo configurarlo, pero no cómo se instala.

¿Tengo que copiarlo directamente?

Disculpen y gracias.

---

### Post by sergiom99 on 2009-08-14
Fijate que en la pagina de ubuntu-ar hay un monton de tutoriales, entre ellos uno excelente de como configurar e instalar Samba
[http://ubuntu-ar.org/node/219](http://ubuntu-ar.org/node/219)

---

### Post by Hei Ku on 2009-08-14
Para la proxima, en el site de ubuntu-ar.org hay una lista de tutos para resolver las tareas mas comunes.

---

### Post by luks911 on 2009-08-14
No hace falta que bajes nada. Como cualquier otra cosa la instalás desde synaptic (buscás el paquete samaba) o en una terminal

```
sudo aptitude install samba
```

Por supuestpo que sí descarga lo necesario desde repositorios.
Otra opción, en este caso, es que intentes compartir una carpeta. En ese caso Ubuntu te dice que necesitás samba y te ofrece instalarlo. Es decir, hacés click derecho en una carpeta, elegís compartirla y te va a dar la opción de instalar samba.
Espero que hay aservido.

---

### Post by juancarlospaco on 2009-08-14
**[1 Click aqui...]("apt:/samba")**

:)

---

### Post by granjero on 2009-08-14
otra forma:

Aplicaciones/Añadir y Quitar...

ponés samba y listo!

---

### Post by GerryEastwood on 2009-08-15
> **GerryEastwood said:**
> Seguramente soy un salame, pero no entiendo nada :oops:

Bajé el samba, **busqué en el foro y lo que encuentro es cómo configurarlo, pero no cómo se instala**.

¿Tengo que copiarlo directamente?

Disculpen y gracias.

Gracias. Es que en Añadir/Quitar no me aparece (creo) :confused:

> No hace falta que bajes nada. Como cualquier otra cosa la instalás desde synaptic (buscás el paquete samaba) o en una terminal
```
sudo aptitude install samba
```Por supuestpo que sí descarga lo necesario desde repositorios.
Otra opción, en este caso, es que intentes compartir una carpeta. En ese caso Ubuntu te dice que necesitás samba y te ofrece instalarlo. Es decir, hacés click derecho en una carpeta, elegís compartirla y te va a dar la opción de instalar samba.
Espero que hay aservido.Gracias, voy a probar eso.

---

### Post by GerryEastwood on 2009-08-15
Listo, gracias. Pensaba que tenía que instalar el que bajé de internet.

---

### Post by Hei Ku on 2009-08-15
No, las cosas se instalan desde los repositorios, no bajando un programa de algun sitio web como suelen hacer en windows.
De hecho, se bajan de repositorios confiables, y que esten firmados. Si no, no.
Linux toma la seguridad en serio, no es para el panfleto de publicidad.

---

### Post by GerryEastwood on 2009-08-15
Jeje, igualmente yo lo había bajado del sitio oficial de samba ;)

¿Lo de [SOLVED] lo ponen ustedes o lo puede poner uno?

---

### Post by guillermolisi on 2009-08-15
> **GerryEastwood said:**
> Jeje, igualmente yo lo había bajado del sitio oficial de samba ;)

¿Lo de [SOLVED] lo ponen ustedes o lo puede poner uno?
Lo correcto es que quien inicio el thread lo haga una vez satisfecha y resuelta su inquietud.

Como no todos tienen esa (sana y respetuosa) costumbre y para guiar a los que estan buscando soluciones sobre los mismos temas, editamos el titulo del thread y se lo ponemos.

---

### Post by GerryEastwood on 2009-08-15
Lo pregunto porque quise hacerlo editando el primer post pero no encontré cómo modificar el título :oops:

---

### Post by guillermolisi on 2009-08-15
> **GerryEastwood said:**
> Lo pregunto porque quise hacerlo editando el primer post pero no encontré cómo modificar el título :oops:
Te paras en el campo Title y en la primera posicion a la izquierda insertas [SOLVED] y un espacio para que se vea bien el tag del nombre del thread (asi quedan todos iguales).

Aceptas el cambio (submit/accept o similar) y listo.

---

### Post by GerryEastwood on 2009-08-15
Es lo que sospechaba, el problema es que no me permite ir al campo Title en la edición, sólo al crear un post nuevo :confused:

---

### Post by Hei Ku on 2009-08-15
Editas el titulo del primer post y eso le cambia el titulo a todo el thread. Me parece.

---

### Post by GerryEastwood on 2009-08-19
Fue lo que intenté (al menos en phpBB se hace así) pero no me habilitaba para cambiar el título. Tal vez sea una función solo para moderadores o admins (o tal vez yo lo intenté dormido y por eso no me funcionó :confused:)

:lolflag:

EDITADO: ¡Lo encontré! Al editar no habilita a cambiar el título, pero el botón EDIT está presente, si se hace click, allí permite cambiar el título, es como si tuviera dos niveles de edición del post.

---

### Post by sergiom99 on 2009-08-19
> **GerryEastwood said:**
> Fue lo que intenté (al menos en phpBB se hace así) pero no me habilitaba para cambiar el título. Tal vez sea una función solo para moderadores o admins (o tal vez yo lo intenté dormido y por eso no me funcionó :confused:)

:lolflag:

EDITADO: ¡Lo encontré! Al editar no habilita a cambiar el título, pero el botón EDIT está presente, si se hace click, allí permite cambiar el título, es como si tuviera dos niveles de edición del post.

Pues yo no puedo lograrlo hombre!

---

### Post by josecuervo86 on 2009-08-19
Sergio, una vez que apretas edit, te cambia el cuadro de dialogo para que puedas modificar el contenido del post. Si volves a apretar edit, te manda a otra pagina y ahí si podes cambiar el título.

---

### Post by sergiom99 on 2009-08-19
> **josecuervo86 said:**
> Sergio, una vez que apretas edit, te cambia el cuadro de dialogo para que puedas modificar el contenido del post. Si volves a apretar edit, te manda a otra pagina y ahí si podes cambiar el título.

Si, pero solo me cambia el titulo del primer post y no del thread.
Mira> [http://ubuntuforums.org/showthread.php?t=1168005](http://ubuntuforums.org/showthread.php?t=1168005)

---

### Post by josecuervo86 on 2009-08-19
Ja! es verdad, cuando vi la opción de cambiar el titulo supuse que se lo cambiaba a todo el thread. Igual el que importa es el primero :)

---

