---
title: "Evolution con Exchange y Almacen Local."
date: 2010-12-03
forum: Software
---

### Post by Wiredfixer on 2010-12-03
Pues bien, tal como lo dice el titulo, me encuentro trabajando en Exchange con Evolution, hasta ahorita no he tenido problemas y todo va genial.

Mi unica situacion, es que me gustaria que todo se guardara de manera automatica en mi PC, no accederlo desde Exchange siempre.

Lo que hago actualmente, es copiar mis correos a mis carpetas locales, hasta ahi todo bien, pero (y ahi esta el pero) me gustaria que fuera como en Outlook.

Antes de que me lapiden, definitivamente es lo que estoy necesitando, en Microsoft Outlook lo hacia en unos cuantos pasos y solo me conectaba y bajaba todo a mi almacen local, mi cuenta principal era la local y todo bien.

He leido varios mailing list y foros, muchos recomiendan usar filtros u otras cosas, pero la idea es hacerlo lo mas "user friendly" posible.

Alguna idea? Script o algo?

Cualquier cosa es aceptada :D

---

### Post by hectorivand on 2010-12-04
> **Wiredfixer said:**
> Pues bien, tal como lo dice el titulo, me encuentro trabajando en Exchange con Evolution, hasta ahorita no he tenido problemas y todo va genial.

Mi unica situacion, es que me gustaria que todo se guardara de manera automatica en mi PC, no accederlo desde Exchange siempre.

Lo que hago actualmente, es copiar mis correos a mis carpetas locales, hasta ahi todo bien, pero (y ahi esta el pero) me gustaria que fuera como en Outlook.

Antes de que me lapiden, definitivamente es lo que estoy necesitando, en Microsoft Outlook lo hacia en unos cuantos pasos y solo me conectaba y bajaba todo a mi almacen local, mi cuenta principal era la local y todo bien.

He leido varios mailing list y foros, muchos recomiendan usar filtros u otras cosas, pero la idea es hacerlo lo mas "user friendly" posible.

Alguna idea? Script o algo?

Cualquier cosa es aceptada :D

Hola, la verdad que entendi muy poco lo que queres hacer.

te cuento, cuando vos abrís Outlook y no estás conectado al exchange, lo que ves en el Inbox es algo cacheado, no es una copia a tu equipo.

Esa es una funcionalidad especifica entre Exchange y Outlook, cualquier otro mortal que quisiera hacer algo parecido con otro software que no sea el mencionado más arriba, debe crear un almacén (equivalente en evolution de PST) aparte y ahí si "bajar" el contenido del cache del inbox a esas carpetas personales.

Se entendió más o menos?

Saludos
Nacho

---

### Post by Wiredfixer on 2010-12-07
Creo que no debi explicarlo como si no supiera.

Se que Exchange trabaja con un Cache que esta alojado en el server, precisamente mi problema es ese.

Quiero evitar que los correos sigan almacenados en el servidor, ya que esto me genera una saturacion y los usuarios de correo son muchos.

Puse el ejemplo de MS Outlook para definir como me gustaria que funcionara en Evolution.

Evolution utiliza un conector de Exchange por OWA, por tanto, el acceso a los correos es como si estuviera entrando desde un Webmail.

Como hasta ahorita se que no hay otra forma de acceder a exchange (a menos que se habiliten las funciones de POP3 en el servidor de la empresa... que no lo haran..) necesito:

- Que Evolution me guarde una copia Local de los correos.
- Evitar tener "2 bandejas", solo necesito una bandeja y tiene que almacenar los correos de manera local tal como sucede en MS Outlook.
- Necesito hacer esto de manera transparente, es decir, que no requiera configuraciones de filtros de correo, quiero evitar configurar cosas extra en Evolution, de ser posible, que si haya que configurar algo, sea fuera de la vista del usuario.

 Es precisamente lo que quiero hacer, un almacen tipo PST, pero en Evolution, cosa que se que se puede hacer pero solo con la version de paga de Evolution en SUSE linux.

---

### Post by hectorivand on 2010-12-08
> **Wiredfixer said:**
> Creo que no debi explicarlo como si no supiera.

Se que Exchange trabaja con un Cache que esta alojado en el server, precisamente mi problema es ese.

Quiero evitar que los correos sigan almacenados en el servidor, ya que esto me genera una saturacion y los usuarios de correo son muchos.

Puse el ejemplo de MS Outlook para definir como me gustaria que funcionara en Evolution.

Evolution utiliza un conector de Exchange por OWA, por tanto, el acceso a los correos es como si estuviera entrando desde un Webmail.

Como hasta ahorita se que no hay otra forma de acceder a exchange (a menos que se habiliten las funciones de POP3 en el servidor de la empresa... que no lo haran..) necesito:

