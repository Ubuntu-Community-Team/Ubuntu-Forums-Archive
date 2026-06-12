---
title: "WTF Kernel's?"
date: 2008-08-27
forum: Software
---

### Post by vk-cdg on 2008-08-27
Esto que me pasa no se si es un problema, si es normal o que... 

Actualmente el Kernel que estoy usando es el 2.6.24.21. Ayer cuando llego a casa veo en la desktop que tengo actualizaciones pendientes. Cuando decido instalarlas me muestra esta lista de actualizaciones que adjunto en la imagen!

Por que me baja un kernel mas viejo cuando ya estoy usando uno mas nuevo?

---

### Post by sergiom99 on 2008-08-27
a mi ya me bajo el 19 como 3 veces en los ultimos 2 meses o algo asi.

---

### Post by luks911 on 2008-08-27
> **]Esto que me pasa no se si es un problema, si es normal o que...

Actualmente el Kernel que estoy usando es el 2.6.24.21. Ayer cuando llego a casa veo en la desktop que tengo actualizaciones pendientes. Cuando decido instalarlas me muestra esta lista de actualizaciones que adjunto en la imagen!

Por que me baja un kernel mas viejo cuando ya estoy usando uno mas nuevo?[/QUOTE]

Ni la menor idea, pero por curiosidad, ¿qué repositorios usás para tener el 2.6.24.21, porque con todos menos el proposed tengo el 2.6.24.19?

[QUOTE=sergiom99 said:**
> a mi ya me bajo el 19 como 3 veces en los ultimos 2 meses o algo asi.

A mí lo mismo. Creo que son actualizaciones de seguridad, así que serían versiones distintas, creo.

---

### Post by vk-cdg on 2008-08-27
> **luks911 said:**
> ...por curiosidad, ¿qué repositorios usás para tener el 2.6.24.21, porque con todos menos el proposed tengo el 2.6.24.19?...

Tengo todos menos el proposed igual que vos, pero lo descargo del servidor principal. Cuando tenía configurado servidor para Argentina no pasaba del 19. En la PC del laburo por algún motivo quedó configurado Servidor Principal y vi que tenia mas actualizaciones (y mas frecuentes) que en casa (con el servidor de Argentina). 

A partir de ahí lo configuré así tanto en la desktop como en la notebook.

---

### Post by luks911 on 2008-08-27
> **vk-cdg said:**
> Tengo todos menos el proposed igual que vos, pero lo descargo del servidor principal. Cuando tenía configurado servidor para Argentina no pasaba del 19. En la PC del laburo por algún motivo quedó configurado Servidor Principal y vi que tenia mas actualizaciones (y mas frecuentes) que en casa (con el servidor de Argentina). 

A partir de ahí lo configuré así tanto en la desktop como en la notebook.

Ah, mirá vos. Lo voy a tener en cuenta, porque sí uso el servidor de Argentina. Estaría bueno que alguno de los que participa más en el proyecto explique a qué se debe. 
¿Discriminan al tercer mundo y nos dan kernels viejos? Jaja, es un chiste, claro. :biggrin:

---

### Post by sergiom99 on 2008-08-27
hablando de repos, a ver si existe y alguien me puede dar una mano.
La familia de distros RH/CentOS, que usan yum para los updates, tienen un plugin para el yum que cuando lo corres por primera vez (o despues de vaciar el cache) testean los repos y descargan del mas rapido (en mi caso desde uno .br)

hay algo asi en apt-get?

---

### Post by luks911 on 2008-08-27
> **sergiom99 said:**
> hablando de repos, a ver si existe y alguien me puede dar una mano.
La familia de distros RH/CentOS, que usan yum para los updates, tienen un plugin para el yum que cuando lo corres por primera vez (o despues de vaciar el cache) testean los repos y descargan del mas rapido (en mi caso desde uno .br)

hay algo asi en apt-get?

No lo explico porque no tengo tiempo, pero sí se puede. Acá ([http://tuxpepino.wordpress.com/2008/04/21/tip-elige-automaticamente-el-repositorio-de-ubuntu-mas-rapido/](http://tuxpepino.wordpress.com/2008/04/21/tip-elige-automaticamente-el-repositorio-de-ubuntu-mas-rapido/)) el cómo. Es fácil.

Saludos

---

### Post by sergiom99 on 2008-08-27
perfecto, le pego una mirada.
Grax!

---

### Post by lega on 2008-08-27
> **luks911 said:**
>  porque con todos menos el proposed...

> **vk-cdg  said:**
> tengo todos menos el proposed igual que vos
Mirá vos, no sabía que algunos servidores estaban más actualizados que otros...ahora preguntonta, "todos menos el proposed" significa backports tambien activado?

Pregunto porque yo activé todo menos proposed y backports y puse el servidor principal y lo unico que me bajó fue una actualización de yelp o algo parecido :)

---

### Post by luks911 on 2008-08-27
> **lega said:**
> Mirá vos, no sabía que algunos servidores estaban más actualizados que otros...ahora preguntonta, "todos menos el proposed" significa backports tambien activado?

Pregunto porque yo activé todo menos proposed y backports y puse el servidor principal y lo unico que me bajó fue una actualización de yelp o algo parecido :)

En mi caso sí, tengo backports activado. Pero me pasa lo mismo, sólo actualizó yelp. El kernel sigue siendo el mismo:confused:

---

### Post by vk-cdg on 2008-08-27
Llegué a casa y me fijé como lo tengo. Acá van las capturas.

---

### Post by luks911 on 2008-08-27
Aaaaaaaaaaaaaahhhhhhhhhhhhhhh, pero tenés activado el repositorio proposed. Por eso tenés otro kernel. 

:lolflag:

---

### Post by pol666 on 2008-08-27
yo uso uno re viejo como de abril, nunca lo actualizo. y hoy se me ocurrio hacerlo pero fue en vano, en el grub aparecia el viejo nomas. Por un lado mejor despues tengo que bardos con los driver nvidia

---

### Post by lega on 2008-08-27
> **luks911 said:**
> Aaaaaaaaaaaaaahhhhhhhhhhhhhhh, pero tenés activado el repositorio proposed. Por eso tenés otro kernel. 



Aaaaaaaaaahhhhhhhhhhhhh :):):):)

---

### Post by vk-cdg on 2008-08-27
Si, el único que no tengo habilitado es el backports

---

### Post by steve_ignorant on 2008-08-30
bueno lo posteo aca, porq es unt ema del kernel, alguno sabe si hay algun parche o alguna actualizacion para el error(grave) de seguridad, que hay cuando alguno te entra en la pc y logra acceder como "root" ? sabia que habia un problema en eso de las versiones 6.0 a 8.06. 

¿tienen alguna idea de eso?

---

### Post by lega on 2008-08-30
creo, alguien me corregirá si no es cierto, que ya se corrigio esa vulneralidad, si bajaste las actualizaciones esta semana ahí estaba te copio lo que leí en un blog.
> USN-637-1: Linux kernel vulnerabilities

Esta es la noticia de seguridad de Ubuntu que ha debido sacar un parche para solucionar una vulnerabilidad en el kernel.

Los sistemas afectados son:

    * Ubuntu 6.06 LTS
    * Ubuntu 7.04
    * Ubuntu 7.10
    * Ubuntu 8.04 LTS
    * Y por supuesto las mismas versiones de Kubuntu, Edubuntu y Xubuntu.

Como se soluciona?

Actualizando el kernel. Si tienes la actualización automática activada (por defecto) habrás visto que dispones de varios paquetes para actualizar. Luego de hacerlo será necesario reinicializar el sistema.

---

