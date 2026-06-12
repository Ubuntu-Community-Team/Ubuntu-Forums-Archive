---
title: "Instalarme otra distriubucion, compartiendo el /home"
date: 2008-05-20
forum: Software
---

### Post by pol666 on 2008-05-20
Hola, les comento que me decidi por achicar mi particion donde se encuentra el sistema ubuntu, y dejar 4gb para instalarme una nueva distro.

Estoy pensando en Mandriva o fedora no se bien..

Lo que trato de advertirme es lo siguiente:
Tengo pensado que esta distribucion comparta el mismo /home que ubuntu (Se encuentra en una particion separada)... A su vez instalarle KDE4.

Mi duda es si afecta algo que 2 distribuciones distintas con Escritorios distintos compartan la misma /home.

Si yo instalo programas en ubuntu, me van a aparecer en Mi otra distribucion?
Las carpetas con los PERFILES de usuario, son las mismas para ambos SO, esto me traera problemas?
Si uso dos nombres distintos para cada usuario corrio riesgos igualmente?



A y punto aparte:

Estoy buscando un distriubucion BIEN distinta a Ubuntu, la cual le voy a poner KDE (4 obviamente)...Osea para tener el polo opuesto..Estuve pensando en Fedora pero tambien pienso en Mandriva que parece que es mejor... Digan cual les gusta mas y por que

---

### Post by tzulberti on 2008-05-20
Talvvez tengas problemas con los archivos de configuracion de los programas. El gnome y kde 3.X usan siempre la misma carpeta de configuracion, asique si tenes dos versiones cuyos archivos de configuracion son distintos entonces algo no te va a funcionar.


Sobre distribuciones distintas da un poco mas de detalles de lo que estas buscando:
-> Si estas buscando aprender cosas de linux entonces Archlinux o SlackWare. Algun bsd?
-> Si queres probrar otro sistema de paquetes entonces ahi si tenes para elegir varias

Tenes para todos los gustos. Una buena pagina que junta casi todas las distros y que se mantiene bastante actualizada para esto es: [www.distrowatch.org](www.distrowatch.org) Te recomiendo buscar ahi una distro (en la busqueda avanzada tenes varios criterios por los cuales buscar).

Consejo personal: si tenes una buena maquina te recomiendo usar un virtualizado hasta aprenderte los "trucos" de la distro que realmente queres probar

---

### Post by Hei Ku on 2008-05-20
La recomendacion es que no compartas el home del usuario. Supongo que con usuarios distintos no habria problemas, pero con el mismo vas a tener conflicto de configuracion entre las distintas distribuiciones. Y si queres KDE4, te recomiendo OpenSuse. Es la que esta mas integrada a KDE. Mandriva siempre fue KDE, pero no tiene tanta gente metida adentro como OpenSuse, y Fedora le dio bola a KDE recien en el ultimo tiempo.

---

### Post by sergiom99 on 2008-05-20
yo uso servidores fedora (desde que era fedora core) y nunca tuve problemas. lo mismo con CentOs.
Pero las desktop de fedora estan buenas con KDE, con gnome no me gustaron. 
Lo que tiene muy bueno Fedora es el instalador, que ya de movida elegis un monton de cosas que queres instalar, a diferencia de _ubuntu que instala por defecto y despues agregas.

---

### Post by valucha on 2008-05-20
[COLOR="DarkOrchid"]Yo digo que instales Gentoo[/COLOR]

---

### Post by guisheca on 2008-05-21
Yo tengo ubuntu y fedora, y comparte la carpeta home, pero no el usuario. Yo te recomendaría que hagas lo mismo y la configuración que necesites la traes del otro user y listo.
Saludos.

---

### Post by faktorqm on 2008-05-21
> **valucha said:**
> [COLOR="DarkOrchid"]Yo digo que instales Gentoo[/COLOR]

Gentoo no está mal, el problema que tiene es que como es un producto derivado de los mas "puristas" de gnu/linux, compilan absolutamente todo. Una instalacion capaz te lleva 20 horas, y el rendimiento (esta bastante probado) no pasa del 5 o el 7% con respecto a instalaciones precompiladas.
Aparte mal o bien todos tienen el mismo conjunto de instrucciones, mmx, 3d-now, sse 1, 2 y 3 asi que por eso no existe diferencia tangible.

Fedora es facil por que es derivado del Red Hat, mi primer gnu/linux, que era "facil", igual para servidores no se que onda, pero el Red Hat 9.0 R3 no deja de ser el mejor (para mi), dependiendo de lo que quieras hacer por supuesto. Salu2!

---

### Post by vk-cdg on 2008-05-21
No tengo mucho tiempo en Linux como para decir que puede llegar a pasar si compartís el /home. Me parece que si compartís el /home sin usar el mismo usuario no deberías tener problemas. Me baso para decir esto en que en mi /home no hay ningun archivo suelto, todo está dentro de la carpeta de mi usuario, por lo que si otra distro usa el mismo /home, pero otro usuario, no creo que pase nada. Backup por las dudas.

En cuanto a las distros, me parece que depende de que es lo que quieras hacer. Si es un SO para desktop (lease usuario final) yo probaría Mandriva. En mi caso, cuando tuve el problema con la sintonizadora de TV, lo probé como liveCD y detectó todo, hasta la sintonizadora, cosa que me llamó mucho la atención. 
Fedora también tiene su trayectoria, pero no me he asomado lo suficiente como para decir algo.

---

### Post by pol666 on 2008-05-21
La verdad es que tengo ganas de probar una distro que me haga aprender pero tampoco un Gentoo o Un BSD.

