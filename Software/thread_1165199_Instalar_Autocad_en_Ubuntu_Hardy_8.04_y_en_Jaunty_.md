---
title: "Instalar Autocad en Ubuntu Hardy 8.04 y en Jaunty Jackalope 9.04"
date: 2009-05-20
forum: Software
---

### Post by icarofallen on 2009-05-20
Holas a todos, este es un post que tenia en el foro antiguo, y que volvere a subir para ver si alguien le sirve

Primero, espero que este pequeño tutorial ayude a personas que como yo trató de instalar de muchas maneras diferentes el famoso Autocad en Ubuntu y poder hacer que corra bien, a mi me ha funcionado ya en 3 pc's, con lo cual creo estar seguro de haberlo hecho bien XD, pero si a alguien no le funciona con gusto tratare de ayudarlo... 
 
Me base en un tutorial que encontre en la web  [http://citywiki.ugr.es/wiki/Tutorial_para_instalar_autocad_2006_en_Ubuntu_8.10](http://citywiki.ugr.es/wiki/Tutorial_para_instalar_autocad_2006_en_Ubuntu_8.10) 
 
Y ahora los pasos a seguir, 
 
1º instalar la ultima version de Wine, desde la consola: 
wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add - 
 
Luego: 
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list](http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/winehq.list 
 
Y estamos casi listos con wine, solo falta bajarse el .deb de la pag de wine  [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb) 
 
o hacerlo desde   Aplicaciones-> Agregar o quitar y busque por Wine 
 
con esto ya tenemos listos la primera parte, ahora los truquitos  [IMG]http://foros.ubuntu-cl.org/images/smiles/icon_biggrin.gif[/IMG]  
 
Abre una terminal (en el panel superior->Aplicaciones->Accesorios->Terminal)  
Accede al directorio de wine introduciendo en la consola:  
 
cd ~./wine/ 
 
A continuación píllate el winetricks así:  
 
wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks) 
 
Ahora ejecuta esto para instalar un complemento de los paquetes microsoft  [IMG]http://foros.ubuntu-cl.org/images/smiles/icon_evil.gif[/IMG] 
 
sudo apt-get install cabextract 
 
Y esto instalará el .net framework 
 
sh winetricks dotnet20 allfonts 
 
ya con eso estamos en condiciones de comenzar a instalar nuestro autocad: 
 
recomiendo copiar todos los archivos de instalacion a alguna carpeta en nuestro PC, una vez allí, vamos a executable de instalación y con un doble click comenzara el proceso tal cual como lo haría en el otro..... [IMG]http://foros.ubuntu-cl.org/images/smiles/icon_evil.gif[/IMG]   (prefiero no nombrarlo) 
 
En el Autocad 2004 no se debe modificar ningún archivo, se debe correr tal como siempre. 
 
Un punto importante, durante la instalacién se preguntara por un procesador de textos, que debe ser el notepad, se debe poner examinar y buscar en C: el notepad.exe y seleccionarlo. La ruta es /home/NOMBREUSUARIO/.wine/windows/notepad.exe 
 
Bueno esos son todos los pasos, espero que les ayude, y pronto espero poder instalar versiones más recientes, jeje 
 
P.D: solo ocurre un error que no se pueden visualizar las barras de herramientas, pero se pueden ejecutar por comandos de teclado o a travez del menu principal, pero aparte de eso,todo funciona perfecto [IMG]http://foros.ubuntu-cl.org/images/smiles/icon_smile.gif[/IMG]

---

### Post by Carlos C on 2009-05-20
Gracias icarofallen. Te edité un detalle. Por favor [mira las normas]("http://ubuntuforums.org/showthread.php?t=1162750"). Estamos tratando de evitar expresiones del tipo "Micro$ot" para seguir el espíritu del [CoC]("http://ubuntuforums.org/index.php?page=policy") ;)

---

### Post by icarofallen on 2009-05-22
gracias, y me comprometo a no hacer comentarios de esa indole, y no habia leido las normas, pero ahora las leere XD.

---

### Post by Carlos C on 2009-06-08
[Post de la semana]("http://ubuntuforums.org/showthread.php?t=1176055"): [Junio 8, 2009]("http://ubuntucl.wordpress.com/2009/06/08/instalar-autocad-en-ubuntu-hardy-8-04-y-en-jaunty-jackalope-9-04/")

---

