---
title: "[SOLVED] Ayuda comando shutdown"
date: 2008-07-06
forum: Software
---

### Post by Mauro22 on 2008-07-06
Buenas!!


Si quieren hacerla corta, leean lo que esta en negrita :)

Les comento:

Tras meses de andar buscando por internet y probando, he podido grabar video y audio usando mencoder y tvtime.

Por lo que ahora estoy haciendo un script para automatizar el proceso. Es decir cuantos minutos a grabar y eso...


Mi duda viene con el comando shutdown para que se apague la PC al terminar de grabar.

Tengo entendido que tengo que editar el archivo sudoers con el comando visudo [B]para que "shutdown" no me pida mi contraseña (Recuerden que debe ser automatico).

La ayuda de visudo no la entiendo y en google encuentre mas de una forma y estoy confundido.

Entonces, necesito a alguien con experiencia que me ayude a editar ese archivo.[/B]



Gracias desde ya!
:guitar:

---

### Post by Hei Ku on 2008-07-06
porq no usas crontab?
esos comando se ejecutan por defecto como root, y es justamente para ese tipo de cosas.

---

### Post by Mauro22 on 2008-07-06
Eso mas o menos lo sabia.

La cosa es asi:

Yo tengo el script hecho, pero al agendarlo con crontab, lo "ejecuta".

Es decir lo ejecuta pero no en modo consola. Sin modo consola no puedo darle para grabe y si no graba no se apaga.

Trate de abrirlo con xterm, gnome-terminal, sh, etc... pero crontab lo ejecuta sin abrir la consola. Hasta que no lo haga, el script no va a llegar nunca a "shutdown"


:D

Gracias!

---

### Post by Hei Ku on 2008-07-06
por q no posteas el script, a ver si te podemos dar una mano con eso?

---

### Post by Mauro22 on 2008-07-06
Este seria el script:

```

#!/bin/bash


menu_c () {
clear
echo "Configuracion:"
echo ""
echo ""
echo "¿Cuanto tiempo desea grabar? - Exprese en minutos"
read min
echo ""
echo ""
echo "Confirmar:"
echo "¿Grabar" $min "minutos? (S/N)"
read res
if [ $res = "S" ]; then
    clear
    preparar
elif [ $res = "s" ]; then
    clear
    preparar
else
    menu_c
fi
}


grabar () {
clear
amixer set Mic unmute
echo ""
echo ""
echo "Lanzando TvTime"
echo ""
sleep 2
gnome-terminal -e tvtime
mencoder -tv driver=v4l2:width=320:height=240:amode=1:device=/dev/video0 tv:// -o $SALIDA -oac lavc -ovc lavc
cerrar
}


cerrar () {
clear
amixer set Mic mute
sleep 2
echo ""
echo ""
echo Borrando menC
sleep 1
rm menC
echo ""
echo ""
echo matando mencoder
sleep 1
killall mencoder
echo ""
echo ""
echo matando tvtime
sleep 1
killall tvtime
sleep 2
echo ""
echo ""
echo ""
echo ""
echo Gracias por usar este script. Que disfrutes de la grabacion.
sleep 7
exit 0
}


preparar () {
clear
echo killall mencoder > menC 
sleep 1
at now + $min minutes -f menC
grabar
}


ayuda () {
clear
echo "Modo Automatico:"
echo "Usando este modo, la grabacion se realiza en forma automatica. Lo unico que se solicita es la duracion (en minutos) que desea grabar. Al finalizar un archivo de video en formato AVI se crea en HOME."
echo ""
echo "Modo Manual:"
echo "Usando este modo, la grabacion se inicia automaticamente pero la finalizacion se debe realizar a mano aprentando Control + C, cuando lo desee. Al igual que el modo automatico, en su HOME habra un video en formato AVI, con los datos grabados."
echo ""
echo ""
echo "Requerimientos:"
echo "1) Placa Sintonizadora :D"
echo "2) TvTime o similar"
echo "3) Mencoder (apt-get)"
echo ""
echo "Observaciones:"
echo "1) La calidad es AVI en 320x240"
echo "2) Se graba desde /dev/video0"
echo "3) El audio se captura el que ingresa por MIC. Verificar nivel de volumen"
echo "4) Todo esto modificable"
echo ""
echo "Notas:"
echo "Cuando empiece a grabar, estos son los pasos:"
echo "1) Abrir el TvTime o similar"
echo "2) Sintonizar el canal y comprobar volumen"
echo ""
echo ""
echo "Por Favor, vuelva a iniciar el script si desea grabar"
echo ""
echo ""
}





clear

SALIDA=$HOME/$1_`date +'%y-%m-%d_%T'`.avi
killall tvtime

echo "+++++++++++++++++++++++++++++"
echo "Personal Video Recorder (PVR)"
echo "+++++++++++++++++++++++++++++"
echo ""
echo "--------------------"
echo "Modo de grabacion:"
echo ""
echo "1 - Automatico"
echo "2 - Manual"
echo "3 - Ayuda"
echo "4 - Salir"
echo "--------------------"
read metodo
auto=3
case $metodo in
"1")
auto=1
;;
"2")
auto=0
;;
"3")
clear
ayuda
exit 0
;;
"4")
echo ""
echo "Hasta Luego!"
echo ""
exit 0
;;
*)
echo "No es una opcion valida. Hasta Luego!"
exit 0
;;
esac

echo ""
echo ""
if [ $auto = 1 ]; then
    echo "Metodo Automatico Seleccionado..."
    echo ""
    menu_c
else
    echo "Metodo Manual Seleccionado..."
    grabar
    cerrar
fi

```