Es muy probable que me tire a un Slackware 12 si es por eso, y a un Fedora si es para usar...

Primero antes que nada voy a explorar mas KDE por que nunca me gusto pero para ser sincero nunca lo use muy a fondo.

Por otro lado no tengo gans de virtualizar por que seria muy facil, ya que me toma el audio,video, etc... y no tengo que configurar mucho.. Asi que vere primero tirare a una distribucion como mandriva o fedora y despues Cuanto tenga Tiempo al dope en vacaciones pruebo una distro mas profesional.


Con respecto al Home... me la dejan picando. Ensima me entere que no puedo hacer una particion primaria mas y no se que voy a a hacer ...

---

### Post by WanderingKnight on 2008-05-21
Probé OpenSUSE hace un tiempo, y fue un garrón por los repos. Debian nos tiene malacostumbrados :) (en OpenSUSE a los repos le falta bocha de software... y se nota. Además me molestó bastante que locate no estuviera incluído en la instalación por default... WTF?).

Debian podés probar si tenés ganas de ver lo que sería un Ubuntu más "serio", por decirlo de alguna manera. Esencialmente son el mismo distro, pero Debian es un poco más hincha con el tema del free software y además se enfoca más en estabilidad que en features nuevas (aunque podés ponerte Sid, la versión inestable, para testear cosas nuevas). Yo a mi vieja le instalé un Debian a medida en una máquina bien viejita (después de hacer varios experimentos en la mía) y salió como piña.

Fedora es algo que siempre quise probar, pero la decisión de poner KDE4, inestable como es en este momento, en Fedora 9 en lugar de KDE3 me pareció muy rara.

Gentoo es para puristas con mucho tiempo de sobra :P

Algún día probaré Arch Linux o Slackware, que según tengo entendido tienen una forma de organizar los archivos que se parece mucho más al estilo de BSD que al que estamos acostumbrados a ver en las distros de Linux.

---

### Post by Hei Ku on 2008-05-21
Si queres ver un KDE en serio, no te recomiendo nada basado en Debian. Lo tocan tanto que termina siendo un engendro mutante.

---

### Post by pol666 on 2008-05-21
Debian NO eso es sabido..quiero agarrarla por la otra rama.

Pero que problema resulta que ya tengo 4 particiones primarias :(


Juro que me compraria un disco para hacer backup por que soy un rata con los DVD jajaja

---

### Post by RJQ on 2008-05-22
En cuanto a un home compartido si lo que deseas es compartir la partición donde esta el /home entonces adelante solo recuerda no formatear esa misma, así se creara un carpeta distinta para cada distro siempre y cuando cambies el nombre de tu compu en cada distro lo cual puede suavizarse con un simple numero u letra, si lo que quieres es compartir el folder-carpeta /home entonces no es posible sin un riesgo extremo. cada instalación te da la opción al momento de partir y repartir el pastel duro.

salud!!

---

### Post by Thalskarth on 2008-06-04
Aprovecho este mismo thread, 

si yo instalo 2 distros, asi como puden compartir el home (con distinto user)...
pueden también compartir el mismo swap? o tengo que crear otra partición más para la segunda distro??

---

### Post by ChameleonDave on 2008-06-04
¡Qué mala idea!

---

### Post by euzkoarima on 2008-06-04
> **Thalskarth said:**
> Aprovecho este mismo thread, 

si yo instalo 2 distros, asi como puden compartir el home (con distinto user)...
pueden también compartir el mismo swap? o tengo que crear otra partición más para la segunda distro??

Tengo entendido que podés compartir la swap sin problemas, es más, es lo más fácil de compartir sin problemas.

---

### Post by pol666 on 2008-06-04
> ¡Qué mala idea!


****?  :shock:

---

### Post by ChameleonDave on 2008-06-04
> **pol666 said:**
> ****?  :shock:

O sea que seguro que va a **** tu sistema.  Habrá conflictos.

Más vale compartir cosas de forma selectiva.  Por ejemplo, puedes utilizar un enlace simbólico para tener los mismos favoritos en tu navegador en los dos sistemas.

---

### Post by faktorqm on 2008-06-05
Para tener el mismo /home lo unico que hay que hacer es ponerse 2 nombres de usuario distintos y listo. por ejemplo faktorqm y faktor_qm y santo remedio. Las configuraciones que queres copiar, las copias a mano y las que no andan, las borras y punto, las regeneras de vuelta con el programa. Si lo "ves" desde afuera, tenes en la misma particion, dos carpetas con cada nombre de usuario y listo. Salu2!

---

### Post by Kantier on 2008-06-05
1) si vas a compartir home, tener dos nombres de usuario distintos ayuda a que no te colisionen configuraciones. si vas a usar más o menos las mismas versiones de programas, no hay drama en compartir un usuario a través de dos distros. lo que si...

2) las UID's. UNIX identifica a los usuarios con números que podes ver en **/etc/passwd** . Si tenés una carpeta de usuario compartida entre dos distros pero el usuario no tiene la misma UID vas a tener unos bonitos errores de seguridad.


[http://es.wikipedia.org/wiki/UID](http://es.wikipedia.org/wiki/UID)

---

### Post by faktorqm on 2008-06-05
No, lo que yo digo es, si tiene una carpeta llamada .compiz, que la copie al otro usuario. y asi con  cada programa. el que no le ande que lo borre de la ultima, entonces para ese programa en particular va a terner 2 configuraciones distintas. salu2!

---

