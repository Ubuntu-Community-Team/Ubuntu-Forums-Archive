---
title: "¿ como instalo picasa?"
date: 2008-11-05
forum: Software
---

### Post by EDGAR MORENO on 2008-11-05
:lolflag::lolflag::lolflag::lolflag:
amigos de UBUNTO 
 

TRATO DE INSTALAR PICASA DE GOOGLE DENTRO DE UBUNTU 

He llegado hasta este link

 [http://www.google.com/linuxrepositories/ubuntu704.html](http://www.google.com/linuxrepositories/ubuntu704.html) 

como tutorial para ello tengo ....

pero me quedo en el punto de la ventana de "sorftware sources" ..cuando le doy click a "import Key file" alli , no me abre nada ....:confused::confused:

gracias de antemamo por sus enseñanzas 

saludos 

Edgar 

los invito a mi blog para que vean mis dibujos 

[http://caricaturasedgar.blogspot.com](http://caricaturasedgar.blogspot.com)

---

### Post by emancu on 2008-11-05
La verdad nunca lo hice de esa manera, siempre es mejor la consola, donde podes ver que error devuelve si ocurre algo o si termino de hacer una tarea.

Intenta hacerlo de esta otra forma:
[http://www.google.com/linuxrepositories/apt.html]("http://www.google.com/linuxrepositories/apt.html")

---

### Post by EDGAR MORENO on 2008-11-05
> **emancu said:**
> La verdad nunca lo hice de esa manera, siempre es mejor la consola, donde podes ver que error devuelve si ocurre algo o si termino de hacer una tarea.

Intenta hacerlo de esta otra forma:
[http://www.google.com/linuxrepositories/apt.html]("http://www.google.com/linuxrepositories/apt.html")


Perdona mi crasa ignorancia en esto de los computadores,amigo  EMANCU fui al sitio pero no se que hacer , soy un completo primiparo , solo se dibujar y pintar con lapices y colores , asi que me quede en ver solamente la pagina que gentilmente me enviaste , pero si me esplicas  un poco mas , por favor , te estare muy agradecido.

saludos 

edgar

---

### Post by pol666 on 2008-11-05
probaste instalando wine como te dije?

busca wine en agregar y quitar programas

---

### Post by faktorqm on 2008-11-06
Te traduzco la pagina y te agrego las cosas que no dice:

Configuracion a traves de linea de comandos para APT

En un sistema basado en APT como ser Debian, Ubuntu, etc., debes descargar la clave y luego usar apt para instalarla y actualizar el indice de paquetes de vuelta.
Para mas informacino sobre la clave para firmar paquetes de Google, mirar la pagina "Signing Key"

Ahora vamos a Aplicaciones -> Accesorios -> Terminal.

(a partir de ahora podes copiar y pegar los siguientes comandos)

```
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub
```

```
sudo apt-key add linux_signing_key.pub
```

Las últimas versiones de apt-get automaticamente intentaran verificaran los paquetes cuando los descargan. Si una clave es inapropiada o el paquete está corrupto, vas a tener un mensaje parecido a este:

```
WARNING: The following packages cannot be authenticated!
packagename  
```

eso significa "AVISO: Los siguientes paquetes no han podido ser autenticados" y abajo la el nombre del paquete. El nuestro creo que esta en castellano y te tira algo muy parecido a eso.

Ahora agregamos la siguiente linea al archivo /etc/apt/sources.list

```
sudo gedit /etc/apt/sources.list
```

y ahi te abre el editor de textos con un archivo. NO BORRES NADA! solo tenes que agregar esta linea al final, guardar y salir.

```
# Google software repository
deb http://dl.google.com/linux/deb/ stable non-free
```

listo, ahora usamos apt-get "como siempre":

(primero actualizamos la lista de paquetes)
```
sudo apt-get update
sudo apt-get install picasa
```

y listo el pollo. Espero que te haya servido. Cualquier cosa pregunta. Salu2!

---

### Post by vk-cdg on 2008-11-06
Otra opción (un poco mas simple) es instalarlo desde el .deb 

De este link se puede descargar el deb de picasa 3.
[http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_3.0-current_i386.deb](http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_3.0-current_i386.deb)

Si bien es bastante mas fácil, para alguien con un poco mas de conocimientos es mejor realizar lo que menciona faktorqm ya que tenemos una mayor seguridad en cuanto al contenido y la ventaja de que si se publica una nueva versión de picasa el gestor de actualizaciones nos avisará y lo actualizará.

---

### Post by ramiro_md on 2008-11-06
Tal cual, pone en google "picasa ubuntu" y te aparecerá la página de descarga de picasa, busca el .deb para ubuntu (sería como el .exe de windows), le das doble click e instala.
Así lo instalé yo.
Un saludo.

---

### Post by EDGAR MORENO on 2008-11-06
> **faktorqm said:**
> Te traduzco la pagina y te agrego las cosas que no dice:

Configuracion a traves de linea de comandos para APT

En un sistema basado en APT como ser Debian, Ubuntu, etc., debes descargar la clave y luego usar apt para instalarla y actualizar el indice de paquetes de vuelta.
Para mas informacino sobre la clave para firmar paquetes de Google, mirar la pagina "Signing Key"

Ahora vamos a Aplicaciones -> Accesorios -> Terminal.

(a partir de ahora podes copiar y pegar los siguientes comandos)

```
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub
```

```
sudo apt-key add linux_signing_key.pub
```

Las últimas versiones de apt-get automaticamente intentaran verificaran los paquetes cuando los descargan. Si una clave es inapropiada o el paquete está corrupto, vas a tener un mensaje parecido a este:

```
WARNING: The following packages cannot be authenticated!
packagename  
```

eso significa "AVISO: Los siguientes paquetes no han podido ser autenticados" y abajo la el nombre del paquete. El nuestro creo que esta en castellano y te tira algo muy parecido a eso.

Ahora agregamos la siguiente linea al archivo /etc/apt/sources.list

```
sudo gedit /etc/apt/sources.list
```

y ahi te abre el editor de textos con un archivo. NO BORRES NADA! solo tenes que agregar esta linea al final, guardar y salir.

```
# Google software repository
deb http://dl.google.com/linux/deb/ stable non-free
```

listo, ahora usamos apt-get "como siempre":

(primero actualizamos la lista de paquetes)
```
sudo apt-get update
sudo apt-get install picasa
```

y listo el pollo. Espero que te haya servido. Cualquier cosa pregunta. Salu2!


gracias amigo factorqm 

tengo en el sitio que me dices esto :
sudo apt-key add linux_signing_key.pub

pero ahora leo esto

usuario@usuario-desktop:~$ 

despues de intentar pegar las direcciones , pero como al parecer me falto una letra y cuando intente escribirla tal ves fue cuando aparecio este letrero pues tuve que borrar toda la clave (creo que hice algo mal) ¿que debe aparecer originalmente cuando se abre? estoy un poco confundido 

pero ahora veo 
en el mismo sitio otra cosa 
veo esto 
usuario@usuario-desktop:~$ 

realmente no se que hacer , ¿he hecho algo malo?  ¿pego sin espaciar? , tal ves hice algo malo ,¿ y se va a desconfigurar algo? , no se que tan grave es esto para todo el sistema , 

pues cuando copie al arrastrar me falto una letra y cuando intente borrar la copia -para luego pegar una nueva completa , veo que cambio el texto, 

mi gran duda ahora es ¿cual es el texto original que debe estar? (en la ventana cuando abre uno -aplicaciones- accesorios-terminal-?????)

cierro esta ventan y aparece solo esto: usuario@usuario-desktop:~$

---

### Post by pol666 on 2008-11-06
Cuando vos abris una terminal te aparece la linea de bash. seria en tu caso esta



usuario@usuario-desktop:~$

Cuando ingresas un comando con sudo, te pide la contraseña, aunque no al veas, vos escribila y luego dale enter. Es por seguridad,.

---

### Post by EDGAR MORENO on 2008-11-06
> **pol666 said:**
> Cuando vos abris una terminal te aparece la linea de bash. seria en tu caso esta



usuario@usuario-desktop:~$

Cuando ingresas un comando con sudo, te pide la contraseña, aunque no al veas, vos escribila y luego dale enter. Es por seguridad,.

que es** sudo**? perdona pero  no se absolutamente nada de estos terminos,

 escribo la clave (con la que entro  ubuntu) dentro de la ventana que se me abre con -aplicaciones-accesorios-terrminal?

---

### Post by valucha on 2008-11-06
[COLOR="DarkOrchid"]Edgard, no te compliques, bajalo de acá [http://picasa.google.com/linux/thanks-deb.html](http://picasa.google.com/linux/thanks-deb.html) y lo instalas "al estilo windows".[/COLOR]

---

### Post by c4d0rn4 on 2008-11-06
en lo personal me bajo el instalador de windows y listo.

El paquete """de""" linux, trae todas cosas que yo ya tengo instaladas. Si tenes wine, un firefox, en realidad lo unico que te hace falta es el exe de instalación

[http://picasa.google.com/linux/download.html#picasa30](http://picasa.google.com/linux/download.html#picasa30)
lean justo arriba de *New Features*

---

### Post by EDGAR MORENO on 2008-11-06
> **vk-cdg said:**
> Otra opción (un poco mas simple) es instalarlo desde el .deb 

De este link se puede descargar el deb de picasa 3.
[http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_3.0-current_i386.deb](http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_3.0-current_i386.deb)

Si bien es bastante mas fácil, para alguien con un poco mas de conocimientos es mejor realizar lo que menciona faktorqm ya que tenemos una mayor seguridad en cuanto al contenido y la ventaja de que si se publica una nueva versión de picasa el gestor de actualizaciones nos avisará y lo actualizará.

como veras amigo , estoy en el duro aprendizaje de esto , en la cual no se nada , de nada,y como piensa uno que de repente hace uno algo que desconfigura cosas importantes , entonces aparece en uno , como una pelicula de suspenso y tension , espero que tenga un final feliz , je je je 

bueno como veo que no pude hacer lo de pegar estos codigos , estoy intentando ahora , lo que propones , pero al abrir el link que gentilemente  me mandas : ( [http://dl.google.com/linux/deb/pool/...rrent_i386.deb](http://dl.google.com/linux/deb/pool/...rrent_i386.deb)  ) aparecen las opciones..... open with..... salva to disk .....do this automatically....¿cual debo marcar?  

gracias por tu palabras

---

### Post by EDGAR MORENO on 2008-11-06
> **c4d0rn4 said:**
> en lo personal me bajo el instalador de windows y listo.

El paquete """de""" linux, trae todas cosas que yo ya tengo instaladas. Si tenes wine, un firefox, en realidad lo unico que te hace falta es el exe de instalación

[http://picasa.google.com/linux/download.html#picasa30](http://picasa.google.com/linux/download.html#picasa30)
lean justo arriba de *New Features*

:lolflag::lolflag::lolflag:gracias amigo por tus comentarios , desearia poder ya tener los conocimientos para entenderte , pero mi generacion , no fue educada , o no nos enseñaron computacion (no existia) asi que los que acabamos de comprar un computador, estamos en la etapa de completos primiparos , como podras entender no comprendo ¿como llego a tener el exe de instalacion ....? cuales serian los pasos para ello?

---

### Post by EDGAR MORENO on 2008-11-06
> **valucha said:**
> [COLOR="DarkOrchid"]Edgard, no te compliques, bajalo de acá [http://picasa.google.com/linux/thanks-deb.html](http://picasa.google.com/linux/thanks-deb.html) y lo instalas "al estilo windows".[/COLOR]

amigo Valucha , en verdad estoy muy agradecido tanto con vos , como con todos los demas amigos en ubuntu, como ves en el link que mandas se abren varias opciones , cual elijo?  
open with..... salva to disk .....do this automatically....¿cual debo marcar? 

gracias de nuevo

---

### Post by c4d0rn4 on 2008-11-06
valucha es mujer, o por lo menos eso me dice el rosa jaja xD... pero más allá de eso.

Usá el link de valucha, yo lo dije más que nada para aclarar el contenido del deb. En tu caso no aclaré, oscurecí jaja xD
--------------------------

Poné save to disk*, o salvar en el disco. Después dale doble click al archivo una vez descargado. Por defecto creo que lo poné en el desktop. Va a revisar unas cosas y después te va a dejar apretar instalar casi en la parte arriba derecha de la ventana.

Le das a todo que sí, probablemente se queje de que podes instalar por los repositorios algunas cosas, pero no hagas caso.




-----------------------------
*La diferencia que hay entre save to disk y open with, es que el primero lo graba en el rigido en un lugar seguro y nada más. El segundo, open with, lo guarda en un lugar temporal y abre el archivo automaticamente.

Cualquiera de las dos opciones realmente son indiferentes para este caso. Pero al guardar algo de manera temporal, notese que es temporal.

---

### Post by EDGAR MORENO on 2008-11-06
[QUOTE=c4d0rn4;6118361]valucha es mujer, o por lo menos eso me dice el rosa jaja xD... pero más allá de eso.

Usá el link de valucha, yo lo dije más que nada para aclarar el contenido del deb. En tu caso no aclaré, oscurecí jaja xD
--------------------------

Poné save to disk*, o salvar en el disco. Después dale doble click al archivo una vez descargado. Por defecto creo que lo poné en el **desktop**. Va a revisar unas cosas y después te va a dejar apretar instalar casi en la parte arriba derecha de la ventana.

estoy en esa etapa de que se instale , te agradeceria si me explicas que es  desktop , para saber que tengo que hacer cuando termine de cargar en este momento va por el 80% , sinenvargo esto ya la habia hecho antes , no se si con el mismo link (no recuerdo) y solo consegui que apareciera en el escritorio, pero no pudo abrir el programa , fue cuando acudi con uds 



Le das a todo que sí, probablemente se queje de que podes instalar por los repositorios algunas cosas, pero no hagas caso.

te avisare que me dice el sistema , no sea que dañe todo yo y me empiece a enredar como un mosco en telaraña  ...je je je

saludos amigo

---

### Post by EDGAR MORENO on 2008-11-06
esta noche voy a intentarlo de nuevo ya que no abrio nada ni aparecio nada en el escritorio . 

les contare mañana . mientras les envio una muestra de mis dibujos . que gracias a los amigos aqui en este foro ya puedo bajar dentro de ubuntu

[IMG]http://img66.imageshack.us/img66/6830/073gk0.jpg[/IMG]

---

### Post by EDGAR MORENO on 2008-11-07
TODAVIA NO HE PODIDO INSTALAR PICASA , pero al menos ya puedo manejar las fotos , pero tengo el problema que en la ventana, no aparece la opcion de ver las imagenes , solo aparecen los codigos , es posible configurar como en windows que se vean las miniaturas?

---

### Post by faktorqm on 2008-11-07
> **EDGAR MORENO said:**
> TODAVIA NO HE PODIDO INSTALAR PICASA , pero al menos ya puedo manejar las fotos , pero tengo el problema que en la ventana, no aparece la opcion de ver las imagenes , solo aparecen los codigos , es posible configurar como en windows que se vean las miniaturas?

amm usas firefox? si es asi, deberia haberte dejado un archivo en el escritorio, o en tu carpeta personal (accedes con lugares -> carpeta personal). Una vez que lo ves le das doble click y te va a saltar una ventana, apretas instalar, te pide contraseña (en todos los casos que vas a manejar vos tenes que poner la misma que pones cuando prendes la compu) y listo. Si te dice algun cartel, no dudes en postear aca y lo vamos viendo. Salu2!

---

### Post by EDGAR MORENO on 2008-11-07
> **faktorqm said:**
> amm usas firefox? si es asi, deberia haberte dejado un archivo en el escritorio, o en tu carpeta personal (accedes con lugares -> carpeta personal). Una vez que lo ves le das doble click y te va a saltar una ventana, apretas instalar, te pide contraseña (en todos los casos que vas a manejar vos tenes que poner la misma que pones cuando prendes la compu) y listo. Si te dice algun cartel, no dudes en postear aca y lo vamos viendo. Salu2!

ESTIMADO AMIGO FAKTORQM 

de nuevo gracias por tus enseñanazas 


si uso firefox 

volvere hoy a ver que puedo hacer para seguir aprendiendo a manejar UBUNTU , cada ves me agrada mas , aun cuando no lo se manejar ni un 0,0001 % creo, je je je je , pero bueno algun dia , sera , tengo muchas dudas que resolver para  mis  humildes trabajos -las caricaturas- y su proyeccion en la red , espero poder aprender rapido , para responder a mis acciones , por ejemplo la pantalla que tengo , ya no es de las antiguas , pero esto hace ver las imagenes "engordadas" es decir alargadas a lo ancho , pero si me mandan un foto para una caricatura , veria las caras distorcionadas ¿se puede arreglar este efecto de pantalla, para ajustarla y verlas como las anteriores pantallas de las antiguas? este es por ejemplo algo que me urge 
tambien tengo el problema de como ver las imagenes miniaturizadas , cuando trato de colocarlas en un blog o foro, cuando el sistema del blog me pide que se las envie , entonces me abre una ventana en ubuntu , pero aun no se manejarla para verlas como en windows cuando se le daba la modalidad de ver las miniaturas ¿como se hace esto en UBUNTU? ¿es posible? , tambien sufro de falta de ortografia , y la ventan del corrector se abre , pero no esta activada , ¿como podre activarla? , bueno amigos son mis dudas y problemas para , poder compartir con mis amigas y amigos , en mi pequeño mundo de compartir sonrisas ....las caricaturas que dibujo....

por ultimo amigo , por supuesto que tu eres uno de los grandes maestros para nosotros los primiparos , pero no encuentro la medallita a la derecha abajo, no la veo , dame mas pistas , por favor.....

saludos 

edgar

---

### Post by EDGAR MORENO on 2008-11-07
A parte de la instalacion de picasa , tengo la duda de como ver las fotografias cuando en alguna blog o pagina como hi5 para cargar las fotos en la ventana que parece como **browse ** al darele clik aparece la ventana de ubuntu cuyo titulo es:  File Uploat pero alli no he podido ver las fotos , solo aparece los codigos , ¿es posible ver las fotos en miniatura, alli en esta ventana " File Uploat " ?

---

### Post by EDGAR MORENO on 2008-11-08
> **valucha said:**
> [COLOR="DarkOrchid"]Edgard, no te compliques, bajalo de acá [http://picasa.google.com/linux/thanks-deb.html](http://picasa.google.com/linux/thanks-deb.html) y lo instalas "al estilo windows".[/COLOR]

MUCHAS GRACIAS AMIGA VALUCHA:D:D:D:D:D 
ya pude instalar PICASA , tal como me enseñaste 

Me han dicho que eres una dama,espero seguir aprendiendo, sobre todo , lo que mas me sirve para mi trabajo , el manejo de imagenes, no se te olvide amiga VALUCHA que estoy a tu ordenes para cuando quieras un dibujo, sera un placer poder hacer algo por y para vos, te mando de nuevo mi correo caricaturasedgararrobagmailpuntocom y de nuevo mi blog de caricaturas 

 [http://caricaturasedgar.blogspot.com/](http://caricaturasedgar.blogspot.com/)

ABRAZOS LLENOS DE GRACIAS 
 
EDGAR

---

