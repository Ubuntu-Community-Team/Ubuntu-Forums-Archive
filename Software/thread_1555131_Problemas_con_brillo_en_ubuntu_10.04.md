---
title: "Problemas con brillo en ubuntu 10.04"
date: 2010-08-17
forum: Software
---

### Post by Panxoreka on 2010-08-17
hola a todos soy nuevo en el foro  y estube buscando si alguien ya habia preguntado esto, si lo habian preguntado pero no habia respuesta [-(, me encanta linux deseche windows , y he tenido a lo largo de este tiempo problemas con drivers configuraciones etc que he ido solucionando poco a poco , ahora tengo problemas con el brillo de la pantalla  siempre esta al 100% puse la mini aplicacion y muchas otras maneras encontradas gracias a la biblia google, pero no dan resultado si alguien sabe como arreglarlo  seria de bastante ayuda
mi note es un samsung np r430 con ubuntu 10.04

---

### Post by quitus on 2010-08-19
Hola, si la tarjeta gráfica es nvidia puedes usar las herramientas smartdimmer o nvclock 

# nvclock -S -10
para disminuir el brillo y +10 para aumentarlo, seguramente deberás instalarlo, pero está en los repositorios.

Ya sabes  

$ man nvclock 

para saber mas sobre el comando.

salut

---

