---
title: "Problema con temas graficos en GNOME + KDE"
date: 2009-05-07
forum: Software
---

### Post by majatu on 2009-05-07
Buenas gente, disculpen el titulo pero la verdad que no sabia como explicar en una frase mi problema, la cosa es así:

Tengo instalado Ubuntu 9.04 en la notebook y se me dio por instalarle el paquete kubuntu-desktop cosa de tener GNOME y KDE. Anda todo fantástico salvo que en KDE las ventanas no aparecen con el tema oxygen, ni cambian de apariencia si selecciono los temas manualmente (me deja seleccionar los temas que trae KDE por defecto, pero no cambian al aplicar los cambios), tengo desde que lo instale, el tema Clearlocks de Ubuntu y no se puede cambiar.

En la pc de escritorio tengo instalado igual GNOME y KDE y los temas andan fantásticos :?

Les dejo una imagen para que vean:
[[IMG]http://img119.imageshack.us/img119/3275/pantallazof.th.png[/IMG]](http://img119.imageshack.us/my.php?image=pantallazof.png)

Alguna idea de que puede estar pasando y como se soluciona? un saludo y muchas gracias!

---

### Post by Hei Ku on 2009-05-07
Asumo que reiniciaste KDE despues de cambiar los temas, no? A veces se hace el dificil cuando le cambias el motor de decorations.

---

### Post by guillermolisi on 2009-05-07
> **Hei Ku said:**
> Asumo que reiniciaste KDE despues de cambiar los temas, no? A veces se hace el dificil cuando le cambias el motor de decorations.
En KDE 3.5.10 hay cambios que requieren reiniciar KDE y sale el correspondiente aviso de que las modificaciones no seran aplicadas hasta que eso suceda. Supongo, porque aun no me meti con KDE 4, que mantuvieron el mismo criterio (con o sin aviso).

---

### Post by infernus92 on 2009-05-07
yo tengo un problema parecido... en GNOME, emerald no me carga los temas... selecciono uno, le doy doble click, se pone la ventana de emerald en gris, despues vuelva a color y nunca carga el tema que le digo...
que podra ser??

Saludos

---

### Post by sergiom99 on 2009-05-07
despues de aplicar los cambios, apreta 'CTRL+ALT+Backspace" para reiniciar el entorno grafico a ver que pasa.

---

### Post by infernus92 on 2009-05-07
trate de hacer eso... pero en JJ viene desactivado por defecto y no se como activarlo o hacerlo de otra forma

---

### Post by josecuervo86 on 2009-05-07
> **infernus92 said:**
> trate de hacer eso... pero en JJ viene desactivado por defecto y no se como activarlo o hacerlo de otra forma

Aca [0] tenes la solución a lo del Ctrl + Alt + Backspace

[0] [http://ubuntuforums.org/showthread.php?t=1141362]("http://ubuntuforums.org/showthread.php?t=1141362")

---

### Post by Hei Ku on 2009-05-07
Cerrá la sesión, y en el menú poné reiniciar servidor X. Es lo mismo que el Ctrl+Alt+Backspace, pero con un poco más de ternura. ;)

---

### Post by majatu on 2009-05-09
Intente lo que me dijeron y no pasa nada, es mas ahora que lo veo bien, cuando inicio sesión en KDE, los primeros segundos que kwallet me pide contraseña, esa ventanita aparece con el tema Oxigen, ahí nomas me parpadea la pantalla un segundo y se pone el tema Clearlocks :-? ni idea de por que pasa eso :(

---

### Post by staar on 2009-05-09
pregunta: en gnome, tenés algún script especial para inicar compiz, o tenés instalado el fusion-icon, y se inicia con la sesión? en gnome, usas emerald o metacity?

si mal no recuerdo, generalmente kde copia la carpeta autostart de gnome cuando se instala (creo que a /home/usuario/.kde4/Autostart), e inicia los mismos programas, incluso los que hayas desactivado en gnome, y me parece que alguno está ejecutando metacity --replace

fijate si es algo de eso...

saludos

---

### Post by majatu on 2009-05-10
Tenia habilitado un script para que me inicie Compiz porque mi video Intel esta blacklisted... y supuse que era eso, lo deshabilite y no paso nada...

Fui a /etc/init.d/ en donde guarde el script y lo cambie de directorio, reinicie y ahora andan bien los temas en KDE, lo único que me tengo que comer iniciar Compiz a mano desde el script pero bueno.

Muchas gracias a todos por sus respuestas! :)

---

