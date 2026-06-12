---
title: "Pulseaudio dudas, opinen."
date: 2008-04-20
forum: Software
---

### Post by MeduZa on 2008-04-20
Hola gente, instale el hardy beta, realmente asombroso, mejoro un 30% la velocidad del sistema con la instalacion box, la verdad que muchas mejoras y cosas nuevas (como lo de la papelera que me hizo ir a google)
por otro lado mirando las cosas que carga vi este demonio llamado pulseaudio, y me puse a buscar informacion de el, realmente no entiendo para que me serviria a mi, y encima me trae problemas (algunos programas no me fuiniona el audio como es el avidemux) y no voy a poner un server de audio ni me interesa que otras maquinas escuchen lo que sale de mi pc.
Yo tengo una sound blaster audigy 2 y siempre me sono todo de diez, tiene aceleracion por hardware o llamemoslo DSP (digital sound processor) lo que hace que todo lo que tenga que ver con audio sea relegado a la placa de sonido por los drivers ALSA.
Segun veo este paquetito "pulse audio" pareciera ser una capa entre las aplicaciones y alsa. que intenta hacer todo eso por software, cosa que no me gusta y que solo le serviria a la gente que tiene placas onboard que no tienen DSP.
Alguno que entienda del tema y comente si es necesario o si lo puedo quitar, de momento lo estoy por quitarlo para ver que sucede.

Saludos.

---

### Post by clasificado on 2008-04-20
eeeee si. no. mas o menos. (Antes que nada, ¿tenes ubuntu o kubuntu?)

Para ubuntu, Pulseaudio reemplaza al ya "difunto" ESD. Pulseaudio tampoco es perfecto, pero viste como es la cosa: Pasa el tiempo y la gente trata de hacer las cosas para mejor.

Por lo que, si antes no te molestaba tener al daemon de ESD al lado de ALSA, ahora no deberia de molestarte el Pusleaudio.  En el principio de los tiempos, Ubuntu no venia con nada mas que ESD y la gente se quejaba de que los sonidos salian de a uno a la vez. Entonces iban y se instalaban ALSA.

De hecho, si lo sacás te vas a quedar sin ESD ni Pulseaudio, y a gnome le gusta bastante ESD como para poder sacarlo asi como asi, podes tener algunos problemas. Es cuestion de probar, creo yo. 

Es que en cuestiones de sonido, Linux nunca estuvo realmente en una muy buena posición. Desde que se decidió que el viejo servidor OSS ya necesitaba un reemplazo, salieron servidores de sonido hasta por debajo de las piedras: ALSA, JACK Audio Connection Kit, aRtsd, NAS, ESD, xine, y por último PulseAudio porque se me gasta el teclado.

Ahora se hicieron quince millones de programas que se reparten entre todos los servidores de sonido. Como todos tienen muy buenas intenciones, intentan por fuerza bruta hacerse compatibles todos con todos haciendo plugins y mas plugins, pero a veces no les sale tan bien. Entonces terminas teniendo un GStreamer colado encima de Pulseaudio que emula a un ALSA.

En serio, si te anda bien el sonido es por una suma de casualidades.

Pulseaudio es la "ultima" de las ideas, y aparentemente va bastante bien. Yo lo he probado bastante y al final me gusta mas.

Mirá, acá te dejo un mapa que nos proporcionan los muchachos de wikipedia para que veas que tan mal está el asunto

[Link al mapa]("http://upload.wikimedia.org/wikipedia/commons/1/14/Pulseaudio-diagram.png")

* De momento, la funcionalidad a la que le saco mas jugo es la de Per-application volume controls, de tal forma puedo silenciar a los browsers y los flash que contienen para que no molesten la armonia de mi musica trash metal :P

clasificado

---

### Post by leo_rockway on 2008-04-20
> **clasificado said:**
> Desde que se decidió que el viejo servidor OSS ya necesitaba un reemplazo

Esto se debió a que en su momento OSS se volvió propietario.[0]

> **clasificado said:**
> para que no molesten la armonia de mi musica trash metal :P

¡Aguante!

