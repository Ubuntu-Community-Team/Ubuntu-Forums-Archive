---
title: "Para los amantes de Conky"
date: 2008-11-02
forum: Software
---

### Post by vk-cdg on 2008-11-02
Navegando por alguno de los tantos blogs que suelo consultar, me encontré con una configuración de Conky muy buena.
Les adjunto la captura y obviamente el archivo de configuración para el que guste usarlo. Luego de unos links, el archivo para descargar está en Gnome-look

---

### Post by marianom on 2008-11-02
Si, está muy angelina... digo muy buena :)
¡Gracias!

---

### Post by vk-cdg on 2008-11-03
Yo por el momento estoy de la vereda de enfrente (en cuanto a los monitores de sistema, a Angelina le entro como rengo a la muleta) ya que uso Screenlet con uno que se llama WaterMark.


Adjunto un screenshot!

---

### Post by Mauro22 on 2008-11-03
Gracias!!


Esta muy bueno!

---

### Post by victor_nesta on 2008-11-03
Bueno, este me gusto asi que me voy a dignar a poner conky en mi compu.
pero tengo una duda.
Las carpetas .font y .scrips, ¿donde las tiraría? ¿en mi /Home?

---

### Post by chakersito on 2008-11-03
> **victor_nesta said:**
> Las carpetas .font y .scrips, ¿donde las tiraría? ¿en mi /Home?
Si, pero fijate que la carpeta .fonts ya la tenes en tu /Home...

---

### Post by vk-cdg on 2008-11-03
Yo no soy muy amigo del conky, las veces que traté de hacerlo andar algo siempre pasaba. La última vez fue la que rebalsó el vaso, me destellaba y lo mandé de paseo.

Estuve un tiempo sin nada y luego me crucé con este screenlet y bue, vino para quedarse.

---

### Post by victor_nesta on 2008-11-03
> **chakersito said:**
> Si, pero fijate que la carpeta .fonts ya la tenes en tu /Home...

Te juro por mi vida, que .fonts no existe en mi /home. 
Igualmente tire todo ahí a ver que pasaba.
Funcionar funciona todo, pero sin el formato tan bonito que tienen la imágenes.

---

### Post by Mauro22 on 2008-11-03
Perdon mi ignorancia...


Pero la estas copiando en /home o en /home/tu_usuario/ ??

---

### Post by victor_nesta on 2008-11-03
en /home/victor (mi usuario)

---

### Post by Mauro22 on 2008-11-03
el proceso normal es pegar:

.fonts
.scripts
.conkyrc 

en tu carpeta y luego desde la consola lanzar conky. 

.fonts tampoco la tenia y sin embargo no hubo problema

---

### Post by victor_nesta on 2008-11-03
> **Mauro22 said:**
> el proceso normal es pegar:

.fonts
.scripts
.conkyrc 

en tu carpeta y luego desde la consola lanzar conky. 

.fonts tampoco la tenia y sin embargo no hubo problema

Ya esta, la cag**a me la mande yo cuando edite el .conkyrc que desactive unas opciones.

Gracias

---

### Post by Kabezon on 2008-11-03
Está bueno, alguien hizo andar lo de GMail? Vieron que trae el script y todo, pero no viene configurado para mostrar gmail raramente o.O cuales son los códigos? Y cómo hago para que en vez de mostrarme el clima en centígrados me los muestre en Fahrenheit? Cómo consigo el código para que me muestre el clima de acá? Por último, mil gracias, muy bonito ^^ Ahora mismo lo estoy retocando así queda lindo con mi wallpaper y los colores GTK :P

[edito]
Qué bajón estos que van al costado :S Yo al mío lo tenia en una renglón abajo con fondo negro. Con este tenés que andar toqueteando los colores dependiendo el wallpaper que usés y en algunos directamente no se ve, tiene que ser liso :S Si le ponés fondo a este se ve re feo :P Se puede ponerle un fondo transparente? Así onda, que quede un negro transparente...

---

### Post by chakersito on 2008-11-03
> **Kabezon said:**
> alguien hizo andar lo de GMail? Vieron que trae el script y todo, pero no viene configurado para mostrar gmail raramente o.O cuales son los códigos?

Fijate en el .conkyrc (linea 83) tenes la parte de gmail, lo unico que tenes que hacer es copiarla y ponerla en la parte que quieras (descomentada la linea). En la misma linea dice user y password, cambia esos valores por los de tu email y listo.
Acordate de cambiar el nombre de la fuente en caso de que no la tengas.

> **Kabezon said:**
> Y cómo hago para que en vez de mostrarme el clima en centígrados me los muestre en Fahrenheit? Cómo consigo el código para que me muestre el clima de acá?
El tiempo de donde queres mostrar? entra a [http://xoap.weather.com/](http://xoap.weather.com/) busca tu  ciudad y copia el código de la ciudad, que aparece en la barra de direcciones cuando entras a ver el pronostico desde esa pagina y se lo tenes que poner en el .conkyrc.

---

