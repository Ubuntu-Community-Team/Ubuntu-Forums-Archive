---
title: "Aprendiendo a usar el Terminal"
date: 2009-04-27
forum: Software
---

### Post by DrKenobi on 2009-04-27
Hola, la cosa es muy simple. Cuando navego por el terminal, hay veces que no puedo acceder a carpetas que tienen en el nombre dos palabras. Por ejemplo, si el nombre de la carpeta es "Mini vMac". Como hago? Porque si yo pongo "cd Mini vMac" me da error.

Gracias

---

### Post by Hernán-Amaya on 2009-04-27
Hola esto se posteo hace un tiempo, para poder acceder a los directorios con nombres que tienen espacios hay varias maneras una es:

cd nombre\ con\ espacio

otra es:

cd "nombre con espacio"

y otra es:

cd 'nombre con espacio'

espero que te sirva otra cosa podes usar la tecla TAB para autocompletar los directorios comandos o archivos!

---

### Post by sdennie on 2009-04-27
> **Hernán-Amaya said:**
> 
espero que te sirva otra cosa podes usar la tecla TAB para autocompletar los directorios comandos o archivos!

Es muy util a aprender a usar Tab.  Acordate que a si no da informacion tenes que apretar Tab otra vez y te da las posibilidades.  Tambien que "m<Tab>" no es lo mismo que "M<Tab>.  Pero, podes arreglar eso facilmente.  Hacete un fichero ~/.inputrc y pone:

```

set completion-ignore-case on 

```

Despues de abrir un terminal nuevo, mayusculas y minusculas son lo mismo con el Tab.

---

### Post by Hernán-Amaya on 2009-04-27
Grande Luca Prodan siempre tirando buena data!

---

### Post by EnriqueK on 2009-04-27
Si tenés acceso gráfico a la carpeta donde querés abrir el terminal, podés usar este pequeño truco que permite introducir la ruta a dicha carpeta al terminal y es simplemente arrastrádola al mismo, resumiendo si querés abrir terminal en una carpeta cualquieram abris un terminal y ponés cd dejás un espacio y luego arrastrás la carpeta al terminal-->Enter y ya. 
Este método de arrastrar al terminal tiene muchos otros usos y sirve tamvién para introducir la ruta de los archivos.

---

### Post by DrKenobi on 2009-04-27
> **sdennie said:**
> Es muy util a aprender a usar Tab.  Acordate que a si no da informacion tenes que apretar Tab otra vez y te da las posibilidades.  Tambien que "m<Tab>" no es lo mismo que "M<Tab>.  Pero, podes arreglar eso facilmente.  Hacete un fichero ~/.inputrc y pone:

```

set completion-ignore-case on 

```

Despues de abrir un terminal nuevo, mayusculas y minusculas son lo mismo con el Tab.

Un fichero es una carpeta?
Si es asi, como lo hago, porque este es oculto
Y el "set completion-ignore-case on" lo hago estando dentro del fichero?

Gracias

---

### Post by Air23 on 2009-04-27
> **DrKenobi said:**
> Un fichero es una carpeta?
Si es asi, como lo hago, porque este es oculto
Y el "set completion-ignore-case on" lo hago estando dentro del fichero?

Gracias
Me parece que asi
```
gedit ~/.inputrc
```
Se abre un archivo en gedit, pegas esto:
```
set completion-ignore-case on
```
Guardas y listo

---

### Post by Hernán-Amaya on 2009-04-28
> **DrKenobi said:**
> Un fichero es una carpeta?
Si es asi, como lo hago, porque este es oculto
Y el "set completion-ignore-case on" lo hago estando dentro del fichero?

Gracias

El amigo Luca Prodan perdón sdennie te dijo que crees el archvio ~/.inputrc

cuando veas el ~ significa que tu home prueba desde cualquier directoria y escribe cd ~ y vas a parar a tu home.

el . delante del nombre del archivo significa que es un archivo oculto.

para crear el archivo usa gedit si no estas canchero con nano o algún otro editor de texto de consola.

podes hacerlo escribiendo en la consola (si estas en tu home)

gedit .inputrc

si no estas en tu home

gedit ~/.inputrc 

escribe lo que puso sdennie y listo guarda el archivo y va andar joya

cualquier cosa pregunta, hay un comando que siempre me saca de apuros: man

para saber como hacerlo andar man man en la consola.

---