- Que Evolution me guarde una copia Local de los correos.
- Evitar tener "2 bandejas", solo necesito una bandeja y tiene que almacenar los correos de manera local tal como sucede en MS Outlook.
- Necesito hacer esto de manera transparente, es decir, que no requiera configuraciones de filtros de correo, quiero evitar configurar cosas extra en Evolution, de ser posible, que si haya que configurar algo, sea fuera de la vista del usuario.

 Es precisamente lo que quiero hacer, un almacen tipo PST, pero en Evolution, cosa que se que se puede hacer pero solo con la version de paga de Evolution en SUSE linux.

Bueno, entonces ya que sabes, tal vez te ofendas si te digo que el que maneja la descarga de correos no es más que el administrador de Exchange y si el mismo no está dispuesto a cambiar esa politica en el mencionado servidor de correo a vos te va a seguir descargando / actualizando el cache cada vez que te conectes.

Lo que queres hacer, si no tenes acceso al Exchange, no lo vas a poder hacer. Entonces la única que te queda, pero claro, sabrás de lo que te hablo, **porque sabes**... es crear una carpeta en Evolution, una carpeta local y bajar ahí el contenido del "historico" que ya no queres / necesitas tener cacheado.

En definitiva la situación más que un "problema" de Evolution es de Exchange y como la organización lo administra. Nada más.

Como dato anecdotico cuando trabaja para la empresa del "mal" hacíamos eso, los emails cacheados, los metiamos en una carpeta local, con eso manteníamos limpios los pobres 300mb que teníamos para los Inbox de Cono Sur.

En fin...

Saludos
Nacho

---

### Post by Wiredfixer on 2010-12-09
Si, de hecho se que todo lo de Exchange lo maneja el Administrador, se lo del cache de correos y TODO lo que ya comentaste.

Se que puedo crear carpetas locales de Evolution y que puedo almacenar mis correos en mi PC, esto ya lo hice y lo hago diario.

No soy un usuario Novato, el chiste es que quiero hacer la configuracion de Evolution lo mas simplificada posible, porque actualmente me encuentro Remasterizando y desarrollando un desktop basado en Ubuntu para una empresa.

Pongamoslo asi si Microsoft Outlook se configura tan simple como:

- Seleccionar que usamos exchange
- Poner el Servidor de Exchange y Buzon
- Al Iniciar Outlook, configuramos para que el correo se almacene localmente a un PST.
- Reinciamos Outlook y listo.

Ahora, en Evolution:

- Seleccionar que usamos Exchange
- Hay que configurar el Servidor OWA, el Buzon y Los permisos.
- Configurar la Libreta de direcciones
- Definir que cada 10 Minutos se revise el correo
- Crear Reglas para que el correo que va llegando se mueva a la carpeta local.
- Etc.

Los primeros 4 Pasos ya estan configurados, para esto, modifique un script que ya estaba en uso y me configura automaticamente el usuario de Evolution y el Mailbox basandose en la coneccion al AD por medio de Likewise... Simple.

Pero quiero evitar la parte de crear reglas para que todo el correo nuevo que llegue, lo mueva a la carpeta local, esto me puede dar varios problemas como:

- Los filtros no trabajen correctamente
- La configuracion de los Filtros lleva tiempo
- Una vez que esta configuracion este hecha, que el usuario no la modifique y evitar incidencias.
- Que sea de manera transparente para el usuario.

En pocas palabras, deseo que el correo llegue directamente al almacen local del equipo, como funciona en Outlook, si me explico? Quiero evitar crear reglas porque se supone que ya tengo un almacen local de correo, que por logica, deberia ser usado para guardar mis correos y no que se queden en el Mailbox de Exchange.

 Ya marque la opcion de "Crear un Almacen local.." y pues pense que esto podria ayudar, aun asi, al menos no me funciona como yo pense.

 Se que esta funcion se puede hacer en el Evolution de SuSE Enterprise, aun asi, no he hayado nada relativo a esta funcionalidad y tratar de adaptarla al Evolution de Ubuntu.

---

### Post by hectorivand on 2010-12-10
No te compliques la vida y decile al admin de Exchange que habilite IMAP  y configura las cuentas en cada Evolution y listo.

Con eso te ahorras de usar el conector para el OWA, sumado a los dramas con el cacheo en el equipo y demas.

Si no te sirve lo que te digo, sinceramente no entiendo lo que queres hacer.

No se quien te dijo que lo que bajas con Outlook desde Exchange no quedan en el buzón, queda todo, por eso te explico que lo que tenes cuando por ejemplo, estas offline es una copia cacheada de tu buzón del exchange, cuando estas conectado, estas viendo directamente.

Mira a Exchange y su tecnología como algo muy parecido a Imap, con pequeñas diferencias, ahora lo que vos queres hacer no es posible sin que intervenga el admin de exchange porque no hay forma de decirle que la maquina local tiene que descargar los emails y borrarlos del servidor tal como pasa con POP.

se entiende? tenes que involucrar al admin de Exchange en esto. Para que te habilite IMAP y los usuarios puedan "descargar" sus emails y tenerlos cacheados, esten o no online.

