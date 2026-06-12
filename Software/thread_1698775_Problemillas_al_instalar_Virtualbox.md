---
title: "Problemillas al instalar Virtualbox"
date: 2011-03-02
forum: Software
---

### Post by dam1977 on 2011-03-02
Me decidí cambiar finalmente mi Ubuntu 10.04 (Andaba todo más que perfecto) por la versión 10.10 en 64 bits (tengo un Dual Core E5200). Mi preocupación es porque al instalar Virtualbox para cargarle un XP que uso para archivos de la oficina, no puedo instalar las Guest Adittions. Las necesito para ajustar el tamaño de la pantalla del XP, para configurar el mouse, etc. Encima no me reconoce los puertos USB 2.0.
Alguién sabrá como hacer? si no puedo corregir esos detalles es un embole manejar el Virtualbox...

---

### Post by granjero on 2011-03-02
instalaste la versión de los repositorios?

instalá la versión de la pagina de Virtualbox

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

la de la página tiene soporte para usb.

salud!

---

### Post by dam1977 on 2011-03-03
Gracias, Granjero! Ahi está la cuestión, no instalé de los repositorios, bajé del sitio oficial de Virtualbox. Eso hice siempre así. Pero esta vez parece que la chingué en algo y no puedo entender qué. Hasta pensé si no tendrá algo que ver la versión para 64 bits. Pero los Guest Adittions que amaba no aparecen por ningún lado. Desinstalo el Vurtualbox por completo y lo vuelvo a instalar? Elimino la MV con el XP que tanto tiempo lleva configurar para que se desenvuelva decentemente? Ser o no ser!!

---

### Post by hectorivand on 2011-03-03
Hola, los additions te los descarga, vos cuando seleccionas la opción, los comienza a descargar? te tendría que salir un aviso.

Para el uso de los USB del host tenes que instalar un complemento.

[http://www.virtualbox.org/manual/ch01.html#intro-installing](http://www.virtualbox.org/manual/ch01.html#intro-installing)

Edit.: no mencionas que versión de VBOX con lo cual asumo que es la 4 y última.

Saludos
Nacho

---

### Post by dam1977 on 2011-03-04
Después de renegar bastante con este tema y probar varias cosas, se me ocurrió iniciar sesión en el viejo Gnome. Oh sorpresa! Me permitió (al iniciar mi VM con XP) instalar las Guest Additions normalmente. El puntero del mouse ya anda tranquilamente desplazandose entre Ubuntu y XP y el tamaño de la pantalla del XP redimendionado como corresponde
Obvio que luego reinicié todo de nuevo a ver como quedaba arrancando con Unity. Bueno: Lo que había configurado quedó OK. Solo que nuevamente en el Menú superior no se puede usar ninguna opción (redimensionar la pantalla, nada). Pero se puede usar perfectamente.
Gracias de nuevo a todos.

---

### Post by dam1977 on 2011-03-04
Evidentemente hay una incompatibiliadad entre Unity y Virtualbox que los chicos de Canonical tendran que analizar cuando venga Unity como gestor de escritorio por defecto en 11.04

---

