---
title: "Kernel 2.6.28-11 vs 2.6.28-14"
date: 2009-08-09
forum: Software
---

### Post by Sanctus119 on 2009-08-09
Hola, tengo el siguiente problema.

Tengo una instalación de Linux Mint 7 equivalente a Ubuntu 9.04 (para los que no saben, Linux Mint es un Ubuntu con codecs pre-instalados y algunas utilidades y temas de escritorio extra, pero en el fondo sigue siendo Ubuntu)

Al momento de la instalación venía con el Kernel Linux 2.6.28-11, que no me daba ningún problema. Sin embargo, en una tarde dejé Synaptic actualizando todos los  componentes del equipo y a la vuelta  me encontré  con el Kernel Linux 2.6.28-14 instalado de manera paralela. Lo lógico habría sido eliminar el kernel antiguo una vez que funcionó el nuevo. Sin embargo, ingresé  con el nuevo kernel y me da ciertos errores, especialmente con el software RutilT (no me detecta el dispositivo ra0). Como dije, con el kernel antiguo no me daba problemas, asi que es con el que sigo iniciando normalmente. 

Lo natural sería desinstalar el nuevo kernel, sin embargo, cuando intento realizar la operación en Synaptic, sucede esto.

- Marco para desinstalar "linux-image-2.6.28-14-generic" y  se me marcan automáticamente para eliminarse: "linux-generic", "linux-image-generic", linux-restricted-modules-2.6.28-14-generic" y "linux-restricted-modules-generic"

- Marco para  desinstalar "linux-headers-2.6.28-14-generic" y se me marca automaticamente "linux-headers-generic"

- Marco para desinstalar  "linux-headers-2.6.28-14" y se me marcan para eliminar automaticamente los dos anteriores.


Quiero saber si es seguro realizar esta operación, ya que varios de los paquetes que se están auto-eliminando se actualizaron inmediatamente y no tienen una "versión 2.6.28-11" que quede después de la desinstalación de las versiones más actualizadas. (paquetes en esta situación: "linux-generic", "linux-image-generic",  "linux-restricted-modules-generic",  "linux-headers-generic")

---

### Post by aledruetta on 2009-08-10
¿Por qué simplemente no booteás con el kenel anterior y esperás un tiempo a ver si los problemas con el nuevo kernel se solucionan? Quizá en unos días esas aplicaciones se actualizan y se acomodan al nuevo kernel.

---

### Post by Sanctus119 on 2009-08-11
> **aledruetta said:**
> ¿Por qué simplemente no booteás con el kenel anterior y esperás un tiempo a ver si los problemas con el nuevo kernel se solucionan? Quizá en unos días esas aplicaciones se actualizan y se acomodan al nuevo kernel.

Estoy booteando con el kernel antiguo sin problemas, pero mi partición de linux es pequeña y quiero liberar esos más de 100mbs que está usando el nuevo kernel que no utilizo.

Por otro lado, es dificil que actualicen RutilT para el nuevo kernel; es un software en desarrollo, de muy lenta actualización y además muy específico para usuarios con problemas con chips ralink

---

### Post by moreback on 2009-08-13
Esos paquetes se te marcan para desinstalación por que son genéricos y siempre dependen del último que esté disponible y el cual siempre es una actualización de seguridad.

Creo que lo que quieres hacer con Synaptic se hace desde el menú **Paquete -> Forzar versión...** con el paquete **linux-generic** seleccionado. En el diálogo se puede escoger la versión que quieres dejar.

Saludos.

---

