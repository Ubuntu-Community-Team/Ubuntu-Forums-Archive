---
title: "Ayuda: Tips Para instalaciones en Pc de pocos recursos"
date: 2008-12-22
forum: Software
---

### Post by NickCis on 2008-12-22
Yo tengo una Compaq Presario 5473(del año 2000), que tiene:
Celeron 500mhz, 512mb (2 memorias dim pc-100 16chips de 256mb), y placa de video on board (dios sabra que tiene) y disco de 18gb.

Me decidi a hacer una instalacion minima, usando la guia de ubuntu ( [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems) )

El que mas me gusto de todos es el Openbox.

Yo lo que estoy buscando en esta maquina es un equilibrio entre rendimiento y estilo visual, no soporto ver un escritorio parecido a windows, o usar esos linux que para ahorrar memoria parecen un windows 98.

Ahora las preguntas:
1- Que recomiendan usar de barra de herramientas?
Las que vi por ahora son:
-[ Avant Window Navigator]("http://wiki.awn-project.org/index.php?title=Main_Page") Muy linda, pero segun algunos usuarios trae muchos problemas y consume mucha memoria (hay un bug conocido en Openbox, pero se como solucionarlo)
-[Wbar]("http://freshmeat.net/projects/wbar/") Linda, parecida al Awn, consume pocos recursos.
- [Lxpanel]("http://www.gnomefiles.org/app.php/LXPanel") Una barra de windows, por lo que vi, muy poco configurable.
- [Perlpanel]("http://freshmeat.net/projects/perlpanel/") Barra parecida a la de Gnome y Xfce.
- [fbpanel]("http://fbpanel.sourceforge.net/") Barra parecida a Gnome y Xfce
- [pypanel]("http://pypanel.sourceforge.net/")
- [Tinytask]("http://code.google.com/p/tint2/") Linda, transparente, configurable
- [Xfce Panel]("http://www.xfce.org/") La barra de Xfce, segun lo que tengo entendido consume mucho, para lo fea que es... xD

Las que mas me gustaron son: el Awn, Wbar y el Tinytask, que me recomiendan?

2 - Como poner Iconos en el escritorio? 
- [Idesk]("http://idesk.sourceforge.net/wiki/index.php/Main_Page")
- [Rox Desktop]("http://rox.sourceforge.net/desktop/static.html")

No entendi las diferencias, que recomiendan/sugieren, hay otros mas?

