---
title: "Auxiliooo!!! - Problema con Apt-get"
date: 2008-09-15
forum: Software
---

### Post by santiagofrias on 2008-09-15
Estimados amigos: como newbie me mandé mi primer error.
Quise instalar un tema nuevo que encontré en "http://losmundosdeyupi.wordpress.com/2008/07/14/instalar-tema-newhuman-intrepid-ibex-en-hardy-heron/" ; seguí los pasos descriptos allí, y cuando reinicié con "Ctrl + Alt + Backspace" todo se inicio pero ni me apareció el tema nuevo y me apareció un ícono de advertencia en la barra superior diciendo que "los repositorios,etc...." dejando de funcionar el gestor de repositorios. No pude volver a editar el archivo de listas y quede sin la posibilidad de recibir actualizaciones.
¿Cómo recupero el estado anterior? (no hice backup del archivo)
Gracias desde ya.

---

### Post by fmsismo on 2008-09-15
Supongo que te anda la consola y sabes usar el 'vi'

hace:

[INDENT]sudo vi /etc/apt/sources.list[/INDENT]

y borra estas dos líneas (estan al final teoricamente)

[INDENT]deb-src [http://ppa.launchpad.net/kwwii/ubuntu](http://ppa.launchpad.net/kwwii/ubuntu) hardy main
deb [http://ppa.launchpad.net/kwwii/ubuntu](http://ppa.launchpad.net/kwwii/ubuntu) hardy main[/INDENT]

después hace

sudo apt-get install -f

Con esto deberías corregir el problema que tenes.

Saludos

---

### Post by sajnox on 2008-09-15
Santiago,

Te edite el titulo del thread, en lo sucesivo te aconsejo que seas mas descriptivo en el titulo del thread, ya que el Auxilio!!! no es muy descriptivo de tu problema real.

Sin tomarlo a rajatabla ya que es un "poco demasiado" te aconsejo que leas lo siguiente:

[http://www.sindominio.net/ayuda/preguntas-inteligentes.html](http://www.sindominio.net/ayuda/preguntas-inteligentes.html)

---

### Post by Hei Ku on 2008-09-15
> **fmsismo said:**
> Supongo que te anda la consola y sabes usar el 'vi'

hace:

[INDENT]sudo vi /etc/apt/sources.list[/INDENT]

y borra estas dos líneas (estan al final teoricamente)

[INDENT]deb-src [http://ppa.launchpad.net/kwwii/ubuntu](http://ppa.launchpad.net/kwwii/ubuntu) hardy main
deb [http://ppa.launchpad.net/kwwii/ubuntu](http://ppa.launchpad.net/kwwii/ubuntu) hardy main[/INDENT]

después hace

sudo apt-get install -f

Con esto deberías corregir el problema que tenes.

Saludos

Es un usuario nuevo y lo mandas a usar el vi?? :lolflag:

tenes tambien el pico, que es mas parecido a un editor comun.

```
sudo pico /etc/apt/sources.list
```

---

### Post by santiagofrias on 2008-09-15
> **fmsismo said:**
> Supongo que te anda la consola y sabes usar el 'vi'

hace:

[INDENT]sudo vi /etc/apt/sources.list[/INDENT]

y borra estas dos líneas (estan al final teoricamente)

[INDENT]deb-src [http://ppa.launchpad.net/kwwii/ubuntu](http://ppa.launchpad.net/kwwii/ubuntu) hardy main
deb [http://ppa.launchpad.net/kwwii/ubuntu](http://ppa.launchpad.net/kwwii/ubuntu) hardy main[/INDENT]

después hace

sudo apt-get install -f

Con esto deberías corregir el problema que tenes.

Saludos
Gracias por el dato, pero no pude cambiar el archivo. En la consola me tira el error que no puede guardar el archivo y me da la opcion para salir sin guardar.
No puedo editar dicho archivo de ninguna forma.

---

### Post by santiagofrias on 2008-09-15
> **sajnox said:**
> Santiago,

Te edite el titulo del thread, en lo sucesivo te aconsejo que seas mas descriptivo en el titulo del thread, ya que el Auxilio!!! no es muy descriptivo de tu problema real.

Sin tomarlo a rajatabla ya que es un "poco demasiado" te aconsejo que leas lo siguiente:

[http://www.sindominio.net/ayuda/preguntas-inteligentes.html](http://www.sindominio.net/ayuda/preguntas-inteligentes.html)
Tenés razon sajnox, me descuidé de ello. La urgencia no me hizo advertir esas cosas.
Un abrazo

---

### Post by leo_rockway on 2008-09-15
> **Hei Ku said:**
> tenes tambien el pico, que es mas parecido a un editor comun.

Me parece copado aclarar (como historia offtopic para los que no lo sepan) que Pico es un editor privativo y que existe un reemplazo GNU que se llama Nano. /usr/bin/pico en Ubuntu es un symlink a nano.

```
$ whereis pico
pico: /usr/bin/pico /usr/share/man/man1/pico.1.gz
$ cd /usr/bin
$ ls -l pico
lrwxrwxrwx 1 root root 22 2008-08-25 21:26 pico -> /etc/alternatives/pico
$ cd /etc/alternatives/
$ ls -l pico
lrwxrwxrwx 1 root root 9 2008-08-30 02:08 pico -> /bin/nano
```

Dice la Wikipedia: "The GNU project has a clone of Pico called nano. Nano was developed because Pico's license is not a free software license, since distribution of a modified version of the code is expressly forbidden."

---

### Post by santiagofrias on 2008-09-15
> **Hei Ku said:**
> Es un usuario nuevo y lo mandas a usar el vi?? :lolflag:

tenes tambien el pico, que es mas parecido a un editor comun.

```
sudo pico /etc/apt/sources.list
```
Solucionado con el pico, no se porque el "vi" no me dejaba guardar los cambios, muchas gracias a todos....Bueno, solo el que no hace nada, nunca comete errores cierto,jeje?
Gracias a todos.

---

### Post by Hei Ku on 2008-09-15
> **leo_rockway said:**
> Me parece copado aclarar (como historia offtopic para los que no lo sepan) que Pico es un editor privativo y que existe un reemplazo GNU que se llama Nano. /usr/bin/pico en Ubuntu es un symlink a nano.

```
$ whereis pico
pico: /usr/bin/pico /usr/share/man/man1/pico.1.gz
$ cd /usr/bin
$ ls -l pico
lrwxrwxrwx 1 root root 22 2008-08-25 21:26 pico -> /etc/alternatives/pico
$ cd /etc/alternatives/
$ ls -l pico
lrwxrwxrwx 1 root root 9 2008-08-30 02:08 pico -> /bin/nano
```

Dice la Wikipedia: "The GNU project has a clone of Pico called nano. Nano was developed because Pico's license is not a free software license, since distribution of a modified version of the code is expressly forbidden."

Buena la aclaracion. Yo uso el nano, pero en algun lugar habia leido que en gnome estaba el pico, asi que le recomende ese. Siempre se aprende algo.

---

### Post by faktorqm on 2008-09-16
Yo al pico lo usaba en Red Hat 6!!! no sabia que estaba aca! igual ya no lo uso mas hace mucho tiempo... pero por que no pense que no estaba! jajaj

---

### Post by sergiom99 on 2008-09-16
para empezar, el mas sencillo me resulto mcedit. (el mc es lo mas cuando no tenes ganas de escribir y no tenes entorno grafico)

---

### Post by Dark_s on 2009-02-22
> **faktorqm said:**
> Yo al pico lo usaba en Red Hat 6!!! no sabia que estaba aca! igual ya no lo uso mas hace mucho tiempo... pero por que no pense que no estaba! jajaj

Hola a todos... en realidad soy nuevo en Ubuntu y en lo personal no hay nada mejor ke Linux...:)

Solo como comentario, tambien he batallado mucho con estos errores:(

deb-src [http://ppa.launchpad.net/kwwii/ubuntu](http://ppa.launchpad.net/kwwii/ubuntu) hardy main
deb [http://ppa.launchpad.net/kwwii/ubuntu](http://ppa.launchpad.net/kwwii/ubuntu) hardy main

Pero ya encontre la solucion:p:KS

En vez de utilizar los comandos:

sudo vi /etc/apt/sources.list
sudo pico /etc/apt/sources.list

Los cuales unicamente permiten borrar esas dos molestas lineas al final de la pantalla de nuestra terminal, pero no nos dejan guardar los cambios hechos:p, mejor usen este comando:

sudo gedit /etc/apt/sources.list

Al activarlo nos aparecera una pantalla muy similar a las otras dos ke antes nos salian, de igual forma, nos vamos al final y ahi tendremos a nuestras dos molestas amigas:

deb-src [http://ppa.launchpad.net/kwwii/ubuntu](http://ppa.launchpad.net/kwwii/ubuntu) hardy main
deb [http://ppa.launchpad.net/kwwii/ubuntu](http://ppa.launchpad.net/kwwii/ubuntu) hardy main

Ok... Las borramos, arriba veremos la opcion de GUARDAR, damos click, cerramos la ventana y en esta ocacion si corremos el comando:

sudo vi /etc/apt/sources.list

Para verificar ke las dos linaes han desaparecido. Si te molesta la alerta roja ke dice ke no puedes actualizar, simplemente reinicia el sistema y cuando entres nuevamente, habra desaparecido.;)

Y listo... a bajar mas actualizaciones.

Espero ayudar un poko con este grandioso sistema y a la vez agradezco todos los tips ke ustedes tambien nos comparten.

Hasta pronto!!!:popcorn:

---

