---
title: "Firefox 3.1b1 vuela"
date: 2008-10-19
forum: Software
---

### Post by Kantier on 2008-10-19
hace poco salió la beta1 del firefox 3.1, y vuela (como en "google chrome vuela", ambos usan la misma técnica para acelerar javascript)

página oficial con descargas para windows, mac y linux: [http://www.mozilla.com/en-US/firefox/all-beta.html](http://www.mozilla.com/en-US/firefox/all-beta.html) (este post es copypasteado de lo que puse en otros foros, por eso el link, pero lo dejo así se lo pasan a gente que use win o mac)

para instalar en ubuntu, un dev puso paquetes en su repositorio de ppa. para agregarlo, ponen esto: 
> deb [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) hardy main
en el sources.list, actualizan lista de paquetes, e instalan "firefox-3.1". si usan KDE, les recomiendo que se fijen de que no instale "ubufox" porque ese paquete tiene varias dependencias con GNOME.

---

### Post by pol666 on 2008-10-19
Esta estable?

Crashea? con Flash como anda?, algun bugsito molesto?

---

### Post by Kantier on 2008-10-19
todavía no me me crasheó (empecé a usarlo hoy domingo). las páginas "pesaditas" que visité son slashdot, gmail (versión full y versión full + better gmail 2), google reader y live mail (versión light creo).

el paquete es de del repo ppa de un miembro de MOTU, y en el ppa de mozilla aparecen paquetes de este tipo (así que asumo que es confiable). [[**link al perfil**]("https://launchpad.net/~fta")]

---

### Post by c4d0rn4 on 2008-10-19
chrome usa SquirrelFish para acelerar el javascript, mientras el equivalente para f3.1 es TraceMonkey que no viene activado por defecto.

En el about:config hay que ponerle true a:
javascript.options.jit.chrome
**javascript.options.jit.content**

según algunos sitios sólo comentan uno (negrita), en otros dicen esos dos.

aviso por si las moscas

---

### Post by faktorqm on 2008-10-20
La prueba de mi fuego, para mi, es abrir, clarin, ole y youtube al mismo tiempo. Si no se te rompio nada, vamos a decir que anda. Si no te rompe la pc, y podes seguir navegando tranquilo, y abrir otras appz normalmente, entonces vamos a decir que anda rapido.

<no_quiero_generar_flame>
Desde ya que Opera cumple con todo, rapido y bien, por eso lo uso :KS
</no_quiero_generar_flame>

Salu2!

---

### Post by valucha on 2008-10-20
> **faktorqm said:**
> La prueba de mi fuego, para mi, es abrir, clarin, ole y youtube al mismo tiempo. Si no se te rompio nada, vamos a decir que anda. Si no te rompe la pc, y podes seguir navegando tranquilo, y abrir otras appz normalmente, entonces vamos a decir que anda rapido.

<no_quiero_generar_flame>
Desde ya que Opera cumple con todo, rapido y bien, por eso lo uso :KS
</no_quiero_generar_flame>

Salu2![COLOR="DarkOrchid"]
Clarin + youtube + alkon + un par de cosas más anda genial. Pero cabe aclarar que a Clarin le bloquie el 90% de los flash (las propagandas mñas que nada) con el adblockplus porque sino directamente abre se pone el firefox negro y hay que cerrarlo.[/COLOR]

---

### Post by pol666 on 2008-10-20
el tema es flash 9 + pulceaudio + firefox + linux.

combinancion desastroza.

Y ahora dicen que flash 10 esta estable, anda bien pero se ve mal los contenidos flash embebidos.

---

### Post by majatu on 2008-10-20
Lo estoy probando, no tiene grandes cambios con respecto a la version anterior, pero si se le nota en promedio que mejoro la velocidad de carga de las webs. Lo cargue bastante con muchas pestañas y distintas webs y mas o menos anda rapido, se las arregla re bien! y el flash player 10 anda un poco mejor y un poco mal... como dice pol.

Va a estar mas bueno cuando sea definitivo, fechas tentativas de la version final? hay?

---

### Post by Kantier on 2008-10-20
Cabe mencionar que sin el JIT ya andaba notablemente rápido. (me avivé de lo de JIT después de postear este thread)

---

### Post by WanderingKnight on 2008-10-21
> 
<no_quiero_generar_flame>
Desde ya que Opera cumple con todo, rapido y bien, por eso lo uso
</no_quiero_generar_flame>

<no_quiero_generar_flame>
Desde ya que Opera no es libre :p
</no_quiero_generar_flame>

Chrome usa SquirrelFish? Tenía entendido que se llamaba V8 :S

---

### Post by Kantier on 2008-10-21
> **WanderingKnight said:**
> <no_quiero_generar_flame>
Desde ya que Opera no es libre :p
</no_quiero_generar_flame>

Chrome usa SquirrelFish? Tenía entendido que se llamaba V8 :S
es imposible recordarnos que el Opera no es libre sin generar flame...

Y Opera no cumple con lo de velocidad. Por lo menos perceptualmente, Opera 9.6 anda más lento que FF3.1b1 (ahora estoy bajando el 9.61 para probar pero no creo que cambie mucho) en páginas pesaditas de javascript. GMail, Slashdot, Google Reader... esas páginas no andan particularmente rápido en Opera =S

edit: sin embargo, para forear y leer webcomics no hay NADA que le gane al Opera =)

---

### Post by WanderingKnight on 2008-10-21
A mí directamente no me gusta el rendering de Opera. Bah, en realidad, salvo el de Firefox, todos los demás renderings me parecen feos, llegado el caso.

---

