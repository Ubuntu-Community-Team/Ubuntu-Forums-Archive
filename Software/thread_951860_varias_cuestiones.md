---
title: "varias cuestiones"
date: 2008-10-18
forum: Software
---

### Post by tsueseres on 2008-10-18
themes
hola, porfin encontre un tema que me gusta pero hay un prblema el cual es que ciertos iconos no me gustan y intente cambiarlos pero el tema no trae ninguna carpeta de iconos dice algo de que el tema es metacy no se si eso tenga algo que ver

cairo-dock
tengo un problema quice agregar una ruta para abrir una carpeta pero lo que ice fue poener la ruta del icono para mostrar, le di aceptar y luego aparecio un icono como separador y ya no puedo kitarlo ni cambiar opciones directamente, alguien tiene idea de como kitarlo.

hibernar
tengo un problema cuando intento acer k la maquina hiberne sale una pantalla negra con algo de que ha fallado y decia algo de 11 tengo ubuntu 8.04

contraseña
cuando intento instalar algo me pide la contraseña y tmb cuando voy ha abrir algo, no hay añguna manera de que no me este pidiendo la contraseña

---

### Post by valucha on 2008-10-18
> **tsueseres said:**
> themes
hola, porfin encontre un tema que me gusta pero hay un prblema el cual es que ciertos iconos no me gustan y intente cambiarlos pero el tema no trae ninguna carpeta de iconos dice algo de que el tema es metacy no se si eso tenga algo que ver

cairo-dock
tengo un problema quice agregar una ruta para abrir una carpeta pero lo que ice fue poener la ruta del icono para mostrar, le di aceptar y luego aparecio un icono como separador y ya no puedo kitarlo ni cambiar opciones directamente, alguien tiene idea de como kitarlo.

hibernar
tengo un problema cuando intento acer k la maquina hiberne sale una pantalla negra con algo de que ha fallado y decia algo de 11 tengo ubuntu 8.04

contraseña
cuando intento instalar algo me pide la contraseña y tmb cuando voy ha abrir algo, no hay añguna manera de que no me este pidiendo la contraseña

Themes:

Tenés varias cosas a cambiar en cuanto a la estética: 1. las ventanas en sí esos se llaman gtk themes. 2. los bordes de la ventana, esos se llaman metacity. 3. los iconos.
Los tres vienen comprimidos de la misma forma por lo que por eso no podés darte cuental. Pero lo que debés hacer es ir a págnas como [www.gnome-look.org](www.gnome-look.org) y elegir uno de cada cosa, quiero decir, un gtk theme, un metacity theme y un pack de iconos. 
Probablemente no tecambian los iconos porque el theme que te bajaste es solo el metacity, es decir que es solo el borde de la ventana Probablemente la persona que lo puso en la página había cambiado los iconos y el resto con otros paquetes, fijate si en algun lugar dice cuales son y bajalos.


cairo dock: no sé no lo uso.


Hibernar: probablemente el problema que tengas sea con el X11, pero es necesario que digas más al respecto de tu problema, ya que no todos los problemas por no poder hibernar son del mismo tipo y así nomás no te puedo decir nada... tratá de anotar lo que te dice, o aunquesea decinos mñás acerca de tu máquina (marca de las cosas, modelos, placa de video, etc)


contraseña: el tema de la contraseña pasa cuando ejecutás algo con sudo en la consola. eso es porque vos entrás a Ubuntu como un "invitado" y no como un "administrador" como es en Windows. No hay formas, o si las hay no son recomendables, de entrar como "administrador" en Ubuntu, igualmente decinos en qué casos te molesta más que te pida la contraseña, ya que por ejemplo para ver tus archivos y abrir todos tus programas no deberia pedirtela. Generalmente la pide para muchas de las opciones que están en sistema->administración, ya que estás cambiando cosas críticas que te pueden arruinar la máquina y esas cosas digamos que las arreglás una vez y después ni las tocás... 
Decinos si hay otro caso que te pida la contraseña y te joda.


Espero que te sirva, Saludos

---

### Post by tsueseres on 2008-10-18
> **valucha said:**
> Themes:

