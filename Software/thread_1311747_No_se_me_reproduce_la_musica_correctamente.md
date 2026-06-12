---
title: "No se me reproduce la musica correctamente"
date: 2009-11-02
forum: Software
---

### Post by MightyWearrior on 2009-11-02
HOla a todos, bueno soy nuevo aqui en ubuntu. Hoy instale el ubuntu 9.10 en mi computador:
Un sony vaio vgn-nr130fe
Mobile Intel® 965 Express
1 gb de ram
120 gb de disco duro
un procesador intel dual core de 1.4 ghz

El problema surge cuando ocupo y el sistema y no me anda optimamente, cuando escucho musica, se queda pegado durante fracciones de segundo y lo mismo ocurre mientras abro ventanas o programas. ¿cual podria ser la causa? ¿aun tiene problemas mi tarjeta de video? y ¿tendra alguna solucion?

De verdad que me gusto mucho el sistema y estaria muy agradecido si tuviese algun tipo de solucion este problema.

Muchos saludos

---

### Post by Carlos C on 2009-11-02
Hola. Por favor recuerda publicar tus dudas en el subforo adecuado. He movido tu thread al subforo "Software". En caso de que no sepas dónde publicar debes mirar el [sticky]("http://ubuntuforums.org/showthread.php?t=1162708") que hemos dispuesto en cada subforo con el fin de solucionar esa duda. Por último te invito a que leas [aquí]("http://ubuntuforums.org/showthread.php?t=1162750").

Respecto a lo que te ocurre, una buena idea sería que cuando veas que el rendimiento del sistema no es el óptimo ejecutes en el terminal el comando "top". De esa forma podrás ver que proceso es el que exige más a tu sistema y así es posible ir encaminandonos a una solución. Te sugiero que uses Ubuntu sin ningún tipo de efecto gráfico, de esa forma puedes saber si el problema pasa por la aceleración gráfica.

Saludos.

---

### Post by moreback on 2009-11-02
Debieras ver qué proceso te está ocupando la CPU, por consola con top y gráficamente con el Monitor del sistema (en Sistema -> Administración). Ordena por tamaño en memoria o por uso de la CPU y verás quien es el causante.

También podría ser que los governadores de frecuencia de la CPU estén en OnDemand y tu sistema esté muy exigido. Para cambiarlo, agrega un applet al panel llamado Monitor de la frecuencia de la CPU. El que funciona mejor es el que dice Performance.

Saludos.

---

