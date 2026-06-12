---
title: "Algunas preguntas sobre CD de musica"
date: 2009-04-17
forum: Software
---

### Post by WooS on 2009-04-17
Tengo una consulta xq un amigo m presto un cd d musica q esta muy bueno pero se lo tengo q devolver. Quisiera saber si alguien m puede guiar como hacer para pasar los temas a mp3 cosa de quedarmels en la compu y la otra cosa q quiero saber es como hacer para reproducir un cd desde el songbird xq intente d mil maneras y no anda... =S

---

### Post by josecuervo86 on 2009-04-17
Para quemar cd's tenes el **Sound Juicer** que esta en **Aplicaciones > Sonido y video > Extractor de sonido de CD**

Ojo que la opcion por defecto es grabarlo en **.oga**, para cambiarlo anda a **Editar > Preferencias** y abajo de todo tenes la opción de cambiarlo a mp3

---

### Post by Air23 on 2009-04-17
Proba Sound Juicer.
```
sudo apt-get install sound-juicer
```
Luego aparece en: Aplicaciones > Sonido y video > Extractor de sonido de CD

Mas info:

[http://www.guia-ubuntu.org/index.php?title=Sound_Juicer&](http://www.guia-ubuntu.org/index.php?title=Sound_Juicer&)
[http://www.tuxapuntes.com/tux/content/view/602/86/](http://www.tuxapuntes.com/tux/content/view/602/86/)

Edit: no vi que josecuervo86 ya habia respondido

---

### Post by WooS on 2009-04-17
Muchisimas gracias a ambos estoy leyendo al respecto y creo q eso es lo q buscaba...
PD: para no abrir otro post pregunto aca de paso xq desde el frostwire m baje solo un tema para probar q onda y no m anduvo...no se q paso pero ningun reproductor m reconoce q pasa y el celu tmp m puede reproducir ese archivo en mp3
Hay q configurar algo para q baje bien la musica?

---

### Post by josecuervo86 on 2009-04-17
No te reproduce los mp3? tenes que bajar los codecs para poder reproducirlos. Ahora no me acuerdo como se llama el paquete, pero si buscas en google te aparece seguro ;)

Edit: para que no te tomes el laburo me lo tome yo :P. El paquete se llama **ubuntu-restricted-extras**. O sea para instalarlos podes hacerlo desde synaptic o mediante consola con ```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by sajnox on 2009-04-17
> **WooS said:**
>  y la otra cosa q quiero saber es como hacer para reproducir un cd desde el songbird xq intente d mil maneras y no anda... =S

Todavia recuerdo los insultos de mi amigo Mariano por que no puede usar sus cds con Songbird. Si mal no recuerdo songbird no tiene soporte para cds

Saludos

---

### Post by pablo.s on 2009-04-17
Che, que pasó con hacer

[COLOR=Green]**cdparanoia -B**[/COLOR]

y pasarle a cada .wav el
conversor a FLAC, eh?

---

### Post by WooS on 2009-04-18
> **sajnox said:**
> Todavia recuerdo los insultos de mi amigo Mariano por que no puede usar sus cds con Songbird. Si mal no recuerdo songbird no tiene soporte para cds

Saludos

jajaja... me paso algo muy similar a tu amigo por eso hice este post
Ya instale todo...muchas gracias!

---

### Post by leosr on 2009-04-23
> **WooS said:**
> Muchisimas gracias a ambos estoy leyendo al respecto y creo q eso es lo q buscaba...
PD: para no abrir otro post pregunto aca de paso xq desde el frostwire m baje solo un tema para probar q onda y no m anduvo...no se q paso pero ningun reproductor m reconoce q pasa y el celu tmp m puede reproducir ese archivo en mp3
Hay q configurar algo para q baje bien la musica?

Hola. Hay muchos archivos que son fake (falsos), cuando terminás de bajarlo andá a la carpeta que lo contine y desde el mismo Nautilus posá el puntero del mouse sobre el archivo descargado y vas a poder escucharlo. Si no se escucha es porque el archivo no sirve.
Espero que te sirva.

Saludos.

---

### Post by WooS on 2009-04-25
ah muchas gracias...quedat tranqui q todo sirve...saludos!

---

