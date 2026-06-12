---
title: "[SOLVED] Instalar Temas en Ubuntu"
date: 2008-12-28
forum: Software
---

### Post by Applelnx on 2008-12-28
Hola pongo el thread aca porque es un tema bastante general. Si corresponde a otra seccion por favor muevanlo.

Acabo de instalar Ubuntu 8.10 y queria instalarle un par de temas de iconos y bordes de ventanas. El problema es simple... no puedo :(

Voy a Sistema > Preferencias > Apariencia > Personalizar Temas > Iconos

En Google busque y decia que tenia que arrastrar el paquete en la parte donde se modifican los tipos de iconos. Eso hice pero no me pregunta nada de si quiero instalarlo o no. Tampoco tengo un boton de instalar o agregar.

Agradezco mucho si alguno me puede ayudar :D

Saludos

---

### Post by santiagoward2000 on 2008-12-28
> **Applelnx said:**
> Hola pongo el thread aca porque es un tema bastante general. Si corresponde a otra seccion por favor muevanlo.

Acabo de instalar Ubuntu 8.10 y queria instalarle un par de temas de iconos y bordes de ventanas. El problema es simple... no puedo :(

Voy a Sistema > Preferencias > Apariencia > Personalizar Temas > Iconos

En Google busque y decia que tenia que arrastrar el paquete en la parte donde se modifican los tipos de iconos. Eso hice pero no me pregunta nada de si quiero instalarlo o no. Tampoco tengo un boton de instalar o agregar.

Agradezco mucho si alguno me puede ayudar :D

Saludos

Hola!
Probá abrir el paquete y ver qué tiene adentro. A veces algunos paquetes tienen el paquete posta adentro, y tenés que arrastrar ese.
Sino podés instalarlos manualmente. Extraés la carpeta de íconos a ~/.icons (si no existe creá la carpeta), o si es un tema GTK, a ~/.themes.
Suerte!

---

### Post by Applelnx on 2008-12-28
Me estoy yendo, despues pruebo eso y te cuento. Gracias Santiago ;)

---

### Post by rodolfojavier1982 on 2008-12-28
Bueno, por si las dudas, te comento lo que yo hago.
Generalmente bajo los paquetes de iconos de gnome-look
Si viene tipo zip, descomprimilo y dentro deberias tener un archivo .tar.gz o .tar.bz2 o similar.
Este es el que vas a instalar desde 
Preferencias de la Apariencia (Boton derecho sobre el Escritorio->Cambiar el Fondo del Escritorio)

Anda a la pestaña "Tema" y elegi "Instalar"
Selecciona el archivo.tar.bz2 o similar que descomprimiste o descargaste y dale instalar.

Te lo va a instalar automaticamente, luego te preguntara si queres aplicarlo ahora o no.
Si le decis que no, lo podes ver en la pestaña 
Temas->Personalizar->Iconos
Te va a aparecer en esa lista, con solo seleccionarlo se previsualiza el tema.

Si elegiste uno de estos paquetes de temas, vas a tener una carpeta oculta en 
         /home/tu_usuario/.icons
Vas a tener una carpeta por cada tema que ya hayas asignado.
Si queres cambiar algun icono en particular reemplaza uno con el mismo nombre en la carpeta correspondiente.

Bueno, espero que te sirva o que le sirva a alguien.
Perdon por el exceso de detalles, pero suelo acordarme mejor de las cosas asi. :)

---

### Post by viper3k on 2008-12-28
Yo hago lo mismo q rodolfojavier1982 prova ese metodo , es el mas facil ( y el unico q conozco) xD

---

### Post by Applelnx on 2008-12-28
Gracias, funciono de esa manera, igual, no me andan bien los iconos "experience" no se por que. No se ven como el preview :(

Por lo otro, funco todo de 10 ;)

---

### Post by rodolfojavier1982 on 2008-12-29
Que bueno que te haya servido!

Gracias por la medallita! :D

---

### Post by santiagoward2000 on 2008-12-30
> **Applelnx said:**
> Gracias, funciono de esa manera, igual, no me andan bien los iconos "experience" no se por que. No se ven como el preview :(

Por lo otro, funco todo de 10 ;)

Me alegro que ande! :D
¿Podrías poner la dirección de esos íconos? Así vemos qué les pasa!
Saludos!

---

