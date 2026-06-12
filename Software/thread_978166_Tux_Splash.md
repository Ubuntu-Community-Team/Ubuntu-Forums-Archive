---
title: "Tux Splash"
date: 2008-11-10
forum: Software
---

### Post by vk-cdg on 2008-11-10
Tengo un pequeño problema que me preocupa mas que nada por no saber como pasó, mas que por el problema en si.

Al encender el equipo, luego de elegir la opción correspondiente en el grub, donde debería aparecer el usplash de Ubuntu (con la barrita naranja creciente) aparece un Tux con un fondo celestón y una barra naranja en la parte inferior de la pantalla.
No se como apareció, ya que no instalé nada relacionado con el usplash!

Como decía mas arriba, no me preocupa demasiado ya que la PC anda, y en unos días (parciales de por medio) voy a instalar Intrepid, pero no se como apareció esto ahí.

Tampoco pude reestablecer el original.

Si alguien puede tirarme una línea se lo agradezco.

---

### Post by rojojuan on 2008-11-11
> **vk-cdg said:**
> Tengo un pequeño problema que me preocupa mas que nada por no saber como pasó, mas que por el problema en si.

Al encender el equipo, luego de elegir la opción correspondiente en el grub, donde debería aparecer el usplash de Ubuntu (con la barrita naranja creciente) aparece un Tux con un fondo celestón y una barra naranja en la parte inferior de la pantalla.
No se como apareció, ya que no instalé nada relacionado con el usplash!

Como decía mas arriba, no me preocupa demasiado ya que la PC anda, y en unos días (parciales de por medio) voy a instalar Intrepid, pero no se como apareció esto ahí.

Tampoco pude reestablecer el original.

Si alguien puede tirarme una línea se lo agradezco.


