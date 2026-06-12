---
title: "Ubuntu vs. Kubuntu"
date: 2011-06-22
forum: Software
---

### Post by aledruetta on 2011-06-22
Hola comunidad!

Instalé Ubuntu Maverick en una partición con la /home separada en otra. Por otro lado, dejé una tercera partición para instalar Kubuntu Natty. Finalmente, instalé Kubuntu en esa partición, pero con la /home apuntando a la misma partición que configuré como /home para Ubuntu Maverick. Utilicé el mismo usuario y la misma seña para las dos instalaciones.

Cuál es el problema? Que no puedo entrar a la sesión gráfica de Kubuntu Natty. Sí por terminal, pero no paso de la GDM en modo gráfico, siempre me vuelve a pedir el usuario y la seña.

Alguna idea?

Muchas gracias!

---

### Post by guillermolisi on 2011-06-23
Cuando ingresas vi consola, podes ver el contenido de /home/<tu_usuario> con un "ls -al" ?
Si lo ves, es el correcto, no ves nada raro respecto de permisos, owner y group de los archivos ?

---

### Post by aledruetta on 2011-06-24
> **guillermolisi said:**
> Cuando ingresas vi consola, podes ver el contenido de /home/<tu_usuario> con un "ls -al" ?
Si lo ves, es el correcto, no ves nada raro respecto de permisos, owner y group de los archivos ?

Gracias Guillermo.

Bueno, era algo mucho más simple, y lo descubrí de pura casualidad. En la pantalla de login hay que seleccionar la sesión que dice algo de "plasma" (ahora no recuerdo bien). Como viene por defecto no entra.

A alguien ya le pasó? Eso no es un bug? Supongo que la mayoría de los usuarios pensamos que vamos a entrar sin tener que seleccionar nada ahí, que es sólo poner el usuario y la contraseña...

---

### Post by guillermolisi on 2011-06-24
Si, seria solo eso siempre y cuando no tengas mas de un entorno grafico instalado.

Por ejemplo, con Ubuntu 11.04 tenes que seleccionar si queres usar Unity, Gnome o Unity2D (si lo instalaste).

En Lubuntu tambien tenes varias opciones para elegir que tipo de sesion grafica queres usar.

---