### Post by robertor on 2009-06-08
> **icarofallen said:**
>  
P.D: solo ocurre un error que no se pueden visualizar las barras de herramientas, pero se pueden ejecutar por comandos de teclado o a travez del menu principal, pero aparte de eso,todo funciona perfecto [IMG]http://foros.ubuntu-cl.org/images/smiles/icon_smile.gif[/IMG]

Creo que es el mismo error que me ocurria con el PowerDesigner, que la barra de tareas se veia una ventana de color gris, sin poder apreciar el contenido de esta. Si es así, la "maña" que yo le pille era redimensionarla y luego hacerle varios clicks rápidos sobre esta. Ahí se cargaban los iconos de la varra de herramientas.
Saludos!
Roberto

---

### Post by arka6 on 2009-10-18
Es una sorpresa ver que mi tutorial se expande. Es una lástima que lo hiciera con tanta prisa. Creo que hay un par de cosas que se me olvidaron.
Para instalar el autocad 2006 habría que instalar adicionalmente los paquetes de msxml y gdiplus, o sea

> sh winetricks gdiplus msxml6

Es posible que también vaya bien algunos paquetes correspondientes al MDAC pero aun no los he probado.
Para el autocad 2006 hay que hacer, además, una ligeras modificaciones en el archivo de configuración de la instalación, para que no se empeñe en instalar versiones antiguas. Está todo en

[CITYwiki]("http://citywiki.ugr.es/wiki/Tutorial_para_instalar_autocad_2006_en_Ubuntu_8.10")

El problema por resolver es el tema del registro, aparentemente no se renderiza correctamente la pantalla donde pegar el código. ¿Alguna sugerencia?

---

### Post by DobleA on 2009-10-20
Yo logré instalar el 2008. [Acá]("http://www.lp.com.uy/foros/index.php?/topic/83760-ubuntu-904-autocad-2008-wine-combinacion-casi-posible/") pueden ver como hice, y de hecho es bastante sencillo. Aun falta cambiar el titulo del thread =P

Suerte.

---

### Post by moreback on 2009-10-20
> **DobleA said:**
> Yo logré instalar el 2008. [Acá]("http://www.lp.com.uy/foros/index.php?/topic/83760-ubuntu-904-autocad-2008-wine-combinacion-casi-posible/") pueden ver como hice, y de hecho es bastante sencillo. Aun falta cambiar el titulo del thread =P

Suerte.

¿Y qué tal el funcionamiento? ¿Haz encontrado alguna diferencia respecto a instalarlo en Windows?

Saludos.

---

### Post by arka6 on 2009-10-23
Alucino, el 2008 ya anda sobre ubuntu... Un pasote. De todas maneras creo es más estable el 2006, en [winehq]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=86") ya tiene la calificación gold. 
Moreback,  el rendimiento no parece superar al de windows, más que nada la visualización no es tan suave (aunque sin efectos visuales de escritorio mejora bastante), y aún queda pulir un poco algunos bugs, sobretodo en un programa par uso profesional como este.[U]
[/U]

---

### Post by beto1 on 2010-02-11
Estimados,
estoy por comprar un pc nuevo armado y opté por usar ubuntu.
soy usuario de autocad desde hace muchos años y photoshop. mi pregunta es por la estabilidad del programa en ubuntu, instaldo con wine. Básicamente se ha descrito cómo se hace la instalación, pero me gustaría saber la experiencia de alguien que lo use todos los días bajo ubuntu. ¿es mejor? ¿es estable? ¿hay algún detalle que sea incompatible o no funcione apropiadamente?
Pregunto esto básicamente porque en la empresa que me armarán el computador no tienen problema en instalarme el ubuntu y me han dicho que no tendré problemas con el photoshop, pero que mas de algún cliente arquitecto ha tenido algún problema con el autocad y  ha tenido que devolver el equipo para una revisión.
saludos,
beto

---

### Post by xtremox on 2010-02-11
podrias usar blender pero el wine es una buena opcion

---

### Post by icarofallen on 2010-03-31
Hola beto, mira en lo personal, no le he dado un uso muy fuerte, eso si he probado con modelos 3d, algunos dibujos grandes, y no me ha dado problemas, tengo instalado si el 2004, ya que el 2006 me da problemas para el crack, y lo encuentro mas estable.
Ya no tengo problemas con la barra de tareas ni nada, es correrlo tal cual en XP, creo que esto se debio a las versiones que estoy usando tanto wine (1.1.39) como ubuntu (9.10).
Espero esta informacion te sea de ayuda.
saludos

---