**se entiende?** con el "protocolo" de exchange, eso, sin Outlook no lo vas a poder lograr, pero repito **Si no le comentas esto mismo al admin de exchange, no lo vas a poder hacer.**

Saludos
Nacho

---

### Post by Wiredfixer on 2010-12-10
Bueno, de hecho, esto de los PST lo hacia en otras empresas.

Se que a fuerza van a llegar al Inbox, eso no lo puedo evitar y pues con IMAP seria todo feliz, el detalle es que son cosas que el admin no va a cambiar para 40 usuarios cuando son mas de 4mil.


En otra empresa lo que haciamos, era que configurabamos el almacen local con Microsoft Outlook, tambien trabajamos con exchange, asi que la cosa era asi.

Al principio. de recien configurado, toda la info la consulta Outlook desde el Inbox que esta en el servidor, esto funciona hasta que el admin nos dice que la informacion debe ser almacenada localmente.

Ahi es cuando creamos un PST Personal, almacenado en la PC y luego lo ponemos como almacen principal:

[http://office.microsoft.com/es-mx/outlook-help/crear-un-archivo-para-guardar-la-informacion-HA001230891.aspx](http://office.microsoft.com/es-mx/outlook-help/crear-un-archivo-para-guardar-la-informacion-HA001230891.aspx)

La idea, es tener los correos Offline, si el administrador decide borrar el cache de Exchange, los correos ya estan en la PC.

Esto mismo quiero lograr con Evolution, el detalle, es que no hay una manera de hacer esto simple, ya que Outlook sabe que tengo un PST y me copia los archivos a mi PST Local, Evolution tiene un almacen local, pero no me copia ahi y se quedan en cache, a menos que yo los copie a las carpetas locales o haga una regla que correo  que me llegue al inbox, me lo copie en carpeta local.

Eso me funciona a mi, pero quiero evitar manejar reglas de correo, porque los usuarios van a querer crear las suyas y algunos manitas podrian mover esta configuracion.

Eso es basicamente mi situacion, mantener un almacen Offline y cada correo que me llegue, se almacene localmente, independientemente de lo que se haga en Exchange, al menos yo ya tengo una copia local a salvo y localizada en mi carpeta de Evolution.

---

### Post by hectorivand on 2010-12-10
> **Wiredfixer said:**
> Bueno, de hecho, esto de los PST lo hacia en otras empresas.

Se que a fuerza van a llegar al Inbox, eso no lo puedo evitar y pues con IMAP seria todo feliz, el detalle es que son cosas que el admin no va a cambiar para 40 usuarios cuando son mas de 4mil.


En otra empresa lo que haciamos, era que configurabamos el almacen local con Microsoft Outlook, tambien trabajamos con exchange, asi que la cosa era asi.

Al principio. de recien configurado, toda la info la consulta Outlook desde el Inbox que esta en el servidor, esto funciona hasta que el admin nos dice que la informacion debe ser almacenada localmente.

Ahi es cuando creamos un PST Personal, almacenado en la PC y luego lo ponemos como almacen principal:

[http://office.microsoft.com/es-mx/outlook-help/crear-un-archivo-para-guardar-la-informacion-HA001230891.aspx](http://office.microsoft.com/es-mx/outlook-help/crear-un-archivo-para-guardar-la-informacion-HA001230891.aspx)

La idea, es tener los correos Offline, si el administrador decide borrar el cache de Exchange, los correos ya estan en la PC.

Esto mismo quiero lograr con Evolution, el detalle, es que no hay una manera de hacer esto simple, ya que Outlook sabe que tengo un PST y me copia los archivos a mi PST Local, Evolution tiene un almacen local, pero no me copia ahi y se quedan en cache, a menos que yo los copie a las carpetas locales o haga una regla que correo  que me llegue al inbox, me lo copie en carpeta local.

Eso me funciona a mi, pero quiero evitar manejar reglas de correo, porque los usuarios van a querer crear las suyas y algunos manitas podrian mover esta configuracion.

Eso es basicamente mi situacion, mantener un almacen Offline y cada correo que me llegue, se almacene localmente, independientemente de lo que se haga en Exchange, al menos yo ya tengo una copia local a salvo y localizada en mi carpeta de Evolution.

Habilita IMAP, pero le da acceso a los 40 usuarios y listo. Vos mismo lo dijiste, si el admin no toca los buzones de esos cuarenta usuarios, poco vas a poder hacer desde Evolution.

No tengo más para decir.

Saludos
Nacho

---

### Post by Wiredfixer on 2010-12-10
Bueno, vere que puedo hacer.

Es muy dificil hacerse entender, jaja..

La idea basica era solo tener una copia Offline, no creo necesitar IMAP, Si ya puedo trabajar y ver los correos, solo necesito que se pasen automaticamente a mi almacen local, es todo.

Mi problema basicamente no es con exchange, es con Evolution y su forma de administrar el almacen local.

Gracias de todos modos :D

---

