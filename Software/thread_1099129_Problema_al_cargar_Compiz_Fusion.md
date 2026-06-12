---
title: "Problema al cargar Compiz Fusion"
date: 2009-03-17
forum: Software
---

### Post by JUTGtgRB7z on 2009-03-17
Hola a todos de nuevo, perdón por molestar con tantas preguntas. Espero que sepan entender que soy novato y hay mucho por aprender. 
Vamos al problema. Tengo instalado Compiz Fusion y Emerald, y Compiz Fusion Icon que inicia automáticamente al iniciar la sesión. El problema que tengo, es que al iniciar la sesión abre Fusion Icon pero no carga Compiz, solo lo hace una vez que pongo "Reload window manager". De lo contrario funciona con Metacity ¿Cómo lo puedo solucionar o a qué creen que se deba?

---

### Post by staar on 2009-03-18
Fijate si en Sistema -> Preferencias -> Apariencia -> Efectos visuales, tenés activados los efectos...

sino es eso, con agregar en Sistema -> Preferencias -> Sesiones, una entrada que carge compiz (el comando es "compiz --replace", sin las comillas) al inicio...

saludos

---

### Post by JUTGtgRB7z on 2009-03-24
> **staar said:**
> Fijate si en Sistema -> Preferencias -> Apariencia -> Efectos visuales, tenés activados los efectos...

sino es eso, con agregar en Sistema -> Preferencias -> Sesiones, una entrada que carge compiz (el comando es "compiz --replace", sin las comillas) al inicio...

saludos

Si los tenía activados pero nada :( por suerte haciendo lo que me pusiste ahí si funcionó :D Gracias.

---

### Post by infernus92 on 2009-03-25
si lo que no te funciona es el compiz-config-settings-manager, hay un paquete para descargar que lo simplifica muchisimo... no me acuerdo como se llama... pero pone compiz en la barra de buscar en synaptic y creo que empieza con s el nombre... en la descripcion dice algo de simple compiz-config-settings-manager

saludos

---

### Post by Aseck on 2009-04-29
Hola que tal la verdad soy nuevo en ubuntu y me he topado con muchos problemas quisiera que me ayudaran el problema por el momento es que no me carga compiz al iniciar sesion tengo que darle en compiz fusion icon reload windows manager ya intente las anteriores soluciones y nada:( Gracias.

---

### Post by jrrpnani on 2009-06-18
> **infernus92 said:**
> si lo que no te funciona es el compiz-config-settings-manager, hay un paquete para descargar que lo simplifica muchisimo... no me acuerdo como se llama... pero pone compiz en la barra de buscar en synaptic y creo que empieza con s el nombre... en la descripcion dice algo de simple compiz-config-settings-manager

saludos

Lo que dice infernus-92 es el paquete simple-ccsm. Lo instalas, luego vas a 
Sistema -> Preferencias -> Apariencia -> Efectos visuales y debería aparecerte 'personalizado'. Si no hay ninguno seleccionado marcas uno, y te preguntara si mantener la configuración anterior o la nueva. Le dices que la nueva, y ya funciona al iniciar sesion.

Un saludo

---

