---
title: "[SOLVED] Instalar fuentes TTF en ubuntu 9.04"
date: 2009-07-01
forum: Software
---

### Post by drazhe on 2009-07-01
Hola, estuve buscando en internet como instalar fuentes TTF en ubuntu y no consigo hacerlo funcionar, hice exactamente lo que dicen en estas paginas por ejemplo y cuando abro el openoffice write no las puedo elegir a las fuentes... 

[http://ubuntux.info/2009/04/26/como-instalar-fuentes-en-ubuntu-904-jaunty-jackalope/](http://ubuntux.info/2009/04/26/como-instalar-fuentes-en-ubuntu-904-jaunty-jackalope/)

[http://www.configurarequipos.com/doc816.html](http://www.configurarequipos.com/doc816.html)


que estoy haciendo mal y como instalarlas correctamente???

---

### Post by pablo.s on 2009-07-01
Te voy a dar mi metodo
(bastante bruto, por cierto)
para instalar las fuentes TTF.
[B]Advertencia: requiere un
cuidado especial con lo que
se copia, porque se usa el
superusuario[/B]. Que conste.

Primero instalás Midnight
Commander. Luego ejecutás
mc como superusuario.

```
sudo mc
```

De una mitad de los paneles,
tenés que estar en el directorio
/usr/share/fonts/truetype
y en la otra mitad tenés que estar
en el directorio en el que tenés
las fuentes para instalar.
Seleccionas con Ins todas las
que te interesan y presionás F5.
Luego salís con F10. Salis de la
sesión y entrás y supuestamente
ya las podés utilizar.

---

### Post by drazhe on 2009-07-01
mira, es lo mismo que me dicen las paginas que mencione, las fuentes TTF que quiero instalar ya estan metidas en ese directorio que dices 

usr/share/fonts/truetype

y para poder copiar, va abrir esa carpeta tuve que entrar como root, enclusive ya probe copiando los archivos ttf dentro de las 3 carpetas que hay dentro de

usr/share/fonts

y en ningun caso cuando abro el openoffice aparecen... ya no se que cuernos hacer....

---

### Post by pablo.s on 2009-07-01
Dos cosas:

Son fuentes TTF, o son OTF/PFB ?

Has reiniciado el servidor X ?

---

### Post by drazhe on 2009-07-01
> **pablo.s said:**
> Dos cosas:

Son fuentes TTF, o son OTF/PFB ?

Has reiniciado el servidor X ?

son todas TTF


pues, en una de las paginas me dicen hacer eso desde este comando

fc-cache -vf

lo hice, y aun nada, tambien probe con reiniciar al sistema, y sigue igual... estoy haciendo mal las cosas?

---

### Post by gmunioz on 2009-07-01
Hola dra...:

El comando es:

```
sudo fc-cache -vf
```

---

### Post by drazhe on 2009-07-01
acabo de hacer

sudo sudo fc-cache -vf

y aun sigo sin ver las fuentes en openoffice.

les pregunto algo, los archivos ttf, deben estar en 

usr/share/fonts

o en 

usr/share/fonts/truetype

o en que carpeta de las 3 que hay ahi adentro de Fonts?

---

### Post by pablo.s on 2009-07-01
Si son fuentes TTF, dentro
de /truetype.
Si son fuentes PostScript,
dentro de /type1
Las OTF pueden ir en /fonts
dentro de su carpeta.
Pregunta: Que versión de OO
estás utilizando?

---

### Post by drazhe on 2009-07-01
la que trae ubuntu 9.04, creo que es la 3.0

acabo de revisar y tengo instalada la version 3.0.1
pero en la pagina de openoffice, hablan de una 3.1.0

tendre que actualizar?

---

### Post by pablo.s on 2009-07-01
No. Me extraña sobremanera
el asunto que no reconozca las
fuentes.
El sistema reconoce las fuentes?
Si quieres poner de tipografia
del sistema alguna de las 
instaladas, te permite hacerlo?
A mi por ejemplo OO no me 
muestra ciertas fuentes PostScript
que le he instalado, pero otros
programas si. Por ende hay algun
dato que no tenemos y que impide
que todas las fuentes se incorporen.

---

### Post by drazhe on 2009-07-01
pablo.s tienes razon, el Sistema si me reconoce las fuentes instaladas, pero cuando las selecciones en lugar de aparecer la fuente aparecen un monston de cuadraditos como si no la reconociera, aunque me permite verla en la lista de seleccion... pero el OO sigue sin mostrarmelas...

---

### Post by drazhe on 2009-07-01
tendra algo que ver que hayan sido unas 500fuentes mas o menos???? y que el SO no aguante tanta cantidad de archivos??? pero si fuera ese el caso, cargaria hasta donde pueda cargar... no creo que no las quiera mostrar o que ubuntu no aguante una cantidad de fuentes grande....

---

### Post by EnriqueK on 2009-07-01
Por lo que entiendo ya tienes instaladas las fuentes, lo que queda es entrar por ejemplo a OO Writer -->Herramientas --> Opciones --> Fuentes --> Desmarca el casillero "**solo fuentes no proporcionales**" seguramente lo temés marcado y es por eso que el OO no puede usar las nuevas fuentes.
Para en otra, para instalar fuentes ttf , podés crear una carpeta oculta dentro de tu carpeta de usuario que llamarás** .fonts**  y allí movés todas las fuentes que quieras.

---

### Post by drazhe on 2009-07-01
> **EnriqueK said:**
> Por lo que entiendo ya tienes instaladas las fuentes, lo que queda es entrar por ejemplo a OO Writer -->Herramientas --> Opciones --> Fuentes --> Desmarca el casillero "**solo fuentes no proporcionales**" seguramente lo temés marcado y es por eso que el OO no puede usar las nuevas fuentes.
Para en otra, para instalar fuentes ttf , podés crear una carpeta oculta dentro de tu carpeta de usuario que llamarás** .fonts**  y allí movés todas las fuentes que quieras.



no, sigue igual, hice lo que dices y mi OO no me quiere dejar usar mis fuentes... 
con eso que me dijiste del crear una carpeta .fonts, tambien lo hice y me resulto igual, tampoco pude ver las fuentes o usarlas.. pero el problema de tu consejo es que solo van a servir para mi usuario, y yo necesitaria que esten disponibles para todos...

---

### Post by drazhe on 2009-07-01
bueno gente, muchas gracias a todos, consegui que mi OO por fin me reconozca las fuentes nuevas instaladas!!! jejeje, al final creando una carpeta .fonts dentro de mi home\(mi usuario) y copiandolas ahi dentro el OO las reconocio y permite usarlas... por desgracias solo andan en mi usuario, pero como soy el que mas las utiliza no tendre mayores dificultades... 
Gracias a todos por molestarse con mi problema!!
Saludos!

---

### Post by Spity on 2009-07-02
...entonces, si la lógica me acompaña, deberías hacer lo mismo para cada usuario. Es decir, crear una carpeta en /home/x/.fonts y copiar las fuentes. :)

---

### Post by EnriqueK on 2009-07-02
Es curioso, a mi me han funcionado ambos métodos, o asa poner las fuentes en /usr/share/fonts/truetype/openoffice o sea creando una carpeta .fonts en el directorio de usuario, este último tiene la ventaja de que te va a servir cuando cambies de versiñon de Ubuntu sienmpre que tengas tu /home separada.
Puede que sea necesario reiniciar sesión para habilitar las nuevas fuentes , la verdad no me acuerdo.

---

### Post by aledruetta on 2009-07-03
> **Spity said:**
> ...entonces, si la lógica me acompaña, deberías hacer lo mismo para cada usuario. Es decir, crear una carpeta en /home/x/.fonts y copiar las fuentes. :)

