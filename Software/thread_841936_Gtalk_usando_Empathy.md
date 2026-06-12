---
title: "Gtalk usando Empathy"
date: 2008-06-26
forum: Software
---

### Post by sergiom99 on 2008-06-26
Gente, siguiendo este howto que parecería funcionar ([http://ubuntuforums.org/showthread.php?t=819046](http://ubuntuforums.org/showthread.php?t=819046)) traté de hacer andar el Google Talk con Voice Talk en Ubuntu.
Instalé los paquetes requeridos sin problemas, pero al momento de correrlo me tira un error>
```
sergio@kubuntu:~$ empathy

(empathy:18340): tp-glib-WARNING **: Failed to connect to starter bus: Failed to execute dbus-launch to autolaunch D-Bus session

```
Alguien tiene idea cuál es el problema y como arreglarlo? (también probé con sudo)

Si quieren puedo traducir el instructivo y ponerlo aca, parece que es un feature bastante requerido y extrañado en GNU/Linux el VOIP de Gtalk.

---

### Post by sergiom99 on 2008-06-26
creo que lo arregle con ```
sudo apt-get install dbus-x11

```
espero que instalar eso no rompa nada.
estoy conectado pero no tengo a nadie online para probarlo :-( abajo pego el tuto.

---

### Post by sergiom99 on 2008-06-26
> 
En Ubuntu 8.04 empathy puede usarse para usar el chat de voz de Google talk.

En una instalación actualizada de Ubuntu 8.04, usando Synaptic Package Manager agregar estos repos e instalar los paquetes indicados.
Instrucciones:
Sistema --> Administración --> Synaptic Package Manager

Ir a Settings->Repositories
Ir a Third Party Software --> Add;
Pegar la siguiente línea en APT line:

deb [http://ppa.launchpad.net/telepathy/ubuntu](http://ppa.launchpad.net/telepathy/ubuntu) hardy main

Salir y refrescar la lista de encabezados.

Buscar y elegir estos paquetes:
Empathy
telepathy-gabble
telepathy-mission-control
telepathy-stream-engine

Usar los últimos paquetes porque las versiones anteriores no admiten  Gtalk/Jingle VOIP.

Referencias:

   1. [https://launchpad.net/~telepathy/+archive](https://launchpad.net/~telepathy/+archive)
   2. [http://ubuntuforums.org/showpost.php...8&postcount=21](http://ubuntuforums.org/showpost.php...8&postcount=21)


Si da un error de dbus ver arriba.

Originalmente posteado en [http://ubuntuforums.org/showthread.php?t=819046](http://ubuntuforums.org/showthread.php?t=819046).
Créditos a **vigyani**

---

### Post by sergiom99 on 2008-07-11
che, alguien lo intento?
despues de mi emocion inicial, y que estaban mis contactos off-line, cuando encontre a alguien y lo probé, solo obtengo una pantalla grisada que no me permite hacer nada, mucho menos hablar:
[[IMG]http://img246.imagevenue.com/loc148/th_78968_instant4nea1_122_148lo.jpg[/IMG]](http://img246.imagevenue.com/img.php?image=78968_instant4nea1_122_148lo.jpg)

En el thread original tampoco tienen mucha explicacion.
Nadie usa Gtalk en linux?

---

### Post by sergiom99 on 2008-07-12
al arrancarlo en la konsola tira este mensaje:
```
sergio@kubuntu:~$ empathy
** (empathy:22495): DEBUG: mission_control_get_presence_actual: MC not running.
** (empathy:22495): DEBUG: mission_control_get_presence_message_actual: MC not running.

(empathy:22495): libebook-WARNING **: Can't find installed BookFactories

(empathy:22495): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
** (empathy:22495): DEBUG: mission_control_get_online_connections: MC not running.
** (empathy:22495): DEBUG: mission_control_get_connection_status: MC not running.
** (empathy:22495): DEBUG: mission_control_get_tpconnection: MC not running.
sergio@kubuntu:~$

```

me esta faltando algo? hay que reportar un bug en alguna parte?

---

### Post by sergiom99 on 2008-07-14
lo hice andar, o casi...
(ver el reporte de bug:
[http://bugzilla.gnome.org/show_bug.cgi?id=542815](http://bugzilla.gnome.org/show_bug.cgi?id=542815)
)

ahora tengo que arreglar el problema del sonido.

Alguien probó empathy con google talk???

---

