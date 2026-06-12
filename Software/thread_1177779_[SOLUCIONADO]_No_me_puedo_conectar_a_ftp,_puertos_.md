---
title: "[SOLUCIONADO] No me puedo conectar a ftp, puertos cerrados?"
date: 2009-06-03
forum: Software
---

### Post by Rago on 2009-06-03
Hola a todos,

Tengo Ubuntu Intrepid y no puedo conectarme a los ftp que uso, intente con los clientes gFTP y Filezilla sin exito.

Probe con mi otro S.O.(win xp) y me conecta perfecto.

Tengo un router con los purtos abiertos, por ende no creo que el problema este ahi(ya que no podria conectarme por win). Asi que supongo que debe ser mi ubuntu.

He buscado en internet y la verdad no encuentro la solucion, lei algo sobre iptables pero no se que debo hacer. ¿Podrian ayudarme?

De ante mano muchas gracias.

---

### Post by Rago on 2009-06-03
> **Rago said:**
> Hola a todos,

Tengo Ubuntu Intrepid y no puedo conectarme a los ftp que uso, intente con los clientes gFTP y Filezilla sin exito.

Probe con mi otro S.O.(win xp) y me conecta perfecto.

Tengo un router con los purtos abiertos, por ende no creo que el problema este ahi(ya que no podria conectarme por win). Asi que supongo que debe ser mi ubuntu.

He buscado en internet y la verdad no encuentro la solucion, lei algo sobre iptables pero no se que debo hacer. ¿Podrian ayudarme?

De ante mano muchas gracias.

Lo consegui =D
Efectivamente era que en el iptables estaban bloqueados los puertos FTP, asi que instale Firestarter y abri los puertos que necesitaba. Por lo que lei en la guia que segui sirve tambien para poder usar clientes p2p, quizas a alguien le ayude, saludos =)

---

### Post by Patriciologico on 2009-06-04
Como complemento, Ubuntu ahora viene con ufw como cortafuegos, y se puede instalar gufw para manejarlo graficamente.

Saludos!

---

### Post by guillermolisi on 2009-06-04
> **Patriciologico said:**
> Como complemento, Ubuntu ahora viene con ufw como cortafuegos, y se puede instalar gufw para manejarlo graficamente.

Saludos!
Una aclaracion.

Frecuentemente se confunde a una interfaz para administrar el cortafuegos como si fuera el cortafuegos mismo.

El cortafuegos de Ubuntu, como en el resto de las distribuciones Linux, esta incluido en el kernel, el nucelo del sistema operativo.

Firestarter, UFW, gUFW, Shorewall, eBox, FIrewallBuilder, etc. son interfaces que permiten una forma amigable de definir las reglas para iptables y no tener que lidiar con sus primitivas.

Tambien es frecuente ver preguntas sobre como activar o desactivar el cortafuegos. El mismo esta siempre activo, por ser parte del kernel, pero son sus reglas las que hacen que trabaje de una u otra forma, siendo mas permisivo o mas "paranoico" (si me permiten el termino).

Por defecto, el cortafuegos permite la salida de toda comunicacion y solo permite la entrada siempre que exista en la PC un programa que este "escuchando" en un port de TCP/IP, caso de un servidor web, uno de e-mail (smtp por ejemplo), etc.

Cuando navegamos la web, es el navegador que "escucha" en el port 80 y permite que la comunicacion con los sitios visitados sea posible en ambos sentidos.

Es decir, si no tenemos programas "escuchando" en algun port TCP/IP, el cortafuegos no permitira el ingreso de paquetes de red (ni siquiera mostrara los ports como cerrados).

---

### Post by Carlos C on 2009-06-04
Buenísimo Guillermo, gracias por la aclaración.
Saludos!

---

### Post by radixs on 2009-06-04
> **guillermolisi said:**
> Una aclaracion.

Frecuentemente se confunde a una interfaz para administrar el cortafuegos como si fuera el cortafuegos mismo.

El cortafuegos de Ubuntu, como en el resto de las distribuciones Linux, esta incluido en el kernel, el nucelo del sistema operativo.

Firestarter, UFW, gUFW, Shorewall, eBox, FIrewallBuilder, etc. son interfaces que permiten una forma amigable de definir las reglas para iptables y no tener que lidiar con sus primitivas.

Tambien es frecuente ver preguntas sobre como activar o desactivar el cortafuegos. El mismo esta siempre activo, por ser parte del kernel, pero son sus reglas las que hacen que trabaje de una u otra forma, siendo mas permisivo o mas "paranoico" (si me permiten el termino).

Por defecto, el cortafuegos permite la salida de toda comunicacion y solo permite la entrada siempre que exista en la PC un programa que este "escuchando" en un port de TCP/IP, caso de un servidor web, uno de e-mail (smtp por ejemplo), etc.

Cuando navegamos la web, es el navegador que "escucha" en el port 80 y permite que la comunicacion con los sitios visitados sea posible en ambos sentidos.

Es decir, si no tenemos programas "escuchando" en algun port TCP/IP, el cortafuegos no permitira el ingreso de paquetes de red (ni siquiera mostrara los ports como cerrados).

Wow... muchas gracias... el que no entiende que lo lea de nuevo xD

Gracias nuevamente.

---

### Post by Carlos C on 2009-06-29
[Post de la semana]("http://ubuntuforums.org/showthread.php?t=1176055"): [29 de junio de 2009]("http://ubuntucl.wordpress.com/2009/06/29/aclaracion-el-cortafuegos-no-es-la-interfaz-con-que-se-administra/").

---

