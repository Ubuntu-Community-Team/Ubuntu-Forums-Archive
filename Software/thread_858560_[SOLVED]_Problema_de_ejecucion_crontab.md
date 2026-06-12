---
title: "[SOLVED] Problema de ejecucion crontab"
date: 2008-07-13
forum: Software
---

### Post by FlyerDie on 2008-07-13
Estimados, luego de luchar contra los molinos de viento me veo en el atrevimiento de molestar por estos lugares.

Resulta que al schedulear un script, este no se ejecuta:confused:
Si este script lo corro en forma manual se ejecuta a las 1000 maravillas, pero no al ponerlo scheduleado dentro de crontab.

el script que se ejecuta es el siguiente :

```
#!/bin/sh

mplayer -playlist /home/flyerdie/Desktop/radio10/playlist.lst -ao pcm:file=/tmp/temporadio.wav -vc dummy -vo null ;
lame -m s /tmp/temporadio.wav -o /home/flyerdie/Desktop/radio10/radio10_`date +"%Y%m%d"`.mp3
rm /tmp/temporadio.wav ;
```

que lo tengo guardado dentro de /home/flyerdie/.grabaradio10
A su vez, tengo dentro de .bashrc el alias:

```
alias grabaradio10='sh /home/flyerdie/.grabaradio10'
```
asi lo puedo ejecutar desde cualquier lado como 'grabaradio10'

Ahora bien, el problema es el siguiente, cuando le agrego la tarea a crontab (la cual la agrega sin mayores inconvenientes) no se ejecuta!

aca el cron:

```
19 18 * * * grabaradio10 
21 18 * * * killall -9 mplayer
```

y aca el resultado en /var/log/cron.log

```
Jul 13 18:19:01 moscu2 /usr/sbin/cron[5375]: (flyerdie) RELOAD (crontabs/flyerdie)
Jul 13 18:19:01 moscu2 /USR/SBIN/CRON[7382]: (flyerdie) CMD (grabaradio10)
Jul 13 18:19:07 moscu2 /usr/bin/crontab[7385]: (flyerdie) LIST (flyerdie)
Jul 13 18:19:16 moscu2 /usr/bin/crontab[7389]: (flyerdie) LIST (flyerdie)
Jul 13 18:19:25 moscu2 /usr/bin/crontab[7402]: (flyerdie) LIST (flyerdie)
Jul 13 18:19:34 moscu2 /usr/bin/crontab[7406]: (flyerdie) LIST (flyerdie)
Jul 13 18:19:43 moscu2 /usr/bin/crontab[7410]: (flyerdie) LIST (flyerdie)
Jul 13 18:19:52 moscu2 /usr/bin/crontab[7414]: (flyerdie) LIST (flyerdie)
Jul 13 18:20:01 moscu2 /usr/bin/crontab[7418]: (flyerdie) LIST (flyerdie)
Jul 13 18:20:10 moscu2 /usr/bin/crontab[7422]: (flyerdie) LIST (flyerdie)
Jul 13 18:20:19 moscu2 /usr/bin/crontab[7426]: (flyerdie) LIST (flyerdie)
Jul 13 18:20:28 moscu2 /usr/bin/crontab[7431]: (flyerdie) LIST (flyerdie)
Jul 13 18:20:37 moscu2 /usr/bin/crontab[7435]: (flyerdie) LIST (flyerdie)
Jul 13 18:20:46 moscu2 /usr/bin/crontab[7459]: (flyerdie) LIST (flyerdie)
Jul 13 18:20:55 moscu2 /usr/bin/crontab[7463]: (flyerdie) LIST (flyerdie)
Jul 13 18:21:01 moscu2 /USR/SBIN/CRON[7467]: (flyerdie) CMD (killall -9 mplayer)

```

si corro en forma manual 'grabaradio10' y dejo que la segunda linea del cron se ejecute (la del kill), esta realiza el kill sin problemas... pero la primer linea nunca se ejecuta :mad:

Idea de que podra ser? desde ya muy agradecido, ya que tengo ganas de grabarme el programa de Dolina (entre otros), y esto me vendria mas que bien :)

Saludos!

---

### Post by Mauro22 on 2008-07-13
Yo me apunto :D


Estoy esperando lo mismo para poder dejar grabando la TV...



:)

---

### Post by faktorqm on 2008-07-13
Mira, para mi tas metiendo mal el comando. El correcto sería: 

```
sh /home/flyerdie/grabaradio10
```

y si en realidad el comando esta bien escrito con esto deberia funcionarte:

```
45 23 * * 1-5 sh /home/flyerdie/.grabaradio10
```

