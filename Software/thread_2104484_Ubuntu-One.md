---
title: "Ubuntu-One"
date: 2013-01-13
forum: Software
---

### Post by Vero1 on 2013-01-13
Buen día a todos,

Tengo una cuenta en Ubuntu-One(free) donde hay 5 Gb de espacio para almacenar. Si veo cuanto espacio me queda, me queda todo.

Quiero hacer Backup de Home y Documentos, mediante dejá-dup y que se almacene en la nube.

Tengo configurado para que haga un backup diario en forma automática pero me sale un cartel diciendo que "en cuanto tenga conexión" se hará.

Yo tengo banda ancha, así que tengo conexión siempre. Hasta el momento no he podido hacer ningún backup.

Me sale el siguiente cartel: RESPALDANDO pero mas abajo dice: Pausado(sin red). No entiendo si como dije tengo conexión siempre.

Alguien me puede echar una mano?

Gracias y saludos):P

---

### Post by guillermolisi on 2013-01-13
Vero

El backup con Deja-Dup lo tenes que configurar para que se realice en un directorio de tu maquina que este suscripto a UbuntuOne para que se realice la sincronizacion.
Ademas tener que contar con el cliente de UbuntuOne instalado en tu maquina y conectado con tu cuenta de U1(se me ocurre esto por el mensaje que te aparece).


Nota al margen: Este tipo de consultas van en Software (UbuntuOne es software y Deja-Dup tambien) ya que claramente no es un problema que involucre hardware (por ahora). Son esos problemas que solamente podes insultar pero no patear lo que no esta funcionando.

---

### Post by Vero1 on 2013-01-13
Hola Guillermo Lisi,

Gracias una vez mas por contestarme :)

Lamento no entender del todo eso del directorio.
A ver como te puedo explicar.
La cuenta está abierta como Verónica B. y mi dirección de correo electrónico.
Hoy hice un share a mi correo electrónico(no sé si está bien en realidad)
Está configurado para que suba a la nube, diariamente, todo lo que es Home y Documentos, pero voy a ver qué hay guardado en Ubuntu-One y no hay nada de Home ni documentos y, como dije antes, el lugar está vacío o sea que están los 5 Gb libres.

En cuanto a lo que decís de cuenta U1 tampoco entiendo a qué se refiere.

Lamento pero necesito mas asistencia.

Gracias.

---

### Post by Vero1 on 2013-01-13
> **Vero1 said:**
> Hola Guillermo Lisi,

Gracias una vez mas por contestarme :)

Lamento no entender del todo eso del directorio.
A ver como te puedo explicar.
La cuenta está abierta como Verónica B. y mi dirección de correo electrónico.
Hoy hice un share a mi correo electrónico(no sé si está bien en realidad)
Está configurado para que suba a la nube, diariamente, todo lo que es Home y Documentos, pero voy a ver qué hay guardado en Ubuntu-One y no hay nada de Home ni documentos y, como dije antes, el lugar está vacío o sea que están los 5 Gb libres.

En cuanto a lo que decís de cuenta U1 tampoco entiendo a qué se refiere.

Lamento pero necesito mas asistencia.

Gracias.

para mayor información, te paso link a imageshack para que veas un poco lo que pasa:

[http://img90.imageshack.us/img90/1396/capturadepantallade2013.png](http://img90.imageshack.us/img90/1396/capturadepantallade2013.png)

---

### Post by guillermolisi on 2013-01-13
UbuntuOne posee un programa que se instala en tu maquina y que oficia de cliente para el servidor donde se alojan contenidos en la nube.
Para iniciar este programa cliente tenes que haberlo configurado en pantalla a partir del icono de U1 de la barra de botones de Unity (o desde el Dash buscando UbuntuOne, es lo mismo).

Una vez que logras que el cliente se conecte al servidor y que este valide tu usuario y contraseña para U1 pasas a determinar que directorios seran sincronizados (cosa que parece que hiciste). A partir de ese momento deberia iniciarse la sincronizacion donde la primera es la que mas tarda ya que no hay nada subido.

Si no tenes ningun archivo de los directorios que marcaste para sincronizar en U1 se me ocurre que no se esta conectando al servidor. Es decir, no pasa por si tenes o no conexion a Internet (que esta visto que si tenes) sino por la conexion de tu maquina con el server de U1 via su programa cliente.

Antes de continuar con la sincronizacion del backup, hay que resolver por que no se produce esta conexion y sincronizacion de archivos de esos directorios que decis haber marcado para subir a la nube.

Resuelto esto, que se verifica constatando que hay copias de los archivos de esos directorios en U1 via web, por ejemplo, se puede encarar el tema backup en la nube sobre una base firme.

---

### Post by Vero1 on 2013-01-13
Todo lo manejé desde el Dash.
Ahora, con lo que me decís, fuí a Archivo, Conectar con el Servidor(cosa que ignoraba que existía) y me sale una ventanita donde habla de:

Servidor........  puerto 21
FTP público(ademas de otras opciones)
Carpeta /

Despues abajo dice conectar.

Lo que no sé qué se pone en Servidor, porque mi Servidor de Internet es Speedy.com.ar pero no sé si tiene que ver.

Como dije antes, en U1 no hay nada de mi home o documentos que debe ser por no tener conexión con el servidor.

Me podés decir qué Servidor debo poner para conectarme?

Gracias

---

### Post by guillermolisi on 2013-01-13
> Para iniciar este programa cliente tenes que haberlo configurado en pantalla a partir del icono de U1 de la barra de botones de Unity (o desde el Dash buscando UbuntuOne, es lo mismo).No menciono Archivo/Servidor.

---

### Post by Vero1 on 2013-01-14
Hola Guillermo,

Instalé FileZilla y parece que conecta con el servidor mío que es Speedy, pero no sé qué dirección tengo que poner en el Servidor Remoto que, en este caso, es Ubuntu-One.

Qué me podés decir?

Gracias

---

### Post by guillermolisi on 2013-01-14
Que te estas yendo por las ramas. Hay que usar el boton de UbuntuOne para terminar de configurar el cliente, que conecte con el servidor y que puedas sincronizar los directorios que mencionaste.

---

### Post by Vero1 on 2013-01-14
ok Guillermo, veo si puedo hacer las cosas mejor.

Gracias y saludos

---

