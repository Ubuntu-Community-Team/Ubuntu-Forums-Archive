---
title: "No puedo ejecutar ningun software"
date: 2009-04-04
forum: Software
---

### Post by ultimate64 on 2009-04-04
Hola soy un usuario nuevo de linux ubuntu y el primer y molesto problema es que no me deja ejecutar ningun tipo de software desde cd (los basicos como los drivers de la placa de video/sonido etc) el error es este : **"error al autoejecutar el software, no se ha podido encontrar el programa de arranque automatico"**

Si me pueden dar una manito se los agradesco.

saludos.

---

### Post by Hei Ku on 2009-04-04
Que programas son los que queres ejecutar?
En general, en linux no tenes arranque automatico de los CDs.
Ademas, seria bueno que nos contaras que version usas, y para que necesitas los drivers de video/sonido/etc. Es muy probable que lo que te venga en el CD no te haga falta, o no sean para linux.

---

### Post by ultimate64 on 2009-04-04
> **Hei Ku said:**
> Que programas son los que queres ejecutar?
En general, en linux no tenes arranque automatico de los CDs.
Ademas, seria bueno que nos contaras que version usas, y para que necesitas los drivers de video/sonido/etc. Es muy probable que lo que te venga en el CD no te haga falta, o no sean para linux.

Hola, uso la version 8.10 de ubuntu, y quiero instalar los drivers de la placa de video y los de audio, los del modem etc etc, tambien intente acceder al exe desde la carpeta pero no me deja ejecutar ninguno.

---

### Post by Hei Ku on 2009-04-04
Ehh, en linux no funcionan los exe. Podrias ejecutarlos usando wine, pero no es la solucion en este caso.

Para que necesitas los drivers de video y audio? Algo no te funciona?

En ese caso, abri una terminal y pone:
```

lspci

```

Copia el resultado que te tire y pegalo acá.

Decinos qué es lo que no te anda y te ayudamos.

---

### Post by guillermolisi on 2009-04-04
> **ultimate64 said:**
> Hola, uso la version 8.10 de ubuntu, y quiero instalar los drivers de la placa de video y los de audio, los del modem etc etc, tambien intente acceder al exe desde la carpeta pero no me deja ejecutar ninguno.
Normalmente y con la version que estas usando, no deberias tener necesidad de instalar drivers salvo que tengas video nVidia o ATI que requieren drivers especiales si queres usarlas a fondo.

Si fuera este el caso, esos drivers se bajan via Internet desde los repositorios de Ubuntu (en un proceso bastante transparente y sencillo).

Con lo que te pide HeiKu vamos a tener una buena idea sobre el hardware que estas usando y de ahi que drivers necesitarias.

---

### Post by guisheca on 2009-04-05
Emmmm muchachos, porque no dan un poco mas de info certera, no ven que es muy muy nuevo en el asunto? Diganle lo que necesita saber y lo tengan dando vueltas.

Ultimate64 primero que nada bienvenido a este mundo y felicitaciones por querer dar el gran paso.

Te explico, los archivos .exe no funcionan en GNU/Linux, es mas, sólo funcionan para windows. Es el formato de programas propio de windows. En ubuntu algo análogo serían los .deb [no es tan así pero por ahora basta con que creas que así lo es, después irás investigando].

En GNU/Linux la mayoría de los drivers de tu pc ya vienen instalados, son parte del sistema, de manera que no tenes que estar lidiando con cds de instalación y demás yerba. Esto es una historia aparte si tu hardware no está soportado por GNU/Linux, es decir, que el fabricante no libera versiones del controlador para nuestro sistema [te quiero decir con esto que no es un problema del sistema si no del fabricante]. También es otro caso si tenes, por ejemplo, una placa de video ATI o NVIDIA, si así lo es ya veremos que intrucciones te damos, pero no es nada del otro mundo.

Bueno creo que con eso está por ahora. Ahora si, abrí un terminal [Aplicaciones>Accesorios>Terminal] y escribí lo que te pusieron mas arriba, copiá y peganos el resultado para que te podamos ayudar [para copiar dentro del programa terminal tenés que seleccionar el texto de manera tradicional, pero usa botón derecho>copiar para hacerlo ya que ctrl+c no funcionan en el terminal, te toca a vos descubrir cuales son las teclas en ese caso :P]

Para mas info un buen comienzo es [http://guia-ubuntu.org](http://guia-ubuntu.org). Pero hay infinidad de info en internet a sólo un buscador [google, yahoo] de distancia. Pero cada ves que no encuentres una solución en internet contá con nosotros para lo que sea.

Saludos y suerte.

PD: escribí corchetes en ves de parentesis porque estuve desarmando mi teclado para limpiarlo y ahora resulta que muchas de mis teclas no andan :lolflag: incluyendo el parentesis :P

---

### Post by infernus92 on 2009-04-05
bueno... como ya dijeron los otros usuarios que postearon aca... los archivos exe no funcionan en linux
para los usuarios nuevos (yo hace algunos meses) y especialmente los que vienen desde window$ esto es un problema...
revisa tu nuevo sistema... te vas a dar cuenta de muchas cosas... por ejemplo... no tenes disco C, D, etc...
GNU/Linux como todos los sistemas derivados de Unix utlilizan una sola carpeta raiz llamada /
desde / podes entrar a cualquier lugar de tu sistema
otra cosa que me gusto mucho es que Ubuntu como las distribuciones derivadas de Debian (segun lo que tengo entendido) tienen unos programas que se llaman gestor de paquetes... en ubuntu por defecto viene synaptic (sistema -> administracion -> Gestor de paquetes synaptic) Desde ahi podes bajar casi cualquier programa e instalarlo simplemente con un doble click
se maneja muy distinto que desde window$ pero es en (varios aspectos) mejor

suerte y que te vaya bien

---

### Post by ADICTOALMAXIMO on 2009-04-06
A mi elos de sonido me los reconocio de una y los de nvdia lo baje usando linux

---

