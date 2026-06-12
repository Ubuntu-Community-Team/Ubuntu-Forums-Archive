---
title: "[SOLVED] Hardy se reinicia solo."
date: 2008-06-02
forum: Software
---

### Post by ramiro_md on 2008-06-02
Hola ubunteros, resulta que hace unos dias instale hh en mi computadora de escritorio. El tema es que anda todo "barbaro", con la excepcion de que cuando quiero abrir aplicaciones, el sistema se reincia solo :confused:..aclaro que no es siempre con la misma aplicacion, sino que a veces lo hace con amsn, otras con kdenlive, y asi estoy xD...si alguien tiene una idea para esto ??..Otra cosa, la opantalla de inicio donde pones el usuario y pass se ve enorme y no se ven las opciones para cambiar sesion y demas...como lo soluciono ??. Un saludo.

---

### Post by faktorqm on 2008-06-02
Para solucionar lo del tamaño de la pantalla de login, tenes que hacer:

```
sudo gedit /etc/X11/xorg.conf
```

y buscar la linea que dice:

```

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		[COLOR="Red"]**Virtual	1600	1200**[/COLOR]
	EndSubSection

```

Tenes que modificar la linea en rojo, si tu resolucion de escritorio es de 1280x1024 ahi te tiene que quedar Virtual 1280 1024.
Si la linea no existe, agregala.

Con lo de los reinicios, fijate los logs a ver si te dan una pista. Salu2!!

---

### Post by nemodot on 2008-06-02
Fijate si no es un problema de hardware. Si tenes Windows instalado decinos si pasa algo parecido o si no.

---

### Post by anarko on 2008-06-03
Fijate que pude ser algo totalmente agento al ubuntu, puede que tengas alguna memoria muy pinchada, o el procesador este calentando o la placa de video este calentando, esas cosas pueden probocar que se reinicie la PC. 

Para lo de la memoria podes usar el teste de memoria que viene con ubuntu, aparece como una opcion en el grub.
Para lo de las temperaturas podes probar con algun soft que lea las temperaturas del BIOS como lmsensors o mas facil buscar algun cosito de esos que se agrega a la barra de tareas que muestren la temp de los componentes del mother.

---

### Post by ramiro_md on 2008-06-05
Muchachos, gracias por las respuestas, pero problemas de hard no creo que sean, porque uso win$ muy frecuentemente y no me pasa, si fuera porblema de hard deberia ocurrir en ambos sistemas.

---

### Post by pablo0469 on 2008-06-06
> **faktorqm said:**
> Para solucionar lo del tamaño de la pantalla de login, tenes que hacer:

```
sudo gedit /etc/X11/xorg.conf
```y buscar la linea que dice:

```

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    Defaultdepth    24
    SubSection "Display"
        Depth    24
        [COLOR=Red]**Virtual    1600    1200**[/COLOR]
    EndSubSection

```Tenes que modificar la linea en rojo, si tu resolucion de escritorio es de 1280x1024 ahi te tiene que quedar Virtual 1280 1024.
Si la linea no existe, agregala.

Con lo de los reinicios, fijate los logs a ver si te dan una pista. Salu2!!

Hice este retoque pero poniendo la resolucion que uso (1024x768) y es Impresionante como Mejoro la Velocidad de Arranque y Carga del Escritorio del Sistema... parece que ya no pierde tiempo haciendo cambios en las resoluciones.

Gracias, y Saludos.

---

### Post by ramiro_md on 2008-06-12
Muchachos, hace mil que postie estop..y me parece raro q nadie me haya dado la soluucion =S...hardy se sigue reiniciando de vez en cuando com ox arte de magia

---

### Post by fgl82 on 2008-06-12
Alguien más arriba te dijo que te fijes en los logs, a mí tb me parece una buena idea.

---

### Post by atari130xe on 2008-06-12
Perdón (vi luz y entré) :), te cuento que yo tengo instalado Hardy heron y me pasaba algo similar. Si hablás de "reiniciar la PC" o sea de que la compu se "bootea" no lo sé, pero si lo que te pasa es que se "reinicia la sesión" o sea que sin llegar a apagarse la pc en ningún momento, volvés a la pantalla de login, y si tenes una placa de video Nvidia (yo tengo una Geforce 8400 GS) lo más probable es que sea el bendito driver propietario con un par de bugs, yo tenia la version que instala EnvyNG que instala la 169... y me pasaba exactamente eso, se reiniciaba la sesion cada vez que intentaba cambiar por ej la imagen a mostrar en aMSN o hacer click en una ventana de aviso con Kopete, la solución en mi caso? desinstalar el driver propietario 169.etc etc etc y Envy y bajarte el último driver del sitio de Nvidia e instalarlo, no es dificil siguiendo los pasos que vas a encontrar en Google), ahora noto que no tengo ese problema pero si problemas con java y el firefox 3.0b5 que se me pone como loca la pantalla, pero ya veré que hago jejeje.

