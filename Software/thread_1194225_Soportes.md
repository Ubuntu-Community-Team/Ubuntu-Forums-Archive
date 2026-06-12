---
title: "Soportes"
date: 2009-06-22
forum: Software
---

### Post by Vero1 on 2009-06-22
Hola a todos,

Hace unos días instalé Jaunty pero no me detecta mis grabadoras de CD y CD/DVD, motivo por el cual no puedo copiar el contenido de un DVD que hice de respaldo de archivos que me interesaba conservar de Intrepid.

Me han comentado que posiblemente sea que el fstab está mal, así que les envío un paste del mismo.

[http://pasto.elefantesrosas.com.ar/pastos/view/26/fstab](http://pasto.elefantesrosas.com.ar/pastos/view/26/fstab)

El único que está reconocido y montado es el floppy.

Las dos grabadoras figuran en Equipo, pero si trato de montarlas me sale una ventanita que indica que no se puede montar ni el lugar ni los archivos.

Por lo tanto no puedo usar el DVD correspondiente.

Agradeceré me orienten sobre qué debo hacer.

Saludos.

---

### Post by juancarlospaco on 2009-06-22
Una pavada pero... si poes un CD ya grabado, no aparece un icono nuevo en el escritorio?

---

### Post by Vero1 on 2009-06-22
Hola,

No, no aparece nada.

saludos

---

### Post by juancarlospaco on 2009-06-22
si cambias:
**noauto**
por:
**auto**
?

Ademas los mountpoint estan mal, 
por decirlo a lo bruto esta queriendo meter el DVD adentro del CD.
**mkdir --verbose /media/cdrom0 ; mkdir --verbose /media/dvdrom0**

---

### Post by Vero1 on 2009-06-22
Si te fijás primero dice auto y despues noauto.

Pero hay algo que no entiendo(entre tantas cosas). 
Acabo de hacer lshw y allí aparece tanto el cdrom como el cd/dvd pero sin puntos de montaje y justamente usè el comando mount /dev/scd1 y me contesta que no hay punto de montaje. Tampoco lo tiene el CD.

Hice lo de tu comando y me contesta:

mkdir: no se puede crear el directorio «/media/cdrom0»: El fichero ya existe
mkdir: no se puede crear el directorio «/media/dvdrom0»: Permiso denegado

Pero hice ésto:
veronica@veronica-jaunty:~$ sudo mkdir --verbose /media/dvdrom0
[sudo] password for veronica: 
mkdir: se ha creado el directorio «/media/dvdrom0»

y ahora?

gracias

---

### Post by juancarlospaco on 2009-06-22
Si lo analizamos con atencion el fstab nos comenta amablemente que:
**/media/cdrom0/dvdrom0**
o sea, esta queriendo montar el DVD adentro del CDrom :)
*una mamuska de unidades jeje*

Asi seria la cosa:
[B]/dev/scd0 /media/cdrom0 
/dev/scd1 /media/dvdrom0[/B]

---

### Post by EnriqueK on 2009-06-22
Yo tengo 2 grabadoras de DVD instaladas y funcionan bien, el caso es que en mi fstab solo figura una de ellas y tiene la siguiente linea que es idéntica a la que figura en el tuyo
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Por esta razón es que en el otro hilo te sugerí que comentes con # la linea 17 en donde claramente está errada, o sino probá con poner esta otra linea
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by Vero1 on 2009-06-22
EnriqueK,

Lamentablemente no funcionó.

Paco,

Gracioso lo de las mamushkas:D

pero tampoco funcionó.

La verdad es que Jaunty me está trayendo problemas...

Gracias por su buena voluntad. 

