---
title: "Dilema con VirtualBox y hardware M-Audio"
date: 2011-05-10
forum: Software
---

### Post by silex89 on 2011-05-10
Que tal gente! :D, soy noob en el foro así que me presento: Me llamo Daniel, estudio Ingeniería Civil Industrial y he usado ubuntu desde Dapper Drake (cuando tenía 15 años).

En fin, voy al meollo del asunto: Me compré una laptop nueva, un Acer Aspire 4552, AMD Athlon ll X2, ATI Mobility Radeon HD 4250 y 320 GB de disco duro. Soy aficionado a la música así que naturalmente tenía mi Windows 7 con todas las herramientas de edición (Cubase, Guitar Rig, Waves Diamond, Vegas Pro 10 bla bla bla). Todo iba bien hasta que un virus dejó inservible a mi computador. Frustrado instalé Ubuntu, sin embargo no quería alejarme de las aplicaciones que uso habitualmente, y como tengo un poco de experiencia sé que plataformas de audio de ese tipo no funcionan sobre Wine ni Cedega ni Crossover. Me propuse emular sobre VirtualBox un Windows XP en el cual pudiera hacer correr todos las aplicaciones de audio. Instalé el guest additions de la VB y todo corre espectacular, hasta le di acceso a mis concentradores de USB, ahora es cuando todo va mal.

El problema surge cuando conecto mi M Audio Fasttrack Pro (que en ubuntu es plug&play, utiliza un usb 1.1) e inicio Cubase para grabar. Mientras use la tarjeta de sonido integrada no hay problema, todos los sonidos de sistema van Ok y cuando grabo con el driver genérico también, pero cuando cambio a usar la fasttrack o no suena o suena un ruido tipo MIDI estridente, es comparable al ruido que solía hacer el Win98 cuando el banco de sonido estaba ocupado y uno iniciaba otra aplicación que requería de sonido... no sé cómo explicarlo bien...

Imagino que es un tema de soporte de drivers... no sé si existirá una solución, la detección y la instalación de todos los drivers es correcta, según los medidores del secuenciador de Cubase 5 todo está correcto, pero el ruido que sale por los audífonos es.... bueno, ya entienden la idea...


Ojalá puedan ayudarme, no quiero tener que crear una partición y meterle windows otra vez a mi máquina.... estoy aburridísimo de los virus...


Saludos :)

---

### Post by bonzini on 2011-05-10
Hola Daniel, desde Vancouver Canadá, al otro lado de la Ruta 5 Sur.  Hay unos años después mi última visíta a Osorno...

Lo que me preocupa es, podrías utilizar otros programas Linux y no los de Windows en Wine / Virtual Box para hacer tu música?

Por ejemplo, hay Ubuntu Studio...

En mi experiencia, si se encuentra problemas con software de Windows operando en Wine / soluciones de virtualización, es el tiempo para explorar soluciones de Linux.

---

### Post by silex89 on 2011-05-10
Ya lo intenté :(.

Debo reconocer que Ubuntu Studio trae muy buenas utilidades para masterizar temas acústicos (JAMin, Mixxx entre otras) y buenos secuenciadores también (Ardour y Rosegarden); la barrera que me impidió seguir usando esa distro es que el driver JACK que usa para el I/O de datos de audio es hmmm.... "inapropiado?" quizá para la Fasttrack. Con el driver de windows no tengo latencia, con JACK, lo mejor que he podido lograr, muestreando 64 bits es 15 ms (con el muestreo tan bajo tengo mucho ruido blanco y la latencia es alta; léase latencia como el tiempo que tarda en llegar el sonido de la línea hasta tus audífonos después de procesarse).

Otro problema que tuve fue al tratar de enlazar Rakarrack (herramienta de modelado de sonido de guitarra) a la entrada/salida de audio de mi interfaz, no todas las entradas y las salidas estaban listadas cuando la probé, esos programas de modelado son escenciales para mi porque el 95% de las cosas que grabo, las grabo directo por línea, aún no hay platita como para comenzar a grabar de formamás profesional, de forma acústica (en cuyo caso, ubuntu studio va pintadito para mi :D)


Saludos por allá :D

---

### Post by bonzini on 2011-05-10
Ok lo entiendo.... pero pensando un poco... software para Windows sobre Windows sobre Virtual Box sobre Ubuntu.... para hacer algo casi real-time...

Eso no me parece una solución a tus problemas de virus.

Porque no preguntar en Launchpad - como llegar a una solución de latencia minimal en Jack por ejemplo?

---

### Post by bonzini on 2011-05-10
Perdón otra idea - podría ser un kernel "low latency" para tu hardware, probablemente en un ppd en Launchpad también.

O quizás algo de configuración del ambiente real-time.  Eso no es mi especialidad :-)

---

