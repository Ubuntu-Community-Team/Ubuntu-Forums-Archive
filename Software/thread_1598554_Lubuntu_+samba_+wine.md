---
title: "Lubuntu +samba +wine"
date: 2010-10-16
forum: Software
---

### Post by carpe omnius on 2010-10-16
Buenas tardes a todos, antes que nada pido disculpas si este post no va aca o ya fue tratado, he buscado informacion antes de hacerlo pero no he podido encontrar solucion a mi problema...


El tema es el siguiente:

En el trabajo tenemos una lan de 7 maquinas viejitas celero, pentium 3 etc...ninguna supera los 256mb de ram. Esas maquinas estan en red trabajando con una base de datos vieja en foxpro, desde la que acceden, y ademas a una serie de documentos que se usan como modelos para distinas cosas.

Queremos instalar linux en todas las maquinas e ir migrando de a poco (1 maquina por ahora para ir viendo el desempeño).

El problema se sucede cuando instale lubuntu en una de las maquinas (que por cierto vuela!), no logro desde el synaptic instalar wine y samba para que la maquina pueda atraves de wine emular la BD y acceder a ella atraves de samba al servidor que de momento es un XP Professional.

La verdad que me aparecen muchas opciones al poner sambay nose cual de todas es...lo mismo con wine...

1.- Hay una manera de hacerlo por consola de comandos?

2.- Para ver los archivos compartidos del servidor y acceder por ej a 1 documento Word, necesito un cliente especial?

Gracias y perdon nuevamente si este tema ya se trato.

---

### Post by guillermolisi on 2010-10-16
Creo que lo mejor, como para ponernos en situacion, seria que nos cuentes como esta planteada esa red. Por ejemplo:
[LIST]
[*]Las PCs utilizan IPs estaticas o dinamicas ?
[*]Tiene su firewall activado ?
[*]Como estan configuradas las politicas de seguridad y comparticion de recursos de Windows en cada una ?
[*]Como es la politica de inicio de sesion en Windows ? Hay usuarios diferentes para cada maquina o estan todos los usuarios replicados en cada una ?
[*]Revisaste y verificaste que esa base de datos en FoxPro funcione adecuadamente con Wine ?
[/LIST]
No soy nadie para decir como hacer este tipo de trabajos pero si se que la ansiedad es enemiga de un laburo exitoso.

---

### Post by carpe omnius on 2010-10-17
Hola Guillermo gracias por responder, te comento...

1.- Las pcs tienen ips estaticas, dentro de un parametro previamente definido.
2.- Las pcs son todas windows xp con el firewall de windows por defecto.
3.- Politicas de Seguridad, sinceramente no hay muchas, calcula que es una oficina del estado (por ende capacitacion o presupuesto=0), las personas que trabajan son en sumayoria gente grande que realiza tareas administrativas (Word sobre todo) por lo que no estan acostumbrados a politicas de seguridad y demas. La unica maquina que comparte documentos es la que hace de Servidor, que es la que aloja la db y los documentos modelos, el resto, solo accede a un directorio compartido, de manera de  tener todo el trabajo centralizado.El GRAN problema que hay y es lo que motivo esto, es que la  red de la oficina, forma parte de una red organizacional mal diagramada de manera que todas las pcs pueden verse, al estar la mayoria infectadas con virus (a nadie le calienta mientras el trabajo salga) llueven cientos de peticiones TCP de todas las maquinas lo que afecta el rendimiento de NUESTRA LAN. Es por eso que estamos pensando a migrar a algo mas robusto como linux en este caso.
4.- La politica de sesion en windows es nula, todos los usuarios de la lan acceden a la carpeta compartida, en contraposicion, cualquiera que chusmee las redes, accede a la carpeta compartida y a la bd.
5.- En principio la bd, funciona bien en wine, tanto como para consulta como para carga de datos en LOCALHOST, via red, osea, a traves de samba no lo hemos probado, es por eso que queriamos hacer la prueba con 1 maquina sola.

Gracias por responder!!!!

> **guillermolisi said:**
> Creo que lo mejor, como para ponernos en situacion, seria que nos cuentes como esta planteada esa red. Por ejemplo:
[LIST]
[*]Las PCs utilizan IPs estaticas o dinamicas ?
[*]Tiene su firewall activado ?
[*]Como estan configuradas las politicas de seguridad y comparticion de recursos de Windows en cada una ?
[*]Como es la politica de inicio de sesion en Windows ? Hay usuarios diferentes para cada maquina o estan todos los usuarios replicados en cada una ?
[*]Revisaste y verificaste que esa base de datos en FoxPro funcione adecuadamente con Wine ?
[/LIST]
No soy nadie para decir como hacer este tipo de trabajos pero si se que la ansiedad es enemiga de un laburo exitoso.

