---
title: "borre todo mi /home/ como lo recupero"
date: 2009-06-18
forum: Software
---

### Post by Barasuishou on 2009-06-18
Bueno en un q******o de mover archivos terminé moviendo demás y quise borrar lo extra pero me borró todo el /home/, hay manera de recuperarlo?, sino estoy frito, ahí tenía todo lo de la facu, música, fotos, etc x_x

espero haya manera de recuperar, chau

edit: perdón me corrigo, por lo que vi mis archivos siguen presentes en la carpeta a donde se habían movido por equivocación, podría volver a ponerlos donde van?

---

### Post by guillermolisi on 2009-06-18
> **Barasuishou said:**
> Bueno en un q******o de mover archivos terminé moviendo demás y quise borrar lo extra pero me borró todo el /home/, hay manera de recuperarlo?, sino estoy frito, ahí tenía todo lo de la facu, música, fotos, etc x_x

espero haya manera de recuperar, chau

edit: perdón me corrigo, por lo que vi mis archivos siguen presentes en la carpeta a donde se habían movido por equivocación, podría volver a ponerlos donde van?
Si, los tenes que volver a mover, tal como hiciste antes pero con muchisimo cuidado. Esta es tu oportunidad de redimirte ante la "locura de hacer orden" :)

En todo caso pasa detalles de donde estan ubicados asi te orientamos en como y donde dejarlos, si es que tenes alguna duda al respecto.

---

### Post by Barasuishou on 2009-06-18
pido mil disculpas por el desorden de mis threads, voy a tratar de ubicarlos bien para la proxima, 

pasando a lo siguiente si la verdad me vendría bien algo de ayuda en esto, los comandos que use previamente fueron:

sudo cp -r * /home/usuario/Downloads/lms4 /usr/local/games/doom3
esto me copió todo a ese lugar, entonces quise borrar las cosas de ahí, moviendome usando cd hasta la carpeta doom3 y ahí hize esto

sudo rm -r /home/
y ahí voló mi home

use el -r y el * por que así había entendido era para mover carpetas con su contenido, por que según sabía el cp, o mv, o rm, eran para mover archivos individuales y yo quería mover la carpeta lms4 completa pero no sabía como XS

---

### Post by WanderingKnight on 2009-06-18
> sudo rm -r /home/

Mmm, no lo veo con muchas esperanzas... si usabas ext3, es prácticamente imposible recuperarlo.

> 
use el -r y el * por que así había entendido era para mover carpetas con su contenido, por que según sabía el cp, o mv, o rm, eran para mover archivos individuales y yo quería mover la carpeta lms4 completa pero no sabía como XS

```
mv /path/al/directorio/fuente /path/al/directorio/destino
```

Con eso basta... pero me parece un poco tarde.

rm es para borrar archivos.

---

### Post by Barasuishou on 2009-06-18
uuu, como dicen acá arriba tampoco está el directorio usr, me fije con el live cd, dios me quiero matarrrrrrrr, tengo que reformatear, re configurar sin contar toda la info que perdí bueno esperaré un rato a ver si alguien me tiene una solución sinó me dispondré a formatear

gracias por todo x_x

---

### Post by guillermolisi on 2009-06-18
> **Barasuishou said:**
> uuu, como dicen acá arriba tampoco está el directorio usr, me fije con el live cd, dios me quiero matarrrrrrrr, tengo que reformatear, re configurar sin contar toda la info que perdí bueno esperaré un rato a ver si alguien me tiene una solución sinó me dispondré a formatear

gracias por todo x_x
Antes habias dicho que tenias los archivos del /home en algun lugar.

Si esto es asi hay posibilidad de normalizar el asunto.
Si no es asi, morde un palito bien fuerte y empeza una instalacion desde cero.

A golpes se hacen los hombres, dijo una madre :)

---