No sé qué puedo hacer :-(

saludos

---

### Post by guillermolisi on 2009-06-23
> **Vero1 said:**
> EnriqueK,

Lamentablemente no funcionó.

Paco,

Gracioso lo de las mamushkas:D

pero tampoco funcionó.

La verdad es que Jaunty me está trayendo problemas...

Gracias por su buena voluntad. 

No sé qué puedo hacer :-(

saludos
Cuando pasan este tipo de situaciones la consola/terminal es una muy buena amiga.

Que pasa cuando intentas montar un CD/DVD a mano con el comando mount ? (si te dice "solo root puede montar" le antepones sudo).

---

### Post by Vero1 on 2009-06-23
Hola guillermolisi,



me contesta lo siguiente sin root:

mount: dispositivo de bloques /dev/sr0 está protegido contra escritura; se monta como sólo lectura
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       En algunos casos se encuentra información en syslog, pruebe
   dmesg | tail   o algo parecido

no me importaría,en este caso, que se montara solo como lectura, ya que contiene archivos que guardé de Intrepid, como .evolution y .mozilla y html de marcadores de firefox., para pasarlos a Jaunty.

Si corro dmesg | tail, me dice:

  362.646558] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  362.646564] sr 1:0:0:0: [sr0] Add. Sense: Id CRC or ECC error
[  362.646571] end_request: I/O error, dev sr0, sector 0
[  370.703995] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  370.704020] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  370.704028] sr 1:0:0:0: [sr0] Add. Sense: Id CRC or ECC error
[  370.704037] end_request: I/O error, dev sr0, sector 4
[  370.704081] UDF-fs: No partition found (1)
[  370.715528] grow_buffers: requested out-of-range block 18446744073709355023 for device sr0
[  370.715535] isofs_fill_super: bread failed, dev=sr0, iso_blknum=-196593, block=-196593

Por supuesto no entiendo qué significa.

Gracias

---

### Post by pablo.s on 2009-06-23
> **Vero1 said:**
> 362.646558] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  362.646564] sr 1:0:0:0: [sr0] Add. Sense: Id CRC or ECC error
[  362.646571] end_request: I/O error, dev sr0, sector 0
[  370.703995] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  370.704020] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  370.704028] sr 1:0:0:0: [sr0] Add. Sense: Id CRC or ECC error
[  370.704037] end_request: I/O error, dev sr0, sector 4
[  370.704081] UDF-fs: No partition found (1)
[  370.715528] grow_buffers: requested out-of-range block 18446744073709355023 for device sr0
[  370.715535] isofs_fill_super: bread failed, dev=sr0, iso_blknum=-196593, block=-196593

Por supuesto no entiendo qué significa.

Gracias

Mmmm, yo si sé lo que
significa... no me atrevo a
contarte.

---

### Post by Vero1 on 2009-06-23
PabloS,

pues si no me contás no me entero:)

Adelante, decime qué pasa por favor.

---

### Post by pablo.s on 2009-06-23
Basicamente, se grabó MAL
el DVD. Siendo un backup,
es de temer que los datos
se hayan perdido. Ahora:
Podés grabar el DVD con los
mismo datos?

---

### Post by Vero1 on 2009-06-23
pablo.s

En realidad no se hizo como un backup si no hice drag and drop.

Por supesto que no puedo grabar nada porque ya Intrepid fue eliminado al instalar Jaunty.

Pero el problema mayor es que Jaunty NO reconoce este soporte, al contrario de Windows que sí lo reconoció. Claro que no lo puede leer... y el hecho de que Jaunty no reconozca el soporte no tendría que ver con que el DVD estuviera mal grabado no?

---

### Post by pablo.s on 2009-06-23
> **Vero1 said:**
> Pero el problema mayor es que Jaunty NO reconoce este soporte, al contrario de Windows que sí lo reconoció. Claro que no lo puede leer... y el hecho de que Jaunty no reconozca el soporte no tendría que ver con que el DVD estuviera mal grabado no?

La mayoria de las veces, si.
Si Windows lo puede leer,
te diria que copies de a poco
la información a la partición
de Windows y la pases.

---

### Post by Vero1 on 2009-06-23
pablo.s

"Windows que sí lo reconoció. Claro que no lo puede leer..."

---

### Post by Vero1 on 2009-06-23
> **Vero1 said:**
> pablo.s

"Windows que sí lo reconoció. Claro que no lo puede leer..."

