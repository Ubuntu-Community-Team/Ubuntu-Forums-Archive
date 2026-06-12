---
title: "Al reiniciar Ubuntu desaparecen efectos Compiz"
date: 2009-09-06
forum: Software
---

### Post by nigromantevader on 2009-09-06
Hola a todos!!!

Les cuento que estoy probando este hermoso sistema operativo (Ubuntu 8.04) :D y despues de buscar algunas algunas guias en foros y demas estoy tuneando el lado grafico de este SO(Sistema Operativo). :cool:

Ahora bien he instalado el Compiz-Fusion y despues de usar y configurar todas las opciones (Que me van de maravilla) al reiniciar el sistema operativo, observo que todos los efectos desaparecen. Investigando un poco veo lo siguiente:
+ Cada vez que reinicio el SO voy Sistema>Preferencias>Apariencia >Efectos Visuales y observo que esta tildado por defecto Ninguno. (Cuando apago el sistema esta en Extra).
+ Esto trae como consecuencia que al activar Extra se me destilden las opciones que tengo en compiz y tenga que tildarlas nuevamente.

E aqui la pregunta (Y busque en google pero no encontre nada) ¿Como logro para que por defecto el sistema se cargue con la opcion de Efectos Visuales Extra.?

Agrego que tengo una Nvidia 8500 con el control privativo marcado y me anda perfecto!!!

Saludos!!!

---

### Post by Cajuma on 2009-09-07
Hola:
Estas usando compiz con GTK o con Emerald 
como decorador de ventanas ?, pues a mi con 
GTK me sucedía lo mismo y con Emerald corre
excelente, también tengo Nvidia.
Chequea por ese lado, y si no vemos.
Saludos. :)

---

### Post by staar on 2009-09-07
y si usas el Administrador de Opciones de CompizConfig (ccsm) para seleccionar los efectos que pasa?

saludos

---

### Post by nigromantevader on 2009-09-07
> **Cajuma said:**
> Hola:
Estas usando compiz con GTK o con Emerald 
como decorador de ventanas ?, pues a mi con 
GTK me sucedía lo mismo y con Emerald corre
excelente, también tengo Nvidia.
Chequea por ese lado, y si no vemos.
Saludos. :)

Graicas por responer !!! Te comento que lo estoy usando con Emerald!!! Algun dato mas???

> y si usas el Administrador de Opciones de CompizConfig (ccsm) para seleccionar los efectos que pasa? 

Estoy usando el ccsm para configurar los efectos(Que en el menu me figura como Configuacion avanzada de los los efectos de escritorio) Un dato que es importante. Al cargar ubuntu las opciones aparecen tildadas (osea que los guarda) pero el tema esta en que en Sistema>Apariencia>Efectos Visuales aparece los efectos configuarados como ninguno.

---

### Post by staar on 2009-09-07
y si en Sistema > Apariencia > Efectos Visuales seleccionás personalizado?

saludos

---

### Post by santiagoward2000 on 2009-09-07
> **staar said:**
> y si en Sistema > Apariencia > Efectos Visuales seleccionás personalizado?

saludos

Por las dudas aclaro que para que aparezca la opción **Personalizado** hay que instalar el paquete **simple-ccsm**.
Saludos!

_EDIT:_
¿Y si instalás **fusion-icon** y lo agregás a los programas que se abren al inicio?

---

### Post by Cajuma on 2009-09-07
Cierto, se me habia pasado por alto, fusion Icon y configuré Compiz y Emerald
desde el inicio.
Gracias, vecino.

---

### Post by nigromantevader on 2009-09-07
Bueno señores parece que ya encontre la solucion!!!!

Igual gracias por todos los aportes!!!!

Lo que hice fue ir a Preferencias>>Sessiones

Y Agregue un envento que se llama Iniciar Compiz(el nombre lo puse yo)

Y en comando escribo Compiz --replace

Y listo ya me ejecuta el compiz correctamente!!!

Saludos!!!

---

### Post by santiagoward2000 on 2009-09-07
> **Cajuma said:**
> Cierto, se me habia pasado por alto, fusion Icon y configuré Compiz y Emerald
desde el inicio.
Gracias, vecino.

Uh! No había visto que había gente de por acá.
De nada, saludos!

---

