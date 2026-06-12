---
title: "PHP y SSH"
date: 2009-09-13
forum: Software
---

### Post by z37a on 2009-09-13
Gente ando buscando algun script php que me permita utilizar ssh via web. Se que esto es medio extraño y que es mas programacion tal vez, pero el tema es que buscando solo me encontre con uno que solo permite ssh v1, y uso ssh v2. Mi idea es agregar a mi sitio de intranet una sccion que me permita ingresar a mi server hogareño y de alli manejarlo via ssh y manejar las PCs de mi red(je ya hasta logre ponerle una funcion de wake on lan y prendo las pcs via intranet por internet!!!). Bueno mas que nada queria saber si alguno probo o uso algun script para dicha tarea, si me puede rcomendar algo, o por donde buscar(no salgan con google che! que ya busque y la verdad solo me encontre con este que permite usar v1, anda de 10, pero necesito ssh version 2).

---

### Post by guillermolisi on 2009-09-13
No vi el script (tampoco lo busque) asi que no tengo una idea concreta de como trabaja, pero imagino (y puedo estar infinitamente equivocado) que el script debe utilizar SSH llamando a las rutinas/librerias/scripts de SSH.

Si esto es asi, con reemplazar las que correspondan (mas sus parametros/opciones) deberia alcanzar para lograr lo que estas buscando. Claro, esto es una idea, hay que hacer el resto del laburo para verificar que funcione correctamente, pero por algun lado se empieza, cierto ?

---

### Post by pablo.s on 2009-09-13
[Acá hay uno]("http://www.rutschle.net/tech/sslh.shtml") que es en Perl.
No se si te será de utilidad.

---

### Post by marianom on 2009-09-13
Y no, no te contesto lo que vos querés :) pero te tiro una opción:
 hace un tiempo postee [un script]("https://lists.ubuntu.com/archives/ubuntu-ar/2008-November/014265.html") de acceso a equipos por ssh con paramiko (python) en la lista de ubuntu-ar, capaz que te sirve

---

### Post by z37a on 2009-09-14
Muchisimas grracias gente voy a ver un poco por esos lados a ver que onda, igual les comento que no soy programador y que mas que nada lo que hago es buscar codigo ver como funca y modificarlo un poco para lo que necesito.

PD: Siguiendo la filosofia el que lo quiera que me lo pida se lo envio, hasta ahora logre armar una web con marcos utilizando autentificacion por mysql con clave encriptada, con scripts para iniciar las pcs de la red y algunas cosillas mas sencillas.

---

### Post by oktubrer on 2009-09-14
> **z37a said:**
> Muchisimas grracias gente voy a ver un poco por esos lados a ver que onda, igual les comento que no soy programador y que mas que nada lo que hago es buscar codigo ver como funca y modificarlo un poco para lo que necesito.

Eso en mi barrio se llama "maximizar la reutilización de código" y es lo que hacen los programadores. :P

---

### Post by z37a on 2009-09-16
> **oktubrer said:**
> Eso en mi barrio se llama "maximizar la reutilización de código" y es lo que hacen los programadores. :P

Perdon el OFF: En mi barrio se llama ser un zoquete programando que no tengo ni idea de como realizar un codigo de 0!!!!! Jajaja, pero bueno hago lo que puedo!!!!!

---

### Post by juank47 on 2010-03-24
Saludos, soy estudiante de un Fp de informatica y como proyecto integrado estoy haciendo una pagina en php con conexciones en ssh para abrir otros pc con sesiones y estoy muy interesado en tu codigo para mejorar mi estructura, si puedes contactar conmigo mi correo es [email]zark_patriota_29740@hotmail.com[/email], un placer, y gracias de antemano

---

### Post by z37a on 2010-03-24
> **juank47 said:**
> Saludos, soy estudiante de un Fp de informatica y como proyecto integrado estoy haciendo una pagina en php con conexciones en ssh para abrir otros pc con sesiones y estoy muy interesado en tu codigo para mejorar mi estructura, si puedes contactar conmigo mi correo es [email]zark_patriota_29740@hotmail.com[/email], un placer, y gracias de antemano

La verdad que con esto nunca llegue a nada, lo deje colgado. El código que encontre lo encontré googleando y no me funciono para nada.

Lo que te puedo pasar si queres es mi sitio de inranet que voy de a poco haciendo(aunque hace meses no lo toco). En el mismo lo mas interesante es el sistema de WOL que integre al php, tal vez te sirva, ya que de esa manera entras a un sitio y encendes las PCs, luego cuand o logres eso del ssh podes también ingresar a la PC evitando el problema de tener una PC apagada y que por eso no puedas acceder!!!!

---

### Post by juank47 on 2010-04-05
Muchas gracias, amigo, podria echarle un vistazo a eso del Wol de tu intranet si, me parece ademas bastante interesante... estamos en contacto mi correo es [email]zark_patriota_29740@hotmail.com[/email], un abrazo

---

### Post by z37a on 2010-04-05
Así lo descarga el que quiera:

[http://rapidshare.com/files/372458515/Intranet-0.4.tar.gz.html](http://rapidshare.com/files/372458515/Intranet-0.4.tar.gz.html)

Si saben donde lo pueda subir para que otros lo descarguen y puedan colaborar genial, igualmente comento que es un compilado de tutoriales en php que dio resultado esto, por lo cual puede(y de seguro lo es) ser un desastre y una desproligidad total, así que ni hace falta lo mencionen! Aunque pueden hacerlo.

---