---

### Post by rojojuan on 2008-06-12
> **faktorqm said:**
> Para solucionar lo del tamaño de la pantalla de login, tenes que hacer:

```
sudo gedit /etc/X11/xorg.conf
```

y buscar la linea que dice:

```

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		[COLOR="Red"]**Virtual	1600	1200**[/COLOR]
	EndSubSection

```

Tenes que modificar la linea en rojo, si tu resolucion de escritorio es de 1280x1024 ahi te tiene que quedar Virtual 1280 1024.
Si la linea no existe, agregala.

Con lo de los reinicios, fijate los logs a ver si te dan una pista. Salu2!!

Para ir aprendiendo más, modificando los parámetros de Virtual, que es lo que estoy haciendo? 
Gracias por responder

---

### Post by xpelaox on 2008-06-12
el problema solo pasa con 8.04? probaste reinstalarlo?

---

### Post by ramiro_md on 2008-06-13
atari130xe, es exactamente lo que me paso capo !..ya estoy instalando el driver de nuevo desde nvidia.Gracias, lo pruebo y te aviso.

---

### Post by ramiro_md on 2008-06-13
Man, en nvidia me dice q no tiene el driver para mi geforce 6100 n405 !!! (es una integrada). Si alguien los tiene, o sabe de que otro lado se pueden obtener avisee, gracias de nuevo.

---

### Post by faktorqm on 2008-06-13
que tenes la ecs con todo integrado? yo le mande el envy y anda a la perfeccion, ni un solo drama... Salu2!

---

### Post by ramiro_md on 2008-06-13
ajajja..vos tambien tenes el mother elitgroup...?...le acabo de mandar envy y sigue igual =S

---

### Post by faktorqm on 2008-06-14
En realidad me dieron en el trabajo una mother de esas y cuando le di gas con linux, bueno, la tuve que configurar, pero instale el envy y ya, luego desactive los efectos por que tengo poca memoria y me relentizaba todo al "gas". Que es lo que te anda? o sea, cual es el error?

rojojuan: con el virtual cambias la resolucion del gdm/kdm/xdm. 

Salu2!

---

### Post by ramiro_md on 2008-06-14
Lo que  pasa es que se "reinicia la sesión", cada vez que intento cambiar por ej la imagen a mostrar en aMSN o hacer click en una ventana de aviso con Kopete.

---

### Post by rojojuan on 2008-06-14
Por si sirve, en Hardy instalé el EnvyNG, no el antiguo Envy. Esta en los repositorios de HH.

---

### Post by faktorqm on 2008-06-15
usa pidgin, no es tan malo despues de todo

---

### Post by ramiro_md on 2008-06-17
jajaja...no es x el mensajero, quiero que las cosas anden bien xD...me fije en el cd del mother y no habia drivers para linux =S y no los encuentro x internet...jugadisimo mal...sido buscando =S

---

### Post by faktorqm on 2008-06-18
En mi ECS el chipset es nvidia, o sea, nforce 4 (aunque segun lshw usa los drivers del nforce 2). la placa es gforce 6100 nforce 405 y el resto de los puentes los controla todos MCP61.
Revisa el setup del bios que se yo, capaz tenes algo mal seteado ahi, pero estas mothers dicen que si en la primera cita..... :D

---

### Post by ramiro_md on 2008-06-18
SI, es exactamente igual a mi mother...el tema q si hubiera algo mal seteando en el bios deberia andar mal en win$ tambien no ??...y en 7.10 con esta misma maquina no me pasaba...

---

### Post by ArtPulse on 2008-06-18
Una pregunta re *****:

Tenés micro de 32 o 64 bits?

(y además respondeme: qué instalaste, Ubuntu 32 o 64?)

conozco uno q se le reiniciaba todo el tiempo el 7.10 :S... tenía 64 bits
El Hardy se le reinicia menos xD creo que tiene que ver con el video.

saludos!

---

### Post by faktorqm on 2008-06-18
O sea tenes ubuntu 32 o 64? el micro es de 64 claro, si tenes ubuntu de 64..... primero explicame por que lo tenés, si no tenés ninguna buena razón que me convenza, borralo e instala de cero ubuntu de 32. Salu2!

---

### Post by ramiro_md on 2008-06-18
Muchachos tengo un atlhon 64 bits y ubuntu 8.04 de 64..me extraña araña...
x q no al de 64 ?? en 7.10 tmb era de 64 y ni un drama...

---

### Post by ramiro_md on 2008-06-19
Muchachos !!!!!!!!! listoooo !!!!!!!! era mas sencillo de lo que parecia....reinstale amsn :$ ahora..enderecemos la nave y partimos nenee !

---

