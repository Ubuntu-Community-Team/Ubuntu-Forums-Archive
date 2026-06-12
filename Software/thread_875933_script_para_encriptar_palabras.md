---
title: "script para encriptar palabras"
date: 2008-07-31
forum: Software
---

### Post by jeffryab on 2008-07-31
Hola gente,

Necesito un script en linux para encriptar palabras. cualquier palabra o letra que ponga en ese sript debe ser encriptada (o cambiada por otra letra, numero u otro caracter). He buscado en en varios foros y en internet pero no he encontrado nada, solo para encriptar archivos pero eso no es lo que quiero. Si alguien tiene algun script o un link o me pueda ayudar les agradeceria mucho. El script es para un proyecto que estoy relizando en linux y soy un principiante en esto.

Gracias,

---

### Post by Hei Ku on 2008-07-31
gpg puede hacer eso, pero usa un esquema de clave publica y privada, que no se si es lo que estas buscando.

---

### Post by jeffryab on 2008-07-31
Hei Ku,

Gracias por tu respuesta. gpg me sirve pero en realidad lo que neceisto es el script en si (con funciones, variables, usando If, For, Case, Sed)

---

### Post by Darkade on 2008-07-31
Si quieres algo simple, lo digo porque tu pregunta suena a proyecto escolar.
puedes hacer basicamente esto:

>Separar la cadena en caracteres
>Luego a cada caracter le puedes buscar su codigo ASCII ejemplo la 'A' es 65
>A ese 65 le puedes hacer algunas operaciones multiplicar sumar restar
>convierte ese entero en caracter
>concatena todos los caracteres

es muy simple pero si es algo asi lo que necesitas eso te puede ser util

para desencriptar solo aplica las operacioens "al revez"

---

### Post by Hernán-Amaya on 2008-07-31
hay un algoritmo que se llama [playfair]("http://www.textoscientificos.com/criptografia/playfair") que te puede servir buscalo en google que seguro debe haber varios ejemplos de como hacerlo. yo lo hice en c hace un tiempo si lo encuentro te lo mando.

---

