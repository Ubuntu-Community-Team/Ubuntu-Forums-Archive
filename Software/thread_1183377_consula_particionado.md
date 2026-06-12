---
title: "consula particionado"
date: 2009-06-10
forum: Software
---

### Post by Barasuishou on 2009-06-10
bueno digamos que mi maquina (a mi parecer) está para el desastre en particiones, les cuento brevemente, con ayuda de un amigo puse xp, desps me dió curiosidad el win7 tonces hize partición y lo mandé, a eso le agregé(no pude pasar mucho tiempo sin volver a mi amado linux) ubuntu, después volvé el win7(por cierto el grub de win7 o como se llame no se fué no se como sacarlo y es muy molesto)

ahora por fin pude hacer espacio y me paso todo lo que tenía en linux a windows, para que, para formatear e instalar linux de mejor manera, voy a instalar en una partición ubuntu, y en otra kubuntu, para probar bien por separado ambos, ya que probé instalando uno encima del otro y es un desastre, y además por que de a poco estoy incentivando a mi hermana menor a usar ubuntu, y a ella le gusta más gnome(no tengo mucho exito no le interesa aprender, si vieran las cosas que me pregunta XD)

la cosa es que quisiera que el /home sea uno solo, y que pueda accederlo desde ambos OSS, por lo que se, si hago un / para ubuntu, y un / para kubuntu, desps hago un solo /home y ambos me lo aceptarían, no?

segunda cuestión en que orden recomiendan instale, ubuntu--kubuntu o inversa?

y la tercera que formato recomiendan ext3 o ext4???


resumido :P

1.si hago dos particiones "/" una para ubuntu y otra para kubuntu, y un "/home" ambas toman el mismo home?.¿Por cierto cuanto espacio recomiendan para las "/"?.

2.recomendación de orden a la hora de instalar.

3.¿ext3 o ext4?


4.a casi me olvido poseo un procesador AMD Athlon64 1.8ghz +3000, con 1gib RAM, y una Nvidia Geforce 7100gs,y utilizo la pc para hacer cosas en blender, gimp, y edición de sonido, además de jugar :P ¿ recomiendan que instale la versión de 32bits o la de 64bits?

solo por si a caso mi disco es de 180gibs y 97gibs los ocupa el winXP xs

soy un usuario un poco por arriba de principiante así que por favor compasión XD

saludos chauuu

---

### Post by staar on 2009-06-10
bueno, primero que nada como tenés 1 GiB de RAM, y vas a usar blender, mejor instalá 32 bits, que usa un poquito menos de memoria...

el /home separado lo vas a tener que hacer durante la instalación de (k)ubuntu (el orden de instalación es indistinto, no afecta en nada), eso sí, mejor crea usuarios con nombres diferentes entre ubuntu y kubuntu, para que cada uno tenga una carpeta distinta dentro de la partición, sino se te va a armar lio y puede haber problemas entre las configuraciones...

también va a ser mejor si compartis la partición de swap, y, obviamente vas a tener que hacer particionado manual en ambas instalaciones, para, en la segunda, indicar el punto de montaje de /home y swap en la partición correspondiente...

para cada /, dejá entre 4 y 8 GB, no más de eso, no es necesario, para swap dejá 1 GB, y el resto para /home, como vas a tener 5 particiones en el disco, vas a tener que crear una extendida (no se pueden poner más de 4 particiones primarias por disco), te recomendaría que crees una sola extendida en todo el espacio no ocupado por Ventanas, y dentro de esta, crear las 4 particiones (lógicas) que vas a necesitar...

filesystem? ext4 anda rápido, pero algunos no confian mucho en él todavía (aparte de que distros con versiones viejas del kernel no lo pueden leer), lo mejorcito y más seguro que podés hacer, es ext4 para los /, y ext3 para el /home, cosa de tener tus datos a salvo (y rescatables más fácilmente con una herramienta externa en caso de falla) y aprovechar la velocidad de ext4...

saludos

---

### Post by gmunioz on 2009-06-10
Hola bar...:

Mi sugerencia es que:

1- Instales en primer término, la versión que no usas personalmente

en este caso Ubuntu. ¿Por qué? Porque la última versión instalada

es la dueña del Grub, asi si decides eliminar Ubuntu y quedarte con 

Kubuntu solamente, no tendrás problemas con el Grub.

2- Versión de 32 bits. ¿Por qué? Porque la de 64 bits, es aconsejable 

usarla a partir de los 4 gigas de RAM.

3- ¿En que particiones? 

a- Primero Ubuntu, en:

a1- Una partición lógica, sistema de archivos ext4, de unos 14 gigas

si vas a copiar dvds, punto de montaje /

a2- Una partición lógica, sistema de archivos intercambio, de 1 giga

punto de montaje por defecto, intercambio, (swap)

a3 - Una partición lógica, sistema de archivos ext4, del resto de los

gigas disponibles menos 14 gigas, punto de montaje /home

b- Segundo kubuntu, en:

b1- Una partición lógica, sistema de archivos ext4, de los 14 gigas 

restantes, punto de montaje /

b2- en a2, la partición lógica de swap, para swap compartida

b3- en a3, la partición lógica de /home, para /home con distinto

usuario y **sin formatear.**

Respecto de ext3 / ext4 es cierto que las distribuciones viejas no

lo pueden acceder, mas si tienes los cds de kubuntu y de Ubuntu,

desde una sesión live de cualquiera de ellos los podrás acceder

así que me inclino por ext4.

---

