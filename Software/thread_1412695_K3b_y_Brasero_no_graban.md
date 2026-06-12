---
title: "K3b y Brasero no graban"
date: 2010-02-21
forum: Software
---

### Post by DarkGlobe on 2010-02-21
Increible, perdi 6 dvd's tratando de solucionar el problema. Resulta que K3b y Brasero no funcionan, ni siquiera comienza a grabar y me lanza este problema K3b.

[[IMG]http://img638.imageshack.us/img638/9360/imgar.th.png[/IMG]](http://img638.imageshack.us/i/imgar.png/)

Hace algunos dias no estaba asi, me da la impresion que es alguna actualizacion que da el problema, pero no se cual. A alguien le pasa algo similar?.

Saludos.

---

### Post by zhelo on 2010-02-21
3 cosas
-ejecuta el programa en consola y pega lo que salga, deberia salir algun error
-puee que la marca de cd sea la mala, porbaste con otras marcas?
-alguien te cambio el grabador por un lector XD

---

### Post by Carlos C on 2010-02-22
Efectivamente es posible que tengas problemas con la marca del dvd, a mí me ha pasado (zykon definitivamente no funciona en mi equipo).

---

### Post by radixs on 2010-02-22
Apoyo el comentario de Carlos_C a mi los CD Master G, me cuesta un mundo para que me los tome o lo grabe bien :S

---

### Post by DarkGlobe on 2010-02-22
los dvd no son el problema, ya que siempre he grabado con ellos. son cursor. incluso tengo una torre de 50 y he ocupado 20 sin problemas... de todas maneras puedo grabar con windows 7 pero no es la idea.

si alguien le ha pasado ojala pueda ayudarme. saludos

---

### Post by zhelo on 2010-02-22
mmm, lee cd/dvd correcatmente????, puede que el lector este muriendo

---

### Post by DarkGlobe on 2010-02-23
tiene menos de 3 meses el grabador.. es un lg... si en w7 graba muy bien, el problema es solo en ubuntu.

---

### Post by Carlos C on 2010-02-23
Puede ser que tengas un problema de permisos. Dime qué te muestra el siguiente comando:
```
ls -l /dev/dvd*
```Saludos.

---

### Post by DarkGlobe on 2010-02-23
Ok, esto me arroja el comando ls

lrwxrwxrwx 1 root root 3 2010-02-23 11:31 /dev/dvd -> sr0
lrwxrwxrwx 1 root root 3 2010-02-23 11:31 /dev/dvdrw -> sr0

---

### Post by CdK1 on 2010-02-23
Como root desde la consola ejecuta k3b y trata de quemar un DVD...

---

### Post by moreback on 2010-02-26
Si no me equivoco tu usuario debiera pertenecer al grupo cdrom para escribir en ese dispositivo (un **ls -l /dev/sr0** debiera indicarte eso). Para meterte en ese grupo tienes que ir a **Sistema -> Administración -> Usuarios y grupos**, pulsar sobre las llaves para desbloquear, luego seleccionar tu usuario, pulsar **Propiedades**, seleccionar la pestaña **Privilegios de usuario** en la ventana que se abrió y finalmente marcar la opción "**Usar unidades de CD-ROM**".

Después de hecho el cambio tienes que logearte de nuevo.

Saludos.

---

### Post by CdK1 on 2010-03-22
Como root usando K3B no deberías tener problemas de permisos, si le diste permisos y persiste el error, prueba quemando con growisofs y ve los resultados...

---

### Post by nechus on 2010-03-25
Tengo un Acer Aspire 5738 y hace dos semanas empecé a recibir el mismo mensajito de K3B cuando quería grabar CDs. El lector sencillamente no los leía. Brasero tampoco funcionaba. Lo raro era que no había ningún problema al leer o grabar DVDs.

Buscando en Internet aprendí que estos lectores tienen dos láseres: uno para los CDs y otro para los DVDs, porque tienen frecuencia de onda distintas y no sé qué más. Suele ocurrir que uno de los dos láseres se echa a perder y hay que cambiar el lector entero.

Lo llevé al servicio técnico. Menos mal que todavía estaba dentro de la garantía, así que me cambiaron la unidad óptica sin ningún problema.

Ahora, la diferencia contigo es que dices que tu lector sí funciona con Windows, por lo que todo esto que estoy escribiendo no te sirve para nada, porque el problema debe ser otro, pero no importa porque ya me desahogué y me siento mejor. Gracias.

---

### Post by tuxsarge on 2010-03-31
brasero en ubuntu 9.10 por lo menos, está pitiado, ya que mis 2 pc de la casa más unos equipos de amigos que han instalado estas versiones, a veces no graba brasero, queda haciendo nada :o

Asi que tuve que instalar k3b y también puse nerolinux y con ellos no he tenido problemas

Y con varias marcas de CD y DVD y en distintos equipos :shock:

---

### Post by nechus on 2010-04-07
Algo tiene que andar mal en Karmic, y no se ha solucionado en Lucid. Pero al menos he logrado grabar sin problemas iniciando K3B con sudo desde la terminal.

---

### Post by Carlos C on 2010-04-08
Es muy extraño, yo puedo grabar en Karmic sin problemas.

---

### Post by joseluis on 2011-05-09
relanzo este post porque me pasa LO MISMO en ubuntu 11.04, lecto grabadora CD DVD LG. En windows funciona perfectamente.
¿alguien sabe algo?

---

### Post by RafaelG on 2011-05-11
> relanzo este post porque me pasa LO MISMO en ubuntu 11.04, lecto grabadora CD DVD LG. En windows funciona perfectamente.
¿alguien sabe algo?Joseluis, 

Te recomiendo para que puedas tener una mejor ayuda y respuesta crees un nuevo post con tu problema ya que tu version en Ubuntu es diferente a la indicada en este post.

Saludos cordiales,

---

