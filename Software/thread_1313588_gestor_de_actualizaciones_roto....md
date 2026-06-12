---
title: "gestor de actualizaciones roto..."
date: 2009-11-03
forum: Software
---

### Post by granjero on 2009-11-03
prendí la maquina y veía un simbolito de contramano en el panel superior... me asusté un toque... después me di cuenta que no era tan grave

o si?

ahí les dejo dos capturas a ver si saben como solucionarlo...
 

```

Ha ocurrido un problema imposible de corregir cuando se inicializaba la información de los paquetes.

Por favor, informe de ésto como un fallo en el paquete «update-manager» e incluya el siguiente mensaje de error:

'E:Error de lectura - read (5 Error de entrada/salida), E:No se pudieron analizar o abrir las listas de paquetes o el archivo de estado.'
```


apt en una terminal me da este resultado:

```
jm@pcjm:~$ sudo apt-get check
Leyendo lista de paquetes... ¡Error!
E: Error de lectura - read (5 Error de entrada/salida)
E: No se pudieron analizar o abrir las listas de paquetes o el archivo de estado
```


```
jm@pcjm:~$ sudo apt-get update
Obj http://ppa.launchpad.net jaunty Release.gpg                                
Ign http://ppa.launchpad.net jaunty/main Translation-es                        
Obj http://packages.medibuntu.org jaunty Release.gpg                           
Ign http://packages.medibuntu.org jaunty/free Translation-es                   
Ign http://packages.medibuntu.org jaunty/non-free Translation-es               
Obj http://security.ubuntu.com jaunt
Obj http://ar.archive.ubuntu.com jaunty-updates/universe Sources               
Obj http://ar.archive.ubuntu.com jaunty-updates/multiverse Packages            
Obj http://ar.archive.ubuntu.com jaunty-updates/multiverse Sources             
Descargados 1988kB en 42s (47,2kB/s)                                           
Leyendo lista de paquetes... Hecho
W: Error de GPG: http://deb.opera.com stable Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY F9A2F76A9D1A0061
W: Tal vez quiera ejecutar 'apt-get update' para corregir estos problemas


```

muchas gracias por su tiempo!


salud!

---

### Post by josecuervo86 on 2009-11-03
Granjero, fijate que tenes ppa's de Jaunty y esos son los que estan fallando. Vas a tener que cambiarlos

---

### Post by granjero on 2009-11-03
josecuervo86, gracias jose cuervo....

lo quise borrar del /etc/apt/sources.list pero no estaba la linea...

entonces fui por sistema>administración>origenes del software y ahí estaban las lineas....

yo pensaba que las iba a encontrar en el sources.list

pero ya se solucionó y ya bajo un par de actualizaciones!

salud!

---

### Post by josecuervo86 on 2009-11-03
Granjero, esas deberian estar en /etc/apt/sources.list.d

Saludos!

Te agrego mas, porque tal vez esos repos te eran utiles, casi seguramente reemplazando **Jaunty** por **Karmic** talvez salgan andando :)

---

### Post by granjero on 2009-11-03
uso jaunty todavía y eran repos del opera que 
lo desinstalé! ;) 

\\:D/

---

### Post by josecuervo86 on 2009-11-03
Ahh, entonces se te trababa por eso, jeje. De cualquier manera llegamos a buen puerto! \\:D/

---

### Post by guillermolisi on 2009-11-04
> **granjero said:**
> uso jaunty todavía y eran repos del opera que 
lo desinstalé! ;) 

\\:D/
Entonces esta solucionado, resuelto ?

---

### Post by granjero on 2009-11-04
pensaba que sí, pero hoy de nuevo tengo el signo de contramano!

ahora yo ni abre el gestor de actualizaciones....

quiere aparecer pero se cierra al instante!


