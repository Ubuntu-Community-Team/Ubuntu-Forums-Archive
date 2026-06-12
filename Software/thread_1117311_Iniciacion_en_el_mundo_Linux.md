---
title: "Iniciacion en el mundo Linux"
date: 2009-04-05
forum: Software
---

### Post by facu112 on 2009-04-05
Hola, gente soy nuevo y por curiosidad  comentarios muy positivos quiero probar como es el mundo linux.
Estube leyendo algunas cosas para poder entender algo del tema pero aun asi estoy muy desorientado.
Los datos de mi pc son:

Pentium 4 2.26 Ghz
1GB Ram
Windows XP SP3
Disco de 27GB NTFS (Instalado Windows)
Disco de 80GB NTFS

Mi idea es instalar ubuntu en el disco mas chico, pero estube leyendo que quizas tendria problemas... quiero conservar windows porque solo quiero probar ubuntu y ver como me va, no quiero que elimine windows ni hacer lios en mi computadora.
Quisiera que me recomienden los mejores pasos a seguir para poder instalar ubuntu de una manera correcta y no frustrarme en el intento.
Muchisimas gracias de antemano a la comunidad. :D

---

### Post by guillermolisi on 2009-04-05
> **facu112 said:**
> Hola, gente soy nuevo y por curiosidad  comentarios muy positivos quiero probar como es el mundo linux.
Estube leyendo algunas cosas para poder entender algo del tema pero aun asi estoy muy desorientado.
Los datos de mi pc son:

Pentium 4 2.26 Ghz
1GB Ram
Windows XP SP3
Disco de 27GB NTFS (Instalado Windows)
Disco de 80GB NTFS

Mi idea es instalar ubuntu en el disco mas chico, pero estube leyendo que quizas tendria problemas... quiero conservar windows porque solo quiero probar ubuntu y ver como me va, no quiero que elimine windows ni hacer lios en mi computadora.
Quisiera que me recomienden los mejores pasos a seguir para poder instalar ubuntu de una manera correcta y no frustrarme en el intento.
Muchisimas gracias de antemano a la comunidad. :D
Si lo que queres es usarlo para ver como te sentis con Ubuntu sin tener que particionar ni usar ni cambiar ni borrar lo que ya tenes, usa el LiveCd de Ubuntu.

Revisa que el BIOS de tu maquina permite iniciar desde el CD como primer dispositivo de boot, pones el CD e inicias.
Fijate que la primera opcion es usar Ubuntu en modo Live, sin instalar. Logicamente, los cambios que realices se perderan cuando reincies la maquina.

Una vez que compruebes que te satisface, ahi vamos por el proceso de instalacion en modo compartido con WinXP.

---

### Post by facu112 on 2009-04-05
Si Guillermo me habian recomendado lo mismo, ahora mismo estoy bajando la version 8.10 desktop de ubuntu. Me dijeron que tengo poner el cd reiniciar y bootear desde el cd, me equivoco?

Despues comentare la primera experiencia que tube con ubuntu... Solo tengo una consulta, que desventajas tengo al usar el livecd??

Muchas gracias.-

---

### Post by staar on 2009-04-05
> **facu112 said:**
> Si Guillermo me habian recomendado lo mismo, ahora mismo estoy bajando la version 8.10 desktop de ubuntu. Me dijeron que tengo poner el cd reiniciar y bootear desde el cd, me equivoco?

Despues comentare la primera experiencia que tube con ubuntu... Solo tengo una consulta, que desventajas tengo al usar el livecd??

Muchas gracias.-

Si tu BIOS esta configurado para iniciar primero desde el cd, lo ponés, reinicias y solito te va a aparecer un menú ;-)...

el livecd tiene dos desventajas principales, la primera es que todo lo que hagas en el sistema (configuraciones, ajustes o lo que sea) se va a perder al reiniciar ya que vas a estar trabajando desde el cd, no desde un disco duro (obviamente si modificas un archivo de tu disco duro, ponele una foto con el gimp, los cambios si se van a guardar), y la otra desventaja es que, por estar usando el sistema desde el cd, te va andar mas lento que despues de instalarlo...

por lo demás el sistema es perfectamente funcional e idéntico a como se verá después de instalado...

