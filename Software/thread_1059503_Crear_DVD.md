---
title: "Crear DVD"
date: 2009-02-03
forum: Software
---

### Post by h9005 on 2009-02-03
Alguien conoce algun programa para ubuntu que permita crear rapidamente y facil un dvd, que genere automaticamente capitulos con animaciones de fondo y todo?

---

### Post by acdm86 on 2009-02-04
> **h9005 said:**
> Alguien conoce algun programa para ubuntu que permita crear rapidamente y facil un dvd, que genere automaticamente capitulos con animaciones de fondo y todo?

Lo que estas buscando es ManDVD, yo uso DeVeDe, no le podes poner animaciones pero si todo lo demas.

---

### Post by Kabezon on 2009-02-05
Hacer un DVD en GNU/Linux es re lento :S Al menos a mí me demoró HORAS hacer un VCD de hora y media... Fue horrible la espera :S

---

### Post by NickCis on 2009-02-06
> **Kabezon said:**
> Hacer un DVD en GNU/Linux es re lento :S Al menos a mí me demoró HORAS hacer un VCD de hora y media... Fue horrible la espera :S

En windows tampoco es tan rapido,,, cuando tuve que hacer un Dvd con tres peliculas (menu y todo) tardo como 2hs, y eso que mi pc se podria considerar decente (Amd Athlon 3800+, 1Gb ram dual chanel, 512mb Nvidia xfx 7300)...

Saludos.

---

### Post by Kabezon on 2009-02-06
> **NickCis said:**
> En windows tampoco es tan rapido,,, cuando tuve que hacer un Dvd con tres peliculas (menu y todo) tardo como 2hs, y eso que mi pc se podria considerar decente (Amd Athlon 3800+, 1Gb ram dual chanel, 512mb Nvidia xfx 7300)...

Saludos.
2 horas las espero, pero esta cosa demoró tanto que decidí irme a dormir mientras lo hacía :P Y si mi memoria no está flasheando loco, me parece que no te graba el DVD, crea un .iso que después vos grabás :P Por suerte mi reproductor de DVD reproduce de todo, le metés una banana y te la reproduce :P Así que no necesito grabarlo en formato DVD, lo tiro como DVD de datos, con todos los videos dentro, y listo.

---

### Post by EnriqueK on 2009-02-06
Uso Intrepid 64 bits y una vez creé un DVD a partir de varios .avi usando DeVeDe , lindo programa pero al ver que demoraba bastante en formar la ISO del DVD, ejecuto top y me encuentro que solo me funcionaba un núcleo ( tengo Intel core2 duo), posiblemente otro programa haga funcionar ambos núcleos con lo que se agilizaría el proceso.

---

### Post by sajnox on 2009-02-06
La ultima version de devede (creo que no esta en los repositorios de Intrepid) ya tiene una opcion para usar los dos nucleos en vez de uno y hacer que la creacion de la pelicula sea mas rapida, desde aca (1) podes bajar la ultima version en .deb

(1) [http://www.rastersoft.com/programas/devede_es.html#download_section](http://www.rastersoft.com/programas/devede_es.html#download_section)

---

### Post by c4d0rn4 on 2009-02-07
sajnox, te comento que la versión de devede que está en los repositorio de intrepid tiene la función. Solo hay que tildarla en la parte avanzada del menú principal de creación del dvd (esa ventana que te dice cuanto pesa el dvd).

Con respecto a Devede, puedo decir que es de mi absoluto agrado. Solo he tenido alguna que otra escaramuza con el tema del tamaño del output que casi siempre tengo que corregir a 4:3.

Yo para hacer una peli de 3 películas estoy mas o menos 5 horas porque lo hago desde un ubuntu en una maquina virtual. Pero cuando lo ejecuto en una máquina normalmente tardará cuanto mucho 2 horas y media.

En cuanto a que no grabe las imágenes directamente, sí da un poco de paja, pero bueno, son dos clicks más; no es tan grave.

---

### Post by EnriqueK on 2009-02-07
Cuando activo la opción de optimizar múltiples núcleos, noto que la velocidad del proceso es la misma, al parecer esta opción lo que que hace es aliviar la carga al núcleo para repartirla con los dos núcleos, corriendo top se ve que ninguno de ellos llega al 100% , sino que ambos rondan por el 50%, pero de todas maneras está muy bueno por que se evitan calentamientos disparejos.
Además el DeVeDe presenta la peculariedad de de usar la misma versión para todos los Ubuntu , ya sean de 32 o 64 bits , o sea no aprovecha las superiores prestaciones de 64 bits, una lástima por que el programa es muy bueno, simple y directo al grano, como debe ser.
Sería interesante saber de algún creador de DVDs que sea optimizado para su uso en 64 bits.

---

### Post by c4d0rn4 on 2009-02-08
> **EnriqueK said:**
> Cuando activo la opción de optimizar múltiples núcleos, noto que la velocidad del proceso es la misma, al parecer esta opción lo que que hace es aliviar la carga al núcleo para repartirla con los dos núcleos, corriendo top se ve que ninguno de ellos llega al 100% , sino que ambos rondan por el 50%, pero de todas maneras está muy bueno por que se evitan calentamientos disparejos.
Además el DeVeDe presenta la peculariedad de de usar la misma versión para todos los Ubuntu , ya sean de 32 o 64 bits , o sea no aprovecha las superiores prestaciones de 64 bits, una lástima por que el programa es muy bueno, simple y directo al grano, como debe ser.
Sería interesante saber de algún creador de DVDs que sea optimizado para su uso en 64 bits.

perdón si digo una GRAN burrada, pero si te bajás los source con apt y lo compilas, no queda para 64bits?

---

### Post by faktorqm on 2009-02-09
no, sigue usando los enteros de 32 bits. salu2!

---

### Post by tzulberti on 2009-02-09
Por lo que vi bajandome del codigo, devede esta hecho en python asique es interpretado...

---

