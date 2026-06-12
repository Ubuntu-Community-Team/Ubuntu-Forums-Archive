---
title: "Desprenderse de Windows"
date: 2008-06-26
forum: Software
---

### Post by Afkael on 2008-06-26
Hola gente, les comento que me he inscripto a la lista pero no llegan los mails que envio, si alguien pudiera explicarme qué estoy haciendo mal se los agradesco y la razón de este post es porque estoy viendo con buenos ojos la posibilidad de instalar Ubuntu en mi PC y prescindir de Windows completamente.
El problema es que tengo hijos que pasan largos ratos jugando en la PC y en definitiva la PC también es de ellos por lo que necesito saber que tan viable es la idea de linux.
Se de las limitaciones de linux en este sentido pero quizá Cedega pueda solucionarlo. He visto la lista de cedega y es bastante completa, no se si "que haya funcionado para alguien" significa que lo hará para todos pero será cuestión de probar. También quisiera saber si juegos que no estan "oficialmente" soportados (como gears of war) puede que se los pueda hacer funcionar tocando un poco. Por eso me gustaría su opinion.
A pesar de que pienso utilizar software libre, por mi trabajo y mis pasatiempos quisiera saber de la posibilidad de disponer de herramientas como Microsoft Office 2007 y Adobe Creative Suite CS3, aunque esto no seria imprecindible.
Seguramente la reproducción de video y audio en la mayor cantidad de formatos posibles es importante y si pudiera hacer uso de los 64bits de mi micro mejor (Win64 tiene también grandes problemas con los drivers).
La configuración de mi PC la armé pensando que en algún momento pueda ser útil para el renderizado de 3D (con upgrade a quad y mucha ram) y con una video de medio pelo para que jueguen los chicos (y los no tan chicos)
 
En fin, escribí ya demasiado... no más les dejo la configuración de mi PC para que me que tan factible será:
 
Micro: AMD 5200+ DualCore (la idea es en algún momento poner un quad)
Mobo: MSI K9A2 Platinum
Memos: 2GB DDR2 Kington (la idea es sumar otro modulo de 2GB cuando pueda)
HDD: Samsung 200GB Sata2
VGA: MSI 8600GT 512DDR3
 
Saludos y espero me tengan buenas noticias

---

### Post by valucha on 2008-06-26
[COLOR="DarkOrchid"]Podrías porbar juegos nativos de linux, y más, podrías probar los juegos que hay en [http://www.ubuntugames.org/](http://www.ubuntugames.org/) que si buen está en portugués se entiende y tiene muchas capturas de pantalla.
Tal vez tus hijos o vos, si están dispuestos a probar nuevos juegos, lo aprovechen, hay de todo.

Con respecto al hard, si tenés una placa High Definition de Realtek o de Intel capaz que tengas un pitido insoportable cuando reproducís un sonido o, que ni tengas sonido, pero como hay mucha mucha gente con ese tipo de placas, hay también muchas soluciones, así que si tenés la mala suerte de que te pase eso con el audio buscás un poco en Google y en 15 mins ya lo tenés solucionado.
El resto creo que va perfecto, te re sobra máquina, ah! y hay quienes que dicen que los juegos en Linux "emulados" (es decir coridos por wine o cedega) funcionan mejor que en Windows, a mi me lo dijo un amigo re gamer con Gentoo. Pero capaz depende de cada uno.

Saludos, Valucha[/COLOR]

---

### Post by sajnox on 2008-06-26
En primer lugar bienvenido!!

Vamos por partes:

1) Lista de mails: En primer lugar te comento que la lista de mails y el foro no van de la mano, aunque muchos de los que estamos aca tambien estamos
alla. Igualmente te comento que vi tu mail y te confirmo que llegan. Cuando envias un mail no lo recibis por ser parte de la lista.
2) Tema juegos y Ubuntu: Si bien como te decia valucha hay muchos juegos para Ubuntu en mi opinion no es necesario que migres TODO de un dia para el otro, se puede tolerar un dual boot por un tiempo. Para mas datos te aconsejo que visites la guia Ubuntu en lo que se refiere a instalacion.
[www.guia-ubuntu.org](www.guia-ubuntu.org)
3) Hay programas (pagos) para dar soporte a la instalacion de MS Office que funcionan muy bien (no se del 2007, si lo vi andando con el 2003)

Saludos y contanos de tus progresos

---

