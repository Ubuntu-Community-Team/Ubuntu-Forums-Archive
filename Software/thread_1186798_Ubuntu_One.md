---
title: "Ubuntu One"
date: 2009-06-13
forum: Software
---

### Post by Apipote on 2009-06-13
Hola estimados.

Interesante Ubuntu one.

Tips and tricks por favor?

Gracias por adelantado.

---

### Post by majatu on 2009-06-13
Buenas, la verdad que Ubuntu One esta bueno, es igual que [Dropbox]("http://www.getdropbox.com/"), lo unico malo es que solo funciona bajo Ubuntu (no se si se lo pude hacer andar en otras distros), entonces no podes sincronizar pcs con Windows o Mac, por lo que me quedo con Dropbox que es multiplataforma y ademas si invitas a tus amigos podes llegar a tener hasta 5gb de espacio gratuito.

En mi opinion es como que esta muy verde todavia, hay que ver que pasará! jeje

Saludos!

---

### Post by juancarlospaco on 2009-06-13
Justamente para mi es una ventaja que no tenga Cliente en Windows, no quiero Virus en mi UbuntuOne.
Si tubiera Cliente para Mac no me molestaria.
SkyDrive tampoco tiene cliente para Ubuntu, 
Gdrive tampoco tiene cliente para Ubuntu.

Lo bueno es que podes compartir cosas con otros Ubuntu, 
y pueden trabajar con los mismos archivos que estan en "Shared with Me".

Yo puse como feature missing que la interfaz web sea multi-lenguaje,
que pongan el HTML en Lauchpad y lo traducimos, 
me contestaron en menos de 24hs que la idea fue aceptada 
y quedo en cola junto con otras.

Ojo si usan Back In Time, 
si restauran las carpetas del UbuntuOne se mama la sincronizacion,
ya le avise al autor de Back In Time pero no me dio mucha bola.

Funciona perfecto, 
rapido sincroniza solo lo que cambio,
seguro con encriptacion SSL.

---

### Post by r@fitiiixxx on 2009-06-15
> **juancarlospaco said:**
> Justamente para mi es una ventaja que no tenga Cliente en Windows, no quiero Virus en mi UbuntuOne.
Si tubiera Cliente para Mac no me molestaria.
SkyDrive tampoco tiene cliente para Ubuntu, 
Gdrive tampoco tiene cliente para Ubuntu.

Lo bueno es que podes compartir cosas con otros Ubuntu, 
y pueden trabajar con los mismos archivos que estan en "Shared with Me".

Yo puse como feature missing que la interfaz web sea multi-lenguaje,
que pongan el HTML en Lauchpad y lo traducimos, 
me contestaron en menos de 24hs que la idea fue aceptada 
y quedo en cola junto con otras.

Ojo si usan Back In Time, 
si restauran las carpetas del UbuntuOne se mama la sincronizacion,
ya le avise al autor de Back In Time pero no me dio mucha bola.

Funciona perfecto, 
rapido sincroniza solo lo que cambio,
seguro con encriptacion SSL.

es una buena explicación, pero yo no tengo ni idea de lo que es, y me a surgido la duda, que diferencia hay con montar un FTP publico? (como el de Gnome Menu [panel] > Lugares > Conectar con el Servidor...)

también e leido por ahí que el software del servidor está cerrado y es privativo, y he leido comentarios malos departe de la gente que opina que es una mala jugada de canonical y que esas cosas no se olvidan...
tan grave es?, piensan liberar el codigo en algun momento o va a quedar asi? (solo curiosidad)

a la parte del programa, es una interfaz grafica en una pagina web o es un programa separado del explorador de internet o algo así? y vos podes entrar como si fuera un Flash drive o una tarjeta de memoria?, como es eso de las invitaciones? donde puedo conseguir una?, fotos de la cosa andando? (aunque sea links de otras paginas o blogs)
--------------------
yo creo que todo esto va en el mismo thread porque son preguntas que cualquiera que entre y vea el titulo y no sepa que es porque recien acaba de leer el post puede que no vea una descripción de que es y para que sirve y como hace lo que hace, seguro va a preguntarse todo eso, son muchas preguntas pero apuntan a un mismo tema (aviso nomas porque si no despues lo que pongo esta mal)