si te gusta el sistema, en el escritorio del livecd vas a tener el acceso al instalador, para que te pases a este lado de la fuerza :lolflag:...

saludos

---

### Post by clasificado on 2009-04-05
el livecd es un poco mas lento que el instalado en el disco, y cosas como la aceleración gráfica no está completamente disponible (de nuevo, hay que instalar)

Después no hay mayores desventajas, de hecho lo usamos mucho. Tené en cuenta que cuando reinicias se vuelve a cero (los programas instalados)

Como paso intermedio a particionar todo está instalarlo desde windows y te queda como un programa en "agregar o quitar programas". A esta configuración se le llama WUBI. De esta forma, no particionas nada, y al mismo tiempo tenés un ubuntu instalado.

Si no te va, o queres probar otra cosa, lo removes desde windows y chau pichu

a mi me dio muy buenos resultados.

clasificado

---

### Post by facu112 on 2009-04-05
> **clasificado said:**
> 
Como paso intermedio a particionar todo está instalarlo desde windows y te queda como un programa en "agregar o quitar programas". A esta configuración se le llama WUBI. De esta forma, no particionas nada, y al mismo tiempo tenés un ubuntu instalado.

Si no te va, o queres probar otra cosa, lo removes desde windows y chau pichu

a mi me dio muy buenos resultados.

clasificado

Me habian contado de un programa que hacia eso, es WUBI no?
Por lo que me decis clasificado, es la opcion mas parecida a tener ubuntu instalado no?
Me parece que me quedare con esta opcion para evaluar mis posibilidades con ubuntu.
Mil gracias a todos.-

Edit
Hay alguna indicacion especial para instalar Wubi? 
Ya lo estoy descargando... :D

---

### Post by josecuervo86 on 2009-04-05
Mira, tal vez me equivoque, pero me parece que te referis a VMware o VirtualBox, que son programas que te permiten virtualizar otro sistema operativo dentro de el (Yo lo uso para virtualizar Window$ en mi Uuntu). Esa es otra opcion. Si te interesa aca [0] te dejo el link de la pagina de VirtualBox para que leas y te fijes como es la onda y si te interesa lo podes bajar instalarlo y despues virtualizar Ubuntu. Tambien tiene como contra que no obtenes el mismo rendimiento que si lo tuvieras instalado. Para que veas como es la onda aca [1] tenes un video que hice del programa funcionando.

[0] [http://www.virtualbox.org/]("http://www.virtualbox.org/")

[1] [http://www.youtube.com/watch?v=CpKnuvKUn7U]("http://www.youtube.com/watch?v=CpKnuvKUn7U")

Saludos y suerte en tu aventura en este lado :D

---

### Post by Monchix on 2009-04-06
Hola como andas, bienvenido a este gran mundo y te comento que si te gusta la informatica hay un gran universo que te espera y la mejor opciones es empezar con Ubuntu.

Con respecto a tus dudas, si Wubi es un probrama que viene en el livecd y te permite ejecutarlo desde windows, este te va a permitir instalar Ubuntu desde windows, tiene us ventajas y desventajas, pero te lo recomiendo si recien empezas y no queres estar particionando tu disco, te dejo un tutorial:

[http://tuxpepino.wordpress.com/2008/05/19/instalar-ubuntu-desde-windows-con-wubi/](http://tuxpepino.wordpress.com/2008/05/19/instalar-ubuntu-desde-windows-con-wubi/)

Espero te sirva y animate que no te vas a arrepentir.

---

### Post by guillermolisi on 2009-04-06
> **facu112 said:**
> Me habian contado de un programa que hacia eso, es WUBI no?
Por lo que me decis clasificado, es la opcion mas parecida a tener ubuntu instalado no?
Me parece que me quedare con esta opcion para evaluar mis posibilidades con ubuntu.
Mil gracias a todos.-

Edit
Hay alguna indicacion especial para instalar Wubi? 
Ya lo estoy descargando... :D
Si, antes de usar Wubi defragmenta el disco.

Wubi no es una instalacion pura de Ubuntu ni tampoco es como el LiveCD. Vas a ver como que Ubuntu queda integrado a Windows.

---

