---
title: "Cosas sobre apariencia"
date: 2008-02-20
forum: Software
---

### Post by faktorqm on 2008-02-20
Hola a todos, queria saber 2 cosas por ahora:

1) Donde dice Aplicaciones Lugares Sistema, y tiene un logo de ubuntu, ¿Cómo hago para cambiar todo eso? En lugar del logo, quiero que aparezca el logo de ubuntu-ar, y Aplicaciones que se llame "Appz" o que no aparezca, que se aprete directamente el logo y salga el menu.

2) En la pantalla de login, yo instale una que me gustaba a mi, y lo que me paso de malo es que donde escribo el nombre de usuario me aparece muy chiquito, y los redondelitos de la contraseña tambien, estaria copado que me aparezcan mas grandes. ¿De donde se cambia el tamaño?

Desde ya muchas gracias a todos. salu2!!

---

### Post by ubuntu27 on 2008-02-20
Respuesta al numero 1.

1) EL dibujo debe de ser en "svg" (no jpeg o bmp u otros).
2) Debe de ser llamado "start-here.svg"

Anda a menu Sistema, Preferencias, Theme (tema?), y luego has click en el tab "Iconos". Observa donde estan guardados los iconos.
 
Ahora pon el archivo svg a uno de los siguientes directorios (que te mostro en el "iconos en el paso anterior). 


/scalable/places
/usr/share/icons/
~/.icons/

Para ser claro, cada theme al parecer utiliza distintos directorios donde guardan los iconos. para eso digo que revises el Theme.

Si estas usando el "Human" theme (tema), entonces tienes que poner el icono en 
/usr/share/icons/Human/scalable/places/

Cuando ayas termindo, reicinia la barra de GNOME con el siguiente comando

```
killall gnome-panel
```

---

### Post by pol666 on 2008-02-20
mmm yo lo cambio desde (archivos ocultos)

home/usuario/.icons/places/


hay dos archivos, rempalaza uno start-here 

y automaticamente remplaza el otro a mi me funciona asi.

Es .png

podes ponerle cualquier cosa:)

---

### Post by User21 on 2008-02-20
Si eliminas el APPLET ese de Aplicaciones/Menu/Apariencia del panel , podes agregar otro que se llama MENÚ PRINCIPAL, y es un ÚNICO ICONO que al darle clic se despliegan todos los menúes !

---

### Post by leo_rockway on 2008-02-20
> **User21 said:**
> Si eliminas el APPLET ese de Aplicaciones/Menu/Apariencia del panel , podes agregar otro que se llama MENÚ PRINCIPAL, y es un ÚNICO ICONO que al darle clic se despliegan todos los menúes !

<troll>Como el K menu? Que inventaran despues?</troll>
:lolflag:

---

### Post by luisito on 2008-02-20
Veo que te respondieron bastante tus preguntas. Yo solo queria agregar una cosa.

Vamos Estudiantes!!!!

---

### Post by User21 on 2008-02-21
> **luisito said:**
> Veo que te respondieron bastante tus preguntas. Yo solo queria agregar una cosa.

Vamos Estudiantes!!!!
o_O?????


:-k

---

### Post by niko_3100 on 2008-02-21
Eso que dice user21 es asi, se llama main menu o menu principal y trate todo metido ahi adentro pero bien organizado, yo lo uso asi y con un solo panel, el de abajo el de arriba lo vole y se ve todo mas grande mejor para leer y no hacer tanto scroll.

---

### Post by spg76 on 2008-02-21
> **faktorqm said:**
> 
2) En la pantalla de login, yo instale una que me gustaba a mi, y lo que me paso de malo es que donde escribo el nombre de usuario me aparece muy chiquito, y los redondelitos de la contraseña tambien, estaria copado que me aparezcan mas grandes. ¿De donde se cambia el tamaño

Para cambiar el tamaño de la fuente en la pantalla de login, tenes que editar el archivo /etc/gdm/gdm.conf
Abrilo con:
```
sudo gedit /etc/gdm/gdm.conf
```
Busca la parte donde dice:
```
[server-Standard]
name=Standard server
-command=/usr/bin/X -br -audit 0
```
Y cambialo por:
```
[server-Standard]
name=Standard server
-command=/usr/bin/X -br -audit 0 [COLOR="Red"]-dpi 96[/COLOR]
```
Donde dice [COLOR="#ff0000"]-dpi 96[/COLOR] es el tamaño de la resolución de la fuente. El valor puede variar según la configuración, pero podés probar con distintos valores hasta que quede como te guste.

> **User21 said:**
> o_O?????


:-k

Puso lo de Estudiantes porque faktorqm tiene el escudo de Estudiantes De La Plata en su avatar.:)

---

### Post by rojojuan on 2008-02-21
[QUOTE=spg76;4376125]Para cambiar el tamaño de la fuente en la pantalla de login, tenes que editar el archivo /etc/gdm/gdm.conf
Abrilo con:
```
sudo gedit /etc/gdm/gdm.conf
```
Busca la parte donde dice:
```
[server-Standard]
name=Standard server
-command=/usr/bin/X -br -audit 0
```
Y cambialo por:
```
[server-Standard]
name=Standard server
-command=/usr/bin/X -br -audit 0 [COLOR="Red"]-dpi 96[/COLOR]
```
Donde dice [COLOR="#ff0000"]-dpi 96[/COLOR] es el tamaño de la resolución de la fuente. El valor puede variar según la configuración, pero podés probar con distintos valores hasta que quede como te guste.


Esto lo hice en:
Sistema-Preferencias-Apariencia-Tipografías-Detalles-Resolución.