¿Y creando la carpeta .fonts en la carpeta root? ¿Servirá?

---

### Post by santiagoward2000 on 2009-07-03
> **aledruetta said:**
> ¿Y creando la carpeta .fonts en la carpeta root? ¿Servirá?

Para instalar las fuentes como root, la carpeta es **/usr/share/fonts**. Ahí las ttf normalmente van a la carpeta **truetype**.
Saludos!

---

### Post by drazhe on 2009-07-03
pasa que la idea de cargar las fuentes en usr/share/fonts es mas que nada para no ocupar tanto espacio, si mi caperta fuentes pesa 150mb y la tengo que copiar en 10 usuarios, terminare usando mas de 1gb para fuentes solamente, por eso queria ponerlas en usr/share...... 

de cualquier manera, cargandolas ahi donde dicen, no me las deja usar el OO, pero cuando cree la .fonts dentro de mi homa/usuario ahi si, por desgracia la puedo usar solamente yo nomas... 
de cualquier manera no se molesten... ya solucione el tema como dije mas arriba, 

gracias a todos por ayudarme...

---

### Post by drazhe on 2009-07-03
Ahora si que no entiendo nada, es posible que la fuente TTF Times New Roman tenga algun conflicto con linux?!

pasa lo siguiente, abro el OpenOffice, escribo cualquier texto, y cuando quiero ponerle a ese texto la fuente Times New Roman, esta se transforma en otra llamada Savatage que es considerablemente diferente a la clasica TNR.... a alguien se le ocurre que pasa???

