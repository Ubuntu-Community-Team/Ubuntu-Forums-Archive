---
title: "No escucho los sonidos de inicio y otros en lucid"
date: 2010-10-15
forum: Software
---

### Post by asterix77 on 2010-10-15
Hace unos meses atrás cambié mi sonido de inicio siguiendo el siguiente tutorial, me funcionó a la perfección.

Pero a partir de algunos días atrás, he dejado de escucharlo, y no tan solo el sonido de inicio, sino también el sonido de advertencia, de error, etc del sistema (¿alguna actualización tal vez?).

No tengo problemas de sonido de videos, mp3, wma, etc.

[http://irvingprog.wordpress.com/2010/06/26/cambiar-sonido-de-inicio-a-ubuntutambores/#respond](http://irvingprog.wordpress.com/2010/06/26/cambiar-sonido-de-inicio-a-ubuntutambores/#respond)

Agradecería que me pudieran ayudar con esto.


Saludos

---

### Post by moreback on 2010-10-15
Supongo que revisaste las Preferencias de sonido (Sistema -> Preferencias -> Control de volumen). En la primera pestaña "Efectos de sonido" aparece el volumen y la selección del tema. Verifica que estén bien seleccionados y a un volumen que lo puedas escuchar.

---

### Post by moreback on 2010-10-16
Revisa también en **Sistema -> Preferencias -> Aplicaciones al inicio** y busca una entrada que dice **GNOME Login Sound**. Ésta tiene el siguiente comando

```
/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"
```

Saludos.

---

### Post by asterix77 on 2010-10-16
Que manera de calentarme la cabeza por algo tan sencillo. Era cosa de poder realizar lo que me comentastes en tu primer post.


Gracias Moreback y saludos

---

### Post by moreback on 2010-10-16
:)

---