y otra cosa pablo, el sistema tiene que reconocer a la grabadora y no al contenido, salvo error de mi parte.

---

### Post by pablo.s on 2009-06-23
> **Vero1 said:**
> el sistema tiene que reconocer a la grabadora y no al contenido, salvo error de mi parte.

Tendrias que probar con otro
disco. Una cosa es que te dé un
error con un disco mal grabado
y otra que no reconozca a la
grabadora. Si haciendo "mount"
te trata de montar el disco, o
directamente lo monta, entonces
hay que retocar fstab para que
lo haga automaticamente.
Si insertás un disco y lo monta solo,
entonces no veo el problema.

---

### Post by Vero1 on 2009-06-23
No tengo un disco virgen en mi casa así que esta tarde compro y pruebo a ver si lo monta.

Despues te digo.

Saludos y gracias.

---

### Post by EnriqueK on 2009-06-23
Ya que tenés dos unidades ópticas, probá con arranar con el Live CD y luego ver si en estas condiciones puede reconocer el DVD.

---

### Post by Vero1 on 2009-06-23
EnriqueK,

El LiveCD arranca desde mi unidad vieja de grabadora de CD, pero NO arranca desde la unidad nueva de CD/DVD. Lo que hace es montar el disco que es un CD.

Vos dirás.

saludos

---

### Post by pablo.s on 2009-06-23
Porque el orden de arranque
en la BIOS debe estar como
primera la lectora de CD.
Lo que dice Enrique es que
cargues el LiveCD y una vez
cargado pruebes con poner
un DVD en la grabadora y ver
si lo monta.

---

### Post by Vero1 on 2009-06-23
Bueno arranqué con el LiveCD desde mi lectora de CD y una vez que se cargó puse un DVD en la lectora de CD/DVD pero me sacó el mismo cartelito de siempre: no se puede montar el archivo.

Veo despues qué pasa con un DVD virgen que tengo que comprar y les digo.

---

### Post by Vero1 on 2009-06-23
> **Vero1 said:**
> Bueno arranqué con el LiveCD desde mi lectora de CD y una vez que se cargó puse un DVD en la lectora de CD/DVD pero me sacó el mismo cartelito de siempre: no se puede montar el archivo.

Veo despues qué pasa con un DVD virgen que tengo que comprar y les digo.

Sí en la Bios el orden de arranque comienza con CD. Vos creés que debería cambiar esa opción por CD/DVD?

---

### Post by pablo.s on 2009-06-23
No. No hace falta. Pero cuando
querés que arranque un LiveCD
desde un lectora o grabadora, lo
que tenés que verificar es que 
sea la primera para arrancar en
la lista de discos en la BIOS.
De otra manera no arranca desde
esa unidad. Tiene un orden. Digamos
que el orden de la grabadora de DVD
es el segundo. Para que arranque de
ahi es preciso que en el dispositivo
que está primero en la lista no haya
ningú medio con autoarrranque.

---

### Post by Vero1 on 2009-06-23
Bueno pablo.s

Se develó la incógnita. Compré un dvd virgen y en cuanto lo puse en la grab adora nueva, montó el disco, lo cual me hace pensar que a lo mejor tuviste razón en decir que los dvd no se montan por estar mal grabados, aunque no entiendo bien la conexión que hay porque a primera vista no debería incidir el contenido, pero en fin.
Lo malo de todo esto es que me quedé sin mis correos de evolution y sin otras cositas que tenía, como así tambien sin los marcadores de Firefox.

Ahora, despues de grabar estos dvd, en Intrepid podía ver el contenido, así que no puedo estar 100% segura de que están mal grabados. 

Qué opinás de todo ésto?

---

### Post by pablo.s on 2009-06-23
Lo que te queda es intentar leer
el disco con otra lectora de DVD.
Me ha pasado que discos que era
imposible que me leyera un aparato,
cuando los trataba de ver con otro
por arte de magia se veian perfecto.
Es una posibilidad.

---

