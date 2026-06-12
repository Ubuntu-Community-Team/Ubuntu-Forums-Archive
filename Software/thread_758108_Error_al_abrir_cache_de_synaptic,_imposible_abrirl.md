---
title: "Error al abrir cache de synaptic, imposible abrirlo, eliminar o actualizar"
date: 2008-04-17
forum: Software
---

### Post by mrchelo2002 on 2008-04-17
Hola que tal. Despues de mucho leer y buscar sobre el tema, necesito pedir ayuda.
Intente instalar Facturalix 1.6.0, pero hubo un error de instalación que no comprendí. Luego de eso en el menu Aplicaciones aparece una rama que dice Otros -> No Name. Supongo que eso se creo porque es nuevo. No se ejecuta.
Al intentar desinstalarlo, Synaptic no inicia, me dice que Facturalix tiene paquetes corruptos, o no tengo privilegios, y se cierra.
INtente varias formar de reinstalar, desinstalar, baje nuevamente el archivo, pero me dice que faltan dependencias.
No tengo idea de como arreglar eso. Actualmente estoy reinstalando ubuntu, pero tengo miedo de intentar instalar otra cosa.
Encontre esta pagina entre tantas cosas, fue lo unico que no probe, pero de ingles poco y nada, y de ubuntu recien comienzo, asi que si alguien puede aclararme el tema le estare inmensamente agradecido.
[http://ubuntuforums.org/showthread.php?t=84676](http://ubuntuforums.org/showthread.php?t=84676)

Chelo.

---

### Post by clasificado on 2008-04-17
que hacés chelo!

Podrias intentar abrir una consola y ejecutar 
```
sudo apt-get update
```

¿Que te dice?

clasificado

---

### Post by mrchelo2002 on 2008-04-18
Hola que tal. Gracias por respoder.
Ahora termine de reinstalar todo el sistema, anda bien, pero agendo todo por si aparece devuelta.
Lo último que hice fue buscarlo en el repositorio y lo encontré, creo que active todas las opciones de recursos (creo que se llama asi de donde se buscan las cosas). Estaba, lo marque para instalar en synaptics, lo instalo, todo ok. Pero no encuentro de donde iniciar el programa pues no aparece en ningun lado. NO tengo idea de donde estan los ejecutables en ubuntu, pero todavía no busque info sobre eso.
Gracias Clasificado!
Chelo

---

### Post by faktorqm on 2008-04-18
Hola, te cuento mas o menos como es, en linux los programas no se instalan, es decir, en windows vos los instalas, los registras, etc,etc. En linux, si tenes los fuentes, lo compilas, y eso se copia a distintas ubicaciones. 
2 de ellas, /usr/bin para los ejecutables de usuario y /usr/sbin para ejecutables de root (administrador). 
/home/nombre_de_usuario/.nombre_programa va la configuracion del programa y asi.
La segunda opcion es que vos tengas un paquete precompilado que lo que hace es "anotarse" en una lista de software como que existe (la del apt) y se copia a las mismas ubicaciones. Es mas, las podes ver cuando le das doble click y despues pones la ficha "archivos" del gestor de paquetes.

Bueno, ahora bien, existe un comando para averiguar donde esta un programa. No necesariamente vas a encontrar ejecutables en todas las ubicaciones, pero sirve de mucho cuando queres saber donde esta algo. 

```
whereis firefox
```

El comando es "whereis", y ahi te puse un ejemplo para que veas donde esta el firefox :P

Ahora bien, suponete que ya averiguaste donde esta el facturalix, ahora andate hasta sistema -> preferencias -> menu principal y ahi selecciona la seccion que quieras y le das al boton "nuevo".
Ahi te pregunta, la ruta al icono del programa, el comando, que va a ser el nombre del archivo mas la ubicacion, (por ejemplo /usr/bin/factura_loca) y ahi ya lo tenes en tu menu de aplicaciones.

Aviso que no estoy mirando un ubuntu y escribi todo esto de memoria, asi que si me equivoque en algun nombre sabe disculpar. :D Espero que te haya servido. Salu2!!!!

p.d.: Para la proxima: con el comando ```
sudo apt-get install -f
``` o algo muy parecido te arregla las depedencias rotas automaticamente y te elimina o instala las dependencias faltantes y te pregunta que queres hacer en cada caso, si instalar todo, borrar todo o probar. Salu2!

---

### Post by Patchiu on 2008-04-18
A mi me paso algo similar un dia que habia bajado varios paquetes Gdebi, y al instalar "Second Life"... la instalacion era media lenta.. y como un salame cancele la instalacion... (por querer instalar los otros primero y despues el Second Life que era mas pesado..)
No me andaba ni el synaptic, ni el programa "añadir/quitar", ni el Gdebi.. es mas, me decia que no encontraba el paquete, cuando lo tenia instalado......

En fin, No recuerdo como hice en este momento.. pero recuerdo que toque de todo... pero lo arregle.. :)

Pero hay una solucion para eso.. salu2!

---

### Post by kantra on 2008-10-02
Les cuento que a mi me pasó el mismo problema,instale Cinelerra de los repositorios akirad y cuando me actualizó sistema me desisteló, el problema es que me dice que tengo dependencias rotas y que el archivo /var/cahe/apt/srcpkgcache.bin está sin permisos y corruptos.

Antes que nada les cuento que ya prove con:
apt-get update
apt-get -f install

incluso le hice un autoremove
apt-get autoremove,

y nada de nada, no puedo instalar, actualizar y nada en mi máquina, alguien tiene idea de que rayos puedo hacer, porque llevo días buscando y nada que encuentro una respuesta.

Saludos, Kantre

---

### Post by faktorqm on 2008-10-03
Tengo entendido que con 

```
sudo apt-get install -f
```

deberia salir andando... que "solucion" propuesta utilizaste? salu2!

---

### Post by berserker_b2k on 2009-01-29
hacé primero un sudo apt-get update

y después sudo update-apt-xapian-index

Saludos!

---

