---
title: "Radio online"
date: 2010-05-10
forum: Software
---

### Post by capcabgue on 2010-05-10
Hola a todos:

Les cuento que uso ubuntu desde hace mucho tiempo, actualmente estoy con la 9.10 64 bits, en un notebook dell inspiron 1525, intel core 2 duo.
Bueno lo que yo he querido hacer es escuchar la radio online (infinita, play, sonar, universo, concierto, es decir cualquiera) y no he podido. 
Modifique el config de mozilla instalé unos plugins para vlc, mplayer agregue la radio (url) a rhytmbox y aún así no he podido escuchar las radios de ninguna manera.
Bueno finalmente modifiqué una shell para oir radio desde la terminal (haciendo uso de mplayer)pero bueno de todas las radios que conseguí la url solamente puedo escuchar unas pocas.
MI pregunta es si alguien sabe como puedo hacer para oir radios desde internet, ya sea desde la misma página o agregandola a un reproductor.

Gracias y espero que me puedan ayudar.

PD: les dejo el script que use para oir música

#!/bin/bash
#
# Llama a mplayer, segun la radio indicada
# $Id: radio,v 1.8 2007-01-04 14:48:32 javier Exp $
# Fixes en etapa de ejecucion por Arturo 'Buanzo' Busleiman
# - 20070104

case "$1" in

#
# Radios Chilenas
#
biobio) # Radio Bio Bio
    URII='http://ifx.laradio.cl:8002/32K'
;;
concierto) # Radio Concierto
    URII='mms://streaming.iberoamerican.cl/concierto'
;;
cooperativa) #Radio Cooperativa
    URII='http://www.cooperativa.cl/prontus_nots/prontus/player_streaming/chile.m3u'
;;
corazon) #Radio Corazon
    URII='http://streaming.iberoamerican.cl/corazon'
;;
tiempo) # Radio Tiempo
    URII='mms://200.27.214.28/fmtiempo'
;;
futuro) # Radio Futuro
    URII="mms://streaming.iberoamerican.cl/futuro"
;;
infinita) # Radio Infinita
    URII='mms://200.27.214.28/infinita'
;;
activa) # Radio Activa
    URII='http://66.175.96.10/clractiva'
;;
rp) # Rock & Pop
    URII='http://streaming.iberoamerican.cl/rockandpop'
;;
universo) # Radio Universo
    URII='http://200.24.230.152/'
;;
play) # Radio Play
    URII='mms://wms02.mediastream.cl/playfm?MSWMExt=.asf'
;;
sonar) # radio Sonar
    URI='mmsh://wms02.mediastream.cl/sonarfm'
;;
#
# Television
#
chilevision) # Chilevision
    URII="mms://201.238.232.211/chv"
;;
canal13) # Canal 13
    URII="http://streaming.entelchile.net/canal13"
;;
#
# Otras radios
#
kehuelga) # Radio libre y social 102.9FM >
    URII="http://www.kehuelga.org:8000/radio.mp3"
    #Aca estan otros espejos en caso de saturacion:
    #[http://stream.r23.cc:2323/kehuelga.mp3](http://stream.r23.cc:2323/kehuelga.mp3)
    #[http://radio.indymedia.org:8000/radiozapote-alta.mp3.m3u](http://radio.indymedia.org:8000/radiozapote-alta.mp3.m3u)
    #[http://radio.indymedia.org:8000/appo.mp3.m3u](http://radio.indymedia.org:8000/appo.mp3.m3u)
;;
*)
    echo "
    Uso: radios [Emisora]

    biobio ( Radio Bio Bio )
    concierto ( Radio Concierto )
    cooperativa ( Radio Cooperativa )
    corazon ( Radio Corazon )
    tiempo ( Radio Tiempo )
    futuro ( Radio Futuro )
    infinita ( Radio Infinita )
    activa ( Radio Activa)
    rp ( Radio Rock pop )
    universo ( Radio Universo )
    play ( Radio Play )
    sonar ( Radio Sonar )

    chilevision ( Chilevision ) (Televisión en directo)
    canal13 (Canal 13 ) (Televisión en directo)
    "
    exit 1
;;
esac
mplayer -af lavcresample=44100 -cache 32 "$URII"

---

### Post by Carlos C on 2010-05-10
probé con la primera que nombras, la infinita. Entré en su página y pude escuchar la radio. No recuerdo haber instalado nada aparte del flash y el plugin de vlc.

