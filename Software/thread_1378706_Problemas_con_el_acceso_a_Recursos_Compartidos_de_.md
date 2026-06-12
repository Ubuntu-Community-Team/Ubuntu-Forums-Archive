---
title: "Problemas con el acceso a Recursos Compartidos de Windows"
date: 2010-01-11
forum: Software
---

### Post by TIaGoX on 2010-01-11
Hola gente del foro. Bueno primero aclaro que busque por varios de los foros de Ubuntu sin encontrar una explicación a mi problema. Además les aclaro que en caso de existir este mismo thread en otro lado invito a los moderadores a destruir con furia este hilo y por favor indicarme el camino.

Básicamente el problema consiste en el acceso a los Recursos Compartidos que creo en Windows.

Desde Windows hacia Ubuntu no tengo ningún problema para acceder.

Y por lo general desde Ubuntu hacia Windows tampoco, pero cada tanto (y sin todavía dilucidar la causa) al querer acceder a estos recursos a los cuales ya monte y ahora tengo como "Bookmarks" en mi lista de **Lugares**, el muy #~@% me vuelve a pedir la password para poder ver los archivos y demás. A pesar de ingresar infinidad de veces las credenciales correctas me rebota y no puedo acceder. Con el tiempo esto se arregla y vuelvo a entrar perfectamente. La verdad no llego a tocar nada para solucionarlo porque no encuentro solución en la red, solo "se auto-soluciona". Pero lamentablemente vuelve a pasar lo mismo, como por ejemplo ahora :(

Me gustaría que alguno de ustedes tenga alguna idea de como sacarme de encima este **molesto** inconveniente.

Espero haber expresado bien cual es el intringulis de la cuestión.

Saludos y espero sus comentarios. Gracias de antemano.

---

### Post by juancarlospaco on 2010-01-11
Para que Windows te deje entrar tiene que tener password, sino esta como deshabilitado a veces.

---

### Post by TIaGoX on 2010-01-11
Hola Juan, lo de la contraseña ya lo tengo contemplado y efectivamente el usuario que utilizo para conectarme a Windows tienen password. De hecho esta falla no es continua, en estos momentos no puedo conectarme, pero tal vez mañana prenda la PC y me encuentre con que si funciona.

Una cosa que no aclare antes es que la versión de Windows es XP.

Gracias por la respuesta :)

---

### Post by guillermolisi on 2010-01-12
> **TIaGoX said:**
> Hola Juan, lo de la contraseña ya lo tengo contemplado y efectivamente el usuario que utilizo para conectarme a Windows tienen password. De hecho esta falla no es continua, en estos momentos no puedo conectarme, pero tal vez mañana prenda la PC y me encuentre con que si funciona.

Una cosa que no aclare antes es que la versión de Windows es XP.

Gracias por la respuesta :)
Las PC con Windows poseen IP estaticas ?
Como esta implementado Samba en esa red a nivel users, IPs admitidas y todo otro dato relacionado con estos ?
Que pasa si accedes a la PC con Windows via su IP ? Te muestra sus recursos compartidos a pesar de que no podes verlas en el browser de la LAN/Dominio ?

---

### Post by TIaGoX on 2010-01-12
> **guillermolisi said:**
> Las PC con Windows poseen IP estaticas ?
Como esta implementado Samba en esa red a nivel users, IPs admitidas y todo otro dato relacionado con estos ?
Que pasa si accedes a la PC con Windows via su IP ? Te muestra sus recursos compartidos a pesar de que no podes verlas en el browser de la LAN/Dominio ?

Hola Guillermo, gracias por el interés y el checklist de los datos útiles. La cosa es más o menos así.

Las computadoras están conectadas con un **Router Wi-Fi**. El direccionamiento IP lo provee el mismo Router pero, las direcciones, están reservadas para cada equipo, así que siempre es la misma IP para los dos.

El equipo con Windows es el Desktop, que esta conectado por cable al Router y el equipo con Ubuntu es mi laptop que el 95% del tiempo esta conectado por Wi-Fi y en algunos casos, que es necesario un poco de velocidad, por cable.

Ambos equipos se encuentran en el mismo grupo de trabajo. Y navegando la LAN (Places -> Network) veo los equipos tanto desde Windows como desde Ubuntu.

Accediendo por la dirección IP, como por el nombre NetBios de los equipos llego a **ver** los "Recursos compartidos" de Windows. Sin problemas pero cuando quiero acceder a esos mismos recursos (a los cuales ya accedí antes y la password quedo seteada para que no la pregunte más) me vuelve a pedir la confirmación de la contraseña y a pesar de poner las credenciales correctas me rebota una y otra vez.

A nivel de usuario no hay nada demasiado complejo, solo intento acceder con los usuarios creados localmente en el equipo con Windows, que tienen los permisos como se debe, de hecho lo pruebo con el usuario "WINDOWS-PC\Administrador"

Creo que no me falto mas información, cualquier cosa haganmelo saber :)

