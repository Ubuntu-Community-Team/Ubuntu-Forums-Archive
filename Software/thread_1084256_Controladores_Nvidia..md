---
title: "Controladores Nvidia."
date: 2009-03-01
forum: Software
---

### Post by JUTGtgRB7z on 2009-03-01
He instalado los últimos controladores de Nvidia (tengo una GeForce 8400 GS) que no estaban en los repositorios (la versión 1.80) pero cada vez que se abre Xubuntu me aparece el gestor de controladores ¿A qué se debe esto? ¿Estan mal instalados mis controladores? Vale aclarar que esto también ocurría cuando tenía los que trae Ubuntu (la versión 1.77). Espero sus respuestas, gracias.;)

Aquí dejo un pantallazo de lo que me aparece cada vez que inicia.
[IMG]http://i437.photobucket.com/albums/qq94/pmzerdan/Screenshot.png[/IMG]

---

### Post by luks911 on 2009-03-02
Qué raro. Fijate en Sistema > Preferencias > Sesiones, en la pestaña Programas de inicio hay una entrada que es "Buscar nuevos controladores de hardware". Seleccionala, hacé click en Qué raro. Fijate en Sistema > Preferencias > Sesiones, en la pestaña editar y chequea que la línea en Orden sea:
```
jockey-gtk --check 60
```

Porque el comando jockey-gtk sólo, sin el resto, ejecuta el gestor de controladores. Si no es eso, fijate en el resto de las entradas de Programas de inicio que no haya ninguno con el comando jockey-gtk. Es lo único que se me ocurre a mí.

---

### Post by JUTGtgRB7z on 2009-03-03
> **luks911 said:**
> Qué raro. Fijate en Sistema > Preferencias > Sesiones, en la pestaña Programas de inicio hay una entrada que es "Buscar nuevos controladores de hardware". Seleccionala, hacé click en Qué raro. Fijate en Sistema > Preferencias > Sesiones, en la pestaña editar y chequea que la línea en Orden sea:
```
jockey-gtk --check 60
```

Porque el comando jockey-gtk sólo, sin el resto, ejecuta el gestor de controladores. Si no es eso, fijate en el resto de las entradas de Programas de inicio que no haya ninguno con el comando jockey-gtk. Es lo único que se me ocurre a mí.

Gracias. ;)

---

### Post by luks911 on 2009-03-03
Buenísmimo. De paso te hago una pregunta, traté de isntalar los drivers 180 (ahora tengo los 177) pero me econtré con un problema: al iniciar mientras carga gnome la pantalla se apaga y para volver tengo que ir a una consola (ctrl+alt+F1) y después volver al entorno gráfico con (ctrl+alt+F7). Sí, debería abrir un thread nuevo pero como veo que usas esa versión del driver.... igual no es grave.

Saludos

---

