---
title: "Donde quedan los ejecutables?"
date: 2009-06-19
forum: Software
---

### Post by ParamDaya on 2009-06-19
[FONT=Georgia][SIZE=2][B]Estimados

Acabo de instalar un software tercero que no aparece en la lista de las aplicaciones. Por lo tanto, para tener un link directo en la barra tengo que agregarlo, pero mi gravisimo problema es que no tengo ni la mas minima idea de donde se instalo, donde quedan los ejecutables y que formato tienen los ejecutables.

El programa es el Webilder, que lo consegui de getdeb.

Por favor alguna ayuda al respecto de esto. Muchisimas gracias.[/B][/SIZE][/FONT]

---

### Post by Psycopatologic on 2009-06-19
> **ParamDaya said:**
> [FONT=Georgia][SIZE=2][B]Estimados

Acabo de instalar un software tercero que no aparece en la lista de las aplicaciones. Por lo tanto, para tener un link directo en la barra tengo que agregarlo, pero mi gravisimo problema es que no tengo ni la mas minima idea de donde se instalo, donde quedan los ejecutables y que formato tienen los ejecutables.

El programa es el Webilder, que lo consegui de getdeb.

Por favor alguna ayuda al respecto de esto. Muchisimas gracias.[/B][/SIZE][/FONT]

 Amigazo, intenta hacer esto:  1.- Apretas el boton derecho del mouse sobre el panel y das click sobre "Add to panel" o "Agregar al panel".  2.- Custom aplication launcher   3.- Pones:  Name: Webilder (o el que quieras)  Command: webilder  Comment: aqui lo que quieras.    Eso deberia bastar. Prueba si el comando funciona primero apretando ALt+F2 y poniendo el mismo comando "webilder", si lo lanza puedes. Es que lo que hace ubuntu, crea scriptscon el nombre de la aplicacion (por lo general el nombre que usas para el comando apt-get) para ser invocados desde terminal y usa esos mismos scripts como fuente para lanzadores.  Espero te sirva, saludos.

---

### Post by kamus on 2009-06-19
> **ParamDaya said:**
> [FONT=Georgia][SIZE=2][B]Estimados

Acabo de instalar un software tercero que no aparece en la lista de las aplicaciones. Por lo tanto, para tener un link directo en la barra tengo que agregarlo, pero mi gravisimo problema es que no tengo ni la mas minima idea de donde se instalo, donde quedan los ejecutables y que formato tienen los ejecutables.

El programa es el Webilder, que lo consegui de getdeb.

Por favor alguna ayuda al respecto de esto. Muchisimas gracias.[/B][/SIZE][/FONT]

Deberia haber quedado en /usr/bin/webilder , de lo contrario puedes buscar (si sabes) el nombre del ejecutable , en una terminal escribes:

```
whereis nombre_programa

```
Esto te dira la ruta del binario ejecutable que puedes poner cuando agreges el enlace en el menu ;)

---

### Post by moreback on 2009-06-19
**dpkg -L webilder** te lista todos los archivos que tiene ese paquete.

---