```
jm@pcjm:~$ sudo apt-get update
[sudo] password for jm: 
Obj http://security.ubuntu.com jaunty-security Release.gpg                     
Ign http://security.ubuntu.com jaunty-security/main Translation-es             
Obj http://ar.archive.ubuntu.com jaunty Release.gpg                            
Obj http://ar.archive.ubuntu.com jaunty/main Translation-es                    
Obj http://packages.medibuntu.org jaunty Release.gpg                           
Ign http://packages.medibuntu.org jaunty/free Translation-es                   
Ign http://packages.medibuntu.org jaunty/non-free Translation-es               
Ign http://security.ubuntu.com jaunty-security/restricted Translation-es       
Ign http://security.ubuntu.com jaunty-security/universe Translation-es         
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-es       
Obj http://security.ubuntu.com jaunty-security Release                         
Obj http://ppa.launchpad.net jaunty Release.gpg                                
Ign http://ppa.launchpad.net jaunty/main Translation-es                        
Obj http://ar.archive.ubuntu.com jaunty/restricted Translation-es              
Obj http://ar.archive.ubuntu.com jaunty/universe Translation-es             
Obj http://ar.archive.ubuntu.com jaunty/multiverse Translation-es           
Des:1 http://ar.archive.ubuntu.com jaunty-updates Release.gpg [189B]        
Ign http://ar.archive.ubuntu.com jaunty-updates/main Translation-es         
Ign http://ar.archive.ubuntu.com jaunty-updates/restricted Translation-es   
Ign http://ar.archive.ubuntu.com jaunty-updates/universe Translation-es     
Ign http://ar.archive.ubuntu.com jaunty-updates/multiverse Translation-es   
Obj http://ar.archive.ubuntu.com jaunty Release                             
Obj http://ppa.launchpad.net jaunty Release.gpg                                
Ign http://ppa.launchpad.net jaunty/main Translation-es                        
Obj http://ppa.launchpad.net jaunty Release.gpg                                
Ign http://ppa.launchpad.net jaunty/main Translation-es                        
Obj http://ppa.launchpad.net jaunty Release                                    
Obj http://packages.medibuntu.org jaunty Release                               
Des:2 http://ar.archive.ubuntu.com jaunty-updates Release [57,9kB]             
Obj http://security.ubuntu.com jaunty-security/main Packages                   
Obj http://ppa.launchpad.net jaunty Release                                    
Obj http://ppa.launchpad.net jaunty Release                                    
Obj http://packages.medibuntu.org jaunty/free Packages                         
Obj http://security.ubuntu.com jaunty-security/restricted Packages             
Obj http://security.ubuntu.com jaunty-security/main Sources                    
Obj http://security.ubuntu.com jaunty-security/restricted Sources              
Obj http://security.ubuntu.com jaunty-security/universe Packages               
Obj http://ppa.launchpad.net jaunty/main Packages                              
Obj http://ppa.launchpad.net jaunty/main Sources                               
Obj http://packages.medibuntu.org jaunty/non-free Packages                     
Obj http://security.ubuntu.com jaunty-security/universe Sources                
Obj http://security.ubuntu.com jaunty-security/multiverse Packages             
Obj http://security.ubuntu.com jaunty-security/multiverse Sources              
Obj http://ppa.launchpad.net jaunty/main Packages                              
Obj http://ppa.launchpad.net jaunty/main Sources
Obj http://ppa.launchpad.net jaunty/main Packages                             
Obj http://ppa.launchpad.net jaunty/main Sources                              
Obj http://ar.archive.ubuntu.com jaunty/main Packages                         
Obj http://ar.archive.ubuntu.com jaunty/restricted Packages
Obj http://ar.archive.ubuntu.com jaunty/main Sources
Obj http://ar.archive.ubuntu.com jaunty/restricted Sources
Obj http://ar.archive.ubuntu.com jaunty/universe Packages
Obj http://ar.archive.ubuntu.com jaunty/universe Sources
Obj http://ar.archive.ubuntu.com jaunty/multiverse Packages
Obj http://ar.archive.ubuntu.com jaunty/multiverse Sources
Des:3 http://ar.archive.ubuntu.com jaunty-updates/main Packages [207kB]
Des:4 http://ar.archive.ubuntu.com jaunty-updates/restricted Packages [2599B]
Des:5 http://ar.archive.ubuntu.com jaunty-updates/main Sources [57,5kB]
Des:6 http://ar.archive.ubuntu.com jaunty-updates/restricted Sources [509B]
Des:7 http://ar.archive.ubuntu.com jaunty-updates/universe Packages [88,8kB]
Des:8 http://ar.archive.ubuntu.com jaunty-updates/universe Sources [24,3kB]
Des:9 http://ar.archive.ubuntu.com jaunty-updates/multiverse Packages [8128B]  
Des:10 http://ar.archive.ubuntu.com jaunty-updates/multiverse Sources [2505B]  
Descargados 449kB en 6s (70,9kB/s)                                             
Fallo de segmentaciónetes... 0%

```