es cierto que la TNR es una fuente totalmente precindible, pero me resulta extraño no poder usarla... 

las demas andan bien, arial, verdana, algeriam y otras que trae el Window$, pero la TNR no...

---

### Post by drazhe on 2009-07-03
Adjunto una foto para ilustrar el problema, no digo mas porque creo que es obvia la diferencia.. jejeje

[http://www.subirimagenes.com/imagen-pantallazo-2823788.html](http://www.subirimagenes.com/imagen-pantallazo-2823788.html)

---

### Post by staar on 2009-07-03
para el tema de copiar las fuentes a otros usuarios, podés hacer links simbólicos a la carpeta .fonts de tu home en los otros homes ```
sudo ln -s /home/*tuusuario*/.fonts /home/*otrousuario*/.fonts
``` tenés que hacerlo con sudo, y después podés cambiarle los permisos y el propietario a los enlaces creados...

ni idea que pasa con la Times New Roman...

saludos

---

### Post by drazhe on 2009-07-03
staar

y eso para que me sirve? lo que hice fue eliminar la fuente savatage y ahora la times new roman volvio a ser la times new roman.. jejejeje.. por suerte no es una fuente que utilice con mucha frecuencia.. jejejeje es muy rotulada para mi gusto...

---

### Post by EnriqueK on 2009-07-03
Probá en jacer ñp siguiente
1.- Mové la carpeta .fonts que has creado en tu carpeta de usuario al directorio **/opt**
2.- En cada carpeta de usuario creas enlaces simbólicos a dicha carpeta, de esta manera cada usuario podrña hacr uso de las nyevas fuentes
cada enlace simbólico tendría una sintaxis simila a la siguiente 
**ln -s /opt/.fonts /home/usuario/ **
en donde usuario es el nombre de cada cuenta-

---

### Post by drazhe on 2009-07-03
> **staar said:**
> para el tema de copiar las fuentes a otros usuarios, podés hacer links simbólicos a la carpeta .fonts de tu home en los otros homes ```
sudo ln -s /home/*tuusuario*/.fonts /home/*otrousuario*/.fonts
``` tenés que hacerlo con sudo, y después podés cambiarle los permisos y el propietario a los enlaces creados...

ni idea que pasa con la Times New Roman...

saludos


perdon, debi haber leido completamente tu mensaje antes de responder lo que dije... ya entendi lo de los enlaces simbolitos...

---

### Post by milovan1971 on 2009-07-03
No se si te sirve, pero yo he instalado muchas fuentes ttf desde repositorios, mucho mas facil.
Fijate aca te nombra muchas: 
[http://lamaquinadiferencial.wordpress.com/2009/05/13/mas-tipos-de-letra-para-ubuntu-fonts/](http://lamaquinadiferencial.wordpress.com/2009/05/13/mas-tipos-de-letra-para-ubuntu-fonts/)

Y perdon por la ignorancia, pero no hay una forma de instalar fuentes ttf sin usar comandos? Esto seguro no atrae mucho a los amantes de win$...:-k

---

### Post by staar on 2009-07-03
> **milovan1971 said:**
> No se si te sirve, pero yo he instalado muchas fuentes ttf desde repositorios, mucho mas facil.
Fijate aca te nombra muchas: 
[http://lamaquinadiferencial.wordpress.com/2009/05/13/mas-tipos-de-letra-para-ubuntu-fonts/](http://lamaquinadiferencial.wordpress.com/2009/05/13/mas-tipos-de-letra-para-ubuntu-fonts/)

Y perdon por la ignorancia, pero no hay una forma de instalar fuentes ttf sin usar comandos? Esto seguro no atrae mucho a los amantes de win$...:-k 
todo comando que sea de la forma ```
sudo aptitude (o apt-get) install *talpaquete*
``` es solo para instalar un paquete desde los repositorios, por lo que puede hacerse perfectamente desde Synaptic, buscando el nombre del paquete e instalándolo...

si querés buscar las fuentes ttf disponibles en los repos, abrí Synaptic, buscá ttf, e instalá las que quieras...

generalmente se explican las cosas con comandos porque es más fácil, rápido y seguro, aunque muchas cosas pueden hacerse desde la interfaz gráfica (pero si vas a usar linux andate acostumbrando a la consola, al final termina siendo tu mejor amiga :-D)

saludos

---

### Post by milovan1971 on 2009-07-03
> **staar said:**
> todo comando que sea de la forma ```
sudo aptitude (o apt-get) install *talpaquete*
``` es solo para instalar un paquete desde los repositorios, por lo que puede hacerse perfectamente desde Synaptic, buscando el nombre del paquete e instalándolo...

si querés buscar las fuentes ttf disponibles en los repos, abrí Synaptic, buscá ttf, e instalá las que quieras...

generalmente se explican las cosas con comandos porque es más fácil, rápido y seguro, aunque muchas cosas pueden hacerse desde la interfaz gráfica (pero si vas a usar linux andate acostumbrando a la consola, al final termina siendo tu mejor amiga :-D)

saludos
Gracias por la aclaracion... aunque se lo que hace aptitude...  pero me parece mas facil hacerlo asi que creando directorios, dando permisos, copiando, etc. desde consola.
Y coincido con vos, la consola es muy util, rapida y practica. Pero es LEJOS el mayor problema de linux respecto a win$: al 90% de los usuarios nuevos les decis "abri la consola y pone $sudo apt-get etc, etc..." y sale huyendo!!  Cuando empece a usar linux [hace unos 10 años!!] fue lo que me hizo volver a win$... hoy es mucho mas facil gracias a la interfaz grafica... antes no servia mucho y casi todo pasaba por la consola.
Pero muchos en vez de explicar las cosas usando la GUI, ante preguntas que vienen de gente que parece no tener demasiada experiencia, le manda un monton de instrucciones usando comandos de consola (yo me incluyo), y ese es un obstaculo imposible para muchos usuarios novatos. Perdon por la fuga de ideas!!
saludos ):P

---

### Post by pablo.s on 2009-07-03
> **milovan1971 said:**
> al 90% de los usuarios nuevos les decis "abri la consola y pone $sudo apt-get etc, etc..." y sale huyendo!!

No creo. Ayer vi los números
del INDEC y decían que los
usuarios que salian huyendo
eran el 9%.

> **milovan1971 said:**
> Pero muchos en vez de explicar las cosas usando la GUI, ante preguntas que vienen de gente que parece no tener demasiada experiencia, le manda un monton de instrucciones usando comandos de consola (yo me incluyo), y ese es un obstaculo imposible para muchos usuarios novatos.

Se le puede explicar lo mismo
usando la consola que con una
GUI. Pero por una razón muy
importante no se hace:
Si el usuario no aprende la
flexibilidad que otorga la linea
de comandos, en cierto punto
donde es imprescindible ese
conocimiento se va a trabar y
ahí si va a salir huyendo. Entonces
cuando más utilice la terminal
más dominio va a adquirir del
funcionamiento de los programas.
Una GUI en por lo general un
front-end de un comando o serie
de comandos.
Por ejemplo yo pod&#341;ía haber ayudado
a drazhe de la siguiente manera:
Ejecutá sudo Nautilus, de ahi seleccioná
las fuentes, presio&#324;á Control+C, etc
hasta que lograra copiar las fuentes.
Pero es más practico que vea que
en los sistemas UNIX todo es un archivo.
Que vea a las fuentes de la misma
manera que si fuera cualquier otro
archivo que necesita copiar a un
destino; asi adquiere el proceso que
necesite realizar ya sea copiar MP3,
videos, archivos de configuración y asi.

---

### Post by milovan1971 on 2009-07-03
Pablo.s:
Mas allá de la broma del INDEC, los que salen corriendo cuando ven algo parecido a la consola son muchos, y no hay que negarlo.
Esta es la razón porque linux no ha ganado más usuarios: al decir "Se le puede explicar lo mismo usando la consola que con una GUI. Pero por una razón muy importante no se hace:..." es una frase que ya escuche antes, y me parece poco feliz: 1) ya que implica que vos sabés lo que el otro tiene/debe aprender y la forma de hacerlo;y 2)dejás afuera a la mayoría de los usuarios, a quienes no les interesa aprender que hay detrás de un GUI en culquier sistema operativo (como windows, macOS, linux varios), sino que quieren poder hacer las cosas sin tener casi conocimientos de informática. 
No hay que ser fundamentalista... y de hecho, ubuntu ha ganado aceptación entre muchos usuarios fieles de windows gracias a que es muy amigable! Por eso es mi pregunta: para que explicar todo solamente con comandos, siendo posible hacerlo tambien a traves de las ventanas? Dejemos de ahuyentar a la gente! Si queremos que GNU/linux siga creciendo, debemos abandonar dogmatismos como el de "usar comandos es mejor"... mejor para quién? Yo obviamente uso comandos, ya que conocí las computadoras cuando sólo se usaban comandos... pero eso no implica que para incentivar el cambio a linux le ande mostrando a la gente lo que se puede hacer con comandos! Disculpas de nuevo por el off-topic!
saludos para todos,
M

