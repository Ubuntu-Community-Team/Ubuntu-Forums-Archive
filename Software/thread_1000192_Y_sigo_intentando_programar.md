---
title: "Y sigo intentando programar"
date: 2008-12-02
forum: Software
---

### Post by erdosain9 on 2008-12-02
Hola a todos... bueno. El tema es que me he metido a intentar aprender a programar en C++... pues bien... les comento que estoy siguiendo un videotutorial que hasta donde voy (cap 10) me parece excelente... tal vez un poco lentín, pero prefiero lento a rápido y no entender nada (después de todo se puede adelantar)

La página del videotutorial es esta: [www.videotutoriales.com](www.videotutoriales.com)

Mi pregunta es en relación a un archivo que se llama conio.h  que he leído no existe para linux... qué se hace con esto??????? (bien no sé para qué sirve porque hasta donde llegué en el tutorial no lo hemos visto... pero si lo noté al bajar algunos código fuente para ir probando)

Saludos y gracias

---

### Post by chalito on 2008-12-02
Hmm mi C/C++ esta bastante oxidado, pero conio.h es el header file para la libreria de manejo de consola en DOS/windows (CONsole I/O). Esa librería no es parte estándar de C/C++, por eso no está en linux. Lo que podes hacer es sacar ese include, y fijate para que se lo usa (que funciones de conio.h son llamadas) y después tratar de averiguar como se implementan esas funciones en linux. Por ejemplo habia una funcion para limpiar la pantalla y getch(). 

fijate aca:
[http://en.wikipedia.org/wiki/Conio.h](http://en.wikipedia.org/wiki/Conio.h)

Y despues si necesitas usarlo, algunas de las funcionalidades de conio las podes encontrar en ncurses, creo.

---

### Post by erdosain9 on 2008-12-02
mmm, muchas gracias...
el ncurses de donde lo saco y cómo lo instalo...
documentación????

Saludos y gracias

---

### Post by MeduZa on 2008-12-02
> **erdosain9 said:**
> mmm, muchas gracias...
el ncurses de donde lo saco y cómo lo instalo...
documentación????

Saludos y gracias

yo tambien estoy programando en c++ y podriamos intercambiar problemas jejejeje 
la curses esta en synaptics pero seguramente ya la tengas instalada.

---

### Post by erdosain9 on 2008-12-02
Hola MeduZa qué tal???
Gracias por contestar... ya instalé las ncurses... haciendo un apt-get...
y vi un par de documentación... igual sólo por arriba porque como estoy recién aprendiendo como que tengo la oportunidad de usar nada de eso...
Si vos también estás comenzando podríamos intercambiarnos un par de cosas, ejemplos, etc... si te parece ¿? (o si me querés ayudar)
Te mando un saludo
  Erdosain9

---

### Post by erdosain9 on 2008-12-03
Para no abrir un nuevo tema...
En el tutorial enseñaron cómo hacer una clase y mandarla a un archivo .hpp
luego hacer #inlude e "incorporarla" en el cpp... pues bien... trabajando con geany... cómo demonios se hace eso??? me refiero a que funcione...porque al poner compilar desde el cpp... me da un error de tal hpp no existe... y cosas así!

ayuda!!!!

---

### Post by erdosain9 on 2008-12-03
mmm. hago una pregunta en el medio...
eh... cómo es que se ejecutan estos archivos que me da el compilador de Geany... porque todo bien si desde geany pongo ejecutar pero si voy al archivo y le hago doble clic... no pasa nada... son ese tipo de archivos que cuyo icono es un rombo de tonalidad azul y que parecen tener engranajes...

Pregunta tonta seguro pero no sólo soy nuevo en programación sino que lo soy también bastante en linux......

saludos y gracias

---

### Post by erdosain9 on 2008-12-03
Bueno... ya di con la respuesta a la pregunta sobre el #include... parece que al agregar este tipo de archivos no hay que hacerlo entre <.....> sino entre ".....".  Por cierto, alguien sabe para qué es en herramientas el plugin llamado "Constructor de Clases" cómo se usa esto??

p.d.: lo peor de todo es que en el tutorial estaba entre "...."(comillas)...

---

### Post by MeduZa on 2008-12-04
> **erdosain9 said:**
> Bueno... ya di con la respuesta a la pregunta sobre el #include... parece que al agregar este tipo de archivos no hay que hacerlo entre <.....> sino entre ".....".  Por cierto, alguien sabe para qué es en herramientas el plugin llamado "Constructor de Clases" cómo se usa esto??

p.d.: lo peor de todo es que en el tutorial estaba entre "...."(comillas)...

te recomiendo que uses anjuta que te hace algunas cosas solo!
tambien podrias usar code::blocks que es muy completo pero no me gusta porque no usa de base el sistema de Makefile xD

yo hace unos meses estaba mas o menos como vos, no solo tenia una capa mas grande que el perito moreno de oxido de no usar c++ en años (muchos) sino que ademas estaba en un entorno totalmente diferente y queriendo compilar multiplataforma :S, creo que me lei media web !

mandame por MP tu msn icq aol u de donde mandas se&#505;ales de humo asi hablamos del tema yo estoy con un problema que no se como solucionar U_U

---

