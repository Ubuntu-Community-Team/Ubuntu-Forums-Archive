---
title: "comando shutdown"
date: 2008-08-10
forum: Software
---

### Post by sonhadorpr on 2008-08-10
Saludos amigos Ubunteros!
Dios me los bendiga!

A veces, jugando/trabajando con Ubuntu/Linux, se puede convertir en un dolor de cabeza.
Ya entiendo por qué la gente le da miedo jugar con Linux, vineindo de Windows.
Yo sé que hay MUUUUCHAS cosas que no se pueden hacer con Windows, y sí en Linux, y de que Linux es gratuito, y muy poderoso, y etc...
pero es que, hay cosas que "se caen de la mata", y linux, en vez de ser fácil, es una maldición de complicado.

Les relato mi problema.

Estoy tratando de escuchar una musiquita suave, para ir a dormir.
Pongo mi música suave, y le trato de decir al sistema, apágate en 30 minutos.
Leo el manual para el comando shutdown, donde el único que me funciona a la perfeción es: shutdown now.
No quiero hacer eso, quiero decirle que se apague luego.
Pues voy a man -k shutdown....me dice que no.
Escribo help shutdown, me dice que no.
escribo shutdown solito, porque sé que si no le digo now, no se apaga, y me dirá cómo programarlo.

Pues escribo shutdown --help
y el manual, muy bonito dice lo siguiente:

sonhadorpr@Ubuntu-Science:/home/romici# shutdown --help
Usage: shutdown [OPTION]... TIME [MESSAGE]
Bring the system down.

Options:
-r reboot after shutdown
-h halt or power off after shutdown
-H halt after shutdown (implies -h)
-P power off after shutdown (implies -h)
-c cancel a running shutdown
-k only send warnings, don't shutdown
-q, --quiet reduce output to errors only
-v, --verbose increase output to include informational messages
--help display this help and exit
--version output version information and exit

TIME may have different formats, the most common is simply the word 'now' which will bring the system down
immediately. Other valid formats are +m, where m is the number of minutes to wait until shutting down and hh:mm
which specifies the time on the 24hr clock.

Logged in users are warned by a message sent to their terminal, you may include an optional MESSAGE included with
this. Messages can be sent without actually bringing the system down by using the -k option.

If TIME is given, the command will remain in the foreground until the shutdown occurs. It can be cancelled by
Control-C, or by another user using the -c option.

The system is brought down into maintenance (single-user) mode by default, you can change this with either the -r or
-h option which specify a reboot or system halt respectively. The -h option can be further modified with -H or -P
to specify whether to halt the system, or to power it off afterwards. The default is left up to the shutdown
scripts.

Report bugs to <upstart-devel@lists.ubuntu.com>

Pues al leer estas instrucciones muy bonitas, presumo yo que el comando para apagar la máquina más tarde es:
shutdown +m 30
Según las instrucciones, porque ..es que NO dice exactamente cómo escribirlo, simplemente tienes que deducirlo.
Pues escribo el maldito comando, y me dice:

sonhadorpr@Ubuntu-Science:/home/romici# sudo shutdown +m 30
shutdown: illegal time value
Try `shutdown --help' for more information.

OK...es que lo acabo de leer 4 veces. No entiendo!!!!!!!!!!!!

Entonces trato una serie de formas, y juego con lo de TIME, time (por si acaso, se me olvida que Linux es Case Sensitive, el muy maldito)y etc..
y le pongo que se apague a las 0400, que se apague a las 0200, no sé...no pasa nada!

sonhadorpr@Ubuntu-Science:/home/romici# shutdown -m 30
shutdown: invalid option: -m
Try `shutdown --help' for more information.
sonhadorprt@Ubuntu-Science:/home/romici# shutdown +m 30
shutdown: illegal time value
Try `shutdown --help' for more information.
sonhadorpr@Ubuntu-Science:/home/romici# shutdown +m TIME 30
shutdown: illegal time value
Try `shutdown --help' for more information.
sonhadorpr@Ubuntu-Science:/home/romici# shutdown +m TIME 0400
shutdown: illegal time value
Try `shutdown --help' for more information.
sonhadorpr@Ubuntu-Science:/home/romici# shutdown +m TIME 04:00
shutdown: illegal time value
Try `shutdown --help' for more information.
sonhadorpr@Ubuntu-Science:/home/romici#

¡Maldito sea el linux que tiene que ser tan complicado!

Alguien que me ayude

Gracias!!!!!!!!!!

-- 
Roberto Omar Millán
Registered Ubuntu User # 23478
Registered Linux User #457355

---

### Post by faktorqm on 2008-08-10
```
Other valid formats are +m, where m is the number of minutes to wait until shutting down and hh:mm which specifies the time on the 24hr clock.

```

La traduccion es: Otros formatos validos son "+m", donde "m" es el numero de minutos a esperar para apagar y hh:mm (hora-minutos) especifica el tiempo como si fuera un reloj de 24 horas.

el comando es entonces ```
shutdown +30
``` para apagar en media hora, por ejemplo.

Para la proxima, menos insulto y mas google, por que dependiendo de la configuracion que tengas en tu pc, te va a pedir la contraseña para apagar el sistema....

---

### Post by Hei Ku on 2008-08-10
también tenés el kshutdown y el gshutdown en los repositorios, si te resulta más fácil hacerlo desde la interfaz grafica.
Sin llegar a algo loco como Google, entrar a Synaptic tampoco molesta.

---

### Post by Mauro22 on 2008-08-10
Para apagar, es:

shutdown -h

la h es por apagar por halt

y la ayuda es man shutdown sin el -k

---

### Post by sonhadorpr on 2008-08-10
Gracias amigos.
Ahora sé.

Gracias al que dijo de lo del gshutdown, o kshutdown, ni sabía que existía ese modo.
Gracias de nuevo.

---

### Post by victor_nesta on 2008-08-10
Para los que les entro la duda por que son lentejas como yo
O solo para repasar mientras escriben (como yo) :)
Resumo.

shutdown 
-h (para apagar)
-r (para reiniciar)

shutdown -h 03:25
shutdown -h +15

Saludos!

---

### Post by FlyerDie on 2008-08-11
y si lo corre como un cron??:rolleyes:
total seguramente quiera hacerlo todos los dias, o que schedulee el cron cuando quiera hacer el shutdown...creo que es mas facil.

---

### Post by niko_3100 on 2008-08-11
schedulee?? y esa palabra? aca hablamos español o en su defecto ingles, no spanenglish... por favor no hagan esoooo que me pone muy maalll!!!!!

---

### Post by FlyerDie on 2008-08-12
> **niko_3100 said:**
> schedulee?? y esa palabra? aca hablamos español o en su defecto ingles, no spanenglish... por favor no hagan esoooo que me pone muy maalll!!!!!

Tu comentario es para aportar o para hacer una critica al dope?

---

### Post by niko_3100 on 2008-08-12
Por otro lado proba haciendo sudo shutdown -h 23:45 (hora que queres que se apague), escribi sudo porque por defecto viene para que sea tarea de superusuario, luego te va a pedir la password del superusuario y despues listo tenes que esperar que solo se apague, a mi me funciona asi y la dejo con un margen de 30 minutos y cuando vuelvo se apaga, me sirve para dejar bajando cosas y se que no la voy a usar mas adelante en el dia, entonces calculo cuanto puede tardar la descarga para que despues se apague y me va de diez.

---