Tenés varias cosas a cambiar en cuanto a la estética: 1. las ventanas en sí esos se llaman gtk themes. 2. los bordes de la ventana, esos se llaman metacity. 3. los iconos.
Los tres vienen comprimidos de la misma forma por lo que por eso no podés darte cuental. Pero lo que debés hacer es ir a págnas como [www.gnome-look.org](www.gnome-look.org) y elegir uno de cada cosa, quiero decir, un gtk theme, un metacity theme y un pack de iconos. 
Probablemente no tecambian los iconos porque el theme que te bajaste es solo el metacity, es decir que es solo el borde de la ventana Probablemente la persona que lo puso en la página había cambiado los iconos y el resto con otros paquetes, fijate si en algun lugar dice cuales son y bajalos.


cairo dock: no sé no lo uso.


Hibernar: probablemente el problema que tengas sea con el X11, pero es necesario que digas más al respecto de tu problema, ya que no todos los problemas por no poder hibernar son del mismo tipo y así nomás no te puedo decir nada... tratá de anotar lo que te dice, o aunquesea decinos mñás acerca de tu máquina (marca de las cosas, modelos, placa de video, etc)


contraseña: el tema de la contraseña pasa cuando ejecutás algo con sudo en la consola. eso es porque vos entrás a Ubuntu como un "invitado" y no como un "administrador" como es en Windows. No hay formas, o si las hay no son recomendables, de entrar como "administrador" en Ubuntu, igualmente decinos en qué casos te molesta más que te pida la contraseña, ya que por ejemplo para ver tus archivos y abrir todos tus programas no deberia pedirtela. Generalmente la pide para muchas de las opciones que están en sistema->administración, ya que estás cambiando cosas críticas que te pueden arruinar la máquina y esas cosas digamos que las arreglás una vez y después ni las tocás... 
Decinos si hay otro caso que te pida la contraseña y te joda.


Espero que te sirva, Saludos

gracias por la informacion.

sobre la contraseña me he fijado en internet (youtube) en los tutoriales que van a instalar algo en la terminal (creo que con sudo) y a ellos no les pide la contraseña, y no parece que esten en modo administrador, no se si solo se puede evitar pedir la contraseña para siertas partes

---

### Post by tsueseres on 2008-10-19
hibernar
el problema completo es:
1899.684778   BUG:Softlockup-CPU #1 stuck for 11s! ntos_wp:4260


contraseña
sobre la contraseña me he fijado en internet (youtube) en los tutoriales que van a instalar algo en la terminal (creo que con sudo) y a ellos no les pide la contraseña, y no parece que esten en modo administrador, no se si solo se puede evitar pedir la contraseña para siertas partes

---

### Post by c4d0rn4 on 2008-10-19
> **tsueseres said:**
> 
contraseña
cuando intento instalar algo me pide la contraseña y tmb cuando voy ha abrir algo, no hay añguna manera de que no me este pidiendo la contraseña

si te pide contraseña para abrir archivos es que no son tuyos los archivos sino del root o que se yo.

Probá desde root cambiar las propiedad de la carpeta con los archivos y darle privilegios a tu usuario.

Tal vez si le pones como dueño a tu usuario a todo el sistema no tengas más dramas con la contraseña, pero no creo que sea buena idea

---

### Post by chalito on 2008-10-20
> **c4d0rn4 said:**
> si te pide contraseña para abrir archivos es que no son tuyos los archivos sino del root o que se yo.

Probá desde root cambiar las propiedad de la carpeta con los archivos y darle privilegios a tu usuario.

Tal vez si le pones como dueño a tu usuario a todo el sistema no tengas más dramas con la contraseña, pero no creo que sea buena idea

de hecho seria una -pesima- idea :)

sudo te pide la contraseña por cuestion de seguridad. En Ubuntu, para realizar tareas administrativas (instalar programas nuevos, cambiar algun setting de sistema o preferencias de funcionamiento), necesitas autentificarte por medio de tu contraseña. Esto permite entre otras cosas mantener los permisos en el sistema separados entre usuarios comunes y administrador, cosa que por ejemplo hace que ubuntu (y GNU/Linux en gral) sea menos vulnerable a troyanos, virus y demás, y menos propenso a que metiendo la pata uno haga desastres en el sistema.

Habiendo dicho esto, si queres poder hacer sudo en la terminal sin poner el password, podes hacerlo editando el archivo /etc/sudoers, pero no te lo recomiendo. Poner la clave cada tanto es una de esas cosas que son un poquito molestas pero conviene hacerlas.

---