esto hace _el comando_ a las 23:45 los dias de lunes a viernes todos los meses. Espero te haya servido. Salu2!!

---

### Post by FlyerDie on 2008-07-13
> **faktorqm said:**
> Mira, para mi tas metiendo mal el comando. El correcto sería: 

```
sh /home/flyerdie/grabaradio10
```

y si en realidad el comando esta bien escrito con esto deberia funcionarte:

```
45 23 * * 1-5 sh /home/flyerdie/.grabaradio10
```

esto hace _el comando_ a las 23:45 los dias de lunes a viernes todos los meses. Espero te haya servido. Salu2!!

Antes que nada gracias por responderme ;)
Mira...hice exactamente como pusiste y sucede lo mismo :( nada..

---

### Post by FlyerDie on 2008-07-15
tendre que tirar cada linea del script como crones :( ? no quiero llegar a esa negrada teniendo la posibilidad de tener prolija la ejecucion de tareas scheduleadas....

---

### Post by FlyerDie on 2008-07-15
> **Mauro22 said:**
> Yo me apunto :D


Estoy esperando lo mismo para poder dejar grabando la TV...



:)

Mauro, probaste lo que tiro faktorqm? te funciono a vos?

---

### Post by Mauro22 on 2008-07-15
Lo que me funciono (en parte) es:

Agrega a tu script esta linea:

PATH=$PATH:/bin:/sbin:/usr/bin:/usr/sbin


Y con eso el crontab lo ejecuta pero sin mostrar nada....


Asi que ahora ANDA pero no como deberia.

---

### Post by faktorqm on 2008-07-15
probaron de ejecutar

```
sudo crontab -e -u <usuario>
```?

ejemplo: sudo crontab -e -u faktorqm en mi caso.

Lo de los path no importa, en realidad ahi lo que estas haciendo es decirle de donde ejecutar las cosas, pero es igual a poner

```
45 23 * * 1-5 /usr/bin/sh /home/flyerdie/grabaradio10
```

y en tu script a cambiar todos los path's por la ruta completa.
Espero que develemos el misterio por que yo en algun momento lo voy a tener que usar en un server nuevo también... Salu2!!!

---

### Post by FlyerDie on 2008-07-15
Genchi,

Hice lo de los path y nada...sigue igual.
Hice tambien de tirar sudo crontab -e -u USUARIO y me da lo mismo que tirando crontab -e... osea, corro siempre con mi usuario las cosas...sera por eso? o tengo que si o si correr los crones como root?:confused:

EDIT:

probe recien:

```
sudo crontab -e -u root
```
y le cargue la linea del cron, pero sucede lo mismo, por lo visto no es un problema de derechos de usuario ni nada de eso... :(

---

### Post by faktorqm on 2008-07-16
Bueno, les voy poniendo lo que voy encontrando, que por cierto son cosas bastante distintas. 

1) El script NO tiene que tener extensión, ni simbolos raros. Sólo admite numeros, letras y guiones del medio y bajo.

2) A uno le funcionó poner su nombre de usuario adelante del comando, ya que cuando cron se ejecuta se hace como root, por lo tanto el /home del root no es nuestro /home.

```
45 23 * * 1-5 faktorqm /usr/bin/sh /home/flyerdie/grabaradio10
```

3) Cuando el cron se ejecuta, no se ve nada en pantalla, seria interesante que chequeen con "ps ax" por ejemplo a ver a donde se esta ejecutando, o si directamente no lo esta haciendo.

4) Para posiblemente ver lo que ocurre bajo crontab, podemos agregar DISPLAY=:0 adelante del comando como si fuera una variable, para por ejemplo poder ejecutar esto y que lo veamos y no que se ejecute en segundo plano.

```
34 23 * * * DISPLAY=:0 /usr/bin/vlc /media/hdc4/video.avi
```

5) Tipica pelea entre debian y ubuntu: sh y bash. Tambien podes probar con poner ```
45 23 * * 1-5 faktorqm export SHELL=/bin/sh/; /usr/bin/sh home/flyerdie/grabaradio10
```

Bueno loco hacelo andar eh! :P Salu2!!

---

### Post by FlyerDie on 2008-07-16
> **faktorqm said:**
> 
2) A uno le funcionó poner su nombre de usuario adelante del comando, ya que cuando cron se ejecuta se hace como root, por lo tanto el /home del root no es nuestro /home.

```
45 23 * * 1-5 faktorqm /usr/bin/sh /home/flyerdie/grabaradio10
```


