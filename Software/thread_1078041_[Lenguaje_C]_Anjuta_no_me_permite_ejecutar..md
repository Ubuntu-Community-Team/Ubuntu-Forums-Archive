---
title: "[Lenguaje C] Anjuta no me permite ejecutar."
date: 2009-02-22
forum: Software
---

### Post by Gallilea on 2009-02-22
Hola a todos, hace cerca de un mes que instalé Ubuntu, es la primera vez el esto; y tengo un problema que he tratado de solucionar desde hace tres días y nada. 

Instalé Anjuta para programar en lenguaje C, pero no logro ejecutar el programa más famoso, "Hola mundo.".
Les dejo información:

-Instalé Anjuta desde Añadir y Quitar ya que se encontraba en los repositorios.
-Compilé y cosntruí (al menos eso pienso)
"/* fichero hola.c */
/* Este programa saluda desenfadadamente. */
#include <stdio.h>
void main(void) {
    printf("Hola! Que tal estas, futuro programador?\n");
}"
pero al ejecutar no sucede nada, de nada, ni con F3 ni desde el menú.
Lo hice primero como archivo, luego como proyecto. 
-En el caso de proyecto, al darle destino me dice "El directorio «/» no está vacío. La creación del proyecto podría fallar si algunos archivos no se pudiesen escribir. ¿Quiere continuar? Sí/No" Pero no hay nada dentro de la carpeta. (Tengo poca experiencia con Ubuntu!)
-Leí el manual. Busqué información en la web, reinstalé algunos paquetes (libgnomeui, libgnome) porque Anjuta me decía que las versiones de ellos no eran mayores a 2.
-Al momento de construir el mensaje es: "make:*** no se hace nada para `all"

De todas formas, intenté compilar desde la terminal, haciendo $gcc hola.c -o hola; pero me dice "gcc; No existe el fichero o directorio."

Ya no tengo idea de qué hacer con esto. Si necesitan otra información me avisan. Por favor, una manito con esto y ya estoy agradecida!!


Saludos!

---

### Post by sherwoodinc on 2009-02-23
Probá instalar el paquete build-essential y volvé a tratar de compilar desde la Terminal.
```
gcc hola.c
```
Si compila bien, te va a generar un ejecutable llamado "a.out" (porque no le especificamos el nombre del resultado). Si no, te va a tirar los errores y/o warnings correspondientes.

---

### Post by Hernán-Amaya on 2009-02-23
Hola mirá yo con la nueva versión de anjuta tuve problemas, y por razones de tiempo me cambié a otra ide uso Codeblocks y anda muy bien, no esta en el repositorio, en la pagina [http://www.codeblocks.org/](http://www.codeblocks.org/) vas a tener mas info.

suerte.

---

### Post by Gallilea on 2009-02-23
Gracias a los dos.

sherwoodinc, tengo la versión 11.4 de build-essential, pero si pongo en la terminal $ gcc hola.c me dice esto:

natalia@Gallilea:~$ gcc hola.c
gcc: hola.c: No existe el fichero ó directorio
gcc: no hay ficheros de entrada

así que ni idea. Voy a probar lo que dice Hernán a ver que pasa.

Saludos.

---

### Post by sherwoodinc on 2009-02-23
Dos cosas:

1 - Me adhiero a la sugerencia del compañero. El codeblocks resulta más fácil de usar. Tenés los paquetes para instalar desde el synaptic (versión del codeblocks 8.02, usan el esquema de versiones año.mes igual que ubuntu), o podés bajarte unos más actualizados de la página.

2 - Es raro que "gcc hola.c" no te funcione. Probaste hacerlo desde el directorio donde el Anjuta te creó el hola.c ?

---

### Post by unsigned on 2009-02-24
Que raro. Yo también soy nuevo en esto de programar sobre plataforma Ubuntu y lo que hice fue bajarme las librerías del GCC a través del gestor de paquetes de Synaptic, ejecutar un "sudo apt-get" y listo. Ya estaba compilando.

---

### Post by Gallilea on 2009-02-24
Hola! Al menos logré ejecutar desde la terminal. Solo que de esa forma los guarda en /home/natalia, es decir quedan tirados y no en una carpeta ¬¬. No es muy ordenado eso eh. Ya veré que más se puede hacer.

---

