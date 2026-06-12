---
title: "Ajustar brillo Xubuntu 10.10"
date: 2011-04-18
forum: Software
---

### Post by Liv~ on 2011-04-18
Hola a todos.
Quería saber alguna forma para ajustar el brillo en Xubuntu Maverick? Más precisamente lo que quiero hacer es aumentarlo porque se ve bastante oscuro. Ya he probado con los botones desde el monitor, brillo y contraste están a 100% y sigue todo igual. Por eso quería saber si hay algún programa o alguna otra forma para poder configurar el brillo de la pantalla. El video es onboard.

Desde ya agradecida.

---

### Post by gmunioz on 2011-04-21
Para cambiar el brillo de la pantalla desde la consola debemos utilizar el comando xgamma
Abres una terminal y ejecutas:
xgamma -gamma 2.0
Esto le dará un brillo más intenso.
Para volver a la normalidad ejecutas:
xgamma -gamma 1.0
man xgamma
Y sabras todas sus opciones

---

### Post by Liv~ on 2011-04-22
Me re sirvió.
Agregué el comando al inicio seteado a mi gusto y, aparentemente, todo bien.

Muchísimas gracias por tu ayuda! :KS

---

### Post by papachan on 2011-04-22
Genial por el tip. es justo lo que buscaba, pero en mi caso estoy en una vaio, cuando instale Maverick  las teclas Fn+f5 y Fn+F6 contralaban el brillo perfectamente, y ahora no. Saben porque dejó de andar? Como uno hace si quisiera volver a ajustar el brillo desde las teclas? tienen informacion?

saludos ! maverick esta de 10 !

---

