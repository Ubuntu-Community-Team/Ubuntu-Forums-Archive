---
title: "[SOLVED] Motor gtk+ necesario"
date: 2008-12-01
forum: Software
---

### Post by Mauro22 on 2008-12-01
Hola!!


La verdad que instale varios motores gtk pero el error sigue (ver imagen adjunta, cuadro de Temas)...


Alguien sabe cual es??

Aclaro: Tengo el 8.10 32bits con Gnome.



PD: les dejo de fondo el songbird que me encanta como quedo :D

---

### Post by juanman on 2008-12-01
Como se llama el tema q te da error?

---

### Post by pol666 on 2008-12-01
mmm pero pareciera que andan a la perfeccion los temas

---

### Post by guisheca on 2008-12-01
A mi me pasa eso con algunos temas, pero cuando no aparece nada entre las comillas ("") me parece que se confunde nomas el ubuntu y el tema anda a la perfección. A mi me pasó con varios, por ejemplo con el Mac4Lin, pero funcionaba de 10.
No se que será.
Saludos.

---

### Post by sajnox on 2008-12-01
Te esta diciendo que el tema que elegiste no tiene algo que esta seteado por defecto. 

Ejemplo: Instalas un tema que no son solos los colores, sino que ademas trae un seteo para controles, iconos. Si no tenes instalado lo que el tema que bajaste tiene seteados te tira ese error. Entra a donde bajaste el tema y fijate si hace mencion a alguna "dependencia"

---

### Post by MeduZa on 2008-12-02
yo encontre un error en el archivo de theme que me generaba ese error
decia algo asi:


engine = "" 
y el error (me di cuenta por eso)
decia que el engine "" no estaba

---

### Post by Mauro22 on 2008-12-07
Gracias a todos!!


Aunque la 'advertencia' no se fue, el tema anda de lujo.... asi que marco como solved y a la bolsa.

):P

---

### Post by faktorqm on 2008-12-09
Yo tengo estos (ubuntu 8.04.1)

```

faktorqm@the-edge:~$ apt-cache search gtk-engines
gtk-engines-begtk - BeOS-like theme for GTK+
gtk-engines-eazel - The Eazel GTK+ theme engine, including the Crux theme
gtk-engines-geramik - Geramik GTK1.x Theme
gtk-engines-geramik-data - Geramik GTK Theme bitmaps
gtk-engines-lighthouseblue - LighthouseBlue theme for GTK+ 1.2
gtk-engines-mist - A flat theme for GTK+ 1.2
gtk-engines-mono - Mono theme for GTK+ 1.2
gtk-engines-qtpixmap - QtPixmap GTK1.x theming engine
gtk-engines-thingeramik - ThinGeramik GTK1.x Theme
gtk-engines-thingeramik-data - ThinGeramik GTK Theme bitmaps
gtk-engines-thinice - ThinIce theme for GTK+ 1.2
gtk-engines-xenophilia - Customisable GTK+ engine with a plain look
faktorqm@the-edge:~$ 
```

Alguno de todos esos es. Salu2!

---

