---
title: "Recomendaciones para un servidor de musica LAN"
date: 2009-06-15
forum: Software
---

### Post by ado@linux on 2009-06-15
Buenas, el siguiente post es para pedir recomendaciones para montar un servidor de musica (y si se puede video) para mi LAN. Voy a tratar de ser prolijo en la explicación para que las recomendaciones puedan ser pertinentes.

**Escenario**:

Equipo de escritorio conectado a un router a través de la placa de red, con un disco externo USB (proximamente e-SATA) con música, videos y otras porquerías.
Dos notebooks conectadas al router de forma inalambirca.
Todas las compus corren Ubuntu 9.04.

**Objetivos**:

Compartir la música en el equipo de escritorio con el resto de la red a través de un servicio que permita tratar la colección como si fuera local, en el marco de un reproductor multimedia, no una página web o directorios compartidos (que dicho sea de paso, no me está andando bien). Creo que DAAP en iTunes y Windows Media Connect hacen más o menos lo que necesito, pero claramente en otras plataformas.

**Extras**:

[LIST]
[*]Sería interesante poder compartir también videos, pero lo prioritario es la música.
[*]No es necesario (ni deseable) la posibilidad de acceso web a la colección.
[*]Actualización automática de la colección en los equipos clientes.
[*]Sería un plus no necesitar compilar nada para instalar (tengo un impedimento cognitivo para quitar programas instalados a través de "make install", por lo que si decido que la solución propuesta no me sirve, va a quedar instalada hasta el fin de los tiempos).
[*]Simpleza en la configuración.
[*]Sería necesario no tener que hacer más que abrir el reproductor multimedia para que el servicio funcione (o sea, nada de andar montando discos en red, o configurando servicios cada vez que se quiera escuchar un tema).
[/LIST]

**Ejemplo del uso deseado**:

Desde una de las notebooks abrir un reproductor multimedia (el preferido de la casa es el Amarok, pero es negociable =D), elegir un disco de la colección (ubicada en el disco externo del equipo de escritorio) y escucharla como si de archivos locales se tratarse. Nada de navegar por páginas web o directorios, todo desde dentro del reproductor multimedia. Nada de macumbas previas al uso del reproductor multimedia.

Se valoran mucho las experiencias de uso, ya que eso permite preguntar detalles del funcionamiento que no se saben al leer las descripciones de los programas.

Espero no haberme equivocado de foro.

Saludos, Anibal

---

### Post by z37a on 2009-06-15
Yo lo resolví de la siguiente manera:

- Server Ubuntu Linux
- NFS
- SAMBA(solo si hay desktop Windows)
- DNS
- DHCP con ips estaticas

