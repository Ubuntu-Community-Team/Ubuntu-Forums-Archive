---
title: "Instalar Ubuntu 9.04 en Celeron M"
date: 2009-10-15
forum: Software
---

### Post by xlxScorpioxlx on 2009-10-15
Primero que todo, me gustaría presentarme, soy un ferviente usuario de windows que luego de descubrir todos los problemas por los que paso para poder usarlo, he empezado la migración al sistema operativo Linux y en general a tratar de entender un poco la filosofía de los sistemas Unix.  El caso es este, tengo una laptop de mi hermana, ya es un poco vieja y ella quiere cambiarla, pero mientras tanto, el equipo con 512MB de RAM y un procesador sencillo (no es 2 núcleos ni siquiera maneja HT) Celeron M de 1.4Ghz y con Windows XP SP3, no corre nada, se demora 7 minutos para arrancar, IE i Firefox se bloquean, en fin, así que pensé que podría instalarle Ubuntu ya que Linux consume mucha menos memoria que Windows.  No obstante, estos últimos meses estuvo usando un Macbook de la oficina donde trabaja y quedó encantada con el sistema operativo leopard (corrijanme si estoy mal, ya que no se con exactitud cuál es la versión del MacOSX de los Macbook Blancos).  Ahora mis dudas son estas:  1. Instalar Ubuntu en un equipo como el de ella funcionará más rápido? 2. Necesito algún requerimiento especial para poder instalarle todos los packs y gadgets para que quede como el Leopard? 3. Esto ya sería un extra, pero es posible instalar el Compiz?  Agradezco mucho su ayuda  Saludos xlxScorpioxlx

---

### Post by faktorqm on 2009-10-15
Hola y bienvenido a la comunidad.

> **xlxScorpioxlx said:**
> 1. Instalar Ubuntu en un equipo como el de ella funcionará más rápido? 

Si, te recomiendo la version Xubuntu que es exclusiva para ese tipo de maquinas.

> **xlxScorpioxlx said:**
> 2. Necesito algún requerimiento especial para poder instalarle todos los packs y gadgets para que quede como el Leopard?

No, sólo que te funcione correctamente la placa de video. Esto es, que te ande el driver con aceleracion 3D.

> **xlxScorpioxlx said:**
> 3. Esto ya sería un extra, pero es posible instalar el Compiz?

Lo mismo, tanto para compiz como para los docks necesitas aceleracion 3D. Salu2!

---

### Post by xlxScorpioxlx on 2009-10-15
Cómo hago entonces para comprobar lo de la aceleración 3D?

---

### Post by josecuervo86 on 2009-10-15
Abrí una terminal (**Aplicaciones** > **Accesorios** > **Terminal**) y pone 
```
lspci
```
Luego pega el resultado aca, asi podemos tener un poco mas de info sobre el hard que tenes.

---

### Post by juancarlospaco on 2009-10-15
> **xlxScorpioxlx said:**
> 1. Instalar Ubuntu en un equipo como el de ella funcionará más rápido?

Si..., 
es mas segun unos Benchmarks de gente que sabe, actualmente Ubuntu es mas rapido que OS X.

> **xlxScorpioxlx said:**
> 2. Necesito algún requerimiento especial para poder instalarle todos los packs y gadgets para que quede como el Leopard?

No...,
pero la aceleracion 3D por hardware te va a permitir hacer lo que quieras,
si no tenes, vas a estar muy limitado realmente.

> **xlxScorpioxlx said:**
> 3. Esto ya sería un extra, pero es posible instalar el Compiz?

No...,
no es necesario, por que ya viene instalado, pero solo se puede habilitar si tenes aceleracion 3D

:)

---

### Post by sitiomatic on 2009-10-17
No se si tu notebook tendra soporte para usar compiz pero yo tengo una de las notebooks mas baratas del mercado. Acer Aspire 5315 Celeron 500 2Ghz.
Lo que hice fue gastar $200 en 2 gigas de memoria (venia con 512 y Vista ....para reirse)
Tengo un dock al estilo mac con gnome-do-docky.
Le doy palo a full 14 horas por dia con Ubuntu 9.04 y anda de maravilla, tengo compiz habilitado con algunos efectos y virtualbox con un xp por si tengo que ver algo en ie7 o en outlook (lamentablemente mis clientes usan esas cosas)
Espero que te sirva mi experiencia con ubuntu.

---

### Post by xlxScorpioxlx on 2009-10-19
Bueno, el problema más grave es que el equipo de mi hermana es un poco más viejo, que ese, es un hp nx6110 pero con un Celeron M de 1.4Ghz sencillo, nada de HT ni Dual-Core, además que sólo aguanta hasta 2GB de memoria (ya más o menos podrán entender que tan viejo es) y con el windows XP se DEMORA para todo, eso sin contar que con el Firefox el equipo se bloquea por completo, o termina el proceso.  Ah y para la aceleración 3D, hay alguna forma de averiguarla pero fuera de linux? se puede con el XP?

---

### Post by juancarlospaco on 2009-10-19
Ver en las caracteristicas de la placa de Video si dice que es completamente compatible con OpenGL 3.x, o como minimo 2.x y con sistemas Linux.

No te guies por XP es mas lento para todo.

---

### Post by Tosh78 on 2009-10-19
Ubuntu necesita 384 de ram como minimo, asi que con 512 deberia funcionar. No se si la placa de video te chupara lo queda. 
Lo mejor y mas simple es que te bajes el LiveCD de Ubuntu y arranques la maquina desde ahi, para ver si levanta. De esa forma vas a ver si te funciona todo el hardware y ademas vas a poder fijate el tema de la placa de video con el comando que te dijeron mas arriba. 
Eso si. Tene presente que desde el LiveCD te va a ir mas lento que si lo tuvieras instalado.
Por el procesador, no te preocupes. Yo hasta hace poco tenia una con un procesador de 1.7, que originalmente me habia venido con 512 de ram (despues le puse 2gb de ram) y volaba.

---

### Post by xlxScorpioxlx on 2009-10-20
Disculpen mi ignorancia, pero cuál LiveCD me descargo? es decir, descargo el de Xbuntu? cuando lo corra, eso no me afecta en nada la instalación que tengo que XP? es decir, puedo correr el liveCD y luego reiniciar, sacar el CD y volver a arrancar por el XP? es que todavía no he hecho backup porque no tengo espacio en ningún laptop :(

---

### Post by josecuervo86 on 2009-10-20
El LiveCD se usa justamente para probar el sistema sin alterar el equipo (elijiendo la opcion específica en el menu de arranque), pero tambien se puede usar para instalarlo en la maquina. Si no le especificas que te lo instale, no te lo va a instalar. Por supuesto que tu partición con XP quedara tal cual, sin ninguna modificacion de ningun tipo!

---

### Post by Tosh78 on 2009-10-21
En tu caso yo probaria con el de Ubuntu. Y como te dicen, no te preocupes que si no elegis la opcion de instalar no va a modificar nada de tu equipo.

---

