---
title: "[SOLVED] Usplash"
date: 2008-09-22
forum: Software
---

### Post by ramiro_md on 2008-09-22
Gente, estaba algo aburrido hoy por la tarde y me puse a ver que podía hacerle de nuevo al sistema. 
Entonces se me ocurrió cambiarle el usplash. Buscando por google encontre esta "guía" [http://neodian.blogsome.com/2007/03/14/instalar-un-usplash-en-ubuntu-2/](http://neodian.blogsome.com/2007/03/14/instalar-un-usplash-en-ubuntu-2/) donde reliazo todos los pasos a la perfección hasta la hora de ejecutar la siguiente linea de comando: 
 **update-alternatives -install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/local/lib/usplash/tux_world-theme.so**
Al ejecutar esto me sale el siguiente error:
**update-alternatives: argumento `-install' desconocido**
NO sé realmente si hay una forma más fácil de hacerlo, o en qué me estoy equivocando, espero que me den una mano. Un saludo.

---

### Post by WanderingKnight on 2008-09-22
Eh, la opción es --install, no -install :p

Editado porque me confundí en la lectura :p

---

### Post by luks911 on 2008-09-22
Ramiro,
Dos cosas: por lo que veo, el problema parace ser que antes de "install" no va un guión, sino dos. O sea
```
update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/local/lib/usplash/tux_world-theme.so
```
Lo veo comparando con [este artículo]("http://www.espaciolinux.com/tallerlinux-articulo-82.html").

Y por otro lado, hay una forma más fácil de hacerlo. Instalá [StartUp Manager]("http://www.guia-ubuntu.org/index.php?title=StartUp_Manager") 

```
sudo aptitude install startupmanager
```

Entre otras cosas permite cambiar el tema del Usplash, está piola y es completamente gráfico.

Un saludo

---

### Post by vk-cdg on 2008-09-22
Por lo que leí no hay forma de ponerle usplash widescreen.

---

### Post by zeroadrenaline on 2008-09-22
Chicos chicos, si buscan en ubuntu-es encontraban la respuesta rapidin rapidin, hace tiempo que hay un how to 
[http://www.ubuntu-es.org/index.php?q=node/57357](http://www.ubuntu-es.org/index.php?q=node/57357)
Yo lo use y funciona barbaro.

---

### Post by pol666 on 2008-09-22
yo cambio el usplash con el programa startupmanager ;)

---

### Post by zeroadrenaline on 2008-09-22
A mi startupmanager me fayo mal, el metodo que te pase no tiene error posible, si lo seguis como corresponde, pero con startupmanager hay cosas que no son tan claras y simples como aparecen en la net.
A mi no me gusto.
Yo recomiendo el post que puse antes (sic).
Eso es todo PAZ!.

---

### Post by ramiro_md on 2008-09-23
Bueno muchachos, probe con la guía de ubuntu-es, me volví loco y terminó por no funcionar. Asique instale el startupmanager, la verdad muy buen programa, bastante completo, debería venir instala ya. Lo único que le faltaría es una opción de "preview" para poder ver el usplash sin tener que reiniciar. Pero poniendo "sudo usplash -c"(lo saque de la guía de ubuntu-es) en la consola se puede hacer tranquilamente. Gracias, y un saludo.

---

### Post by Mister X on 2008-09-23
a mi tampoco me gusto el programa ese startupmanager, prefiero leer un poquito, saber lo que estoy haciendo y hacerlo en la consola ;)

---

### Post by ramiro_md on 2008-09-24
> **Mister X said:**
> a mi tampoco me gusto el programa ese startupmanager, prefiero leer un poquito, saber lo que estoy haciendo y hacerlo en la consola ;)

Y eso es lo copado en realidad, pero cuando las cosas no te salen y te come la cabeza, siempre está la opción fácil jejeje.

---

