---
title: "Un programa parecido a esto...?"
date: 2008-06-24
forum: Software
---

### Post by --Lutari-- on 2008-06-24
A ver si me explico. Quiero un programa que al ingresar un código de un producto diga cuanto sale, como se llama, etc. Espero sus respuestas :)

---

### Post by Kantier on 2008-06-24
erm... ¿con una base de datos tuya? eso es relativamente simple de hacer sin conocer DEMASIADO de programación...

---

### Post by tzulberti on 2008-06-24
> **--Lutari-- said:**
> A ver si me explico. Quiero un programa que al ingresar un código de un producto diga cuanto sale, como se llama, etc. Espero sus respuestas :)

Los productos tienen un codigo de barras que sino me equivoco es unico. Sin embargo, un lugar de donde sacar que codigo corresponde a que producto no existe (menos aun comparando precios).

---

### Post by Hei Ku on 2008-06-24
De hecho, son muy caras de mantener esas bases de datos. Las tienen las empresas mas grandes de estudios de mercado, y son bases de datos enormes. Pensa en terabytes de informacion solo para los archivos maestros.

---

### Post by Tosh78 on 2008-06-26
Me parece que lo que estas pidiendo no es algo que exista de forma standard. Es decir, para hacer eso, necesitas una base de datos en la que figuren los productos y los codigos que les corresponden. Ademas de eso, necesitarias una pistola de lectura y armar el programa. En mi trabajo una vez tuvimos que hacerlo. Como es en SAP, la base de datos era MaxDB, y los programas decodificaban el codigo en numeros. Esto lo hicimos con funciones RFC con ABAP. La cantidad de espacio que necesitarias depende de la cantidad de productos que tengas, pero no creo qe lleguen a ser terabytes. 
Con todo esto, a lo que voy es que no hay algo ya establecido, deberias ver que te conviene a vos y ajustarlo a lo que necesites.

---

