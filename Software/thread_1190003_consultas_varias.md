---
title: "consultas varias"
date: 2009-06-17
forum: Software
---

### Post by Barasuishou on 2009-06-17
HOLA, bueno bien por suerte después de varios problemas y soluciones al fin tengo las cosas corriendo bien, en mi kubuntu(que adoro =D), 

hace rato se que los .deb son fáciles de instalar, pero no tengo idea de como manejar los .tar.bz o .tar.bz2, como instalo esos?, me podrían decir paso a paso como hacer, ya hace tiempo había visto que debia hacer algo tipo make, make installer o algo así y salió totalmente para atrás :S

después en mi facultad estamos usando C#, ya instalé mono y monodevelop,  pero tengo este problema, quizás sea algo simple no se, la cuestion es que hago algo simple como tratar de tomar una entrada de teclado "Console.ReadLine();", y al ejecutar como que se ejecuta de corrido, osea ejecuta y termina, sin siquiera dejarme ingresar nada :S, es un problema de alguna configuración o el problema es que quizás lo estoy haciendo mal???

---

### Post by staar on 2009-06-17
los .tar.bz y .tar.bz2 son archivos comprimidos, como los .rar o los .zip, el software que se distribuye de esa forma no está compilado, tenés que hacerlo vos...

lo primero que se necesita para compilar un programa en ubuntu, es instalar el paquete build-essential ```
sudo aptitude install build-essential
``` que contiene las herramientas necesarias para compilar la mayoría de las cosas...

después, una vez bajado el archivo comprimido (las fuentes), se lo descomprime en alguna carpeta a elección, por ejemplo /home/*usuario*/*programa-versión*, y se navega, en una consola, hasta dicho directorio...

una vez allí, los comandos que se deban ejecutar dependen del programa (en la mayoría de los casos, se explica cuales son en el Readme que trae el mismo), pero los más comunes son ```
configure
``` luego ```
make
``` y finalmente ```
sudo make install
``` como dije, esos pasos pueden variar, depende del programa...


de mono, mejor no emito opinión....

saludos

---

### Post by clasificado on 2009-06-17
Buenas buenasssssss

1) .tar o .tar.gz es como decir .zip: Puede ser un programa, pueden ser fotos, puede ser cualquier cosa :D

Pero supongamos que queda bien claro que es un programa: el camino es este:
```
./configure
make
sudo checkinstall
```

- el ./configure lo prepara según lo que tengas instalado. Si falla en este paso es porque hay que instalar dependencias.
- el make lo compila, dandonos el ejecutable (.exe, .bin, o un ejecutable sin extensión, depende del lenguaje del programa)
- el checkinstall es como el "make install", lo instala en el sistema y te deja desinstalarlo mas adelante.

Pero no es garantia: el .deb es recontra estable, en los tar el procedimiento puede cambiar en el 10% de los casos, ponele.

2) ¿probaste ejecutar el binario desde la consola? el monodevelop de jaunty deja una carpeta "debug" con el bin ahi adentro. Digo para separar el problema, por ahi el ReadLine tiene una implementación diferente en Mono, o el monodevelop tenga algún problema particular

clasificado

pd: pobrecito mooooonooooo, acá lo tienen de hijo :P a mi me va

---

### Post by PablitoFlores on 2009-06-17
Hola gente..soy nuevo y espero q me puedan ayudarme, estoy empezando a interesarme en este sistema operativo que es ubuntu.
Mi problema es el siguiente, quiero bajar el ubuntu 9.04 y despues de un tiempo de empezar la descarga ésta se detiene llegando a descargar aproximadamente 200mb del sistema, alguien me podria decir a que se debe esto?... Eh verificado la conexion de internet y no es, asique esta descartado por lo menos a mi criterio.
Desde ya muchas gracias al que pueda ayudarme.
Saludos

---

### Post by pablo.s on 2009-06-17
> **PablitoFlores said:**
> quiero bajar el ubuntu 9.04 y despues de un tiempo de empezar la descarga ésta se detiene llegando a descargar aproximadamente 200mb del sistema, alguien me podria decir a que se debe esto?

Proba bajando la .ISO
por [Bit Torrent]("http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.iso.torrent").

---

### Post by Barasuishou on 2009-06-17
o sino encargá un cd, es fácil y llegan rápido

---

