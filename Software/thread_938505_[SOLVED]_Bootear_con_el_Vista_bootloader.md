---
title: "[SOLVED] Bootear con el Vista bootloader"
date: 2008-10-04
forum: Software
---

### Post by santiagoward2000 on 2008-10-04
Hola gente!
Ando con una de esas dudas existenciales. Tengo una Dell XPS m1330, que tiene una cosa que se llama Dell Media Direct. Es un programa metido en una partición separada con partes de XP, que se puede abrir con un botón, si la máquina está apagada, sin tener que entrar al Vista.
Lo primero que hice fue meter Xubuntu como había hecho siempre. El tema es que esto hizo que ese botón deje de funcionar, porque mientras cargaba el programa este me saltaba el grub.
Por lo que estuve leyendo, tengo que instalar el grub en la partición de / , y después modificar el BCD del Vista.
¿Está bien eso de instalar el grub en la misma partición del / ? ¿Alguien sabe cómo modificar el BCD? (Por lo que vi hay 2 programas: EasyBCD y VistaBootPro) ¿O me conviene usar WUBI?
Gracias!

---

### Post by pol666 on 2008-10-05
El grub no esta instalado siempre en /boot/grub?

---

### Post by santiagoward2000 on 2008-10-05
> **pol666 said:**
> El grub no esta instalado siempre en /boot/grub?

Por lo que yo entendí buscando sobre esto, el grub se instala por defecto en el mrb, pero si instalo con un AlternateCD puedo elegir dónde instalarla.
Lo que estuve leyendo fue [esta guía]("http://www.nodigasni.com/blog/2008/05/windows-xp-vista-ubuntu-dell-media-direct-en-dell-xps-m1530/"), pero el tipo instala también el XP, y lo usa para bootear modificando el boot.ini, que ya no existe en el Vista.

---

### Post by WanderingKnight on 2008-10-05
> El grub no esta instalado siempre en /boot/grub?

GRUB tiene sus archivos de configuración de /boot/grub, pero en realidad necesita instalarse en el MBR (el sector 0 de cualquier disco, que no pertenece a ninguna partición) porque ahí es donde el BIOS va a buscar un programa para ejecutar. El BIOS de por sí no tiene la más pálida idea de qué sistema está en qué partición, ya que ésa es tarea del bootloader... Pensá que si GRUB se instalara sólo en /boot/grub, cómo sabe el BIOS a qué partición (y peor, a qué directorio!) ir a buscar el bootloader? Más teniendo en cuenta que para leer /boot/grub debería ya realizar un montaje de disco, lo cual requeriría que el kernel estuviese andando, etc...

Si te fijás bien, cada vez que modificás el menu.lst tenés que correr grub-update, lo cual reescribe los datos del MBR y aplica la configuración nueva.

> Por lo que yo entendí buscando sobre esto, el grub se instala por defecto en el mrb, pero si instalo con un AlternateCD puedo elegir dónde instalarla.

GRUB *siempre* se instala en el MBR. Lo que podés hacer en la instalación (tanto en la Alternate como en la común) es elegir una partición aparte para guardar el /boot, que tiene los archivos de configuración, pero eso no significa que GRUB esté alojado en otro lado.

---

### Post by santiagoward2000 on 2008-10-05
> **WanderingKnight said:**
> GRUB *siempre* se instala en el MBR. Lo que podés hacer en la instalación (tanto en la Alternate como en la común) es elegir una partición aparte para guardar el /boot, que tiene los archivos de configuración, pero eso no significa que GRUB esté alojado en otro lado.

Eh.. No entiendo! JEJE
Viendo en esta [otra guía]("http://sabravof.wordpress.com/2007/05/03/dell-inspiron-6400-media-direct-3-con-todos-los-codecs-ubuntu-704-windows-xp/") veo un screen de la instalación con AlternateCD que, después de haberle dicho que no para instalar el GRUB dice:
> Ahora debe configurar el sistema recién instalado para que sea arrancable, instalando para ello el cargador GRUB en un dispositivo del que se pueda arrancar. La forma habitual de hacerlo es instalar GRUB en el registro principal de arranque (master boot record) del primer disco duro. **Si lo prefiere, puede instalar GRUB en cualquier otro punto del disco duro, en otro disco duro, o incluso en un disquete.**
¿Eso no quiere decir que puedo instalar el GRUB en otro lugar? :confused:

---

### Post by Mister X on 2008-10-05
> **santiagoward2000 said:**
> Eh.. No entiendo! JEJE
Viendo en esta [otra guía]("http://sabravof.wordpress.com/2007/05/03/dell-inspiron-6400-media-direct-3-con-todos-los-codecs-ubuntu-704-windows-xp/") veo un screen de la instalación con AlternateCD que, después de haberle dicho que no para instalar el GRUB dice:

¿Eso no quiere decir que puedo instalar el GRUB en otro lugar? :confused:

Se puede instalar en el MBR o en una particion, yo lo tengo instalado en una particion. En el MBR quedó el gestor del XP como vino de fabrica y yo modifique el boot.ini para agregar el grub.
El arrancador del Vista no lo conozco (ni quiero) asi que no te puedo ayudar, pero seguramente se pueda hacer.

