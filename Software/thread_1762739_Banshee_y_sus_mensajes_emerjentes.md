---
title: "Banshee y sus mensajes emerjentes"
date: 2011-05-19
forum: Software
---

### Post by drazhe on 2011-05-19
Algo que odié siempre fueron los mensajes emergentes de **Rhythmbox**, y ahora con **Banshee** parece que volvieron...

[CENTER][IMG]http://s2.subirimagenes.com/imagen/previo/thump_6423362pantallazo.png[/IMG][/CENTER]

Alguno sabe donde esta la opción para que no me muestre el tema que estoy escuchando de manera tan intrusiva?

---

### Post by granjero on 2011-05-20
hola, hacé click derecho sobre el icono en el área de notificación. destildá mostrar notificaciones.

salud!

---

### Post by drazhe on 2011-05-21
> **granjero said:**
> hola, hacé click derecho sobre el icono en el área de notificación. destildá mostrar notificaciones.

salud!

y donde realmente está el icono en el área? porque cuando hago clic derecho en la zona donde aparece solo se despliega el menú del escritorio o de firefox o de libre office, dependiendo de que aplicación esté funcionando en ese momento...

---

### Post by granjero on 2011-05-21
ahí te cuelgo una imagen. yo lo tengo en 10.04 en 11.04 espero que sea igual.

salud.

---

### Post by drazhe on 2011-05-22
> **granjero said:**
> ahí te cuelgo una imagen. yo lo tengo en 10.04 en 11.04 espero que sea igual.

salud.

no che, no me aparece nada en esa zona... recuerdo que en Rhythmbox la opcion de hacer desaparecer los avisos emergentes estaba entre las opciones del **menú ver**, pero en banshee no hay nada parecido...

---

### Post by granjero on 2011-05-23
no se que decirte. ahí logré sacar una imagen del menú que te digo.

tratá de que te aparezca en el área de notificación el icono de banshee.

usas 11.04?

salud!

---

### Post by drazhe on 2011-05-24
No che, sigue sin aparecer el bendito ícono en el área de notificación, inclusive en las preferencias de banshee doy para forzar que dicho ícono aparezca y nada... 

[IMG][[IMG]http://img845.yfrog.com/img845/1217/pantallazope.png[/IMG]](http://yfrog.com/nhpantallazopep)[/IMG]


De cualquier manera, ya son varias las cosas que me están molestando de Ubuntu 11.04 y en cuanto tenga tiempo lo voy a hacer volar...

---

### Post by granjero on 2011-05-24
no te puedo decir nada más al respecto.... yo decidí saltar de LTS en LTS.

salud!

---

### Post by drazhe on 2011-05-25
> **granjero said:**
> no te puedo decir nada más al respecto.... yo decidí saltar de LTS en LTS.

salud!


jeje, es una buena idea eso de LTS a LTS, a mi me gusta probar de todo, hace varios meses atrás me fui a **Fedora** y estaba muy cómodo con ese SO, pero volví a **Ubuntu** para probar el nuevo concepto de **Unity** y todo eso, y la verdad que no fue una experiencia muy grata, es medio que se nota mucho que esta muy verde todo y muchas aplicaciones no se integran bien y finalmente termina siendo muy incomodo.... y repito, no es solo el tema de banshee... 

De cualquier manera, gracias por la ayuda brindaba hasta al momento, quizás para abril del año que viene me tengan de nuevo para probar en que anda **Ubuntu** por entonces...

---

### Post by granjero on 2011-05-29
fijate si en 11.04 es igual que acá.

alt+F2 gconf-editor

/apps > banshee > plugins > notification_area > destilar Show notifications.

salud!

---

### Post by igatjens on 2011-07-21
Yo encontré una solución para Ubuntu 11.04 natty, no muy elegante pero funciona, son muchos pasos pero es sencillo


[LIST=1]
[*]Cerrar la sesión de escritorio Unity
[*]Iniciar sesión de escritorio clásico (GNome 2)
[*]Abrir Banshee
[*]Ir a Editar>>Preferencias>>**Extensiones**
[*]En la categoría de **Herramientas**, marcamos **Icono en el área de notificación**
[*]Cerramos la ventana de Preferencias
[*]Salimos por completo de Banshee, use Ctrl+Q para asegurarse de que salio y no sólo se cerró la ventana
[*]Abrimos Banshee nuevamente y ahora aparecerá el icono de Banshee en el área de notificaciones como muestra granjero en el [_pantallazo_ ]("http://ubuntuforums.org/attachment.php?attachmentid=192983&d=1306166821")
[*]Damos clic derecho sobre el icono de Banshee y desmarcamos **Mostrar notificaciones**
[*]Cerramos sesión de escritorio clásico
[*]Iniciamos sesión de escritorio Unity y listo
[/LIST]

Banshee aún estará en el menú de sonido en el escritorio Unity y funcionara igual que antes pero sin notificaciones.

Saludos

---

