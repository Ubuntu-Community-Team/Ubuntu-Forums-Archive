---
title: "[SOLUCIONADO] Coneccion internet: Conflico de CNTLM y banda ancha"
date: 2009-07-28
forum: Software
---

### Post by flakojaime on 2009-07-28
HOla, les cuento.

Tengo un dell Xps1730 funcionando con ubuntu 9.04.
Impecable, nada que decir, de hecho, cada dia me convenzo mas que fue una de las mejores decisiones al cambiarme y ahora voy por cambiar los sistemas en mi casa.

Me sali un poco del tema jejeje.

Bueno, logre configurar un paquete CNTLM para usar un proxy ISA.

Ese proxy esta en mi trabajo y desde alli no tengo ningun problema, me puedo conectar a internet y puedo descargar las acurlizaciones. Lo unico que no pude hacer es configurar el amsn por proxy.

Hasta ahi todo bien.

Ahora mi pregunta es:

El tener instalado  CNTLM me provoca conflictos con una conexion de banda ancha?

Les pregunto ya que cuando llego a casa, desactivo el proxy en Proxy de la red, y en todos lados dejo conexion directa a internet y cuando intento conectar por medio de banda ancha (con todo configurado) no funciona. O sea. no puedo navegar, y no puedo actualizar.

En este momento estoy en mi trabajo, cuando llegue a casa, les pondre el error especifico.



¿provoca conflictos la coneccion de banda ancha con el CNTLM?

Gracias!!:popcorn:

---

### Post by moreback on 2009-07-28
No sé que es ese CNTLM, pero por lo que cuentas tengo la impresión que te hace cambios en la configuración de red y éstos no se pueden usar con Network-Manager.

---

### Post by gmunioz on 2009-07-29
Hola fla...:

Cntlm Authentication Proxy, es un proxy que se debe instalar 

en los ordenadores que se quieren conectar a una red que utiliza

 el isa server.

Actua como el proxy de un proxy.

Una vez configurado queda escuchando en la dirección de loopback

127.0.0.1 por el puerto 3128.

Tratádose de un ordenador portátil, cuando sea necesario conectarse

en otro sitio se requiere cambiar o deshabilitar el proxy del sistema

de todas las aplicaciones y **DESHABILITAR EL DEMONIO CNTLM**para

que no interfiera con el network manager en uso.

---

### Post by flakojaime on 2009-08-06
Bueno. no logre desactivar el CNTLM.

Asi que opte por comprar un router ethernet/wifi Linksys formateado para linux y lo instale depues del modem de telefonica.

Ahora todo bien.

Gracias por todo

---

