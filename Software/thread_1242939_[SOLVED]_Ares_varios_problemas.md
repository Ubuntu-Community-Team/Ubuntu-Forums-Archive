---
title: "[SOLVED] Ares varios problemas"
date: 2009-08-17
forum: Software
---

### Post by jorgebada on 2009-08-17
me instale el wine y tengo la ultima version dl ares el 2.1..1.3035 cuando lo instale se conecto al toque ahora no me conecta tengo activado el firewall de ubuntu y abri el puerto del ares el cual estaba en la parte d paner de control. Hoy lo voy a dejar varias horas prendido para ver si se conecta. El win lo tengo configurado como windows ME

Otro problema es que cuando le doy maximizar al ares empieza a parpadear y no para como que no puede maximizar lo mismo cuando intento minimizar que puede ser esto.

---

### Post by sianhulo on 2009-08-17
te recomiendo utilizar el frostwire,es nativo en linux y nunca me ha dado problemas

---

### Post by santiagoward2000 on 2009-08-17
Hola!
Si querés conectarte a la red del Ares, podés probar con giFT. Acá te dejo una guía: [http://ubuntuforums.org/showthread.php?t=1088793&highlight=ares+wine]("http://ubuntuforums.org/showthread.php?t=1088793&highlight=ares+wine")
Así te olvidás de los problemas que pueden venir por culpa de wine.
Saludos!

---

### Post by guisheca on 2009-08-17
La config del wine tiene que estar en winxp para que funcione correctamente el ares.

Lo del parpadeo también me pasa y no le encuentro solución mas que mantener la ventana en tamaño original y no tocarla (es decir, no minimizar, maximizar, redimensionar, etc).

Con el tema de la conexión, sabemos que es casi un misterio porque el ares no se conecta muchas veces, yo siempre hago lo siguiente (esto que voy a poner a continuación carece de toda lógica, pero quien sabe porque, me funciona) descargo el script [winetrikcs]("http://wiki.winehq.org/winetricks") e instalo el directx :confused:, si, eso hago, antes de instalar el wine y todo me funciona siempre.

Si no, espero laaaargas horas hasta que en algún momento se conecta, después de eso siempre anda.

Y dejame decirte que, en lo personal, ninguna de las opciones que te dieron como alternativa al ares por wine me resultó mejor. El frostwire esta bueno, pero no encontras lo mismo que con wine. Y el giFT con el plugin de ares tiene sus fallas, como por ejemplo que te descarga dos veces el mismo archivo a veces.

Saludos.

---

### Post by jorgebada on 2009-08-20
JOJOJO ya me anda. Me descarge la ultima version del ubuntu el 9.04 e igual no me andaba el ares. Hice unas cosa y andubo, les detallo ahora.  Pasos que hice:

1- puse en la configuracion del wine para q trabaje como xp (lo tenia en ME porque vi en un post d otra pag q asi funcionava)

2- En panel de control del ares en la parte GENERAL destilde todos las opciones, solo deje mostrar mi estado en la barra de titulo de la ventana principal (creo q lo significativo aca es que destilde la que decia AUTOCONECTARSE A LA RED CUANDO INICIO ARES). Osea ahora cada ves que entro tengo q poner CONECTAR 

Por ahora me anda muy bien jejeje. Y con respecto a que se me tildaba cuando lo maximizaba o minimizaba, ahora ya no tengo problema, capas sea porque actualice el ubuntu o porque instale otro driver del nvidia, el 173.

No les puedo describir lo contento que estoy probe hasta lo imposible para que funcionara, hasta instale el aMula hoy y es una cagad..................... no se compara con el ares.

---

