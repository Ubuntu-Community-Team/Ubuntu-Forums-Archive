---
title: "XAMPP - Error con el archivo My.cnf"
date: 2009-09-10
forum: Software
---

### Post by bruno_vgg_5 on 2009-09-10
Hola a todos:este es mi 1º post ya q soy nuevo en ubuntu..
Tengo un prolema, he instalado el xampp y funciona todo bien, lso servicios inician correctamente, salbo un error que es el sgte:

uan vez que desde la terminar pongo 
sudo /opt/lampp/lampp start 

arrancan todos los servivios , pero da este error :

Warning: *World*-*writable* config file '/opt/*lampp*/etc/*my*.*cnf*' is ignored 

Funciona todo bien, pero no me permite abrir el phpMyAdmin.

Ya lo inmstalè y lo desinstale como 15 veces jaja

Necesito una ayuda con esto gente, desde ya gracias.

---

### Post by marianom on 2009-09-10
Eso quiere decir que cualquier persona tiene acceso de escritura a tu archivo my.cnf (que si la memoria no me falla es el de configuracion de mysql). Cuando digo cualquier persona, quiere decir cualquiera que pueda conseguir acceso a ese archivo sin necesidad de darte un palo por la cabeza y loguearse en tu lugar (ergo: rw-rw-rw)
Tenés que cambiarles los permisos, e.g.:

```
chmod 644 /opt/lampp/etc/my.cnf
```

---

### Post by bruno_vgg_5 on 2009-09-11
Pero muchisimas gracias [Mariano]("https://wiki.ubuntu.com/Marplatense") , te lo agradezco, cuando llegue a casa lo pruebo y te aviso ...Saludos!!

---

