---
title: "problema al iniciar ubuntu(sale el gdm)"
date: 2009-08-17
forum: Software
---

### Post by sianhulo on 2009-08-17
hace poco reinstale ubuntu(ayer xD) y la ultima ves que se me reinicio,puse usuario y contraseña,me sale la pantalla negra con mi cursor(como cuando carga ubuntu),pero nunca sale cargando y se queda en negro(el cursor no se congela sino que se puede mover aun con el mouse),y no me queda mas que apagar la pc desde el boton(fisico).


informacion extra:tengo el gdm,el tema de escritorio y del cursor cambiado,pero ya habia reiniciado la pc despues de instalarlos y aun funcionaba ubuntu(despues que dejo de funcionar el gdm muestra el theme que le instale,y el cursor se sigo viendo normal,como cuando funcionaba),tengo ubuntu 9.04,usando gnome

---

### Post by guillermolisi on 2009-08-17
> **sianhulo said:**
> hace poco reinstale ubuntu(ayer xD) y la ultima ves que se me reinicio,puse usuario y contraseña,me sale la pantalla negra con mi cursor(como cuando carga ubuntu),pero nunca sale cargando y se queda en negro(el cursor no se congela sino que se puede mover aun con el mouse),y no me queda mas que apagar la pc desde el boton(fisico).


informacion extra:tengo el gdm,el tema de escritorio y del cursor cambiado,pero ya habia reiniciado la pc despues de instalarlos y aun funcionaba ubuntu(despues que dejo de funcionar el gdm muestra el theme que le instale,y el cursor se sigo viendo normal,como cuando funcionaba),tengo ubuntu 9.04,usando gnome
Probaste de ver si tenes consolas con Ctrl+Alt+F1/F6 ?

---

### Post by sianhulo on 2009-08-17
> **guillermolisi said:**
> Probaste de ver si tenes consolas con Ctrl+Alt+F1/F6 ?
efectivamente,se puede usar el modo consola

---

### Post by guillermolisi on 2009-08-17
Actualizaste despues de instalar ?
Que placa de video tenes ?
Que version de Ubuntu tenias antes de reinstalar ?
Que version de kernel usabas antes ? ( con la cual supongo funcionaba todo bien)

---

### Post by jjgomera on 2009-08-17
si tienes acceso a las consolas prueba a arrancar las x, usa el comando startx a ver que error te da

---

### Post by sianhulo on 2009-08-17
> **guillermolisi said:**
> Actualizaste despues de instalar ?
Que placa de video tenes ?
Que version de Ubuntu tenias antes de reinstalar ?
Que version de kernel usabas antes ? ( con la cual supongo funcionaba todo bien)
no,no,no.
cuando reinstale(y reinicie por varios programas)al principio me funcionaba,pero ahora ya no,antes y despues de reinstalar usaba 9.04,el kernel no lo recuerdo,mi tarjeta de video es una nvidia geforce 9500gt(y funciona bien)

pd:2gb ram,core 2 duo 2.53 ghz

---

### Post by guillermolisi on 2009-08-17
> **sianhulo said:**
> no,no,no.
cuando reinstale(y reinicie por varios programas)al principio me funcionaba,pero ahora ya no,antes y despues de reinstalar usaba 9.04,el kernel no lo recuerdo,mi tarjeta de video es una nvidia geforce 9500gt(y funciona bien)

pd:2gb ram,core 2 duo 2.53 ghz
Con el "no, no, no" asumo que no actualizaste despues de reinstalar. Si es asi, hacelo.

La tarjeta de video puede andar muy bien pero si no carga el driver correctamente no vas a poder usar el escritorio grafico.

---

### Post by sianhulo on 2009-08-17
> **guillermolisi said:**
> Con el "no, no, no" asumo que no actualizaste despues de reinstalar. Si es asi, hacelo.

La tarjeta de video puede andar muy bien pero si no carga el driver correctamente no vas a poder usar el escritorio grafico.
me refiero a que pense que tu pensabas que despues de reinstalar no funcionaba ubuntu

---

### Post by guillermolisi on 2009-08-17
> **sianhulo said:**
> me refiero a que pense que tu pensabas que despues de reinstalar no funcionaba ubuntu
Eso se verifico cuando respondiste que tenias las consolas operativas.

---

### Post by sianhulo on 2009-08-18
jjgomera,perdon por no contestarte,pero no habia reiniciado,me marco el siguiente error:

fatal server error
server is already active for display 0
if this server is no longer running,remove /tmo/.x0.lock and start again

please consult the The X.Org foundation support

