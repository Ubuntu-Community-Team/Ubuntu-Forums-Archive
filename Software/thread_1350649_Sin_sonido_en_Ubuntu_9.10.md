---
title: "Sin sonido en Ubuntu 9.10"
date: 2009-12-09
forum: Software
---

### Post by Abraxsmano on 2009-12-09
Como señale en el titulo me cargue la instalacion de Ubuntu 9.10 debido a unos deb que instale el dia de hoy ,resulta que ahora no tengo sonido y ademas sale la barra de Kubuntu al iniciar y apagar el sistema ¿puedo dejar ubuntu de 0 sin reinstalar el S.O eliminando todo lo instalado? ,resulta que esto se causo por querer isntalar los paquetes faltantes ,pero los ultimos packages me presentaron estos problemas ,vale decir que soy usuario offline ,por lo cual esto de los repositorios se me ha complicado un pelin ,esta es mi primera experiencia con Ubuntu ,¿existe alguna forma mas simple de dejar actualizado Ubuntu de forma Offline?,¿gun rar en alguna pagina ,algun auto install ? ,es que he bajado muchos packages pero al final me pierdo entre uno y otro ,saludos y gracias;)

---

### Post by Patriciologico on 2009-12-09
Por favor publica en la seccion adecuada, no es primera vez que lo haces. Procura leer las normas.


Movido a Instalacion y Actualizacion.


Empieza por eliminar completamente los paquetes que instalaste.

Si eres usuario offline te recomiendo que uses aptoncd. [http://www.guia-ubuntu.org/index.php?title=APTonCD](http://www.guia-ubuntu.org/index.php?title=APTonCD)

---

### Post by Carlos C on 2009-12-10
Edité el título porque iba contra las normas. En caso de dudas te pido que leas [esto]("http://ubuntuforums.org/showthread.php?t=1162750").

---

### Post by nechus on 2009-12-10
>he bajado muchos packages pero al final me pierdo entre uno y otro
:confused: No entiendo. ¿Estás bajando paquetes DEB uno por uno? ¡Usa Synaptic!
Usar Linux (al menos Ubuntu) sin conexión a Internet puede ser considerado una forma de masoquismo.

---

### Post by CdK1 on 2009-12-10
1°,. Ve que te dice "alsamixer", 2°.- elimina lo que instalaste con dpkg --purge "nombredelpackage", para saber el nombre del paquete que instalaste; dpkg -l | less, etc, etc, etc...

---

### Post by Abraxsmano on 2009-12-10
;)Si al final logre corregirlo , es facil perderse entre tantos debs y dependecias siendo usuario offline ,gracias a todos .

---

### Post by Carlos C on 2009-12-10
Lo doy por resuelto entonces. Creo que para una próxima ocasión puedes probar un script que un usuario de este foro desarrolló justamente para personas que necesitan instalar paquetes sin tener una conexión a internet y no quieren luchar con las dependencias:

[http://ubuntuforums.org/showthread.php?t=1342971](http://ubuntuforums.org/showthread.php?t=1342971)

Saludos.

Pd: me parece que este thread debiera ir en "Software" o no? (Ping! Patriciologico).

---

### Post by Abraxsmano on 2009-12-12
> **Carlos C said:**
> Lo doy por resuelto entonces. Creo que para una próxima ocasión puedes probar un script que un usuario de este foro desarrolló justamente para personas que necesitan instalar paquetes sin tener una conexión a internet y no quieren luchar con las dependencias:
 
[http://ubuntuforums.org/showthread.php?t=1342971](http://ubuntuforums.org/showthread.php?t=1342971)
 
Saludos.
 
Pd: me parece que este thread debiera ir en "Software" o no? (Ping! Patriciologico).
 
 
Bueno intente con UNVI ,lo recomiendo ampliamente , es un buen script bat , en un principio no me arrancaban las descargas pero me costo poco tiempo el darme por enterado para pòder ejecutarlo, descargue varios paquetes interesantes(quizas mas de lo que era necesario XD) bueno gracias y por favor que algun moderador de el tema por cerrado.
 
Pd: Si alguien tan Novato como yo necesita ayuda con este fichero ,solo haganmelo saber ,saludos

---

### Post by Abraxsmano on 2009-12-14
> **nechus said:**
> >he bajado muchos packages pero al final me pierdo entre uno y otro
:confused: No entiendo. ¿Estás bajando paquetes DEB uno por uno? ¡Usa Synaptic!
Usar Linux (al menos Ubuntu) sin conexión a Internet puede ser considerado una forma de masoquismo.
 
Si ya me entere de ello , como dijo otro Usuario "Ubuntu si Internet es como un asado sin Vino" , pero bueno UNVI ,me soluciono y facilito mucho las cosas,saludos.

---

### Post by Patriciologico on 2009-12-14
> **Carlos C said:**
> Pd: me parece que este thread debiera ir en "Software" o no? (Ping! Patriciologico).

Si, movido.

---

