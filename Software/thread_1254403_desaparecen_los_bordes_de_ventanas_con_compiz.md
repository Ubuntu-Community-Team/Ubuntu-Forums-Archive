---
title: "desaparecen los bordes de ventanas con compiz"
date: 2009-08-31
forum: Software
---

### Post by rodrigo24 on 2009-08-31
como el título lo dice, cuando aplico los efectos de escritorio desaparecen los bordes de las ventanas.

He leido en varias páginas sobre este ptoblema, y he hecho lo siguiente:
- instalé Emerald
- agruegué a xorg 
Section "DRI"
Mode 0666
EndSection

- instalé el compiz icon y reinicié el windows manager

esas son todas las souluciones que aparecen en mi busqueda en googel, agradecería muchísimo si alguién pudiera 
ayudarme con este problema, ya que no tener los efectos de escritorio le quita un poco de brillo a mi escritorio.

muchas gracias.

---

### Post by moreback on 2009-08-31
Cuando no te aparecen los bordes de las ventanas significa que no te cargó el administrador de ventanas, lo cual se puede deber a que intentas activar compiz pero no tienes soporte para aceleración activado en tu tarjeta de video (estás usando un driver incorrecto) o puede ser por un error del mismo administrador de ventanas.

Indícanos el modelo de tu tarjeta de video con el comando **lspci** y te orientaremos en la solución.

Saludos.

---

### Post by nopersona on 2009-08-31
En el fusion icon seleccionaste metacity o emerald?

---

### Post by Carlos C on 2009-08-31
Movido a "Software".

---

### Post by rodrigo24 on 2009-08-31
el modelo de mi tarjeta de video es una NVidia Geforce MX400 64 mb

los drivers que tengo son los que me recomendó ubuntu.

activé emerald y también metacity.


no sé que otra solución hay exepto las clásicas que salen en internet :S

---

### Post by augias on 2009-09-01
prueba abriendo la opcion de "window decoration" en compizconfig-settings-manager. en la parte que dice "Command" debes poner /usr/bin/compiz-decorator. no te olvides activar esa opcion tambien. asi compiz sabe como decorar las ventanas. ojala eso te haya servido.
saludos

---

