---
title: "como tener gcc-4.4 y gcc-4.5 simultaneamente?"
date: 2011-03-28
forum: Software
---

### Post by thegreeneyes on 2011-03-28
Hola, quizás alguno de Uds. pueda decirme cómo hacer para tener dos compiladores (o más) instalados simultáneamente en la misma máquina. 

Tengo un programa que compila y corre todo bien en gfortran, gcc 4.4, pero cuando trato de compilar y correr en otra máquina con 4.5 instalados , usando los mismos fuentes y procedimientos, genera el ejecutable sin problemas pero tiene resultados parciales diferentes, y eventualmente aborta en medio de la ejecución.

El programa es Espresso-4.0.3 con EPW-2.3.3

He leído que hay algo llamado rte (run time environment) pero no sé cómo crearlos.

Gracias.

Victor

---

### Post by mama21mama on 2011-03-28
al instalar el compilador nuevo por medio de flags o bien manualmente lo pones en una carpeta.

luego via .bashrc

```
PATH=/directorio/compilador/viejo:$PATH
export PATH
```

[Fuente]("http://foro.noticias3d.com/vbulletin/showpost.php?p=113603&postcount=7")

---

### Post by EnriqueK on 2011-03-28
Se pueden tener a ambos instalados, el tema es definir cual de los dos es el que está activo, en mi caso lo encaré de la siguiente manera.
Si entrás a /usr/bin verás que gcc es en realidad un enlace simbólico que apunta a gcc-4.4 o a gcc-4.5, según a donde apunte, será el gcc activo, por lo que si lo querés cambiar tenés que borrar el enlace gcc y volverlo a crear para apunte al otro , por ejenplo si querés que apunte a gcc-4.5, ponés
sudo -i
cd /usr/bin/
rm gcc
ln -s gcc-4.5 gcc
Si a estos cambios los vas a hacer seguido, te conviene crear dos pequeños script

---

### Post by thegreeneyes on 2011-03-29
Muchas gracias por las sugerencias. 

Ahora parece que es más divertido (?) de lo que esperaba instalar una generación previa de compiladores!!!, no sé si tendrán alguna mejor sugerencia. Me fijé que la 

gcc --version 

y

gfortran --version

tienen 4.4.3 en donde el programa funciona, y 4.4.5 donde produce errores. Encontré los repositorios con versiones anteriores en 

[http://ftp.gnu.org/gnu/gcc/gcc-4.4.3/](http://ftp.gnu.org/gnu/gcc/gcc-4.4.3/)

de donde bajé los archivos fuente, y en 

[http://gcc.gnu.org/install/prerequisites.html](http://gcc.gnu.org/install/prerequisites.html)

los paquetes que preciso preinstalar:

GNU Multiple Precision Library (GMP) version 4.3.2 (or later)
MPFR Library version 2.4.2 (or later) 
MPC Library version 0.8.1 (or later)
Parma Polyhedra Library (PPL) version 0.11
CLooG-PPL version 0.15

los 3 primeros puedo bajarlos y copiarlos directamente en el directorio de gcc para que se instalen cuando gcc se instala, El Polyhedra lo instalé directamente con Synaptics, y con el último no sé qué hacer (-configure y make no usarían el gcc que tengo actualmente instalado? sería compatible con una versión anterior lo que allí se genere?)

La cosa es que de puro optimista siguiendo las páginas de 

[http://gcc.gnu.org/install/configure.html](http://gcc.gnu.org/install/configure.html)

generé un directorio OBJECT en el mismo que contiene a gcc y corrí desde allí

../gcc/configure --with-pkgversion=gcc443  --prefix=$HOME/Z/SOFT_LINUX/COMPILERS/local --program-suffix=-344

que terminó exitosamente.

Luego ejecuté make que concluyó tristemente con error tipo ...

checking for gmp internal files... configure: error: header files gmp-impl.h and longlong.h not found
make[2]: *** [configure-stage1-mpfr] Error 1
make[2]: Leaving directory `..../Z/SOFT_LINUX/COMPILERS/OBJDIR'
make[1]: *** [stage1-bubble] Error 2
make[1]: Leaving directory `..../Z/SOFT_LINUX/COMPILERS/OBJDIR'
make: *** [all] Error 2

... y mi pregunta optimista viene: hay algún modo más fácil de instalar otra versión de los compiladores?, como indicarle a synaptic que muestre versiones viejas de paquetes?

Quizás mama21mama puedas especificarme mejor eso de :

" ... al instalar el compilador nuevo por medio de flags o bien manualmente lo pones en una carpeta...."

No sé qué es eso de "flags". En mi caso yo debo instalar un compilador más viejo que la versión actualmente ofrecida por UBUNTU.

Gracias y perdón por la longitud del texto.

Victor

---

### Post by alfplayer on 2011-03-29
También podés instalar otro sistema en un chroot.

---

### Post by thegreeneyes on 2011-03-30
genial lo de chroot!!!

segui las instrucciones de 

[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)

e instalé UBUNTU LUCID que contiene las versiones de gcc que preciso. Al instalar gfortran automáticamente instaló la versión consistente con gcc. Para openmpi debí ir a 

[http://www.open-mpi.org/](http://www.open-mpi.org/)

pues apt-get no localizaba este paquete en el repositorio (me parece que usa sólo el repositorio de donde sacó LUCID).

Muy bueno lo de chroot. Lástima que no aprendí a tener dos compiladores accesibles en el mismo "ambiente", pero esto de todos modos me sirve.

Gracias. Saludos

---

### Post by alfplayer on 2011-03-30
Open MPI... parece un proyecto interesante.

---

### Post by thegreeneyes on 2011-04-04
Sí!!, antes había intentado instalar MPICH2, pero sin suerte, con openmpi parece que es mucho más fácil instalar y correr programas en paralelo, por ejemplo LAMMPS.

Funciona bárbaro (aunque no sé por qué sigo con problemas con los programas que a mí más me interesan). 

Suerte!!

---

### Post by alfplayer on 2011-04-04
> **thegreeneyes said:**
> Funciona bárbaro (aunque no sé por qué sigo con problemas con los programas que a mí más me interesan).

Suerte con eso.

---

