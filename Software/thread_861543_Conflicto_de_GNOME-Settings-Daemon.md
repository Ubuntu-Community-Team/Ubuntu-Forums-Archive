---
title: "Conflicto de GNOME-Settings-Daemon"
date: 2008-07-16
forum: Software
---

### Post by wanchan on 2008-07-16
Hola comunidad, el problema es que no puedo instalar un tema de gnome, es el tema 56438-Aurora-1.4.tar.bz2, que lo baje de la pagina 
[http://www.gnome-look.org]("http://www.gnome-look.org")
Antes de que se ejecute el programa para instalar el tema me aparece el siguiente mensaje:

> No se puede iniciar el gestor de configuración «gnome-settings-daemon».
Si el gestor de configuración de GNOME no se está ejecutando, es posible que algunas de las preferencias no surtan efecto. Ésto puede ser el síntoma de un problema con Bonobo o que un gestor de configuración que no es de GNOME (por ejemplo KDE) ya esté activo y en conflicto con el gestor de configuración de GNOME.

Luego se ejecuta pero no puedo instalar el tema. No se que conflicto puede haber, ni que es Bonobo. Espero que alguine pueda darme una mano.

PD: Otra cosa, ultimamente el sistema se me cierra la sesion inesperadamente, por lo menos no me reinicia la pc, pero es muy molesto!!.
Alguien sabe porque?, no se si puede ser por algun virus, que no creo porque a linux no le afecta casi ningun virus (creo). 

Salu2!!

---

### Post by [P]oli on 2008-07-16
> **wanchan said:**
> Hola comunidad, el problema es que no puedo instalar un tema de gnome, es el tema 56438-Aurora-1.4.tar.bz2, que lo baje de la pagina 
[http://www.gnome-look.org]("http://www.gnome-look.org")
Antes de que se ejecute el programa para instalar el tema me aparece el siguiente mensaje:



Luego se ejecuta pero no puedo instalar el tema. No se que conflicto puede haber, ni que es Bonobo. Espero que alguine pueda darme una mano.

PD: Otra cosa, ultimamente el sistema se me cierra la sesion inesperadamente, por lo menos no me reinicia la pc, pero es muy molesto!!.
Alguien sabe porque?, no se si puede ser por algun virus, que no creo porque a linux no le afecta casi ningun virus (creo). 

Salu2!!

Puede ser que hayas actualizado el kernel? tenés instalado otro entorno gráfico? (KDE, E17 etc etc) y que se te cierra la sesión, es cuando navegás en firefox?

---

### Post by wanchan on 2008-07-16
Hola gracias por responder tan rapido.

Con actualizar el kernel te referis a que actualice de Ubuntu Gibbon a Hardy?, si eso te referis, si lo actualice a Hardy. Si no, hace poco actualice algo pero no me acuerdo jeje, pero no creo que haya sido el kernel.
 Uso GNOME de entorno grafico.
 Si cuando navego con firefox se me cierra sesion, pero sera problemas de firefox?, porque una vez no estaba navegando y lo mismo se me cerro.

Saludos!

---

### Post by [P]oli on 2008-07-16
> **wanchan said:**
> Hola gracias por responder tan rapido.

Con actualizar el kernel te referis a que actualice de Ubuntu Gibbon a Hardy?, si eso te referis, si lo actualice a Hardy. Si no, hace poco actualice algo pero no me acuerdo jeje, pero no creo que haya sido el kernel.
 Uso GNOME de entorno grafico.
 Si cuando navego con firefox se me cierra sesion, pero sera problemas de firefox?, porque una vez no estaba navegando y lo mismo se me cerro.

Saludos!

Me refiero actualizar el kernel, a las actualizaciones que dicen algo como "linux-headers 2.24-19" **(o algo similar)**, 
A mi se me cerraba la sesión cuando navegaba en firefox, por problemas con flash (las publicidades no cargaban o mandaban error y se cerraba la sesión). Probaste reiniciando? a ver si se soluciona

---

### Post by wanchan on 2008-07-16
Aaa mira me fije en Synaptic para ver las versiones del kernel y tengo estas instaladas:
linux-image-2.6.22-14-generic 2.6.22.14.46 (version instalada)
linux-image-2.6.24-16-generic 2.6.24.16.30 (version instalada)

La ultima version vendria a ser esta? 
   linux-image-2.6.22-14-generic 2.6.22.14.46
Puedo desinstalar sin drama la otra?

Ahora que me decis que puede existir problema con flash, hace poco instale Flashblock extension for Firefox. Sera eso el problema?

---

### Post by Mauro22 on 2008-07-16
Lo de Bonobo a mi me aparecia cuando tenia la fecha/hora mal configurada... 

Basta con poner en "automatico" y listo

---

### Post by wanchan on 2008-07-17
> **Mauro22 said:**
> Lo de Bonobo a mi me aparecia cuando tenia la fecha/hora mal configurada... 

Basta con poner en "automatico" y listo

La fecha y hora las tengo bine configuradas.
Ya pude instalar un Tema, solo habia que descomprimirlo jeje.
Pero de vez en cuando se me clava el sistema, anoche por ejemplo, no estaba navegando y se cabo por completo y tuve que reiniciarlo, la verdad no se porque pasa esto. Como puedo proceder cuando se me clave, ademas no me responde ni el mouse, se ancla totalmente.

Salu2!

---

### Post by [P]oli on 2008-07-17
> **wanchan said:**
> La fecha y hora las tengo bine configuradas.
Ya pude instalar un Tema, solo habia que descomprimirlo jeje.
Pero de vez en cuando se me clava el sistema, anoche por ejemplo, no estaba navegando y se cabo por completo y tuve que reiniciarlo, la verdad no se porque pasa esto. Como puedo proceder cuando se me clave, ademas no me responde ni el mouse, se ancla totalmente.

Salu2!

sólo para cuando no te acepta el Ctrl + Alt + Borrar, 

```

Ctrl + Alt + ImprPant (éstos 3 siempre apretados) mientras escribís **muy lento** R + E + I + S + U + B

```

Éstos son "atajos" de algunas operaciones que hace al apagar, y la **B** hace que se reinicie la pc totalmente ;)

Ésto es para no tener que apretar el famoso botón Reiniciar, siendo que se le puede forzar a Ubuntu a reiniciar.

---

### Post by Mister X on 2008-07-17
> **'[P]oli said:**
> sólo para cuando no te acepta el Ctrl + Alt + Borrar, 

```

Ctrl + Alt + ImprPant (éstos 3 siempre apretados) mientras escribís **muy lento** R + E + I + S + U + B

```

Éstos son "atajos" de algunas operaciones que hace al apagar, y la **B** hace que se reinicie la pc totalmente ;)

