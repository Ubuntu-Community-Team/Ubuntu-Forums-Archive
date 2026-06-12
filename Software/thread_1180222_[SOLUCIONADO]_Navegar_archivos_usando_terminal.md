---
title: "[SOLUCIONADO] Navegar archivos usando terminal"
date: 2009-06-06
forum: Software
---

### Post by felipeleven on 2009-06-06
Hola:

Esta es mi consulta:

¿Existe algún programa que permita navegar fácilmente por archivos usando el terminal?, o si alguien me pueda recomendar la mejor forma para navegar en este (consola).
Saludos

---

### Post by Patriciologico on 2009-06-07
[Midnight Commander]("http://www.midnight-commander.org/")

```
sudo aptitude install mc
```

[IMG]http://4.bp.blogspot.com/_9cmpUFVazDc/SEg2LLKp4YI/AAAAAAAAAO8/z8eBeKTthZ8/s320/mc.jpeg[/IMG]

Saludos

---

### Post by Carlos C on 2009-06-07
para navegar en el terminal yo uso lo básico: ls para ver los ficheros y la tecla TAB para no tener que escribir el nombre de las carpetas.
Midnight commander es genial, igual al antiguo norton commander. Aunque desde que descubrí krusader, no lo cambio por nada.

---

### Post by felipeleven on 2009-06-07
Gracias a los dos por las respuestas, voy a probar todas sus sugerencias.:D
una consulta:
al usar "cd" uno deja referenciado un directorio, para salir de este ¿Que comando se usa?

Eso y denuevo gracias, esto lo consultaba porque pienso usar la versión server de ubuntu y hacer ciertas cosas sin usar entornos graficos (ej: agregar un repositorio editando el archivo correspondiente usando nano).

Saludos

---

### Post by guillermolisi on 2009-06-07
> **felipeleven said:**
> Gracias a los dos por las respuestas, voy a probar todas sus sugerencias.:D
una consulta:
al usar "cd" uno deja referenciado un directorio, para salir de este ¿Que comando se usa?

Eso y denuevo gracias, esto lo consultaba porque pienso usar la versión server de ubuntu y hacer ciertas cosas sin usar entornos graficos (ej: agregar un repositorio editando el archivo correspondiente usando nano).

Saludos
Si queres volver a tu home directory, con ingresar cd a secas alcanza.

Si queres pasarte a otro directorio, cd <otro_directorio>.

---

### Post by moreback on 2009-06-07
**cd ..** para subir un nivel
**cd .**  para quedarse en el mismo (algo estúpido, pero no falta jaja)

---

### Post by felipeleven on 2009-06-07
> **guillermolisi said:**
> Si queres volver a tu home directory, con ingresar cd a secas alcanza.

Si queres pasarte a otro directorio, cd <otro_directorio>.

Muchas gracias, tal cual dijiste. :p

Probé Midnight commander y está muy bueno el programa, es super instuitivo. Krusader es tipo "Midnight commander" pero en entorno grafico (qt4), en ambos se puede navegar bastante rápido. 
Ahora usando los comando incluidos en teminal (ls, cd, dir...) también se puede navegar de forma muy cómoda, ahora la única precaución es colocar las carpetas que usan espacio entre comillas.
Ej: al elegir la carpeta: **Fondos de pantalla** , usar si uno quisiera elegirla **cd "Fondos de pantalla"**, respetando siempre las mayúsculas.

Eso, saludos y denuevo gracias :D

---

### Post by guillermolisi on 2009-06-07
> **felipeleven said:**
> Muchas gracias, tal cual dijiste. :p

Probé Midnight commander y está muy bueno el programa, es super instuitivo. Krusader es tipo &quot;Midnight commander&quot; pero en entorno grafico (qt4), en ambos se puede navegar bastante rápido. 
Ahora usando los comando incluidos en teminal (ls, cd, dir...) también se puede navegar de forma muy cómoda, ahora la única precaución es colocar las carpetas que usan espacio entre comillas.
Ej: al elegir la carpeta: **Fondos de pantalla** , usar si uno quisiera elegirla **cd &quot;Fondos de pantalla&quot;**, respetando siempre las mayúsculas.

Eso, saludos y denuevo gracias :D
Es que el espacio en Linux es significativo e interpretable por el shell, por eso hay que filtrarlo de alguna forma (el espacio se usa para separar opciones de una lista o parametros para un comando como archivo de entrada y archivo de salida, etc.).

Una buena practica es evitar usarlos en nombres de archivos (los directorios con archivos tambien) reemplazandolos por "_" (guion bajo) que no requiere de filtros ya que no es interpretable por el shell (no es significativo).

---

