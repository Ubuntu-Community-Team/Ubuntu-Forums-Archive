---
title: "[SOLVED] Pantalla negra en KDE"
date: 2009-08-15
forum: Software
---

### Post by FB91 on 2009-08-15
ayer instalé KDE en mi ubuntu, encontré en este foro que una manera de hacerlo era por medio del 
[FONT=monospace]
[/FONT]```
sudo aptitude install kubuntu-desktop
```

la cuestión es que me andubo 10 puntos pero cuando quise usar un widgets que se llamaba "Magnification" (es como una lupa para hacer zoom, no recuerdo bien su nombre) se me puso la pantalla totalmente negra. Ni bien apreté en esa lupa se puso negra la pantalla :S

Entonces reinicié... pero la pantalla negra seguía ahí.

Hay algunos programas, bah en realidad uno solo (el emesene) que lo había configurado para que inicie solo ni bien enciendo el equipo, ¡y sigue funcionando! Nosé si me entienden... es medio "raro" porque todo el fondo es negro pero la ventana del emesene sigue lo más bien, como si fuese un problema del escritorio!

PD: intenté haciendo  sudo aptitude remove kubuntu-desktop  y luego   sudo aptitude install kubuntu-desktop  pero sigue igualito

---

### Post by Hei Ku on 2009-08-15
Podés poner en una terminal:

rm .kde/share/config/plasmarc

Eso va a borrar la configuración de plasma y debería solucionarlo.
Tendrías que hacerlo desde afuera de KDE, antes de iniciar.

---

### Post by FB91 on 2009-08-15
Probé ese comando y ahora me funciona, muchas gracias!

El único problema es que cada tanto me pasa lo mismo y nose porqué, hace un ratito estaba usando el firefox y de golpe todo lo demás se volvió negro :S las barras de menú y el escritorio... reinicié y ya estaba todo funcionando bien.

Me preocupa que me pase lo mismo cuando esté haciendo algún trabajo importante, hay alguna manera de saber qué es lo que entra en "conflicto"? 

gracias :D

---

### Post by Hei Ku on 2009-08-15
Probá apretando Alt+Shift+F12 para desactivar los efectos.
Por otro lado, no será algo asi como el protector de pantalla que se activa solo o similar, no?

---

### Post by FB91 on 2009-08-15
no, el protector de pantalla no es seguro porque la aplicación que tenga abierta la sigo viendo lo más bien... el "fondo" es decir, la barra inferior y el fondo de pantalla desaparecen dejando todo negro. Y una vez que pasa eso los atajos de teclado tampoco funcionan...

Otra cosa.... esto no se podrá solucionar instalando kubuntu arriba de ubuntu? es decir, manteniendo mis archivos pero instalando el kubuntu en la partición "/" manteniendo el home...

---

### Post by Hei Ku on 2009-08-15
Por alguna razon me parece que el plasma se te muere. Si esperas un poco no vuelve a aparecer?

---

### Post by FB91 on 2009-08-15
la deje unos 15 minutos y no vuelve...

Ahora me anda peor (y no toque nada!! :S) cuando incio la sesión y aparece esa animación que "aparecen" unos íconos (un disco rigido, unas herramientas, el mundo azul y el logo de kde) se me tilda ahí... queda la pantalla con todos esos iconos ya cargada y no pasa nada. Probé clickeando en cualquier parte de la pantalla y volvió la pantalla negra

---

### Post by guillermolisi on 2009-08-15
Si no recuerdo mal, la version de KDE que bajas de los repos actuales es la 4.1 o 4.2.

Mi recomendacion es agregar los ppa de la 4.3 y actualizar. Hay muchisimos bug fixes y alta probabilidad que este tema supuestamente de Plasma se solucione.

---

### Post by FB91 on 2009-08-15
y como agrego eso?

( es la primera vez que uso KDE y estoy en una nube :D )

---

### Post by guillermolisi on 2009-08-15
Fijate si esto te ayuda (si no te llevas bien con el Ingles avisa)
> Users of our stable 9.04 release can install it from the Kubuntu Backports PPA.

deb [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu) jaunty main

It is strongly recommended that you verify the integrity of these packages by installing the archive's GPG key. You may do this by following the instructions on [this page]("http://www.kubuntu.org/faq/PPA-keys").

This archive includes a new network manager application, run "knetworkmanager" (the Plasmoid is just a dummy currently).

Packages for Jaunty are not officially supported. KDE 4.3 will be part of Kubuntu Karmic 9.10 to be officially released this October.

---

### Post by staar on 2009-08-15
muchas veces los problemas con plasma son debidos a los plasmoides que esten activados, hay varios que andan mal y que crashean plasma de vez en cuando (por ejemplo el de networkmanager), cuales tenés activados ahora?

también, cuando se te muera plasma, podés abrirlo de nuevo con Alt + F2 *plasma* (o plasma-desktop desde kde 4.3)

si seguis sin poder entrar, volvé a hacer lo que te dijo Hei Ku y fijate...

saludos

---

### Post by FB91 on 2009-08-15
agregué los repositorios pero me dice q no tengo suficiente espacio en "/"

Aparte hay muchas cosas que no me funcionan como el synaptic, me da este error:

