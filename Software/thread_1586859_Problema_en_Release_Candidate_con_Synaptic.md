---
title: "Problema en Release Candidate con Synaptic"
date: 2010-10-02
forum: Software
---

### Post by ketzelleshelle on 2010-10-02
Instalé la release candidate de Maverick.
Quise instalar wakoopa, para lo cuál agregué el repositorio correspondiente y me salió este error:

[B]No se ha podido inicializar la información de los paquetes

Ha ocurrido un problema imposible de corregir cuando se inicializaba la información de los paquetes.

Por favor, informe de ésto como un fallo en el paquete «update-manager» e incluya el siguiente mensaje de error:

'E:Línea 59 mal formada en lista de fuentes /etc/apt/sources.list (análisis de dist)'[/B]

Ahora cada vez que abro synaptic, me sale este aviso y no me deja hacer nada.
Alguna sugerencia o ayuda?

Gracias!

---

### Post by alfplayer on 2010-10-02
> **ketzelleshelle said:**
> 'E:Línea 59 mal formada en lista de fuentes /etc/apt/sources.list (análisis de dist)'[/B]

Se puede probar editando y corrigiendo ese archivo.

---

### Post by juancarlospaco on 2010-10-03
Agregar un " # " al comienzo del renglon 59 de /etc/apt/sources.list 

Probar de nuevo...

---

