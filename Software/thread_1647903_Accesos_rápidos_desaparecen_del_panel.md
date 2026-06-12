---
title: "Accesos rápidos desaparecen del panel"
date: 2010-12-18
forum: Software
---

### Post by mecdem on 2010-12-18
Equipo: Toshiba Satellite A105-S4384
Sistema: Ubuntu 10.04 (32 bits)
__________

Hola amigos.

Uso muchísimos accesos rápidos -a aplicaciones, directorios y archivos- que acomodo en varios elementos “cajón” en un panel del escritorio.

Ver:
Imagen 1, escritorio
	[http://picasaweb.google.com/mecdem/Botica#5551909254989407218](http://picasaweb.google.com/mecdem/Botica#5551909254989407218)
Imagen 2, sección del panel con los “cajones” cerrados
	[http://picasaweb.google.com/mecdem/Botica#5551909263378772530](http://picasaweb.google.com/mecdem/Botica#5551909263378772530)
Imagen 3, id. con los “cajones” desplegados.
	[http://picasaweb.google.com/mecdem/Botica#5551909264737998562](http://picasaweb.google.com/mecdem/Botica#5551909264737998562)
(Estas imágenes están tomadas de otro equipo, Toshiba NB 105-SP2802A, con el mismo SO y configurados sus paneles igual que los de la consulta).

El problema actual es su desaparición del panel. Esto ocurre desde la reciente instalación de Ubuntu 10.04.
__________

Después de la instalación de Ubuntu 10.04 (instalación a nuevo, no upgrade) observé que, no obstante tener tildada cada uno de ellos la opción “Fijar al panel”, los accesos creados cambiaban de lugar dentro de su cajón. Pero lo peor estaba por venir; después de creada una buena cantidad de accesos -casi todos- de pronto en el acto de crear uno nuevo, todo desaparecía. Repetí un par de veces la tarea con igual resultado.

Ver:
Imagen 4: aspecto del panel después de la desaparición de los accesos rápidos
	[http://picasaweb.google.com/mecdem/Botica#5551909269727302674](http://picasaweb.google.com/mecdem/Botica#5551909269727302674)
Imagen 5: ventana “Añadir al panel”
	[http://picasaweb.google.com/mecdem/Botica#5551909267163172226](http://picasaweb.google.com/mecdem/Botica#5551909267163172226)

Los accesos que desaparecen son los creados con las opciones “Lanzador de aplicación personalizado” y “Lanzador de aplicaciones...”. No desaparecen los de las demás opciones que la ventana ofrece (de las cuales utilizo siete u ocho, los separadores y el elemento “cajón”).

Busqué solución en el foro y por analogía de lo que decía en [http://ubuntuforums.org/showthread.php?t=1084014&highlight=panel+de+gnome](http://ubuntuforums.org/showthread.php?t=1084014&highlight=panel+de+gnome),  revisé en Ubuntu Tweak “Configuración de los íconos del escritorio” comprobando que la opción “Mostrar íconos de escritorio” NO estaba tildada. La tildé y reinicié la paciente tarea de recrear los accesos con sus íconos.
__________

Salvo unos pocos desplazamientos de los íconos del lugar donde los ponía -lo que fue subsanado-, todo se desarrolló con normalidad, pude poner los accesos deseados, y funcionaron perfectamente... durante cinco días.
Al querer agregar un nuevo acceso, todo volvió a desaparecer del panel.
__________

1. La opción “Mostrar íconos de escritorio” en Ubuntu Tweak “Configuración de los íconos del escritorio” permanece tildada.

2. Todos los accesos con sus íconos permanecen en .gnome2 > panel2.d > default > launchers.
Ver: Imagen 6: vista del contenido de .gnome2 > panel2.d > default > launchers.
	[http://picasaweb.google.com/mecdem/Botica#5551912640808712514](http://picasaweb.google.com/mecdem/Botica#5551912640808712514)

3. Si cliqueo sobre cualquiera de ellos, se ejecuta normalmente.

O sea que la anomalía es que no se los ve en el panel donde debieran seguir viéndose.
__________

Ruego y agradezco instrucciones para intentar la solución.
Cordial saludo. MEC

---

### Post by Pan0ramix on 2010-12-18
¿has probado de bloquear del todo los paneles de gnome? En Ubuntu Tweak tenés la opción para hacerlo dentro del grupo Escritorio>Configuraciones de Gnome.

Espero que ayude.

---

### Post by mecdem on 2010-12-18
Hola Panoramix.
Gracias por tu intervención.
__________

No he probado con el bloqueo de los paneles de gnome... ¡porque no sabía para qué podía servir!
Por defecto viene desactivado. Y -sin ánimo agorero- te cuento que en el otro equipo (Toshiba NB 105-SP2802A, alias Toshibita) está desactivado pero los accesos se mantienen firmes en sus sitios.

Voy a probar el bloqueo. Voy a crear unos cuantos accesos (por ahora no todos) y los usaré un par de días. Si veo que la cosa anda, seguiré agregando y observando. Espero que esta maquinita infernal no haga como hasta ahora, que esperaba a que terminara de crear accesos y al agregar el último ¡zas! se mandaba su felonía.
__________

Agrego algo que se me ocurre ahora.
La instalación de Ubuntu 10.04 se hizo cuando el UbuCon, y ahí mismo se instaló el Ubuntu Tweak, que yo no conocía. 
En Toshibita el mismo SO está instalado desde hace unos cuatro meses, iguales accesos estaban configurados y funcionando a la perfección. Después de haberlo conocido, le instalé el Ubuntu Tweak y todo siguió sin problemas. Ecuación "accesos primero - Ubuntu Tweak después". 
En Toshiba la ecuación fue "Ubuntu Tweak primero - accesos después". No será Ubuntu Tweak el que anda haciendo pavadas ¿no?
__________

Por las dudas, andá preparando un poco de poción mágica para rociar a Toshiba si vuelve a sus maldades. De mi parte, haré la tarea bajo la advocación del Gran Tutatis [-o<

En un par de días vuelvo para contar como va la cosa.
Nuevamente, gracias. MEC

---

### Post by biale on 2010-12-19
Cuando veas que el/los elementos desaparecen, podes probar una recarga de los paneles. Desde una consola:

killall gnome-panel

O sino salir del usuario y volver a ingresar.

---

### Post by mecdem on 2010-12-20
Aquí vuelvo.

Gracias biale por tu intervención.
Tomo nota de tu propuesta, aunque ahora no la usaré por lo que voy a contar. Pero me deja una duda: esa instrucción ¿no implica eliminar el panel?
Hace un tiempo hice una consulta ([http://ubuntuforums.org/showthread.php?p=8914237#post8914237](http://ubuntuforums.org/showthread.php?p=8914237#post8914237)) por la desaparición del panel principal, lo que se solucionó con la instrucción rm -rf .gnome .gnome2 .gconf .gconfd .metacity, cuya ejecución hizo reaparecer el panel tal como se presenta cuando recién se instala.
killall gnome-panel ¿no produciría un efecto similar?
Bueno, estas son preguntas de puro curiosa.
__________

Paso a contar.

Siguiendo la propuesta de panoramix, puse en fila los once cajoncitos que uso, y reconstruí en dos de ellos cinco o seis accesos dentro de cada uno. Luego usé la opción de Ubuntu Tweak bloquear del todo los paneles, y reinicié.

¡¡Horror!! :shock:
Todo estaba peor que antes. No solo los accesos habían cambiado de lugar dentro de los cajones, sino también los mismos cajones que había dejado prolijamente alineados a la derecha, estaban desparramados desordenadamente a lo largo del panel.

En mi mensaje anterior insinué mi sospecha de que era Ubuntu Tweak el que estaba haciendo mal las cosas. Ningún fundamento "científico", de puro bruja nomás. A la vista del desastre que se presentó ante mi vista, desinstalé completamente Ubuntu Tweak. Una vez más, pacientemente, rehice tooooodos los accesos directos. Y ¡oh, milagro! se quedaron en su lugar y todavía permanecen allí.
__________

Conté antes que en el otro equipito, una netbook Toshiba, Ubuntu Tweak fue instalado un tiempo después de la instalación del sistema operativo, cuando todos los ícono estaban creados y funcionando normalmente. Ahí no pasó nada, todo siguió igual.

Me queda la enorme intriga de saber qué ha estado pasando, pero eso queda para ustedes los expertos.

Vuelvo en dos o tres días, por un lado para ver si hay alguna respuesta a mis preguntas (aunque entiendo que responder lleva tiempo y estas que hago son preguntas -como ya dije- de puro curiosa) :-k ; y segundo, para decirles si, como espero, los íconos siguen en su lugar.

Les agradezco mucho la ayuda.
Un abrazo. MEC

---

### Post by mecdem on 2010-12-20
ADDENDA: me quedó un "problemita". Resulta que como no tenía mis accesos rápidos, en Ubuntu Tweak activé la opción mostrar en el escritorio la carpeta personal del usuario.

Como ahora no tengo el Tweak ¡no puedo sacar la carpeta¡
¿Hay alguna forma, vía consola, de eliminarla?
Si la hay, agradezco la/s instrucción/es. Si no, reinstalaré Ubuntu Teak, sacaré la carpeta y nuevamente desinstalaré el Tweak.
Peroooo... ¡es que le tomé miedo!! :|

Gracias. MEC

---

### Post by biale on 2010-12-20
Desde consola, para no ver el icono de la carpeta de usuario seria:

gconftool-2 --type Boolean --set /apps/nautilus/desktop/home_icon_visible False

/apps/nautilus/desktop/home_icon_visible   Va todo junto, es una clave del registro.

En princio Ubuntu tweak hace eso. No hay drama en instalarlo, modificar y borrar.

killall gnome-panel  en si no puede hacer nada malo, solo recargas las definiciones almacenadas cuando la sesion ya esta estabilizada.

Y si por esas la cosa queda peor, significa que hay otro problema. Idem si los resultados son aleatorios.

Para conjurar los miedos, te propongo crear un segundo usuario, que puede ser sudoer o no y experimentar desde alli. Los paneles son definiciones a nivel de usuario y no de sistema.

---

### Post by mecdem on 2010-12-24
> Desde consola, para no ver el icono de la carpeta de usuario seria:
gconftool-2 --type Boolean --set /apps/nautilus/desktop/home_icon_visible False /apps/nautilus/desktop/home_icon_visible
Va todo junto, es una clave del registro.

Biale, no se puede creer: el ícono de la carpeta de usuario... ¡desapareció solo!
Es lo que tenía que hacer, pero lo hizo un día y medio después de desinstalado Ubuntu Tweak.
(Conservar un cierto grado de cordura cuando uno es usuario de computadora -cualquiera sea el sistema operativo- es una dura tarea  :-( )
__________

> Para conjurar los miedos, te propongo crear un segundo usuario, que puede ser sudoer o no y experimentar desde alli. Los paneles son definiciones a nivel de usuario y no de sistema.

¡Qué bueno! No se me había ocurrido. Voy a crear un segundo usuario para cuando quiera hacer "experimentos" sin temor a romper mis archivos y configuraciones.

[CENTER]La buena nueva es que
**los accesos directos siguen firmes en sus sitios**.[/CENTER]

O sea que el culpable del desaguisado fue Ubuntu Tweak. El misterio que quedará sin develar es por qué razón en este equipo tuvo tan mal comportamiento.
__________

Panoramix, Biale, muchísimas gracias por la ayuda.
Un abrazo.
Tengan un feliz 2011.
):P

---

### Post by biale on 2010-12-24
Ojo que eso vale para las configuraciones "de usuario". Si desinstalas algo serio o cambias la resolucion de pantalla, eso se aplica a todos los usuarios del sistema.

Feliz 2011!

---

### Post by mecdem on 2010-12-26
Oops, no había visto tu nuevo mensaje. Gracias, biale, lo tendré en cuenta.

Aunque cuando hablaba de "experimentar", tranqui, tranqui, que no me refería a programar iptables en el kernel...  :p   sólo a esas cositas que a veces nos gusta ensayar a los usuarios curiosos: un programita nuevo que no precisamos para nada, un decoradito de la pantalla, esas cosas. Me gusta la idea de hacerlas en otro "terreno".

Pero, pensándolo bien: tener doble usuario ¿no sería una proyección de un "trastorno de identidad disociativo", como se le dice ahora a la doble personalidad? Mmmmm... :-k :p

Abrazote y muchas gracias.
MEC

---

### Post by mecdem on 2011-02-01
**[SIZE="4"]¡¡VOLVIERON A DESAPARECER!![/SIZE]**
#-o :frown:

Durante unos días (un par de semanas, más o menos) los íconos estuvieron allí, y de pronto... ¡zas! desaparecieron de los paneles.

Hubo otro problemita con los íconos, ya resuelto, que está en [http://ubuntuforums.org/showthread.php?p=10419073#post10419073](http://ubuntuforums.org/showthread.php?p=10419073#post10419073). Lo menciono por si tuviera algo que ver en el conjunto de calamidades.
__________

La rebelde Toshiba y la netbook "Toshibita" tienen la misma versión de Ubuntu (10.04 - 32 bits) y Toshibita tiene Ubuntu Tweak. Los mismos íconos que en Toshiba desaparecen, funcionan OK en "Toshibita". Me he puesto a mirar y remirar las diferencias en una y otra, a ver si esto sirve como dato útil.

1. Versión de EoG:
En "Toshibita": 2.30.0-0ubuntu1.
En Toshiba: 2.32.0-0ubuntu1.

2. Orígenes del software:
En "Toshibita": apuntan todos a lucid.
En Toshiba: apuntan a lucid y a maverick.

3. linux-headers:
En "Toshibita": 2.6.32-28.
En Toshiba: 2.6.35-24.

Las dos máquinas están tirando mensajes de error al actualizar.
Y no agrego más porque no sé si esto les sirve para el tema del hilo. Si sirvieran de algo, puedo agregar más detalles de los puntos 2 y 3.
__________

Mil gracias por la ayuda.
MEC

---

### Post by mecdem on 2011-03-19
Ajajá!
Nadie vino por aquí ¿eh?

Bueno, como mi maquinita andaba que parecía un Win con virus :frown: -no terminaba de solucionar un problemita que ya aparecía otro-, la solución fue: ¡quirófano! Nueva instalación del SO y se arreglaron el problema de esta consulta y otros más que andaban dando vuelta.

Sí, ya sé que no es la ortodoxia, pero si la ortodoxia no da resultados (y resultados más o menos rápidos porque no es cuestión de pasar la vida insistiendo ](*,) en un único camino cuando ya lo recorrimos lo suficiente para ver que no lleva a ninguna parte), entonces, como dije, quirófano.

Ahora anda de maravilla, \\:D/ como debe hacerlo un Ubuntu que se precie.
Gente linda: agradezco todo el tiempo que me dedicaron.
Cariños. MEC
):P

---