Puse en marcha el server, por NFS monte en todos los equipos Linux monte en el /mnt/fs todo el contenido como un file server. Por seguridad les puse a las pcs ips estaticas mediante DHCP(por que si les quiero cambiar la ip lo hago desde el server y no maquina por maquina) dandole acceso total al NFS solo a las IPS que yo determine. Luego en cada home del usuario reemplaze la carpeta Musica pro un link symbolico al /mnt/fs/Musica y configure en cada equipo que la boiblioteca musical este en /home/musica. El DNS lo utilize para darle un nombre al server y asi desde la laptop donde este conecte via internet de ser necesario y tener acceso toal(cosa que va muy lento gracias al upstream de Fibertel!!!

PD: Como extra al mismo server le puse unas cosillas mas que pueden resultarte utiles, por ejemplo TorrentFlux-B4rt, un cliente torrent que funciona con interfaz web, que descarga todo automaticamente en el mismo /mnt/fs que esta compartido, y bueno un CUPS como print server, donde me queda registrado cuanto imprime cada usuario y a la vez puedo imprimir desde la laptop en la calle fuera de casa en mi casita.

PD2: Seguramente me sarpe escribiendo mal, si no entendes algo pregunta nomas que te lo detallo mejor!!!!

---

### Post by Mauro22 on 2009-06-15
Mi mejor opcion seria comprar un disco de red y santo remedio...


Desde mi punto de vista es la solucion mas sencilla y ""barata""... y trabaja independiente de cualquier maquina, simplemente se conecta al router y hasta podes acceder desde el exterior de la LAN.

---

### Post by ado@linux on 2009-06-15
Muchas gracias a ambos por las respuestas :p.

Mauro, el disco en red está descartado porque no tengo pensado comprar un case con soporte de red por el momento. Sé que es una buena opción, pero no ahora, quiero aprovechar el hard que ya tengo instalado.

z37a, en casa por el momento el tema de asignación de IP en la red lo maneja el router, y preferiría no cambiarlo. Me tengo que fijar cuan amigo de las IP estáticas es el mismo, pero creo que poco. Voy a tener en cuenta tu recomendación porque me permitiría seguir usando el Amarok en los 3 equipos, aunque prefiero escaparle a los directorios compartidos. Si ir más lejos, ayer mi novia no podía acceder a los direcetorios compartidos en mi equipo, y no encontramos la fuente del error, tocó joderse. Preferiría descansar sobre un programa que me ahorre un dolor de cabeza como ese, en vez de un share común y corriente. 
También me pasa que cada vez que reconecto el disco (es externo) el share del directorio compartido dentro del mismo desaparece y tengo que hacerlo de nuevo. Ese tipo de cosas las quiero evitar.

---

### Post by juancarlospaco on 2009-06-15
Yo te diria **proba el Sockso**, 
es un Servidor de musica stand-alone, portable, no se instala,
se descomprime el tar.gz y se ejecuta un .sh y ya esta andando,
la interfaz grafica de control esta hecha en Java,
te levanta una web *(sin instalar apache ni nada)* en PHP,
con reproductores Flash libres, reproductores simples,
podes distribuir por ese medio listas de musica compatibles con Amarok, iTunes, Winamp, etc.
permite autenticacion de los usuarios que se conectan a la web,
tiene un navegador de caratulas "estilo iTunes"*(busca solo las caratulas en internet)*,
es facil de modificar la web por defecto, permite descargar listas y mp3,
y un par de cosas mas.
Sus dependencias son Java, y ninguna mas.

*Probalo, no se si es lo que andabas buscando, pero es simple y funcional.*

---

### Post by z37a on 2009-06-15
> **ado@linux said:**
> Muchas gracias a ambos por las respuestas :p.

Mauro, el disco en red está descartado porque no tengo pensado comprar un case con soporte de red por el momento. Sé que es una buena opción, pero no ahora, quiero aprovechar el hard que ya tengo instalado.

z37a, en casa por el momento el tema de asignación de IP en la red lo maneja el router, y preferiría no cambiarlo. Me tengo que fijar cuan amigo de las IP estáticas es el mismo, pero creo que poco. Voy a tener en cuenta tu recomendación porque me permitiría seguir usando el Amarok en los 3 equipos, aunque prefiero escaparle a los directorios compartidos. Si ir más lejos, ayer mi novia no podía acceder a los direcetorios compartidos en mi equipo, y no encontramos la fuente del error, tocó joderse. Preferiría descansar sobre un programa que me ahorre un dolor de cabeza como ese, en vez de un share común y corriente. 
También me pasa que cada vez que reconecto el disco (es externo) el share del directorio compartido dentro del mismo desaparece y tengo que hacerlo de nuevo. Ese tipo de cosas las quiero evitar.

Pero compartistes por samba o por NFS???? por que NFS es el nativo de Linux, y para evitar problemas solo con tener los mismos usuarios en el mismo orden en todos los equipos ya tenes solucionado, es como si montaras una particion real en tu sistema.

---

### Post by sebastianabate on 2009-06-16
Acá tenés un minitutorial de lo que necesitás: un servidor DAAP con mt-daapd, para poderl acceder tu música desde cualquier aplicación que soporte este protocolo (como Amarok, Itunes, Windows Media Player, etc.)

[http://bloqnum.com/posts/howto-compartir-la-musica-en-red-con-amarok/](http://bloqnum.com/posts/howto-compartir-la-musica-en-red-con-amarok/)

Fijate que mt-daapd está en los repositorios, y es muy simple de configurar.

Te aclaro que yo no lo puse a funcionar, pero lo tenía visto porque un cliente me había hecho la misma pregunta que vos (aunque nunca se implementó)

---

### Post by ado@linux on 2009-07-08
Gracias a todos nuevamente. Finalmente me decanté por el MT-DAAP y anda 10 puntos. Sólo tiene como contra que tengo que usar rythmbox en vez de Amarok, pero bueno, sobreviviré.

El Sockso parece bueno, pero no cumple con el requisito de permitirme usar un reproductor local tipo Amarok, sino que tengo que usar uno flash en una web, y dista de ser lo ideal.

Gracias nuevamente!

---

