---
title: "Grabar streaming con VLC"
date: 2010-08-26
forum: Software
---

### Post by Brath-ga on 2010-08-26
Saludos a tod@s.

Estoy grabando unos archios asf de una web de televisión a la carta con VLC.

Tengo un par de problemas:
1 - Cuando pulso el botón de grabar al tiempo que reproduce, no se si está grabando a menos que mire en mi /home si algún archivo nuevo está creciendo de tamaño, tanto si está grabando como si no, el botón está en rojo.
2 - Al ser un  streaming, tiene que cargar el buffer constantemente y lleva mucho tiempo.
Puedo aumentar el tamaño del buffer?
Puedo grabarlos de otra forma?
Me recomendais algún programa mejor para lo que pretendo?

Gracias.

---

### Post by viralmeme on 2010-08-26
> **Brath-ga said:**
> Me recomendais algún programa mejor para lo que pretendo?Gracias.
Nos gusta pensar de [MythTV]("http://www.mythtv.org/detail/mythtv") como la última grabadora de video digital y el hogar del centro de medios centro. Piense en ello como una alternativa libre y de código abierto para Windows Media Center o Tivo ..

---

### Post by EnriqueK on 2010-08-26
Con Mplayer, el comando sería
mplayer -dumpstream URL_de_la_transmisióm
Por ejemplo si querés grabar radio del Plata, debes abrir  un terminal en la carpeta que quieras contener la grabación y poner:
**mplayer -dumpstream mms://delplata.telecomdatacenter.com.ar/delplata**
A mi entender este método tiene dos inconvenientes

1.- Si se corta la transmisión se se paraliza la grabación, o sea no la retoma cuando retorna la transmisión.
2,. Si querés seguir grabando después de un corte, tenés que renombrar el primer archivo de grabación por que el nuevo te lo machaca.

---

