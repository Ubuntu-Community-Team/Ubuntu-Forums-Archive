---
title: "Dudas con Remastersys"
date: 2009-02-24
forum: Software
---

### Post by carcar8 on 2009-02-24
Hola, Salu2!

Tengo una duda con Remastersys.
Lo instale en modo gráfico.
Intente generar una ISO del sistema completo incluyendo archivos personales.
Genera casi todo pero se interrumpe el proceso en el 99 %.
Revise el directorio Home/Remastersys y encuentro varias carpetas, entre ellas una llamada ISOTEMP.
Falta que habilite algo mas?
Se supone que debe terminar con una .ISO para grabarla luego con Brasero o 3KB?

Gracias

Carcar8

---

### Post by luks911 on 2009-02-24
En esa carpeta crea varios archivos, entre ellos una iso que después podés grabar y que por default va a llamarse custom.iso.
Lo he usado con buenos resultados. Me extraña que se interrumpa sin terminar. ¿Te da algún mensaje? ¿cuánto tiempo esperaste antes de cerralo?
Se me ocurren un par de cosas: 1) Fijate si en efecto generó la iso y 2) asegurate de que tengas suficiente espacio en el disco (Tené en cuenta que al querer incluir todos tus datos va a poner en la iso *todo* tu home, salvo que en las opciones le indiques que excluya alguna carpeta. Lo remarco porque si tenés, por ejemplo, archivos de música o video, los va a incluir y tal vez el resultado exceda la capacidad de un DVD, aunque es cierto que podés grabarlo en un USB con Unetbootin por ejemplo.

---

### Post by EnriqueK on 2009-02-25
Es mucho mejor usar la opción "distribuible" , la carpeta de usuario la podés grabar aparte, por ejemplo en un pendrive y así luego a esa carpeta la montas en el /home del Live DVD y así tendrás tu sistema con todo y además todas las modificaciones tanto en los documentos y configuraciones, serán persistentes por que estarán alojados en el pendrive o puede ser un DD externo, o tenerla en una partición del DD y así el Live DVD solo tendrá el directorio raíz y lógicamente las modificaciones no serán permanentes, pero eso no tendría mayor importancia si al Live DVD lo tienes bien surtido de programas.

Antes de crear la ISO, lo que hago siempre es desmontar todas las particiones, discos externos y red, además le hago una limpieza del caché de paquetes descargados, para dejar al sistema lo mas liviano posible (sudo aptitude clean && sudo apt-get clean)
Otra cosa, si vas a crear otra ISO, debes abrir nuevamente Remastersys y allí elegir la opción de borrar archivos temporales , esto además de quiar estos archivos que son bastante pesados, es necesario para que los datos estos no interfieran en la creación de la nueva ISO.

---

### Post by carcar8 on 2009-02-25
Gracias muchachos !

El problema es la falta de espacio (apenas queda 1Gb)
Voy a recurrir a un disco externo para generar la .ISO
Ahora la pregunta es: ¿Se pueden direccionar a otro disco los temporarios?
Sospecho que se satura con solo 1Gb de espacio.

Nota: Esta fue la primera instalación que hice de Ubuntu y en ese momento
ni siquiera tome en cuenta la partición HOME
solo esta ROOT y SWAP.

De otra forma tendre que instalar de cero creando la partición HOME como es aconsejable. (y con mucho más espacio)

Carcar8

---

### Post by luks911 on 2009-02-25
Todo es posible. Por un lado, podés cambiar el directorio de trabajo de Remastersys. Para eso, vas a la opción Modify y allí, con un doble click en Working Directory, cambiás la ruta por la de tu disco externo.
Y también podés separar tu / de tu /home en dos particiones diferentes sin necesidad de reinstalar, algo más que recomendable más allá de lo que querés hacer con Remastersys. Acá ([http://tuxpepino.wordpress.com/2007/09/18/independizando-el-home/](http://tuxpepino.wordpress.com/2007/09/18/independizando-el-home/)) hay un tutorial para hacerlo, parece largo porque está bastante explicado, cosa de que sepas qué hacés, pero no es difícil. Y acá ([http://bernux.blogspot.com/2008/05/separar-home.html](http://bernux.blogspot.com/2008/05/separar-home.html)) hay otro igual al que se le agrega un inconveniente al final con permisos y su solución.

---

### Post by carcar8 on 2009-02-25
Hola, SAlu2 !!

Gracias a Uds. estoy aprendiendo mucho. ;)

Espero poder retribuir en el futuro.
Si es que mis neuronas me lo permiten (tengo poca RAM ja )

Por ahora solo me llevo, mas adelante aportare.

Carcar8

---

