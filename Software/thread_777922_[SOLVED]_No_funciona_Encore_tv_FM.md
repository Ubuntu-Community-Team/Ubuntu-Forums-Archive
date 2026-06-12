---
title: "[SOLVED] No funciona Encore tv FM"
date: 2008-05-01
forum: Software
---

### Post by mfzeitune on 2008-05-01
Quiero saber si me pueden ayudar con la instalacion de la 
**" Encore Tv Fm Turner Pro (ENLTV) "** en **Ubuntu 8.04**ya instale el tvtime y no me la reconoce.
El ubuntu lo instale desde wubi que esta en la *.iso oficial.
ya trate de instalarlo como en otras versiones pero no me funciona y vi en una pagina que reconocia la sintonizadora de primera sin instalar nada.
Les aclaro que no se nada de ubuntu/linux asi que por favor les pido que me detallen lo mas posible las soluciones.(cabe aclarar que la placa funciona sin inconvenientes en windows).

Muchas gracias y espero ayuda.

---

### Post by Mauro22 on 2008-05-01
Yo instale ubuntu Hardy Heron y la hice andar sin problemas!

Como los drivers de esa placa ya vienen incluidos, lo unico que tenes que hacer es:

abris la consola y pones:

sudo su
aca pone tu contraseña de usuario (aunque veas que no se escibe nada)
ahora pones:
rmmod saa7134_alsa (este te puede da error, pero no creo) le das enter y seguis con
rmmod saa7134 otra vez enter
modprobe saa7134 card=3 tuner=69 (esos valores me andan a mi, tengo la misma placa y puedo usar la tv y la radio)
y ahora dale enter otra vez y abris el tvtime.


Se tendria que escuchar y ver sin problemas. Tal vez en el tvtime tendras que scanear canales y eso.



Si te funciona avisa que lo ponemos para que se inicie siempre junto con hardy




:lolflag:

---

### Post by Hei Ku on 2008-05-01
en vez de poner sudo su al principio, directamente pone sudo antes de los comandos siguientes.
no hace falta usar root para eso, con el sudo alcanza y sobra.

---

### Post by mfzeitune on 2008-05-02
Muchas gracias.
Funciono de 10 gracias Mauro22 y Hei Ku.
Lo que noto es que el volumen es un bajo y cierro el tvtime sigue funcionando el sonido
Hay alguna solucion para alguna de las 2 cosas?
que no sea el bajarle el volumen del todo al tvtime o subir el audio a tope

Y Les vuelvo a agradecer muchachos.


 Saludos   :lolflag:

---

### Post by Hei Ku on 2008-05-02
Fijate el volumen del audio in. Probablemente tenga un canal separado para controlarlo y el nivel por default suele ser bajisimo.

---

### Post by User21 on 2008-05-02
Yo me mudé hace poco, y como ahora no tengo Inet (snif!) , me puse a ver mi placa de TV. La hice funcionar!!! :D 
Lo del sonido, es seguramente el canal de audio que usa la placa de TV. Puede ser LINE IN o como esté configurada en tu caso. Solo tenés que darle doble clic al icono de sonido, buscar cual es el canal que usa (si no aparece, agregarlo tildandole la casilla), y subirle el volumen. :)

---

### Post by Mauro22 on 2008-05-02
Para que se escuche solo cuando ves tvtime, tenes que hacer un script:


#!/bin/sh
amixer set Line unmute
tvtime
amixer set Line mute



Lo guardas en /usr/bin con el nombre que quieras. (yo le puse tv)
Le das permisos de ejecucion (sudo chmod a+x tv (o el nombre que le pusiste))


y listo!:lolflag:

---

### Post by vk-cdg on 2008-05-02
> **mfzeitune said:**
> 
Lo que noto es que el volumen es un bajo y cierro el tvtime sigue funcionando el sonido
Hay alguna solucion para alguna de las 2 cosas?


Los del sonido que sigue funcionando, se soluciona con un script, cuando llego a casa lo posteo.

En cuanto al volumen, a mi me pasa algo parecido, usando el cable de puente, a la entrada auxiliar, no escucho nada, aún teniendo todos los volumenes al mango. Pensé que era un problema del sintonizador o algo pero no, descubrí que enchufando unos parlantes amplificados y subiendo el volumen al mango, anda, pero pierdo la posibilidad de controlar el volumen desde el teclado o desde el mismo tvtime.
Este punto todavía sigue pendiente..... me queda probar:

- Conectar el cable de puente a la entrada del MIC en vez de LINE IN
- Probar con el cable interno, que es similar al de audio del CD, que se conecta a la placa.
- Resignarme a usar unos parlantes enchufados directo a la sintonizadora :(

---

### Post by mfzeitune on 2008-05-02
Disculpen mi ignorancia o idiotes por no estar familiarizado con este SO.

Cuando reinicio la PC nuevamente deja de captarme los canales y tengo que volver a abrir la consola y poner el 
" sudo su
  rmmod saa7134_alsa
  rmmod saa7134
  modprobe saa7134 card=3 tuner=69 "

para que funcione.
Se que debe ser muy facil para que cada vez que inicie la sesion no tenga que hacer esto, pero no se como.

con respecto al script pude poner un archivo llamado **tv.sh**  en la carpeta **usr/bin** el archivo contiene lo siguiente:
[CENTER]''#[B]!/bin/sh
           amixer set Line unmute
           tvtime
           amixer set Line mute[/B]'' [/CENTER]
y aparte mediante propiedades lo deje con permisos de ejecucion unicamente pero igual cuando cierro el tvtime no me pone en mute el sonido

Disculpen y Muchas gracias.

---

### Post by Mauro22 on 2008-05-02
Para que se inicie siempre al cargar ubuntu hace:

abris la consola y pone

sudo gedit /etc/modprobe.d/options

Por ahi te aparezca un archivo de texto ya escrito. Agregale esto a lo ultimo:

options saa7134 card=3 tuner=69


Guardalo, con eso ya esta.


Ahora lo del script. Una vez que moves el script a /usr/bin y le diste permisos de ejecucion para ver la tele usa el comando tv en lugar de tvtime. Ya que el script que te pase ejecuta tvtime, o sea hace esto:

libera el mudo de la linea
ejecuta tvtime
vuelve a liberar el mudo de la linea


En resumen, para ver la television, ahora el comando es tv y no tvtime

---

### Post by mrchelo2002 on 2008-05-04
Hola que tal. Seguí todos los pasos enumerados arriba, y pude hacer andar la placa, pero no consigo tener audio. Toque todas las configuraciones, pero nada. Estoy re ansioso porque es lo único que me falta para hacer andar todas mis winutilidades en ubuntu. Si alguien tiene una idea la agradezco desde ya. Muchas gracias!!
Marcelo

---

### Post by Mauro22 on 2008-05-04
Han reportado que la saa7134 no es que no posee sonido, sino que la salida no es lo suficientemente fuerte para alcanzar un volumen normal.


Prueba:

Conectar parlantes/auriculares directamente a la sintonizadora (si tiene la salida)



De mas esta aclarar, que hayas subido el volumen en tvtime y en el controlador de audio de ubuntu (doble clic en el parlante y subes al maximo "linea de entrada", si tienes el modelo enltv-(fm)

---

### Post by mrchelo2002 on 2008-05-05
El chips es el saa7134. La marca es Kworld no recuerdo el modelo. Aún no probé ni recuerdo si tiene salida de sonido, pero probaré. Los controles de sonido estan todos al máximo, los que se cuales son y otros que no tengo ni idea.
Mil Gracias.

Marcelo

---

### Post by vk-cdg on 2008-05-05
Man, como va todo?
Yo tengo la misma placa que vos y estoy con el mismo problema. Fijate que la placa tiene una salida de audio, que se usa con un puente (cable con dos fichas plug), es de color verde y normalmente se conecta entra la salida de la sintonizadora y la entrada de audio del mother. 

Con Ubuntu, la salida de la sintonizadora no entrega un nivel de volumen como para que algo se escuche. Esto no pasa con otras distros (como Mandriva) o con Windows. 

Probá conectar los parlantes directos, solo como para saber si suena, ya que haciendo esta conexión, perdés todo control de volumen desde el teclado o desde el alsa mixer, solo te queda subir o bajar desde la perillita de los parlantes, pero es solo para probar.

Solución?.... no tengo idea, calculo que habrá que reportarlo a Canonical para ver si lo arreglan o hacer alguna conexión media rara por hardware.

Otra cosa que probé (sin éxito) es conectar la salida de audio que tiene la sintonizadora adentro directamente al mother (usa el cable de audio CD), pero tampoco funciona. :(

---

### Post by anarko on 2008-05-05
Probaron si no tienen en silencio el mixer? o con el volumen muy bajo?
Para mi la mejor opcion es conectar mediante el patch la salida de audio de la placa de tele con la entrada de linea de la placa de sonido.
Tambie fijense en /etc/tvtime/tvtiume.conf en la linea donde dice que device usar para el sonido en el mio dice : 
<option name="MixerDevice" value="/dev/mixer:line"/>
Pongo esto del tvtime porque lei que lo estaban usando, yo tambien lo uso y va de 10 mas desde que hice andar el lirc ( maldita Winfast TV2000FM ) aunque le tengo ganas al mythTV, pero todabia no lo entiendo del todo, me queda mucho por goglear.

---

### Post by mrchelo2002 on 2008-05-06
Hola gente. Mil gracias por los consejos!!!! Efectivamente, conecte los auriculares a la salida de sonido de la placa y se escucha bien. No hice el puente desde la salida de audio de placa a entrada auxiliar de sonido porque no tengo un cable de esas caracteristicas en la mano, probaré cuando pueda.
Solucionado esto me aventuré en lo del mythtv. Ya que el uso principal que le doy a la maquina de mi casa es grabar todas las series de tv que por estar en el trabajo me las pierdo.
Después de avanzar y retroceder un rato, pude calibrar los canales y hacer que se vea, sonido obvio también por la salida de la placatv. El problema ahora es que sale desfazado el audio y el video, sale primero el audio y el video viene con segundos de retardo. El otro inconveniente es que al grabar video, el resultado también es sin sonido, lo que tira por el suelo el logro anterior.
Hay que configurar algún codec o algo para cambiar esto? Infinitas gracias desde ya

---

### Post by anarko on 2008-05-06
Lo del sonido desbe ser por el delay que usa el myth tv para que puedas hacer pausa rewind cuando enchufes la salida de la placa de tele a la plaka de sonido seguro se arregla

---

### Post by guillermoezquer on 2008-09-01
hola gente, segui los consejos q dicen mas arriba y tvtime me sigue diciendo q no señal!!!! es lo unico q me falta hacer funcionar para por fin librarme de win... si me ayudan lo voy a agradecet mucho..

---