---

### Post by Tosh78 on 2010-10-17
Hola! Para instalar wine en la linea de comandos podes usar:
sudo apt-get install wine
Samba nunca lo use :S

---

### Post by guillermolisi on 2010-10-17
> **carpe omnius said:**
> Hola Guillermo gracias por responder, te comento...

1.- Las pcs tienen ips estaticas, dentro de un parametro previamente definido.
2.- Las pcs son todas windows xp con el firewall de windows por defecto.
3.- Politicas de Seguridad, sinceramente no hay muchas, calcula que es una oficina del estado (por ende capacitacion o presupuesto=0), las personas que trabajan son en sumayoria gente grande que realiza tareas administrativas (Word sobre todo) por lo que no estan acostumbrados a politicas de seguridad y demas. La unica maquina que comparte documentos es la que hace de Servidor, que es la que aloja la db y los documentos modelos, el resto, solo accede a un directorio compartido, de manera de  tener todo el trabajo centralizado.El GRAN problema que hay y es lo que motivo esto, es que la  red de la oficina, forma parte de una red organizacional mal diagramada de manera que todas las pcs pueden verse, al estar la mayoria infectadas con virus (a nadie le calienta mientras el trabajo salga) llueven cientos de peticiones TCP de todas las maquinas lo que afecta el rendimiento de NUESTRA LAN. Es por eso que estamos pensando a migrar a algo mas robusto como linux en este caso.
4.- La politica de sesion en windows es nula, todos los usuarios de la lan acceden a la carpeta compartida, en contraposicion, cualquiera que chusmee las redes, accede a la carpeta compartida y a la bd.
5.- En principio la bd, funciona bien en wine, tanto como para consulta como para carga de datos en LOCALHOST, via red, osea, a traves de samba no lo hemos probado, es por eso que queriamos hacer la prueba con 1 maquina sola.

Gracias por responder!!!!
Ok. Bastante completa la explicacion.

Lo primero que haria es mantener el archivo "hosts" de cada maquina con el nombre e IP de cada PC de la red. Esto resolvera el acceso por nombres en forma rapida entre las PCs. La alternativa mas "pro" seria un DNS local, pero por tu comentario sobre presupuesto y capacitacion por ahora lo descarto.

Luego intentaria que el ancho de banda a la maquina que contiene la base de datos comun sea mayor que el resto de ancho debanda de la red para que los requerimientos y respuestas que se canalizan no generen un cuello de botella desmejorando el rendimiento general de la red (siempre marcado por el componente de menor desempeño).

Si la idea es tener todas las maquinas con Ubuntu Linux descartaria Samba ya que este haria falta si y solo si la red posee maquinas con Win. En lugar de Samba implementaria NFS para disponibilizar los recursos que requieran ser accedidos por las otras maquinas. Es muchisimo mas rapido, simple y seguro que Samba.

Esto siempre que la base de datos de Fox Pro bajo Wine pueda publicarse via NFS y los accesos sean controlables (evitar falsos bloqueos a las tablas y filas, asegurarse que las actualizaciones bloqueen adecuadamente, etc.). En caso que quieran utilizar Samba, igualmente haria la verificacion respecto de los accesos y los bloqueos de tablas y filas cuando se accede desde otra maquina (!= localhost).

Si esto ultimo no funciona correctamente, cambiaria la estrategia ya que sin esa base publicable y usable por las demas PCs entiendo que no es viable la migracion.

Si esta LAN es parte de otra en la cual hay tormenta de paquetes, de la clase que sean, no resolveran la perdida de ancho de banda por trafico espureo a raiz de los virus, solo tendran la ventaja de no contagiarse (que no es poco) siempre que todas esas PCs que quieren migrar tengan Linux y no Win.

---

### Post by carpe omnius on 2010-10-20
> **guillermolisi said:**
> Ok. Bastante completa la explicacion.

Lo primero que haria es mantener el archivo "hosts" de cada maquina con el nombre e IP de cada PC de la red. Esto resolvera el acceso por nombres en forma rapida entre las PCs. La alternativa mas "pro" seria un DNS local, pero por tu comentario sobre presupuesto y capacitacion por ahora lo descarto.

