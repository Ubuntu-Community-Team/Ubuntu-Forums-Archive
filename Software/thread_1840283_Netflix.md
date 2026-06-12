---
title: "Netflix"
date: 2011-09-07
forum: Software
---

### Post by rojojuan on 2011-09-07
Netflix (almacén de películas por Pesos 39 mensuales) llegó a Argentina y parece que no estará disponible para usarlo con Ubuntu.
Ya esta habilitada la suscripción por un mes gratis.
Link:[https://signup.netflix.com/?mqso=80030571&locale=es-AR&mkwid=sFpMG4elR&pcrid=8966787666](https://signup.netflix.com/?mqso=80030571&locale=es-AR&mkwid=sFpMG4elR&pcrid=8966787666)
¿Alguien tiene idea sobre qué hacer para poder usar Ubuntu? Aclaro que no me suscribí a esa promoción porque leí en la web que no funciona con “Linux”

---

### Post by Beacon11 on 2011-09-07
Por desgracia, Netflix utiliza Microsoft Silverlight para sus videos, que sólo es compatible con Windows y Mac OS X. Silverlight se usa en lugar de Flash (por ejemplo), ya que de su aplicación DRM. La única manera que conozco para ver vídeos Netflix en Linux es ejecutar Windows en una máquina virtual (por ejemplo, VirtualBox: [http://www.virtualbox.org/](http://www.virtualbox.org/)).

---

### Post by rojojuan on 2011-09-07
> **Beacon11 said:**
> Por desgracia, Netflix utiliza Microsoft Silverlight para sus videos, que sólo es compatible con Windows y Mac OS X. Silverlight se usa en lugar de Flash (por ejemplo), ya que de su aplicación DRM. La única manera que conozco para ver vídeos Netflix en Linux es ejecutar Windows en una máquina virtual (por ejemplo, VirtualBox: [http://www.virtualbox.org/](http://www.virtualbox.org/)).

Muchas gracias por la info!!

---

### Post by rojojuan on 2011-09-07
> **Beacon11 said:**
> Por desgracia, Netflix utiliza Microsoft Silverlight para sus videos, que sólo es compatible con Windows y Mac OS X. Silverlight se usa en lugar de Flash (por ejemplo), ya que de su aplicación DRM. La única manera que conozco para ver vídeos Netflix en Linux es ejecutar Windows en una máquina virtual (por ejemplo, VirtualBox: [http://www.virtualbox.org/](http://www.virtualbox.org/)).

Investigando un poco más llegué a esta página:

[http://www.go-mono.com/moonlight/download.aspx](http://www.go-mono.com/moonlight/download.aspx)


Que te parece? Puede servir?

---

### Post by Beacon11 on 2011-09-08
> **rojojuan said:**
> Que te parece? Puede servir?

Desafortunadamente, mientras que Moonlight es de hecho una implementación de código abierto de Silverlight y puede utilizar los codecs necesarios, que carece de soporte DRM por lo que utiliza Netflix Silverlight en el primer lugar. Para más información, consulte la FAQ Moonlight: [http://www.go-mono.com/moonlight/faq.aspx](http://www.go-mono.com/moonlight/faq.aspx)

---

### Post by rojojuan on 2011-09-08
> **Beacon11 said:**
> Desafortunadamente, mientras que Moonlight es de hecho una implementación de código abierto de Silverlight y puede utilizar los codecs necesarios, que carece de soporte DRM por lo que utiliza Netflix Silverlight en el primer lugar. Para más información, consulte la FAQ Moonlight: [http://www.go-mono.com/moonlight/faq.aspx](http://www.go-mono.com/moonlight/faq.aspx)


Muchísimas gracias. Me quedó todo claro.

---

### Post by hictio on 2011-09-08
Ayer estuve Googleando el tema después de ver tu post, lamentablemente no hay manera de hacerlo funcionar en Linux. Ni siquiera funciona con Wine.
Por lo que leí, la única manera es usando una imagen virtual de Windows.

---

### Post by rojojuan on 2011-09-09
> **hictio said:**
> Ayer estuve Googleando el tema después de ver tu post, lamentablemente no hay manera de hacerlo funcionar en Linux. Ni siquiera funciona con Wine.
Por lo que leí, la única manera es usando una imagen virtual de Windows.

Muchas gracias por tu aporte.

---

### Post by Beacon11 on 2011-09-09
> **hictio said:**
> Ayer estuve Googleando el tema después de ver tu post, lamentablemente no hay manera de hacerlo funcionar en Linux. Ni siquiera funciona con Wine.
Por lo que leí, la única manera es usando una imagen virtual de Windows.

rojojuan, le sugiero que marca este tema como resuelto antes de llegar a respuestas más duplicados :) .

---

### Post by guillermolisi on 2011-09-10
> **Beacon11 said:**
> rojojuan, le sugiero que marca este tema como resuelto antes de llegar a respuestas más duplicados :) .
Los threads que realmente arribaron a una solucion efectiva son los que deben marcarse como SOLVED.

Los que no llegaron a una solucion efectiva, sea porque hubo una reinstalacion sin investigacion de causas que determinaran esta accion como unica solucion, o como este caso donde por el momento no hay como acceder al servicio usando Ubuntu, son temas NO resueltos.

Si a los casos citados se los marca somo resueltos estaremos confundiendo a quienes eligen esos hilos pensando que encontraran una solucion concreta y efectiva a su problema (cuando en realidad no la hay).

Esta en cada uno darse cuenta en que duplicar mensajes que no aportan nada nuevo es esteril y que a raiz de esto es mejor abstenerse de repetir lo que otros han dicho antes.

Por estas razones le modifique el tag volviendolo a su valor original (no resuelto).

---

