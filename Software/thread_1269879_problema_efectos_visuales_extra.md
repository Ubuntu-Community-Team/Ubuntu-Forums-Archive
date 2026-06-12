---
title: "problema efectos visuales extra"
date: 2009-09-18
forum: Software
---

### Post by warkan on 2009-09-18
hola a todos 

bueno soy nuevo en ubuntu instale el 9.04 y en general no e tenido problemas asta ayer
lo q paso es q tenia actibados los efectos visuales y todo vien pero hoy prendo mi pc y sorpresa desapàrecieron los controles de las ventanas (- ^ X)  cuando abro una ventana de consola esta queda en blanco y cuando quiero configurar algo la ventana q pide la contraseña de root tambien queda en blanco.Los efectos estaban funcionando vien asta hoy, le quito los efectos y todo buelve a la normalidad pero no entiendo q es lo q paso.

si me pudiesen ayudar se los agradeseria de ante mano muchas gracias

---

### Post by Carlos C on 2009-09-19
Parece que tienes un problema con el decorador de ventanas. Prueba escribiendo en el terminal:
```
metacity --replace
```

Movido a "Software".
Saludos.

---

### Post by warkan on 2009-09-19
di esa instruccion en una consola pero no hiso nada todo sigue =

metacity --replace

---

### Post by moreback on 2009-09-19
¿Tarjeta de video Intel en blacklist de Compiz?

---

### Post by warkan on 2009-09-20
tengo una geforce4mx no se si ese sera el problema pero lo raro es q ase poco todo me funcionaba sin problemas asta q actualiso no se q cosa.

---

### Post by moreback on 2009-09-20
¿Actualización de kernel?

---

### Post by Carlos C on 2009-09-21
Verifica que el decorador de ventanas esté activado en la configuración de compiz.

Saludos.

---

