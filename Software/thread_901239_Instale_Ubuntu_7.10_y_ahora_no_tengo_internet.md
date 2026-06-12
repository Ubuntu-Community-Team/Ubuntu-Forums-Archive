---
title: "Instale Ubuntu 7.10 y ahora no tengo internet"
date: 2008-08-26
forum: Software
---

### Post by guillermoezquer on 2008-08-26
Hola gente, primero q nada espero no equibocarme en el lugar q he hecho esta consulta, si es asi... pido disculpas.
Ahora les comento q soy bastante nuevo en esto de linux, estuve migrando desde win desde hace muy poco a ubuntu 7.04 en el cual se me precentaron un par de problemas como a cualquier amateur pero los pude solucionar....
Una vez solucionados estos problemas pense q era hora de actualizar mi ubuntu a la version 7.10 para llegar despues a la version 8.04... 
El grave inconveniente q se me precento fue q al terminar de actualizar mi ubuntu ya no tenia internet... y la verdad es q no tengo ni idea de por que... si inicio mi pc con win, internet anda bien, al igual q en cualquier otra maquina de la red...
Desde ya se valora cualquier tipo de ayuda y recuerden q soy muy nuevo en esto jeje

---

### Post by faktorqm on 2008-08-26
postea como te conectas a internet, adivinos no somos (casi, pero no del todo) si tenes adsl, cablemodem, 3G, etc.
y otra cosa, para que queres actualizar si en octubre sale 8.10? te conviene moverte a la ultima de una y no pasar por todas.... va, me parece una perdida de tiempo, capaz lo necesitas por algo en particular, no se. Salu2!

---

### Post by guillermoezquer on 2008-08-26
Muchas gracias por el consejo sobre la actualizacion... la verdad q no estaba muy al tanto sobre esta... 
Respecto a mi problema, me conecto mediande DSL con un modem ZXDSL, con el cual antes no habia tenido ningun problema... o al menos al configurar feisty no los tuve...
Gracias desde ya por haber contestado.

---

### Post by faktorqm on 2008-08-26
aca tenes como configurarlo (capaz ya lo hiciste) [http://www.speedy.com.ar/soporte.php?event=detalle&idcontenido=214&root=132](http://www.speedy.com.ar/soporte.php?event=detalle&idcontenido=214&root=132) 
y pone la placa de red en dhcp o en un ip del rango que diga el link ese q t pase. o sino bootea con un kernel anterior (desde el grub, no se si tenes) y podes probar ahi el tema de la conexion a internet, capaz actualizaste el kernel y perdiste eso. Salu2!

---

### Post by guillermoezquer on 2008-08-26
Disculpame la ignorancia... pero no te comente q tengo 2 pc mas conectadas a ese modem mediante un swich... queria saber si cambiandole esa configuracion al modem voy a tener q reconfigurar las pc q tienen winxp...

---

### Post by guillermoezquer on 2008-08-26
otra vez yo... me fije la configuracion q me pasaste en el link y es igual a la que tengo lo q no se hacer es poner mi placa como me dijiste en dhcp... si pudieras ser mas explicito seria de gran ayuda... gracias!

---

### Post by faktorqm on 2008-08-26
sistema -> administracion -> red; 
boton desbloquear, ingresas tu clave;
elegis conexion cableada, boton propiedades;
elegis ip automatica, y cerras todo.

---

### Post by guillermoezquer on 2008-08-27
Otra vez yo... lamentablemente eh hecho lo q me digiste y no ah habido ningun tipo de cambio respecto a mi conexion de internet... no se si se les ocurre alguna otra idea q pueda probar...

---

### Post by faktorqm on 2008-08-27
y si booteas con el live cd pasa lo mismo? salu2!

---

### Post by guillermoezquer on 2008-08-27
Baje el Ubuntu live 8.04 y en este si me funciona la red y mi conexion a internet... pero como es costumbre al menos para mi... ahora tengo el problema de q no detecta bien mi placa de video... se ve todo rayado y no se entiende casi nada... tuve q hacer milagros para ver si andaba la red con este problema... por suerte lo logre y pude ver q si me anda... el problema ahora es poder configurar mi placa de video... es un via integrada p4m890... si tienes idea de como solucionar esto te lo agradeceria...

---

### Post by faktorqm on 2008-08-27
la verdad la verdad, no se. Yo me estuve peleando con uno de esos bichos durante casi 1 año y no logre hacer andar nada de nada. O sea, lo de las rayas si se puede solucinar, y eso ya estaba posteado por aca. Salu2!

---

