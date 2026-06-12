---
title: "Problema con la instalación de flash player 10"
date: 2009-09-01
forum: Software
---

### Post by pelaolinux on 2009-09-01
Hola !!! 
bueno mi problema es el siguiente: estaba buscando la manera para que los flash de las pagina incluyendo los videos no se vieran cortados, actualice el flash player a la versión de flash player 10 para ver si de esa manera alomejor podrían solucionarse todos mis problemas y asi poder ver  todas las animaciones y videos funcionaran correctamente en mi navegador, pero después de haber actualizado el flash player me encontré con un gran problema el cual es que no  se escuchan los sonidos de las animaciones swf en las paginas y tampoco los de los videos como en youtube, también e visto un montón de forma como resolver ese problema y todas dicen lo mismo y al final tengo 0 solución con ese problema y ahora quiero eliminar el flash player 10 y regresar al anterior que tenia instalado pero no se como puedo eliminar el paquete del flash player 10 . 

por favor ayuden a resolver ese problema  o  mejor digan como eliminar el flash player 10 para regresar a la versión anterior y seguir viendo una forma de arreglar el problema que tenia antes !! 

saludos !

---

### Post by josecardenasvejar on 2009-09-01
Hola!

Los primeros meses que empezé a utilizar ubuntu, me pasó lo mismo.

Lo que hice fué deshabilitar algunos complementos que venían instalado en firefox, y dejar solamente el flashplayer. 

Para desinstalarlo, desde la consola [COLOR=#009900][FONT=monospace]_sudo_[/FONT][/COLOR] apt-get remove flashplugin-nonfree

Atento a tus comentarios, saludos

---

### Post by pelaolinux on 2009-09-01
> **josecardenasvejar said:**
> Hola!

Los primeros meses que empezé a utilizar ubuntu, me pasó lo mismo.

Lo que hice fué deshabilitar algunos complementos que venían instalado en firefox, y dejar solamente el flashplayer. 

Para desinstalarlo, desde la consola [COLOR=#009900][FONT=monospace]_sudo_[/FONT][/COLOR] apt-get remove flashplugin-nonfree

Atento a tus comentarios, saludos


Hola josecardenasvejar y gracias por tu ayuda pero ya había solucionado el problema!! 
lo que ise fue lo siguiente :

desintale flashplayer 10 con el comando 

```
sudo apt-get remove --purge  adobe-flashpluguin
```

luego fui aver si haun se reproducían los video y supuestamente ya no tendrían que verlo echo por que elimine el flash y me di cuenta que todavía lo hacia y también los reproducía sin sonido en ese entonces entre seguir buscando cual paquete podría ser el problema y borre esto ingresando estos comando en el terminal : 

```
sudo apt-get remove --purge flashplugin-installer
```

```
sudo apt-get remove --purge swfdec-gnome

```
y ya no me reproducía nada y cumplí el objetivo de poder desactivar todas las animaciones de todo los que son los flash luego instale el paquete:

```
sudo apt-get install flashplugin-nonfree
```

y ese me instalo también el paquete flashplugin-installer y luego abri los 2 navegadores que utilizo que es el Opera y el Firefox y revise si al reproducir las animaciones en flash se escuchaba el sonidos y si a si fue, se escuchaban excelente de nuevo igual como antes pero haun sigo con el problema principal que se ven muy cortada las imágenes de los flash y ese es el problema q estoy tratando de solucionar nuevamente &#8230;.

saludos!:D

---

### Post by moreback on 2009-09-01
Lo de los videos cortados pueden ser algo relacionado con la aceleración de video, pero para eso mejor que inicies otro post y nos des detalles de tu tarjeta de video.

Saludos.

---