Te comento un poco la experiencia que tuve.. si corro "crontab -e" desde consola (sin el parametro -u ) me edita los crones de MI usuario, pero si corro con el parametro "-u root", me aparece otro listado de crones que pertenece a los del user root.
Quiero entender que no seria necesario aclarar el user dentro del listado de crones si ejecuto la sentencia desde ese mismo usuario, ya que inclusive se supone que ni debo poner los PATH y me deberian funcionar los ALIAS sin drama, pero con probar no se pierde nada!!

Ojo, de todas las deducciones me hago cargo yo, osea..con mi conocimiento amateur..para nada profesional de linux! Sabeme disculpar si en algo de esto estoy diciendo alguna barrabazada (que no seria nada raro! :lolflag: )

---

### Post by faktorqm on 2008-07-16
La verdad ni idea, estoy igual o mas desorientado que vos con la falla. Hasta te digo mas, como son dos instrucciones, yo ya hubiera probado de mandarle el comando derecho viejo en lugar del script :P

```
45 23 * * 1-5 flyerdie /usr/bin/mplayer -playlist /home/flyerdie/Desktop/radio10/playlist.lst -ao pcm:file=/tmp/temporadio.wav -vc dummy -vo null; lame -m s /tmp/temporadio.wav -o /home/flyerdie/Desktop/radio10/radio10_`date +"%Y%m%d"`.mp3; rm /tmp/temporadio.wav
```

Salu2!!

---

### Post by FlyerDie on 2008-07-16
Probe como me dijiste, de mandarle el comando derecho viejo..pero lo mismo (igualmente no le puedo mandar asi separado por ; porque no me lo reconoce..
me esta agarrando la enfermedad...
como no me estaba funcionando, creyendo que era un tema del script, le puse simplemente que abriera un mc (Midnight Commander), simplemente eso que a X hora abriera uno...

NUNCA SE LEVANTO UN PROCESO QUE LLAME A MC!! :confused::confused::confused: 

Me supera esto! como puedo comprobar que esto este levantado? 

Si chequeo el syslog me dice lo siguiente:
```
Jul 16 15:03:01 moscu /usr/sbin/cron[5490]: (flyerdie) RELOAD (crontabs/flyerdie)
Jul 16 15:03:01 moscu /USR/SBIN/CRON[6878]: (flyerdie) CMD (mc) 
```
pero en el System Monitor nunca aparece el proceso "mc" levantado....:mad:

EDIT: Me llama poderosamente la atencion la segunda linea del cron.log que el path este en MAYUSCULAS ?????? eso esta bien? ya que linux es case sensitive

---

### Post by Mister X on 2008-07-16
Yo lo que te diría es que trates de aislar los procesos para poder detectar de donde viene el error.

Primero hacé un script simple, que te muestre un resultado (como para saber que se ejecutó) y agregalo al crontab. Una vez que sabes que el cron lo está ejecutando como esperás, podes ir agregando complejidad al script hasta llegar a que realice la tarea que necesitas.


Por ejemplo:
```

#!/bin/bash
# esto crea un archivo en tu home

touch /home/flyerdie/se-ejecuto-ok


```

---

### Post by FlyerDie on 2008-07-16
Si, es verdad..al comienzo como que largue con un script medio complejo quizas, pero ya a lo ultimo estoy probando con cosas sencillas, como que levante un Midnight Commander, pero no lo hizo.
Lo que si me acaba de funcionar es levantar un firefox:}

```
01 16 * * 1-5 export DISPLAY=:0 && firefox
```

Y funciono a la perfeccion!!, pero si corro 

```
05 16 * * 1-5 mc
```

No pasa nada
Al menos lo que entendi al leer el man de cron, es que la semantica que se utiliza es la misma que para linea de comando del mismo usuario de ejecucion del cron...lo que quiero decir con esto que si quiero correr el Midnight Commander, con solo poner en la parte semantica del cron **mc** bastaria para su ejecucion, pero no aparece...

---

### Post by FlyerDie on 2008-07-16
PROBLEMA SOLUCIONADO!! :guitar:

La forma que se debe ejecutar es la siguiente:


```
17 17 * * 1-5 export DISPLAY=:0 &&  gnome-terminal --command="sh /home/flyerdie/.grabaradio10"
``` 
*(.grabaradio10 es un ALIAS al script original)*

De esta manera me abre una sesion de terminal y se ejecuta dentro de ella\\:D/

Bueno, creo que fue mas que productivo al menos en mi caso, ya que me termine empapando mas de lo que creia en lo que son los crones.

Gracias a todos por la colaboracion y espero que les sirva a los que nos gusta guardar programas de radio y/o television (ahora mi objetivo pendiente es el thread que arme por la placa capturadora jajaja) :lolflag:

