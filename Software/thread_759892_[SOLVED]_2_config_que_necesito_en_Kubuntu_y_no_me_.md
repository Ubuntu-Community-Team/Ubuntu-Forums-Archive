---
title: "[SOLVED] 2 config que necesito en Kubuntu y no me salen"
date: 2008-04-19
forum: Software
---

### Post by sergiom99 on 2008-04-19
Hola gente,
estoy necesitando terminar de configurar 3 cosas q no puedo hacer andar en Kubuntu Gutsy y hasta ahora no tuve solucion. a saber:
1) Quiero usar la tecla Win izquierda para que funcione como "compose key" para tipear los caracteres castellanos que el teclado de la laptop no tiene. pude habilitarlo en  "K\Systems settings\Local\Keyboard-> Xkb options".
Pero si lo dejo asi, las teclas multimedia dejan de andar y solo vuelven a funcionar cuando lo deshabilito y reinicio X. 
Alguien sabe como activar el compose Key sin romper toda la configuracion multimedia? (Hacer andar las teclas me costo bastante)

2) Cada vez que apreto el boton  on/off del Synaptics Touchpad,aparece el  KDE Help Center. 
Alguna idea de donde cambiar la asociacion de teclas o en que archivo esta guardada para borrar la linea??

3) Tampoco pude hacer andar las teclas de brillo/contraste de la pantalla (Fn+F7/F8 ).

Gracias gente por sus comentarios.

---

### Post by valucha on 2008-04-19
[COLOR="DarkOrchid"]¿Qué notebook tenés? Me suena a que es una Toshiba por las teclas... bajate el toshutils algo asi del synaptics y otro paquete que empieza con tosh y a mi con eso me funcionan todas, todas las teclas de fn a la perfección (en una toshiba L35)

Sobre el otro problema, no sé :S pero fijate si esto te sirve:
[http://ubuntuforums.org/showthread.php?t=9962](http://ubuntuforums.org/showthread.php?t=9962)[/COLOR]

---

### Post by sergiom99 on 2008-04-19
valucha,
tengo una HP Pavilion DV6646us.

---

### Post by Hei Ku on 2008-04-19
La configuracion de las teclas la manejas desde Preferencias del Sistema/Teclado y raton/Accesos rapidos de teclado

De ultima, te podes instalar el keytouch, que te permite configurar mas atajos, y otras cosas que a veces con la configuracion del sistema no funcan

---

### Post by sergiom99 on 2008-04-20
Gracias Hei Ku,

> **Hei Ku said:**
> La configuracion de las teclas la manejas desde Preferencias del Sistema/Teclado y raton/Accesos rapidos de teclado
aca no encontre nada para des-asociar el boton del touchpad con Kde help center. Por eso queria saber en que archivo se guarda esto para sacar esa linea.

> 
De ultima, te podes instalar el keytouch, que te permite configurar mas atajos, y otras cosas que a veces con la configuracion del sistema no funcan
Lo habia instalado, pero tiene solo 5 teclados definidos para HP y son modelos viejos. tendria que armar el mio.

---

### Post by Hei Ku on 2008-04-20
Armarlo es muy facil. Yo lo hice para mi teclado, y en 10 minutos lo tenia andando. Eso siempre que las teclas generen un codigo reconocible para el kernel.
En mi caso, la perilla de zoom del MS Ergonomic no está todavia en el kernel de Gutsy.

---

### Post by sergiom99 on 2008-04-20
Gracias Hei Ku por tu ayuda.
estoy luchando con eso ahora. keytouch-editor me da un error al arrancar. dice que no encuentra el device.

y ahora encima CTRL+T me abre cualquier cosa menos una nueva solapa en firefox!!!

---

### Post by sergiom99 on 2008-06-08
Les cuento que está todo arreglado.
Para referencia futura y para cerrar el thread, cuento que paso.
1. Compose key:
agregué este código en mi xorg.conf
```
 Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
# agregado para tratar de usar LWIN como Compose Key -- 08/06/08
        Option         "XkbOptions" "compose:lwin"
EndSection

```
(calaste que ahora pongo los acentos papá! :-D)
Las teclas multimedia siguen funcionando!!

2 y 3. el botón del touchpad y las teclas Fn se arreglaron al instalar HH.

**PS:** Para los mas fanaticos: vieron esto? [http://en.andrenoel.com.br/2007/11/28/ubuntu-without-win-key/](http://en.andrenoel.com.br/2007/11/28/ubuntu-without-win-key/)
quien se anima, jaja.

---