> No se pudo ejecutar /usr/sbin/synaptic como usuario root.

 No es posible copiar el archivo Xautorization del usuario.

prefiero hacer una instalación limpia de Kubuntu. Tendría que hacerla arriba de mi actual particion "/" ? y eso no borraría mis archivos de /home? eso sí, por lo poco que se mis programas se borrarían no?

(¿tendría que abrir un nuevo post?)

---

### Post by guillermolisi on 2009-08-15
> **FB91 said:**
> agregué los repositorios pero me dice q no tengo suficiente espacio en "/"

Aparte hay muchas cosas que no me funcionan como el synaptic, me da este error:



prefiero hacer una instalación limpia de Kubuntu. Tendría que hacerla arriba de mi actual particion "/" ? y eso no borraría mis archivos de /home? eso sí, por lo poco que se mis programas se borrarían no?

(¿tendría que abrir un nuevo post?)
Si, si el tema de la pantalla negra en KDE lo finalizas aqui, abri otro thread aunque en algun thread se hablo sobre el tema de reinstalacion y no hace mucho.

---

### Post by Hei Ku on 2009-08-15
Y en KDE no se usa Synaptic, se usa KPackageKit.

---

### Post by FB91 on 2009-08-15
¿hay muchas probabilidades de que el problema de la pantalla negra continúe pasando si hago una instalación limpia de kubuntu?

¿es recomendable que actualice a KDE4.3 ni bien tenga el Kubuntu?

---

### Post by guillermolisi on 2009-08-15
> **FB91 said:**
> ¿hay muchas probabilidades de que el problema de la pantalla negra continúe pasando si hago una instalación limpia de kubuntu?

¿es recomendable que actualice a KDE4.3 ni bien tenga el Kubuntu?
Nunca se sabe pero no tener espacio suficiente en disco podria ser una causa (remota, pero posible).

Si haces una fresh installation mi recomendacion es usar KDE 4.3, es como un antes y un despues.

---

### Post by oktubrer on 2009-08-15
> **guillermolisi said:**
> Nunca se sabe pero no tener espacio suficiente en disco podria ser una causa (remota, pero posible).

Si haces una fresh installation mi recomendacion es usar KDE 4.3, es como un antes y un despues.

A mi me pasaba lo mismo, se moría el plasma mientras cargaba al iniciar, y no lo podía levantar de ninguna forma.  Actualice a 4.3 como te comentaron antes y se resolvió.

---

### Post by FB91 on 2009-08-15
al final voy a hacer una "fresh installation" (que bien que suena :P) una última consulta...

mis particiones están dadas de esta manera:

/
/home
/media/disk (una partición en la que tenía windows pero al final la formateee para usar en linux)
linux-swap

ahora... cuando instale Kubuntu, en la parte de editar las particiones como las tengo que dejar?

/  -> Formatear y usar
/home  -> usar
/media/disk  -> usar
linux-swap -> usar 

¿Tienen que quedar así? quiero estar bien seguro antes de proceder, no sea cosa que me quede sin nada :S

---

### Post by guillermolisi on 2009-08-15
> **FB91 said:**
> al final voy a hacer una "fresh installation" (que bien que suena :P) una última consulta...

mis particiones están dadas de esta manera:

/
/home
/media/disk (una partición en la que tenía windows pero al final la formateee para usar en linux)
linux-swap

ahora... cuando instale Kubuntu, en la parte de editar las particiones como las tengo que dejar?

/  -> Formatear y usar
/home  -> usar
/media/disk  -> usar
linux-swap -> usar 

¿Tienen que quedar así? quiero estar bien seguro antes de proceder, no sea cosa que me quede sin nada :S
Correcto. Solo se regenera la particion que aloja /

Luego, deberia montarte el resto tal como lo tenes y con el contenido que tenes.

---

### Post by harry2006 on 2009-08-15
i request everyone to post threads in "English" to make it usable for a wider audience...else we're refraning people to make use of the solution/help to an existing problem already fixed/posed by someone... :-)

---

### Post by josecuervo86 on 2009-08-15
> **harry2006 said:**
> i request everyone to post threads in "English" to make it usable for a wider audience...else we're refraning people to make use of the solution/help to an existing problem already fixed/posed by someone... :-)

This is the Argentine Forum. We speak in spanish, not in english

---

### Post by guillermolisi on 2009-08-15
> **harry2006 said:**
> i request everyone to post threads in "English" to make it usable for a wider audience...else we're refraning people to make use of the solution/help to an existing problem already fixed/posed by someone... :-)
Harry

I've told you in another thread: This is the Argentina LoCo Team Forum. Spanish is our language.

Some of us can speak and write English (as you can see), but is not a "common, massive ability" among LatAm native members.

Sorry, we couldn't satisfy your request.

---

### Post by FB91 on 2009-08-15
La instalación fué un éxito :D

Lo que me falta solucionar es la configuración para tener internet... pero voy a abrir otro post sino este queda hecho una ensalada :P

Cuando cree el otro post, edito y les paso el link!

Gracias!

EDIT: aquí está el post » [http://ubuntuforums.org/showthread.php?t=1241214](http://ubuntuforums.org/showthread.php?t=1241214)

---

