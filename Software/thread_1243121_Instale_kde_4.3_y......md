---
title: "Instale kde 4.3 y....."
date: 2009-08-17
forum: Software
---

### Post by Cajuma on 2009-08-17
[SIZE=2]Hola a todos:[/SIZE] 
Quiero compartir esta  experiencia con ustedes;  debido a
conflictos con el 4.2, decidí probar con el 4.3 , y lo instale 
según esto:
[http://linuxologist.com/linuxhowto/howto-install-kde-4-3-on-ubuntu-jaunty/](http://linuxologist.com/linuxhowto/howto-install-kde-4-3-on-ubuntu-jaunty/)
Creo que el error fue no desinstalar previamente la versión 
anterior, ya que al reiniciar me encontré con:
Apareció el full screen logo del Bios (lo tenia desactivado)
Press resume F2 para iniciar, pantalla negra...........
No aparece el mensaje de grub 1.5 cargando y después de 
unos 15" apareció el menú del grub selecciono kernel 14 y   
Pantalla de inicio (login) en el centro de la pantalla, con dos 
franjas laterales con imágenes de restos de ventanas, ahí no
termina, donde debería estar el icono de red aparece otro
indicando que debo reemplazarlo por el Knetworkmanager.
voy a synaptic desinstalo el anterior e instalo el sugerido, 
nunca mas apareció el icono en add widgets no esta.
Firefox 3.5.2 instalado desde:   
  	 	 	 	 	[http://sourceforge.net/projects/ubuntuzilla/files/](http://sourceforge.net/projects/ubuntuzilla/files/)
y después:    	[COLOR=#888888]ubuntuzilla.py -a [/COLOR]**[COLOR=#888888]install[/COLOR]**[COLOR=#888888] -p firefox[/COLOR] 
Al querer abrir el fullscreen de youtube se congela, lo reinicio
y aparece un aviso que ya se esta ejecutando y no se puede
abrir, probé con kill pid4632, y nada tengo que reiniciar para
poder abrirlo nuevamente, el consumo de memoria es excesivo
550 MiB solo el SO. y hay mas pero no quiero extenderme.
Hard: MB Asus P5K SE/EPU, Intel core 2 duo 8400, Nvidia Gforce
8600 GT Ram 2GiB Kingston 2 sata 160Gib c/u
Disco 1 ventanas, disco 2 KJJ  y  UJJ 9.04(Excelente ni un problema)
el capo del Grub es KJJ ultimo instalado.
En fin estoy buscando soluciones, pero para KK me parece que 
me quedo con GNOME.
Un abrazo, Cajuma.
	 	 	 	 	  [INDENT][COLOR=#888888]
[/COLOR][COLOR=#888888][/COLOR][/INDENT]

---

### Post by guillermolisi on 2009-08-17
El tema con KK es como en los edificios antiguos. En la plana baja habia un cartelito que decia "Habiendo escaleras la administracion no se hace responsable de los daños que el uso del ascensor pueda ocasionar".

Aqui, habiendo JJ no hay responsabilidad por el uso de KK mientras este en fase "unstable". :)

---

### Post by Cajuma on 2009-08-17
> **guillermolisi said:**
> El tema con KK es como en los edificios antiguos. En la plana baja habia un cartelito que decia "Habiendo escaleras la administracion no se hace responsable de los daños que el uso del ascensor pueda ocasionar".

Aqui, habiendo JJ no hay responsabilidad por el uso de KK mientras este en fase "unstable". :)
Yo voy por las escaleras, lo que instalé fue KDE 4.3 en K JJ 9.04 relee mi post....

---

### Post by pablo.s on 2009-08-18
> **Cajuma said:**
> En fin estoy buscando soluciones, pero para KK me parece que me quedo con GNOME.

Que una mala experiencia no
te haga tener resentimiento
para con KDE. Es un excelente
DE y si tenés la oportunidad de
probarlo otra vez pero sin estas
dificultades, vas a ver que es tan
bueno como cuentan todos los
que lo han experimentado.
Te sugiero que ya que aprendiste
a no mezclar versiones, la próxima
lo instales desde [este PPA]("http://ubuntuforums.org/deb%20http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu%20jaunty%20main"), que es
el aconsejado para la versión 4.3.
Saludos.

---

### Post by Cajuma on 2009-08-18
Hola Pablo-
Es factible desinstalar KDE 4.3  y reinstalarlo como 
corresponde ?.
Cuales serian los pasos a seguir ?
Desde ya muchas gracias !!

---

### Post by pablo.s on 2009-08-18
> **Cajuma said:**
> Es factible desinstalar KDE 4.3  y reinstalarlo como 
corresponde ?.

Para desinstalarlo y que quede
sin rastros, tendrias que empezar
con

```
sudo apt-get remove kubuntu-desktop
```

y a partir de ahi, cuando te muestre
la lista de paquetes a desinstalar,
LEER CUIDADOSAMENTE cuales
son los que dependen de kubuntu,
y tomar nota de los que va a desinstalar,
porque luego, si desinstala un paquete
esencial, te vas a complicar.

Una alternativa buena a la desinstalación
es tratar de arreglar los errores que causa,
lo cual lleva mas tiempo e investigación
pero creo que en TU CASO es mas viable.
Desconozco si podés perder algún dato
importante si las cosas no salen bien. Por
eso te digo que es más viable la resolución
de errores.

Otra cosa que tendrías que hacer es limpiar
todo rastro del KDE anterior, dado que no
le vas a dar uso e inclusive puede haber
conflictos.

Si te decidis por arreglar los errores que te
ha causado, podés hacer un post por cada
error y verás como entre todos lo podemos
solucionar.

Espero que te haya servido como guia para
encontrar la solución. Saludos.

---

### Post by guillermolisi on 2009-08-18
> **Cajuma said:**
> Yo voy por las escaleras, lo que instalé fue KDE 4.3 en K JJ 9.04 relee mi post....
Es que recuerdo habias tenido problemas oportunamente con KDE hace unos dias atras y si no recuerdo mal los habias solucionado.

Ademas decis > Disco 1 ventanas, disco 2 KJJ  y  UJJ 9.04(Excelente ni un problema) y eso me dio la impresion de que significaba que el tema era con KK, por eso mi mensaje.

Disculpa la mala interpretacion que hice.

---

### Post by Hei Ku on 2009-08-18
De todas maneras me parece que estas mezclando las cosas. El BIOS no se cambia porque instales KDE o Gnome. 

Despues, el KNetworkmanager no anda bien. Lo lamento. Siempre decimos que hay que usar el Wicd.

Y la actualizacion de Firefox la hiciste con un metodo por fuera de los repositorios y no es la version probada para Jaunty. 

Lo unico que quiero decir con todo es que tengas paciencia, y que preguntes antes de hacer algunas cosas o sacar algunas conclusiones.

---

### Post by Cajuma on 2009-08-18
Guille, Pablo y Hei Ku, ante todo agradezco los consejos, y reconozco
que debido a mi inexperiencia en Linux he cometido varios errores
conceptuales, y ademas tuve la mala idea de trastear con Kde, que
me parece es mas quisquilloso que Gnome, de todas maneras, creo
que voy a intentar resarcir  mis errores y ver como reparar KDE 4.3.
pero paciencia, tengo muy poco tiempo para hacerlo, y muy poca
experiencia, obviamente los voy a seguir requiriendo, si no les molesta.
Gracias !!!!

---

### Post by guillermolisi on 2009-08-18
No esta muerto quien pelea y nosotros (me atribuyo la voluntad de los demas) pensamos seguir por aqui un tiempo mas, suficiente como para que disfrutes del esfuerzo que estas haciendo. Asi que a no aflojar :)

---

### Post by Cajuma on 2009-08-19
Mil disculpas por no haber contestado antes, es que con 12hs. de trabajo diario y
cuatro vástagos, no le puedo dedicar el tiempo que yo quisiera.
Estoy preparando una lista de fallos e investigando cada uno, cualquier duda 
consulto.
Gracias nuevamente.
PD.:
Creo que tengo que ir preparando un cordero al asador para ir invitándolos..:)

---

### Post by oktubrer on 2009-08-19
> **pablo.s said:**
> Para desinstalarlo y que quede
sin rastros, tendrias que empezar
con

```
sudo apt-get remove kubuntu-desktop
```



Los meta paquetes *ubuntu-desktop son solo para instalar, pero no sirven para hacer la desinstalación.  Por lo menos asi era antes, y en mi Jaunty sigue funcionando asi.  Por esto, para desinstalar KDE por completo habría que conseguir la lista completa de paquetes, es un poco más complicado.
¿No sería mejor agregar el repositorio oficial, y hacer un upgrade?

---

### Post by guisheca on 2009-08-20
Hay un problema (conocido para mi) con las actualizaciones del escritorio kde4. Cada ves que pasa de 4.x a 4.y se arma un embole y lo unico que resta es borrar todos los archivos de configuración del home.

Por favor si alguien sabe las carpetas correctas que hay que borrar que le explique a este amigo, ya que las veces que lo hice yo borre cosas que no debia jejeje.

Pero creo que eso es todo el problema que tiene nuestro amigo.

Saludos.

---

### Post by Cajuma on 2009-08-20
Estuve revisando todo el synaptic para ver que se había instalado, y todo
figura como KDE 4.3 solo hay un paquete el python plasma, como 4.2 pero
no se si tendrá algo que ver. 
Por lo pronto ya cambie knetworkmanager por Wicd y la red ok.( gracias
Hei ku ).
En cuanto al entorno gráfico, además de aparecer la pantalla de inicio con 
un collage de ventanas a los dos lados, cuando arrastro las ventanas, traza
dos lineas perpendiculares y el contorno exacto de la ventana, que al soltar
el mouse y fijar la ventana desaparece, otra es que no me cambia los iconos
de las carpetas solo los del escritorio. tire un    	 	 	 	 	 	  ```
dpkg -l
```
en consola y estoy viendo si encuentro algo por ahi, pero no se por donde 

empezar, si alguien me tira un cable, agradecido.
Saludos.

---

### Post by guillermolisi on 2009-08-20
> **guisheca said:**
> Hay un problema (conocido para mi) con las actualizaciones del escritorio kde4. Cada ves que pasa de 4.x a 4.y se arma un embole y lo unico que resta es borrar todos los archivos de configuración del home.

Por favor si alguien sabe las carpetas correctas que hay que borrar que le explique a este amigo, ya que las veces que lo hice yo borre cosas que no debia jejeje.

Pero creo que eso es todo el problema que tiene nuestro amigo.

Saludos.
Si, hasta la 4.2 tambien tuve ese problema de referencias circulares en algunos paquetes nuevos que resolvi forzando la instalacion. Nunca mas tuve que desinstalar para actualizar.

Con la 4.3 no tuve ese problema.

---

### Post by Cajuma on 2009-08-20
> **guillermolisi said:**
> Si, hasta la 4.2 tambien tuve ese problema de referencias circulares en algunos paquetes nuevos que resolvi forzando la instalacion. Nunca mas tuve que desinstalar para actualizar.

Con la 4.3 no tuve ese problema.
Ok y que me recomendas ?:(

---

### Post by guillermolisi on 2009-08-20
> **Cajuma said:**
> Ok y que me recomendas ?:(
Que placa de video usas ?
Tenes activados los efectos visuales ?

Luego, revisa con el KPackagekit/Synaptic (mejor el primero) si hay algun paquete retenido sin aplicar.

Si es asi utilice Synaptic para instalarlo y/o forzar su instalacion si no queria por referencia circular.

---

### Post by Cajuma on 2009-08-20
Hola Guille:

Nvidia Gforce 8600gt, efectos visuales activados, 4 actualizaciones retenidas
Linux Generic 2.6.28.14.19 etc. Actualización de Kernel. 
Lo instalo con apt-get upgrade ?......

---

### Post by guillermolisi on 2009-08-20
> **Cajuma said:**
> Hola Guille:

Nvidia Gforce 8600gt, efectos visuales activados, 4 actualizaciones retenidas
Linux Generic 2.6.28.14.19 etc. Actualización de Kernel. 
Lo instalo con apt-get upgrade ?......
Podes hacerlo asi y fijarte si los instala todos.

Si no lo hace, usa un gestor de paquetes en modo grafico de los que mencione (a mi me resulta mas ductil Synaptic para forzar instalacion de paquetes pero y como siempre, se termina en una linea de comando en consola, solo que la interface grafica te abstrae de eso) para instalar forzadamente, asi resolves la circularidad.

---

### Post by Cajuma on 2009-08-21
Hecho
```
Sudo aptitude upgrade
```
Reinicio y todo sigue igual, en synaptic figuran instalados
2.6.28.11/13/14/15 y restricted 2.6.28.15.20
Por donde puedo  investigar ?
Gracias

---

### Post by Cajuma on 2009-08-24
Definitivamente me falta mucho camino por recorrer en Linux, 
no pude solucionar el problema, y aplique cirugia mayor.
Restaure arranque del  ventanas y reinstale KJJ 9.04 (EXT4)con
KDE 4.2 en el Sata 2 con arranque dual con UJJ 9.04, baje las
actualizaciones e instale todo desde synaptic o consola y sigo
con Firefox 3.0 que no crashea en fullscreen de youtube como
me sucedía con el 3.5.2 con KDE 4.3 habilite todos los repos
necesarios y hasta ahora todo bien.
Pero como esto no me satisface, voy a probar reinstalar KDE
4.3 nuevamente, esta vez desisntalando KDE4.2 previamente.
Desde ya agradezco la data de los foreros que me contestaron
y de los que no tambien, por interesarse.
Ya les comentare como me fue y en una de esas en algun tiempo
mas pueda aportar alguna solución en ves de estar molestando
continuamente.
Saludos.

---

### Post by sitiomatic on 2009-10-07
Este thread es un poco viejo, pero como tengo ganas de instalar kde 4.3 en ubuntu y estaba buscando data, encontre un post en un foro sobre como instalar y "desinstalar" kde 4.3 en ubuntu JJ sin riesgo.
Lo dejo para otro que busque info como yo.
[http://webupd8.blogspot.com/2009/08/install-kde-43-in-ubuntu-jaunty-904.html]("http://webupd8.blogspot.com/2009/08/install-kde-43-in-ubuntu-jaunty-904.html")

---

### Post by emiliano_raso on 2009-10-09
La verdad de la milanga para que desaparezca KDE por completo:

```
sudo apt-get remove --purge kdelibs* kde*
```

```
sudo apt-get autoremove kde
```

```
sudo apt-get install deborphan
```

```
sudo apt-get remove --purge $(deborphan)
```

Don't worry, be happy. Chau KDE :-P
(Igual estoy usandoló ahora :-P)

---

### Post by sitiomatic on 2009-10-09
Muchas gracias por la data.
Ya lo borre asi la proxima vez vuelvo a intentar de cero.

---