Te dejo este link por si te puede servir:
[http://www.ubuntu-es.org/index.php?q=node/2938](http://www.ubuntu-es.org/index.php?q=node/2938)

---

### Post by rojojuan on 2008-11-11
También podés hacerlo entrando por Sistema - Administración - Ventana de Entrada

---

### Post by vk-cdg on 2008-11-11
Naaaa, decime que me estás gastando ¿desde Ventana de Entrada se puede?
Mirá que revolví todos los menúes pero jamás se me hubiera ocurrido que estaba ahí. Toqué con startup manager y nada, no se arregla.

Lo miro y las cuento!

---

### Post by rojojuan on 2008-11-11
> **vk-cdg said:**
> Naaaa, decime que me estás gastando ¿desde Ventana de Entrada se puede?
Mirá que revolví todos los menúes pero jamás se me hubiera ocurrido que estaba ahí. Toqué con startup manager y nada, no se arregla.

Lo miro y las cuento!

En ventana de entrada estan todas las opciones para cuando ingresas el usuario y pass. 
Podés cambiar esa ventana completamente, que funcionen los temas aleatoriamente, cambiar sonido, etc.
Nunca tuve ni tengo el propósito de gastar a nadie, especialmente en el foro por el respeto que le tengo a todos. 
Para mi es muy valorable la actitud que hay aquí, todos tratan de ayudar, cada uno dentro de sus posibilidades (aclaro que las mías son muy pocas).

---

### Post by rojojuan on 2008-11-11
También encontré este link, que te explica todo lo que podés hacer con splash.

[http://www.guia-ubuntu.org/index.php?title=Cambiar_imagen_splash_de_Ubuntu#Gnome_Splash_Screen_Manager](http://www.guia-ubuntu.org/index.php?title=Cambiar_imagen_splash_de_Ubuntu#Gnome_Splash_Screen_Manager)

---

### Post by luks911 on 2008-11-11
> **rojojuan said:**
> En ventana de entrada estan todas las opciones para cuando ingresas el usuario y pass. 
Podés cambiar esa ventana completamente, que funcionen los temas aleatoriamente, cambiar sonido, etc.
Nunca tuve ni tengo el propósito de gastar a nadie, especialmente en el foro por el respeto que le tengo a todos. 
Para mi es muy valorable la actitud que hay aquí, todos tratan de ayudar, cada uno dentro de sus posibilidades (aclaro que las mías son muy pocas).

Una duda: ¿el splash no es la imagen que se ve durante la carga de sistema y que tiene una barra que se va llenando? Porque si es así, desde Ventana de entrada me parece que lo que se puede modificare es la pantalla de login, que es posterior al splah. 
¿O estoy diciendo huevadas?
Aunque si estoy en lo cierto sí sirve lo que pasás de la Guía Ubuntu. De hecho está bueno lo de gconf. Yo suelo usar el Startup manager pero voy a probar esto otro. Y ahora tengo otra duda: el Startup manager para cambiar el splash me pedía (lo hice una sola vez) un archivo .so, pero con este otro sistema necesito un .png y además veo en Gnome-art que los que hay para bajar en efecto son png :confused:
Bueh, más tarde con mi Ubuntu lo pruebo.

Saludos

---

### Post by staar on 2008-11-11
> **luks911 said:**
> Una duda: ¿el splash no es la imagen que se ve durante la carga de sistema y que tiene una barra que se va llenando? Porque si es así, desde Ventana de entrada me parece que lo que se puede modificare es la pantalla de login, que es posterior al splah. 
¿O estoy diciendo huevadas?
Aunque si estoy en lo cierto sí sirve lo que pasás de la Guía Ubuntu. De hecho está bueno lo de gconf. Yo suelo usar el Startup manager pero voy a probar esto otro. Y ahora tengo otra duda: el Startup manager para cambiar el splash me pedía (lo hice una sola vez) un archivo .so, pero con este otro sistema necesito un .png y además veo en Gnome-art que los que hay para bajar en efecto son png :confused:
Bueh, más tarde con mi Ubuntu lo pruebo.

Saludos

tienen nombres parecidos pero no son lo mismo, el usplash es el que va despues del grub, el de la barrita que carga, ese se cambia desde el startup manager, y tienen extension .so, el splash screen es el otro, que aparece, si lo tenes activado, despues del login, que son imagenes png, y que se puede cambiar de varias formas, con el gconf-editor, con el ubuntu-tweak o copiandola a /usr/share/pixmaps/splash

saludos

---

### Post by luks911 on 2008-11-11
Listo. Dudas aclaradas, muchas gracias.

---

### Post by vk-cdg on 2008-11-12
> **luks911 said:**
> Una duda: ¿el splash no es la imagen que se ve durante la carga de sistema y que tiene una barra que se va llenando? Porque si es así, desde Ventana de entrada me parece que lo que se puede modificare es la pantalla de login, que es posterior al splah. 
¿O estoy diciendo huevadas?
Aunque si estoy en lo cierto sí sirve lo que pasás de la Guía Ubuntu. De hecho está bueno lo de gconf. Yo suelo usar el Startup manager pero voy a probar esto otro. Y ahora tengo otra duda: el Startup manager para cambiar el splash me pedía (lo hice una sola vez) un archivo .so, pero con este otro sistema necesito un .png y además veo en Gnome-art que los que hay para bajar en efecto son png :confused:
Bueh, más tarde con mi Ubuntu lo pruebo.

Saludos

Exacto, es la pantalla negra con la barrita naranja que se va llanando. Por eso me extraño, pero como todavía estoy en franco aprendizaje sobre ubuntu, no lo descarté y lo agendé para verlo el Domingo.

Como mencionás vos, probé con el StratUp Manager, el cual me pide un .so como bien decís, pero no hubo caso, no actualiza nada.

---

### Post by vk-cdg on 2008-11-12
Mi problema es definitivamente con el Usplash

---

### Post by santiagoward2000 on 2008-11-12
> **vk-cdg said:**
> Como mencionás vos, probé con el StratUp Manager, el cual me pide un .so como bien decís, pero no hubo caso, no actualiza nada.

Hola!
Que loco que se haya cambiado así de golpe! Pregunta: ¿que te aparece en **Upslash theme** en el Startup Manager, abajo de Appearance?
Saludos!

---

### Post by luks911 on 2008-11-12
> **vk-cdg said:**
> Exacto, es la pantalla negra con la barrita naranja que se va llanando. Por eso me extraño, pero como todavía estoy en franco aprendizaje sobre ubuntu, no lo descarté y lo agendé para verlo el Domingo.

Como mencionás vos, probé con el StratUp Manager, el cual me pide un .so como bien decís, pero no hubo caso, no actualiza nada.

Cuando tenía Hardy lo había cambiado con el Startup Manager. Pero al actualizar a Intrepid noté, ahora lo recuerdo, que el nuevo usplash había desaparecido y sólo veía la terminal. Luego tuve que reinstalar y sí veía el usplash pero, claro, el original. 
Ayer traté de cambiarlo y no pude. Veía unas imágenes de colores que me hicieron acordar a la señal de ajuste de la tele. 
Y en [este]("http://www.ubuntugeek.com/how-to-change-the-bootsplash-in-ubuntu-810-intrepid-ibex.html")[0] post de Ubuntu Geek se habla de un bug que no permite el cambio y cómo solucionarlo. Todavía no lo probé y no sé si es lo que me pasó a mí. Habría que meter un poquito de mano...


[0] [http://www.ubuntugeek.com/how-to-change-the-bootsplash-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-change-the-bootsplash-in-ubuntu-810-intrepid-ibex.html)

---

### Post by staar on 2008-11-12
> **luks911 said:**
> Cuando tenía Hardy lo había cambiado con el Startup Manager. Pero al actualizar a Intrepid noté, ahora lo recuerdo, que el nuevo usplash había desaparecido y sólo veía la terminal. Luego tuve que reinstalar y sí veía el usplash pero, claro, el original. 
Ayer traté de cambiarlo y no pude. Veía unas imágenes de colores que me hicieron acordar a la señal de ajuste de la tele. 
Y en [este]("http://www.ubuntugeek.com/how-to-change-the-bootsplash-in-ubuntu-810-intrepid-ibex.html")[0] post de Ubuntu Geek se habla de un bug que no permite el cambio y cómo solucionarlo. Todavía no lo probé y no sé si es lo que me pasó a mí. Habría que meter un poquito de mano...


[0] [http://www.ubuntugeek.com/how-to-change-the-bootsplash-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-change-the-bootsplash-in-ubuntu-810-intrepid-ibex.html)

lo que pasa es que en intrepid no funcionan los usplash para hardy, al parecer hay que buscar alguno que incluya el source y compilarlo a mano :(, en este [_post_]("http://tennessee.ubuntuforums.com/showthread.php?t=960221"), hablan del tema
fijate que la solucion que pusiste lo que hacen es desinstalar usplash y poner el splashy

saludos

---

### Post by luks911 on 2008-11-12
> **staar said:**
> lo que pasa es que en intrepid no funcionan los usplash para hardy, al parecer hay que buscar alguno que incluya el source y compilarlo a mano :(, en este [_post_]("http://tennessee.ubuntuforums.com/showthread.php?t=960221"), hablan del tema
fijate que la solucion que pusiste lo que hacen es desinstalar usplash y poner el splashy

saludos

Ajá, veo, veo... para eso eran las fuentes incluidas en el qu eme bajé de Gnome-look. A compilar, entonces.
Y sí, había visto que desinstalaba usplash lo que pasé. Creía que después se podía reemplazar el archivo .so de la misma forma. Pero como no lo probé...

Gracias

---

### Post by luks911 on 2008-11-12
Por si hace falta confirmación, probé compilar el usplash que me había bajado y funcionó de maravilla. La cuestión es conseguirse uno que tenga las fuentes (¿está bien dicho o sería código fuente?).

Saludos

---

### Post by vk-cdg on 2008-11-13
> **santiagoward2000 said:**
> Hola!
Que loco que se haya cambiado así de golpe! Pregunta: ¿que te aparece en **Upslash theme** en el Startup Manager, abajo de Appearance?
Saludos!

Me aparece la opción default, no la puedo quitar ni actualizar.

Traté de hacer el mismo procedimiento que hice en la notebook (puse el original pero wide) copiando el archivo .so (instrucciones de un blog) y en la desktop no tuve suerte.

Como dije en el post original, no me preocupa demasiado porque en unos días haré un fresh install de Intrepid, pero me preocupa saber por que pasó.

---

### Post by vk-cdg on 2008-11-13
> **staar said:**
> lo que pasa es que en intrepid no funcionan los usplash para hardy, al parecer hay que buscar alguno que incluya el source y compilarlo a mano :(, en este [_post_]("http://tennessee.ubuntuforums.com/showthread.php?t=960221"), hablan del tema
fijate que la solucion que pusiste lo que hacen es desinstalar usplash y poner el splashy

saludos

Mmmmmm.... creo saber que fue lo que pasó!
Hace un par de semanas instalé splashy para ver que era. Después nunca mas lo toque. 
La PC la reinició mi señora para entrar en el ventanuco así que yo no vi como se apagó y como estoy con parciales hacía unos días que no la tocaba.
El splashy debe haber cambiado el usplash original de Ubuntu.

---