[0] [http://en.wikipedia.org/wiki/Open_Sound_System#Free.2C_proprietary.2C_free](http://en.wikipedia.org/wiki/Open_Sound_System#Free.2C_proprietary.2C_free)

---

### Post by ariel on 2008-04-21
> **MeduZa said:**
> Hola gente, instale el hardy beta, realmente asombroso, mejoro un 30% la velocidad del sistema con la instalacion box, la verdad que muchas mejoras y cosas nuevas (como lo de la papelera que me hizo ir a google)
por otro lado mirando las cosas que carga vi este demonio llamado pulseaudio, y me puse a buscar informacion de el, realmente no entiendo para que me serviria a mi, y encima me trae problemas (algunos programas no me fuiniona el audio como es el avidemux) y no voy a poner un server de audio ni me interesa que otras maquinas escuchen lo que sale de mi pc.
Yo tengo una sound blaster audigy 2 y siempre me sono todo de diez, tiene aceleracion por hardware o llamemoslo DSP (digital sound processor) lo que hace que todo lo que tenga que ver con audio sea relegado a la placa de sonido por los drivers ALSA.
Segun veo este paquetito "pulse audio" pareciera ser una capa entre las aplicaciones y alsa. que intenta hacer todo eso por software, cosa que no me gusta y que solo le serviria a la gente que tiene placas onboard que no tienen DSP.
Alguno que entienda del tema y comente si es necesario o si lo puedo quitar, de momento lo estoy por quitarlo para ver que sucede.

Saludos.


Por si no lo notaste, con pulseaudio por primera vez es posible estar escuchando tu musica favorita con audacious o escuchando un stream de radio o tv con VLC, y a la vez navegar a youtube o cualquier pagina con contenido multimedia y tener sonido. Lo mismo si tenias varias maquinas virtuales VBOX, solo una podia tener audio. Antes, incluso los sonidos del sistema se perdian en esos casos.

Solo por eso ya vale la pena. Si ademas contas la calidad del mixer de pulseaudio que es mucho mejor que los mixers legacy, y en ultimo lugar la posibilidad de remotizar audio (que sumado a los displays remotos de X, te da una solucion completa para terminales). 

pulseaudio esta buenisimo desde cualquier punto de vista. como todo, va a tomar un tiempito aprender a usarlo. Yo lo estoy usando desde hace dos meses y parece muy solido, nunca se pianto.

---

### Post by pol666 on 2008-04-21
Antes que nada:

LA placa es uan porqueria. Yo la uso y me da millones de problemas en ubuntu Gutsy.. Siempre que reinstalo me olvido como hacerla andar. (N)

Ahora voy a instalar Hardy si me da quilombos la placa a la bolsa vuelvo a Gutsy

---

### Post by spg76 on 2008-04-22
Una pequeña recomendación, para controlar el audio de diferentes aplicaciones con PulseAudio pueden instalar PulseAudio Volume Control con:
```
sudo apt-get install pavucontrol
```
No entiendo porque no viene instalado de manera predeterminada teniendo que es una de las mejoras características de PulseAudio.
Incluso, estaría bueno que se pueda acceder desde el applet de volumen lo que lo haría más útil.
Voy a ver si alguien lo sugirió en [Ubuntu Brainstorm]("http://brainstorm.ubuntu.com"), si no es así lo agrego.

EDIT= Recién descubrí PulseAudio Device Chooser que es un applet que permite acceder desde el area de notificación a las preferencias de PulseAudio. Pueden instalarlo con:
```
sudo apt-get install padevchooser
```

---

### Post by MeduZa on 2008-04-22
> **ariel said:**
> Por si no lo notaste, con pulseaudio por primera vez es posible estar escuchando tu musica favorita con audacious o escuchando un stream de radio o tv con VLC, y a la vez navegar a youtube o cualquier pagina con contenido multimedia y tener sonido. Lo mismo si tenias varias maquinas virtuales VBOX, solo una podia tener audio. Antes, incluso los sonidos del sistema se perdian en esos casos.

Solo por eso ya vale la pena. Si ademas contas la calidad del mixer de pulseaudio que es mucho mejor que los mixers legacy, y en ultimo lugar la posibilidad de remotizar audio (que sumado a los displays remotos de X, te da una solucion completa para terminales). 

pulseaudio esta buenisimo desde cualquier punto de vista. como todo, va a tomar un tiempito aprender a usarlo. Yo lo estoy usando desde hace dos meses y parece muy solido, nunca se pianto.

gracias por la respuesta, parece que estoy en un mundo distito o tengo demaciada suerte
desde que uso linux escucho TODAS LAS APLICACIONES de audio a la vez, nunca tuve problemas ni de volumen ni de ruidos ni de nada, incluso cuando usaba la porqueria de la onboard que la saque porque la calidad de audio no solo era mala sino que los canales (7.1 LoL) salian por donde se le cantaba a la onboard.

Nunca use ESD, desde que tengo ubuntu y me anime a compilar mi propio kernel tengo ALSA y mi driver y nada mas, y todo anda en perfecta armonia.

De todas maneras tu post me puso al tanto de como era la cosa, y quite el pulse audio y ahora me anda todo de nuevo, quite los paquetes y los arranques, TODO, me quedo la pc como antes y ya soy feliz jajaajaj

un saludo y gracias por la exceleten respuesta.

PD:antes salia que distro estabas usando arriba a la derecha :P

---

### Post by MeduZa on 2008-04-22
> **pol666 said:**
> Antes que nada:

LA placa es uan porqueria. Yo la uso y me da millones de problemas en ubuntu Gutsy.. Siempre que reinstalo me olvido como hacerla andar. (N)

Ahora voy a instalar Hardy si me da quilombos la placa a la bolsa vuelvo a Gutsy

no se cual tenes vos pero a mi CERO, problemas, todo de una andando incluso desde el liveCD, no se ra la mejor placa pero tampoco es como una porqueria de esas onboard.

Antes de esta tenia un live 5.1, y tambien andaban de 10

---

### Post by pol666 on 2008-04-22
> **MeduZa said:**
> no se cual tenes vos pero a mi CERO, problemas, todo de una andando incluso desde el liveCD, no se ra la mejor placa pero tampoco es como una porqueria de esas onboard.

Antes de esta tenia un live 5.1, y tambien andaban de 10



:shock: NO PUEDO CREER lo que me decis 
 
lo mio es un parto.. me privaria de instalar otra distro o updatear por que se que el problema va a ser esa placa.

Y esto de pulceaudio no me gusto nada quiero seguir con mi alsa y con mi oss y que me dejen tranquilo :(

---

### Post by clasificado on 2008-04-22
> **pol666 said:**
> :shock: quiero seguir con mi alsa y con mi oss:(

De eso se trata linux!

No hay que estar necesariamente en "la última" sino estar donde cada uno le es cómodo.

Hasta te podés lucir diciendo "Con alsa estoy joya y le saco todo el jugo a mi pc, esa de pulseaudio no me vá" :mrgreen:

Después de todo, las actualizaciones de Fiesty van a durar por 18 meses todavia, están los paquetes backported, y después de eso, podés hacer las actualizaciones vos personalmente, no es como para dejar una clavícula por eso.

Es un lujo que con Windows no te podés dar: No solamente le podés agregar cosas que te gustan, _sino sacarle las que no_

clasificado.

---

### Post by MeduZa on 2008-04-22
> **pol666 said:**
> :shock: NO PUEDO CREER lo que me decis 
 
lo mio es un parto.. me privaria de instalar otra distro o updatear por que se que el problema va a ser esa placa.

Y esto de pulceaudio no me gusto nada quiero seguir con mi alsa y con mi oss y que me dejen tranquilo :(
decime que placa tenes bien y te doy una mano, si tenes una audigy 2 no necesitas OSS (lo emulas con el alsa para las aplicaciones viejas)

yo la primera vez compile los drivers alsa como modulo pero ahora los compilo directamente dentro del kernel, AUNQUE no es necesario porque vienen unos que andan bien sin tocar nada.

Decime que placa tenes bien bien asi te doy una mano porque a mi me anda marabillosamente, es mas no sabia que a los demas les andaba un solo sonido a la vez (el alsa si detecta qeu la placa no tiene mixer por hard usa un plugin que mescla todo "en las onboard por ejemplo"

Saludos

---

### Post by pol666 on 2008-04-23
no creo que tengo la Audgy 1.   despues me fijo igual te pregunto, que paquetes bajo?

(desde ya que por defecto no tengo sonido cuando instalo),

---

### Post by MeduZa on 2008-04-23
> **pol666 said:**
> no creo que tengo la Audgy 1.   despues me fijo igual te pregunto, que paquetes bajo?

(desde ya que por defecto no tengo sonido cuando instalo),

interesante !! la audigy 1 usa el mismo driver que la mia.

pone esto y despues pasamos a "paquetes"

cat /proc/asound/cards
y
cat /proc/asound/pcm 
para ver de que es capaz tu placa.

---

### Post by atari130xe on 2008-08-24
Uyyy este post se me "pasò" :lolflag: (estaba en plena mudanza y no tenia internet). Meduza a mi con PulseAudio me va mal, simplemente MAL. Mi PC tiene buen sonido pero solo de a una aplicaciòn a la vez. Instalè Ubuntu en 3 PC`s diferentes y en las 3 con configuraciones diferentes no pude obtener los benditos sonidos simultaneos.

PC1: Chip AC97 Integrada - En Gustsy de 10, en Hardy un drama.
PC2: PCI Genius SoundMaker Value 5.1, en Gutsy bien, en Hardy idem que la PC1.
PC3: Realtek Integrada - no la probè con gutsy pero en Hardy el mismo problema.

¿Coincidencia? o ¿algo no funciona como deberia en la v8.04? Si hay alguien que posteò muchas cosas con referencia al sonido ese fuì yo :(. Lo ùnico que deseo es tener la suerte de contar con la version 8.10 funcionando sin entrar a desmantelar y toquetear el sistema como lo vengo haciendo hasta ahora.

Por Ej.: En la "PC3" desinstalè por completo PulseAudio y las aplicaciones (no importa la cantidad que abra) funcionan perfecto pero me quedè sin sonidos de sistema, parece ser un problema de Gnome y ESD. En la PC2: Hice lo mismo pero "milagrosamente :confused: " funcionan las aplicaciones y los sonidos del sistema. 

Cosas de la informàtica... :lolflag:

---

### Post by pol666 on 2008-08-24
no te se decir con las demas pero yo tengo una  Realtek Integrada que al tengo deshabilitada pero anda eh...

Pülseaudio esta muy bueno una vez que le agarras la mano es una masa.. En 2seg tengo sonido 5.1 y multisound

---

### Post by atari130xe on 2008-08-24
> **pol666 said:**
> no te se decir con las demas pero yo tengo una  Realtek Integrada que al tengo deshabilitada pero anda eh...

Pülseaudio esta muy bueno una vez que le agarras la mano es una masa.. En 2seg tengo sonido 5.1 y multisound

Esta bueno cuando sabès a donde "meter mano" cosa que no deberia ser asi, o sea algo esencial como el sonido en un SO es INSTALAR Y USAR asi lo entiendo yo, soy muy curioso y vivo metiendo mano en mi pc y luego de un problema del cual no veia como salir reinstalè muuuchas veces pero que se yò me resisto a pensar que a otras personas le pase lo mismo y que en launchpad me hayan respondido esto:

> shane fagan proposed the following answer:
I presume they are it is a bad enough problem.
I think you can pick alsa instead if you want to get back the multiple sounds.

Hope that helps
Shane Fagan


a pocas palabras buen entendedor....

---

### Post by victor_nesta on 2008-08-25
atari130xe puede que tengan mi problema?
Fijate capaz que es esto..
[SOLVED] Reproducir 2 sonidos a la ves en Ubuntu. Se puede?
[http://ubuntuforums.org/showthread.php?t=885458](http://ubuntuforums.org/showthread.php?t=885458)

Mi Audigy causaba problemas pero lo solucione gracias a pol666

---