---

### Post by faktorqm on 2008-02-21
Muchas gracias a todos, lo pruebo y aviso. Vamos pincharratas!! :D

---

### Post by faktorqm on 2008-02-25
Che lo de spg76 anduvo perfecto (sos grosso, sabelo!) pero con lo otro no tuve tanta suerte.
en mi pc no existe home/faktorqm/.icons/places, ni /scalable/places, el mio es un tema modificado de uno original, esta en /usr/share/icons/LiNsta/, pero la carpeta blabla/scalable/places/ tampoco existe. tampoco encontre el start-here, o sea, esta pero nada relacionado con el tema de iconos que puse. 
Lamento no haberlo solucionado por mi mismo, escucho sugerencias mientras sigo buscando. salu2 y gracias a todos!! :KS

---

### Post by spg76 on 2008-02-26
La carpeta "places" la podés crear y ponerle los iconos que quieras cambiar.
Si quere conservar el tema actual crea la carpeta "/usr/share/icons/LiNsta/22x22/places" y ahí agregá el icono que quieras y nombralo "start-here.png". Tene en cuenta que tiene que ser de 22 x 22 pixeles.

---

### Post by faktorqm on 2008-02-26
groso! ahh y otra cosa, con el gimp no pude grabar en formato svg, se puede con algun plug-in/add-on/patch o algo parecido? o con png ya estamos? en teoria es mas rapido si todos los iconos estan en formato svg. Un chiche no mas. Salu2!

---

### Post by spg76 on 2008-02-26
Tengo entendido que Gimp solo puede importar SVG (via plugin) pero no puede exportar (que alguien me corrija si estoy equivocado).
Podrías instalar Inkscape, aunque con una imagen PNG debería funcionar.

---

### Post by Mafber on 2008-02-26
ya que estamos con preguntas de apariencia... sumo algunas mias :)
cuando me carga el splash el fondo es anaranjado... ¿como lo cambio? busque en google hasta que desistí. El las versiones anteriores era mas fácil cambiar el color. 
en la pantalla de login la resolución es 1280 x 1024 ¿como la cambio a una resolución mas acorde a mi monitor? :confused:

---

### Post by spg76 on 2008-02-26
> **Mafber said:**
> ya que estamos con preguntas de apariencia... sumo algunas mias :)
cuando me carga el splash el fondo es anaranjado... ¿como lo cambio? busque en google hasta que desistí. El las versiones anteriores era mas fácil cambiar el color.

Creo que para cambiar el color tenes que ir a "Sistema > Administración > Ventana de entrada", y ahí hay una opción que es "Color de fondo".

> **Mafber said:**
> en la pantalla de login la resolución es 1280 x 1024 ¿como la cambio a una resolución mas acorde a mi monitor? :confused:

Tenés que editar xorg.conf para agregarle la resolucion que querés, pero no me acuerdo bien donde, así que mejor espera a alguien que sepa más.

---

### Post by Mafber on 2008-02-26
ya le cambié el color en "Ventana de entrada" (como en las versiones anteriores) pero no me cambia el fondo.
Puedo cambiar el fondo de la pantalla de login pero cuando me muestra el splash... todo anaranjado ](*,)
no encontré nada en google... así que desistí

---

### Post by spg76 on 2008-02-26
Según lo que dicen [en este thread]("http://ubuntuforums.org/showthread.php?t=651389"), tenés que editar el archivo /etc/gdm/PreSession/Default
Escribí en una terminal:
```
sudo gedit /etc/gdm/PreSession/Default
```
Hay una parte donde dice:
```
# Default value
if [ "x$BACKCOLOR" = "x" ]; then
BACKCOLOR=[COLOR="Red"]"#dab082"[/COLOR]
fi
```
Cambiá donde dice [COLOR="Red"]"#dab082"[/COLOR] por el color que quieras.
También podés comentar esas líneas (poner un # antes de la línea) para que respeten el color que elegiste en "Ventana de entrada".
Espero que te sirva.

---

### Post by Mafber on 2008-02-26
gracias funcionó!!! por fin tengo otro color!!!!
al principio pensé que había que comentar solo la linea del color... ja no levantó mas sesión... y cuando entraba a "modo prueba de fallo" y trataba reiniciar, se me freezaba el sistema
despues lei el  thread que habias puesto y entendí que hay que comentar todas esas 3 linea.
Gracias!!!! :)

---

### Post by leogagliardi on 2009-07-20
Lo que habia dicho spg76 sobre editar el archivo gdm.conf esta bien pero entiendo que no es lo mismo que cambiar la opcion en sistema/preferencia/apariencia....etcétera ya que esto último ya es configuración de gnome mientras que gdm tiene una configuración propia que gnome puede tomar y levantar igual o no. En las opciones de Gnome yo tenia -96 dpi y sin embargo el tamaño de fuente den user y pass en usplash era gigante. Y pese a formatear y reinstalar distintas versiones (7.10 y 8.04) el error persistia.

Para cambiar la resolución de pantalla tenes que editar usplash.conf:
:~$ sudo gedit /etc/usplash.conf
por defecto contiene

# Usplash configuration file
# These parameters will only apply after running update-initramfs.

xres=1280
yres=800   

pero podes cambiarlo a lo que necesites. Para que estos cambios tengan efectos tenes que hacer que tome esa nueva configuración haciendo:
sudo update-initramfs -u -k `tu kernel`

donde `tu kernel` es lo que te responde al poner uname -r en consola

espero que haya servido de ayuda
Saludos
Leo

PD: Mis respetos a Estudiantes que acaba de ganar la libertadores

---

