---
title: "Jaunty: Epiphany no funciona"
date: 2009-05-17
forum: Software
---

### Post by hernan blau on 2009-05-17
Amigos: Cuando abro este navegador aparece esta leyenda "El archivo «/usr/share/ubuntu-artwork/home/locales/index-C.html» no se ha encontrado."
¿Podrían indicarme por favor qué debo hacer? Gracias. HB.

---

### Post by staar on 2009-05-17
y no te funciona por eso? por que eso está indicando que no encuentra un html (supongo que será la página de inicio, generalmente guardada en el disco, con info sobre el navegador o el sistema)

me fijé, y en jaunty por lo menos, la carpeta locales no se llama así, se llama locales-ubuntu, y dentro está el index-C.html, para solucionarlo, podrías crear un enlace de esa carpeta a una que se llame locales, así:

- abrí nautilus como root, en una Terminal ```
sudo nautilus
``` OJO, después de hacer esto cerralo, no lo sigas usando, y no borres ni toques nada desde él, porque lo estas usando con permisos de administrador y podés romper algo...

- andá hasta la carpeta /usr/share/ubuntu-artwork/home/

- hacé click derecho sobre la carpeta 'locales-ubuntu' y seleccioná 'crear enlace'

- renombrá el enlace, para que se llame 'locales'

- cerrá, y probá si anda Epiphany...

saludos

---

### Post by hernan blau on 2009-05-17
Gracias. Hice todo lo que decís. Cuando quiero renombrar el enlace para que se llame "locales" me dice que no es posible porque ya existe una carpeta con ese nombre. Cordialmente, HB.

---

### Post by Mauro22 on 2009-05-17
Crea un archivo vacio y fijate que onda.

```
sudo touch /usr/share/ubuntu-artwork/home/locales/index-C.html
```

---

### Post by staar on 2009-05-17
que raro, me fijé mejor, y si, yo también ya tengo un archivo llamado locales, es un enlace que lleva a /etc/alternatives/firefox-homepage-locales y este, a su vez, también es un enlace que lleva a /usr/share/ubuntu-artwork/home/locales-ubuntu, osea la carpeta correcta, donde está index-C.html...

por casualidad, no habrás desinstalado firefox? eso explicaría que ya no exista el /etc/alternatives/firefox-homepage-locales al que redirige /usr/share/ubuntu-artwork/home/locales, y nunca podrías llegar a /usr/share/ubuntu-artwork/home/locales-ubuntu, donde está el html...

mi sugerencia es que, el enlace que creaste, lo muevas a /etc/alternatives y lo renombres como firefox-homepage-locales, para que Epiphany pueda encontrar el html...

saludos

---

### Post by pablo.s on 2009-05-17
Tiene que reinstalar el
paquete ubuntu-artwork.

---

