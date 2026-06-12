---
title: "[HOW-TO] Modificar cómo se ve el Pidgin"
date: 2008-02-21
forum: Software
---

### Post by santiagoward2000 on 2008-02-21
Hola gente!
El otro día estaba aburrido y me puse a ver cómo editar el Pidgin. Voy a poner lo que encontré (es mi primer guía, tenganme paciencia)
Los ejemplos que puse son del mío. Los colores que elegí son para que combinen con el theme Glossy que yo uso. Por si quieren verlo es así:
**VER IMAGEN ADJUNTA**

**_Fondo y letras_**
Empecemos por cambiar el fondo del Pidgin. Supongo que no soy el único al que no le gusta tener el fondo blanco.
[LIST=1]
[*]Vamos a crear (si no está ya) un archivo ~/.gtkrc-2.0. En Ubuntu, abrimos una terminal y ponemos:
```
gedit ~/.gtkrc-2.0
```
En Xubuntu sería:
```
mousepad ~/.gtkrc-2.0
```
[*]Ahora escribimos los valores que queremos para el color de fondo, letras, imagen de fondo, etc.
Por ejemplo:
```
pixmap_path "~/"
style "my-blist" {
font_name = "Sans 10"
text[NORMAL] = "#000000"
bg[NORMAL] = "#DADFE4"
base[NORMAL] = "#DADFE4"
GtkTreeView::odd_row_color = ""
GtkTreeView::even_row_color = ""
}

```
Esto cambia el color de fondo y base (que la verdad no estoy seguro para qué está si el Pidgin no puede usar transparencias) a gris (#DADFE4) y las letras a negro (#000000). Pueden elegir los colores que quieran. También cambia las fuentes a Sans 10.
Si quieren usar una imagen en el fondo, solo hay que agregar abajo de **style "my-blist" {**:
```
bg_pixmap[NORMAL] = "~/imagen"
```
cambiando **~/imagen** por la dirección y nombre del archivo.


[*] Ahora hay que elegir a qué ventanas se lo aplicamos. Agregamos al archivo:
```
widget "*pidgin_blist_treeview" style "my-blist"
widget "*pidgin_conv_entry" style "my-blist"
widget "*pidgin_conv_imhtml" style "my-blist"
widget "*pidgin_log_imhtml" style "my-blist"
widget "*pidgin_request_imhtml" style "my-blist"
```
Esto hace que el estilo que hicimos antes se aplique a la lista de contactos, la ventana de conversaciones y el log.
[/LIST]

**_Íconos de Estado_**
Ya que había cambiado todos los colores para que haga juego con el theme Glossy, los íconos de estado verdes no quedaban, entonces también los edité.
Para eso vamos a abrirlos usando el GIMP (con sudo, ya que están en la carpeta /usr/share/pixmaps)
```
gksudo gimp /usr/share/pixmaps/pidgin/status/11/available.png
```
Acá podemos editar la imagen como queramos. Como me gustan las formas de los íconos de fábrica, lo único que hice fue usar **Colors/Colorify...** y elegir un azul, pero si quieren pueden dibujar algo, cambiar la forma, etc. Después guardamos.
Hay que repetir esto con todos los íconos que queramos modificar. También hay que cambiar los de otros tamaños, que están en las carpetas **11**, **16**, **22**, **32** y **48**, dentro de **usr/share/pixmaps/pidgin/status/**.
Traten de que los íconos para un mismo estado queden iguales, sino pueden ver un ícono en la lista de contactos y otro distinto en la conversación.

**_Tray_**
Cambiar el ícono de la bandeja es igual a cambiar los íconos de estado. Solo hay que editar los archivos que están en **/usr/share/pixmaps/pidgin/tray/**.
Como hicimos antes:
```
gksudo gimp /usr/share/pixmaps/pidgin/tray/16/tray-online.png
```
Lo editamos, guardamos, y repetimos con todos los íconos
(también los de las carpetas **22**, **32** y **48**)

Y ya está! (si no me olvidé nada ;))
Espero que les sirva. Cualquier duda pregunten!
Saludos!

PS: Por las dudas, para que los bordes de ventana se vean así uso un emerald theme que yo hice a partir de otro que encontré en gnome-look.org. Si tengo tiempo otro día hago una guía para eso! Si les interesa bajarlo o modificarlo, acá les dejo el link:
[http://gnome-look.org/content/show.php/Glossy+Emerald+Theme?content=75623]("http://gnome-look.org/content/show.php/Glossy+Emerald+Theme?content=75623")

---

### Post by leo_rockway on 2008-02-21
Ya no uso más Pidgin (uso Kopete) pero se agradece el [HOW-TO].

Ahora bien... ¿qué es ese contacto "Encarta"? :-S

---

### Post by pol666 on 2008-02-21
es un bot que "responde" lo que le preguntas usando como base de datos un plugin del michisoft encarta 


nunca hace nada y solo sirve para ******** cuando estas de malas xD

---

### Post by nemodot on 2008-02-21
Me encanta el tema glossy!

Junto con las letras de mejoradas queda espectacular.

Gracias por el tuto.

---

### Post by santiagoward2000 on 2008-02-22
> **nemodot said:**
> Me encanta el tema glossy!

Junto con las letras de mejoradas queda espectacular.

Gracias por el tuto.

De nada! :KS
Me alegro que te guste!

---

### Post by barx on 2008-10-30
Ahhh!! Exelente :D ahora podre personalizar Pidgin, pero

¿No hay una forma de ver mas grandes las imagenes para mostrar, display pictures o vatars?

Imganes muy pequeñas, eso es una crueldad para mis ojos . . . jeje. Y bueno, se que no van a poner imgagenes para redimensonar a la hora de verlas en conversación, que seria bueno, y exelente que se corriera la voz, pero de verdad, mientras

¿No hay una forma de cambiar en el .gtkrc-2.0 una forma de hacer la imagen de muestra de mis contactos mas grande? 

Mis ojos te lo agradecerán y yo también

---

### Post by santiagoward2000 on 2008-10-30
> **barx said:**
> Ahhh!! Exelente :D ahora podre personalizar Pidgin, pero

¿No hay una forma de ver mas grandes las imagenes para mostrar, display pictures o vatars?

Imganes muy pequeñas, eso es una crueldad para mis ojos . . . jeje. Y bueno, se que no van a poner imgagenes para redimensonar a la hora de verlas en conversación, que seria bueno, y exelente que se corriera la voz, pero de verdad, mientras

¿No hay una forma de cambiar en el .gtkrc-2.0 una forma de hacer la imagen de muestra de mis contactos mas grande? 

Mis ojos te lo agradecerán y yo también

Hola!
Hasta donde sé, no se puede. No creo que el .gtkrc-2.0 pueda manejar el tamaño de las imágenes. Perdón!
Saludos!

---

### Post by victor_nesta on 2008-10-30
Te mereces medallita.
En el ultimo por que en el primero no se puede

---

### Post by santiagoward2000 on 2008-10-30
GRACIAS! :) Me alegro que te haya gustado!

---

### Post by barx on 2008-11-07
Hola,pues el tutorial me sirvió hasta la versión anterior de Ubuntu la 8,04. Esta versión 8.10 ya vienen instalados  con todos los controladores para mi portatil.

Antes Si funcionaba lo de la imagen de fondo, de hecho llegue a defender a pidgin en algunos foros haciendo un toma de pantalla de como l decoré.

Pero ahora en no funciona y me encantaría ver otra vez mi pidgin decorado.

Dos cosas, 1:  

Si mi codigo esta mal dime

Codigo actual

pixmap_path "/home/barx/.purple/backgrounds"
style "my-blist" {
bg_pixmap[NORMAL] = "/home/barx/.purple/backgrounds/aurora.png"
text[NORMAL] = "#000000"
bg[NORMAL] = "#F5D8BC"
base[NORMAL] = "#F5D8BC"
GtkTreeView::odd_row_color = ""
GtkTreeView::even_row_color = ""
widget "*pidgin_blist_treeview" style "my-blist"
widget "*pidgin_conv_entry" style "my-blist"
widget "*pidgin_conv_imhtml" style "my-blist"
widget "*pidgin_log_imhtml" style "my-blist"
widget "*pidgin_request_imhtml" style "my-blist"
}

Codigo anterior(con el que funcionaba)

pixmap_path "~/"
style "my-blist" {
bg_pixmap[NORMAL] = "/home/barx/.purple/backgrounds/aurora.png"
text[NORMAL] = "#000000"
bg[NORMAL] = "#F5D8BC"
base[NORMAL] = "#F5D8BC"
GtkTreeView::odd_row_color = ""
GtkTreeView::even_row_color = ""
}
widget "*pidgin_blist_treeview" style "my-blist"
widget "*pidgin_conv_entry" style "my-blist"
widget "*pidgin_conv_imhtml" style "my-blist"
widget "*pidgin_log_imhtml" style "my-blist"
widget "*pidgin_request_imhtml" style "my-blist"


2: Con esta versión de Intrepid pidgin tiene un gtkrc2 sin punto en la carpeta de .purple . . ¿Lo borro?, le pongo punto, lo saco de esa carpeta¿

¿Qué me sugieres?
¿Buscar una versión anterior de pidgin?
La verdad es que me estaba empezando a gustar que tuviera fondo la lista de contactos, color diferente y esa nueva modalidad de agregar iconos perzonalizados por tu cuenta, que Pro'

De verdad, si te funciona en varias compus, hasta podemos hacer un tutorial xD, jaja

---

### Post by santiagoward2000 on 2008-11-08
> **barx said:**
> Hola,pues el tutorial me sirvió hasta la versión anterior de Ubuntu la 8,04. Esta versión 8.10 ya vienen instalados  con todos los controladores para mi portatil.

Antes Si funcionaba lo de la imagen de fondo, de hecho llegue a defender a pidgin en algunos foros haciendo un toma de pantalla de como l decoré.

Pero ahora en no funciona y me encantaría ver otra vez mi pidgin decorado.

Hola!
La verdad que todavía no tuve tiempo de ponerme a ver cómo está hecho en Intrepid. Pero recién me metí en la carpeta .purple y no tengo ningún gtkrc ahí.
Además, por lo que veo en tu código actual, creo que el { está mal puesto, porque así está incluyendo dentro del style a que ventanas lo aplicás. ¿Probaste ponerlo como antes para ver si anda?
Veo si mañana tengo tiempo para verlo (aunque según andan diciendo van a cortar la luz todo el día para arreglar no sé que... :()
Saludos!

---

### Post by c4d0rn4 on 2008-11-09
una pregunta, se le puede poner al fondo un poco de trasnparencia como en la consola?

---

### Post by santiagoward2000 on 2008-11-09
> **c4d0rn4 said:**
> una pregunta, se le puede poner al fondo un poco de trasnparencia como en la consola?

No, si querés hacer algo parecido tendrías que poner el wallpaper como fondo, pero transparencias reales, hasta donde yo sé no se puede.

---

### Post by santiagoward2000 on 2008-11-09
> **santiagoward2000 said:**
> Veo si mañana tengo tiempo para verlo (aunque según andan diciendo van a cortar la luz todo el día para arreglar no sé que... :()

SUSPENDIERON EL CORTE! :lolflag:
Como supongo que si no lo hacía barx se iba a poner re violento :confused:, hoy me puse a ver si andaba en Intrepid. Lo primero que hice fue copiar los archivos que había hecho para Hardy... y me anduvo todo... hasta el fondo...
Estuve pensando qué puede ser que esté mal en tu archivo. Lo primero que creo es lo que marqué antes, la posición del "}". ¿Probaste cambiarlo?
Sino, aunque supongo que esto debe estar bien, el archivo .gtkrc-2.0 tiene que estar en tu home, y no en .purple. Yo en .purple no tengo ningún gtkrc, supongo que podrías borrarlo (o por las dudas copiarlo en otro lado).
También, ¿el archivo aurora.png está donde dice tu archivo?
Para que veas si está todo bien, dejo mi código:
```
pixmap_path "~/"
style "my-blist" {
text[NORMAL] = "#000000"
bg[NORMAL] = "#C6C6C6"
base[NORMAL] = "#C6C6C6"
bg_pixmap[NORMAL] = "/.purple/backgrounds/background.png"
GtkTreeView::odd_row_color = ""
GtkTreeView::even_row_color = ""
}
widget "*pidgin_blist_treeview" style "my-blist"
widget "*pidgin_conv_entry" style "my-blist"
widget "*pidgin_conv_imhtml" style "my-blist"
widget "*pidgin_log_imhtml" style "my-blist"
widget "*pidgin_request_imhtml" style "my-blist"
```
Con esto me anda bien.
Espero que te sirva, si sigue sin andar avisá!
Saludos!

---

### Post by barx on 2009-06-01
Si, ya esta bien puse tal y como tienes el código, solo que extraño mi código anterior que podía cambiar el color de la conversación letras y fondo de diferente forma a como esta en la lista de contactos.

Por cierto al de transparente, Hay un screenlet para pidgin que si te deja tener la lista de contactos transparente.

A propósito, estaba viendo que el gtkrc-2.0 lo usan en otros escritorios para modificar muchas instancias, estoy investigando si hay alguna manera de ponerle imagen de fondo a la conversación, sería excelente.

por cierto asi es como tengo pidgin actualmente en la imagen

---

### Post by santiagoward2000 on 2009-06-01
Si querés tener colores distintos para la lista de contactos y las conversaciones, tenés que armar otro "style", y aplicarlo a la ventana que quieras, por ejemplo:
> pixmap_path "~/"
style "my-blist" {
text[NORMAL] = "#000000"
bg[NORMAL] = "#C6C6C6"
base[NORMAL] = "#C6C6C6"
bg_pixmap[NORMAL] = "/.purple/backgrounds/background.png"
}
style "my-conv" {
text[NORMAL] = "#FEFEFE"
bg[NORMAL] = "#C6C6C6"
base[NORMAL] = "#C6C6C6"
}
widget "*pidgin_blist_treeview" style "my-blist"
widget "*pidgin_conv_entry" style "my-conv"
widget "*pidgin_conv_imhtml" style "my-conv"
widget "*pidgin_log_imhtml" style "my-blist"
widget "*pidgin_request_imhtml" style "my-blist"

Ahí tendrías letras negras para los contactos y letras blancas para las conversaciones.

Lo de poner una imagen de fondo en las conversaciones, me parece que no se puede. Como está puesto en el primer post, estarías aplicando una imagen en las conversaciones también, pero no las toma.

El archivo .gtkrc-2.0 es como armar un tema GTK, solo que lo estás restringiendo a algunas ventanas en particular. Se puede hacer todo lo que hace cualquier tema, para cualquier ventana GTK. Yo por ejemplo ahora uso uno para poner un fondo en los paneles de Xfce (que no tienen la opción como los de GNOME).

Y yéndome un toque de tema, la idea de usar screenlets para esto no me gusta. La última vez que lo probé, la ventana de conversaciones era la normal (no sé si cambiaron esto), y yo prefiero que las ventanas estén un poco más "relacionadas". Pero es todo tema de gustos :)
Saludos!

---

### Post by barx on 2009-08-26
Jaja, perdon por las molestias. Acabo de recordar porque me sucedio.

Guarde la imagen que queria poner de fondo en dos formatos, JPG y PNG, la que tenia en JPG la borre, entonces se me hacia raro porque la imagen con PNG no se mostraba, Aunque ya después de lo que aconteció pude obtener algo de lo que queria y era no tener el fondo blanco en mis conversaciones, por lo menos de otro color.

Debo agradecer por la paciencia que se me ha tenido, y reconocer su gran esfuerzo.

Gracias.

Por cierto, ¿Creen que se pueda poner una imagen en el fondo de las conversaciones? (solo curiosidad, jeje)

---

### Post by santiagoward2000 on 2009-08-26
No te preocupes, no es molestia.
Acerca de la imagen de fondo en las conversaciones, creo que no se puede. El archivo, tal cual está arriba, le dice que use la misma imagen en las ventanas de conversaciones y contactos, pero igual no lo toma. Supongo que no se debe poder.
Saludos!

---

