---
title: "no puedo iniciar ubuntu 9.04"
date: 2010-02-28
forum: Software
---

### Post by nestor l on 2010-02-28
Hola a todos, me llamo a nestor y uso ubuntu hace un par de años y casi que no he tenido problemas con este sistema, hasta hoy y quisiera saber si alguien me puede ayudar y evitar tener que formatear

me ocurre lo siguiente , he tenido un corte de energia , cuando esta volvio y quise iniciar mi pc (solo tengo ubunto 9.04, no windows) me aparece el siguiente mensaje de error

"ha ocurrido un error mintras cargaba o guardaba la informacion de cconfiguracion de evolution-alarm-notify. puede de que alguno de sus ajuste de configuracion no funcione adecuadamente"
y tengo dos botones uno de ACEPTAR y otro de detalles, si clickeo este me dice que hay un fallo al contactar con el servidor de configuraciones y que tengo activar tcp/ip en orbit o que tengo bloqueos de nfs debido a una caida del sistema
si apreto aceptar queda colgada y no pasa mas nada 
que se puede hacer ???
puse el cd de instalacion la opcion de reparar y nada, queda colgada. necesito sobre todo recuperar mis archivos, los que estan todos en el escritorio. (no es mucah cantidad) luego si tengo que reinstalar lo hare, pero si existe una forma de salvarlo todo...
agradecere soluciones posibles
saludos para todos

---

### Post by juancarlospaco on 2010-02-28
Desde el LiveCD podes acceder al disco y hacer backup.

Desinstala el Evolution, despues si queres lo volves a instalar.

Hace un chequeo de integridad del filesystem:
**sudo touch /forcefsck ; sudo reboot**

---

