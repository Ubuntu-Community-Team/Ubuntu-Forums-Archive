---
title: "Recomendacion..."
date: 2009-04-04
forum: Software
---

### Post by WooS on 2009-04-04
Gentes m compre una notebook q tiene 160gb d disco duro...como ya he comentado en otros post soy un queso y quiero instalar el ubuntu
No m quiero apurar x miedo a hacer lio por eso quisiera q m orienten bien antes...
Lo primero es si tienen alguna guia para seguir los pasos d la instalacion...lo segundo es q vi q para hacer las particiones hay q asignar distintos espacios a cada "parte" asi q si pueden recomendarme algo (cuanto espacio a cada parte acorde a mi situacion) antes d meter la pata se los voy a agradecer
PD:no se si sirven estos datos q les voy a tirar pero bue como soy principiante mas vale q sobren datos y no q falten
Intel Dual core T2370(1,73 Ghz),1Gb d ram SO:W vista starter (si se puede tener los dos mejor)
Saludos

---

### Post by guillermolisi on 2009-04-04
> **WooS said:**
> Gentes m compre una notebook q tiene 160gb d disco duro...como ya he comentado en otros post soy un queso y quiero instalar el ubuntu
No m quiero apurar x miedo a hacer lio por eso quisiera q m orienten bien antes...
Lo primero es si tienen alguna guia para seguir los pasos d la instalacion...lo segundo es q vi q para hacer las particiones hay q asignar distintos espacios a cada "parte" asi q si pueden recomendarme algo antes d meter la pata se los voy a agradecer
PD:no se si sirven estos datos q les voy a tirar pero bue como soy principiante mas vale q sobren datos y no q falten
Intel Dual core T2370(1,73 Ghz),1Gb d ram SO:W vista starter (si se puede tener los dos mejor)
Saludos
Hasta hace unos meses atras no recomendaba dual boot en maquinas que tuvieran WinVista porque cada tanto el Vista hacia desaparecer la informacion de Ubuntu en el Grub (que es el administrador de arranque), sobreescribiendola.

Estaria bueno que quienes tengan experiencias exitosas comenten, asi no te embarcas en proyectos frustrantes.

Ahora, si queres sacar WinVista y poner solamente Ubuntu, eso es mas facil y el instalador practicamente te guia automagicamente.

---

### Post by staar on 2009-04-04
bueno te felicito por tus ganas de aprender ;-)... la instalación de ubuntu es extremadamente fácil, cuando sigas el asistente vas a ver, lo difícil para los novatos es el tema de las particiones, mirá, las notebooks generalmente vienen ahora con el disco dividido en dos particiones, una grande con el winbugs (OFF: como pueden vender algo tan terriblemente capado como las versiones starter? no se pueden abrir mas de 3 aplicaciones a la vez, y en el proximo 7 starter no se va a poder cambiar el wallpaper!! :-o) y otra chica que es la de "recuperación", lo que, a grandes rasgos, haces al instalar ubuntu es achicar la partición grande dejando espacio libre suficiente en el disco para las nuevas particiones, y despues crear dos nuevas particiones una, de 1 Gb en tu caso, la swap (análoga al archivo de intercambio o "memoria virtual" de windos) y la otra donde se instalará ubuntu...
el instalador de ubuntu tiene una herramienta de particionado (si mal no recuerdo es el 'paso 4') muy simple, te muestra un gráfico con forma de barra que representa las particiones de tu disco y te da varias opciones, como usar todo el disco (borrando windos ;-) ), particionado automático, y particionado manual...
yo te recomiendo que elijas el particionado automático, que hace solito lo que te expliqué más arriba de achicar la otra y todo eso, te deja al windos intacto y toma para ubuntu la mitad del disco (OJO windos no puede leer el sistema de archivos de linux, pero linux si el de windos, asi que los datos compartidos trata de ponerlos en el windos)...
despues el instalador te instala :-P el Grub, un cargador de arranque, que te permite acceder al sistema que quieras con un menu al prender la notebook...

saludos

---

### Post by staar on 2009-04-04
> **guillermolisi said:**
> Hasta hace unos meses atras no recomendaba dual boot en maquinas que tuvieran WinVista porque cada tanto el Vista hacia desaparecer la informacion de Ubuntu en el Grub (que es el administrador de arranque), sobreescribiendola.

Estaria bueno que quienes tengan experiencias exitosas comenten, asi no te embarcas en proyectos frustrantes.

Ahora, si queres sacar WinVista y poner solamente Ubuntu, eso es mas facil y el instalador practicamente te guia automagicamente.

apa, no sabia esa, en serio hace eso esa cosa? que asco... igual no estaria del todo mal sacarlo, sobre todo siendo starter :-P

saludos

---

### Post by WooS on 2009-04-05
Gracias por sus aportes...
Voy a probar primero dejando windows de la manera q m recomendaron total si pasa algo saco todo a la m... e instalo solamente el ubuntu
Espero que no surja nada pero el vista lo dejo solamente para jugar al World of Warcraft
La buena noticia es q el amigo d un amigo lo tiene y m va a guiar asi q mejor tdv xq el supongo q la va a tener mas clara...
Saludos!

---

### Post by Hei Ku on 2009-04-05
El WoW funciona bien en Wine, y si no tenes problemas con los drivers de tu placa, a veces hasta funciona mejor de esa manera que en win.

---

### Post by WooS on 2009-04-05
Si he leido pero como no se bien usar nisiquiera este SO si todo anda bien lo dejo asi... de todas maneras voy a ir averiguando como hacer para jugarlo en wine y una vez q aprenda sacare el W definitivamente... pero para eso vey a necesitar un tiempo primero xq lo primero q quiero hacer es aprender del entorno grafico xq estoy leyendo sobre eso y creo q es algo con lo q m voy a llevar bien xq m encanta cambiar todo a mi gusto...muchas gracias
Saludos

---

### Post by guidito73 on 2009-04-05
Bueno, como te dijeron, la instalación es bastante sencilla, donde se puede complicar es en el particionado del disco.

Acá encontré un video que explican bastante bien, en gallego sí, pero bueno.

[http://www.youtube.com/watch?v=hDkvIr_Ns1M](http://www.youtube.com/watch?v=hDkvIr_Ns1M)

Y sino busca por Youtube que hay bastante para ver y aprender.

Bienvenido!

---