Luego intentaria que el ancho de banda a la maquina que contiene la base de datos comun sea mayor que el resto de ancho debanda de la red para que los requerimientos y respuestas que se canalizan no generen un cuello de botella desmejorando el rendimiento general de la red (siempre marcado por el componente de menor desempeño).

Si la idea es tener todas las maquinas con Ubuntu Linux descartaria Samba ya que este haria falta si y solo si la red posee maquinas con Win. En lugar de Samba implementaria NFS para disponibilizar los recursos que requieran ser accedidos por las otras maquinas. Es muchisimo mas rapido, simple y seguro que Samba.

Esto siempre que la base de datos de Fox Pro bajo Wine pueda publicarse via NFS y los accesos sean controlables (evitar falsos bloqueos a las tablas y filas, asegurarse que las actualizaciones bloqueen adecuadamente, etc.). En caso que quieran utilizar Samba, igualmente haria la verificacion respecto de los accesos y los bloqueos de tablas y filas cuando se accede desde otra maquina (!= localhost).

Si esto ultimo no funciona correctamente, cambiaria la estrategia ya que sin esa base publicable y usable por las demas PCs entiendo que no es viable la migracion.

Si esta LAN es parte de otra en la cual hay tormenta de paquetes, de la clase que sean, no resolveran la perdida de ancho de banda por trafico espureo a raiz de los virus, solo tendran la ventaja de no contagiarse (que no es poco) siempre que todas esas PCs que quieren migrar tengan Linux y no Win.


hola Guillermo, gracias por una respuesta tan didactica y tan clara!!!! De lo leido me surgen las siguientes dudas y comentarios....

A fin de que la migracion de windows a Linux no sea tan duro para el personal de la oficina, aremos de a 1 pc por ves, y ello también con el fin de poder ir evaluando el desempeño del comportamiento de la BD en red que es lo que mas importa...Algo que me olvide de comentarte, es que, la pd esta en produccion las 24 hs de lunes a viernes por lo que no me puedo dar el lujo de cambiar todas las maquinas a linux y que no funcione nada, por que como minimo todo estaria caido durante unas 6 horas mas o menos...Consecuentemente la estructura de red quedaria de momento asi:


[LEFT]PC A: XP -------|[/LEFT]
 
[LEFT]PC B: XP -------|[/LEFT]
                   [CENTER]&#8596; Server: XP Prof (BD FoxPro)[/CENTER]
[LEFT]PC C: XP -------|[/LEFT]   
   
[LEFT]PC D: Lubuntu --|[/LEFT]


