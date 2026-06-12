---
title: "Acentos en la consola tty"
date: 2008-07-05
forum: Software
---

### Post by bagm on 2008-07-05
Hola,
    Mi teclado es US International (with dead keys). En la consola tty puedo ingresar ñ y Ñ, pero no puedo ingresar áéíóú. Puedo verlos a todos (áéíóúñÑ), solamente no puedo ingresar áéíóú.  ¿Alguno tiene idea?
    Gracias y saludos a todos.

---

### Post by Hei Ku on 2008-07-05
tenes configurado el idioma para español?

Probá haciendo:

```

sudo dpkg-reconfigure console-setup

```

---

### Post by bagm on 2008-07-06
> **Hei Ku said:**
> tenes configurado el idioma para español?

Probá haciendo:

```

sudo dpkg-reconfigure console-setup

```

Ya probé, sin suerte.
Mi teclado es US International (with dead keys), no español.
Gracias desde ya.

---

### Post by Hei Ku on 2008-07-06
una cosa es la distribución del teclado y otra el idioma que tenés configurado.

---

### Post by bagm on 2008-07-06
> **Hei Ku said:**
> una cosa es la distribución del teclado y otra el idioma que tenés configurado.

Gracias por tu respuesta.
¿dónde/cómo configuro el idioma?

---

### Post by Hei Ku on 2008-07-06
En el comando que te pasé antes, en la pantalla donde elegis la codificación de la consola, tenés que elegir ISO 8859-1

Esa codificación es la que permite todos los caracteres del español. Fijate que quizás tengas que apretar '+a y después la barra espaciadora para que te aparezca la á.

---

### Post by bagm on 2008-07-06
> **Hei Ku said:**
> En el comando que te pasé antes, en la pantalla donde elegis la codificación de la consola, tenés que elegir ISO 8859-1

Esa codificación es la que permite todos los caracteres del español. Fijate que quizás tengas que apretar '+a y después la barra espaciadora para que te aparezca la á.

Gracias por tu respuesta.
Tengo una bronca...
Mirá, si pongo ISO 8859-1 funciona como vos decís, pero no puedo ver caracteres UTF-8 obviamente. A veces pongo UTF-8 (la predeterminada) y los acentos andan bien hasta que reinicio o vuelvo a ejecutar dpkg-reconfigure dejando las mismas opciones. En pocas palabras, anda cuando quiere.
Otra cosa: Cuando me pregunta: "Set of characters that should be supported by the console font:" yo le pongo "# Latin1 and Latin5 - western Europe and Turkic languages", no sé si está bien, no es la predeterminada, no recuerdo ya cuál era la predeterminada.
Saludos.
Gracias de nuevo.

---

### Post by Hei Ku on 2008-07-06
yo le puse lo mismo que vos, y me andan bien.

---

