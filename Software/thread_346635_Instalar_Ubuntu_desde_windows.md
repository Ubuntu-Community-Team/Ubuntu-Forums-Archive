---
title: "Instalar Ubuntu desde windows"
date: 2007-01-26
forum: Software
---

### Post by Mafber on 2007-01-26
Hola a todos :D  !!! quería preguntarles si alguien ya probó esto de instalar Ubuntu desde windows
[https://wiki.ubuntu.com/install.exe/Prototype](https://wiki.ubuntu.com/install.exe/Prototype)
Es como para recomendar a gente que tiene ganas de instalar ubuntu, pero no tiene idea de como instalar un SO?? :confused: 
funciona bien ubuntu con esa forma de instalación??? :confused: 
es confiable ese instalador???? (que diferencia hay entre beta y prototipo? :confused:  )

---

### Post by lavaramano on 2007-01-26
prototipo me suena a que es un modelo que puede romperte todo.
y beta es una version usable semi estable, pero con bugs.

si tenes una maquina que se banque al vmware player instalar al windows desde ahi y probalo desde ahi, si se rompe algo no perdes nada

---

### Post by BlackHero on 2007-01-26
INSTALANDO UBUNTU DESDE WINDOWS


1. TENER INSTALADO WINDOWS COMO OS PRIMARIO EN UNA PARTICION TIPO C PERO DEJANDO ESPACIO EN EL DISCO FISICO ASI ENTRE EL OTRO OS 
2. DESFRAGMENTAR EL DISCO 
3. REINICIAR
4. INGRESAR AL BIOS Y ACTIVAR QUE BOTEE EL CD
5. INSERTAR EL LIVE CD EN LA SIDITERA, REINICIAR
6. CUANDO SE CARGA EL LIVE CD PARA LA INSTALACION NORMAL HACER TODO COMO UNA INSTALACION NORMAL 
7. CUANDO ESTA EN LA SECCION DE QUE VAS A HACER CON EL DISCO LE MANDAS REZIZE  
AL ESPACIO LIBRE
8. LISTO 



EL GRUB TE VA A CARGAR POR DEFECTO UBUNTU/XUBUNTU MEJOR DICHO xD Y TE DA LA OPCION DE CARGAR WINDOWS HACIENDO LA FLECHITA PARA ABAJO

---

### Post by spg76 on 2007-01-26
> **BlackHero said:**
> INSTALANDO UBUNTU DESDE WINDOWS


1. TENER INSTALADO WINDOWS COMO OS PRIMARIO EN UNA PARTICION TIPO C PERO DEJANDO ESPACIO EN EL DISCO FISICO ASI ENTRE EL OTRO OS 
2. DESFRAGMENTAR EL DISCO 
3. REINICIAR
4. INGRESAR AL BIOS Y ACTIVAR QUE BOTEE EL CD
5. INSERTAR EL LIVE CD EN LA SIDITERA, REINICIAR
6. CUANDO SE CARGA EL LIVE CD PARA LA INSTALACION NORMAL HACER TODO COMO UNA INSTALACION NORMAL 
7. CUANDO ESTA EN LA SECCION DE QUE VAS A HACER CON EL DISCO LE MANDAS REZIZE  
AL ESPACIO LIBRE
8. LISTO 



EL GRUB TE VA A CARGAR POR DEFECTO UBUNTU/XUBUNTU MEJOR DICHO xD Y TE DA LA OPCION DE CARGAR WINDOWS HACIENDO LA FLECHITA PARA ABAJO

BlackHero, lo que decis vos es una instalación para hacer dual boot.
Lo que comenta Mafber es sobre un programita para Windows que instala Ubuntu, sin instalar GRUB, agregando la opción de usar Ubuntu desde una partición de Windows sin necesidad de particionar y agregando Ubuntu al Boot Loader de XP.

---

### Post by BlackHero on 2007-01-26
ah jejeje disculpen entonces tipee de mas :)

---

### Post by spg76 on 2007-01-26
> **BlackHero said:**
> ah jejeje disculpen entonces tipee de mas :)

Igual tu explicación queda como ejemplo de lo fácil que es instalar Ubuntu sin borrar Windows.:)

---

### Post by damcito on 2007-02-02
pucha, pense que era una forma de usar ubuntu dentro de windows sin necesidad de maquina virtual, no existe nada para hacer eso no?

(aclaro que es por mi maquina del laburo, me obligan a usar windows por el ******* sistema)

---

### Post by beuno on 2007-02-02
> **damcito said:**
> pucha, pense que era una forma de usar ubuntu dentro de windows sin necesidad de maquina virtual, no existe nada para hacer eso no?