yo no se si será esto a raiz de un apagon que hubo en casa hace unos días.

tuve que correr el fsck para que arregle un par de cosas rotas....

salud!

---

### Post by guillermolisi on 2009-11-04
Podrias volver a mostrar el contenido de /etc/apt/sources.list y /etc/apt/sources.list.d ?

---

### Post by granjero on 2009-11-04
sources.list

```
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ar.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://ar.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ar.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://ar.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ar.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://ar.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://ar.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://ar.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ar.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://ar.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://ar.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://ar.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ar.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://ar.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse

#gnome do 0.8.2
deb http://ppa.launchpad.net/do-core/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/do-core/ppa/ubuntu jaunty main

#emesene crazy 1.5
deb http://ppa.launchpad.net/bjfs/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/bjfs/ppa/ubuntu jaunty main

#ifuse
deb http://ppa.launchpad.net/jonabeck/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/jonabeck/ppa/ubuntu jaunty main
```


```
jm@pcjm:~$ ls /etc/apt/sources.list.d
medibuntu.list  medibuntu.list.save  opera.list  opera.list.save

```

---

### Post by granjero on 2009-11-04
agrego esto...

```
jm@pcjm:~$ sudo update-manager 
Fallo de segmentación

```

---

### Post by granjero on 2009-11-04
y agrego esto:

```
jm@pcjm:~$ apt-get check
E: No se pudo abrir el fichero de bloqueo '/var/lib/dpkg/lock' - open (13 Permiso denegado)
E: Imposible bloquear el directorio de administración (/var/lib/dpkg/), ¿es superusuario?
jm@pcjm:~$ sudo apt-get check
[sudo] password for jm: 
Fallo de segmentaciónetes... 0%

```

de paso hay un error de traducción que no se donde hay que reportar...

Fallo de "***segmentaciónetes***"

salud!

---

### Post by granjero on 2009-11-04
Encontré esta solución :

