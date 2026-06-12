---
title: "reproducir la radio de metro951.com"
date: 2008-08-11
forum: Software
---

### Post by eldragon on 2008-08-11
alguien puede decirme si es posible desde la web de la metro? yo no pude, no funciona muy bien que digamos en esta notebook (los botones del applet flash no responden)...

---

### Post by lega on 2008-08-11
no a mi tampoco me funciona, de todos modos te paso la dir por si no la tenes la pones en el mplayer (abrir url) y sale andando
 mms://200.59.146.10/radiometro-ba
Saludos

---

### Post by eldragon on 2008-08-11
gracias, justo eso buscaba yo, ahi la agregue al rhythmbox :D

---

### Post by faktorqm on 2008-08-12
Armamos un sticky? 

Yo escucho a petti a la mañana en "la 100". 

mms://streamla100.uigc.net/la100

---

### Post by eldragon on 2008-08-12
yo estaba por proponer algo asi.........recolectar todas las radios de argentina......y quiza armar un script que las agregue a rhythmbox.....

alguien sabe cual es la rock and pop? si es que tiene?

ahi la encontre: mms://200.59.146.10/rockandpop-ba

---

### Post by [P]oli on 2008-08-12
> **eldragon said:**
> yo estaba por proponer algo asi.........recolectar todas las radios de argentina......y quiza armar un script que las agregue a **rhythmbox**.....

alguien sabe cual es la rock and pop? si es que tiene?

ahi la encontre: mms://200.59.146.10/rockandpop-ba

Al Exaile me lo dejan afuera :(

---

### Post by faktorqm on 2008-08-12
yo uso vlc, con la lista me alcanza xD

agrego am del plata: mms://delplata.telecomdatacenter.com.ar/delplata que lka tengo a mano salu2!

---

### Post by [P]oli on 2008-08-12
[ Acá ](http://www.radiosargentina.com.ar/ARCD.htm#)dejo casi todas, es una recopilación de todas las radios de la Ciudad de Buenos Aires. Es un link directo a la página de la radio (o tele tmb). Para hacerlo andar en cualquier reproductor, hay que buscar en el código de fuente una dirección que empieze como mms://... o termine en .asx (generalmente es ../radio.asx)

Espero que les sirva, y si necesitan de otras ciudades, busco también

---

### Post by eldragon on 2008-08-12
> **'[P]oli said:**
> Al Exaile me lo dejan afuera :(

yo mencione rhythmbox porque es el que uso, y el oficial de ubuntu...

deberia de incluirse en la localizacion del sistema, toda la data sobre multimedia local tambien, de manera de que los programas puedan obtener de ahi la informacion necesaria sobre radios / television...etcetera...

pero no se ni donde empezar por sugerirlo, yo odio las conecciones por web, y rhythmbox hace todo tan simple que ni me caliento por otro programa.


asi que si alguien tiene mas links mms que los publique...yo los voy agregando al rhythmbox... :)

---

### Post by [P]oli on 2008-08-12
> **eldragon said:**
> yo mencione rhythmbox porque es el que uso, y el oficial de ubuntu...

deberia de incluirse en la localizacion del sistema, toda la data sobre multimedia local tambien, de manera de que los programas puedan obtener de ahi la informacion necesaria sobre radios / television...etcetera...

pero no se ni donde empezar por sugerirlo, yo odio las conecciones por web, y rhythmbox hace todo tan simple que ni me caliento por otro programa.


asi que si alguien tiene mas links mms que los publique...yo los voy agregando al rhythmbox... :)

Era en chiste lo que decía del Exaile ;)

y muy buena idea, tener una base de datos (en inernet o en cualquier lado) en donde aparezcan todas las radios argentinas, divididas por cuidad, etc etc

---

### Post by lega on 2008-08-12
yo uso el Mplayer con los demas no puedo conectar

