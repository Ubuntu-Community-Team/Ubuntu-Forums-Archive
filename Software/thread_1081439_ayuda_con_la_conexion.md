---
title: "ayuda con la conexion"
date: 2009-02-26
forum: Software
---

### Post by Diegos7 on 2009-02-26
hola, les explico...
en mi casa tenemos una conexion inalambrica, la cual funciona perfectamente (de 2 Mb) y el problema es el siguente...
antes los 3 computadores que hay acá ocupabamos windows y compartiamos la conexion mediante el programa NetLimiter 2 pro... hace un par de semanas me cambié a Ubuntu 8.10 y he tratado de encontrar un programa para dividir la conexion equitativamente sin lograrlo... ayudenme porfavor ya que acá me estan armando demasiados problemas (ni se imaginan las peleas que he tenido jajaja)
ojala puedan ayudarme...
muchas gracias!!

---

### Post by hictio on 2009-02-26
Pero, por aclarar, la máquina que tiene 8.10 es la que está funcionando como gateway de ese enlace, verdad?

Es decir, tiene dos tarjetas de red, y está entre tu red interna y el modem del ISP.

---

### Post by Diegos7 on 2009-02-26
no, es un pc con windows el gateway... yo me conecto a través de wifi

---

### Post by hictio on 2009-02-26
No te entiendo, perdoname.

El gateway es una máquina Windows con el NetLimiter 2 pro instalado y controlando y distribuyendo el ancho de banda de tu conexión, es así?

Vos lo que querés es que tu laptop Ubuntu no se robe todo el ancho de banda porque al conectarse por el WiFi, el NetLimiter 2 pro no le puede aplicar los límites?

---

### Post by Diegos7 on 2009-03-02
mira...
utilizabamos el netlimiter 2 en cada maquina... asi configurabamos cada una de ellas con el ancho de banda equitativo correspondiente a los 2mb dividido en 3 maquinas.
ahora solo funciona en 2 maquinas (ambas con windows) y yo no puedo limitar mi notebook robandome asi casi toda la conexion, produciendoles lag a los otros pc's...

---

### Post by hictio on 2009-03-02
Entiendo... Yo nunca lo hice para una máquina en particular, sino para una red.
Fiajte este link, si te sirve: [Use bandwidth shapers (wondershaper or trickle) to limit internet connection speed](http://www.ubuntugeek.com/use-bandwidth-shapers-wondershaper-or-trickle-to-limit-internet-connection-speed.html)

Es una solución para aplicar en tu propia máquina Ubuntu.
La otra cosa que podés hacer, para limitar el uso del ancho de banda en tu máquina Ubntu, es ponerle un límite a los downloads, antes de empezarlos, para que no se robe toda la conexión.

Por ejemplo, asi:
```

wget --limit-rate=20k http://algun.dominio.net/archivo.algo ENTER

```

Donde tenés que tipear eso en un Terminal para limitar el download de 'archivo.algo' para que sólo use 20 Kb/s, pero funciona con archivos que son grandes, más de 1 MB.

---