3 - Como hacer un autologin? (Que cuando prenda la pc, entre solo al usuario y a la sesion openbox)
- c4d0rn4 me sugirio usando el Rungetty, aca un post que explica como usarlo[http://ubuntuforums.org/showthread.php?p=4552480#post4552480]("http://ubuntuforums.org/showthread.php?p=4552480#post4552480")
En ese post, dice que le mato la pc :S, hay otra manera de hacerlo, me explican como se usa este programa?.

4 - FileManagers
- Xfe
- Thunar
- PcmanFM
- Rox Filer
Cual recomiendan? (Nautilus, ni lo puse por que tiene fama de consumir mucho)

5 - Exploradores
- Firefox
- Dillo, (espantoso, no entiendo como te lo dan de posibilidad xD)
- [swiftweasel]("http://swiftweasel.tuxfamily.org/")
- [Firefox 1.5]("http://wiki.dennyhalim.com/ubuntu-minimal-desktop#toc15")
- [internet explorer 5, 5.5, 6]("http://wiki.dennyhalim.com/ubuntu-minimal-desktop#toc15")
- [google chrome]("http://it.dennyhalim.com/2008/09/google-chrome-on-ubuntu-hardy.html")
Principalmente lo buscado es que consuma pocos recursos, y muestre las paginas bien (no importa tanto el soporte java, y todo eso)

6 - Programas de Chat (protocolo Msn)
- Pidgin
- [Emesene]("www.emesene.org/")
- [Amsn]("www.amsn-project.net/")
Lo que se busca: Minimo consumo de ram, que tenga alerta sonora y muestre un aviso en pantalla.

7 - Que prosesador de texto recomiendan que consuma poco? (abyword?)
8 - Que programa se puede usar para abrir archivos Pdf?
9 - Que programa se puede usar para descomprimir?
10 - Que terminal recomiendan? (xterm, etc)

No quiero instalar un login manager, por eso pregunto por el auto login.
El fin para esta pc, es que se pueda chatear, ver alguna que otra pagina por internet y usar el Tuxguitar, de manera fluida.

Perdonen, si esto es muy largo, pero bueno, vi muchos post acerca de instalaciones en pc de bajos recursos con pocas respuestas y esto (con la ayuda de ustedes) puede ser como un resumen.

Saludos.

---

### Post by andy_91 on 2008-12-22
> **NickCis said:**
> 

El que mas me gusto de todos es el Openbox. Totalmente, yo lo prefiero como WM

> **NickCis said:**
> 

-[Wbar]("http://freshmeat.net/projects/wbar/") Linda, parecida al Awn, consume pocos recursos.
- [Perlpanel]("http://freshmeat.net/projects/perlpanel/") Barra parecida a la de Gnome y Xfce.
- [Tinytask]("http://code.google.com/p/tint2/") Linda, transparente, configurable

Quedate con alguna de esas

> **NickCis said:**
> 
2 - Como poner Iconos en el escritorio? 
- [Idesk]("http://idesk.sourceforge.net/wiki/index.php/Main_Page")
- [Rox Desktop]("http://rox.sourceforge.net/desktop/static.html") por que no pcanfm trae buscador gestion del escritorio y explorador de archivos, todo en uno. Tambien esta xfdesktop, que esta bueno para combinar con wbar ya que se pueden minimizar las ventanas al escritorio(eso si tendrias que usar thunar)

FileManagers
- Xfe (recomendable si vas a usar idesk o roxdesktop)
- Thunar (tiene papelera, cosa que nose si te conviene mucho, pero es recomendable si elegis xfdesktop)
- PcmanFM (altamente recomendable, porque tenes 3 programas en uno)

Exploradores
- Firefox no
- [swiftweasel]("http://swiftweasel.tuxfamily.org/") no
- [Firefox 1.5]("http://wiki.dennyhalim.com/ubuntu-minimal-desktop#toc15") posiblemente
- [internet explorer 5, 5.5, 6]("http://wiki.dennyhalim.com/ubuntu-minimal-desktop#toc15") es cuestion de gustos (posiblemente)
- [google chrome]("http://it.dennyhalim.com/2008/09/google-chrome-on-ubuntu-hardy.html") no lo probe, pero dicen que es bueno

> Principalmente lo buscado es que consuma pocos recursos, y muestre las paginas bien (no importa tanto el soporte java, y todo eso)
 en ese caso podrias usar Kazehakase, se que suena trabalenguas pero es el que estoy probando ahora y corre muy bien, venia incluido en ubuntu lite 0.8
otras opciones: 

Epiphany, Galeon, seamonkey, netscape, mozilla u opera (creo que no hay mas, creo...)

Programas de Chat (protocolo Msn)
- Pidgin: posiblemente, pero no tiene aviso en la pantalla
- [Emesene:]("www.emesene.org/") recomendado
- [Amsn:]("www.amsn-project.net/") consume mucho, en otras palabras no

> 
7 - Que prosesador de texto recomiendan que consuma poco? 
abyword y leafpad para archivos de texto sencillo (txt entre otros)
> 8 - Que programa se puede usar para abrir archivos Pdf? 
google docs creo que los abre, sino evince
> 9 - Que programa se puede usar para descomprimir?
 Xarchiver
> 10 - Que terminal recomiendan? 
xterm

> 
Saludos

---

### Post by ramiro_md on 2008-12-22
Bueno NickCis acá te dejo algunas de mis ideas para lo que preguntas...espero te sirva.

> 2 - Como poner Iconos en el escritorio? 
Si te referías a enlazar carpetas, programas, discos y demás, podrías generar accesos directos (botón derecho en lo que deseas enlazar al escritorio y le dás a "crear enlace") luego los cortas y los pegás al desktop. 
Para ver "Mi Pc" la papelera, y el Home (Mis Documentos), debés configurarlo desde el gconf-editor de la siguiente manera:
- teclea alt + F2
- ingresa "gconf-editor" sin las comillas y dale a ejecutar
- despliega la ssiguientes ramas del panel izquierdo: apps > nautilus > desktop
- en el recuadro derecho tilda las opciones "computer_icon_visible" "home_icon_visible" y "trash_icon_visible".

> 3 - Como hacer un autologin? (Que cuando prenda la pc, entre solo al usuario y a la sesion openbox)
Yo lo configuré desde Sistema > Administración > Ventana de entrada, una vez ahí vas a la solapa "seguridad" y activás la opción "entrada automática" y elegís el usuario.

> 6 - Programas de Chat (protocolo Msn)
Emesene es muy livianito y es lo que más se puede asemejar a MSN Messenger (le podes poner los emoticons de msn y el estilo sin que consuma recursos de más), pidgin también es liviano y bueno, pero esticamente son algo diferentes.

> 8 - Que programa se puede usar para abrir archivos Pdf?
A mi me los abre con el "Document Viewer" el programa parece bueno y liviano. Creo que viene instalado por defecto.

> 9 - Que programa se puede usar para descomprimir?
El qué viene por defecto no te va ?

NOta: tal vez si usas aplicaciones de xfce te sean más dinámicas a la hora de ejecutarse.
Espero te haya ayudado en algo, un saludo y suerte !.

---

### Post by NickCis on 2008-12-23
> **ramiro_md said:**
> 
El qué viene por defecto no te va ?

No, no es eso, es que estoy haciendo una instalacion minima (desde 0, instalando el ubuntu Command Line), con otro gestor de ventanas (Openbox) y no viene nada instalado, y cuando digo nada, es NADA, ni explorador, ni gestor de ventanas, ni login manager, ni paneles, ni escritorio. 
Lo que busco es hacer usable a una maquina vieja, y para eso instalo aplicaciones de bajos recursos y solo las que nececito.

- Probe instalando la wbar, el thunar y el xfdesktop, saben como hago para que las aplicaciones minizadas aparescan en el escritorio?.

- En la Wbar, se puede poner un reloj?, y un "Mostrar Escritorio" (que minimice todas las ventanas abiertas) ? O uno de apagar?

Saludos, y muchas gracias.

---

### Post by NickCis on 2008-12-23
Solucione lo del AutoLogin y iniciar.
Instrucciones:
```
====== Autologins ======

Compiling an autologin script is an easy and effective way to cut the boot time on almost any machine. The downside is, of course, that it's neither practical nor appropriate if you need accounts for more than one person. So it might not be something you want to use.*

Autologins are usually managed with [[http://packages.ubuntu.com/feisty/gnome/gdm|GDM]] and the like. But on a machine without a display manager, it's better to [[Set up Feisty for speed:Start X automatically|start X automatically]] and either log in at the tty, or compile a script to log in for you. It's going to depend on the human of course, but getting from Grub to the desktop without logging in is going to be far faster without typing a name and password.

The autologin script is basically a one-liner that looks like this.

	int main() { execlp( "login", "login", "-f", "your_user_here", 0); }

Open a text file, copy that line into it, substitute the account name, save the file as autologin.c, then compile it. Of course, you'll need to install build-essential (or just gcc, really) for this step.

	gcc -o autologin autologin.c

You might get some warnings, which may or may not include these:

	autologin.c: In function ‘main’:
	autologin.c:1: warning: incompatible implicit declaration of built-in function ‘execlp’
	autologin.c:1:62: warning: no newline at end of file

Don't sweat those; as long as there are no error messages, it should be fine. Copy the resulting file to your /usr/local/sbin directory with 

	sudo cp autologin /usr/local/sbin

Now we can tell Feisty to look for it on boot. In the old days of pre-Edgy machines, the script was triggered in the inittab file. Edgy and Feisty use the Upstart system, and as a result, the autologin needs to be moved to /etc/event.d/tty1

	sudo nano -w /etc/event.d/tty1

At the end of the file you should see this line

	exec /sbin/getty 38400 tty1

Comment it out, and add this line below it.

	exec /sbin/getty -n -l /usr/local/sbin/autologin 38400 tty1

Save the file and exit. On your next reboot, you should be automatically logged in as the user you listed in the script.
```
Fuente: [http://ubuntuforums.org/showthread.php?t=546544#7](http://ubuntuforums.org/showthread.php?t=546544#7)

Si no tienen el compilador gcc, lo instalan con "sudo apt-get install gcc". 

Despues para que arranque la sesion: (en terminal)
```
sudo nano ~/.profile 
```
y agregamos al final
```
startx
```
Fuente: [http://ubuntuforums.org/showthread.php?p=4552480#3](http://ubuntuforums.org/showthread.php?p=4552480#3) (ahi dice que se haga esto en el archivo "~/.bash_profile" pero yo lo tuve que hacer en el "~/.profile", ya que el otro no existia)

Saludos

---

### Post by NickCis on 2008-12-23
> **NickCis said:**
> No, no es eso, es que estoy haciendo una instalacion minima (desde 0, instalando el ubuntu Command Line), con otro gestor de ventanas (Openbox) y no viene nada instalado, y cuando digo nada, es NADA, ni explorador, ni gestor de ventanas, ni login manager, ni paneles, ni escritorio. 
Lo que busco es hacer usable a una maquina vieja, y para eso instalo aplicaciones de bajos recursos y solo las que nececito.

- Probe instalando la wbar, el thunar y el xfdesktop, saben como hago para que las aplicaciones minizadas aparescan en el escritorio?.

- En la Wbar, se puede poner un reloj?, y un "Mostrar Escritorio" (que minimice todas las ventanas abiertas) ? O uno de apagar?

Saludos, y muchas gracias.
Nadie tiene idea de estas cosas?, por que la verdad es molesto tener que poner siempre "sudo shutdown -P 0" para apagar, no saber que ventanas tengo abiertas o no saber la hora...
Y saben como se puede poner la wbar en un "Always on top", por que cualqier ventana que abro me la tapa... :S

Saludos.

---

### Post by andy_91 on 2008-12-23
para colocar las ventanas minimizadas en el escritorio tenes que ejecutar xfce-setting-show backdrop o algo asi y en la segunda pestaña te da la opcion de que queres que se muestre en el escritorio (iconos, ventanas, nada)

pero en este momento no recuerdo si era 100% xfce-setting-show backdrop pero esta cerca de eso

---

### Post by NickCis on 2008-12-23
> **andy_91 said:**
> pero en este momento no recuerdo si era 100% xfce-setting-show backdrop pero esta cerca de eso
Era exactamente ese comando, muchas gracias.

Y para apagar, como puedo hacer?, estoy harto de tener que abrir la consola y poner "sudo shutdown -P 0". Hice un icono en la wbar que ejecuta "gksudo shutdown -P 0", pero siempre me pide la clave, como hago para hacer algo que apague la pc y no tenga que poner mi clave?.
Se puede poner un reloj en la wbar?, si no como puedo poner un reloj que siempre este por ensima de todo?.

------
La wbar puede estar en un "always on top"? EDIT: Solucionado
Editando el archivo ~/.config/openbox/rc.xml bajo la seccion de <applications>, le agregue esto:
```
<application name="wbar">
 <layer>above</layer>
</application>
```
Aunque con esto, me surgio el problema de que la transparencia de la wbar es falsa (copia el fondo cuando abre), entonces que un cacho de fondo colgado ocupando espacio.

- Nadie sabe de una barra de este tipo que tenga transparencia, o se auto esconda?
- O como puedo hacer que la wbar, ocupe todo ese espacio y no deje a las ventanas ponerse detras de ella?
-----

Saludos.

---

### Post by c4d0rn4 on 2008-12-23
fijate si la barra toma xcompmgr, si lo hace vas a tener trasnparencias reales.

---

### Post by andy_91 on 2008-12-23
para lo del apagado fijate  si en el xfce-setting-show backdrop no hay una opcion, para que cuando le das click con el boton secundario te salga un menu y ahi te deberia apareser la opcion salir (bueno asi es en xubuntu no se si esa opcion vendra solo con xfdesktop)

si el menu de xfce no lo tenes, instalete el xfce4-menueditor podes crearte un menu para cuando le das click con el boton secundario te salga. (lo que estoy seguro, que me parese que se puede es editar el menu de openbox con xfce4-menueditor)

bueno espero que eso te solucione el problema

---

### Post by NickCis on 2008-12-24
> **c4d0rn4 said:**
> fijate si la barra toma xcompmgr, si lo hace vas a tener trasnparencias reales.
Como si la barra toma xcompmgr?, esta barra no nececita ningun acelerador 3d. Por lo que tengo entendido no tiene transparencia real, sino, que copia el fondo cuando lo abre (cosa que es muy molesta).

Nadie conoce de una barra buena de bajos recursos de este estilo?.

Ahh, muchas de estas cosas me piden que las compile haciendo un:
make
sudo make install
Que tendria que instalar para poder instalar estas cosas?.

Saludos.

---

### Post by Hei Ku on 2008-12-24
te referis a que te da un error al poner make, o a conseguir un repositorio que las tenga armadas asi no tenes que compilar?

Si no compilaste nunca, instalate el build-essential

```

sudo apt-get install build-essential

```

---

### Post by Hei Ku on 2008-12-24
te referis a que te da un error al poner make, o a conseguir un repositorio que las tenga armadas asi no tenes que compilar?

Si no compilaste nunca, instalate el build-essential

```

sudo apt-get install build-essential

```

---

### Post by NickCis on 2008-12-24
Era que nunca habia compilado, muchas gracias.

Ahora, en openbox, hay alguna manera de hacer, que el espacio que ocupa la wbar (ej, toda la franja de 40 pixeles de abajo), no pueda ser ocupado por ninguna otra ventana?.
EDIT; Solucionado, en el archivo rc.xml habia algo que se llamaba margin, le puse los pixeles adecuados y andubo perfecto.

-------
El problema es que me qede sin reloj :S, alguna aplicacion que sea simplemente un reloj digital y consuma lo menos posible?

Ademas, pensando en todo de bajos recursos manejador de ventana, etc, me olvide del sonido :S, que tengo que instalar para que alla sonido (lo que busco que es emesene con su plugin sound emita sonido).

Saludos.

---

### Post by andy_91 on 2008-12-24
si no recuerdo mal esta el asclock es un reloj con calendario muy ligero

[IMG]http://web.cs.mun.ca/~gstarkes/wmaker/dockapps/shots/asclock.gif[/IMG]

*************EDIT*****************

[esta web]("http://web.cs.mun.ca/~gstarkes/wmaker/dockapps/time.html") tiene muchos relojes

---

### Post by NickCis on 2008-12-25
Gracias por el reloj, pero finalmente decidi instalar el pypanel y de paso veo las ventanas que tengo abiertas. (Tuve mucha pelea con el wmclockmon, no se por que el openbox no me lo ubicaba donde qeria y todo eso, pero bueno, no importa)

Ahora mi problema, vuelve a apagar y al sonido.
Para el sonido hice un "sudo apt-get install alsa", y sigo sin poder escuchar, no puedo ni abrir el alsamixer.
Como puedo solucionar esto?.

Y como puedo apagar la pc, sin recurrir al comnado shutdown, (que nececita derechos de root)?

Saludos.

---

### Post by andy_91 on 2008-12-25
para el apagado nesesitas el gnome-power-manager, lo que nose es que comando ejecuta al momento de darleapagar que te aparese el vcartel con las opciones (apagar, reiniciar, etc.)

fijate si alguien sabe , yo lo vi una vez cuando usaba USP pero no le preste atencion :P

---

### Post by andy_91 on 2008-12-25
[aca]("http://linexiando.blogspot.com/2008/07/openbox-en-ubuntu-804.html") hay cosas sobre alternativas bajos recursos por ahi te sirve alguno

---

### Post by NickCis on 2008-12-26
Encontre esto: [http://braianet.blogspot.com/2008/01/apagar-el-sistema-sin-ser-root.html](http://braianet.blogspot.com/2008/01/apagar-el-sistema-sin-ser-root.html)
Me parece que es mas facil que andar instalando el gnome-power-manager.

Gracias por la ayuda igual.

Ahora, si uso el gestor de aplicaciones xfe, como hago para montar los pendrives (memorias usb)?.

Saludos.

---

### Post by jjgomera on 2008-12-26
> **NickCis said:**
> 
Ahora mi problema, vuelve a apagar y al sonido.
Para el sonido hice un "sudo apt-get install alsa", y sigo sin poder escuchar, no puedo ni abrir el alsamixer.
Como puedo solucionar esto?.

sobre barras te recomiendo tint2, que es especifica para openbox, o visibility que es más minimalista, el reloj yo lo tengo puesto con conky, y el systray donde ponen el icono programas tipo emesene, amule, lo hace trayer, todo eso lo puede hacer por ejemplo pypanel o fbpanel.
Sobre apagar, no recuerdo si aparece por defecto en el menú de openbox, yo juraría que sí, si no lo añades usando obmenu ¿te resulta molesto poner la contraseña cada vez que quieres apagar el equipo? a mi me parece una medida apropiada para evitar errores, pero si no te gusta puedes editar el archivo sudoers para permitir a tu usuario apagar el equipo, abre el archivo /etc/sudoers como root y añade al final una linea como:
```
usuario   ALL = (ALL) NOPASSWD: /sbin/halt, /sbin/reboot
```
poniendo tu nombre de usuario

---

### Post by andy_91 on 2008-12-26
> **NickCis said:**
> Encontre esto: [http://braianet.blogspot.com/2008/01/apagar-el-sistema-sin-ser-root.html](http://braianet.blogspot.com/2008/01/apagar-el-sistema-sin-ser-root.html)
Me parece que es mas facil que andar instalando el gnome-power-manager.

Gracias por la ayuda igual.

Ahora, si uso el gestor de aplicaciones xfe, como hago para montar los pendrives (memorias usb)?.

Saludos.

yo diria que uses pcman que trae gestion del escritorio y te muestra los pendrives

---

### Post by NickCis on 2008-12-30
Estube probando Pcmanfm, y el problema que tengo es que para entrar en los pendrives, (que los auto monte, verlos, y modificar sus archivos) tengo que abrirlo con Root, si no tira carteles de error en blanco :S.

Es problema del Fm, o de mi configuracion?, como puedo solucionarlo? o que FM me recomiendan que traiga una auto deteccion y montado de pendrives?.

Saludos.

---

### Post by andy_91 on 2008-12-31
es un problema de configuracion, seguramente tu usuario no tiene los permisos para montar los pendrives

fijate si alguien te da una mano con eso

---

### Post by NickCis on 2008-12-31
Como configuro para darle los permisos necesarios?, y ademas, cuando meto un Cd, tampoco me lo auto monta, como puedo arreglar eso?.

Saludos.

---

### Post by Hei Ku on 2009-01-01
Postea una copia de tu /etc/fstab
Y el automount es tarea del desktop manager. Parece que el que usas no lo tiene, o al menos no predeterminado.

---

### Post by NickCis on 2009-03-23
Bueno, revivo Post para contar experiencias y para prengutar mas. Me parece que para el que busque, encontrar este post con mucha info va a ser mejor que pequeños post con pocas respuestas...

Termine haciendo una instalacion en limpio de ubuntu 8.04 Alternate y Minima.
Use Lxde como escritorio, completito, terminal, todo,,,
Repo: [https://launchpad.net/~lxde/+archive/ppa](https://launchpad.net/~lxde/+archive/ppa)
Para musica Lxmusic (que no taba en los repositorios), para eso hay que agregar los repos de xmms2 ( [https://launchpad.net/~bdrung/+archive/ppa](https://launchpad.net/~bdrung/+archive/ppa) ) y descargar el deb de ak: [http://twemu.no-ip.org/apt/lxmusic/](http://twemu.no-ip.org/apt/lxmusic/)
Visor de Pdf: Xpdf (dsd repos de ubuntu).
Abyword, para textos, y Pttviewer para powerpoint.
Webs con midori.
Msn con Emesene.

Bue ahora las preguntas: 
* nececito imprimir, que es lo que nececito?, como podria tener un icono con la cola de impresion en el systray (como en GNOME)?

* Algun programa para configurar la red graficamente?, el lxnm de lxde, no lo entiendo muy bien, cuando lo ejecuto por terminal me sale esto:
```
oldpc@oldpc:~$ lxnm

** ERROR **: Bind on socket failed: Address already in use

aborting...
oldpc@oldpc:~$ 

```

Saludos.

---

### Post by pablo.s on 2009-03-23
> **NickCis said:**
> 

Bue ahora las preguntas: 
* nececito imprimir, que es lo que nececito?, como podria tener un icono con la cola de impresion en el systray (como en GNOME)?

* Algun programa para configurar la red graficamente?

Bueno loco, me satisface mucho que hayas logrado el objetivo que querías!

Para imprimir necesitas el servidor CUPS. Instalate todo lo que aparezca como 
CUPS en los repositorios (un poco exagerado lo mio). Tambien depende de la
impresora que uses, puede ser que también haga falta HPLIP, gutenprint,
foomatic, dale masa que si parece mucho después te saca de problemas.

Para configurar la red graficamente tenés pyneighborhood, gsambad, o sino
todo a manopla que no hace daño.

Saludos.

---

### Post by NickCis on 2009-03-23
Ok, lo de la impresera bueno, que hago un "sudo apt-get install cups*"?, la impresora es una Hp Laserjet 4l. Despues como configuro la impresora, osea, lo tengo que hacer por terminal, no?, cuales son los comandos que tendria que usar?. Y despues, para ver la cola de impresion, nececito el applet que se inicia en Gnome?, el "system-config-printer-applet", basta con instalarlo desde los repos de ubuntu?.

Con lo de red, se que se usa el comando ifconfig, pero ahi me quede, como puedo hacer para configurar que sea por dhcp, para configurar una ip statica, una puerta de enlace y los Dns?.

Saludos.

---

### Post by pablo.s on 2009-03-23
> **NickCis said:**
> Ok, lo de la impresera bueno, que hago un "sudo apt-get install cups*"?, la impresora es una Hp Laserjet 4l. Despues como configuro la impresora, osea, lo tengo que hacer por terminal, no?, cuales son los comandos que tendria que usar?. Y despues, para ver la cola de impresion, nececito el applet que se inicia en Gnome?, el "system-config-printer-applet", basta con instalarlo desde los repos de ubuntu?.

Para manejar CUPS, podés hacerlo desde la interfaz web, [aca]("http://draxus.org/weblog/2005/11/06/habilitar-la-interfaz-web-de-cups-en-ubuntu/") dice como se hace.
Desde la configuración hasta la cola de impresión, todo lo podés ver en esta
interfaz. Yo lo usaba asi hace unos seis o siete años ( o mas tambien?)


> **NickCis said:**
> Con lo de red, se que se usa el comando ifconfig, pero ahi me quede, como puedo hacer para configurar que sea por dhcp, para configurar una ip statica, una puerta de enlace y los Dns?.

Saludos.

Ah, yo te habia entendido otra cosa. Instala NetworkManager y ahi le pones los
datos.

---

### Post by NickCis on 2009-03-24
Ok, lo que no entendi son los paquetes que tengo que instalar, para el CUPS.
Solo con hacer "sudo apt-get install cups",y ya esta?, (carezco de cualquier entorno grafico para instalar paquetes, nunca tuve ganas de instalarlo y el modo consola funciona espectacular).

Saludos, y muchas gracias !!

Edit: estaba buscando un Login Manager, pero nececitaba uno que me muestre el nombre de todos los usuarios. El unico que existe de ese tipo es GDM?, como lo configuro para que sea asi y no de la forma normal.

Ej de lo que qiero, algo asi: [http://files.opensuse.org/opensuse/en/a/a6/Os103-gdm-userlist.png](http://files.opensuse.org/opensuse/en/a/a6/Os103-gdm-userlist.png) o asi: [http://linuxfud.files.wordpress.com/2006/11/gdm-login.png](http://linuxfud.files.wordpress.com/2006/11/gdm-login.png)

Con xdm no puedo hacer esto, no?. Lo que estoy buscando es que tenga Face browser, esto en gdm depende del tema, no?.

---

### Post by pablo.s on 2009-03-24
Ah, por un momento pensé que habias instalado LXDE. ¿No tenés Synaptic?
Probá con aptitude. O tampoco lo tenés? Cuidado con los extremos, que se
tocan eh...

---

### Post by NickCis on 2009-03-24
> **pablo.s said:**
> Ah, por un momento pensé que habias instalado LXDE. ¿No tenés Synaptic?
Probá con aptitude. O tampoco lo tenés? Cuidado con los extremos, que se
tocan eh...

Si tengo instalado LXDE, pero no nececito tener un gestor de paquetes grafico para hacerlo. Trabajo por consola con Aptitude y apt-get (creo qe son lo mismo).

Volviendo a lo de CUPS, para instalarlo "sudo apt-get install cups"?, esto me instala tambien los drivers o los tengo que instalar a mano?.

Login managers, cuales me permiten tener un face browser, solo el GDM?, esto depende del theme?.

Despues reproductores de musica: Estoy entre Audacious y Bmpx, que me dicen?.
Video: Gxine, Vlc o Mplayer?
Como instalo los codecs multimedia para video y sonido, para estos reproductores, y la configuracion del firefox (para ver peliculas y sonidos) depende del reproductor?. Tengo que instalar algo especifico?.
O solo basta con un "suo apt-get install ubuntu-restricted-extras".
Grabado de Cds: Brasero o xfburn?.


Saludos y gracias :P

Edit: Solucione lo de los pluigns de video, son mozilla-plugin-vlc (para vlc) y mozilla-mplayer (para mplayer), igual me parece que me qedo con el Vlc. Despues tiene alguna idea del pluign para el Cups?.

---

### Post by pablo.s on 2009-03-24
> **NickCis said:**
> Volviendo a lo de CUPS, para instalarlo "sudo apt-get install cups"?, esto me instala tambien los drivers o los tengo que instalar a mano?.

sudo apt-get install cups hplip foomatic-filters foomatic-db hplip-gui


> **NickCis said:**
> Login managers, cuales me permiten tener un face browser, solo el GDM?, esto depende del theme?.

GDM y KDM tienen face browser. Depende del theme, exacto (en KDE no estoy tan seguro porque no lo uso, eh)

> **NickCis said:**
> Despues reproductores de musica: Estoy entre Audacious y Bmpx, que me dicen?.
Video: Gxine, Vlc o Mplayer?
Como instalo los codecs multimedia para video y sonido, para estos reproductores, y la configuracion del firefox (para ver peliculas y sonidos) depende del reproductor?. Tengo que instalar algo especifico?.
O solo basta con un "suo apt-get install ubuntu-restricted-extras".
Grabado de Cds: Brasero o xfburn?.

BMPx aunque con VLC podés reproducir musica también. Si lo que buscás es ahorrar espacio es lo que más conviene. Para los codecs multimedia la receta mágica es:

sudo apt-get install gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-ffmpeg gstreamer0.10-pitfdll

---

### Post by jjgomera on 2009-03-24
> **NickCis said:**
> Ok, lo que no entendi son los paquetes que tengo que instalar, para el CUPS.
Solo con hacer "sudo apt-get install cups",y ya esta?, (carezco de cualquier entorno grafico para instalar paquetes, nunca tuve ganas de instalarlo y el modo consola funciona espectacular)

sudo tasksel

y marcas la casilla de servidor de impresoras

Para el gestor de redes: wicd a mi me parece muy superior al propio de gnome, y es muy ligerito

Gestor de sesiones, si quieres una cosa espartana usa wdm o qingy

Para escuchar musica, mpd con algún gui ligero como sonata, si ya quieres manejar librerías gmusicbrowser

---

### Post by NickCis on 2009-03-26
Una pregunta, que nececito instalar (plugins y demas) para reproducir peliculas, videos, sonidos, juegos flash, java, e imprimir con el firefox?.

Por si esta info sirve: pienso instalar vlc como reproductor de video y bmpx como audio.

Saludos.

---

### Post by NickCis on 2009-03-27
> **NickCis said:**
> Una pregunta, que nececito instalar (plugins y demas) para reproducir peliculas, videos, sonidos, juegos flash, java, e imprimir con el firefox?.

Por si esta info sirve: pienso instalar vlc como reproductor de video y bmpx como audio.

Saludos.

Alguna idea?

---

### Post by pablo.s on 2009-03-27
> **pablo.s said:**
> Para los codecs multimedia la receta mágica es:

sudo apt-get install gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-ffmpeg gstreamer0.10-pitfdll

No lees mis posts muchacho...

---

### Post by NickCis on 2009-03-27
Ok, perdona, pense que como no figuraba nada que diga Java, faltaban plugins...

Y para imprimir?, nececito algo mas? o alguno de esos me da la posibilidad para imprimri? (o sera que no tengo qe instalar nada , el imprimir viene de fabrica con el firefox? xD..)

Saludos...

---

### Post by pablo.s on 2009-03-27
Para Java:

sudo apt-get install sun-java6-bin

Para Flaaaaaaa

sudo apt-get install flashplugin-nonfree

No comprendo lo de imprimir con Firefox. Si instalaste CUPS y está
configurado, sale rodando.

Saludos loco!

---

