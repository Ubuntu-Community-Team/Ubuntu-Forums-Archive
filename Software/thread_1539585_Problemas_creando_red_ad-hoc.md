---
title: "Problemas creando red ad-hoc"
date: 2010-07-26
forum: Software
---

### Post by themasterdark on 2010-07-26
Hola chicos

Me dirijo al foro, y en el área de software porque por la parte de hardware de las inalambricas esta todo ok.

Bueno resulta que se daño el router de la casa de mis padres =(, y por ahora no esta en planes comprar otro jaja, bueno la cosa es la siguiente, trate de compartir internet mediante una red ad-hoc entre dos notebooks (uno con ubuntu 10.04 el mio, y otro con xp)
peeero el problema es el siguiente:

UBUNTU (creo la red con network manager, wicd, o manualmente)

XP (ve la red pero no conecta :shock:)

dejando todo en automatico.

Ahora si lo hago todo asignando yo las ip, dns y demas.

pasa lo mismo :shock:

Trate de hacerlo desde xp a ubuntu (cosa que no es la idea, pero pasa exactamente igual en ese caso ubuntu ve la red y no conecta :shock:)

Asi, que llego para que me den una mano, busque informacion en bastaaaaantes lugares pero todo me daba la misma info, probe firestarter también.

Saludos.!! =)

---

### Post by themasterdark on 2010-07-27
Y bueno me respondo solo xD....

Ya lo solucione funciono de ambos lados de ubuntu a windows y de windows a ubuntu (siendo la ultima la que use, ya que si lo hacia de ubuntu a windows el **** windows ingresaba solo a paginas de google por el tema de MTU que me dio flojera arreglar)

bueno la solucion es bastante facil.

Mi tarjeta inalambrica es una Broadcom y estaba usando el driver B43XXX... 

Lo que hice fue cambiarlo por el STA que ofrece el mismo sistema en Administracion -> hardware.

Una vez hecho esto hay que crear la red ad-hoc dandole los parametros de ip y dns al servidor (XP o ubuntu)(en mi caso XP).

y al segundo en caso de ser ubuntu crear la red ad-hoc y dejar que tome ip de forma automatica por dhcp, los dns tambien.

En el caso de ser windows hay que fijarle los parametros de ip, puerta de enlace y dns.

Y eso es todo =) asi que Solucionado

PD: Ahora mismo escribo desde mi ubuntu en modo cliente ad-hoc recibiendo internet de un **** Windows del note de mi hermano xD jaja, si lo apaga sone claro.! xD jaja

---

