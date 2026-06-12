---
title: "leer pdf protegido por clave pki#12"
date: 2008-11-25
forum: Software
---

### Post by kasiko on 2008-11-25
hola,

¿quien me puede decir como leer pdf protegidos con claves pki #12? un ejemplo, ir a esta web [http://j4ckware.blogspot.com/](http://j4ckware.blogspot.com/) y bajar algun fichero en rar que dentro viene un pdf y un fichero de clave.

En windows, sin problemas, pero yo quiero leerlo y verlo desde linux.

¿quien me puede ayudar?

gracias.

---

### Post by juanman on 2008-11-26
Hola kasiko, creo q no te va a quedar otra q instalarte el maligno, privativo y pesado lector de pdf de Adobe: el Acrobat Reader :P

1) Lo bajas desde su web [http://www.adobe.com/support/downloads/product.jsp?product=10&platform=unix](http://www.adobe.com/support/downloads/product.jsp?product=10&platform=unix)
2) Click en Adobe Reader for Unix
3) Seleccionas en Operating System -> Linux
en Installer -> el .deb
en Language -> Spanish
4) Click en Continue y Download Adobe Reader
5) Al .deb q se haya descargado, lo instalas con doble click
6) Una vez q se instale, abris el Adobe Reader.
7) Vas a Documento -> Configuracion de Seguridad (aca te puede saltar un error de q falta una libreria, no le des importancia)
8) Vas a agregar ID -> Buscar un ID Existente -> En nombre de archivo, buscas el .pfx q venia en el zip y en Contraseña, pones la contraseña q estaba en el LEER.txt -> Siguiente -> Finalizar
9) Cerras la ventanita de configuracion de seguridad y ya vas a poder abrir el pdf...

Por ultimo, te recomiendo, si queres programar tambien sobre linux, considerar aprender algun otro lenguaje (Mono es compatible con .NET, la versión 2.0 salió hace poco [http://www.mono-project.com/](http://www.mono-project.com/))

Saludos!

---

### Post by kasiko on 2008-11-26
Muchas gracias !!!

Un saludo.:guitar:

---