---

### Post by asterix77 on 2010-05-10
Yo tuve un problema similar, no podía escuchar las radios. El problema era Firestarter que lo tenía programado en modo restrictivo. Así es que si lo tienes, verificalo.

Te dejo mi scrip para escuchar radios.

#!/bin/sh
# script para agregar emisoras favoritas

clear
echo "##################################"
echo "#    Radioemisoras Favoritas     #"
echo "##################################"
echo ""
echo "Por favor elige su emisora desde la siguiente lista "
echo ""
echo "************************************"
echo "1 >Radio Cooperativa"
echo "2 >Radio BioBio"
echo "3 >Radio El Conquistador"
echo "4 >Radio Radio Ambrosio"
echo "5 >Radio FM Dos"
echo "6 >Radio Play FM"
echo "7 >Radio Rock&Pop"
echo "8 >Radio Tornagaleones"
echo "9 >Radio Infinita FM"
echo "10 >Salir del Programa"
echo ""
echo ""
read radio
if [ "$radio" = "1" ]; then
mplayer [http://209.88.205.240:80](http://209.88.205.240:80)
elif [ "$radio" = "2" ]; then
mplayer [http://ifx.laradio.cl:8000/32K.m3u](http://ifx.laradio.cl:8000/32K.m3u)
elif [ "$radio" = "3" ]; then
mplayer mms://200.27.86.250/radioconquistador
elif [ "$radio" = "4" ]; then
mplayer [http://sc.digitalproserver.com:9420](http://sc.digitalproserver.com:9420)
elif [ "$radio" = "5" ]; then
mplayer [http://streaming.iberoamerican.cl/fmdos](http://streaming.iberoamerican.cl/fmdos)
elif [ "$radio" = "6" ]; then
mplayer [http://wms02.mediastream.cl/playfm](http://wms02.mediastream.cl/playfm)
elif [ "$radio" = "7" ]; then
mplayer [http://streaming.iberoamerican.cl/rockandpop](http://streaming.iberoamerican.cl/rockandpop)
elif [ "$radio" = "8" ]; then
mplayer mms://tornagaleones.dyndns.org:1180
elif [ "$radio" = "9" ]; then
mplayer mms://200.27.214.28/infinita
elif [ "$radio" = "10" ]; then
exit
fi
#FIN


Por si acaso, debes darle permiso de ejecución

#sudo chmod +x yyyyy , donde y es el nombre que le has asignado al script, y luego lo ejecutas en consola.


Saludos

---

### Post by capcabgue on 2010-05-10
> **asterix77 said:**
> Yo tuve un problema similar, no podía escuchar las radios. El problema era Firestarter que lo tenía programado en modo restrictivo. Así es que si lo tienes, verificalo.

Te dejo mi scrip para escuchar radios.


Gracias, sin embargo probé el script de asterix 77 y bota en varias radios, cuando esta llenando el caché para oir la mñusica, supongo que es un problema de internet.

Respecto al dato que me dieron de firestarter me pueden decir como soluciono esto, ya que ni siquiera tenía instalado este SW, yo utilizo para navegar Mozilla firefox.

Respecto al uso del script, me autorizas a incluir las radios que yo escucho asterix77.

Gracias.

Por otra parte que puedo hacer para escuchar radio directamente desde mozilla, me falta algo que instalar, tengo algún tipo de restricción.

---

### Post by neen on 2010-05-10
I wish I understood ha

---

### Post by capcabgue on 2010-05-14
Gracias Asterix77, he utilizado tu script.
Bueno pero volviendo a mi pregunta original, comoo puedo hacer para escuchar la radio desde el browser mismo, sin tener que agregar una radio al script. Alguien sabe como se puede resolver el problema.

Gracias

---

### Post by bernajohn on 2010-05-16
gracias e script de [asterix77]("http://ubuntuforums.org/member.php?u=840386") funciona perfecto, solo tuve que modificar algunas direcciones.

#!/bin/sh
# script para agregar emisoras favoritas

clear
echo "##################################"
echo "# Radioemisoras Favoritas #"
echo "##################################"
echo ""
echo "Por favor elige su emisora desde la siguiente lista "
echo ""
echo "************************************"
echo "1 >Radio Cooperativa"
echo "2 >Radio BioBio"
echo "3 >Radio El Conquistador"
echo "4 >Radio Radio Ambrosio"
echo "5 >Radio FM Dos"
echo "6 >Radio Play FM"
echo "7 >Radio Rock&Pop"
echo "8 >Radio Pudahuel"
echo "9 >Radio Infinita FM"
echo "10 >Salir del Programa"
echo ""
echo ""
read radio
if [ "$radio" = "1" ]; then
mplayer [http://209.88.205.240:80](http://209.88.205.240:80)
elif [ "$radio" = "2" ]; then
mplayer [http://online.laradio.cl:8000/32K](http://online.laradio.cl:8000/32K)
elif [ "$radio" = "3" ]; then
mplayer mms://200.27.86.250/radioconquistador
elif [ "$radio" = "4" ]; then
mplayer [http://sc.digitalproserver.com:9420](http://sc.digitalproserver.com:9420)
elif [ "$radio" = "5" ]; then
mplayer [http://66.165.172.171/CLFMDOS](http://66.165.172.171/CLFMDOS)
elif [ "$radio" = "6" ]; then
mplayer [http://wms02.mediastream.cl/playfm](http://wms02.mediastream.cl/playfm)
elif [ "$radio" = "7" ]; then
mplayer [http://66.165.172.171/CLROCKPOP](http://66.165.172.171/CLROCKPOP)
elif [ "$radio" = "8" ]; then
mplayer [http://66.165.172.171/CLPUDAHUEL](http://66.165.172.171/CLPUDAHUEL)
elif [ "$radio" = "9" ]; then
mplayer mms://200.27.214.28/infinita
elif [ "$radio" = "10" ]; then
exit
fi
#FIN

---

### Post by capcabgue on 2010-05-26
Bueno, hola a todos. Volviendo al tema de escuchar directamente desde la página, alguien sabe como hacerlo, o intentar una forma que me permita comenzar el metodo de error y ensayo, hasta pillar una solución.

Gracias

---

### Post by capcabgue on 2010-06-02
Estoy siendo un poco majadero con el tema, pero es que encuentro vergonzoso tener que abrir virtualbox windows así poder escuchar las radios online.
En linux, si bien es cierto puedo escucharlas con el script de asterix77, pero a lo más mínimo se corta (y las sigo escuchando en windows). Además encuentro poco práctico si quiero escuchar una radio que no tengo en el script editarlo cada vez que incluyo una radio.

En fin alguien me puede ayudar a tratr de solucionar este problema de no oir las radios desde las páginas web de cada emisora.

Quizas sirva comoo antecedente o quizás no, si me meto a youtube y trato de ver un video me indica que un erro ha ocurrido, que lo intente más tarde (An error occurred. please try again later).
Espero sirva de algo para resolver lo de las radios.
En caso que no sea útil me pueden decir para abrir un hilo con este error en youtube.

Gracias
PD: en windows si puedo ver videos

---

### Post by EnriqueK on 2010-06-03
Resulta que los flash que se instalan via repositorios son todos para 32 bits, por lo tanto 
1.- El primer paso es desinstalarlos a todos ya sea el flashplugin-nonfree , el flashplugin-installer y gnash y todo que "huela" a fLash.
2.- Entra a la carpeta oculta .mozilla situafa en tu directorio personal y te fijas si allí existe una carpeta denominada "plugins", si no es así la creas.
Entra al sitio experimental de Adobe y te descargas el Flash para 64 bits
[http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)
3,. Por último descomprimes el archivo que has bajado (libflashplayer.so) y lo pones dentro de la carpeta "plugins" y eso sería todo.
Otra cosa, si ya tuvieras la carpeta ·"plugins", te fijas si tiene algún flash metido allí, en ese caso, lo borras antes de poner el que has bajado.

---

### Post by capcabgue on 2010-06-03
> **EnriqueK said:**
> 
2.- Entra a la carpeta oculta .mozilla situafa en tu directorio personal y te fijas si allí existe una carpeta denominada "plugins", si no es así la creas.
Entra al sitio experimental de Adobe y te descargas el Flash para 64 bits
[http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)

Gracias EnriqueK:

Te pasaste, por lo menos ahora con las radios que hice la pruba funcionó perfectamente.
en definitiva quedo SOLUCIONADO.

Gracias y espero que a alguien más sea útil

---

