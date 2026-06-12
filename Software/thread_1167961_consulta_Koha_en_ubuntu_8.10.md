---
title: "consulta Koha en ubuntu 8.10"
date: 2009-05-23
forum: Software
---

### Post by Gideon26 on 2009-05-23
Hola como estan queria preguntar si alguien ya tuvo alguna experiencia con koha (software para gestion de bibliotecas, por supuesto es GNU) y concejos a tener en cuenta en el momento de montarlo en un servidor. Cualquier info seria de mucha Ayuda. Gracias.

---

### Post by Gideon26 on 2009-05-24
Hol gente nuevamente consulto  haber si alguien sabe algo al respecto eh instalado el server LDAP y todas las dependencias como para correr koha segun lo relatado en este how to [http://www.blazingmoon.org/guides/k3-on-u810-8.html](http://www.blazingmoon.org/guides/k3-on-u810-8.html)
pero quiero correr koha por mozilla segun el how to (se accede via intranet) [http://127.0.1.1:8080](http://127.0.1.1:8080) y en vez de abrir la pagina me da un archivo en binario. alguien sabe cual es el problema?? y si trato de abrir el OPAC [http://127.0.1.1](http://127.0.1.1) me da este error

por Koha error

The following fatal error has occurred:

Unknown MySQL server host 'http' (1) at /usr/share/koha/lib/C4/Context.pm line 666.
Compilation failed in require at /usr/share/koha/lib/C4/Circulation.pm line 25.
BEGIN failed--compilation aborted at /usr/share/koha/lib/C4/Circulation.pm line 25.
Compilation failed in require at /usr/share/koha/lib/C4/Overdues.pm line 24.
BEGIN failed--compilation aborted at /usr/share/koha/lib/C4/Overdues.pm line 24.
Compilation failed in require at /usr/share/koha/lib/C4/Members.pm line 27.
BEGIN failed--compilation aborted at /usr/share/koha/lib/C4/Members.pm line 27.
Compilation failed in require at /usr/share/koha/lib/C4/Auth.pm line 31.
BEGIN failed--compilation aborted at /usr/share/koha/lib/C4/Auth.pm line 31.
Compilation failed in require at /usr/share/koha/opac/cgi-bin/opac/opac-main.pl line 21.
BEGIN failed--compilation aborted at /usr/share/koha/opac/cgi-bin/opac/opac-main.pl line 21.

cualquier ayuda viene bien gracias.

---

### Post by guillermolisi on 2009-05-24
> **Gideon26 said:**
> Hol gente nuevamente consulto  haber si alguien sabe algo al respecto eh instalado el server LDAP y todas las dependencias como para correr koha segun lo relatado en este how to [http://www.blazingmoon.org/guides/k3-on-u810-8.html](http://www.blazingmoon.org/guides/k3-on-u810-8.html)
pero quiero correr koha por mozilla segun el how to (se accede via intranet) [http://127.0.1.1:8080](http://127.0.1.1:8080) y en vez de abrir la pagina me da un archivo en binario. alguien sabe cual es el problema?? y si trato de abrir el OPAC [http://127.0.1.1](http://127.0.1.1) me da este error

por Koha error

The following fatal error has occurred:

Unknown MySQL server host 'http' (1) at /usr/share/koha/lib/C4/Context.pm line 666.
Compilation failed in require at /usr/share/koha/lib/C4/Circulation.pm line 25.
BEGIN failed--compilation aborted at /usr/share/koha/lib/C4/Circulation.pm line 25.
Compilation failed in require at /usr/share/koha/lib/C4/Overdues.pm line 24.
BEGIN failed--compilation aborted at /usr/share/koha/lib/C4/Overdues.pm line 24.
Compilation failed in require at /usr/share/koha/lib/C4/Members.pm line 27.
BEGIN failed--compilation aborted at /usr/share/koha/lib/C4/Members.pm line 27.
Compilation failed in require at /usr/share/koha/lib/C4/Auth.pm line 31.
BEGIN failed--compilation aborted at /usr/share/koha/lib/C4/Auth.pm line 31.
Compilation failed in require at /usr/share/koha/opac/cgi-bin/opac/opac-main.pl line 21.
BEGIN failed--compilation aborted at /usr/share/koha/opac/cgi-bin/opac/opac-main.pl line 21.

cualquier ayuda viene bien gracias.
La primer line con error pareceria indicar que te falta definir en donde corre el servidor MySQL que brinda servicios a Koha.

Por las dudas, deberias revisar los permisos de acceso a la base de datos que consume Koha porque si no estan adecuadamente habilitados no podres acceder a sus tablas.

Con esto estoy refiriendome no solo a usuario y password sino tambien a grupo, posibilidad de acceder desde otra maquina (una IP distinta de la que posee localhost), etc.

Que contiene ese archivo "context.pm" ? Es un script ?

Posiblemente las lineas siguientes sean consecuencia de la primera.

---