---

### Post by juancarlospaco on 2009-06-15
Lo que es..., es un sistema de sincronizacion con unos servidores en internet,
que no existen fisicamente, y probablemente nunca existan fisicamente,
que tiene un cliente Open Source escrito en Python, que incluye 1 Demonio,
que a juzgar por lo que pienso yo *[SIZE="1"](puedo estar equivocado)[/SIZE]*,
levanta un tunel Cifrado SSL*[SIZE="1"](la palabra encriptado no existe realmente)[/SIZE]*,
y sincroniza nuestra carpeta en ese servidor,
usando algun tipo de RSync sobre SSL o version modificada/similar a este,
asi mismo al *"Registrar"* el cliente en ese servidor para esa cuenta,
genera un Hash con un logaritmo que tiene, 
para que sea como *"un DNI"* de ese equipo para esa cuenta,
entonces tambien sincroniza el resto de los equipos registrados,
ejemplo cada vez que modificas algo en la carpeta de UbuntuOne en la Notebook,
la mofidicacion se refleja en la Desktop de tu casa automatico.
La carpeta de UbuntuOne es:
$HOME/Ubuntu One/

Gracias al Hash puedes tener varias cuantas de UbuntuOne en un mismo equipo,

Gracias a que es *[SIZE="1"]tipo-[/SIZE]*RSync solo se trasmite por la red el Delta, 
o lo que se modifico, consumiendo muy poco ancho de banda.

Gracias al SSL es Seguro, esta Cifrado*[SIZE="1"](mal dicho encriptado)[/SIZE]*, 
si NO fuera asi, te agarran con un WireShark o un Driftnet nomas 
y te sacan todos tus datos personales.

Asi mismo lo que nadie menciona es un metodo Seguro de compartir cosas entre Ubuntu y Ubuntu,
dos usuarios pueden trabajar con los mismos archivos, 
invitarse a carpetas compartidas muy facilmente,
los archivos no se bloquean, solo se trasmite lo que se modifico.


Un FTP publico no tiene la capacidad para trasmitir unicamente el Delta de los datos,
o sea no puede trasmitir unicamente aquellos Bytes que fueron modificados,
un ejemplo mas simple, abriste un .odt de 500 paginas, 
le escribiste la fecha en la primer pagina,
el FTP debera trasmitir todas las 500 paginas completas por la red,
sobreescribiendo el archivo original al vuelo,
y bloqueando el archivo hasta que finalize la transferecia de datos.
Asi mismo un FTP no te va a hacer lo que te decia, 
de sincronizar multiples cuentas, en multiples equipos, 
con minimo consumo de ancho de banda, y todo automatizado,
el solo entiende de USER y PASSWORD.
Es seguro, es TCP, es con autenticacion, 
es relativamente rapido, pero UbuntuOne puede ir mas alla.

Pero si, como poder podes, montarte un FTP publico,
Ubuntu te provee todas las herramientas y documentacion,
pero vas a necesitar un hardware interesante si queres hacerlo bien realmente, 
UPS, RAID de discos, Servidores de Backup, DSL simetrico, blah, blah.


El software del servidor está en la Nube E3 de Amazon,
no existen servidores de UbuntuOne,
Amazon tengo entendido que no deja que se libere el codigo fuente,
y Canonical, hoy por hoy, 
andaban ocupados en Liberar todo el codigo fuente de Launchpad.
Canonical no tiene la escalabilidad necesaria para usar sus propios servidores.