1.- Mi primera pregunta es: Debo instalar algún soft en especial en el Servidor (XP Professional, ademas del samba y wine que debo instalar en Linux?

2.- Ademas del inicio de sesion clasico en ubuntu, debo gestionar algun tipo de sesion especial en red para acceder a la bd? O solo con poner un acceso en el escritorio de Lubuntu de la bd o la carpeta compartida funciona?

2.- Que archivo debo editar en lubuntu, a fin de que cuando se inicie sesion, automaticamente se monte la carpeta compartida en el escritorio y la bd?

3.- Me podrias explicar como es lo del archivo host? Lo debo editar en la maquina que hace de servidor, informandole que ip se corresponde a que maquina?

Muchas gracias por la ayuda!!!!

---

### Post by guillermolisi on 2010-10-21
> **carpe omnius said:**
> hola Guillermo, gracias por una respuesta tan didactica y tan clara!!!! De lo leido me surgen las siguientes dudas y comentarios....

A fin de que la migracion de windows a Linux no sea tan duro para el personal de la oficina, aremos de a 1 pc por ves, y ello también con el fin de poder ir evaluando el desempeño del comportamiento de la BD en red que es lo que mas importa...Algo que me olvide de comentarte, es que, la pd esta en produccion las 24 hs de lunes a viernes por lo que no me puedo dar el lujo de cambiar todas las maquinas a linux y que no funcione nada, por que como minimo todo estaria caido durante unas 6 horas mas o menos...Consecuentemente la estructura de red quedaria de momento asi:


[LEFT]PC A: XP -------|[/LEFT]
 
[LEFT]PC B: XP -------|[/LEFT]
                   [CENTER]&#8596; Server: XP Prof (BD FoxPro)[/CENTER]
[LEFT]PC C: XP -------|[/LEFT]   
   
[LEFT]PC D: Lubuntu --|[/LEFT]


1.- Mi primera pregunta es: Debo instalar algún soft en especial en el Servidor (XP Professional, ademas del samba y wine que debo instalar en Linux?
En principio creo que en WinXP no estarias obligado a instalar algo adicional.
> 
2.- Ademas del inicio de sesion clasico en ubuntu, debo gestionar algun tipo de sesion especial en red para acceder a la bd? O solo con poner un acceso en el escritorio de Lubuntu de la bd o la carpeta compartida funciona?
Posiblemente WinXP te pida que validez la cuenta con la cual queres acceder. Esto depende de como esten establecidas las politicas de WinXP. Convendria (y no soy el mas indicado para afirmarlo) que la cuenta con la cual se accede a Lubuntu tambien exista (como equivalente) en el XP.

Creo que la gestion con la base de datos, que esta en el recurso compartido publicado por el XP, la hara FoxPro corriendo via Wine y hasta aqui llego porque nunca use FoxPro asi que no se como lleva a cabo este tipo de cosas.

> 2.- Que archivo debo editar en lubuntu, a fin de que cuando se inicie sesion, automaticamente se monte la carpeta compartida en el escritorio y la bd?
El montaje de medios se realiza en un directorio del sistema de archivos de Linux. Podes utilizar el directorio /media/<nombre_de_directorio_para_recurso_compartido> o crear una estructura "ad hoc" (simplemente con mkdir).
No uses el directorio Escritorio porque lo que montes "tapara" el contenido que ese directorio posea y si es Escritorio te quedaras sin el cada vez que se monte el recurso publicado de Windows.

> 3.- Me podrias explicar como es lo del archivo host? Lo debo editar en la maquina que hace de servidor, informandole que ip se corresponde a que maquina?
El archivo /etc/hosts se utiliza para resolucion local de nombres cuando no tenes a mano un servidor DNS que haga esta tarea. Podes editarlo en todas las PCs para que sepan donde esta el servidor.
Generalmente tienen un contenido similar a este ejemplo:
```
<ip> <nombre-del-host>
```
con esto, cuando una PC busca algo en otra y lo hace utilizando el nombre, con este archivo lo "traduce" a su direccion IP antes de acceder a la otra maquina (es el metodo lmhost de Windows).
Es practico para instalaciones muy estaticas y reducidas.

---

### Post by darta2032 on 2010-10-24
Estuve leyendo el post y me parece que en la pregunta:
2.- Que archivo debo editar en lubuntu, a fin de que cuando se inicie sesion, automaticamente se monte la carpeta compartida en el escritorio y la bd? 
El archivo que tienes que editar es el 'fstab', que está en la carpeta '/etc', que es el que monta todos los archivos al iniciar el sistema.

---

### Post by Wiredfixer on 2010-10-26
Y no seria mas facil usar SeamlessRDP?

Yo lo empeze a usar y la verdad, me quita mucho trabajo de mis desktop.


La cosa es esta, en el "server" con Windows XP Pro, descargas este archivo:

[http://www.cendio.com/seamlessrdp/](http://www.cendio.com/seamlessrdp/)

ya puesto en ruta, solo instalas los programas que quieres ejecutar en los desktop y a traves de un RDesktop, los puedes ejecutar en Lubuntu.

rdesktop -A -s "x:\seamlessrdp\seamlessrdpshell.exe x:\Program Files\aplicacion.exe" ip.del.server.appz

Asi la aplicacion se ejecuta en el servidor, las Desktops solo lo trabajan de manera transparente, asi te evitas el tener problemas con el WINE, que no es muy fiable.

Digamos que, es usar un Terminal Server estilo Citrix.

Tambien la situacion es correr la BD de manera mas nativa, asi que creo yo, que la opcion Seamless es la mas correcta y simple de usar.

Precisamente, en esas me encuentro yo, ir cambiando equipos de Windawgs a Ubuntu 10.04 y la idea es hacerlo lo mas "user friendly" posible.

Saludos!

---

### Post by biale on 2010-10-26
> con una base de datos vieja en foxpro,

No trabajé con Fox, solo Clipper: El sistema es win32 o DOS?  Hay que instalar/ configurar algo en las PC "clientes" Win o solo basta con copiar y hacer doble click al ejecutable?

---

