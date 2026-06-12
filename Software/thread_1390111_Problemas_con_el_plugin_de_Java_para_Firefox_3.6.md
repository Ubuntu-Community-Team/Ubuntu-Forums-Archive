---
title: "Problemas con el plugin de Java para Firefox 3.6"
date: 2010-01-25
forum: Software
---

### Post by Red_Hood on 2010-01-25
Buenas gente, desde ya muchas gracias por prestarle atención a este mensaje.
Mi problema es el siguiente: en estos últimos días actualizé el Firefox 3.5.7 al nuevo 3.6 mediante Ubuntuzilla sin problema alguno. La cuestión está en que el plugin de Java no aparece instalado en el Firefox. Intenté instalarlo mediante el centro de software y bajarlo e instalarlo (siguiendo las instrucciones) por el sitio oficial de Java sin éxito alguno.
¿Alguién me puede ayudar para instalar el plugin de Java para Firefox 3.6?
Nuevamente, muchas gracias.
Saludos.

---

### Post by nanotube on 2010-01-25
hola

es un bug in sun-java6-plugin

aqui es un workaround:
[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Java_plugin_not_showing_up_.28on_Ubuntu_Karmic.29](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Java_plugin_not_showing_up_.28on_Ubuntu_Karmic.29)

---

### Post by Red_Hood on 2010-01-25
Muchas gracias por tu ayuda...
Lamentablemente sigue sin detectarme el plugin. Intenté agregarlo desde los agregados de Firefox y pasa lo siguiente. Lo instala (muy rápidamente) y me pide reiniciar el explorador. Lo reinicio, y el mismo explorador me arroja un cartel con la siguiente leyenda:

[I] "The Java Console extension is no longer supported and will be automatically removed the next time you restart Firefox.  This will not affect any Java applications or websites in any way.

Do you want to restart Firefox now?"[/I]

Vuelto a reiniciar Firefox, el mismo, sigue sin el plugin de Java...
De nuevo, muchas gracias...

---

### Post by jmarpu33 on 2010-01-26
La solución al problema de Java con el nuevo firefox está en [http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Java_plugin_not_showing_up_.28on_Ubuntu_Karmic.29](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Java_plugin_not_showing_up_.28on_Ubuntu_Karmic.29)

Se trata de asegurarse que tenemos instalado Java con
sudo apt-get install sun-java6-plugin

Y posteriormente escribir en el terminal lo siguiente:
sudo update-alternatives –install /usr/lib/mozilla/plugins/libjavaplugin.so mozilla-javaplugin.so /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so 50

Reiniciamos el navegador y listo.

---