Saludos y gracias.

---

### Post by guillermolisi on 2010-01-12
> **TIaGoX said:**
> Hola Guillermo, gracias por el interés y el checklist de los datos útiles. La cosa es más o menos así.

Las computadoras están conectadas con un **Router Wi-Fi**. El direccionamiento IP lo provee el mismo Router pero, las direcciones, están reservadas para cada equipo, así que siempre es la misma IP para los dos.

El equipo con Windows es el Desktop, que esta conectado por cable al Router y el equipo con Ubuntu es mi laptop que el 95% del tiempo esta conectado por Wi-Fi y en algunos casos, que es necesario un poco de velocidad, por cable.

Ambos equipos se encuentran en el mismo grupo de trabajo. Y navegando la LAN (Places -> Network) veo los equipos tanto desde Windows como desde Ubuntu.

Accediendo por la dirección IP, como por el nombre NetBios de los equipos llego a **ver** los "Recursos compartidos" de Windows. Sin problemas pero cuando quiero acceder a esos mismos recursos (a los cuales ya accedí antes y la password quedo seteada para que no la pregunte más) me vuelve a pedir la confirmación de la contraseña y a pesar de poner las credenciales correctas me rebota una y otra vez.

A nivel de usuario no hay nada demasiado complejo, solo intento acceder con los usuarios creados localmente en el equipo con Windows, que tienen los permisos como se debe, de hecho lo pruebo con el usuario "WINDOWS-PC\Administrador"

Creo que no me falto mas información, cualquier cosa haganmelo saber :)

Saludos y gracias.
Cuando te solicita la pass para acceder al recurso compartido que esta en Windows, que pasa si le das Cancelar en lugar de ingresar el dato correcto ? Ingresa o te da un mensaje de error ?

---

### Post by TIaGoX on 2010-01-12
> **guillermolisi said:**
> Cuando te solicita la pass para acceder al recurso compartido que esta en Windows, que pasa si le das Cancelar en lugar de ingresar el dato correcto ? Ingresa o te da un mensaje de error ?

Simplemente lo vuelve a pedir sin más, no informa que el password sea incorrecto ni nada similar, vuelve el prompt para ingresar los datos. Si le das cancelar no hace nada tampoco.

---

### Post by TIaGoX on 2010-01-12
Intente además, reiniciando el servicio de Samba en mi laptop. Restableciendo la contraseña en Windows. Y nada de eso funciona, la configuración de Samba esta por default el único retoque es la configuración del nombre del Grupo de Trabajo, pero que no son hechos que hayan desencadenado la falla sino que así como esta todo ahora funcionaba perfectamente.

---

### Post by TIaGoX on 2010-01-19
Actualizo un dato más. Probando nuevas cosas, me doy cuenta que me falto informar sobre un dato por demás importante. Los recursos a los que trato de acceder, sin éxito, son a los **C$**, **D$**, etc. Esos famosos recursos por defecto de Windows.

Ayer cree otra carpeta compartida y pude acceder sin problemas. Ahora, no hubieron actualizaciones en Windows como para que cambie algo en la configuración de esos recursos *ocultos*.

Bueno imagino que mas de uno ahora se va a acordar de todos mis familiares, pero sigo queriendo acceder a esos recursos nativos de Windows. Ojala a alguien se le prenda la lamparita :)

Saludos.

---

### Post by macardos on 2010-01-25
Hola!

Primer post en el foro.

Lo que te pasa me viene pasando desde que instalé Ubuntu al querer conectarme con mi máquina XP. Y tenes razón: el problema son los dichosos recursos $, que nunca entendí para qué están. La primera vez que me conecté, vi los recursos por defecto $, pero entré en ese ciclo infinito de pedidos de passwd. Finalmente comprendí que lo que debía hacer era compartir las carpetas/archivos desde Win$, y santo remedio. A partir de entonces veo los $ y los otros, pero los únicos a los que puedo entrar son los que yo explícitamente dije que eran accesibles. Aun hoy sigo viendo D$, que es una particion chica que me quedo en el disco de XP a la que nunca dije que quisiera compartir (y que de hecho solo tiene algunos archivos de algun backup que hice alguna vez).

Es mas, alguna vez me voy a poner a investigar para ver como hago para que la máquina XP comparta su DVD (la compu que uso corre unicamente ubuntu y nunca le cambie la lectoescritora de CD por DVD, y está ubicada junto a la otra).

Espero sirva el comentario.

Hasta pronto.

---

### Post by TIaGoX on 2010-01-26
> **macardos said:**
> Hola!

Primer post en el foro.

