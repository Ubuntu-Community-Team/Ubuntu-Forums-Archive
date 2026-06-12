---
title: "Problema Con Consola"
date: 2009-10-13
forum: Software
---

### Post by demian86 on 2009-10-13
[B]Andamos de mal en peor.

Luego de que se me aruinara el disco.

Instalo nuevamente U-JJ, y me dispongo a instalar los controladores de Nvidia.

Luego de instalarlo tengo que entrar a la consola para detener GDM, para poder editar xorg.conf. Pero siempre cuando intento logearme me sale "Login Incorrect".

que yo sepa se debe ingresar la contraseña del Root, pero no me la toma, y tan bobo como para poner 10 letras no soy.

¿ Puede haber otro problema acaso ?.

Gracias.[/B]

---

### Post by guillermolisi on 2009-10-13
La pass que te pide es la de tu usuario. Se supone que el usuario root no tiene password (a menos que lo hayas modificado).

---

### Post by demian86 on 2009-10-13
> **guillermolisi said:**
> La pass que te pide es la de tu usuario. Se supone que el usuario root no tiene password (a menos que lo hayas modificado).

[B]
Se la cambie  a la pass de Root.


Intente con las dos 2 pass, la de root y la de usurio, pero me salta logeo incorrecto ._.[/B]

---

### Post by guillermolisi on 2009-10-13
> **demian86 said:**
> [B]
Se la cambie  a la pass de Root.


Intente con las dos 2 pass, la de root y la de usurio, pero me salta logeo incorrecto ._.[/B]
Despues de la instalacion actualizaste todo el sistema o esta tal como queda despues de haber instalado ?

Podes abrir el escritorio grafico ?

---

### Post by demian86 on 2009-10-13
> **guillermolisi said:**
> Despues de la instalacion actualizaste todo el sistema o esta tal como queda despues de haber instalado ?

Podes abrir el escritorio grafico ?

[B]no lo actualize todavia, ya que esta en 640x480 y es muy molesta esta resolucion.

Lo que es Gnome y Nautilus no presenta problema alguno.


Solo es en el logeo cuando estoy en la consola, por que estoy obligado  a editar el xorg.conf por la resolucion, ya que no me toma ni 1024, ni 800.

:F[/B]

---

### Post by guillermolisi on 2009-10-13
> **demian86 said:**
> [B]no lo actualize todavia, ya que esta en 640x480 y es muy molesta esta resolucion.

Lo que es Gnome y Nautilus no presenta problema alguno.


Solo es en el logeo cuando estoy en la consola, por que estoy obligado  a editar el xorg.conf por la resolucion, ya que no me toma ni 1024, ni 800.

:F[/B]
Y que pasa si abris una terminal en el escritorio grafico para editar el xorg.conf ?
Aunque no sea lo mas comodo por la resolucion que tenes ahora, no deberias tener problemas con sudo si te dejo iniciar bien la sesion grafica y asi poder modificar lo que te haga falta para acomodar la resolucion.

---

