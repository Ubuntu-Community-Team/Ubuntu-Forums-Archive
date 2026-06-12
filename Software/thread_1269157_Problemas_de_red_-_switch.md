---
title: "Problemas de red - switch"
date: 2009-09-17
forum: Software
---

### Post by harryscode on 2009-09-17
Hace un tiempo configuré una red entre xubuntu y xp con un Huawei MT882 y a los ponchazos lo logrè hacer funcionar. Xp se conectaba via usb y xubuntu via ethernet. El tema es que con xp tenia tambien dual ubuntu y como via usb no logre hacerlo andar, compre un switch y todo funciono muy bien. Los otros días "actualicé" xubuntu (pasé de ext3 a ext4) y quise configurar nuevamente la red, instalé samba, modifiqué el smb.conf tal cual la guia que aparece acá, pero tanto desde xp como desde ubuntu no puedo ver la maquina ni las carpetas de xubuntu. Desde xubuntu si lo puedo hacer. Mi pregunta es si hay que modificar o hay que hacer algo más si hay un switch en el medio. Gracias.

---

### Post by guillermolisi on 2009-09-18
> **harryscode said:**
> Hace un tiempo configuré una red entre xubuntu y xp con un Huawei MT882 y a los ponchazos lo logrè hacer funcionar. Xp se conectaba via usb y xubuntu via ethernet. El tema es que con xp tenia tambien dual ubuntu y como via usb no logre hacerlo andar, compre un switch y todo funciono muy bien. Los otros días "actualicé" xubuntu (pasé de ext3 a ext4) y quise configurar nuevamente la red, instalé samba, modifiqué el smb.conf tal cual la guia que aparece acá, pero tanto desde xp como desde ubuntu no puedo ver la maquina ni las carpetas de xubuntu. Desde xubuntu si lo puedo hacer. Mi pregunta es si hay que modificar o hay que hacer algo más si hay un switch en el medio. Gracias.
Si es solo un switch lo que esta en el medio, no hay que hacer nada diferente de lo que hiciste para que lo que comentas continue funcionando.

Me parece que el tema viene mas por el lado de la reinstalacion y configuracion de la misma que por otra cosa.

Por otra parte, si estas usando el mismo cable de red que tenias para interconectar ambas maquinas y el switch no posee ports con autosense nunca podras comunicarte porque el armado de cables para un caso y otro es diferente.

Cuando no hay switches el cable es cruzado (los hilos que escuchan de un lado son los que hablan del otro). Cuando hay un switch en el medio se usan cables rectos, derechos, sin cruzar, ya que el switch se encarga de hacer el cruce.

Los switches con bocas autosense verifican que tipo de cable se esta usando e invierten o no la comunicacion en funcion de eso, entre otras cosas.

---

### Post by harryscode on 2009-09-18
Gracias guillermo por la contestaciòn. A ver si te entiendo bien, supuestamente si antes funcionaba sin problemas, ahora deberia funcionar bien (ya que no toque nada físico). ¿Es así, no?. 
De ser así voy a tener que volver a revisar la instalación y configuración de samba. Lo que me parece extraño es que ni siquiera desde ubuntu puedo ver la pc que tiene xubuntu. Algo raro debo haber hecho. Gracias. 
PD. Me fijo y si sigo sin encontrarle la vuelta, los molesto de nuevo. 
Gracias nuevamente

---

### Post by guillermolisi on 2009-09-18
> **harryscode said:**
> Gracias guillermo por la contestaciòn. A ver si te entiendo bien, supuestamente si antes funcionaba sin problemas, ahora deberia funcionar bien (ya que no toque nada físico). ¿Es así, no?. 
De ser así voy a tener que volver a revisar la instalación y configuración de samba. Lo que me parece extraño es que ni siquiera desde ubuntu puedo ver la pc que tiene xubuntu. Algo raro debo haber hecho. Gracias. 
PD. Me fijo y si sigo sin encontrarle la vuelta, los molesto de nuevo. 
Gracias nuevamente
En realidad y si lees otra vez mi respuesta, digo que pueden ser dos cosas por separado o en forma simultanea, que esten actuando.

Si bien agregar un switch entre dos PCs no deberia modificar nada, esto es cierto siempre que el switch se de cuenta que el cable de red que estas usando es cruzado y "acomode" la comunicacion en funcion de esto.

Si el switch no tiene esta funcionalidad, no va a funcionar la red. Es decir, haber agregado el switch podria obligarte a cambiar por lo menos un cable de red.

Como tambien hiciste una reinstalacion, aqui juega como otro factor ya que, salvo que hayas tenido la precaucion de documentar todo lo que hiciste y que te condujo a que la cosa funcionara, siempre algun detalle se escapa.

Mi consejo es que vuelvas a probar todo tal como estaba originalmente (sin el switch) y verifica que asi la red funciona para un lado y otro. Con esta verificacion colocas el switch en juego y si deja de funcionar entonces probaria con cables de red derechos, no cruzados. Asi ya tenes acotado que funciona bien y que no.

---

### Post by harryscode on 2009-09-18
Ok.. ahora si me quedó claro. Probaré lo que me decis y comento como me fue.
Muchas Gracias.

---