Lo que te pasa me viene pasando desde que instalé Ubuntu al querer conectarme con mi máquina XP. Y tenes razón: el problema son los dichosos recursos $, que nunca entendí para qué están. La primera vez que me conecté, vi los recursos por defecto $, pero entré en ese ciclo infinito de pedidos de passwd. Finalmente comprendí que lo que debía hacer era compartir las carpetas/archivos desde Win$, y santo remedio. A partir de entonces veo los $ y los otros, pero los únicos a los que puedo entrar son los que yo explícitamente dije que eran accesibles. Aun hoy sigo viendo D$, que es una particion chica que me quedo en el disco de XP a la que nunca dije que quisiera compartir (y que de hecho solo tiene algunos archivos de algun backup que hice alguna vez).

Es mas, alguna vez me voy a poner a investigar para ver como hago para que la máquina XP comparta su DVD (la compu que uso corre unicamente ubuntu y nunca le cambie la lectoescritora de CD por DVD, y está ubicada junto a la otra).

Espero sirva el comentario.

Hasta pronto.
Exactamente eso es una de las soluciones. Pero en este caso yo si podía acceder a esas particiones ocultas. El tema es que esas particiones estan ocultas dentro de las redes Windows. Solo si escribís la ruta completa a los recursos $, ahí podes acceder desde una máquina Windows.

Ahora solo a modo informativo, los recursos $ son como si vos estuvieras trabajando directamente con el disco, sin ningún tipo de restricción si tenes las credenciales de Administrador. Son recursos más que útiles para todos los Sys Admin.

Ahora bien, se da que yo no quiero compartir nada en ese equipo de Windows. Y si espero acceder por medio de los recursos $, más que nada porque no quiero que cualquier otro usuario de la red pueda ver algún recursos compartidos.

---

### Post by macardos on 2010-01-27
Es evidente que tenemos situaciones distintas.

En mi caso no me interesa mucho restringir, pues la red es solo local a los miembros de la casa, y en general no separamos aguas (mi mujer y yo trabajamos en lo mismo y el nene tiene 8); alguna vez lo hicimos, pero no nos funciona. Debe ser por eso que ni siquiera tengo definido un usuario administrador en Win$. Quiza de haberlo tenido me hubiese enterado de para que servian esos dichosos recursos $.

Como sea, gracias por el dato. Al final, terminaste ayudandome vos a mi. Al fin y al cabo, deje de usar Win$ hace ya 4 años definitivamente.

---

### Post by jorgtledo on 2010-01-27
Mira yo tube un problema parecido en mi caso tengo samba en ubuntu, por ejemplo compartiendo la carpeta xxx.. con el user root:toor ,etc por dar un ej al querer acceder desde windows me pedia el usuario y contraseña pero no me dejaba acceder, modifique los permisos en ubuntu, los usuarios y todo parecia estar bien pero me estaba volviendo loco #-oal final lo solucione cambiando el grupo de trabajo de windows por el que tenia ubuntu , asi pertenecian a la misma red y me funciono y pude acceder en este caso se llamaba por dar un ejemplo \\GNU\kerberos\carpeta.. 
esa seria una posible solucion pero no se si viene a tu caso;)

---

### Post by TIaGoX on 2010-01-28
> **macardos said:**
> Es evidente que tenemos situaciones distintas.

En mi caso no me interesa mucho restringir, pues la red es solo local a los miembros de la casa, y en general no separamos aguas (mi mujer y yo trabajamos en lo mismo y el nene tiene 8); alguna vez lo hicimos, pero no nos funciona. Debe ser por eso que ni siquiera tengo definido un usuario administrador en Win$. Quiza de haberlo tenido me hubiese enterado de para que servian esos dichosos recursos $.

Como sea, gracias por el dato. Al final, terminaste ayudandome vos a mi. Al fin y al cabo, deje de usar Win$ hace ya 4 años definitivamente.

Es bueno saber que el dato te sirvió. Yo me puse más de en serio este año con Ubuntu y estoy también tratando de despegarme definitivamente, pero es un proceso largo cuando algunos equipos son compartidos por mas personas. Ahora que pude hacerme de una laptop propia se me hizo un poco más fácil la migración.

> **jorgtledo said:**
> Mira yo tube un problema parecido en mi caso tengo samba en ubuntu, por ejemplo compartiendo la carpeta xxx.. con el user root:toor ,etc por dar un ej al querer acceder desde windows me pedia el usuario y contraseña pero no me dejaba acceder, modifique los permisos en ubuntu, los usuarios y todo parecia estar bien pero me estaba volviendo loco #-oal final lo solucione cambiando el grupo de trabajo de windows por el que tenia ubuntu , asi pertenecian a la misma red y me funciono y pude acceder en este caso se llamaba por dar un ejemplo \\GNU\kerberos\carpeta.. 
esa seria una posible solucion pero no se si viene a tu caso;)

Mmm, en mi caso todo el tema de Grupos de trabajo esta solucionado, y de hecho puedo compartir recursos comunes desde Windows. El acceso desde la PC con Win hacia la de Ubuntu la puedo realizar sin problemas. El tema esta en poder acceder a los recursos "$*". Desde Windows también revisé permisos y usuarios, pero todo esta normal. Además, antes podía acceder a esos mismos recursos y ahora ya no.

---

