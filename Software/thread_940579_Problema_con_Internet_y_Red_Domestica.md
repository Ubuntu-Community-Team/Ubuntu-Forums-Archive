---
title: "Problema con Internet y Red Domestica"
date: 2008-10-07
forum: Software
---

### Post by santiagofrias on 2008-10-07
Desde hace unos días, mi conexión a Internet se encuentra cortada (el cable telefónico se cortó y estoy esperando que Telecom se decida ir a repararlo), desde entonces, no puedo conectar mi dos computadoras entre sí (una PC y una Laptop, ambas con Ubuntu 8.04 y Windows XP). Antes de este problema y cuando instalé Ubuntu en las máquinas, no tuve que configurar nada y las máquinas se veían y compartían archivos entre sí sin ningún problema. La Laptop se comunicaba mediante Wi-Fi ya que el modem-router que dispongo tiene esta posibilidad.
Ahora bien, si inicio en Win XP, las máquinas se conectan entre sí sin ningún problema (a pesar de no tener Internet, repito); pero en Ubuntu, no.
¿Tiene algo que ver que no tenga la conexión a Internet? 
¿La red en Ubuntu de pende de la conexión a Internet?
¿Cambio algo, o espero a que se restablezca Internet y veo?
Este es el esquema de mi conexión y el tipo de modem-router que tengo.
[IMG]http://fdntga.bay.livefilestore.com/y1pgSUUm3R7P-8ntAlp0rmQgAl9--JuJh_kI3ZirED5Tff6ZRpge0rPVBU5cLJ5oi_FUJ8o7rXFPFc/Red.png[/IMG]

Gracias a todos desde ya.

---

### Post by faktorqm on 2008-10-07
Hola, lo mas mas mas rapido que podes hacer para superar el problema, es, es una pc tenes xp y ubuntu, y en la otra solo ubuntu (en realidad no importa)) peor si al menos compartis en una via, en un ubuntu tenes un samba, alcanza con configurar el samba en la otra y ya! (te estarias conectando a traves de smb a tu otro ubuntu). Esto no es lo mas tecnicamente feliz que podes hacer, pero para no cambiar 1000 cosas y que encima no te ande, lo mas rapido y directo es eso. (y si cambias a xp la otra, tambien vas a ver el ubuntu)
Yo postie un pequeño manual de samba para principiantes, si queres pegale una leida rapida (es APB, si ya manejaste samba, saltealo)

[http://ubuntuforums.org/showpost.php?p=4343317&postcount=3](http://ubuntuforums.org/showpost.php?p=4343317&postcount=3)

Lo de internet bueno, cuando te lo arreglen va a seguir todo igual por que son dos cosas distintas la comparticion de archivos e internet. Espero que te haya servido. Salu2!

---

### Post by santiagofrias on 2008-10-07
> **faktorqm said:**
> Hola, lo mas mas mas rapido que podes hacer para superar el problema, es, es una pc tenes xp y ubuntu, y en la otra solo ubuntu (en realidad no importa)) peor si al menos compartis en una via, en un ubuntu tenes un samba, alcanza con configurar el samba en la otra y ya! (te estarias conectando a traves de smb a tu otro ubuntu). Esto no es lo mas tecnicamente feliz que podes hacer, pero para no cambiar 1000 cosas y que encima no te ande, lo mas rapido y directo es eso. (y si cambias a xp la otra, tambien vas a ver el ubuntu)
Yo postie un pequeño manual de samba para principiantes, si queres pegale una leida rapida (es APB, si ya manejaste samba, saltealo)

[http://ubuntuforums.org/showpost.php?p=4343317&postcount=3](http://ubuntuforums.org/showpost.php?p=4343317&postcount=3)


Lo de internet bueno, cuando te lo arreglen va a seguir todo igual por que son dos cosas distintas la comparticion de archivos e internet. Espero que te haya servido. Salu2!

Muchas gracias faktorqm, en cuanto llegue a casa pruebo con tu manual, la única duda que me quedó es porque este problema se me presentó cuando se cortó el cable, o sea: cuando tenía internet, todo andaba bien, los archivos compartidos entre los dos ubuntus, internet y demás; pero cuando se cortó el cable...nada; ya no se veían las máquinas en ubuntu, etc.
Gracias desde ya por el manual.

---

### Post by faktorqm on 2008-10-07
Bueno pero el router no lo tenes que apagar eh! sino no tenes conexion fisica. el router lo tenes que dejar prendido como si nada y ahi deberias tener conexion. sino pone ifconfig en ambas compus y postea la salida. salu2!

---

