---
title: "bajar soft en ubuntu 9.10"
date: 2009-10-26
forum: Software
---

### Post by joseluis on 2009-10-26
HOLA..Hasta ubuntu 9.04 estaba la posibilidad de bajar todo tipo de soft desde Añadir / quitar (soft libre, de las comunidad, etc.) Por lo que veo, en el ubuntu 9.10 solo me da la posibilidad de bajar soft libre en "Centro de Software". ¿no es limitado? ¿o me estoy perdiendo algo?

---

### Post by luks911 on 2009-10-26
Ahora Añadir/Quitar se llama Centro de Software de Ubuntu, la cantidad de soft disponible me parece que es la misma. Al menos por lo que vi, los repositorios habilitados son los mismos, así que no hay limitaciones.
Además, tenés las opciones de siempre: instalar con apt-gte, aptitude y Synaptic.

Saludos

---

### Post by oktubrer on 2009-10-26
Corrijanme si me equivoco, pero cuando probé el live CD de Ubuntu 9.10 vi el viejo y querido "Agregar/Quitar" dentro del menú de administración.  No lo quitaron del todo, solo lo cambiaron de lugar.

---

### Post by Mauro22 on 2009-10-26
Cual probaste? alguna alpha??


El Centro de software de Ubuntu pasó por varias etapas...


Añadir o Quitar
Software Store
Volvió a añadir o quitar
finalmente quedo App Center (Centro de software de Ubuntu en español)

---

### Post by Fak89 on 2009-10-26
> **oktubrer said:**
> Corrijanme si me equivoco, pero cuando probé el live CD de Ubuntu 9.10 vi el viejo y querido "Agregar/Quitar" dentro del menú de administración.  No lo quitaron del todo, solo lo cambiaron de lugar.

Nop, no esta mas.
Me acabo de fijar en la RC..

Lo que si sigue estando es Synaptic.

---

### Post by oktubrer on 2009-10-26
> **Fak89 said:**
> Nop, no esta mas.
Me acabo de fijar en la RC..

Lo que si sigue estando es Synaptic.

Mirá vos, hubiera jurado que fue el RC, pero entonces debe haber sido en el beta o una de las alphas anteriores.

---

### Post by Fak89 on 2009-10-26
> **oktubrer said:**
> Mirá vos, hubiera jurado que fue el RC, pero entonces debe haber sido en el beta o una de las alphas anteriores.

Eso puede ser, las alphas y betas no las vi :p
De todas formas el App Center esta bastante bueno.. aunque todavía no instale nada desde ahí..

---

### Post by joseluis on 2009-10-26
Bueno, pero sin encontrar la posibilidad de elegir software. Es decir, se que está apt-get, sinaptyc, pero cuando yo iba a Agregar/Quitar, buscaba en la lista y elegía de ella en la opción "todas las aplicaciones disponibles" (creo que se llamaba asi), ahora solo me deja Aplicaciones Libres.
Quizas debe configurar algo en Origenes del Software? Alguien lo sabrá??

---

### Post by guillermolisi on 2009-10-26
> **joseluis said:**
> Bueno, pero sin encontrar la posibilidad de elegir software. Es decir, se que está apt-get, sinaptyc, pero cuando yo iba a Agregar/Quitar, buscaba en la lista y elegía de ella en la opción "todas las aplicaciones disponibles" (creo que se llamaba asi), ahora solo me deja Aplicaciones Libres.
Quizas debe configurar algo en Origenes del Software? Alguien lo sabrá??
Sobre eso se hablo a partir [de este post]("http://ubuntuforums.org/showpost.php?p=8084544&postcount=136").

---

### Post by luks911 on 2009-10-26
> **oktubrer said:**
> Corrijanme si me equivoco, pero cuando probé el live CD de Ubuntu 9.10 vi el viejo y querido "Agregar/Quitar" dentro del menú de administración.  No lo quitaron del todo, solo lo cambiaron de lugar.

Che, yo también lo tengo en la RC. Aparece en Administración y en inglés: Add/Remove Applications. De hecho está instalado el paquete gnome-app-install y funciona. Ahora lo desinstalo :-P

---

### Post by oktubrer on 2009-10-27
> **luks911 said:**
> Che, yo también lo tengo en la RC. Aparece en Administración y en inglés: Add/Remove Applications. De hecho está instalado el paquete gnome-app-install y funciona. Ahora lo desinstalo :-P

Sabía que no estaba [tan] loco. :p

---

### Post by joseluis on 2009-10-27
En mi RC no aparece el Agregar / Quitar. Pero el tema va más allá de eso, el tema pasa por el hecho de que solo se pueda descargar software libre, y no da posibilidad de otros soft, como en la anterior versión. ¿O me equivoco?

---

### Post by pablo.s on 2009-10-27
> **joseluis said:**
> el tema pasa por el hecho de que solo se pueda descargar software libre, y no da posibilidad de otros soft, como en la anterior versión. ¿O me equivoco?

¿Què significa otros soft?

---

### Post by guillermolisi on 2009-10-27
> **joseluis said:**
> En mi RC no aparece el Agregar / Quitar. Pero el tema va más allá de eso, el tema pasa por el hecho de que solo se pueda descargar software libre, y no da posibilidad de otros soft, como en la anterior versión. ¿O me equivoco?
Tenes que leer mas detenidamente. [En este post]("http://ubuntuforums.org/showpost.php?p=8172216&postcount=9") te tire una punta y parece que paso de largo. Ahi tenes como solucionar lo que preguntas.

---

### Post by joseluis on 2009-10-28
ok..ya voy entendiendo entonces. Lei el post que señalan. Lo que concluyo es que todo se centra en una única opción, lugar, y que las opciones anteriores fueron resumidas en una sola. Las otras que yo decia eran: "soft mantenido por canonical", "soft mantenido por la comunidad", "soft de terceros", y alguna mas....
Pareciera entonces que todo está en una sola.

---

### Post by pablo.s on 2009-10-28
> **joseluis said:**
> Lo que concluyo es que todo se centra en una única opción, lugar, y que las opciones anteriores fueron resumidas en una sola. Las otras que yo decia eran: "soft mantenido por canonical", 

Es el software que està en el 
repositorio main.

> **joseluis said:**
> "soft mantenido por la comunidad", 

Es el software que està en el
repositorio universe.

> **joseluis said:**
> "soft de terceros", y alguna mas....
Pareciera entonces que todo está en una sola.

Los demàs repositorios son
los de los drivers propietarios,
en restricted, los que llamariamos
de "terceros" que son los de multiverse
y luego todos los demàs repositorios
y PPA que tengas configurados en
tu .sources.list.

Depende de tu configuraciòn que es
lo que te muestra. Ademàs hay que
tener en cuenta que Synaptic es mucho
màs flexible para gestionar software.
Incluso saber los comandos para
solucionar paquetes rotos o actualizar
el sistema son muy utiles para aprenderse
de memoria.

---

### Post by joseluis on 2009-10-28
Gracias pablo.s. Voy a ver cómo está el source.lst, porque por ahí puede estar el tema entonces.

---