---

### Post by pablo.s on 2009-07-03
> **milovan1971 said:**
> Esta es la razón porque linux no ha ganado más usuarios: al decir "Se le puede explicar lo mismo usando la consola que con una GUI. Pero por una razón muy importante no se hace:..." es una frase que ya escuche antes, y me parece poco feliz: 1) ya que implica que vos sabés lo que el otro tiene/debe aprender y la forma de hacerlo;

Bueno, es mi opinión
o es la tuya. Yo me quedo
con la mía. Vos quedate
con la tuya. Mi intención es
que el usuario aprenda a
usar una computadora
como una herramienta.


> **milovan1971 said:**
> 2)dejás afuera a la mayoría de los usuarios, a quienes no les interesa aprender que hay detrás de un GUI en culquier sistema operativo (como windows, macOS, linux varios), sino que quieren poder hacer las cosas sin tener casi conocimientos de informática.

Ahi me parece que hay
un error de sentido común.
No se puede subestimar a
la gente cómo para decir que
la mayoría no quiere aprender.
Ese mismo error lo ha cometido
Microsoft y lo ha cometido Apple
y somete a la gente. Te sugiero
leer las cuatro libertades del
Software Libre.

> **milovan1971 said:**
> Si queremos que GNU/linux siga creciendo, debemos abandonar dogmatismos como el de "usar comandos es mejor"... mejor para quién?