---

### Post by Mauro22 on 2008-07-16
Te doy las gracias como corresponde!

:popcorn:

---

### Post by faktorqm on 2008-07-16
che y si no es ahi en el gnome-terminal, existe un programa que se llama "terminal" o "console"? por que tengo un server sin interfaz grafica... alguno que haya manejado servidores que me tire un cablecito? Salu2!!

---

### Post by leo_rockway on 2008-07-17
```
konsole -e
```

en lugar de ```
gnome-terminal --command=
``` para KDE

---

### Post by Hei Ku on 2008-07-17
> **faktorqm said:**
> che y si no es ahi en el gnome-terminal, existe un programa que se llama "terminal" o "console"? por que tengo un server sin interfaz grafica... alguno que haya manejado servidores que me tire un cablecito? Salu2!!

quizas llamando directamente a bash, en vez de a gnome-terminal. con probar no perdes nada

---

### Post by Mauro22 on 2008-07-18
Gracias Hei Ku, con bash hace lo mismo y es mas corto :D


No sabia que exista ese comando... jeje

---

### Post by Hei Ku on 2008-07-19
> **Mauro22 said:**
> Gracias Hei Ku, con bash hace lo mismo y es mas corto :D


No sabia que exista ese comando... jeje

Yo lo encontre porque muchas veces me logueaba por ssh a los servidores y el tab no andaba ni ahi. Resulta que tenian otro shell por defecto. Hasta q vi q alguien ponia bash y entonces andaba todo como tenia que andar.
Segun recuerdo, tambien esta el ksh (korn shell), que esta justamente mas orientado a scripting. [http://kornshell.com/](http://kornshell.com/) y [http://en.wikipedia.org/wiki/Korn_shell](http://en.wikipedia.org/wiki/Korn_shell)

---

### Post by FlyerDie on 2008-07-21
interesante lo de bash ;) buen punto!

---

### Post by faktorqm on 2008-07-25
Bueno revivo el hilo... ahora no me anda a mi :(

Quise grabar radio del plata (am 1030) por que está un tal dany martinez de 0 a 4 de la mañana, pero me encontré con varios problemas.
El primero, es, que yo al crontab solo puedo especificarle cuando quiero que empiece a grabar digamos, pero como lo paro? 
Se me habia ocurrido hacer otro crontab a las 4 de la mañana tipo "kill mplayer" (se que no es asi, luego lo implemento, solo es la idea), pero es esto "valido" digamos? quiero decir, no es de bruto animalito hacer eso? o es normal?
Segundo, el crontab si ejecuta mi script, pero exactamente cuando el archivo tiene 384kb se corta, pero se corta digamos y no sigue el script (es muy muy parecido al de flyerdie) asi que no se... 384 es un numero demasiado conocido como para pensar que es casualidad...
Tercero y ultimo, como hicieron para que la pc se apague sola? Yo mismo contesté varios posts pero la verdad no me acuerdo y como acá hay gente que graba la radio, mauro la tele, capaz ya tenian ese problema cocinado y lo resolvia en un 1-2-3...
Como siempre, gracias a todos por su ayuda y salu2!!!! :D

---

### Post by Mauro22 on 2008-07-25
Para dejar de grabar podes hacer esto:

echo killall mplayer > temp 
at now + 240 minutes -f temp


Esto lo que hace es:

1) crea un archivo temp con el texto "killall mplayer"
2) y lo ejecutara (at) desde ahora (now) + 240 minutes (60 * 4hs) el archivo (-f) temp


Esto me sirve para mis grabaciones de TV, pero dale un poco mas de tiempo, porque a veces corta solo antes :S (estoy probandolo)


Para apagar solo, podes, crear una entrada en crontab con el comando shutdown -h now siendo root, o sea:

sudo crontab -e

No se si anda, no lo probe.

Podes, tambien, agregar al script esto:

sudo shutdown -h +04:00

Eso apagaria la pc a las 4 am pero te pediria el pass, (aclaro que a mi se me vence a los 10 minutos, o sea, si pongo apagar ahora +20m me pide el pass y a los 20 lo vuelve a pedir o se cancela). Para evitar eso deberias editar el sudoers y sacarle el password a shutdown.
[B]
Por ahora apago la pc a la antigua jeje, [/B]

---

### Post by FlyerDie on 2008-07-25
y si faktor... lo hago asi a lo guarango:

```
10 18 * * * killall -9 mplayer
```

es lo mas practico porque asi continua luego con la conversion a mp3 ;)

Mauro, vos grabas tele? viste que puse un thread que me encuentro con un problema? :( tenes idea?

---