### Post by Vero1 on 2009-06-23
Si la idea es buena pero no me serviría de mucho ya que no tengo otra lectora de dvd y si voy a un cyber no puedo usar ese dvd para transferir los datos a los lugares correspondientes que están en mi PC.

Te hago un comentario sobre algo que acabo de recordar.

Entre tantas cosas que he probado, en un momento dado y no sé ahora con qué comando había salido, decía que el dvd solamente tiene permiso de lectura, cosa que no me importaría pues lo que quiero es pasar los datos nada mas.

Te dice algo?

---

### Post by pablo.s on 2009-06-23
> **Vero1 said:**
> Entre tantas cosas que he probado, en un momento dado y no sé ahora con qué comando había salido, decía que el dvd solamente tiene permiso de lectura, cosa que no me importaría pues lo que quiero es pasar los datos nada mas.

Te dice algo?

Si, por supuesto que es solo lectura.
Los medios opticos (CDs, DVDs) solamente
se acceden con permiso de lectura.
Que se puedan grabar no les da permisos
de escritura; por eso en fstab están descriptos
con "ro" que significa "read-only".
Con respecto a que se me ocurre para
recuperar los datos no se me ocurre nada,
aparte que le pidas a alguien que tenga una
lectora de dvd que te deje transferir los
contenidos (si es que los lee). Alguien con
una notebook?

---

### Post by Vero1 on 2009-06-23
Sí, tengo una persona que tiene una notebook pero tiene Windows y ya sabemos que no lee lo grabado en Ubuntu.

Bueno pablo.s, no quiero quitarte mas tiempo. 

Agradezco tu buena voluntad y te saludo.

---

### Post by Mauro22 on 2009-06-23
> **Vero1 said:**
> 

[  362.646558] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  362.646564] sr 1:0:0:0: [sr0] Add. Sense: Id **CRC or ECC error**
[  362.646571] end_request: I/O error, dev sr0, sector 0
[  370.703995] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  370.704020] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  370.704028] sr 1:0:0:0: [sr0] Add. Sense: Id CRC or ECC error
[  370.704037] end_request: I/O error, dev sr0, sector 4
[  370.704081] **UDF-fs: No partition found (1)**
[  370.715528] grow_buffers: **requested out-of-range block** 18446744073709355023 for device sr0
[  370.715535] isofs_fill_super: bread failed, dev=sr0, iso_blknum=-196593, block=-196593


Ahi te habia cantado el error. 

Error CRC (Chequeo de redundacia ciclica). En criollo, la informacion difiere del original, ergo no se puede leer.

No partition found: No hay particion para montar, por eso no monta nada.

requested out-of-range block: Bloque solicitado fuera de rango. Siginifica que la lectora intenta leer un bloque que no esta en el rango de los existentes, provocado por el error fatal de no haber montado uno.


En fin, con el CRC alcanza para perder los datos.

Cuando lo grabaste, le diste verificiar datos grabados??

---

### Post by Vero1 on 2009-06-23
Mauro, ya dí tantas vueltas con este asunto que ni recuerdo qué programa usé para grabar. Lo que sí recuerdo es que no tenía la opción de chequear los datos, despues de grabar.

Ya los doy por perdidos. Tendré que recuperar las direcciones de e-mail.

Por suerte tengo copia de los marcadores de Firefox y eso lo puedo arreglar.

Hay otras cosas que no podré recuperar pero bueno, no tengo alternativa.

Gracias por tus comentarios.

---

### Post by Mauro22 on 2009-06-23
Si lo montara seria otra cosa...

Podrias probar una sarta de soft para recuperar datos...




* Probaste:

```
sudo mount -t iso9660 -o ro /dev/scd0 /media/cdrom0
```

?

(Sabien que /media/cdrom0 existe, sino creala)

y tambien:

```
sudo mount -t UDF -o ro /dev/scd0 /media/cdrom0
```


UDF es el sistema de archivos de win, y por lo que vi hay un bug reportado.[0]


Si es un bug, y la escritura OK, los datos estan salvados. Pero ubuntu no los lee y win tampoco :confused::confused:

