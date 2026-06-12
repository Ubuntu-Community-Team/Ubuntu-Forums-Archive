---
title: "Clonar sistema con ubuntu y algunas duditas"
date: 2009-01-09
forum: Software
---

### Post by KaKuS on 2009-01-09
Hola gente, les comento que soy nuevo en el mundo de linux. Siempre me quise pasar pero recien ahora despues de un par de cursos basicos me estoy empapando con todo.

Ya puedo decir que tengo ubuntu en casa y en la oficina, pero todavía no pude con algunos vicios que traigo del uso de Windows.

Si alguno me puede dar algún empujón se agradece, perdón de antemano por la falta de conocimientos.

Ya tengo mi sistema configurado con el hardware, el software como lo quiero y estoy a punto de instalar una maquina virtual para emular los programas que todavía no hay para ubuntu. Como ya tuve una mala experiencia y tuve que formatear para empezar desde cero decidí buscar alguna aplicación que me permita generar una imagen del disco.

Yo estoy acostumbrado a usar el Ghost 11.5 bajo DOS para mis sistemas Microsoft pero no estoy seguro si existe uno similar para sistemas unix.
La idea sería generar una imagen en uno (o varios) DvDs para volver atrás si pasa algo.

Y ya que estoy molestando... todo esto de la maquina virtual lo estoy por instalar debido a que no encontré una manera de trabajar archivos de Microsoft Visio con mi ubuntu. Probé varias aplicaciones pero ninguna cuenta con la versatilidad ni variedad de usos que me presenta este programa y para colmo ya tengo toda la red de mi empresa, sectores y diagramas de flujo confeccionados (años de documentación) en dicho programa. ¿Conocen alguna aplicación que se le acerque?

Desde ya muchas gracias por el tiempo que perdieron leyendo mi post =P

PD: 
Es un Ubuntu 8.10 intrepid
Kernel Linux 2.6.27-9-generic
Corriendo GNOME 2.24.1
Memoria 2.0 GB y es un Pentium 4 de 2.66 GHZ

---

### Post by guillermolisi on 2009-01-09
> **KaKuS said:**
> Hola gente, les comento que soy nuevo en el mundo de linux. Siempre me quise pasar pero recien ahora despues de un par de cursos basicos me estoy empapando con todo.

Ya puedo decir que tengo ubuntu en casa y en la oficina, pero todavía no pude con algunos vicios que traigo del uso de Windows.

Si alguno me puede dar algún empujón se agradece, perdón de antemano por la falta de conocimientos.

Ya tengo mi sistema configurado con el hardware, el software como lo quiero y estoy a punto de instalar una maquina virtual para emular los programas que todavía no hay para ubuntu. Como ya tuve una mala experiencia y tuve que formatear para empezar desde cero decidí buscar alguna aplicación que me permita generar una imagen del disco.

Yo estoy acostumbrado a usar el Ghost 11.5 bajo DOS para mis sistemas Microsoft pero no estoy seguro si existe uno similar para sistemas unix.
La idea sería generar una imagen en uno (o varios) DvDs para volver atrás si pasa algo.

Y ya que estoy molestando... todo esto de la maquina virtual lo estoy por instalar debido a que no encontré una manera de trabajar archivos de Microsoft Visio con mi ubuntu. Probé varias aplicaciones pero ninguna cuenta con la versatilidad ni variedad de usos que me presenta este programa y para colmo ya tengo toda la red de mi empresa, sectores y diagramas de flujo confeccionados (años de documentación) en dicho programa. ¿Conocen alguna aplicación que se le acerque?

Desde ya muchas gracias por el tiempo que perdieron leyendo mi post =P

PD: 
Es un Ubuntu 8.10 intrepid
Kernel Linux 2.6.27-9-generic
Corriendo GNOME 2.24.1
Memoria 2.0 GB y es un Pentium 4 de 2.66 GHZ

En la oficina clonamos 13 servidores con Clonzilla ([http://clonezilla.org/](http://clonezilla.org/)) pero hemos experimentado algunos problemas cuando usamos esos discos con motherboards que no eran iguales a las que se usaron en la instalacion original. Esto no tiene que ver con Clonzilla sino con cuestiones de compatibilidad binaria con el hardware.

Respecto del tema Visio y VMs, tres comentarios.

El primero es que dado que el tema es diferente al asunto, las buenas practicas de un foro, particularmente de este, recomiendan abrir un post especifico. Con esto se le facilita la resolucion y la transferencia de conocimientos a otros que pueden tener las mismas dudas y/o problemas y buscan en el foro por soluciones e ideas para resolverlos,

El segundo es que desde que solo uso Linux no he encontrado una aplicacion equivalente al Visio. Primero lo resolvi de la misma forma en que estas pensando, via una VM con Windows, y asi lo segui usando hasta que me canse y deje de utilizarlo a cambio de otros no tan vistosos pero igualmente efectivos a la hora de documentar diagramas (con algo mas de trabajo de mi parte).
Uso Dia que graficamente no se acerca a Visio pero igual permite realizar diagramas y esquemas.

Para hacer VMs podes usar varias alternativas. Una es VirtualBox, que tiene dos versiones, una OpenSource y una privativa (esta ultima reconoce puertos USB, la primera no).
Otra es VMware y tambien tenes virtualizacion via KVM.

Personalemnte uso VirtualBox para uso personal y VMware para uso corporativo.

---

### Post by KaKuS on 2009-01-10
Muchas gracias, ya estoy bajando el Live CD. Perdón por el desorden =P

---

