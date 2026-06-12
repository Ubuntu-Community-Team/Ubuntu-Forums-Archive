---
title: "Habiltar Perl en Apache2"
date: 2008-12-30
forum: Software
---

### Post by rodolfojavier1982 on 2008-12-30
Bueno aca yo de nuevo...:(
El tema es que quiero ejecutar programas Perl sobre el navegador.
Aclaro soy super principiante, pero quiero aprender...
Tengo configurado Apache2, MySQL y PHP (pude meter codigo PHP en codigo HTML y funciona), el tema es que quiero hacer una mini aplicacion que imprima algo en un navegador utilizando el lenguaje Perl.
Tengo este codigo

#!/usr/bin/perl 

print "content-type: text/html \n\n";

print "Bienvenidos a mi script, si vemos este mensaje es porque funciona todo perfecto\n";

exit(1);

Al ejecutarlo en una consola con 
$perl ejemploPerl.pl

Me aparece en la consola (y no en el navegador)

  content-type: text/html 

  Bienvenidos a mi script, si vemos este mensaje es porque funciona todo  perfecto

Averigue en internet y vi que necesitaba un modulo para perl
    libapache2-mod-perl2
Lo instale, tambien modifique el archivo de configuracion de Apache, como decia en ese mismo sitio.
Agregue al final del archivo apache2.conf las sig lineas...

AddHandler cgi-script .cgi
<Files ~ &#8220;\.pl$&#8221;>
    Options +ExecCGI
</Files>
<Files ~ &#8220;\.cgi$&#8221;>
    Options +ExecCGI
</Files>

Reinicie el Servidor Apache con 
    $sudo /etc/init.d/apache2 restart

Luego intente ejecutar el archivo ejemploPerl.pl y me aparecio en la consola, como antes....
Estoy omitiendo algo?? 

Espero que alguien me ayude.
Desde ya, gracias por la atención.

---