Se que puede ser mas corto, pero no estoy muy acostumbrado a Bash

---

### Post by Hei Ku on 2008-07-06
Dejame entender un poco mas.

Vos ejecutas esto por consola, y lo que queres es agregarle una opcion para que una vez grabada la cantidad de minutos que vos le decis, se apague la PC, no?

En el momento de correr el script no habria problemas en pedir el sudo, no? 
Podrias poner algo así: 

```

sudo shutdown +90 

```

Eso ejecutaria el shutdown en 90 minutos. 

No estoy seguro exactamente del formato, podes fijarte con man shutdown. Lo importante es que podes ejecutar el shutdown en el mismo momento que corres el script, y se ejecuta en la cantidad de minutos que vos queres. Eso te sirve?

---

### Post by Mauro22 on 2008-07-06
Eso lo probe, pero no funciona ya que 'sudo' es como que vence a los 15 minutos creo.

Entonces  al querer apagarlo mas tarde, me vuelve a pedir la contraseña.

---

### Post by Hei Ku on 2008-07-06
que p***! :D

Probaste agregar al final del script un comando que agregue el shutdown al cron?

Faktor!!! Un poco de ayuda por aca, vos que estas con el tema de scripts.

---

### Post by Mauro22 on 2008-07-06
Eso no lo probe porque todavia no descubri como meter algo en el archivo de crontab.

Al hacer crontab -e y guardarlo, cada vez es un directorio distinto. 


Gracias por la Ayuda Hei Ku

---

### Post by Hei Ku on 2008-07-06
Fijate en:

man cron
man crontab

---

### Post by niko_3100 on 2008-07-07
estas seguro si haces sudo shutdown -h 22:30   eso se ejecuta y al instante te pide la contraseña y se va a apagar a las 22:30, yo lo hago en la notebook para dejar bajandome cosas y le pongo un horario que se que se bajo todo para que se apague automatico, y lo hace.

---

### Post by Mauro22 on 2008-07-07
Que raro :S


Yo lo pongo por ejemplo para que se apague a las 22, y los pongo a las 20. y las 22 me vuelve a pedir la contraseña.

---

### Post by marianom on 2008-07-07
¿Probaste con sudoers/visudo? (ambos accessibles con man)

Esto viene en sudoers:

> NOPASSWD and PASSWD

       By default, sudo requires that a user authenticate him or herself before running a command.  This behavior can be modified via the NOPASSWD tag.  Like a
       Runas_Spec, the NOPASSWD tag sets a default for the commands that follow it in the Cmnd_Spec_List.  Conversely, the PASSWD tag can be used to reverse things.
       For example:

        ray    rushmore = NOPASSWD: /bin/kill, /bin/ls, /usr/bin/lprm

       would allow the user ray to run /bin/kill, /bin/ls, and /usr/bin/lprm as root on the machine rushmore as root without authenticating himself.  If we only want
       ray to be able to run /bin/kill without a password the entry would be:

        ray    rushmore = NOPASSWD: /bin/kill, PASSWD: /bin/ls, /usr/bin/lprm

       Note, however, that the PASSWD tag has no effect on users who are in the group specified by the exempt_group option.

       By default, if the NOPASSWD tag is applied to any of the entries for a user on the current host, he or she will be able to run sudo -l without a password.
       Additionally, a user may only run sudo -v without a password if the NOPASSWD tag is present for all a user&#8217;s entries that pertain to the current host.  This
       behavior may be overridden via the verifypw and listpw options.

Ergo, deberías poder correr el comando shutdown sin pssword en sudo si lo estableces en los permisos de sudoers para tu usuario, a través de visudo

---

### Post by faktorqm on 2008-07-08
Hola, disculpa que no postie nada pero estoy a full con la facu y con los modems adsl usb :S