Yo tambien he leido comentarios malos de parte de gente ignorante,
que opina que es una mala jugada de canonical, 
tenes que tomar como parte de quien viene, 
hay mucha envidia por el triunfo de Ubuntu,
de que sea usado por Google, de que sea vendido instalado en las Dell,
y demas cosas asi que hacen que la gente involucrada en otros sistemas pagos,
algunos relacionados con Linux, otros con Microsoft o Apple les de bronca,
sucede que los Trolls y la Sincronizacion contra Nubes no son compatibles,
pero esas personas ignorantes probablemente nunca hallan leido una Licencia completa,
por ejemplo[ la Licencia GNU Affero GPL:]("http://www.affero.org/oagpl.html")

```
[SIZE="1"]The GNU General Public License does an excellent job of protecting freedoms for users and developers, but there are questions about the applicability of the license for software that is run over a network.

Since Affero's software is run over a network, and since we believe that the freedom should be fully protected, we have decided to publish yet another license.

You will find it nearly identical to the GNU GPL, with an addition of section 2 (d), which covers use of the software over a computer network. We're sorry for the inconvenience of another license.

And yes, we did get permission to use the GNU GPL as the basis for this license;)[/SIZE]
```
Puedes ver como esa Licencia GNU avala el sistema.



La parte del programa...
Si, es una interfaz grafica en una pagina web,
Si, es un programa separado del explorador de internet, integrado al Nautilus,
Si, vos podes entrar como si fuera un Pendrive o una tarjeta de memoria, 
Te podes Auto-Invitar desde la web de Ubuntu One,
tambien te pueden invitar los que ya tienen Ubuntu One *[SIZE="1"](en este caso tiene mas prioridad creo)[/SIZE]*,
Podes hacerte una[ en este link,]("https://ubuntuone.com/")


Fotos de la cosa andando:

[IMG]http://img23.imageshack.us/img23/2567/ubuntu1.jpg[/IMG]

La cosa andando en la desktop de casa.



**[COLOR="Blue"]TIP:[/COLOR]**
Para los que quieran mas Seguridad todavia..., 
usen SeaHorse para Firmar y Cifrar sus archivos en Ubuntu One, 
que Ubuntu para eso tiene su servidor de llaves PGP *(keyserver.ubuntu.com)*
Click derecho sobre el archivo--->Cifrar...
Guarden un backup en un lugar seguro de sus llaves privadas, 
y suban las publicas al servidor.


:D

---

### Post by Apipote on 2009-06-15
Bien Juan !!!

---

### Post by r@fitiiixxx on 2009-06-15
@juancarlospaco:

 Muchisimas gracias juan, la verdad has echo un review mas que interesante y me sacaste muchas dudas, yo había buscado por internet pero como dije en mi post, eran comentarios que no explicaban y se sentraban en lo que pasaba con respecto a canonical.

hay varios terminos que no entendí de primera (soy novato) pero que releyendo un poco pude entender todo.

y yo también creía que era poco probable que canonical hiciera algo así, pero bueno siempre mejor comentar las dudas.

solo no entendí una cosa> ...El software del servidor está en la Nube E3 de Amazon,
no existen servidores de UbuntuOne, ...

como es eso de la Nube E3? he googleado un poco pero es algo que no entendí, igual voy a seguir googleando,
hasta ahora encontré este pobre link:

[http://www.dreig.eu/caparazon/2008/10/30/¿que-es-el-cloud-computing-definicion-tendencias-y-precauciones/](http://www.dreig.eu/caparazon/2008/10/30/¿que-es-el-cloud-computing-definicion-tendencias-y-precauciones/)

salu2 ):P

---

### Post by juancarlospaco on 2009-06-15
Un Cluster de Servidores Fisicos en un Data Center,
ejecutando un software de computacion en Nube para procesamiento On-Demand,
[aca se puede ver la web de Amazon.]("http://aws.amazon.com/")

No es una maquina fisica individual, ningun servidor tiene el sistema en si mismo.
No es una maquina virtual individual, es un sistema distribuido de computacion.

Algo similar al Eucalyptus de Ubuntu Server.
:)

---

### Post by z37a on 2009-06-15
que suerte tienen algunos, hace tiempo solicite una invite para este nuevo servicio, y sigo esperando!!!! Quiero probarlo!!!!!!

---

