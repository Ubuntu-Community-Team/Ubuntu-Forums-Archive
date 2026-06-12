---
title: "Solicitar contraseña de root?"
date: 2010-11-11
forum: Software
---

### Post by asterix77 on 2010-11-11
En varias oportunidades he querido realizar alguna acción que implica hacer algún cambio al sistema (en forma gráfica), pero me aparece un cuadro de diálogo donde se pide la contraseña de root. Como muestra les dejo la siguiente imagen

[http://img440.imageshack.us/img440/3356/rootu.png](http://img440.imageshack.us/img440/3356/rootu.png).


Mi sistema no cuenta con una cuenta de root por lo que al ingresar mi contraseña de superusuario no lo reconoce, por lo que no puedo realizar la acción, como en este caso agregar un usuario a un grupo.

Sé que puedo hacerlo por consola, pero ya que está la forma gráfica de hacerlo, debiera poder hacerse sin mayores problemas.


la pregunta entonces es ¿será necesario hacerse de una cuenta de root?


Saludos

---

### Post by Oscaroto on 2010-11-12
asterix77:

La cuenta root viene creada por defecto, es necesario en todo ubuntu y siempre existe, sin embargo, para poder hacer cosas con esta cuenta debes darle una contraseña, esto lo haces por consolacon el comando:

sudo passwd root

te pedirá la contraseña dos veces.

Luego para acceder a la cuenta, debes hacerlo en un terminal con el comando 

su

y te pedira la contraseña root

luego podrás hacer todo con esta cuenta en el terminal.

si quieres una forma gráfica de hacer cosa con la cuenta, luego de hacer el comando su, haz:

nautilus en consola para abrir esta aplicacion con permisos root.

---

### Post by moreback on 2010-11-12
Que extraño que te pida contraseña de root siendo que una instalación estandar de Ubuntu no te pide contraseña para root (y de hecho éste queda sin) y usa sudo o gksu para autentificar.

Creo que sólo basta con ingresar la contraseña de tu usuario normal.

Saludos.

---

### Post by asterix77 on 2010-11-13
Si, es extraño. En otras versiones de ubuntu podia hacer todo con la contraseña de sudo. Pero acá hay varias cosas que me pide la contraseña de root. Por ejemplo cuando quiero instalar una impresora. Opté fialmente por colocarle una contraseña a root.


Saludos.

---