### Post by Barasuishou on 2009-06-18
pregunta clientes de mensajería instantanea o messengers, que o cual me recomiendan?

en lo posible busco uno que:
-que sea en lo posible de Qt, ya que uso kubuntu
-me permita emoticones personalizados
-transferencia de archivos
-fotos de contactos en la lista y en las ventanas de conversación
-(opcional) colores en los nicks estilo msn plus

mi cuenta es de hotmail XP, aunque estoy pensando en cambiarla ya que hotmail no lo abre el konqueror :S

ya e probado varios pero  logro decidir bien cual, hace muuucho usába el pidgin/gaim, y está bueno pero tuve problemas para pasar archivos, la vista de fotos es un poco fea ya que son chicas, y es de gtk

después probé el kopete, medio confuso de configurar, algo complicado el tema de las identidades, y me crasheo un par de veces :S

después de eso pase al kmess, de los mejores que probé, tenía casi todo lo que "quiero" en un messenger, pero no me cargaba los emoticones personalizados que me mandaban haciendo imposible la lectura de ciertos mensajes, y un día tuve problemas por que no me cambiaba el nick, osea yo lo veía diferente pero la gente que usa la cosa (xD) esa de microshot me decía que no así que quise probar otro

el último y junto con kmess me dejó muy contento el emesene, tiene colorcitos, avisos de mensaje y demás, muy bueno, pero tengo dos problemas, a veces no me cambia el nick o la foto, y la transferencias de archivos me es imposible, nunca llegan (ni salenn por así decirlo)

si me pueden dar una solución para el emesene o kmess sería bueno, 

sino con cual de los dos me recomiendan me quede? o que otro programa me recomiendan?

a y por cierto si cambio mi mail a cual recomiendan me cambie, tengan en cuenta todos mis contactos son o  @hotmail.com o @live.com o @gmail.com

---

### Post by sergiom99 on 2009-06-18
para cambiar de direccion de mail? Gmail sin duda.
Cliente? casi no uso la red de msn, pero tengo Kmess para msn y empathy para Gtalk.

---

### Post by SLA_leandrin on 2009-06-18
Mirá, tengo ahora kubuntu y el que mejorcito me ha funcionado por ahora es el kmess pero la versión 2, que aún está en beta, pero es muuuuy utilizable... te la recomiendo.

---

### Post by juancarlospaco on 2009-06-18
**Yo uso y recomiendo Gmail.**
Gmail tiene chat en el mail, 
te conecta con Identi.Ca *(clon libre de Tweeter)*.
Tengo redireccionado mi Hotmail*(apesta!)* a mi Gmail, 
todos los correos de Hotmail me llegan a Gmail. 

Para chatear uso Pidgin que conecta con Gmail, MSN, Identi.Ca.
Sino uso Emesene 2 desde el CVS de Mariano Guerra.

**Para pasar archivos ahora uso Ubuntu One.**

Antes *(o para gente que no se quiere hacer cuenta en Launchpad)* 
usaba para pasar archivos y fotos, 
lo hago independiente del programa de mensajeria,
con un comando de Python en un script de Bash:

mkdir --verbose $HOME/compartido/ ; cd $HOME/compartido/ ; python -m SimpleHTTPServer & ; firefox [http://www.whatsmyip.org/](http://www.whatsmyip.org/)

y le pasas esa direccion IP agregandole " :8000 " al final,
las cosas que quiero pasar van en la carpeta " compartido " 
dentro de mi Carpeta Personal.

Si no anda la VideoConferencia del emesene,
uso paginas como Fonomo.com

Igual..., 
programas para hacer Streaming de Video en Ubuntu hay, 
desde Motion hasta DimDim, es cuestion de instalarlos.

---

### Post by Barasuishou on 2009-06-18
a ver alguien me ayuda verán quería instalar el mod para doom3 de last man standing, así que lo descomprimí y quise mover el directorio ese a la carpeta de doom 3 donde va, pero al usar le comando cp -r * , me copio todo el home a la carpeta de doom3, entonces quise usar rm -r para borrarlo de ahí, y me borro el /home/ completo, como lo recupero?

---

### Post by josecuervo86 on 2009-06-18
Te aconsejaria que abrieras un nuevo thread para tu última consulta, asi no se arma despiole.

Consejo adicional: tene MUCHO cuidado con los comandos del tipo rm -r...

---

