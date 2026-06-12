---
title: "Avahi y Bind9"
date: 2009-10-24
forum: Software
---

### Post by Fistandantilus on 2009-10-24
Hola a todos!

Estoy trantando de ver como configurar avahi para que labure con bind9 y no encuentro nada. A ver si se les ocurre algo a ustedes...

Lo que estoy tratando de hacer es configurar el avahi-daemon para que labure actualizando registros en un servidor dns(bind9 en este caso).
¿Por que no elegir solo una de las opciones? Simple, a bind9 lo necesito para configurar un dominio con OpenLDAP y Krb, pero no quiero perder todas las cosas buenas que trae el uso de avahi en una red...

Mi idea era configurar el bind9 para que permita updates desde la red local pero nesecito algo que lo actualize(por ej. si a una maquina se le dio otra ip estando debajo de un dhcp al iniciar, etc...).

Capaz exista alguna otra opción, que desconosca.

Saludos!.

---

### Post by juancarlospaco on 2009-10-25
*No entiendo del todo...*, 
vos decis algo para que no venga alguien con una IP fija igual a tu servo y te voltee el servo?,
pero para eso seria recomendable usar **VLans**, 
de paso ganas performance, mas si hay Windoz dando vueltas,
tambien seguridad, si tenes una red plana, en ataques se cae facil,
proba..., agarra tu red con un Yersinia y dale massa, 
vas a ver que los Switches *(layer3)* se vuelven Hubs 
y no anda ni para atras *(esto asusta hasta algunos Cisco los mata a palos)*.

---