Pop Radio [http://pop.telecomdatacenter.com.ar/pop](http://pop.telecomdatacenter.com.ar/pop)
Mega [http://mega.telecomdatacenter.com.ar/mega](http://mega.telecomdatacenter.com.ar/mega)
Kabul [http://streaming.elserver.com:9000/](http://streaming.elserver.com:9000/)

---

### Post by EnriqueK on 2008-08-12
Una alternativa a tener lista de reproducción es la de generar una especie de lanzador a cada emisión, el proceso sería el siguiente, se abre un archivo de textos y se pone
[Reference]

Ref1=URL de la transmision 

por ejemplo 
[Reference]

Ref1=mms://streamla100.uigc.net/la100

luego se guarda el archivo con el nombre de la emisora, luego para escucharla basta hacerle un doble click (previa definición del reproductor, puede ser VLC,mplayer, etc, yo uso el gnome-mplayer.

Otra cosa, si queremos grabar el streaming, abrimos un terminal en la carpeta donde queremos que se guarde y luego escribimos

mplayer -dumpstream mms://streamla100.uigc.net/la100
Esto va a generar un archivo stream.dump que luego podemos renombrar.

Otra cosa, una página domde creo están todas la emisoras es esta
[http://bahiadigital.com.ar/medios/radios/](http://bahiadigital.com.ar/medios/radios/)

---

### Post by lega on 2008-08-12
un extension de firefox excelente para escuchar las radios o ver tv es mediaplayer connectivity, una vez configurado abre todo en el reproductor que elijas, recomendado anda con firefox3, aclaro esto porque en los primeros tiempos no andaba pero ya hicieron una actualización [https://addons.mozilla.org/es-ES/firefox/search?q=mediaplayer](https://addons.mozilla.org/es-ES/firefox/search?q=mediaplayer)

---

### Post by [P]oli on 2008-08-13
> **eldragon said:**
> asi que si alguien tiene mas links mms que los publique...yo los voy agregando al rhythmbox... :)

[ Acá ](http://www.radiosargentina.com.ar/ARCD.htm)dejo casi todas, es una recopilación de todas las radios de la Ciudad de Buenos Aires. Es un link directo a la página de la radio (o tele tmb). Para hacerlo andar en cualquier reproductor, hay que buscar en el código de fuente una dirección que empieze como mms://... o termine en .asx (generalmente es ../radio.asx)

Espero que les sirva, y si necesitan de otras ciudades, busco también

---

### Post by victor_nesta on 2008-08-14
Perfecto probé La Voz de las Madres, que es la que escucho yo. Y camina sin drama.
Yo en guindows usaba el Screamer Radio que es un caño, trae once millones de radios prepogramadas y le agregas las que quieras y lo mejor que es libre. Estaría bueno que algún capo, lo convierta a Linux, pero ese es otro tema.
Ah, porque sali con lo del Screamer? Por que se puede extraer la Base de Datos de las muchisimas radios sin problema.

---

### Post by Duyos on 2008-08-15
Bueno, dando vueltas por ahi encontre este pequeño script al cual le agregue un par de radios.
AUTOR DEL SCRIPT: Arturo ‘Buanzo’ Busleiman. (blogs.buanzo.com.ar)
Aca les dejo una especie de tutorial para hacerlo funcionar:
1- copiar el codigo y pegarlo en un archivo de texto en tu carpeta de usuario que se llame .radios.sh (no olvidar el punto delante del nombre).
2- Dale permisos de ejecucion: chmod +x .radios.sh
3- Insertale un alias para llamarlo desde cualquier parte:
  para esto tenes que llamar al editor de textos desde la consola con un sudo (puede ser gedit, knote, vim, nano o lo que tengas)

 sudo gedit /home/USUARIO/.bashrc

(donde dice USUARIO va tu nombre de usuario.

agregale una linea al archivo que diga por ejemplo:

alias radios='sh /home/USUARIO/.radios.sh'
(acordate de cambiar USUARIO por tu nombre)
 Despues lo unico que tener que hacer es volver a iniciar tu session.

escribi radios
y te tiene que aparecer el menu con las radios
escribis radios y el nombre de la radio y listo

#!/bin/bash
#
# llama a mplayer, segun la radio indicada
#
# $Id: radio.sh,v 1.8 2007-01-04 14:48:32 javier Exp $
#
# Fixes en etapa de ejecucion por Arturo 'Buanzo' Busleiman
# <buanzo arroba buanzo.com.ar> - 20070104
# Otras radios y fixes menores por Vampii
# <vampii arroba buanzo.com.ar> - 20082304

case "$1" in

    #
    # radios argentinas
    #

    mitre) # Radio Mitre 792 AM
        URII='mms://streammitre.uigc.net/mitrevivo'
        ;;
    rp) # Rock and Pop
        URII="mms://200.59.146.10/rockandpop-ba"
        ;;
    delplata) # Del Plata AM 1030
        URII='mms://delplata.telecomdatacenter.com.ar/delplata'
        ;;
    radio10) # Radio 10 (Dolina) AM 710
        URII='mms://radio10.telecomdatacenter.com.ar/radio10'
        ;;
    continental) # AM 590 Continental
        URII='http://66.175.96.10/arcontinental'
        ;;
    los40) # Los 40 Principales
        URII='http://66.175.96.10/ARLOS40P'
        ;;
    mega) # Mega 98.3 Puro Rock Nacional
        URII='http://mega.telecomdatacenter.com.ar/mega'
        ;;
    fm100) # FM 100 99.9 rtsp://g2.prima.com.ar/vivo/cadena100.rm
        URII='rtsp://g2.prima.com.ar/vivo/cadena100.rm'
        ;;
    heavy) # HEAVYMETAL.COM.AR [http://65.254.42.234:15060/listen.pls](http://65.254.42.234:15060/listen.pls)
	URII="http://65.254.42.234:15060/listen.pls"
	;;
    america) # Radio 10 (Dolina) AM 710
        URII='mms://radio10.telecomdatacenter.com.ar/radio10'
        ;;
    fmsi) # 89.1 FM BA San Isidro
        # (requiere faad/aac)
        URII='http://streaming.euro-web.com.ar:8000'
        ;;
    dolina) # Radio 10 para escuchar a Dolina
   	 URII='mms://radio10.telecomdatacenter.com.ar/radio10'
  	  ;;
    kabul) # Kabul
    	URII='http://streaming.elserver.com:9000/'
    	;; 
    metro) # Metro - Sonido Urbano
    	URII='mms://200.59.146.10/radiometro-ba'
    	;;

    #
    # television
    #

    tn24) # TN 24 Horas
        URII="mms://wmedia01.uigc.net/TN"
        ;;

    #
    # otras radios
    #

    kehuelga) #Radio libre y social 102.9FM ::.K-HUELGA>
        URII="http://www.kehuelga.org:8000/radio.mp3"
        #Ac&#65533; est&#65533;n otros espejos en caso de saturaci&#65533;n:
        #[http://stream.r23.cc:2323/kehuelga.mp3](http://stream.r23.cc:2323/kehuelga.mp3)
        #[http://radio.resistenciacreativa.org.mx:8000/radioresisteincia.mp3.m3u](http://radio.resistenciacreativa.org.mx:8000/radioresisteincia.mp3.m3u)
        #[http://radio.indymedia.org:8000/radiozapote-alta.mp3.m3u](http://radio.indymedia.org:8000/radiozapote-alta.mp3.m3u)
        #[http://radio.indymedia.org:8000/appo.mp3.m3u](http://radio.indymedia.org:8000/appo.mp3.m3u)
        ;;

    *)
        echo "
  Uso: radio.sh opci&#65533;n

        mitre       ( Radio Mitre 792 AM )
        rp          ( Rock and Pop )
        delplata    ( AM 1030 )
        los40       ( Los 40 Principales )
        fm100       ( FM 100 99.9 )
	radio10     ( AM 710 )
        continental ( AM 590 )
        mega        ( Mega 98.3 Puro Rock Nacional )
        fmsi        ( 89.1 FM BA San Isidro )
        heavy       ( Radio Heavy )
        america     ( Radio América )
        dolina	    (Radio 10)
 	kabul       (radio Kabul)
        metro       (radio metro 95.1)
        
        kehuelga    ( Radio libre y social 102.9FM ::.K-HUELGA )
        
        tn24        ( TN 24 Horas )
        "
        exit 1
        ;;
esac

mplayer -af lavcresample=44100 -cache 32 "$URII"

---