Para mi, tenes que agarrar y hacer un script nuevo, MAS SIMPLE, y le pasas los parámetros por comando. Esto es, llamas a tu script y le pasas las configuraciones "a mano" sin tantos menues.

ejemplo: $ ./tuscript <cantidad de minutos> <nombre_de_archivo>
ejemplo 2: $ ./tuscript 120 estudiantes7_gimnasia0_15-10-06.avi

y el script que propongo es:

```

#!/bin/bash
# reemplazo $min por $1 ($0 es el nombre del programa)
# reemplazo $salida por $2, si no se especifica nada le pongo uno yo. No estoy de acuerdo con el nombre de la variable, deberia ser output_file_name o algo por el estilo ;)

if [ $1 = "" ] # si no ingreso nada muestra la ayuda y sale
        ayuda
fi           
if [ $2 = "" ] # si solo ingreso el tiempo le pongo el nombre yo
        SALIDA=$HOME/$1_`date +'%y-%m-%d_%T'`.avi
else
        SALIDA = $2 # si no, asigno lo que ingreso a "salida"
fi

echo killall mencoder > menC 
sleep 1
at now + $1 minutes -f menC
amixer set Mic unmute
sleep 2
gnome-terminal -e tvtime
mencoder -tv driver=v4l2:width=320:height=240:amode=1:device=/dev/video0 tv:// -o $SALIDA -oac lavc -ovc lavc
amixer set Mic mute
sleep 2
rm menC
sleep 2
killall mencoder
sleep 2
killall tvtime
exit 0
}

ayuda () {
echo ""
echo "Modo de utilización:"
echo "./grabar_tv <minutos> <nombre_archivo>"
echo ""
exit 0
}


```

Ahi el crontab no te lo va a trabar. Espero que te haya servido. Salu2!!

---

### Post by Mauro22 on 2008-07-08
gracias pero ya lo habia hecho. El posteado es el primero que hice

en realidad hice otro script para programar una grabacion usando crontab


Los menues era la primera opcion, hasta que lei como leer parametros.
[I]Igual los dejo pq me costaron :D



Ya me falta poco para tenerlo de 10!!


Lo que no se es si alguien ya lo probo

:lolflag:
[/I]

---

### Post by rodo26 on 2008-08-11
Hola, así es, tienes que editar el archivo sudoers, yo tenia el mismo problema. Lo primero que hice fue editar sudoers con nano

en la terminal abres el archivo con: sudo nano /etc/sudoers

ya dentro del archivo al final agregas esta linea:

usuario_x ALL=NOPASSWD:/sbin/shutdown

usuario_x: es el nombre del usuario que va a ejecutar el comando.

y guardas el archivo con Ctrl+O(Letra O), te va a preguntar el nombre del archivo, tu solo das enter, Ctrl+X para salir.

Ahora si, cuando quieras apagar la compu solo tienes q escribir en la terminal: sudo shutdown -h now y no te va a pedir la contraseña.

Espero te sirva de algo, saludos.

---

### Post by Mauro22 on 2008-08-11
Primero, GRACIAS! :D

Segundo, corrijo un par de cosas:

> en la terminal abres el archivo con: sudo nano /etc/sudoers

En lugar de eso, seria:

```
sudo visudo -f /etc/sudoers
```

> ya dentro del archivo al final agregas

Apretas insert para poder escribir

> guardas el archivo con Ctrl+O(Letra O), te va a preguntar el nombre del archivo, tu solo das enter, Ctrl+X para salir.

Apretas : y luego w (write) y q (quit)
```
:wq
```


Pero la esencia esta bien!! :lolflag:
Solo que si editas sudoers con nano, fuiste!

---

### Post by faktorqm on 2008-08-12
che, y no es lo mismo abrir una terminal como root y tirarle el shutdown? salu2!

---

### Post by niko_3100 on 2008-08-12
aj... claro es verdad esa, pero con sudo shutdown le das enter y te pide la contraseña la escribis volves a dar enter y despues solo tenes que esperar que se apague, por lo menos me pasa eso a mi.

---

### Post by faktorqm on 2008-08-12
Yo estaba observando esa posibilidad, de todo lo que se posteo al final pense que es mas facil abrir una terminal como root, correr en el cron con 3 comandos, el que empieza la grabacion, el que la corta, y el que te apaga la compu, y todo sin pedirte contraseña. lo evaluo proximamente y les comento como me fue. Salu2!

---

### Post by Mauro22 on 2008-10-12
Lo pongo aca como link para no hacer repost, y marco como SOLVED

[http://ubuntuforums.org/showthread.php?t=943895](http://ubuntuforums.org/showthread.php?t=943895)

---

