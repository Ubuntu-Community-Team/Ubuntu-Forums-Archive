---
title: "Ayuda para instalar conky colors"
date: 2009-08-27
forum: Software
---

### Post by matias_tati on 2009-08-27
Hola quiero instalar el conky colors un conky hermoso que encontre en gnome-look.
[http://www.gnome-look.org/content/show.php/CONKY-colors?content=92328](http://www.gnome-look.org/content/show.php/CONKY-colors?content=92328)
Mi primer problema se planteo al ejecutar los sig comandos siguiendo el tutorial de la pagnina:
$make
$./conky-colors --help
$./conky-colors (options)
$make install
A lo que me tira lo siguiente:
[[img]http://a.imagehost.org/t/0665/1_69.jpg[/img]](http://a.imagehost.org/view/0665/1_69)
El archivo lo baje y lo extrai en el escritorio quizas sea eso pero nose donde debo copiarlo.
Ademas creo estar ejecutando mal los comandos si alguien me pudiera aclarar un poco y decirme que intenta hacer ademas le agradeceria mucho. Saludos!!!

---

### Post by santiagoward2000 on 2009-08-27
Hola!
Lo que pasa es que primero tenés que ir a la carpeta del archivo. Por ejemplo, si lo descomprimiste en el escritorio, hacés:
```
cd ~/Desktop/conky_colors
```
Y ahí sí, le das make y tendría que andar.
Saludos!

---

### Post by staar on 2009-08-27
cuando abrís una terminal por defecto te encontrás en tu home (eso significa el ~), el comando cd sirve para cambiar de directorio, por ejemplo, si los archivos están en tu escritorio dentro de una carpeta que se llama conky-colors, hacés un ```
cd /home/*tuusuario*/Escritorio/conky-colors
``` (el */home/tuusuario/* lo podés suplantar por un ~, o directamente obviarlo, yo lo puse para que te des cuenta) y recién ahí hacer el make (este necesita un archivo makefile para funcionar, y lo busca en el directorio en el que estés al momento de correrlo, por eso el error que te sale)

el ./conky-colors le indica que corra el archivo conky-colors (supongo que será un script de customización del conkyrc a instalar) que se encuentra en la carpeta actual (el . significa eso), el --help supongo será para que te liste las diferentes opciones del script, despúes lo corrés con las opciones que elijas (no sé, por ejemplo ./conky-colors -abcd), y después corres el make install para que lo instale...

saludos

---

### Post by cr1571an on 2009-08-27
hola! me meti a la pagina que sugirio, y estoy instentando instalarlo.Recien estoy empezando a usar Ubuntu.

de donde bajaste conky-colors.tar.gz?

y en esta parte nose que se termina haciendo?

**[B]Copy .conkyForecast.config in ~/.conky folder to your home and replace the values**
	
Update your font cache:
$sudo fc-cache -v -f

**+++ SCRIPTS INSTRUCTIONS +++**
Conky Weather Script: [http://ubuntuforums.org/showthread.php?t=869328](http://ubuntuforums.org/showthread.php?t=869328)
Conky SSL Mail Script: [http://ubuntuforums.org/showthread.php?t=869771](http://ubuntuforums.org/showthread.php?t=869771)
Conky Pidgin Script: [http://ubuntuforums.org/showthread.php?t=969933&highlight=pidgin+conky](http://ubuntuforums.org/showthread.php?t=969933&highlight=pidgin+conky)
Conky Rhythmbox Script: [http://ubuntuforums.org/showthread.php?t=928168&highlight=conky+rhythmbox](http://ubuntuforums.org/showthread.php?t=928168&highlight=conky+rhythmbox)
Conky Banshee Script: [http://ubuntuforums.org/showthread.php?p=7683570](http://ubuntuforums.org/showthread.php?p=7683570)
Conky Exaile Script: [http://ubuntuforums.org/showthread.php?t=926041](http://ubuntuforums.org/showthread.php?t=926041)

If you choose **--todo** option, create a file called ToDo.txt in your home and open ~/scripts/task file to install this script. This one will help you to easy add and remove tasks[/B]


Saludos!

---

### Post by matias_tati on 2009-08-27
> **cr1571an said:**
> hola! me meti a la pagina que sugirio, y estoy instentando instalarlo.Recien estoy empezando a usar Ubuntu.

de donde bajaste conky-colors.tar.gz?

y en esta parte nose que se termina haciendo?

**[B]Copy .conkyForecast.config in ~/.conky folder to your home and replace the values**
	
Update your font cache:
$sudo fc-cache -v -f

**+++ SCRIPTS INSTRUCTIONS +++**
Conky Weather Script: [http://ubuntuforums.org/showthread.php?t=869328](http://ubuntuforums.org/showthread.php?t=869328)
Conky SSL Mail Script: [http://ubuntuforums.org/showthread.php?t=869771](http://ubuntuforums.org/showthread.php?t=869771)
Conky Pidgin Script: [http://ubuntuforums.org/showthread.php?t=969933&highlight=pidgin+conky](http://ubuntuforums.org/showthread.php?t=969933&highlight=pidgin+conky)
Conky Rhythmbox Script: [http://ubuntuforums.org/showthread.php?t=928168&highlight=conky+rhythmbox](http://ubuntuforums.org/showthread.php?t=928168&highlight=conky+rhythmbox)
Conky Banshee Script: [http://ubuntuforums.org/showthread.php?p=7683570](http://ubuntuforums.org/showthread.php?p=7683570)
Conky Exaile Script: [http://ubuntuforums.org/showthread.php?t=926041](http://ubuntuforums.org/showthread.php?t=926041)

If you choose **--todo** option, create a file called ToDo.txt in your home and open ~/scripts/task file to install this script. This one will help you to easy add and remove tasks[/B]


Saludos!

La baje de ahi mismo abajo dice download...

---

### Post by staar on 2009-08-27
> **cr1571an said:**
> Copy .conkyForecast.config in ~/.conky folder to your home and replace the values
esto copia la configuración del script conkyForecast a una carpeta en tu home, y te pide que la modifiques para adaptarla a tu ubicación...
> **cr1571an said:**
> Update your font cache:
$sudo fc-cache -v -f
esto es para actualizar la cache de fuentes, para que conky pueda ver las nuevas fuentes instaladas que necesita...
> **cr1571an said:**
> +++ SCRIPTS INSTRUCTIONS +++
Conky Weather Script: [http://ubuntuforums.org/showthread.php?t=869328](http://ubuntuforums.org/showthread.php?t=869328)
Conky SSL Mail Script: [http://ubuntuforums.org/showthread.php?t=869771](http://ubuntuforums.org/showthread.php?t=869771)
Conky Pidgin Script: [http://ubuntuforums.org/showthread.php?t=969933&highlight=pidgin+conky](http://ubuntuforums.org/showthread.php?t=969933&highlight=pidgin+conky)
Conky Rhythmbox Script: [http://ubuntuforums.org/showthread.php?t=928168&highlight=conky+rhythmbox](http://ubuntuforums.org/showthread.php?t=928168&highlight=conky+rhythmbox)
Conky Banshee Script: [http://ubuntuforums.org/showthread.php?p=7683570](http://ubuntuforums.org/showthread.php?p=7683570)
Conky Exaile Script: [http://ubuntuforums.org/showthread.php?t=926041](http://ubuntuforums.org/showthread.php?t=926041)
estas son intrucciones para otros scripts que quieras agregarle al conky...
> **cr1571an said:**
> If you choose **--todo** option, create a file called ToDo.txt in your home and open ~/scripts/task file to install this script. This one will help you to easy add and remove tasks
esto es para hacer una lista To-Do...

saludos

---

### Post by cr1571an on 2009-08-27
Gracias Muchachos, disculpen mi ignorancia!!

entre en la parte Download Ubuntu Conky 1.7.2

Despues me derivo a [https://launchpad.net/~norsetto/+archive/ppa](https://launchpad.net/~norsetto/+archive/ppa)

y despues termine bajando [         conky - 1.7.2-0ubuntu1~jaunty2]("https://launchpad.net/%7Enorsetto/+archive/ppa/+sourcepub/707549/+listing-archive-extra") 

que es un .deb

y en la pagina dice que baje 
**Download and extract the conky-colors.tar.gz **

Nose si es lo mismo que un .deb.

sigo al pie de la letra las instrucciones, porq recien estoy metiendo mano.:confused:

Saludos

---

### Post by matias_tati on 2009-08-27
Este tenes que bajar: Source	(conky_colors)
El que estas bajanmdo vos es el programa conky te lo da por si no lo tenes instalado.

Bueno quedo bastante bueno desp voy a juguetear con las opciones pq justo elegi un tema que no se ve con mi escritorio
Mas o menos quedo asi:
[[img]http://a.imagehost.org/t/0869/screenshot_001.jpg[/img]](http://a.imagehost.org/view/0869/screenshot_001)

---

### Post by matias_tati on 2009-09-03
Que me quiere decir con esto? Por que no me muestra el cover del exaile. Que debo hacer?

[[img]http://a.imagehost.org/t/0193/Escritorio-conky-colors.jpg[/img]](http://a.imagehost.org/view/0193/Escritorio-conky-colors)

---

### Post by Mustaine666 on 2009-09-05
se puede usar en conky con amarok.. y no con Rhythmbox.. voy a ver si aunque sea puedo instalarlo..

---

### Post by Mustaine666 on 2009-09-06
despues de pelear por mucho tiempo ... 

[[img]http://h.imagehost.org/t/0979/Pantallazo.jpg[/img]](http://h.imagehost.org/view/0979/Pantallazo)

---

### Post by matias_tati on 2009-09-07
Es el conky colors?
Porque a mi me quedo distinto.....

[[img]http://h.imagehost.org/t/0034/Pantallazo.jpg[/img]](http://h.imagehost.org/view/0034/Pantallazo)

---

### Post by Mustaine666 on 2009-09-07
si lo q pasa es q utilice otro  conkyrc .. igual borre la carpeta de coky del escritorio.. y ahora no anda mas! ..

---

