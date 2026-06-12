---
title: "[GCC] Como agrego las librerias?"
date: 2009-04-15
forum: Software
---

### Post by Just64 on 2009-04-15
Alguien me puede decir como hago para agregar las librerias de C?
Y como hago para ejecutar el codigo? No me acuerdo bien pero era algo de 
$ gcc "nombre del fuente" -o "nombre del ejecutable" , asi era?

---

### Post by Hei Ku on 2009-04-15
Primero que nada, instala el paquete build-essential.

---

### Post by faktorqm on 2009-04-15
> **Just64 said:**
> Alguien me puede decir como hago para agregar las librerias de C?
Y como hago para ejecutar el codigo? No me acuerdo bien pero era algo de 
$ gcc "nombre del fuente" -o "nombre del ejecutable" , asi era?

Hola, librerias no se como se agregan, no creo que el gcc pueda tampoco. 

La sintaxis para compilar algo "rapido" asi no mas puede ser

```
gcc archivo.c -o archivo.exe
```

puse .exe para distinguir el ejecutable, no es necesario poner .exe ni nada por el estilo.

Para agregar bibliotecas yo usaba el parametro -I mas la ruta completa, te deberia quedar algo asi:

```
gcc archivo.c -o archivo.exe -I/home/ricardo-ruben/bibliotecas/
```

obviamente en el preprocesador va la info de que archivo es especificamente. salu2!

---

### Post by Just64 on 2009-04-16
Una vez q compilo el codigo y creo el ejecutable, como lo ejecuto? Como es la linea de comando?

---

### Post by rubioo on 2009-04-16
Hola just...
 Para ejecutar el programa tenes que poner esto:

 ```

  cristian@cristian-desktop:~$ ./programa
 
```

 Si no podes, tenes que darle permisos de ejecucion al archivo (con chmod)

   Saludos

---

### Post by Just64 on 2009-04-16
> **rubioo said:**
> Hola just...
 Para ejecutar el programa tenes que poner esto:

 ```

  cristian@cristian-desktop:~$ ./programa
 
```

 Si no podes, tenes que darle permisos de ejecucion al archivo (con chmod)

   Saludos
Tenes razon... no me acordaba nada.

---

