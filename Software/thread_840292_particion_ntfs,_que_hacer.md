---
title: "particion ntfs, que hacer?"
date: 2008-06-25
forum: Software
---

### Post by xpelaox on 2008-06-25
Hola gente!! 

Tengo instalado Ubuntu y vista en mi notebook, pero vista ya no lo quiero mas (ademas que toque algo y lo rompi:P)entonces tengo la particion ntfs ahi, y queria "anexarla" a ubuntu.

Lo primero que se me ocurrio es borrar esa particion y "fusionarsela" a la de ubuntu, pero por lo que lei eso no se puede hacer sin tener que reinstalar todo.

entonces, mi pregunta es, como puedo hacer para aprovechar ese espacio? Que me recomiendan?

---

### Post by MeduZa on 2008-06-25
> **xpelaox said:**
> Hola gente!! 

Tengo instalado Ubuntu y vista en mi notebook, pero vista ya no lo quiero mas (ademas que toque algo y lo rompi:P)entonces tengo la particion ntfs ahi, y queria "anexarla" a ubuntu.

Lo primero que se me ocurrio es borrar esa particion y "fusionarsela" a la de ubuntu, pero por lo que lei eso no se puede hacer sin tener que reinstalar todo.

entonces, mi pregunta es, como puedo hacer para aprovechar ese espacio? Que me recomiendan?

si lo podes hacer, siempre y cuando no metas la pata y borres la particion que no es.
te conviene hacerlo desde le LIVE CD, Abris el gparted, borras la particion NTFS, y despues a la particion EXT3 le pones CRECER y la expandis al tamaño nuevos que vos quieras, eso se hace sin perde informacion y sin tener que instalar todo de nuevo.
El unico problema que puede surgir es que se te baya la luz XD pero bue eso ya no lo manejas vos :lolflag:

yo lo hice sin problemas, pero si queres hacerlo seguro haces un backup antes para ESTAR mas SEGURO, pero te digo que es facil y seguro.

Suerte.

---

### Post by odiseo77 on 2008-06-25
Hola. Lo que yo haría antes de hacer cualquier otra cosa sería respaldar toda la información y datos personales que puedas tener en tu notebook. Si tienes un disco duro externo, mucho mejor. Lo importante es respaldar toda esta información en algún dispositivo de almacenamiento que esté fuera de tu notebook, en caso de que algo salga mal.

Luego, tienes dos opciones:

A): Bajarte live-cd de Gparted o PartedMagic de [DistroWatch]("http://distrowatch.com/"), quemarlo en un cd (obviamente) y arrancar la PC con el cd puesto (yo te recomendaría Gparted; una vez usé PartedMagic y me pareció un poco defectuoso). Luego, reparticionar todo el disco duro a tu gusto, lo cual significaría volar la partición de windows y la de ubuntu y luego crear un nuevo esquema de particionado para uso exclusivo de ubuntu. Finalmente, reinstalar ubuntu en las particiones recién creadas.

B): No estoy seguro de que esta otra posibilidad funcione, aunque *en teoría* debería funcionar (y de paso, es más elegante y pulida que la anterior; sólo que como nunca lo he hecho, no estoy seguro de que funcione). Se trata de formatear la partición windows y crear allí mismo una partición linux (ext3, resiserfs, o alguna otra que prefieras) en ese espacio del disco. Luego, una vez tengas creada la partición, usar el comando ***dd*** para crear una imagen de tu partición Ubuntu y transferirla a la partición linux que creaste (donde estaba windows). NOTA: el comando "dd" es un comando muy versátil y extremadamente potente que puede servir para muchas cosas, entre esas dejar un disco duro completamente en blanco, así que no conviene para nada usarlo alegremente sin saber cómo funciona (te puedo apuntar a un wiki sobre este comando y decirte cómo realizar esta operación). Luego tendrías que modificar el /boot/grub/menu.lst del Ubuntu clonado para poder arrancarlo. Después de esto, tendría que usar chroot para acceder y tomar control del Ubuntu clonado y reinstalar el grub en el MBR. 
Finalmente (y aquí es donde me parece que las cosas podrían ir mal), para conseguir lo que buscas, que es darle todo el espacio del disco duro a Ubuntu, tendrías que borrar todas las particiones excepto la del Ubuntu clonado (obviamente), que estaría al principio del disco duro, y usar el live-cd de Gparted para redimensionarla de manera que ocupe todo el disco duro (dejando un espacio al final para la swap, claro está). Pero, como dije antes, es en este último paso donde las cosas podrían ir mal, ya que, según me parece, al redimensionar la partición de Ubuntu, probablemente cambiaría su UUID y eso crearía problemas en el arranque.

Después de verlo todo en retrospectiva, la solución más simple (y la que seguro funcionará) es la primera. Creo que la única ventaja de la segunda opción es que no tendrías que reinstalar drivers, plugins y demás (y aprenderíamos cosas nuevas :)). Después de todo, creo que yo me iría por la primera opción (o en caso de que estuviera de vacaciones y con algún tiempo ocioso, probaría la segunda, sólo para ver qué tal).

Saludos.

Bueno, creo que MeduZa se me adelantó. Esa seria otra opción :)

---

### Post by xpelaox on 2008-06-25
gracias por sus consejos! voy a probar con el live cd, pero creo que en una oportunidad intente hacerlo y no me dejo, pero ya estoy backupeando:)

cuando termine les cuento que paso!

Saludos y gracias gentes!:D:guitar:

---

### Post by EnriqueK on 2008-06-25
Lo que yo haría es formatear la partición ntfs en EXT3 u otra propia de linux y allí mover la /home , de esa manera te evitas el tener que redimensionar y además es mas eficiente.

---

