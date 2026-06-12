---
title: "Lubuntu, como compartir carpetas?"
date: 2010-05-29
forum: Software
---

### Post by harryscode on 2010-05-29
Buenos dias, desde ayer que estoy jugando con lubuntu lucid, linda distro, livianita y va muy bien en la pIII del laburo (nada exigente, necesito gnumeric y navegar). El problema es que no encuentro la forma de compartir carpetas.Vi en otro post que el problema lo habian solucionado instalando nautilus, cosa que hice pero no funciona. Puedo abrir la carpeta compartida que tengo en otra pc con ubuntu lucid, puedo abrir, pegar, borrar archivos, pero desde ubuntu no aparece esa pc en la red, obvio, si no comparto nada raro que aparezca. 
Si alguien que conozca como hacerlo, más que agradecido.

---

### Post by joseluis on 2010-05-29
ejecutá nautilus.
Luego, sobre la carpeta a compartir, verás que en el explorador pcpacman (asi se llama?), haciendo click derecho, aparece abrir con Nautilus, y ahi le das.

---

### Post by harryscode on 2010-05-29
A ver.. me debo haber expresado mal... quiero compartir una carpeta que tengo en Lubuntu, para poder verla en otra pc que tiene Ubuntu. En la pc con Lubuntu instale el nautilus, pero si le hago click derecho sobre la carpeta no hay ninguna opción que diga compartir como sí aparece en Ubuntu. Al no tener nada compartido en Lubuntu, obviamente no puedo verla en Ubuntu... tres triste tigres parece.. jaja.. Por lo que entendí joseluis ejecuto nautilus, abro el file manager (PCManFM) y sobre la carpeta que quiero compartir doy click derecho y tildo abrir con nautilus?.. eso me decis?

---

### Post by alfplayer on 2010-05-29
Haciendo una búsqueda rápida en la web me entero que esa funcionalidad de nautilus es provista por el paquete nautilus-share. Te recomiendo probar si aparece la opción para compartir carpetas después de instalar ese paquete.

---

### Post by harryscode on 2010-05-29
> **alfplayer said:**
> Haciendo una búsqueda rápida en la web me entero que esa funcionalidad de nautilus es provista por el paquete nautilus-share. Te recomiendo probar si aparece la opción para compartir carpetas después de instalar ese paquete.
Si.. eso tambien pensé yo.. lo instalé y sigue igual. Igual creo que el nautilus-share esta orientado más hacia samba, ¿no?. No es algo que no me deje dormir, puedo solucionarlo ya que puedo abrir una carpeta de la pc con Ubuntu y dejar los datos que quiero ahi... lo lindo seria que sea tanto de un lado como desde el otro. Seguiré investigando y toqueteando..

---

### Post by alfplayer on 2010-05-29
Para estar seguro que no funcionó habría que reiniciar la sesión.

Sí, nautilus-share usa Samba.

---

### Post by joseluis on 2010-05-29
imagino que instalaste samba no?

---

### Post by alfplayer on 2010-05-29
> **joseluis said:**
> imagino que instalaste samba no?

Con Ubuntu (ubuntu-desktop) nautilus-share pregunta si se quiere instalar Samba (si no está instalado).

---

### Post by harryscode on 2010-05-29
Mil perdones por mi burrada que voy a cometer.. pero si estamos hablando de dos sistemas linux... hace falta samba?... Tenia entendido que samba es para interacción entre linux y windows..:confused:

---

### Post by harryscode on 2010-05-29
Reiniciar!!!... contestar y poner como solved esto me da vergüenza... algo tan básico como reiniciar.. bueno.. todo en la vida uno no puede. Si, evidentemente hacia falta el nautilus-share y luego reiniciar. Después de eso aparece la opción de compartir la carpeta y desde ya se puede visualizar en la pc con ubuntu. Mil gracias a todos los que aportaron. Cuesta pero se aprende algo nuevo todos los dias.

---

### Post by alfplayer on 2010-05-29
Samba tiene cliente y servidor en linux, por eso se puede usar de linux a linux.

---

