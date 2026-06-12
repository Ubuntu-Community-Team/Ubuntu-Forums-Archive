---
title: "Configurar (saltear) proxy"
date: 2009-05-07
forum: Software
---

### Post by sergiom99 on 2009-05-07
Hola gente, 
hoy estaba en la facultad y me conecté a un par de nodos que había por ahí, pero en ambos pude bajar mails pero no navegar.
Despues me acordé que para salir hay un proxy, pero como no se que configuración lleva, quería preguntarles si hay alguna manera de:
1) Descubrir que IP tiene el proxy (no creo que lleve clave) para configurar el FF.
2) Configurar mi Kubuntu para que de alguna manera, la que sea, saltear el proxy y poder navegar.

Los mails los bajé sin problema y podía pingear a cualquier lado, por host y por IP.

Saludos- Sergio

---

### Post by Hei Ku on 2009-05-07
Podrias hacer un traceroute y configurar como proxy la ultima IP privada. El tema es el puerto, que podes probar el 80 o el 8080, que son los mas comunes.

---

### Post by sergiom99 on 2009-05-07
hmmmm... no se me habia ocurrido, que panfilo.
La proxima lo pruebo y veo si funca.
Gracias!

---

### Post by faktorqm on 2009-05-08
yo tiraria "deteccion automatica", capaz esta activado eso y te lo autodetecta. 

Una vez que lo tengas lo podes saltear de mil formas, depende de lo que quieras hacer, avisame y te digo :P (tengo experiencia :P:P:P) Salu2!

---

### Post by sergiom99 on 2009-05-08
> **faktorqm said:**
> yo tiraria "deteccion automatica", capaz esta activado eso y te lo autodetecta. 

En el FF?
Gracias Martín!

---

### Post by sergiom99 on 2009-05-18
> **faktorqm said:**
> yo tiraria "deteccion automatica", capaz esta activado eso y te lo autodetecta. 

Una vez que lo tengas lo podes saltear de mil formas, depende de lo que quieras hacer, avisame y te digo :P (tengo experiencia :P:P:P) Salu2!

Deteccion automatica no funciono. Pero fue mas facil: pregunte a un admin y me lo dijeron.

Lo que si el proxy de la UBA es zarpado garca y tiene filtrado el SMTP (Ademas de ssh, millones de sitios, etc) asi que no pude ni mandar mails usando mi servidor y/o gmail.
Esto sabes como saltearlo? Creo que tenes insider-information ;);)

---

### Post by Hei Ku on 2009-05-18
Usa tor.

---

