---
title: "Awn"
date: 2008-05-21
forum: Software
---

### Post by ramiro_md on 2008-05-21
Hola amigos ubunteros, resulta que tengo un drama con el avant windows navigator. La cuestion es que intente de manera fallida instalarlo desde los repositorios, xq me dice error al actualizar la sources.list: 
Err [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy/avant-window-navigator Packages        
  404 Not Found
Err [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy/avant-window-navigator Sources         
  404 Not Found
Entonce sbaje los paquetes deb..la cuestion es que anda de maravillas peor no tengo los applets y no se de donde conseguirlos, si alguien me da una mano jejeje...
Mi ubuntu es la 7.10.

---

### Post by pol666 on 2008-05-21
Borra lo que pusiste del AWN en el SOurce list, desinstala AWn y volvela a instalar desde unos REPOSITORIOS que anden bien.

---

### Post by ramiro_md on 2008-05-21
La cosa es q no encuentro repositorios ¬¬ los unicos q encuentro son los de tuxfamily.org q no andan =(

---

### Post by Mataca on 2008-05-21
Repos para Gusty

deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main

De nada :)

---

### Post by vk-cdg on 2008-05-22
Que versión de Ubu tenés? Gutsy o Hardy?

Acá en [este]("http://ubuntuforums.org/showthread.php?t=782787") thread yo pedía ayuda con lo mismo y lo pude solucionar. 
Instalé la de los repos oficiales de AWN y no la de los repos de Ubuntu. Esta última viene pelada.

---

### Post by ramiro_md on 2008-05-22
GRacias mataca ya corre, lueo de poenr esas linueas en el sources.list la actualize y puse a descargar lo siguiente (para el q lo necesite):
 sudo aptitude install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr
Gracias a vk-cdg tambien, auqnue no probe su opcion xD.

---

### Post by ramiro_md on 2008-07-30
Muchachos, he instalado awn desde los repos de hh...pero viene pelado !! como consigo los aplets ?? otra cosa..hay alguna forma de hacer que las ventanas no se minimizen en el dock ?? gracias de ante mano =)

---

### Post by pol666 on 2008-07-30
Desconosco cual es la razon por la que el AWN de los repositorios oficiales viene sin applets, te recomiendo que la borres e instales desde los repositorios que estan en la pag oficial.

O de ultima, fijate si encontras el .deb que viene awn+awn curves. que me costo un monton encontrar pero el efecto curve esta bueno ;)

---

### Post by crosssover on 2008-07-31
yo te recomiendo que borres el AWN e instales el cairo-dock. le pasa el trapo completamente y no da problemas.

[http://developer.berlios.de/projects/cairo-dock/](http://developer.berlios.de/projects/cairo-dock/)

---

### Post by pol666 on 2008-07-31
no, no es mejor ni peor, es diferente, yo con Cairo dock tuve unos dramas o no la entendi bien... pero esta buena tiene unos efectitos copados que awn no tiene..pero no es mejor Awn es practica y tiene buenos applets.

---

### Post by Darkade on 2008-07-31
Aqui hay un howto del AWN, aunque esta ingles.

[http://ubuntuforums.org/showthread.php?t=762363](http://ubuntuforums.org/showthread.php?t=762363)

Basicamente es agregar otros repositorios e instalarlo desde ahi. estos si tienen applets y funcionan bien. Los de tuxfamily estaban bastante buggeados. Este es un proyecto activo y soporta nativamente el AWN curves.

---

### Post by ramiro_md on 2008-07-31
> **Darkade said:**
> Aqui hay un howto del AWN, aunque esta ingles.

[http://ubuntuforums.org/showthread.php?t=762363](http://ubuntuforums.org/showthread.php?t=762363)

Basicamente es agregar otros repositorios e instalarlo desde ahi. estos si tienen applets y funcionan bien. Los de tuxfamily estaban bastante buggeados. Este es un proyecto activo y soporta nativamente el AWN curves.

al actualizar la source.list me tira este error

Des:36 [http://espelhos.edugraf.ufsc.br](http://espelhos.edugraf.ufsc.br) hardy-security/multiverse Sources [14B] 
Descargados 8397kB en 1min52s (74,8kB/s)                                       
E: No se pudo bloquear /var/lib/dpkg/lock - open (11 Recurso temporalmente no disponible)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

y no me agrega los repos =S

---

### Post by Hernán-Amaya on 2008-07-31
Ramiro fijate que debes tener abierto el synaptic o debes estar usando el aptitude o algo así, cerrá e intenta de nuevo

---

### Post by Darkade on 2008-07-31
Estas usando otro synaptic o algo asi? debes de usar solo una entidad para instalar/desinstalar aplicaciones a la vez. Yo tengo Ubuntu en ingles, pero creo q es ese el error que te esta arrojando, por el dpkg.
cierra todas lo que instale cosas y vuelve a intentar agregar los repositorios

---

### Post by ramiro_md on 2008-07-31
> **Hernán-Amaya said:**
> Ramiro fijate que debes tener abierto el synaptic o debes estar usando el aptitude o algo así, cerrá e intenta de nuevo

SISI era eso...no me di cuenta jejeje...gracias hernan !...un saludo muchachos =)

---

### Post by pol666 on 2008-07-31
mmm, estuve usando kde, y me di cuenta que tanto cairo como awn, son pesimo el desempeño en kde, aunque por lo menos cairo andaba, awn ni eso.

En fin, estuve ojeando Cairo, y me es un poco molesto lo inflado que esta el programa... podria ser un poco mas liviano, como awn

---

### Post by Darkade on 2008-07-31
> **pol666 said:**
> mmm, estuve usando kde, y me di cuenta que tanto cairo como awn, son pesimo el desempeño en kde, aunque por lo menos cairo andaba, awn ni eso.

En fin, estuve ojeando Cairo, y me es un poco molesto lo inflado que esta el programa... podria ser un poco mas liviano, como awn

intenta con [Kiba]("http://www.kiba-dock.org/") y si no KDE tiene un excelente dock: Kool Dock

---

### Post by pol666 on 2008-07-31
Kiba? sigue existiendo eso?.. .

probe con KXdock pero no lo pude instalar, tambien probe slimdock y nda, me canso un poquito estoy enchufado desde las 2 de la tarde en la pc ya no quiero sabes mas nada ( y sigo estando aca... por favor que vicio)

---

### Post by Darkade on 2008-07-31
> **pol666 said:**
> Kiba? sigue existiendo eso?.. .

probe con KXdock pero no lo pude instalar, tambien probe slimdock y nda, me canso un poquito estoy enchufado desde las 2 de la tarde en la pc ya no quiero sabes mas nada ( y sigo estando aca... por favor que vicio)

Existe y esta activo [http://www.kiba-dock.org/](http://www.kiba-dock.org/)

---

### Post by Hei Ku on 2008-08-01
Proba con kooldock. Tanto AWN, como cairo-dock son para gnome, Kiba esta discontinuado, y Kxdock estaba todavia en beta la ultima vez que mire. Tambien habia un applet de Karamba que hacia de dock, pero no recuerdo el nombre.

---

### Post by pol666 on 2008-08-01
Pude usar la Cairo en KDE, el problema radica en que KDE, convierte lo GTK en KDE nativo.. y ese es el problema, lio desactive en Configurar su computadora/Apariencia/y en la ultima pestaña cambie la opcion de ver como kde, como gtk.

---