Ésto es para no tener que apretar el famoso botón Reiniciar, siendo que se le puede forzar a Ubuntu a reiniciar.

una pequeña correccion, la tecla CTRL no hay que presionarla, solamente Alt + ImprPant + la secuencia de letras

---

### Post by wanchan on 2008-07-17
> **'[P]oli said:**
> sólo para cuando no te acepta el Ctrl + Alt + Borrar, 

```

Ctrl + Alt + ImprPant (éstos 3 siempre apretados) mientras escribís **muy lento** R + E + I + S + U + B

```

Éstos son "atajos" de algunas operaciones que hace al apagar, y la **B** hace que se reinicie la pc totalmente ;)

Ésto es para no tener que apretar el famoso botón Reiniciar, siendo que se le puede forzar a Ubuntu a reiniciar.
Gracias por el dato.
ImprPant es Print Screen o Delete? En mi teclado no tengo la tecla "ImprPant".

---

### Post by [P]oli on 2008-07-17
> **wanchan said:**
> Gracias por el dato.
ImprPant es Print Screen o Delete? En mi teclado no tengo la tecla "ImprPant".

Es Print Screen ;)

> **Mister X said:**
> una pequeña correccion, la tecla CTRL no hay que presionarla, solamente Alt + ImprPant + la secuencia de letras

Gracias, no sabía eso :D

---

### Post by ramiro_md on 2008-09-26
Tengo un problema con eso del título cuándo arranca gnome :S, antes de cargar el escritorio (que por cierto tarda eternidades) aparece el cartel que adjunto más abajo.
EMpezo a aparecer depsués de agregar un script al inicio del sistema, pero ya lo saque y el problema sigue estando. TAmbién probe con añardarlio a sesiones y tampoco nada. Y con respecto a las actualizaciones de kernel no creo xq no actualizé en estos días.

---

### Post by WanderingKnight on 2008-09-27
Probá haciendo:

```
sudo /usr/X11R6/bin/gnome-settings-daemon start
```

y fijate qué te tira la consola.

Ojo que no tengo GNOME así que no sé si el path que te pasé es el correcto, pero es lo que encontré googleando (y los daemons de KDE también están alojados ahí).

---

### Post by ramiro_md on 2008-09-27
Gente, al parecer se solucionó. Después de haber reinstalado por enésima vez el gnome-setting-control dejó de aparecer el problema. :)

---

