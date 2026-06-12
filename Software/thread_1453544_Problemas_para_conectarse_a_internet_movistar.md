---
title: "Problemas para conectarse a internet movistar"
date: 2010-04-11
forum: Software
---

### Post by dieguiño on 2010-04-11
Hola, 
no se si este sea el lugar para preguntar, pero ahí va: hace ya 2 años uso ubuntu y estoy de verdad feliz. siempre me conecté facilmente (automaticamente) a internet con una conección de vanda ancha cableada (vtr) en stgo. Bueno la cosa es q me cambié de casa al centro, donde no hay mas opción q telefonica-movistar. tomé el servicio y no he podido conectarme, es decir el ícono aparece y dice q se ha establecido la conección pero el navegador no abre páginas. En soporte de movistar me dijeron q tenia q cambiar de sistema operativo porq no tenian soporte !!!!! q tal??? el monopolio de telefónica en el sector me ha jodido ....q hago??? alguien me puede ayudar???
Muchas gracias y sorry por la lata.

Dieguiño.

---

### Post by bichopro on 2010-04-13
Salta a a la parte que se hace con consola (pppoeconf) y primero asegurate de borrar las configuraciones que hiciste antes y no te funcionaron.

[http://www.taringa.net/posts/linux/2503756/~~Conectar-Internet-en-Ubuntu~~.html](http://www.taringa.net/posts/linux/2503756/~~Conectar-Internet-en-Ubuntu~~.html)

---

### Post by Matnet on 2010-05-21
> **bichopro said:**
> Salta a a la parte que se hace con consola (pppoeconf) y primero asegurate de borrar las configuraciones que hiciste antes y no te funcionaron.

[http://www.taringa.net/posts/linux/2503756/~~Conectar-Internet-en-Ubuntu~~.html](http://www.taringa.net/posts/linux/2503756/~~Conectar-Internet-en-Ubuntu~~.html)
Luego de las indicaciones de bichopro, anda a Sistema > Configuración > Aplicaciones al Inicio e incluyes una nueva:

Nombre: Internet (o el que quieras, da lo mismo)
Comando: gksudo pon dsl-provider (gksudo es para que te pida la contraseña en un dialogo en vez de un terminal, o que simplemente no funcione; el resto es el comando que aconseja pppoeconf)

Y le das a aceptar. Luego de esto, cada vez que logees va a conectar de la misma manera en que lo habría hecho en un equipo con Windows.

Mucha suerte

---

