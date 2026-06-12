---
title: "bespin compilado con soporte ARGB"
date: 2009-08-28
forum: Software
---

### Post by pol666 on 2009-08-28
> **staar said:**
> ese amarok es el 1.4, para que se vea así en jaunty la vas a tener difícil, porque necesitás instalar kcontrol (con sus dependencias) para modificar el aspecto de las aplicaciones de KDE3, yo lo hice, pero con intrepid, instalando paquetes de hardy, no se sí funcionará en jaunty (capaz que entre en conflicto con los paquetes de KDE4 de jaunty, no sé, la verdad) y habia que forzar las versiones de algunos de esos paquetes para que no se actualizaran...

bespin compilado con soporte ARGB :-D (le falta, pero pinta bien)

[[img]http://h.imagehost.org/t/0416/instant_nea56.jpg[/img]](http://h.imagehost.org/view/0416/instant_nea56)

saludos

Nuuuu que locura. Donde viste eso?

---

### Post by staar on 2009-08-28
> **pol666 said:**
> Nuuuu que locura. Donde viste eso?
en ningún lado, es mi propio trabajo sucio :-D :-P, [acá]("http://cloudcity.svn.sourceforge.net") podés ver las últimas revisiones hechas en el código, y [acá]("http://cloudcity.sourceforge.net/download.php") la instrucciones para compilarlo, lo único que hice fue, antes de correr el ./configure, abrir el CMakeLists.txt y cambiar la opción ENABLE_ARGB a ON (supongo que debe haber una forma más elegante, pero es la que se me ocurrió primero :-D), y después seguir las intrucciones normalmente...

saludos

---

### Post by guisheca on 2009-08-28
Que ventajas tiene que tenga soporte para ARGB?? Perdón la ignorancia

---

### Post by Hei Ku on 2009-08-28
Conocen las reglas. ;)

---

### Post by staar on 2009-08-28
> **guisheca said:**
> Que ventajas tiene que tenga soporte para ARGB?? Perdón la ignorancia
que se puede definir la transparecia de la ventana desde el estilo, sin usar compiz/kwin (y con la diferencia que las letras y otras cositas no se transparentan)

saludos

---

### Post by pol666 on 2009-08-29
muy bueno che, realmente se zarpa. Se ven así todos los programas o algunos no mas? por que me acuerdo que en gnome estaba murrine argba eprot enia que parchear algunos programas.

---

### Post by staar on 2009-08-29
> **pol666 said:**
> muy bueno che, realmente se zarpa. Se ven así todos los programas o algunos no mas? por que me acuerdo que en gnome estaba murrine argba eprot enia que parchear algunos programas.
de los que probé, funciona en todos, no hizo falta compilarlos de nuevo, creo que porque Qt ya tiene soporte ARGB (osea que solo hacía falta algo que haga uso de esa capacidad), con la excepción de amarok, smplayer y dragonplayer que vienen excluidos por defecto (como se ve en la captura), el desarrollador sabrá porqué...

igual, todavía es MUY experimental (tené en cuenta que es muy reciente, no tiene ni una semana) y hay algunos problemas, el que encontré yo es que si inicio sesión con la transparencia activada, plasma tiene problemas, como que pasa a segundo plano y solo se ve el fondo de escritorio...

saludos

---

### Post by LuisAugusto on 2009-09-16
> **staar said:**
> con la excepción de amarok, smplayer y dragonplayer que vienen excluidos por defecto (como se ve en la captura), el desarrollador sabrá porqué...

Es porque las aplicaciones que usan XEmbed (casi todos, o todos, los reproductores de video por ejemplo) no funcionan con el soporte ARGB. Agrego que Tomás dijo que quizás no tenga solución.

---

