---
title: "Problema con Emerald/Compiz/Ubuntu 10.10"
date: 2010-10-15
forum: Software
---

### Post by Gpafundi on 2010-10-15
Bueno, hoy decidí instalar el Ubuntu 10.10 (que la verdad, es un espectáculo). Mi tema fue el siguiente. Como soy un usuario novato, decidí buscar en internet que cosas debo hacer después de instalarlo y llegué a esta pagina: [http://www.taringa.net/posts/linux/7393082/despues-de-instalar-ubuntu-10_10.html](http://www.taringa.net/posts/linux/7393082/despues-de-instalar-ubuntu-10_10.html) . Empecé instalando todo y funciono todo de diez hasta que instalé el emerald de la siguiente forma:

sudo apt-get install simple-ccsm compizconfig-settings-manager emerald

/usr/bin/emerald --replace 

Y fue esa última línea de código la que me arruino todo. Hizo que se me desaparezcan la barra de arriba que tiene los íconos de cerrar, maximizar. 

Luego buscando por internet encontré esta linea de código que vuelve la barra esa.

nohup metacity --replace & 

Mi tema es que ahora no puedo activar el modo cubo en el compiz. Tampoco puedo activar ningún efecto del compiz.

¿Alguien me ayuda por favor?

---

### Post by Cajuma on 2010-10-15
Ejecuta en consola compiz --replace, pues con el comando
metacity --replace estas activando precisamente metacity
y para usar emerald tenes que tener compiz activado.
Saludos.

---

### Post by Gpafundi on 2010-10-15
Pongo en la consola compiz --replace. Me pone esto:

Backend     : ini
Integration : true
Profile     : default
Adding plugins
Initializing core options...done

y se me van las barras de arriba. Es más, pruebo editar las configuraciones del compiz en Sistema>Preferencias>Administrador de opciones CompizConfig y no aplica los cambios que hago. De la única manera que se me vuelve a ver la barra es con el metacity --replace pero no me deja aplicarle efectos visuales.

Es como que al poner el Emerald y después ese código (/usr/bin/emerald --replace), arruine el Compiz ...

---

### Post by matias_tati on 2010-10-16
Instalaste compiz fusion? Puede ser muy util, esta en el centro de software. Mira antes de instalar cuaquier cosa buscala en centro de software salvo que busques algun programa especifico o una version en particular, compiz & emerald los podrias haber instalado tranquilamente desde ahi, como hice yo sin necesidad de meter mano en la terminal, menos de fuentes poco confiables. Saludos!!!!!!

---

### Post by Gpafundi on 2010-10-16
Si, también lo instalé pero no me fue de ayuda en esta situación. Me parece que voy a formatear Ubuntu y esta vez no le instalo el Emerald.

Me da bronca porque de como 10 veces que instale ubuntu en mi vida, 7 fueron veces que la formatie porque no podía resolver problemas. Es todo un problema ser ignorante en linux. De todos modos me gusta mucho Ubuntu y vale la pena intentarlo.

---

### Post by matias_tati on 2010-10-16
Naaaa porque no esperas un poco mas quizas alguien aca te resuelva el problema si formateas no vas a saber que fue lo que fallo. En la mayoria de los casos es una pavada. Y en cuanto a ser ignorante eso no es un problema solo no te guies por toda la informacion que anda dando vueltas por ahi yo hace un año o menos que estoy con esto y la verdad ya no tengo problemas. Saludos!

---

### Post by Gpafundi on 2010-10-19
No quiero parecer rompe pero formatee la maquina, volví a reinstalar Ubuntu esta vez sin el Emerald. Estuvo andando de 10 hasta el día de hoy que se instaló una actualización y me volvió a pasar lo mismo. La verdad es que esto me tiene a mal traer. Porque no tengo la barra de arriba, no me carga el Compiz, ni el Compiz Fusion, ni nada. Ahora pongo metacity --replace y me pone las barras, pero cuando cierro la terminal vuelve todo a su estado original y en cima me anula el teclado.

Para colmo, no puedo ni usar el Windows porque ahora no se por que, cuando pongo que arranque el Windows 7 en el GRUB, me tira error... Ya no se que hacer. La verdad es que siempre le di una oportunidad a Ubuntu a pesar de todos los problemas, pero esta vez, realmente me está superando. Me está dejando sin maquina y no quiero reinstalar tooodo otra vez.

POR FAVOR, ALGUIEN QUE ME AYUDE

---

### Post by guillermolisi on 2010-10-19
Por favor, no habras otros threads por el mismo problema. El que dejaste en la seccion general fue marcado como borrado para mantener las respuestas en un solo hilo. Gracias

---

### Post by Gpafundi on 2010-10-19
Gracias Guillermo, quise borrarlo pero no supe como hacerlo.

---

### Post by josecuervo86 on 2010-10-19
para que no se "desaparezcan las barras" tenes que poner ejecutarlo con **Alt + F2**. O sea, apretas ALT + F2 y pones:

```
metacity --replace
```

---

### Post by Gpafundi on 2010-10-19
Si hago eso, aparecen las barras. Pero desaparecen cuando cierro la terminal. Obviamente, todo queda sin efectos del compiz. El tema es que una vez que cierro esa terminal, no solo se van las partes de arriba de las ventanas sino que también me bloquea el teclado.

---

### Post by Gpafundi on 2010-10-19
Acá alguien identificó mi problema y puso una solución.

[http://www.youtube.com/watch?v=i7sh1BLW53c](http://www.youtube.com/watch?v=i7sh1BLW53c)

Pero el tema es que al principio dice que hay que poner el compiz fusion icon, que yo ya lo tengo instalado. Pero al ejecutarlo no me aparece el iconito. Y al ejecutarlo desde terminal como:

sudo fusion-icon

Me aparece esto:

gaston@gaston-desktop:~$ sudo fusion-icon
[sudo] password for gaston: 
 * Detected Session: unknown
 * Searching for installed applications...
Backend     : ini
Integration : true
Profile     : default
Traceback (most recent call last):
  File "/usr/bin/fusion-icon", line 57, in <module>
    from FusionIcon.interface import choose_interface
  File "/usr/lib/python2.6/dist-packages/FusionIcon/interface.py", line 21, in <module>
    from util import env
  File "/usr/lib/python2.6/dist-packages/FusionIcon/util.py", line 419, in <module>
    decorators = CompizDecorators(_installed)
  File "/usr/lib/python2.6/dist-packages/FusionIcon/util.py", line 226, in __init__
    self.command = context.Plugins['decoration'].Display['command']
KeyError: 'decoration'

Ya no se que hacer con este problema. O sea, Ubuntu me anda perfecto en todo lo demás, excepto esto que ya me puso demasiado nervioso.

---

### Post by josecuervo86 on 2010-10-19
lo que yo te explique no es para ponerlo en terminal, si no solo para ejecutarlo mediante **alt + F2**

---

### Post by Gpafundi on 2010-10-20
No se por que pero tengo bloqueado los atajos de teclado. Ni alt + f2 ni ctrl + tab me andan. Pero si en la terminal pongo:

metacity --replace

Después me andan todos los atajos. Ya no se que hacer al respecto...

---

### Post by Gpafundi on 2010-10-20
Listo! Encontré la solución buscando en internet.

De acá saque la solución:

[http://www.taringa.net/posts/linux/5406879/_Solucion-plugins-Compiz-en-Lucid-Lynx_.html](http://www.taringa.net/posts/linux/5406879/_Solucion-plugins-Compiz-en-Lucid-Lynx_.html)

Voy a poner los pasos que hice yo por si algún día borran la página de donde saque la respuesta.

1. Ir a Sistema > Gestor de paquetes Synaptic. Ahí ir a Configuración, Repositorios. Ir a la solapa Otro Software y desactivar todos excepto los de canonical.

2. Luego buscar en el buscador de los paquetes Synaptic "compiz", hacer click derecho sobre cada paquete y poner "Marcar para desinstalar completamente". Así con todos.

3.  Abrir un terminal (asegurándonos de tener las PPA's desactivadas) y tipear:

sudo apt-get update

4. Después de eso tipear:

sudo apt-get install compiz compiz-plugins compiz-gnome compiz-core compiz-fusion-plugins-main compiz-fusion-plugins-extra compizconfig-backend-gconf

5. Reiniciar el equipo. Buscar los paquetes en el gestor de paquetes Synaptic: CCSM y Emerald. Marcar para instalarlos y aplicar los cambios.

Por suerte a mí eso me funcionó. Espero que le sirva a alguien más.

Gracias a todos los que intentaron ayudarme.

---

### Post by ma13129926 on 2010-10-24
Excelente solución, gracias!!!!

---

