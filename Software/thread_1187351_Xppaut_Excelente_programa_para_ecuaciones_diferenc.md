---
title: "Xppaut: Excelente programa para ecuaciones diferenciales"
date: 2009-06-14
forum: Software
---

### Post by Fisaulerod on 2009-06-14
Xppaut es un ligero y potente programa científico para la resolución de ecuaciones diferenciales, sistemas lineales y no lineales, especial para la modelación de diversos problemas matemáticos. La programación es muy sencilla y tiene soporte a gráficos 3D, animaciones, entre otras muchas posibilidades. Cabe destacar que al ser un programa específico, todas sus funcionalidades están enfocadas a las ecuaciones diferenciales y a la modelación. Como dato freak, Xppaut fue desarrollado inicialmente para la modelación de ciertos problemas biológicos (como las plagas).

**Instalación:**

Primero vayan a: [http://www.math.pitt.edu/~bard/xpp/download.html](http://www.math.pitt.edu/~bard/xpp/download.html), y se bajan la última version: Source code for the latest version.  Luego lo descomprimen y lo dejan en una carpeta conocida y accequible (por ejemplo /home/programas/xppaut_latest). Una vez descomprimido abran la terminal y se van a la carpeta donde se descomprimió el programa, por ejemplo:

```
cd programas

cd xppaut_latest
```

Una vez allí, lo compilan:

```
make 
```

Si el proceso se demora un buen tiempo y no da ningun error, significa que todo ha ido bien.  Para comprobarlo tipean:

```
ls xppaut
```

Si sale marcado xppaut (verde en mi caso), el programa quedó perfectamente instalado.

Ahora asociaremos los archivos .ode a xppaut. Para ello nos vamos a la carpeta ode (dentro de la carpeta del programa: /xppaut_latest/ode) y hacemos click derecho en un archivo .ode (6×6.ode por ejemplo). Se van a Propiedades y allí a la pestaña abrir con, hacen click en el boton añadir y en la nueva ventana ponen usar comando personalizado, allí ponen examinar. Finalmente se van a la carpeta del programa y buscan un archivo que se llama xppaut (sin extensión), ponen aceptar a todo y los archivos .ode ya están asociados.


Para abrirlos sólo hace falta hacer doble click sobre los archivos .ode, pero deben recordar que para programar se debe usar un editor de textos como Gedit o Leafpad.

Espero muy pronto hacer un tutorial de cómo usar el programa, ya que hay nula documentación en español y el programa se lo merece. Por mientras pueden ver los ejemplos que hay en la carpeta ode.

P.D: Esto lo copié de mi blog: [http://linuxisnotfreedom.wordpress.com/](http://linuxisnotfreedom.wordpress.com/). Es nuevo...y eso xD, ahí puse una imágen de programa para que se hagan una idea.

---

### Post by Carlos C on 2009-06-14
Ojalá puedas hacer un how-to con imágenes y todo eso. Yo estoy tomando nota de cada how-to que se añade al foro y lo tengo en mente para el [[COLOR="DarkRed"]post de la semana[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1176055").

---

### Post by zhelo on 2009-06-14
se ve interesante, gracias

---

### Post by Fisaulerod on 2009-06-14
Ya, lo antes posible trataré de ponerle imágenes.
Es un software muy interesante y con muchas posibilidades, lamentablemente hay practicamente nula documentación, incluso en inglés. Cuando salga de vacaciones..que no es en mucho tiempo, creo que haré un pequeño tutorial,tampoco soy un experto en el programa ni mucho menos, pero ya un poco de documentación creo que podría ser útil.

---

### Post by Fisaulerod on 2009-06-14
Aquí unas imágenes sobre la instalación y del programa:

[ATTACH]117702[/ATTACH]

[ATTACH]117703[/ATTACH]

[ATTACH]117704[/ATTACH]

[ATTACH]117706[/ATTACH]

[ATTACH]117707[/ATTACH]

Como pueden ver, en el menu del programa sale para cambiar las condiciones iniciales, los parametros a graficar, entre otras muchas cosas. Sé que al comienzo se ve muy feo, pero no es verdad xD. 
Para correr el programa por defecto, con las condiciones iniciales dadas y la variable a graficar puesta en el código, se van a Initial Cond. y ponen Go.

---

### Post by Fisaulerod on 2009-06-15
Hola. Instalando este mismo programa, un amiga tiene un problema al hacer el make, le sale esto:

                           ```
ximena@xime:~/Escritorio/xppaut_latest$ make
    cd libI77 ; make
    make[1]: se ingresa al directorio `/home/ximena/Escritorio/xppaut_latest/libI77'
    ar r libf2cm.a Version.o backspace.o dfe.o due.o iio.o inquire.o rewind.o rsfe.o rdfmt.o sue.o uio.o wsfe.o sfe.o fmt.o lio.o lread.o open.o close.o util.o endfile.o wrtfmt.o wref.o err.o fmtlib.o rsne.o wsne.o fc77.o f2cstart.o
    ranlib libf2cm.a
    cp libf2cm.a ../.
    make[1]: se sale del directorio `/home/ximena/Escritorio/xppaut_latest/libI77'
    cd cvodesrc ; make
    make[1]: se ingresa al directorio `/home/ximena/Escritorio/xppaut_latest/cvodesrc'
    (ar rcv libcvode.a cvode.o  cvdense.o  dense.o  cvband.o band.o  cvdiag.o  cvspgmr.o  spgmr.o iterativ.o  vector.o  llnlmath.o cv2.o; ranlib libcvode.a ; cp libcvode.a ../.)
    r - cvode.o
    r - cvdense.o
    r - dense.o
    r - cvband.o
    r - band.o
    r - cvdiag.o
    r - cvspgmr.o
    r - spgmr.o
    r - iterativ.o
    r - vector.o
    r - llnlmath.o
    r - cv2.o
    make[1]: se sale del directorio `/home/ximena/Escritorio/xppaut_latest/cvodesrc'
    gcc -g -O -DMACOSX -DAUTO -DCVODE_YES  -DMYSTR=5.98 -I/usr/X11R6/include   -c -o main.o main.c
    main.c:25:22: error: X11/Xlib.h: No existe el fichero ó directorio
    main.c:26:23: error: X11/Xutil.h: No existe el fichero ó directorio
    main.c:27:21: error: X11/Xos.h: No existe el fichero ó directorio
    main.c:28:24: error: X11/Xproto.h: No existe el fichero ó directorio
    main.c:29:23: error: X11/Xatom.h: No existe el fichero ó directorio
    In file included from main.c:36:
    browse.h:3: error: expected specifier-qualifier-list before ‘Window’
    In file included from main.c:37:
    struct.h:24: error: expected specifier-qualifier-list before ‘Window’
    struct.h:41: error: expected specifier-qualifier-list before ‘Window’
    struct.h:68: error: expected specifier-qualifier-list before ‘GC’
    struct.h:74: error: expected specifier-qualifier-list before ‘Window’
    struct.h:84: error: expected specifier-qualifier-list before ‘Window’
    struct.h:93: error: expected specifier-qualifier-list before ‘Window’
    struct.h:101: error: expected specifier-qualifier-list before ‘Window’
    struct.h:116: error: expected specifier-qualifier-list before ‘Window’
    struct.h:127: error: expected specifier-qualifier-list before ‘Window’
    struct.h:133: error: expected specifier-qualifier-list before ‘Window’
    struct.h:146: error: expected specifier-qualifier-list before ‘Window’
    struct.h:151: error: expected specifier-qualifier-list before ‘Window’
    main.c:46:28: error: X11/cursorfont.h: No existe el fichero ó directorio
    main.c:66: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
    main.c:70: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘deleteWindowAtom’
    main.c:82: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘TopButton’
    main.c:83: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘init_win’
    main.c:84: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘make_fancy_window’
    main.c:86: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘draw_win’
    main.c:87: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘make_input_strip’
    main.c:88: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘main_win’
    main.c:89: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘command_pop’
    main.c:90: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gc’
    main.c:97: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
    main.c:108: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
    main.c: En la función ‘do_main’:
    main.c:148: aviso: declaración implícita incompatible de la función interna ‘strlen’
    main.c:167: error: ‘main_win’ no se declaró aquí (primer uso en esta función)
    main.c:167: error: (Cada identificador no declarado solamente se reporta una vez
    main.c:167: error: para cada funcion en la que aparece.)
    main.c:221: error: ‘display’ no se declaró aquí (primer uso en esta función)
    main.c: En la función ‘init_X’:
    main.c:263: error: ‘main_win’ no se declaró aquí (primer uso en esta función)
    main.c:268: error: ‘display’ no se declaró aquí (primer uso en esta función)
    main.c:279: error: ‘ExposureMask’ no se declaró aquí (primer uso en esta función)
    main.c:279: error: ‘KeyPressMask’ no se declaró aquí (primer uso en esta función)
    main.c:279: error: ‘ButtonPressMask’ no se declaró aquí (primer uso en esta función)
    main.c:280: error: ‘StructureNotifyMask’ no se declaró aquí (primer uso en esta función)
    main.c:280: error: ‘ButtonReleaseMask’ no se declaró aquí (primer uso en esta función)
    main.c:280: error: ‘ButtonMotionMask’ no se declaró aquí (primer uso en esta función)
    main.c:282: aviso: declaración implícita incompatible de la función interna ‘strcpy’
    main.c:287: error: ‘big_font’ no se declaró aquí (primer uso en esta función)
    main.c:290: error: ‘small_font’ no se declaró aquí (primer uso en esta función)
    main.c:308: error: ‘gc’ no se declaró aquí (primer uso en esta función)
    main.c:309: error: ‘gc_graph’ no se declaró aquí (primer uso en esta función)
    main.c:310: error: ‘small_gc’ no se declaró aquí (primer uso en esta función)
    main.c:311: error: ‘font_gc’ no se declaró aquí (primer uso en esta función)
    main.c: En la función ‘set_big_font’:
    main.c:327: error: ‘display’ no se declaró aquí (primer uso en esta función)
    main.c:327: error: ‘gc’ no se declaró aquí (primer uso en esta función)
    main.c:327: error: ‘big_font’ no se declaró aquí (primer uso en esta función)
    main.c: En la función ‘set_small_font’:
    main.c:335: error: ‘display’ no se declaró aquí (primer uso en esta función)
    main.c:335: error: ‘gc’ no se declaró aquí (primer uso en esta función)
    main.c:335: error: ‘small_font’ no se declaró aquí (primer uso en esta función)
    main.c: En el nivel principal:
    main.c:341: error: expected ‘)’ before ‘report’
    main.c: En la función ‘do_events’:
    main.c:465: error: ‘XEvent’ no se declaró aquí (primer uso en esta función)
    main.c:465: error: expected ‘;’ before ‘report’
    main.c:467: error: ‘main_win’ no se declaró aquí (primer uso en esta función)
    main.c:476: error: ‘display’ no se declaró aquí (primer uso en esta función)
    main.c:476: error: ‘report’ no se declaró aquí (primer uso en esta función)
    main.c: En la función ‘bye_bye’:
    main.c:487: error: ‘display’ no se declaró aquí (primer uso en esta función)
    main.c:487: error: ‘big_font’ no se declaró aquí (primer uso en esta función)
    main.c:488: error: ‘small_font’ no se declaró aquí (primer uso en esta función)
    main.c:490: error: ‘symfonts’ no se declaró aquí (primer uso en esta función)
    main.c:491: error: ‘romfonts’ no se declaró aquí (primer uso en esta función)
    main.c:493: error: ‘gc’ no se declaró aquí (primer uso en esta función)
    main.c: En la función ‘clr_scrn’:
    main.c:500: error: ‘draw_win’ no se declaró aquí (primer uso en esta función)
    main.c: En la función ‘redraw_all’:
    main.c:511: error: ‘BROWSER’ no tiene un miembro llamado ‘maxrow’
    main.c:512: error: ‘draw_win’ no se declaró aquí (primer uso en esta función)
    main.c: En el nivel principal:
    main.c:736: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘init_win’
    main.c:742: error: expected identifier or ‘(’ before ‘{’ token
    main.c:825: error: expected ‘)’ before ‘w’
    main.c:841: error: expected ‘)’ before ‘w’
    main.c:850: error: expected ‘)’ before ‘w’
    main.c:878: error: expected ‘)’ before ‘report’
    main.c: En la función ‘make_top_buttons’:
    main.c:900: error: ‘TopButton’ no se declaró aquí (primer uso en esta función)
    main.c:900: error: ‘main_win’ no se declaró aquí (primer uso en esta función)
    main.c: En la función ‘getGC’:
    main.c:919: error: expected declaration specifiers before ‘GC’
    main.c:922: error: ‘XGCValues’ no se declaró aquí (primer uso en esta función)
    main.c:922: error: expected ‘;’ before ‘values’
    main.c:930: error: argumento de tipo inválido de ‘unary *’ (se tiene ‘int’)
    main.c:930: error: ‘display’ no se declaró aquí (primer uso en esta función)
    main.c:930: error: ‘main_win’ no se declaró aquí (primer uso en esta función)
    main.c:930: error: ‘values’ no se declaró aquí (primer uso en esta función)
    main.c:931: error: argumento de tipo inválido de ‘unary *’ (se tiene ‘int’)
    main.c: En la función ‘load_fonts’:
    main.c:940: error: ‘big_font’ no se declaró aquí (primer uso en esta función)
    main.c:940: error: ‘display’ no se declaró aquí (primer uso en esta función)
    main.c:946: error: ‘small_font’ no se declaró aquí (primer uso en esta función)
    main.c:954: error: ‘symfonts’ no se declaró aquí (primer uso en esta función)
    main.c:966: error: ‘romfonts’ no se declaró aquí (primer uso en esta función)
    main.c: En la función ‘make_pops’:
    main.c:988: error: ‘Window’ no se declaró aquí (primer uso en esta función)
    main.c:988: error: expected ‘;’ before ‘wn’
    main.c:989: error: ‘Cursor’ no se declaró aquí (primer uso en esta función)
    main.c:989: error: expected ‘;’ before ‘cursor’
    main.c:990: error: ‘display’ no se declaró aquí (primer uso en esta función)
    main.c:990: error: ‘main_win’ no se declaró aquí (primer uso en esta función)
    main.c:990: error: ‘wn’ no se declaró aquí (primer uso en esta función)
    main.c:996: error: ‘command_pop’ no se declaró aquí (primer uso en esta función)
    main.c:999: error: ‘info_pop’ no se declaró aquí (primer uso en esta función)
    main.c:1002: error: ‘cursor’ no se declaró aquí (primer uso en esta función)
    main.c:1002: error: ‘XC_hand2’ no se declaró aquí (primer uso en esta función)
    main.c:1005: error: ‘KeyPressMask’ no se declaró aquí (primer uso en esta función)
    main.c:1005: error: ‘ButtonPressMask’ no se declaró aquí (primer uso en esta función)
    main.c:1005: error: ‘ExposureMask’ no se declaró aquí (primer uso en esta función)
    main.c: En la función ‘FixWindowSize’:
    main.c:1018: error: expected declaration specifiers before ‘Window’
    main.c:1021: error: ‘XSizeHints’ no se declaró aquí (primer uso en esta función)
    main.c:1021: error: expected ‘;’ before ‘size_hints’
    main.c:1024: error: ‘size_hints’ no se declaró aquí (primer uso en esta función)
    main.c:1024: error: ‘PSize’ no se declaró aquí (primer uso en esta función)
    main.c:1024: error: ‘PMinSize’ no se declaró aquí (primer uso en esta función)
    main.c:1024: error: ‘PMaxSize’ no se declaró aquí (primer uso en esta función)
    main.c:1046: error: ‘display’ no se declaró aquí (primer uso en esta función)
    main.c: En la función ‘getxcolors’:
    main.c:1054: error: expected declaration specifiers before ‘XWindowAttributes’
    main.c:1055: error: expected declaration specifiers before ‘XColor’
    main.c:1061: error: argumento de tipo inválido de ‘unary *’ (se tiene ‘int’)
    main.c:1061: error: ‘XColor’ no se declaró aquí (primer uso en esta función)
    main.c:1061: error: expected expression before ‘)’ token
    main.c:1063: error: argumento de tipo inválido de ‘->’ (se tiene ‘int’)
    main.c:1063: error: ‘TrueColor’ no se declaró aquí (primer uso en esta función)
    main.c:1069: error: argumento de tipo inválido de ‘->’ (se tiene ‘int’)
    main.c:1074: error: argumento de tipo inválido de ‘->’ (se tiene ‘int’)
    main.c:1077: error: argumento de tipo inválido de ‘unary *’ (se tiene ‘int’)
    main.c:1077: error: expected expression before ‘)’ token
    main.c:1080: error: argumento de tipo inválido de ‘->’ (se tiene ‘int’)
    main.c:1080: error: ‘DirectColor’ no se declaró aquí (primer uso en esta función)
    main.c:1086: error: argumento de tipo inválido de ‘->’ (se tiene ‘int’)
    main.c:1086: error: argumento de tipo inválido de ‘->’ (se tiene ‘int’)
    main.c:1087: error: argumento de tipo inválido de ‘->’ (se tiene ‘int’)
    main.c:1087: error: argumento de tipo inválido de ‘->’ (se tiene ‘int’)
    main.c:1088: error: argumento de tipo inválido de ‘->’ (se tiene ‘int’)
    main.c:1088: error: argumento de tipo inválido de ‘->’ (se tiene ‘int’)
    main.c:1090: error: argumento de tipo inválido de ‘unary *’ (se tiene ‘int’)
    main.c:1091: error: argumento de tipo inválido de ‘unary *’ (se tiene ‘int’)
    main.c:1093: error: argumento de tipo inválido de ‘->’ (se tiene ‘int’)
    main.c:1095: error: argumento de tipo inválido de ‘->’ (se tiene ‘int’)
    main.c:1097: error: argumento de tipo inválido de ‘->’ (se tiene ‘int’)
    main.c:1102: error: argumento de tipo inválido de ‘unary *’ (se tiene ‘int’)
    main.c:1103: error: argumento de tipo inválido de ‘unary *’ (se tiene ‘int’)
    main.c:1107: error: ‘display’ no se declaró aquí (primer uso en esta función)
    main.c:1107: error: argumento de tipo inválido de ‘->’ (se tiene ‘int’)
    main.c:1107: error: argumento de tipo inválido de ‘unary *’ (se tiene ‘int’)
    main.c: En la función ‘test_color_info’:
    main.c:1120: error: ‘XColor’ no se declaró aquí (primer uso en esta función)
    main.c:1120: error: ‘colors’ no se declaró aquí (primer uso en esta función)
    main.c:1121: error: ‘XWindowAttributes’ no se declaró aquí (primer uso en esta función)
    main.c:1121: error: expected ‘;’ before ‘xwa’
    main.c:1125: error: ‘display’ no se declaró aquí (primer uso en esta función)
    main.c:1125: error: ‘main_win’ no se declaró aquí (primer uso en esta función)
    main.c:1125: error: ‘xwa’ no se declaró aquí (primer uso en esta función)
    make: *** [main.o] Error 1

```



Supongo que le falta alguna librería o algo, no entiendo mucho de eso. A mí y a otras personas les funcionó, ¿qué le falta? Gracias de antemano...

---

### Post by moreback on 2009-06-16
Parece que le falta un paquete de desarrollo de X11, ya que no te encuentra varios archivos .h. Lo ideal es que ejecutes esto en tu sistema (no el de ella) para ver a qué paquete pertenecen esos archivos

```
dpkg -S /usr/X11R6/include/X11/Xlib.h
```

Luego instalas esos paquetes en el pc de tu amigui.

Saludos!

---

### Post by Patriciologico on 2009-08-24
Publicado como [Post de la Semana]("http://ubuntuforums.org/showthread.php?t=1176055"): [24 de agosto]("http://www.ubuntu-cl.org/grupos/foro/xppaut-aplicacion-para-ecuaciones-diferenciales") de 2009

¡Felicitaciones!

---

### Post by Angela- on 2009-09-02
Yo no lo pude instalar de esa forma, aparecieron errores en el terminal, así que bajé un binario que funciona bien ([xppaut5.98-linux-binary.tgz)]("http://www.math.pitt.edu/%7Ebard/bardware/binary/xppaut5.98-linux-binary.tgz")

---

### Post by Patriciologico on 2009-09-02
> **Angela- said:**
> Yo no lo pude instalar de esa forma, aparecieron errores en el terminal, así que bajé un binario que funciona bien ([xppaut5.98-linux-binary.tgz)]("http://www.math.pitt.edu/%7Ebard/bardware/binary/xppaut5.98-linux-binary.tgz")

Buen Dato, lo agregare en la entrada de la web [Ubuntu-cl.org]("http://www.ubuntu-cl.org/grupos/foro/xppaut-aplicacion-para-ecuaciones-diferenciales").

Agrego ademas que para revisar la última versión compilada pueden visitar 

[http://www.math.pitt.edu/~bard/bardware/binary/?C=M;O=D](http://www.math.pitt.edu/~bard/bardware/binary/?C=M;O=D)

Saludos!

---

### Post by franlanderreche on 2011-04-25
Hola, quiero instalarlo haciendo lo que me decis y me salta esta error:

fran@ubuntu:~/Descargas/xppaut$ make
gcc -g -O -m32 -DNON_UNIX_STDIO -DAUTO -DCVODE_YES  -DHAVEDLL -DMYSTR1=6.0 -DMYSTR2=10  -I/usr/X11R6/include   -c -o main.o main.c
In file included from /usr/include/features.h:387,
                 from /usr/include/stdlib.h:25,
                 from main.c:1:
/usr/include/gnu/stubs.h:7: fatal error: gnu/stubs-32.h: No existe el fichero o el directorio
compilation terminated.
make: *** [main.o] Error 1
fran@ubuntu:~/Descargas/xppaut$

que puedo hacer para solucionarlo?

---

### Post by Patriciologico on 2011-04-26
> **franlanderreche said:**
> Hola, quiero instalarlo haciendo lo que me decis y me salta esta error:

fran@ubuntu:~/Descargas/xppaut$ make
gcc -g -O -m32 -DNON_UNIX_STDIO -DAUTO -DCVODE_YES  -DHAVEDLL -DMYSTR1=6.0 -DMYSTR2=10  -I/usr/X11R6/include   -c -o main.o main.c
In file included from /usr/include/features.h:387,
                 from /usr/include/stdlib.h:25,
                 from main.c:1:
/usr/include/gnu/stubs.h:7: fatal error: gnu/stubs-32.h: No existe el fichero o el directorio
compilation terminated.
make: *** [main.o] Error 1
fran@ubuntu:~/Descargas/xppaut$

que puedo hacer para solucionarlo?

Baja el binario, te falto leer esto --> [http://ubuntuforums.org/showpost.php?p=7888611&postcount=10](http://ubuntuforums.org/showpost.php?p=7888611&postcount=10)

Saludos!

---