### Post by tzulberti on 2008-06-26
> **Afkael said:**
> Hola gente, les comento que me he inscripto a la lista pero no llegan los mails que envio, si alguien pudiera explicarme qué estoy haciendo mal se los agradesco y la razón de este post es porque estoy viendo con buenos ojos la posibilidad de instalar Ubuntu en mi PC y prescindir de Windows completamente.


Revise los mails y no llego ninguno que pareciera de alguien que esta por instalar ubuntu. A que direccion de mails los enviastes? Confirmastes el mail de darte de alta en la lista (no me acuerdo si este ultimo paso era necesario) ?

> **Afkael said:**
> 
El problema es que tengo hijos que pasan largos ratos jugando en la PC y en definitiva la PC también es de ellos por lo que necesito saber que tan viable es la idea de linux.
Se de las limitaciones de linux en este sentido pero quizá Cedega pueda solucionarlo. He visto la lista de cedega y es bastante completa, no se si "que haya funcionado para alguien" significa que lo hará para todos pero será cuestión de probar. También quisiera saber si juegos que no estan "oficialmente" soportados (como gears of war) puede que se los pueda hacer funcionar tocando un poco. Por eso me gustaría su opinion.



Nos juegos que no estan oficialmente soportados realmente es muy poco probable que los puedas hacer funcionar. Cedega nunca lo use, pero use wine (wwww.winehq.org) que es el "original" a partir del cual se basa cedega. Las aplicaciones que correr con wine estan aca: [http://appdb.winehq.org/](http://appdb.winehq.org/), y buscando sobre tu consulta en particular dice que no corre ni para atras ([http://appdb.winehq.org/objectManager.php?sClass=application&iId=6155](http://appdb.winehq.org/objectManager.php?sClass=application&iId=6155))


Se que wine puede usar las librerias (dlls) de un windows que tengas instalado en otra particion, asique talvez haciendo eso te funcione.

> 
A pesar de que pienso utilizar software libre, por mi trabajo y mis pasatiempos quisiera saber de la posibilidad de disponer de herramientas como Microsoft Office 2007 y Adobe Creative Suite CS3, aunque esto no seria imprecindible.
Seguramente la reproducción de video y audio en la mayor cantidad de formatos posibles es importante y si pudiera hacer uso de los 64bits de mi micro mejor (Win64 tiene también grandes problemas con los drivers).


La verdad es que vas a tener un par de problemas usando 64 con los codecs. Tambien tendrias un par de problemas con el Wine o Cedega, y otro par de aplicaciones comunes. Personalmente te recomiendo que te instales una version de 32 bits hasta que te sientas comodo. 

Para muchos programas de Windows existen sus equivalentes de linux. Aca tenes una lista un poco desactualizada: 
[http://www.linuxrsp.ru/win-lin-soft/index-spanish.html](http://www.linuxrsp.ru/win-lin-soft/index-spanish.html)
[http://alts.homelinux.net/](http://alts.homelinux.net/)


> 
La configuración de mi PC la armé pensando que en algún momento pueda ser útil para el renderizado de 3D (con upgrade a quad y mucha ram) y con una video de medio pelo para que jueguen los chicos (y los no tan chicos)
 
En fin, escribí ya demasiado... no más les dejo la configuración de mi PC para que me que tan factible será:
 
Micro: AMD 5200+ DualCore (la idea es en algún momento poner un quad)
Mobo: MSI K9A2 Platinum
Memos: 2GB DDR2 Kington (la idea es sumar otro modulo de 2GB cuando pueda)
HDD: Samsung 200GB Sata2
VGA: MSI 8600GT 512DDR3
 
Saludos y espero me tengan buenas noticias

Para ver si el hardware te funciona correctamente, en el livecd vas a poder testear el sonido/video/red/etc... sin problemas.

---

### Post by vk-cdg on 2008-06-27
Como dice el amigo sajnox no hace falta migrar completamente a linux, sobre todo si en casa tenés público "gamer". 
En mi caso, mi SO principal es Ubuntu, pero mantengo un XP con dualboot (en otro disco rígido) para los juegos.
Finalmente, como mi mujer no pudo/quiso adaptarse a Ubuntu ella usa también el XP. 
Todos mis archivos y programas están en Ubuntu, pero de vez en cuando tengo que usar el XP por algún soft de modelado de software, que si bien existen alternativas libres, como trabajo en equipo, tengo que usar lo que la mayoría usa.

En fin, resumiendo, mi consejo es, Ubuntu para casi todo, y los juegos... en Windows. De esa forma, si se percha el XP, se reinstala y listo, no hay datos que perder (o muy pocos)

---

### Post by Afkael on 2008-06-27
Bueno, en realidad no se si es lo que esperaba... si bien estoy lejisimo de ser un experto, he instalado linux muchas veces y realmente no tiene sentido que mis hijos terminen de jugar en WinXP y tenga que reiniciar la PC para ejecutar Blender, ver un video o escuchar música en Linux si en definitiva también puedo hacerlo en Win. Seria solamente una perdida de espácio y de tiempo. El DualBoot fué la razón de que todas mis instalaciones de Linux fracasaran.
La idea es deshacerse de Windows, lamentablemente gran parte del uso importante que le doy a mi PC son los games y quiero evitar que se desperdicie el hard que tengo (deben saber ya que una 8600GT puede correr juegos como Assasine Creed a full en 1280x1024 a 25FPS).
Asi como dice Valucha que tiene un amigo gamer que supongo a echo funcionar juegos "importantes" en su Gentoo quiero prepara el Ubuntu que instale para que esté preparado para correr muchos de los juegos que tengo.
No me importa que al instalar esté todo (con windows siempre funciona el sonido y el video pero para ver Big Buck Bunny tuve que descargar codecs) sino que se pueda configurar y que descargando lo necesario no tenga problemas como que "no, no existe ni la más remota posibilidad de que puedas reproducir un .mp3 en linux".
En definitiva es saber si con esfuerzo y agotando las posibilidades creen que pueda llegar a un final satisfactorio y no a decir "me tengo que volver a Windows".
De Gears of War leí por ahí que Microsoft habia trabado el desarrollo del port para linux ya que no le caia bien la idea. Pensé por ahí que de forma "no oficial" se podría haber filtrado algo.
Quizá conozcan alguna comunidad LinuxGamer en español que me puedan ayudar.
En fin, Gracias y Saludos

---

### Post by niko_3100 on 2008-06-27
El problema no es linux o ubuntu, el problema es que las compañias no desarrollan sus juegos para linux simplemente porque no venden o tienen contrato con microsoft. Personalmente no me parece malo lo del doble booteo ya que con tremenda maquina levanta al toque asi que...

---

### Post by faktorqm on 2008-06-27
Yo sin wine ni cedega ni nada llegué a correr muchos juegos. Ahora, el problema no es para mi ni la venta, ni el contrato con microsoft. Por ejemplo ID (empresa archiconocida) saco desde el quake I para linux y para windows. De hecho la ultima version de quake I es con soporte openGL. Quake 2 y 3 y 4 lo mismo. Entonces ya el problema para mi es la manera en que programan. Mas alla de que los de ID sean los mejores, los tipos programaron todo pensando en la portabilidad, y eso cuenta mucho. No se si sabian pero los de ID (los dos primeros) eran programadores de PM y se tiraron a hacer juegos por que les gustaba jaj asi por que si digamos.

El otro gigante en cambio, Blizzard, jamás hizo nada por Linux. Hasta los juegos que conozco yo digamos (Starcraft, Starcraft Broodwar, Warcraft I, II y III, WOW los mas renombrados) nunca ni siquiera apuntaron a pensar en el mercado linuxero. Lo ultimo que lei de blizzard es que con la popularizacion de ubuntu y demas distros, el starcraft II lo iban a sacar para linux, pero creo que 6 meses despues de sacarlo para windows, una cosa asi era.

De todas maneras, hay muchos juegos que se pueden correr bajo linux igual, yo te digo los que probe: Starcraft, Starcraft Broodwar, Warcraft III y la expansion (como me costo pasar la final de la expansion....)

Para los juegos nuevos la verdad no tendria idea como seria la mano por que no me da la compu ni para virtualizar una 386, pero creo que instalando directx 10 bajo wine deberia funcionar sin mayores.. capaz no te anda no se, pero seria cuestion de sentarse y probar mucho.
Con respecto a adobe y derivados, bueno, eso no anda ni a palos. bajo wine en su momento podias llegar a correr varias cosas.. pero si realmente se trata de trabajo, no me arriesgaria a un cuelgue. Eso depende de vos. 
Salu2!

---

### Post by pol666 on 2008-06-27
conoces WUBI?

---

### Post by Afkael on 2008-06-27
Bueno, quizá me expresé mal... No quiero más a Windows, es eso. Si tengo que compartir mi PC entre Win y Linux.. me quedo con Windows hasta que Linux me permita precindir de él.
De todos modos algunas cosas me han echo ser optimista al respecto (por ejemplo [esto]("http://pasionlinux.blogspot.com/2008/05/assassins-creed-en-mandriva-linux-20081.html")) y si le agrego la posibilidad de emular consolas (principalmente PS2 - por ser más "real" -)es bastante interesante.
He visto videos de cedega con Call of Duty 4, Fall Out 2, Need for Speed Carbon y bueno, un surtido interesante..
Tengo un HD de 80Gb sin usar.. voy a hacer pruevas en él y veremos...

Saludos

---

### Post by MeduZa on 2008-06-28
> **Afkael said:**
> Bueno, quizá me expresé mal... No quiero más a Windows, es eso. Si tengo que compartir mi PC entre Win y Linux.. me quedo con Windows hasta que Linux me permita precindir de él.
De todos modos algunas cosas me han echo ser optimista al respecto (por ejemplo [esto]("http://pasionlinux.blogspot.com/2008/05/assassins-creed-en-mandriva-linux-20081.html")) y si le agrego la posibilidad de emular consolas (principalmente PS2 - por ser más "real" -)es bastante interesante.
He visto videos de cedega con Call of Duty 4, Fall Out 2, Need for Speed Carbon y bueno, un surtido interesante..
Tengo un HD de 80Gb sin usar.. voy a hacer pruevas en él y veremos...

Saludos

aca tenes una larga lista de juegos que andan en cedega:

[http://www.cedega.com/gamesdb/](http://www.cedega.com/gamesdb/)

y aca tenes otra para wine, yo uso los 2 pero principalmente uso WINE salvo que el juego se me haga imposible correrlo en wine.

[http://appdb.winehq.org/](http://appdb.winehq.org/)


Yo en mis ratos de oscio soy gamer y me pasé 100% a linux de un dia para otro (El golpe al principio fue duro pero no duele tanto como parece), prefiero peliarme con un juego 10 horas hasta hacerlo andar en linux que tener un dual boot con windows. Lo unico que tengo en mi pc es un virtual machine de un windows xp home (original :P pero vino de prepo en la notebook de mi mujer) que solo uso para testeos de programas y paginas web para laburo, sino ni eso tendria!

he jugando incontables juegos de windoes en linux, desde el oblivion pasando por warcraft 3, half life 2 y muchoas mas, hasta juegos nativos de linux como son el quakewars enemy territory que esta de 10.

Aca es simple el que quiere puede. ;)

---

### Post by Afkael on 2008-06-28
> **MeduZa said:**
> aca tenes una larga lista de juegos que andan en cedega:

[http://www.cedega.com/gamesdb/](http://www.cedega.com/gamesdb/)

y aca tenes otra para wine, yo uso los 2 pero principalmente uso WINE salvo que el juego se me haga imposible correrlo en wine.

[http://appdb.winehq.org/](http://appdb.winehq.org/)


Yo en mis ratos de oscio soy gamer y me pasé 100% a linux de un dia para otro (El golpe al principio fue duro pero no duele tanto como parece), prefiero peliarme con un juego 10 horas hasta hacerlo andar en linux que tener un dual boot con windows. Lo unico que tengo en mi pc es un virtual machine de un windows xp home (original :P pero vino de prepo en la notebook de mi mujer) que solo uso para testeos de programas y paginas web para laburo, sino ni eso tendria!

he jugando incontables juegos de windoes en linux, desde el oblivion pasando por warcraft 3, half life 2 y muchoas mas, hasta juegos nativos de linux como son el quakewars enemy territory que esta de 10.

Aca es simple el que quiere puede. ;)

Ok, es lo que busco.. Ahora mismo me pongo en campaña.
Después estube pensando en WinVista y DirectX 10 y se me cruzaba por la mente que alguien lograra correr DX10 en linux.. se vendría la noche en MS.
Si consigo en linux una plataforma medianamente gamer... me traigo unos cuantos con migo \\:D/\\:D/

---

### Post by MeduZa on 2008-06-28
> **Afkael said:**
> Ok, es lo que busco.. Ahora mismo me pongo en campaña.
Después estube pensando en WinVista y DirectX 10 y se me cruzaba por la mente que alguien lograra correr DX10 en linux.. se vendría la noche en MS.
Si consigo en linux una plataforma medianamente gamer... me traigo unos cuantos con migo \\:D/\\:D/

estaban laburando en eso la ultima vez que lei, decia que no se les iba a complicar tanto portar dx10 a linux teniendo la base de dx9 de todas maneras el dx10 fue una maniobra marquetinera de m$ para que los ganers usen vista, parece que van a sacar dx11 en poco tiempo segun lei

---