Probaria en tantas PC como pudiera y si se puede, VirtualBox.


[0] [https://bugs.launchpad.net/ubuntu/+bug/193017](https://bugs.launchpad.net/ubuntu/+bug/193017)

---

### Post by Vero1 on 2009-06-23
Mauro, no sé si sabes que tengo 2 grabadoras.

1 es CD
1 es CD/DVD

Si edito el fstab dice lo siguiente:

/dev/scd0       /media/cdrom0     udf,iso9660 rw,user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0    auto    rw,user,noauto,exec,utf8 0       0
/dev/scd1       /media/dvdrom1    udf,iso9660 rw,user,noauto,exec,utf8 0 0 

No sé siquiera si ésto está bien o no porque se arregló con indicaciones que he recibido de distintas personas. Sobre todo del último renglón que correspondería a mi lectora nueva.

He probado "ver" los dvd grabados en Windows pero dice que los archivos son desconocidos y no los puede leer.

Si corro el primer comando que me das,correspondería al cdrom y no al cd/dvd, si no me equivoco.

Antes que nada, qué opinás del fstab?

---

### Post by Mauro22 on 2009-06-23
Yo en la notebook tengo 1 solo unidad que es DVD-RW

sin embargo, el fstab me canta:

```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0   0
```


Y funciona todo joya.


si queres, edita el fstab como sudo, comenta (#) la ultima linea y escribi como la que tengo yo.

cambiar el punto de montaje por dvdrom1 ( o el que quieras mientras exista)


Te repito, en el mio dice cdrom pero es dvd-rw, y hasta ahora hace todo bien. lee y graba.

---

### Post by Vero1 on 2009-06-23
ok Mauro, ya comenté la ultima linea y cambié lo que me indicaste.
De todos modos te envío un pastebin de mi lshw donde podés ver ambas grabadoras.

Hay algo que me llama la atención en la grabadora de dvd. Dice dvd-ram.
No debería ser dvd-rom?

[http://pasto.elefantesrosas.com.ar/pastos/view/28/dvd](http://pasto.elefantesrosas.com.ar/pastos/view/28/dvd)

---

### Post by Mauro22 on 2009-06-23
Antes me olvidé:

cuando terminas de editar hace:


sudo mount -a

para volver a montar todas las unidades y despues proba con el dvd...


2) Creo que tenes la misma que tenia en la PC de escritorio y nunca me trajo problemas.

3) DVD RAM son (practicamente) todas, son basicamente dvds que se pueden acceder aleatoriamente :confused:


wikipedia:

Formato de disco DVD regrabable aprobado por el DVD-Forum. Se diferencia del DVD-RW (y del DVD+RW) en que no hace falta borrar todo el disco para recuperar el espacio de los contenidos que deseamos borrar y en que se puede grabar directamente en él cómo si fuera un disco duro, sin necesidad de programas de grabación de DVD, ni de programas controladores intermedios (en el caso de grabadores DVD-RAM para ordenadores).

---

### Post by Vero1 on 2009-06-23
Haga lo que haga sigue la misma respuesta: No se puede montar el lugar o los archivos...

Voy a volver a probar en Win, a ver qué pasa.

Despues te digo.

---

### Post by EnriqueK on 2009-06-23
Nunca tuve un caso así, pero suponiendo que el dcd estuviera mal grabado, esto no debería ser motivo para que no lo pueda montar, en mi opinión esto se puede deber a que la marca del dvd es incompatible con tu quemadora, es raro que esto pase, pero a mi me pasó, te sugiero probar varias cosas.
1- Fijate si el dvd no tiene algún deterioro físico
2.- Buscá la manera de instalar en win el programa Isobuster, si al dvd lo grabaste con las opciones normales, es muy posible que con este programa puesdas extraer los fatos y luego los vuelves a grabar en otro dvd
3.- buscate otra PC y probalo allí.
4.- Decias que al dvd lo grabaste en Intrepid, entonces probá con correr el Live CD de instalación de Intrepid y tratá de correr allí el dvd.

---

### Post by Vero1 on 2009-06-23
Mauro,

Nada que hacer, ni en Ubuntu ni en Windows...

---

### Post by Vero1 on 2009-06-23
EnriqueK,

Da la casualidad que hoy compré otro DVD tambien Verbatim, como el que no se puede montar, pero este dvd que es virgen si se puede montar.

Estoy de acuerdo con vos en que debería poder montarse esté bien o mal grabado, pero se emperra en no poder montarse.

Voy a probar lo que me sugerís y gracias.

Oportunamente te informo.

---

### Post by Vero1 on 2009-06-24
EnriqueK,

Ese programa Isobuster es para leer dvd de imagen, porque yo grabé como datos y no imagen.

---

### Post by Vero1 on 2009-06-24
> **Vero1 said:**
> EnriqueK,

Ese programa Isobuster es para leer dvd de imagen, porque yo grabé como datos y no imagen.

Instalé Isobuster en Windows y el DVD tiene todos los datos que yo grabé.

El único problema que se me presenta ahora es que no puedo grabar en la grabadora de dvd porque aparentemente Windows no lo registra y me manda a la grabadora de CD que, por supuesto, no sirve.

Me fuí a la Bios para ver si registra el dvd y sí lo registra pero entre los soportes extraíbles no aparece...(hablo de MiPC).

Francamente qué de problemas me trae este asunto.

Qué me aconsejas que haga?

Gracias.

---

### Post by EnriqueK on 2009-06-24
Poe lo que entiendo ya has podido extraer los archivos del dvd en win , entoces ya podrás desde Ubuntu entrar a esa partición (dede el menú Lugares) y copiar o mover esos archivos , entonces esto estaría solucionado, a menos que no puedas entrar a esta partición, te quedaría la opción de usar (en win) el programa Winrar para partir esos archivos para que quepan en CDs.
Me da la impresión de que tu problema está en que no te han instalado adecuadamente la grabadora de DVD , sugiero que hagas revisar la instalación de la quemadora y como última opción quedaría reemplazar el lugar que ocupa la grabadora de CDs y poner allí la de DVDs , te quedarías sin la de CDs., pero no es tan grave por que con la DVD tenés suficiente y además los CDs se usan cada vez menos.

---

### Post by Vero1 on 2009-06-25
En Win con Isobuster pude ver los archivos grabados.
Intenté grabarlos en un dvd nuevo y Brasero empezó a grabar, pero llegó un momento en que marcó error. Tengo el log. Te lo envío con paste. A ver qué opinás.

[http://pasto.elefantesrosas.com.ar/pastos/view/31/log.Brasero](http://pasto.elefantesrosas.com.ar/pastos/view/31/log.Brasero)

disculpá tanta lata.

---

### Post by EnriqueK on 2009-06-25
Desfraciadamente no es mi fuerte el entender los logs, pero lo que no me queda claro es si has podido ewataurar ek backup extrayéndolo del dvd desde win, ko que no entiendo es el motivo para querer volver a grabarlo en dvd, el error puede deberse a que los dvd verbatin no son compatibles con tu quemadoram además tengo entendido que hay mucha falsificación, así que te sugiero que uses otra marca de dvd , también te sugerí que pruebes en otra PC a ver como anda la cosa y así vas descartando posibilidades, personalmente opino que si desde win tenés problemas de no reconocimiento de la unidad, es muy probable que tu quemadora fué mal instalada o que esté fallada,  sugiero que la hagas revisar por quien te la instaló.

---

### Post by Vero1 on 2009-06-27
EnriqueK,

No hay problema con la grabadora ya que la probé con otro dvd.

Aclaro que quería volver a grabar lo que deja ver Isobuster para poder grabarlo en Ubuntu y así poder incluir el contenido en los lugares correspondientes o sea en evolution y en home.

Pero no se puede o yo no lo sé hacer. Inclusive estuve usando wine pero tampoco.

Bueno, creo que voy a tener que dejar las cosas como están, lamentando perder mis mails y contactos de evolution.

Gracias por tu ayuda y te envío un saludo.

---

