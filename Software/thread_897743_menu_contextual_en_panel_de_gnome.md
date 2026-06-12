---
title: "menu contextual en panel de gnome"
date: 2008-08-22
forum: Software
---

### Post by mhoyos on 2008-08-22
buenas:

en el panel de gnome, y mas especificamente en la aplicacion "Lista de ventanas" , necesito restringir la ejecucion de las opciones que posee:

- minimizar
- maximizar
- redimensionar
- etc...

saque y elimine matacity y estoy utilizando sawfish como gestor de ventanas...

alguien me podria indicar, que o cual funcion debo cambiar para habilitar/deshabilitar la ejecucion de esas opciones ??... es porque necesito limitar algunas ventanas que el usuario no pueda modificar/cambiar/ejecutar...

desde ya, gracias..!!

---

### Post by mhoyos on 2008-08-26
alguna respuesta / guia / tips ?

Gracias..!!

---

### Post by firomero87 on 2011-01-27
Cuando doy clic derecho en el menu contextual del panel de gnome, no me sale todas las opciones del menu contextual, ¿como lo arreglo?

---

### Post by firomero87 on 2011-01-27
[CENTER][B]Ya sé como es



RECUPERAR LOS PANELES[/B][/CENTER]

Para esto debemos de utilizar una terminal y si resulta que no tenemos  los paneles desde donde abrir una, podemos pulsar las teclas ALT+F2 para  lanzar aplicaciones y escribimos:

[COLOR=#BF9000]gnome-terminal[/COLOR]

Y pulsamos ejecutar.

Una vez abierta la terminal ejecutamos los siguientes comandos, uno después de otro:

[COLOR=#BF9000]gconftool-2 --shutdown [/COLOR]

[COLOR=#BF9000]rm -rf ~/.gconf/apps/panel[/COLOR]

[COLOR=#BF9000]pkill gnome-panel[/COLOR]

Y listo paneles restaurados, igualitos a los que teníamos cuando instalamos Ubuntu.

[CENTER]**RECUPERAR ICONO DEL SONIDO**[/CENTER]

Si lo que quieres es sólo recuperar el icono del sonido, ve a  Sistema -  Preferencias - Aplicaciones de inicio, en el cuadro que se  abre, donde  dice orden, pones lo siguiente: [COLOR=#BF9000]gnone-volume-control-applet [/COLOR]
Y el icono volvera a aparecer en el lugar que le corresponde.


[CENTER]**RECUPERAR GNOME**[/CENTER]

Para restaurar **Gnome** a su estado original ejecuta en una terminal el siguiente comando:
[COLOR=#BF9000]gconftool-2 --recursive-unset /[/COLOR]

**Notas**:
1. esto volverá a configurar también la red y si es wifi debes de introducir de nuevo la contraseña.
2. esto os hará desaparecer los paneles y para recuperarlos utilizad el apartado de recuperar los paneles 


[CENTER]**RESTAURAR LA CONFIGURACIÓN POR DEFECTO DE COMPIZ**[/CENTER]

Para restaurar la configuración predeterminada de **compiz**:
[COLOR=#BF9000]gconftool-2 --recursive-unset /apps/compiz[/COLOR]

---

