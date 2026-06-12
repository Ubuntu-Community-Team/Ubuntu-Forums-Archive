---
title: "Problema al usar gestor de actualizaciones"
date: 2010-06-08
forum: Software
---

### Post by dam1977 on 2010-06-08
Estaba usando el gestor de actualizaciones y apareció lo siguiente:

E: No se pudo bloquear /var/cache/apt/archives/lock - open (11: Recurso temporalmente no disponible)
E: No se ha podido bloquear el directorio de descargas

Por consiguiente, no actualizó nada.
Si alguien tiene alguna idea...:confused:

---

### Post by Mister X on 2010-06-08
muy probablemente tenias abierto algun programa para instalar paquetes (synaptic, aptitude, etc) estos necesitan acceso exclusivo a la base de datos y por eso podes usar solo uno a la vez

---

### Post by leonardomdq on 2010-06-08
Probablemente es como dice Mister X tenias usando synaptic o algun otro. Si no es asi proba desde la consola con **sudo aptitude update** .

---

### Post by dam1977 on 2010-06-09
Gracias por atenderme! Prometo la próxima vez ser un poco más paciente! No tengo idea de qué pasó, pero se arregló solo. No tenía nada abierto. Tengo la impresión de que mi viejo disco está haciéndome trastadas!! (puede ser?) Al tercer intento descargó e instaló todas las actualizaciones.

---

