---
title: "Iniciar entorno gráfico desde la terminal"
date: 2011-05-02
forum: Software
---

### Post by FB91 on 2011-05-02
Hola, instalé Ubuntu 11.04 en mi netbook dell mini 10 usando el "gestor de actualizaciones". Una vez finalizado todo con éxito reinicio la PC y cuando ingresa al entorno gráfico solamente se me vé el fondo de pantalla. Es decir, puedo hacer click, click derecho, crear carpetas en el escritorio... es decir, puedo hacer cualquier cosa pero no se me ve la barra izquierda y superior del nuevo Unity.

Entonces lo que yo busco es loguearme desde la terminal al entorno gráfico pero sin usar Unity, usando el gnome2 común. Necesito hacerlo si o sí desde la consola porque cuando me muestra el listado de usuarios con cual iniciar no me muestra la opción de con cual entorno gráfico quiero ingresar.

Gracias por su ayuda ;)

---

### Post by granjero on 2011-05-03
hola FB91, creo que el comando es ```
startx
```

salud!

---

### Post by FB91 on 2011-05-03
> **granjero said:**
> hola FB91, creo que el comando es ```
startx
```salud!
y para hacer que inicie las X pero con el entorno gráfico que yo quiera? kde, gnome, unity?...

busqué en el **man startx** pero no encontré nada

---

### Post by eduavaz on 2011-05-05
Hola FB91, hice lo mismo en mi notebook y tuve el mismo problema y lo solucione asi:
El problema es que tenia activada compiz con el cubo de escritorio y esto en principio no es compatible con unity (auque lei que hay forma de activarlo).
reinicie  en modo reparacion que te permite iniciar una interfaz grafica limitada, inicie Administrador de opciones cpompizconf y en el item escritorio vi que el icono de unity estaba destildado. Destilde cubo de escritorio, tilde Desktop wall y Ubuntu unity plugin, me aparecieron carteles señalando conflictos, pulse resolver conflictos o desactivar los item que generaban estos conflictos segun corresponda y al reiniciar todo funciono normal.
Espero que esto te sirva
Saludos

---

