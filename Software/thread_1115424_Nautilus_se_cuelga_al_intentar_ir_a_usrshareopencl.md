---
title: "Nautilus se cuelga al intentar ir a /usr/share/openclipart - Ubuntu 8.04 LTS i386"
date: 2009-04-03
forum: Software
---

### Post by anagramagia on 2009-04-03
Hola, Nautilus se cuelga, les cuento que uso Ubuntu 8.04 LTS i386 en una pc con amd 64 x2 dual core, y 2GB RAM. Y así y todo Nautilus se cuelga, aproximadamente 4 de cada 5 veces que hago lo siguiente: click en sistema de archivos, usr, share, openclipart, incluso, a veces se cuelga directamente cuando clickeo en share. Noto que el indicador de uso de cpu del monitor de sistema sube hasta 50% con algunos picos superiores y eso lo utiliza el proceso de nautilus. No importa cuánto espere (de todos modos no he esperado más de 5 minutos) no muestra el contenido de la carpeta y no me queda otra que terminar el proceso de manera forzada. Luego de cerrarse, se abre de nuevo automáticamente una ventana del administrador de archivos y muestra mi carpeta personal.
Si quiero acceder a /usr/share/openclipart con el midnight commander, no tengo ningún problema.
Me gustaría saber por qué se cuelga y si existe alguna solución, porque el hardware que hay es más que suficiente, ¿no?. 
También intenté arrancar el nautilus desde el terminal porque pensé que cuando sucediera el cuelgue iba a aparecer un mensaje de error o alguna información útil para dilucidarlo pero no aparece ningún texto que ayude. Este procedimiento me lo sugirió alguien en el foro de puppy linux cuando tuve problemas con abiword y en ese caso sirvió para ver qué fallaba.
Les agradezco si me pueden ayudar.

---

### Post by pablo.s on 2009-04-03
Qué versión de Nautilus es?

---

### Post by anagramagia on 2009-04-05
Es la que viene con Ubuntu 8.04 LTS i386. No sé qué número de versión es. Ahora no puedo fijarme, estoy en otra máquina.

---

### Post by pablo.s on 2009-04-06
> **anagramagia said:**
> Es la que viene con Ubuntu 8.04 LTS i386. 

Si es la versión sin actualizar, la podés actualizar a
la mas reciente. Si es la mas reciente, entonces hay
que ver la causa que hace reiniciar el proceso de
Nautilus. ¿Tiene el mismo comportamiento al
mostrar los archivos como icono que como lista?
Si solamente reinicia cuando está como icono puede
ser causa de una falla en la extensión de Nautilus
que presenta las miniaturas.

---

### Post by guisheca on 2009-04-06
Pero no se puede actualizar a la versión mas reciente estando en hardy (8.04) lo único que le queda es actualizar el ubuntu, si es que la única solución que le queda es actualizar nautilus.

---

### Post by euzkoarima on 2009-04-06
Mi pc en la oficina es similar, y misma versión de ubuntu. No tengo el problema. Lo único que se me ocurre es que en preferencias de nautilus, solapa vista previa, deshabilites todo.
Que esté tratando de calcular la vista previa de algún archivo, quizas corrupto y se cuelgue haciendo eso, es lo único que se me ocurre que pueda estar consumiendo tanta cpu.

Saludos,
Eduardo

---

### Post by pablo.s on 2009-04-06
> **guisheca said:**
> Pero no se puede actualizar a la versión mas reciente estando en hardy (8.04) lo único que le queda es actualizar el ubuntu, si es que la única solución que le queda es actualizar nautilus.

Claro, pensé que estaba sobreentendido que decia
a la versión mas reciente dentro de 8.04. Porque me da
la impresión que está con la versión que trae Hardy en
la instalación. Yo le recomiendo actualizar dentro de su
versión, no que actualice de versión.

Con respecto a lo que dice Eduardo es casi lo mismo que
le comento yo: hay alguna extensión que está abortando
el proceso o causando [segmentation fault]("http://es.wikipedia.org/wiki/Access_violation") al parecer.
Si actualiza y sigue haciendo el mismo error podemos ir
barajando otras causas. Espero la respuesta...

---

### Post by anagramagia on 2009-04-12
La versión que estoy usando es la 2.22.2,sin actualizar, voy a intentar bajar una actualización. Voy a ver si pasa lo mismo en la vista de íconos y en la de lista. También voy a probar deshabilitar todo en vista previa de las preferencias. Y en unos días les cuento lo que resulta.
Gracias y saludos.

---

### Post by anagramagia on 2009-04-20
Todavía no actualicé, ya que no tengo una conexión a internet en la máquina con ubuntu y se me complica. 
Pero descubrí que se cuelga sólo si intento abrir /usr/share desde el panel lateral de árbol de nautilus. Si cierro el panel lateral y uso el panel que queda, entonces no hay problema, y funciona tanto en la vista de íconos como en la de lista.

---