### Post by Kantier on 2008-10-21
ah, pero es una cuestión de motores de renderizado más que de browsers. El fuerte de Opera para mi no es el motor de renderizado, sino la UI. Opera es una obra de arte en lo que a UI concierne, aunque los defaults de las últimas versiones me están pareciendo un poco "pop" para mi gusto (léase "tirando a firefox para atraer gente", por suerte siempre se puede modificar eso)


(UI = User Interface = interfaz de usuario)

---

### Post by c4d0rn4 on 2008-10-21
> **WanderingKnight said:**
> <no_quiero_generar_flame>
Desde ya que Opera no es libre :p
</no_quiero_generar_flame>

Chrome usa SquirrelFish? Tenía entendido que se llamaba V8 :S

jajaj xD sii, perdón.
El v8 es de chrome, me confundí los webkits

---

### Post by faktorqm on 2008-10-22
No se loco yo abro Clarin + Ole + youtube + lo que quieras, (Ssin bloquear nada, no como Val) y si bien puede ser que lo haga mas lento que firefox, no se me cuelga, no se me muere nada, no me muestra ninguna pantalla blanca, ni nada de esas cosas raras. Puedo seguir usando otras appz sin tirar el disco al maximo, puedo maximizar y minimizar sin que se rompa nada, (no uso compiz aclaro) y todo anda bien. Segun Kant un poco mas lento que 3.1b1, pero antes que rapido y que no ande, prefiero que ande pero (siempre un poquito) mas lento. Salu2!!

---

### Post by guisheca on 2008-10-22
Yo me descargué el firefox3.1b y la verdad que lo noto igual che. La prueba que hice fué abrir una página que tenga muchas imágenes (por ejemplo algún post de imágenes de Taringa) en donde el firefox se pone como tortuga hasta que carga todas las imágenes (cuando digo "como tortuga" me refiero a desplazarme dentro de esa misma página, por ejemplo moviendo el scroll hacia abajo). El firefox 3.1b anduvo igual nomás.
Saludos.

---

### Post by valucha on 2008-10-22
> **guisheca said:**
> Yo me descargué el firefox3.1b y la verdad que lo noto igual che. La prueba que hice fué abrir una página que tenga muchas imágenes (por ejemplo algún post de imágenes de Taringa) en donde el firefox se pone como tortuga hasta que carga todas las imágenes (cuando digo "como tortuga" me refiero a desplazarme dentro de esa misma página, por ejemplo moviendo el scroll hacia abajo). El firefox 3.1b anduvo igual nomás.
Saludos.[COLOR="DarkOrchid"]

Pero eso no es lo que esstá más rápdio, es más, a mi me pasa eso cuando todavía no instalo la placa de video, ¿está bien instalada o soportada?[/COLOR]

---

### Post by Kantier on 2008-10-22
> **guisheca said:**
> Yo me descargué el firefox3.1b y la verdad que lo noto igual che. La prueba que hice fué abrir una página que tenga muchas imágenes (por ejemplo algún post de imágenes de Taringa) en donde el firefox se pone como tortuga hasta que carga todas las imágenes (cuando digo "como tortuga" me refiero a desplazarme dentro de esa misma página, por ejemplo moviendo el scroll hacia abajo). El firefox 3.1b anduvo igual nomás.
Saludos.
la mejora importante del FF3.1 es en cosas pesadas de javascript, no en abrir muchas imágenes.

---

### Post by guisheca on 2008-10-22
> **valucha said:**
> [COLOR="DarkOrchid"]

Pero eso no es lo que esstá más rápdio, es más, a mi me pasa eso cuando todavía no instalo la placa de video, ¿está bien instalada o soportada?[/COLOR]

Sip ta todo re bien, corro compiz, jueguis, etc. Igual no es que se pone reeeeee lento pero el desplazamiento no es fluido, y mal que me pese en opera no pasa :( (no te agrandes faktorqm :))
Disculpen que no aporté mucho, en realidad no se mucho sobre las cosas estas de renderizado, ni motor, web, etc.

---

### Post by granjero on 2008-10-22
a mi lo que me encanta del opera son los "mouse gestures" existen en firefox?

salud!

sera offtopic esto?

---

### Post by c4d0rn4 on 2008-10-22
[https://addons.mozilla.org/en-US/firefox/search?q=mouse+gesture&cat=all&as=true&vfuz=true&appid=1&lver=3.0&hver=any&atype=0&pid=0&lup=&pp=20&sort=weeklydownloads](https://addons.mozilla.org/en-US/firefox/search?q=mouse+gesture&cat=all&as=true&vfuz=true&appid=1&lver=3.0&hver=any&atype=0&pid=0&lup=&pp=20&sort=weeklydownloads)

sin dudas, firefox es tan popular por su versatilidad.

No te puedo recomendar alguna (no uso ese tipo de extensiones), pero en el link están por orden de más descargadas

---

### Post by faktorqm on 2008-10-23
guille: es que opera maneja mejor todo ese tema de las imagenes, si cargas muchas grandes no se tara, no te las muestra o te las va mostrando a poquito y ya. (igual opera usa una optimizacion que solo sirve si la pagina esta bajo algun standard html, si pusieron img src=lalala.jpg ya no la usa)

si hay gestos del mouse en firefox, no se como se usan ni como se instalan, pero me consta que estan. Salu2!

---

### Post by Aspergillus on 2008-10-24
ayer baje la b1 para probar dado que este tred me intrigo y la verdad que no note la diferencia asi que volvi al Opera, que justamente cuando lo abri me dijo que ya estaba para actualizar a la 9.61, la baje y para mi ohh gran sorpresa esa si que vuelaaaaaaa

---

