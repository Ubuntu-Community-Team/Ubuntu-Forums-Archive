---
title: "Problemas con Avahi entre JJ y KK"
date: 2009-11-25
forum: Software
---

### Post by Fistandantilus on 2009-11-25
Hola!, 

El tema es el siguiente: en mi casa tengo un router y debajo del router tengo 2 maquinas, la de mi viejo con JJ y la mia con KK. El problema es que desde la maquina de mi viejo "veo" la mia por medio de avahi(aunque no siempre), pero desde la mia no lo veo a él.
Además cuando ejecuto "avahi-browse" me sale un mensaje raro que presupongo que debe estar relacionado(xq en la maquina de mi viejo ese mensaje no me sale).

```

gera@gera-desktop:~$ avahi-browse -avt
Versión del servidor: avahi 0.6.25; Nombre del equipo: gera-desktop.local
E Ifaz Prot Nombre                                        Tipo                 Dominio
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect
+ eth0 IPv4 gera-desktop [00:15:f2:74:50:02]              Workstation          local
+ eth0 IPv4 Export                                        _nfs4._tcp           local
: Caché agotada
: Todo por ahora

```Antes cuando los dos teníamos JJ no pasaba... no se si será algún tema de incompatibilidad entre las versiones de avahi-daemon...

Alguna idea de xq será???

Saludos!.

---

### Post by Fistandantilus on 2009-11-26
Hoy a la mañana descubrí otra cosa rara...

Ayer a la noche antes de irme a dormir ejecute otra vez el comando "avahi-browse" y, al menos, me veia a mi... Pero hoy a la mañana(teniendo la computadora prendida toda la noche) ya no aparecia siquiera las entradas que muestro en el post anterior... nada... solo el warning :(

Lo estoy sintiendo muy inestable el avahi en KK. 

Alguien ha tenido alguna experiencia similar con avahi?

Saludos.

---

### Post by Fistandantilus on 2009-11-27
Por lo que sigo viendo sobre el tema no es un problema entre JJ y KK, sino entre avahi-deamon y d-bus.

Justamente estoy probando un proyecto que usa d-bus para buscar info en avahi-deamon y conectarse a ciertas señalas... Y casi siempre cuando ejecuto el servicio(del projecto, no avahi) me empieza a tirar time-outs al tratar de conectarse con el bus de avahi-deamon. Si reinicio el avahi-deamon empieza a funcionar correctamente, pero al rato otra vez deja de funcionar...

Ya llega a ser frustrante este problema, me esta retrasando mucho en otros temas :(

¿Alguna idea?, ya estoy llegando al punto de leerme los funtes del "avahi-browse" para ver de donde puede salir ese "warning" que muestro en el 1er post...

Saludos.

---