(aclaro que es por mi maquina del laburo, me obligan a usar windows por el ******* sistema)

Lo que vos queres es [vmware]("http://www.vmware.com/")

---

### Post by damcito on 2007-02-05
pero como dije, no quiero instalar virtuales :(

---

### Post by lavaramano on 2007-02-05
> **damcito said:**
> pero como dije, no quiero instalar virtuales :(

entonces si no queres instalar virtuales lo que podes hacer como otra opcion.
es tener una maquina con ubuntu conectada a internet a la cual te puedas loggear remotamente y conectarte asi.

de esa forma tenes ubuntu, sin virtualizar nada y tampoco instalando un sistema operativo en la maquina del trabajo.

---

### Post by BlackHero on 2007-02-05
claro man muchas opciones no hay pero varias si 

1 dual boot
2 virtual machines 
3 remote conection
4 emulators
5 comprate otra para instalar el otro sistema operativo
6 comprate un disco rigido mas e instala ahi el sistema que quieras usar por ejemplo hasta podes comprarte un flash drive e instalarlo ahi o sino un carry con un disco rigido adentro como hize yo pero en xubuntu el carry con un sata2 adentro mediante usb no me funciona muy bien pero funciona :)



osea para eso estan los diferentes sistemas operativos tampoco podes pedir algo imposible 

WINBUNTU

---

### Post by ecodina22 on 2007-08-28
Correcion de interpretacion:
Prototipo Significa modelo de prueba, que no esta oficialmente desarrollado.
Beta es un desarrollo que puede ser probado antes de ser definitivo en el caso del correo yahoo! ( que tiene el correo en beta pero full funcional.). El beta esta en desarrollo constante y. En linux en general hay versiones betas cuyos desarrollos se hacen en forma constante (valga la redundancia).
Es mejor probar una beta (que se desarrola en forma constante) que un prototipo (que no se ha comenzado oficialmente a desarrollar).
Parece un juego de palabras SORRY !  pero es lo mas explicativo que se me ocurre.
[CENTER]:lolflag::lolflag::lolflag:[/CENTER]


> **lavaramano said:**
> prototipo me suena a que es un modelo que puede romperte todo.
y beta es una version usable semi estable, pero con bugs.

si tenes una maquina que se banque al vmware player instalar al windows desde ahi y probalo desde ahi, si se rompe algo no perdes nada

---

### Post by por100pre1 on 2007-08-28
El OP se refiere a [Wubi]("http://en.wikipedia.org/wiki/Wubi_(Ubuntu)") un installador de Ubuntu para usar en la session de Windows. [Esta]("http://wubi-installer.org/") su su pagina. :)

---

### Post by Kittukahier on 2007-09-15
Yo probé Wubi, salvo las limitaciones en los efectos de pantalla anduvo muy bien para probar ubuntu, no probé xubuntu ni kubuntu, tampoco edubuntu que son las opciones que da para instalar. Yo primero bajé la imagen después la puse en la misma carpeta del wubi y listo como en las explicaciones de la página donde se descarga.
El booteo es bastante parecido a si se lo tuviera instalado de verdad, viene con un grub. Después hice una instalación con partición desde una imagen del cd y comparandolos no encuentro la gran diferencia con el wubi, ya que a mí me funcionó todo: sonido, conexión, compartir carpetas y estable todo el tiempo.

---

### Post by maukeli on 2009-01-08
hola gente de ubuntu es mi primer post por que soy nuevo en linux
quisiera empezar a disipar algunas dudas la de hoy
es esta.
yo tengo instalado en mi pc windows xp en una particion y tengo otra particion libre donde quisiera instalar ubuntu, ahora bien, como instalo ubuntu en esa particion vacia y ademas voy apoder iniciar tanto con windows o ubuntu segun lo elija?

por favot quisisera que m etengan paciencia soy nuevo

desde ya muchas gracias

---

### Post by sajnox on 2009-01-08
Bienvenido,

Si podes instalar Ubuntu en la particion vacia, es mas facil de lo que pensas. Para hacerlo te recomiendo que leas esta guia 
[www.guia-ubuntu.org]("http://www.guia-ubuntu.org/index.php?title=Categor%C3%ADa:Instalaci%C3%B3n")
Ahi te aclaran todo lo que precisas saber para instalar, yc cualquier duda que tengas consultas por aca.

Y si, cuando prendas la PC vas a poder elegir que sistema operativo queres usar

Saludos

---

### Post by NETWORKsolutions on 2009-05-13
Bueno lo mas mas facil que te aconsejo es ir a wubi-installer.org y bajarte el programa.
Wubi por si solo te bajara el archivo ISO que contiene linux ubuntu y lo instalara el mismo

---