---

### Post by Mister X on 2008-10-05
> **WanderingKnight said:**
> 
GRUB *siempre* se instala en el MBR. Lo que podés hacer en la instalación (tanto en la Alternate como en la común) es elegir una partición aparte para guardar el /boot, que tiene los archivos de configuración, pero eso no significa que GRUB esté alojado en otro lado.

Esto no es asi.
Si elegis instalarlo en una particion, el MBR queda intacto. Lo que sí vas a necesitar otro gestor en el MBR para que puedas cargar despues el grub.

---

### Post by guisheca on 2008-10-05
A la ******, ahora si que quedé mas desconcertado que perro en bote...

---

### Post by santiagoward2000 on 2008-10-05
> **Mister X said:**
> Se puede instalar en el MBR o en una particion, yo lo tengo instalado en una particion. En el MBR quedó el gestor del XP como vino de fabrica y yo modifique el boot.ini para agregar el grub.
El arrancador del Vista no lo conozco (ni quiero) asi que no te puedo ayudar, pero seguramente se pueda hacer.

Sigo leyendo sobre el EasyBCD, que es un programa que me deja modificar el arranque del Vista, y que viene con opciones simples para agregar Ubuntu sin problemas.
Creo que voy a probar con eso. Pero antes, ¿dónde me conviene instalar el GRUB?
Gracias!

---

### Post by WanderingKnight on 2008-10-05
> 
Si elegis instalarlo en una particion, el MBR queda intacto. Lo que sí vas a necesitar otro gestor en el MBR para que puedas cargar despues el grub.

Ajá, no contemplé esa posibilidad. De todas formas me parece bastante raro tener que pasar por dos bootloaders para cargar un solo sistema operativo... honestamente no le veo la utilidad.

---

### Post by santiagoward2000 on 2008-10-05
> **WanderingKnight said:**
> Ajá, no contemplé esa posibilidad. De todas formas me parece bastante raro tener que pasar por dos bootloaders para cargar un solo sistema operativo... honestamente no le veo la utilidad.

En este caso es porque el Media Direct no me anda si uso GRUB (no sé si alguna vez lo voy a usar, pero ya que está no quiero romperlo). Estaría usando 2 bootloaders para cargar Ubuntu, pero uno solo para Vista y Media Direct.

---

### Post by santiagoward2000 on 2008-10-05
Bueno gente, parece que anda! :)
Lo que hice fue instalar el GRUB en la misma partición que tengo / (sda6 en mi caso). Cuando reinicié la máquina, entró directo al Vista. Entonces lo que hice fue instalar el [EasyBCD]("http://neosmart.net/dl.php?id=1") y seguir [estas instrucciones]("http://neosmart.net/wiki/display/EBCD/Ubuntu") para agregar Ubuntu al arranque de Vista.
Y anda el Media Direct! :)

---

### Post by marcianus on 2008-10-08
Os cuento "mi aventura" instalando ubuntu64 a ver si me podeis ayudar. He seguido las instrucciones que mas o menos hay en este post y algo falla o se me escapa algun concepto.
Quiero instalarlo en un mismo disco en el que instalare Vista (aunque de momento Vista no esta instalado). 

El gestor de particiones de Ubuntu durante el proceso de instalacion me identifica el disco donde lo voy a instalar comoo sda8. En el equipo hay ademas otros 5 discos que identifica correctamente. Pero lo que me "mosquea" es que 4 de ellos estan configurados en volumenes Raid (4 volumenes, 2 raid0 y dos raid1) pero el gestor de particionado del instalador de Ubuntu se "pasa por el forro" los volumenes e identifica los discos fisicos (cosa que no pasa con otras herramientas de particionado). Ademas, independientemente de como ordene los volumenes/discos en la Bios, siempre los ordena igual (atendiendo al orden "fisico" de los discos segun estan conectados a placa). Esto no es normal, no?. No reconoce Ubuntu los raid del intel ich9r?. 

Pese a las dudas anteriores, he particionado el disco asi: 
Una primera particion ntfs donde instalare Vista 
Una segunda particion ext3 para montar /
Una tercera particion ext3 para montar /home
La cuarta particion para swap.

A la hora de instalar grub eligo opciones avanzadas porque quiero que se instale en una particion (concretamente en la particion reservada a / . Lo hago asi porque empleo otro gestor de particiones llamado GAG que si instalo en el MBR y me permite arrancar Vista y XP en otros discos del equipo. 

El proceso de instalacion ha sido correcto (al menos lo ha parecido) pero no arranca Ubuntu, aparece el menu de grub con 2 opciones: 

Ubuntu bla,bla,bla y Ubuntu (recuperacion9, pero eliga el que eliga me da un error #22 y no arranca. Incluso añadiendolo como opcion de arranque para GAG apuntando a la particion donde he instalado grub, tampoco tira.

Que se me escapa?

PD: No tengo ningun problema si instalo Ubuntu de la manera habitual con GRUB en el MBR. Pero esto me obliga a instalarlo en otro disco y cambiar en bios las opciones de arranque cada vez que quiero cambiar de S.Operativo, lo cual no me apetece.

saludos y perdon por el ladrillo.

---