No digo que sea mejor
"per se". Contribuye a que
las habilidades de razonamiento
se ejerciten. No hace daño.
No es perder el tiempo. Es un
muy buen hábito, cómo debatir
esto.

---

### Post by EnriqueK on 2009-07-04
Francamente no le encuentro sentido a eso de la lucha entre consola vs gui , opino que lo mejor es tratar de aprovechar las ventajas que tienen cada una de ellas dependienfo de las circunstancias, por ejemplo el saber usar la consola tiene enormes ventajas para poder automatizar procesos mediante la creación de Scripts o la gui para el  maaejo simple de archivos y de apremdizaje de nuevas aplicacioes , etc, etc, . En definitiva, uso ambas alternetivas e inclusive trato de hacerlo de forma simultánea , por ejemplo cuando tengo que introducir una ruta a un archivo en la consola, simplemente entro a Nautilus y seguidamente arrastro al terminal a dicho fichero y así queda escrita su ruta en la terminal y  como este, pueden baber varios casos en que la consola y la gui pueden complementarse y muy bien.

---

### Post by drazhe on 2009-07-04
a la mier*** un pequeñp problema con un ignorante supremo de linux en general, se termino conviertiendo en un debate ejejjeje... 
les comento que yo comence en la informatica con una comodore 128, y despues pase a un 386sx con DOS (no recuerdo su version) y window$ 3.1 asi que algo de comando se, pasa que el DOS y el terminal de Linux, es como medio diferente en cuanto a comandos, pero nada del otro mundo, en lo personal, la gui grafica me confunde mas que el terminal... 

en otro post mio, tambien se dio una discusion similar, decian que las cosas se podian hacer en window$ y linux, aunque de diferentes formas, el tema esta en sentarse 10min y leer el manual, ya que si uno viene de algun SO diferente, (ya sea windo$, mac os x, solaris, colibri OS o cualquiera que se les ocurra) es obvio que va a costar aprender linux, de la misma manera que si se migra alrevez, de linux a cualquiera de esos SOs, va a haber problema, el asunto es sentarse un tiempo y leer el manual y no matarse.

