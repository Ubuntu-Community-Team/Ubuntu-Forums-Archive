---
title: "Clave de Root"
date: 2010-12-02
forum: Software
---

### Post by HectorQ on 2010-12-02
Hola, soy muy nuevo en linux, pero ya hace un tiempo instale en una pc ubuntu y la verdad que no recuerdo la password root, se puede hacer algo?

---

### Post by alfplayer on 2010-12-02
Te recomiendo buscar un artículo (actualizado) con Google que explique como cambiar la contraseña. Para eso, se pueden usar los términos, por ejemplo: *recuperar contraseña ubuntu*.

---

### Post by Wiredfixer on 2010-12-03
De hecho, aqui la cosa es tener un disco de ubuntu y localizar el archivo /etc/shadow

ahi, lo editas desde terminal y listo.

No recuerdo exactamente las lineas, pero basicamente es eliminar el area de la contraseña que se encuentran el /etc/shadow de esta manera:

admin:1QJDO!Q::QO38294ISIA

Y eliminar lo que esta entre los primeros dos puntos:

admin:**1QJDO!Q**::QO38294ISIA

mas o menos asi.

Aunque esta mejor explicado por aca:

[http://bootlog.org/blog/linux/como-cambiar-la-clave-de-root-en-linux](http://bootlog.org/blog/linux/como-cambiar-la-clave-de-root-en-linux)

Disculpa la mareada.

---

### Post by granjero on 2010-12-04
vulnerar la clave de root es tan fácil como bootear con un liveCD?

eso no es una cuestión de seguridad GRAVE?

---

### Post by alfplayer on 2010-12-04
> **granjero said:**
> vulnerar la clave de root es tan fácil como bootear con un liveCD?

eso no es una cuestión de seguridad GRAVE?

Ni es necesario el live CD. Si se acceden a los archivos (no encriptados) se tiene control total.

---

### Post by granjero on 2010-12-04
y la seguridad de la que tanto se habla?

o hay una parte que me estoy perdiendo?

---

### Post by alfplayer on 2010-12-04
> **granjero said:**
> y la seguridad de la que tanto se habla?

o hay una parte que me estoy perdiendo?

Seguridad informática es un tema muy amplio. No es lo mismo asegurar contra intrusiones remotas que contra una persona con acceso al hardware, que es este caso.

Las PC de escritorio o portátiles en general no tienen este tipo de seguridad, sin importar el sistema operativo, pero se puede tomar algunas medidas como encriptación de disco.

---

### Post by madjr on 2010-12-04
> **granjero said:**
> y la seguridad de la que tanto se habla?

o hay una parte que me estoy perdiendo?

linux esta bien seguro de fuentes remotas como el internet, virus, spyware, etc, pero hackear la pc directamente es diferente.

Asi mismo podemos acceder a los archivos de windows desde linux.

para estar totalmente seguros deben encriptar sus datos / particion.

hacerlo no es muy dificil.

---

### Post by gmunioz on 2010-12-04
1 - En principio si de Ubuntu se trata, el usuario root está deshabilitado.
2 - Si lo que se quiere es mantener los datos a salvo, simplemente se requiere cifrarlos, 
Ubuntu ofrece esta opción en el momento de la instalación, eso si mejor recuerden la contraseña, porque es imposible accederlos sin ella.

---

### Post by alfplayer on 2010-12-04
Por si alguien no lo sabe y quiere usarlo, una advertencia: la encriptación de disco usa recursos, tiene un costo en la performance del sistema.

---

### Post by granjero on 2010-12-04
un poco más claro ahora....

---

### Post by biale on 2010-12-05
Por las dudas...
> Si lo que se quiere es mantener los datos a salvo, simplemente se requiere cifrarlos, 

O sea: "a salvo contra intrusos". Las pocas pruebas que hice mostraron que la encriptación es un tema delicado, antes de encriptar conviene analizar todo dos veces y tener un backup no encriptado en lugar seguro.

---