at [http://wiki.x.org](http://wiki.x.org)
for help
(lo del te The es asi)
no elimine el archivo porque no se que consecuencias pudo traer,aunque creo que es para cerrar la sesion grafica

---

### Post by Fistandantilus on 2009-08-19
Eso es q ya tenes un xorg activo para el display 0.
hacele un pidof gmd (o Xorg) y un kill a los pids que te tira, luego trata de iniciarlo otra vez a ver que te tira.

Si con el pidof no te tiro ningun pid, chequea si tenes el archivo  /tmp/.X0-lock, si existe eliminalo(solo si no te tiro ningun pid tanto con gmd como con Xorg).

---

### Post by sianhulo on 2009-08-19
hice lo que me dijiste,me salieron los pids 2721 y 2724, los mate, puse starx y me salio:

xauth:creating new authory file /home/simon/.xauthorty

X.Org X server 1.6.0
realese date: 2009-2-25
x protocol version 11, revision 0
build operating system: linux 2.6.24-23-server i686 ubuntu
current operating system: linux simon-desktop 2.6.28-14-generic #47-ubuntu SMP S
at jul 25 00:28:35 UTC 2009 i686
Build date: 09 april 2009 02:10:02 AM
xorg-server 2:1.6.0-0ubuntu 14 (buildd@rothera.buildd)
before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
to make sure that you have latest version.
markers: (--) probed, (**) from config file, (==) default settting
(++) from comman line, (!!) notice (II) informational,
(WW) warning, (EE) error, (NI) not implemented, (??) unknown
(==) log file "Var/log/xorg.log", time: wed aug 19 12:19:002009
(==) using config file "etc/x11/xorg.conf"
the xkeyboard key map compiler(xkbcomp) reports:
>warning:         type"ONE_LEVEL" has 1 levels,but <RALT> has 2 symbols
>                      ignoring extra symbols
errors from xkbcomp are not fatal to the server x

---

### Post by Fistandantilus on 2009-08-19
no veo nada rara...

proba de hacer lo mismo pero tipea gdm en ves de startx.

si se te muere justo despues de iniciar sesion debe ser el gdm .

pega lo que esta en /var/log/gdm/:0.log a ver si te tiro algun error ahi.

---

### Post by sianhulo on 2009-08-20
> **Fistandantilus said:**
> no veo nada rara...

proba de hacer lo mismo pero tipea gdm en ves de startx.

si se te muere justo despues de iniciar sesion debe ser el gdm .

pega lo que esta en /var/log/gdm/:0.log a ver si te tiro algun error ahi.me sale el inicio de sesion,pero despues cuando deberia de salir ubuntu,sale una pantalla negra y lo unico que sale es el mouse.

---

### Post by staar on 2009-08-20
suena a que la configuración de gnome está corrupta, hace una cosa, crea un nuevo usuario con ```
sudo adduser *nombreusuarionuevo*
``` y después ponele una contraseña con ```
sudo passwd *nombreusuarionuevo*
``` e intentá loguearte con él...

saludos

---

### Post by sianhulo on 2009-08-22
> **staar said:**
> suena a que la configuración de gnome está corrupta, hace una cosa, crea un nuevo usuario con ```
sudo adduser *nombreusuarionuevo*
``` y después ponele una contraseña con ```
sudo passwd *nombreusuarionuevo*
``` e intentá loguearte con él...

saludos
el problema no es el logueo,el problema es que no carga el escritorio(se queda negro)

---

### Post by guillermolisi on 2009-08-22
> **sianhulo said:**
> el problema no es el logueo,el problema es que no carga el escritorio(se queda negro)
Estaba pensando que en realidad no se sabe si carga o no el escritorio porque la pantalla queda negra.

Luego, podra ser alguna cuestion de frecuencias de refresh/sincronizacion vertical/horizontal del monitor que estan fuera de rango y por eso queda negra la pantalla ?

Para saber si carga o no Gnome, nada mejor que un "top" en busca del proceso gdm o "ps -ef |grep gdm" y si aparece corriendo entonces esta cargado.

---

### Post by staar on 2009-08-22
si se queda la pantalla negra, pero el puntero del mouse se ve, entonces queda descartado algún problema con la configuración de pantalla...

lo que te propongo que hagas es que crees un usuario nuevo para poder iniciar gnome con una configuración default, a eso apunto, a que la configuración de gnome (o de algún otro programa que arranque al inicio) de tu usuario está corrupta, o tiene algún problema, creando un usuario nuevo podés verificar si es ese el problema...

saludos

---

### Post by sianhulo on 2009-08-23
> **staar said:**
> si se queda la pantalla negra, pero el puntero del mouse se ve, entonces queda descartado algún problema con la configuración de pantalla...

lo que te propongo que hagas es que crees un usuario nuevo para poder iniciar gnome con una configuración default, a eso apunto, a que la configuración de gnome (o de algún otro programa que arranque al inicio) de tu usuario está corrupta, o tiene algún problema, creando un usuario nuevo podés verificar si es ese el problema...

saludos
es que cree un nuevo usuario y el problema persiste(efectivamente,la pantalla negra y el mouse sale)

---