hoy en dia el desarrollo de linux esta mucho mas avanzado que cuando comenzo y con la internet y foros como este se hace mucho mas sencillo aprenderlo y en lo personal, me satisface mucho mas usar linux que cualquier otro SOs, (y eso que yo trabajo con Mac OS X) no estoy hablando de dejar de usar window$ solamente, sino que creo que es hasta mejor linux que mac... 

bueno, saludos a todos, y como dije antes, mis problemas con las fuentes ttf, ya se solucionaron, si quieren cerrar el post esta todo bien y abramos otro en el cual discutir estos temas, ya que medio como que nos fuimos por las ramas... jejeje

Saludos a todos nuevamente!

---

### Post by Hei Ku on 2009-07-04
Se cortó la discusión, que no tiene nada que ver con el tema a tratar.

Si a algún amante de Win le molesta usar los deditos, lo lamento. Si miran hacia la parte superior de la pantalla, el foro es de **Ubuntu**. 

Todo post siguiente que no tenga que ver con el tema del thread, se borra.

---

### Post by MPx1 on 2009-07-06
Yo hago esto:

me bajo las fuentes en formato ttf..
abro la terminal..
tipeo: 

sudo nautilus

[contraseña]

te habre una ventana como root.. navegas hasta 

/usr/share/fonts/truetype 

listo copias y pegas.. cerras la ventana de root y ya está

---

### Post by drazhe on 2009-07-08
> **MPx1 said:**
> Yo hago esto:

me bajo las fuentes en formato ttf..
abro la terminal..
tipeo: 

sudo nautilus

[contraseña]

te habre una ventana como root.. navegas hasta 

/usr/share/fonts/truetype 

listo copias y pegas.. cerras la ventana de root y ya está


Gracias nuevamente, pero el problema ya esta solucionado, ademas en el primero mensaje que deje, mencione un par de paginas, una de ellas, me dice hacer lo que vos decis de abrir el nautilus desde el terminal con sudo, copiar las fuentes en ese lugar que dices y listo, pero el OO no me las reconocia cuando hacia eso... por eso comence este post.. de cualquier manera, gracias nuevamente yalo solucione...

---

### Post by juancarlospaco on 2009-07-08
Yo las Ubuntizo *[SIZE="1"](o Debianizo)[/SIZE]* y las guardo en DVD.
Ejemplo, les dejo** Todo DaFont.com en 1  .deb**
Por licencias dice la pagina: *" Archive of freely downloadable fonts. "*

Doble click y se instalaron.

Name:	dafont_1-1_all.deb
Size:	**376.7MB** *(395027162 bytes)*
Created:	2009-07-08 17:00:01
Shared:	   Publicly Shared
URL:	
[http://www.adrive.com/public/0ea4435da766da6f7722cfae44d7f1ffc294a95a6c8c9e5d35a9024a1bfe987d.html](http://www.adrive.com/public/0ea4435da766da6f7722cfae44d7f1ffc294a95a6c8c9e5d35a9024a1bfe987d.html)

:p

---

### Post by varg04444 on 2009-09-16
Hola @[drazhe]("http://ubuntuforums.org/member.php?u=798309"), se que dijiste que el tema esta solucionado, pero aún así me parece que queda la duda de por que no te funcionan las fuentes cuando las copias en /usr/share/fonts y creo que di con el chiste. En mi caso me pasaba lo mismo, las fuentes estaban ahí pero Openoffice no las reconocía y el problema resultó ser de permisos, no me había fijado y las carpetas que copié solo tenian permisos de lectura y ejecución para el root, esto hacía que Openoffice como usuario normal no pudiera leer las carpetas y tomar las fuentes. Así que lo unico que hice fue un "sudo nautilus" y cambiar los permisos.

Bueno, espero que les sirva.

---

### Post by elucubracion on 2010-10-24
Buenas tardes,

Se que el tema está cerrado pero para futuras lecturas por parte de usuarios que encuentren este hilo dejo el siguiente enlace:

[http://lobotuerto.com/blog/2010/05/14/convertir-archivos-otf-a-ttf-en-ubuntu/](http://lobotuerto.com/blog/2010/05/14/convertir-archivos-otf-a-ttf-en-ubuntu/)

Podréis realizar un script gracias a la potencia de fontforge para convertir fuentes OTF a TTF.

Un saludo,

---

