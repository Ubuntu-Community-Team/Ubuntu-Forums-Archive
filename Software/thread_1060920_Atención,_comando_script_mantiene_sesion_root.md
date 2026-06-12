---
title: "Atención, comando script mantiene sesion root"
date: 2009-02-05
forum: Software
---

### Post by joseluisb on 2009-02-05
Buenas,
acabo de instalar ubuntu en mi Acer Aspire 4520 y en la pc de mi casa.

En ambas estoy instalando Apache2, PHP, MySQL y PostgreSQL con intenciones de montar un servidor web hogareño.

La cuestión es que intentando registrar todos los comandos necesarios para instalarlos decido utilizar el comando script:
$sudo script install.log

Me llevo la sorpresa que nunca volvió al usuario normal dejando la sesión de root hasta que finalicé el logueo con Ctrl+D.

No se si es correcto que ocurra esto, a mi se me ocurre que no, que debería comenzar el logueo y volver al usuario normal.

Bueno, también soy nuevo en el foro y espero poder ayudar en algo además de encontrar respuestas.

Saludos.

---

### Post by Hei Ku on 2009-02-05
La pregunta seria por que corriste el script con sudo? Lo haga el script probablemente es abrirte la terminal corriendo sobre el programa. Como script lo abriste con sudo, la terminal la corre como root.

---

