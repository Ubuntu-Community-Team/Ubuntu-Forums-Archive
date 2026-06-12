---
title: "Grub2 me odia."
date: 2010-07-23
forum: Software
---

### Post by Javierkaiser on 2010-07-23
Buenas gente.
Les paso a comentar mi problema.
Para empezar les cuento ke uso dos rigidos configurados en Raid 0, y 4 gb de ram (x ende, ubuntu x64).

Hace un tiempo habia descargado el Kubuntu 9.10 y lo tenia instalado en el sistema, dual boot con win7. Luego cambie los discos (a los actuales, Raid 0) y justo coincidio con la salida del Ubuntu 10.04. 
Bueno, descargue el Kubuntu 10.04 y mientras lo instaladaba (ya llegando al final), error fatal, el Grub no se habia podido instalar. Cuando me fijo en ke parte lo estaba instalando al grub, veo ke estaba instalanadolo en uno de los rigidos y no en la raid (x ende, no iba a poder) y cuando cambie para ke use la raid y segui la instalacion, error de nuevo, y veo ke sigue tratando de instalarlo en el rigido y no en la raid.
Pense ke tal vez estaba mal bajada la version, y me baje el ubuntu 10.04...y sorpresa, me paso lo mismo.

Asike toco instalar el 9.10 (ke me instalo el Grub viejo) y de ahi actualizar el OS. Una vez safa... pero yo ke estoy aprendendiendo y mandando mano a todo, creo ke llevo 5 reinstaladas en menos de 2 semanas...y tener ke actualizar desde la 9.10 tantas veces cansa.

Y tambien me paso algo similar cuando probando, kise instalar el BURG, y tmb me estrelle contra una pared. En ese momento pense ke era x por algun error mio o algo ke se me habia pasado.

Luego cuando kise arreglar la imagen de inicio (playmouth) vi que era un metodo con GRUB2, y ahi me percate ke tenia el Grub viejo.
Trate de instalar el Grub2, y mientras se configuraba me dio para elegir donde instalarlo, y claro, solo aparecian los dos rigidos, y no la Raid.

Asike, como veran, los Grub2 no kieren instalarse en mi Raid. Alguna idea?

---

### Post by alfplayer on 2010-07-24
> **Javierkaiser said:**
> Les paso a comentar mi problema.
Para empezar les cuento ke uso dos rigidos configurados en Raid 0, y 4 gb de ram (x ende, ubuntu x64).

También se puede usar ubuntu/linux de 32 bits con PAE usando 4 GB o más también.

---

### Post by Javierkaiser on 2010-07-27
Gracias x el dato, pero estoy encariñado con el x64 ;)

Y alguna idea del grub caprichoso¿?

---

### Post by Javierkaiser on 2010-08-03
Bueno, gracias a ke los muchachos actualizaron la version del grub a la 1.98-1ubuntu7 el problema de poder instalarlo en la raid se arreglo! 
Ya saben para los ke tengan dramas con las raids, actualizen el grub y sean felices.

Saludos.

---

