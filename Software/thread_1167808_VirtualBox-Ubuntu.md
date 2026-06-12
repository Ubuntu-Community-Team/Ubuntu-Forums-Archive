---
title: "VirtualBox-Ubuntu"
date: 2009-05-23
forum: Software
---

### Post by prostata on 2009-05-23
hago una pregunta de primaria, pues aunque imagino la respuesta, por falta de experiencia deseo confirmación para no meter la gamba....

1-si instalo virtualbox sobre jaunty, tengo que desinstalar previamente wxp...? o me reconoceria este ya sin más...??

2-cada vez que se actualice la versión de ubuntu, con virtualbox instalado, deberia proceder a instalarlo nuevamente o la nueva versión de ubuntu reconoceria la configuración existente y me permitiria seguir trabajando con la máquina virtual...? viendo indistintamente wxp como ubuntu...??

Pregunto porque; si antes debo desintalar wxp, con solo ubuntu instalar virtualbox y luego a partir de ahí instalar wxp, me parece un palo repetir el procedimiento cada vez que cambie la versión de ubuntu....

¿estoy en lo cierto...?

Saludos

---

### Post by pol666 on 2009-05-23
> 
1-si instalo virtualbox sobre jaunty, tengo que desinstalar previamente wxp...? o me reconoceria este ya sin más...??


te referis al Windows instalado en tu disco?; eso no tiene nada que ver, la virtual box simplemente virtualiza una maquina donde le tenes que instalar un sistema operativo, en este caso instalarias nuevamente XP en la virtual box.

> 
2-cada vez que se actualice la versión de ubuntu, con virtualbox instalado, deberia proceder a instalarlo nuevamente o la nueva versión de ubuntu reconoceria la configuración existente y me permitiria seguir trabajando con la máquina virtual...? viendo indistintamente wxp como ubuntu...??

Si actualizas desde internet o tenes la "/home" separada solamente basta con volver a isntalar virtual box, el windows virtual no lo perderias. En caso de que borres todo, incluyendo la home, tendrias que que reinstalar virtual box y el windows virtual salvo que, hagas un backup del archivo .vdi
> 

Pregunto porque; si antes debo desintalar wxp, con solo ubuntu instalar virtualbox y luego a partir de ahí instalar wxp, me parece un palo repetir el procedimiento cada vez que cambie la versión de ubuntu....


No, como te dije antes, podes hacer el backup del archivo .vdi en caso de que tambien borres /home, si actualizas por internet, no es necesario. Yo por ejemplo concervo el mismo Windows Virtualizado desde 8.04

---

### Post by prostata on 2009-05-23
> **pol666 said:**
> te referis al Windows instalado en tu disco?; eso no tiene nada que ver, la virtual box simplemente virtualiza una maquina donde le tenes que instalar un sistema operativo, en este caso instalarias nuevamente XP en la virtual box.



Si actualizas desde internet o tenes la "/home" separada solamente basta con volver a isntalar virtual box, el windows virtual no lo perderias. En caso de que borres todo, incluyendo la home, tendrias que que reinstalar virtual box y el windows virtual salvo que, hagas un backup del archivo .vdi


No, como te dije antes, podes hacer el backup del archivo .vdi en caso de que tambien borres /home, si actualizas por internet, no es necesario. Yo por ejemplo concervo el mismo Windows Virtualizado desde 8.04



Pues gracias, era lo que suponia, pero necesitaba consejo ya que no lo había hecho antes y tenía esas dudas....

Saludos

---

### Post by z37a on 2009-05-23
> **prostata said:**
> Pues gracias, era lo que suponia, pero necesitaba consejo ya que no lo había hecho antes y tenía esas dudas....

Saludos

Consejo, anda a la pagina de virtualbox y agrega los repostorios de esta a la lista de tu ubuntu, asi podes instalar la version estandar y se te va a actualizar solo con el gestor!!!

[http://www.virtualbox.org/](http://www.virtualbox.org/)

PD: Parece loco que prefiera algo que no es 100% libre, peor la verdad que el OSE no funciona tan bien como el otro, y este otro tiene USB y algunas cosillas mas que lo hacen mas interesante.

---

