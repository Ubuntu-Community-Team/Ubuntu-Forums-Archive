---
title: "se corta la conexion inalambrica"
date: 2010-05-06
forum: Software
---

### Post by drazhe on 2010-05-06
Desde que actualice a Lucid Linx, noto que cuando cierro la pantalla de la portatil esta pierde la conexión inalambrica. cuando la vuelvo a abrir esta un cartel de error diciendo eso y pidiendome el anillo de claves default que me pide al encender la notebook. 
Hay alguna manera de evitar que esto pase? porque hay veces que la tengo que dejar trabajando en internet pero no quiero dejarla con la pantalla prendida o el protector de pantalla....

---

### Post by alfplayer on 2010-05-06
Creo que aparecen esos carteles porque se está suspendiendo o hibernando cuando se cierra la tapa.

En Sistema --> Preferencias --> Gestión de energía

se puede cambiar una opción para que se ponga la pantalla negra cuando se cierra la tapa.

---

### Post by drazhe on 2010-05-06
> **alfplayer said:**
> Creo que aparecen esos carteles porque se está suspendiendo o hibernando cuando se cierra la tapa.

En Sistema --> Preferencias --> Gestión de energía

se puede cambiar una opción para que se ponga la pantalla negra cuando se cierra la tapa.

Te adjunto un par de imágenes de 

**En Sistema --> Preferencias --> Gestión de energía**

para que veas como lo tengo configurado y aún así al cerrar la tapa de la notebook se corta la conexión inalambrica.

[CENTER][IMG]http://i42.tinypic.com/25fina1.png[/IMG]

[IMG]http://i44.tinypic.com/2vteamh.png[/IMG][/CENTER]

Por lo que se, está todo como debería estar, por eso me parece raro que corte la conexión, yo creo que el problema esta en el anillo de claves por default.

---

### Post by alfplayer on 2010-05-06
Lo que está en la imagen es para controlar, según el título de la pestaña, cuando el cable de energía está conectado. El problema es cuando está conectado?

No tengo Lucid para probar en una notebook, pero creo que aparece la pestaña de batería cuando está funcionando a batería, y esa configuración también debe ser modificada (para cambiar el comportamiento cuando está funcionando a batería).

Es poco intuitivo. Debería poder configurarse todo cuando el cable está conectado y desconectado.

---

### Post by drazhe on 2010-05-07
> **alfplayer said:**
> Lo que está en la imagen es para controlar, según el título de la pestaña, cuando el cable de energía está conectado. El problema es cuando está conectado?

No tengo Lucid para probar en una notebook, pero creo que aparece la pestaña de batería cuando está funcionando a batería, y esa configuración también debe ser modificada (para cambiar el comportamiento cuando está funcionando a batería).

Es poco intuitivo. Debería poder configurarse todo cuando el cable está conectado y desconectado.


da igual, con batería, con batería y cableada, cableada y sin la batería puesta, cada vez que cierro la pantalla se corta la conexión, y al abrirla me pide nuevamente el password del router y el anillo de claves por default.

---

### Post by alfplayer on 2010-05-07
> **drazhe said:**
> da igual, con batería, con batería y cableada, cableada y sin la batería puesta, cada vez que cierro la pantalla se corta la conexión, y al abrirla me pide nuevamente el password del router y el anillo de claves por default.

Entonces es un bug. El problema es que no hace lo que tiene que hacer, que es oscurecer la pantalla. Oscurecer la pantalla solo debe afectar al monitor, para el resto del sistema es como si no pasara nada.

Si el problema sucede después de un tiempo de dejar la tapa cerrada el bug es que no se deshabilita la suspensión o hibernación.

---

### Post by drazhe on 2010-05-08
> **alfplayer said:**
> Entonces es un bug. El problema es que no hace lo que tiene que hacer, que es oscurecer la pantalla. Oscurecer la pantalla solo debe afectar al monitor, para el resto del sistema es como si no pasara nada.

Si el problema sucede después de un tiempo de dejar la tapa cerrada el bug es que no se deshabilita la suspensión o hibernación.

y te diría que es instantáneo, el otro día probé, dejando bajando algo, cerré la tapa, fui a la cocina por algo de café y cuando volví a abrir la pantalla estaba pidiéndome las claves nuevamente y obviamente sin conexión.
En Karmic también noté eso, pero era mas esporádico, en os 6 meses que usé KK me habrá tirado el mismo error un par de veces muy espaciadas entre si. pero con LL es siempre que cierro la tapa de la portátil.

---