I had a similar problem in the past and solved it by adding the following line 
in /etc/apt/apt.conf (create the file if you don't have one) :

APT::Cache-Limit "100000000";

then re-run apt-get update

try a higher value if it does not work, but I don't know what it means exactly 
so maybe there's a risk of breaking something.

[http://linux.derkeiler.com/Mailing-Lists/Debian/2007-03/msg01530.html](http://linux.derkeiler.com/Mailing-Lists/Debian/2007-03/msg01530.html)

que opinan ?

---

### Post by granjero on 2009-11-04
bueno al final esa no era la solución pero la terminé encontrando en un foro de ubuntu venezuela...

lo que hice fue abrir sistema>administración>origenes del software

ahí destildé **absolutamente** todo.

después cerré, me pidió recargar los repos, le di que sí, y después volví a abrir y a tildar todo.

parece haber funcionado..

sudo apt-get update
sudo apt-get upgrade
sudo apt-get check

esos tres comandos dan ok!

[http://www.ubuntu-ve.org/node/2490](http://www.ubuntu-ve.org/node/2490)

---

### Post by guillermolisi on 2009-11-05
En algun momento hubo reportes sobre problemas con los repositorios de Opera para Jaunty. Comento porque tal vez tambien estaba jugando este tema en tu caso.

Deja pasar unos dos o tres dias y si no tenes mas problemas, por favor marca el thread como resuelto.

---

### Post by granjero on 2009-11-05
otra vez hoy a la mañana el gestor estaba roto...

ya google me dio todo lo que me podia dar... lo que voy a probar hoy a la noche cuando llegue a casa es volver a destildar todo. y empezar a tildar un casillero por dia

para ver que es lo que genera el conflicto...

si no no se me ocurre que más hacer...

alguien tiene más ideas?


salud!

---

### Post by guillermolisi on 2009-11-05
> **granjero said:**
> otra vez hoy a la mañana el gestor estaba roto...

ya google me dio todo lo que me podia dar... lo que voy a probar hoy a la noche cuando llegue a casa es volver a destildar todo. y empezar a tildar un casillero por dia

para ver que es lo que genera el conflicto...

si no no se me ocurre que más hacer...

alguien tiene más ideas?


salud!
Deshabilita los repos de Opera para ver si despues de eso no se vuelve a repetir el incidente.

---

### Post by granjero on 2009-11-05
ya están borrados los de opera....

o eso creo.

borre dos archivos de /etc/apt/sources.list.d 


salud!

---

### Post by guillermolisi on 2009-11-05
> **granjero said:**
> ya están borrados los de opera....

o eso creo.

borre dos archivos de /etc/apt/sources.list.d 


salud!

Proba de hacer una actualizacion del cache de paquetes a ver que pasa.

---

### Post by granjero on 2009-11-05
> Proba de hacer una actualizacion del cache de paquetes a ver que pasa. 

ahí ya me perdí...

me tirás el comando?

---

### Post by guillermolisi on 2009-11-06
> **granjero said:**
> ahí ya me perdí...

me tirás el comando?
Lo hiciste cantidad de veces:
> después cerré, me pidió recargar los repos, le di que sí, y después volví a abrir y a tildar todo.

parece haber funcionado..

sudo apt-get update

Extractado de [este post]("http://ubuntuforums.org/showpost.php?p=8245584&postcount=14") tuyo :)

Actualizar el cache de repositorios es lo que llamaste recargar los repos.

---

### Post by granjero on 2009-11-07
hola acá yo de nuevo...

la actualización del cache de paquetes anda bien. también el upgrade y el check.

también le mande autoclean por si las moscas...

pero ahora tengo este error al tratar de actualizar el sistema....

dejo la captura de pantalla....

salud!

---

### Post by granjero on 2009-11-07
agrego:

```
jm@pcjm:~$ sudo apt-get upgrade -f
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Se actualizarán los siguientes paquetes:
  libgd2-noxpm libhtml-parser-perl pm-utils
3 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.
Se necesita descargar 0B/364kB de archivos.
Se utilizarán 8192B de espacio de disco adicional después de esta operación.
¿Desea continuar [S/n]? s
(Leyendo la base de datos ... dpkg: error fatal irrecuperable, abortando:
 files list file for package `adobe-flashplugin' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

---

### Post by josecuervo86 on 2009-11-07
Granjero, fijate este reporte del bug, que muestra una solución: [https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/108189](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/108189)

---

### Post by granjero on 2009-11-07
gracias josé...

hoy a la tarde me lo leo bien y me fijo si lo soluciono!

salud!

---

### Post by granjero on 2009-11-07
estuve leyendo pero entre el inglés y lo técnico me vi superado!

:-(

---

### Post by granjero on 2009-11-07
bué!

me mande con lo tapones de punta!

hice backup de todos los archivos de /var/lib/dpkg/info/adobe-flashplugin.LOQUESEA

y después borré todos los adobe-flashplugin.

le di apt-get upgrade y me instaló un par de actualizaciones y me salió un cartelito que decía que le faltaban los paquetes de flashplugin pero que iba a suponer que no estaban instalados.

asi que pareciera que está solucionado el tema...

lo que me gustaría es saber donde están rotos los archivos adobe-flashplugin.algo para restaurarlos...

en unos días le pongo solved si sigue andando!


salud!

---

### Post by josecuervo86 on 2009-11-07
Supuestamente estan rotos los binarios o por lo menos eso es lo que entendi. La verdad que mucho no se entiende lo que te pase, pero basicamente lo que hizo el flaco es lo que hiciste vos :)

---

### Post by granjero on 2009-11-07
si eso fue lo que entendí y por eso me mande por ahí...

gracias por la ayuda josecuervo y guillermolisi!!!!
=D>=D>=D>=D>=D>=D>

---

### Post by granjero on 2009-11-12
nuevamente el gestor está roto!

anteayer me bajo unas actualizaciones entre ellas una de firefox 3.5 y ahora el firefox ya no anda

y nuevamente tengo este mensaje al hacer sudo apt-get update:

```
Fallo de segmentaciónetes... 0%

```

no me deja instalar absolutamente nada!

salud!

---

### Post by guillermolisi on 2009-11-12
Agregaste o modificaste la lista de repositorios activos para esa maquina antes de hacer esta actualizacion ?

---

### Post by granjero on 2009-11-12
No no le modifique nada.  Solo quise instalar la ultima versión del vbox desde un paquete .deb y ahí me di cuenta  que de nuevo había problemas. 

Salud.

---

### Post by granjero on 2009-11-12
destildé todo en orígenes del software y se abrió el gestor de paquetes cuando ejecuté el .deb del Virtual box.

empezó a instalar hasta que....

también aparecieron en el escritorio estos directorios extraños

---

### Post by granjero on 2009-11-22
bump!

estoy sin poder instalar nada.... voy a tener que reinstalar?

---

### Post by guillermolisi on 2009-11-23
La verdad es que este caso es bastante particular.
Si los repositorios que estan activos estan bien, o sea son de la distribucion adecuada en uso y no hay otros repositorios especiales, tipo ppa o similares, extras, que puedan corromper la estructura del cache de tu maquina, no se me ocurre que otra razon que de origen a este problema en forma recurrente como vino sucediendo.

---

### Post by Mauro22 on 2009-11-23
[0] [http://74.125.47.132/search?q=cache:tjq2rCxyYxYJ:ba-k.com/showthread.php%3Ft%3D586589+synaptic+%2B+Fallo+de+segmentaciónetes...+0%25&cd=1&hl=es&ct=clnk&gl=ar](http://74.125.47.132/search?q=cache:tjq2rCxyYxYJ:ba-k.com/showthread.php%3Ft%3D586589+synaptic+%2B+Fallo+de+segmentaciónetes...+0%25&cd=1&hl=es&ct=clnk&gl=ar)
[1] [http://74.125.47.132/search?q=cache:VyC6fTB0TeYJ:https://answers.launchpad.net/ubuntu/%2Bquestion/85471+synaptic+%2B+Fallo+de+segmentaciónetes...+0%25&cd=2&hl=es&ct=clnk&gl=ar](http://74.125.47.132/search?q=cache:VyC6fTB0TeYJ:https://answers.launchpad.net/ubuntu/%2Bquestion/85471+synaptic+%2B+Fallo+de+segmentaciónetes...+0%25&cd=2&hl=es&ct=clnk&gl=ar)


Por ahi tenes suerte!

---

### Post by granjero on 2009-11-24
gracias mauro22 pero el error persiste! por un momento tuve esperanzas....

este viernes termino con mis exámenes y me voy a disponer a instalar KK...

es una lástima que no se halla podido solucionar el tema...

salud!

:frown::frown::frown::frown::frown::frown::frown:

---

### Post by fragua on 2010-01-10
Hola Granjero, 
Seguramente ya reinstalaste desde Noviembre.
Estuve con un problema en aptitude que daba el mensaje de Fallo de Segmentaciónetes
No me funcionó la técnica de comentar los repositorios.
Sin embargo, esta solución me funcionó a la primera:
[URL="http://sistemasoperativos.wordpress.com/2006/12/25/fallo-de-segmentacion-con-apt/"]http://sistemasoperativos.wordpress.com/2006/12/25/fallo-de-segmentacion-con-apt/
[/URL]

Se resuelve limpiando la carpeta de cache
sudo rm /var/cache/apt/*.bin
:popcorn:
Espero le funcione a alguien más.
Saludos,

---

### Post by erickelrojas on 2010-06-03
Solución:
[http://www.elleonplateadodeojosrojos.es/blog/apt/](http://www.elleonplateadodeojosrojos.es/blog/apt/)

---

