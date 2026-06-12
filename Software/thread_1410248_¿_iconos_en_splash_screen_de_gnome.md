---
title: "¿ iconos en splash screen de gnome ?"
date: 2010-02-18
forum: Software
---

### Post by VonlisT on 2010-02-18
Saludos a todos.
Resulta que hace varios días he estado buscando como agregar los íconos de carga de los módulos a la imagen del splash screen de gnome. He visto que KDE lo trae por defecto y el motor se llama, si no me equivoco, ksplashx.
¿Existe la posibilidad de implementar esto en GNOME ?

---

### Post by CdK1 on 2010-02-18
Más fácil imposible...

[http://www.youtube.com/watch?v=VaY03SK_i60](http://www.youtube.com/watch?v=VaY03SK_i60)

---

### Post by VonlisT on 2010-02-18
> **CdK1 said:**
> Más fácil imposible...
[http://www.youtube.com/watch?v=VaY03SK_i60](http://www.youtube.com/watch?v=VaY03SK_i60)

Creo que me expliqué mal, no pretendo cambiar el boot screen, quiero cambiar el splash que sale después de logearse en GDM.
Algo como esto:
[http://www.youtube.com/watch?v=I6EnqV8qSCk](http://www.youtube.com/watch?v=I6EnqV8qSCk)
Pero claro, para GNOME. Activé el splash con gnome-splashscreen-manager, pero sólo muestra la imagen.

Saludos

---

### Post by CdK1 on 2010-02-19
Pues es casi lo mismo, tendrás que buscar un theme de splash y aplicarlo, si quieres poner iconos etc, deberías bajarte cualquier theme y ver como esta diseñado...

---

### Post by CdK1 on 2010-02-19
Y más fácil, debes activarlo;

gconf-editor /apps/gnome-session/options/show_splash_screen

---

### Post by RafaelG on 2010-02-19
Si lo que quieres es cambiar la Imagen del Splash de Ubuntu entonces te recomiendo leer este link:

[http://www.guia-ubuntu.org/index.php?title=Cambiar_imagen_splash_de_Ubuntu](http://www.guia-ubuntu.org/index.php?title=Cambiar_imagen_splash_de_Ubuntu)


Saludos Grandes.

---

