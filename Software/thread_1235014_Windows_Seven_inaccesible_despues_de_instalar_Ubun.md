---
title: "Windows Seven inaccesible despues de instalar Ubuntu."
date: 2009-08-08
forum: Software
---

### Post by Tio Bill on 2009-08-08
[LEFT]Tengo dos discos, uno un Sata II de 500Gb con una particion de 50Gb donde tengo instalado Windows Seven, y un disco Ide de 160 con una partición de 15Gb para Ubuntu 9.04.[/LEFT]                               [LEFT]Anteriormente había instalado la versión 8.04, luego grabe la Iso del cd Live de la 9.04 y al formatear para instalar limpiamente cometí un error muy estúpido por mi falta de conociemientos, en un paso de la instalación en una opción avanzada tildé cargar el arranque en Windows Vista, creyendo así iniciar con W7 y poder elegir si quería entrar en Ubuntu. Pero me llevé una desagradable sorpresa, por que directamente cargó Ubuntu, sin opciones de arranque, y cuando quise acceder a la partición asignada a W7 desapareció por completo, estaba inaccesible. Intenté una recuperación con fixboot, fixmbr, chkdsk /r, y todos los comandos de reparación de inicio de Windows pero todos me daban error, o decian que no había sistema operativo. Me resigné a formatear, pero tampoco podía acceder a ese disco. Entonces lo que hice con el cd de inicio formatee y borre las particiones del disco asignado a Ubuntu y recién ahí pude formatear el otro disco asignado a W7.                                            [/LEFT]                                                                        Poco mas de dos horas ya tenía formateado e instaladas las aplicaciones y programas y configurado el sistema tal y cual lo tengo cotidianamente. Vale decir que me quedé haciendo esto hasta las 4 de la madrugada. Primero la bronca, luego mas relajado dije voy a darle otra oportunidad a Ubuntu (y a mi estupidez) y volvi a formatear e instalar el disco asignado a Ubuntu, y cuidándome de no tocar nada y revisar donde se iba a instalar el cargador de arranque, el cual se iba a instalar en hd0 el cual es ese mismo disco de 160. Confiado instalo y arranco el sistema, pero cuando reinicio, otra vez lo mismo el disco asignado a W7 desaparece y esta inaccesible. A esta altura ya van cuatro dias que no puedo usar Ubuntu ni disfrutarlo. Recién termino de configurar todo mi W7 otra vez, pero ya me da miedo instalar Ubuntu, pero no por resentimiento o bronca si no por mi ignorancia. No se si me borra el MBR o que pero me deja inservible esa partición.Gracias y saludos.

---

### Post by Fak89 on 2009-08-08
Bueno, el tema de que no te deje elejir el SO al iniciar la pc se puede arreglar con el CD de [Super Grub Disk]("http://www.supergrubdisk.org/index.php?pid=5") .. pero si decis que no podes acceder desde el Ubuntu a la particion de Win, lo unico que se me ocurre es que la puedas haber formateado en algun momento..
 
Menos mal que no se mucho :P

---

### Post by staar on 2009-08-08
a ver si entendí bien, ubuntu está en un disco ide y ventanas en un sata, no? cual es el primero en el que busca la BIOS para arrancar? el ide o el sata? el GRUB (cargador de arranque de linux) se instala en la MBR del disco ide o en la del sata?

lo que tenés que hacer es instalar el GRUB en la MBR del disco que inicie primero, y modificar el menu.lst (el archivo de configuración de este) en ubuntu para agregarle la entrada para ventanas (que parece que no te lo reconoce automáticamente el instalador), cualquier cosa te ayudamos a agregarla, es fácil...

SuperGrubDisk es una buena opción, pero no hace milagros, y sobre todo si no se sabe como usarlo (tiene un lenguaje medio complicado)

saludos

---

### Post by guillermolisi on 2009-08-08
No se si lo dije antes, pero primero hay que revisar el junper de configuracion del disco IDE para que sea reconocido como Primario de su canal, dejando otras unidades IDE como secundarias para el mismo canal.

Si el disco esta como secundario es altamente posible que no sea visto como un disco disponible al momento del boot.

---

### Post by Tio Bill on 2009-08-08
**staar**, si es asi, en el Sata esta w7 y en el Ide Ubuntu. Lo que hice mal fue elegir donde inicia el cargador, la primera vez puse en Windows Vista (Así aparecía la opción) y ahí fué cuando quedo inaccesible. Pero la segunda vez no modifique nada y el cargador se instalo en hd0, que vendría a ser el Ide. E igual me dejo inaccesible por segunda vez a Windows. Probé con el cd de inicio de W7 a repararlo pero no hubo caso, decía que no había sistema. Algo hice mal de seguro pero ya me da cosa volver a fallar y que quede inaccesible otra vez ese disco. ¿Si lo desconecto durante la instalación de Ubuntu y después con el Startup manager modifico el inicio? ¿Se entiende lo que quiero decir o soy medio confuso al explicar el problema? Gracias **staar** y **Fak89**

---

### Post by Tio Bill on 2009-08-08
> **guillermolisi said:**
> No se si lo dije antes, pero primero hay que revisar el junper de configuracion del disco IDE para que sea reconocido como Primario de su canal, dejando otras unidades IDE como secundarias para el mismo canal.

Si el disco esta como secundario es altamente posible que no sea visto como un disco disponible al momento del boot. Guillermo, el disco Ide es master pues ya lo había configurado gracias a tu consejo. Y es la única unidad Ide. Gracias.

---

### Post by Tio Bill on 2009-08-08
> **Fak89 said:**
> Bueno, el tema de que no te deje elejir el SO al iniciar la pc se puede arreglar con el CD de [Super Grub Disk]("http://www.supergrubdisk.org/index.php?pid=5") .. pero si decis que no podes acceder desde el Ubuntu a la particion de Win, lo unico que se me ocurre es que la puedas haber formateado en algun momento..
 
Menos mal que no se mucho :P
No solo desde Ubuntu no puedo acceder a esa partición, ni siquiera desde el cd de instalación de W7. Solo pude acceder una vez formateado el disco Ide con Ubuntu y pude acceder solo a formatear pues no se reconocían datos en el disco.

---

### Post by Fak89 on 2009-08-08
> **Tio Bill said:**
> ¿Si lo desconecto durante la instalación de Ubuntu y después con el Startup manager modifico el inicio?
 
Y si, podrias intentar desconectandolo y luego agregar la entrada del Win en el grub.. Me parece raro ya que yo tengo win7 y siempre me lo reconocio normalmente :S

---

### Post by guillermolisi on 2009-08-08
No tengo idea de como es el grub del System7, pero a efectos de sacarte el miedo y esa sensacion de frustracion, me parece una idea sumamente practica desconectar el disco SATA hasta que termines la instalacion de Ubuntu. Ya habra tiempo para entender que esta sucediendo.

---

### Post by Tio Bill on 2009-08-08
Gracias a todos por el apoyo. Voy a desconectar el disco sata hasta terminar la instalación de Ubuntu y despues comento como me fué. Luego mas tranquilo voy a exponer en detalle los pasos que seguí en la instalación fallida, a ver si damos con el error que cometí, para evitar en la medida de lo posible que otro user inexperto pase por lo mismo. Saludos y buen fin de semana a todos.

---

