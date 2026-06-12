---
title: "No puedo bootear desde USB"
date: 2009-05-01
forum: Software
---

### Post by RENGOdeDIA on 2009-05-01
Buenas gente, siempre los leo y nunca posteo, pero me aparecio este problemita y no se que hacer:
en la PC de mi casa, que es un poco vieja no puedo arrancar desde el pen, pero si puedo con el liveCD, y en la del laburo y con el mismo pen puedo bootear lo mas bien y tengo ubuntu al pelo.
me aparece esto:

```
Searching for Boot Record from USB RMD-FDD.. OK
SYSLINUX 3.63 Debian 2008-07-15 C BIOS Copyright (c) 1994-2008 H. Peter Anvin
boot:_
Could not find kernel image: linux
boot:_
```

Algunos datos:
PC de mi casa: AMD Sempron 2400, MB ASRock K7S41, 700 Mb ram
PC del laburo: Pentiun 4, 512 Mb ram, es una HP.
YO: usuario intermedio con muchas ganas de pasarse a Linux

Cualquier comentario es bienvenido.
Gracias y saludos

---

### Post by guillermolisi on 2009-05-01
> **RENGOdeDIA said:**
> Buenas gente, siempre los leo y nunca posteo, pero me aparecio este problemita y no se que hacer:
en la PC de mi casa, que es un poco vieja no puedo arrancar desde el pen, pero si puedo con el liveCD, y en la del laburo y con el mismo pen puedo bootear lo mas bien y tengo ubuntu al pelo.
me aparece esto:

```
Searching for Boot Record from USB RMD-FDD.. OK
SYSLINUX 3.63 Debian 2008-07-15 C BIOS Copyright (c) 1994-2008 H. Peter Anvin
boot:_
Could not find kernel image: linux
boot:_
```Algunos datos:
PC de mi casa: AMD Sempron 2400, MB ASRock K7S41, 700 Mb ram
PC del laburo: Pentiun 4, 512 Mb ram, es una HP.
YO: usuario intermedio con muchas ganas de pasarse a Linux

Cualquier comentario es bienvenido.
Gracias y saludos

En que boca USB pones el pendrive ? en las frontales o en las posteriores ?
El USB de esa PC es 1.0 o 2.0 ?
Tenes algun otro dispositivo USB conectado cuando haces la prueba de iniciar desde el pendrive ?

---

### Post by RENGOdeDIA on 2009-05-01
Gracias por responder tan rápido,
la pc tiene solo 4 puertos USB en la parte de atrás, son 2.0 y tengo conectado el cable del celular (sin el celular), el cable de la cámara de fotos (sin la cámara) y la webcam.
voy a probar de dejar libres los demás puertos a ver que pasa.
Saludos

---

### Post by clasificado on 2009-05-02
Proba una vez con todas las bocas: En las computadoras viejas habian varios controladores por eso de la compatibilidad. Por ahi algunos funcionen y otros no

clasificado

---

### Post by infernus92 on 2009-05-02
tenes activado el booteo por USB desde el setup de la BIOS?

---

### Post by RENGOdeDIA on 2009-05-02
Bueno actualizo, probé en mi casa sacando todos los dispositivos USB y booteando solo con el pen pero hizo exactamente lo mismo. El Booteo esta habilitado, yo habilito el boot menu en el arranque.
Lo raro es que ahora estoy en el trabajo y probe en esta PC y bootea lo mas bien del pendrive, elijo idioma español, aparece la barra de progreso de ubuntu como que estuviera cargando y de repente me sale esto:

```
Loading, please wait...

BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _
```

y tengo que resetear por que no me deja hacer mas nada.
El usb lo hice desde el LiveCD de JJ, el pen se monta lo mas bien y puedo ver los archivos y carpetas, pero no puedo bootear.
Voy a seguir probando...
Alguna sugerencia?
Gracias

---

### Post by guillermolisi on 2009-05-02
> **RENGOdeDIA said:**
> Bueno actualizo, probé en mi casa sacando todos los dispositivos USB y booteando solo con el pen pero hizo exactamente lo mismo. El Booteo esta habilitado, yo habilito el boot menu en el arranque.
Lo raro es que ahora estoy en el trabajo y probe en esta PC y bootea lo mas bien del pendrive, elijo idioma español, aparece la barra de progreso de ubuntu como que estuviera cargando y de repente me sale esto:

```
Loading, please wait...

BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _
```y tengo que resetear por que no me deja hacer mas nada.
El usb lo hice desde el LiveCD de JJ, el pen se monta lo mas bien y puedo ver los archivos y carpetas, pero no puedo bootear.
Voy a seguir probando...
Alguna sugerencia?
Gracias
De que capacidad es el pendrive ?

---

### Post by RENGOdeDIA on 2009-05-02
Es un Kingston de 8 GB, en la pc del laburo ya andubo bien, arranque con el LiveCD, hice de nuevo el USB booteable pero le asigne menos espacio para guardar los archivos, lo deje como viene por default y andubo bien, pero recien probe en la de mi casa donde estoy ahora y nada, me sigue apareciendo lo del primer post, probe en todos los puertos usb y sin ningun dispositivo conectado pero no quiere andar.
Voy a seguir buscando.
Saludos!

---

### Post by pablo.s on 2009-05-02
Hola: Me intriga conocer el
método que estas utilizando
para hacer el pendrive booteable.
Me contás?

---

### Post by RENGOdeDIA on 2009-05-02
> **pablo.s said:**
> Hola: Me intriga conocer el
método que estas utilizando
para hacer el pendrive booteable.
Me contás?
Arranque la PC con el LiveCD de UBUNTU 9.04, creo que en el menu sistema hay una opcion que dice hacer dispositivo de arranque usb o algo asi y segui las intrucciones, te pide la iso y que dispositivo usb y algunas otras  opciones.
Lo hizo asi y andubo lo mas bien en la pc del laburo, guardo las configuraciones, etc.   El Live CD anda perfecto en las 2 PC, en la de mi casa no puedo hacer el arranque desde usb, se entiende? sino diganme que me explico mas, pido disculpas pero recien le estoy metiendo mano a esto...
Gracias por tu intriga

---

### Post by pablo.s on 2009-05-02
Veo que estás haciendo el
procedimiento para hacer un
pendrive para instalación, aunque
probablemente vos lo que querés
hacer es una instalación full en
un pendrive... ¿Que tal si probás
hacer una instalación desde el
Live CD al pendrive (utilizando este
como si fuera un disco rigido,
haciendo las particiones de rigor)
y después, asegurandote que 
Grub se haya instalado en la MBR
del pendrive, probás como se
porta?

El paso de instalación de Grub
al pendrive (no a hd0) es, creo
yo, lo más dificil de hacer, pero
si te fijás, casi al terminar la instalación
te pregunta donde querés que
se instale.

---

### Post by RENGOdeDIA on 2009-05-02
> **pablo.s said:**
> Veo que estás haciendo el
procedimiento para hacer un
pendrive para instalación, aunque
probablemente vos lo que querés
hacer es una instalación full en
un pendrive... ¿Que tal si probás
hacer una instalación desde el
Live CD al pendrive (utilizando este
como si fuera un disco rigido,
haciendo las particiones de rigor)
y después, asegurandote que 
Grub se haya instalado en la MBR
del pendrive, probás como se
porta?

El paso de instalación de Grub
al pendrive (no a hd0) es, creo
yo, lo más dificil de hacer, pero
si te fijás, casi al terminar la instalación
te pregunta donde querés que
se instale.
Interesante lo que me decis, algunas dudas que me surgen apenas leo tu respuesta:
* voy a poder seguir usando el resto del pen o lo que me sobre para almacenar datos y que lo pueda usar en win? (yo calculo que si)
* cuantas particiones me recomiendan que haga y cuanto espacio le asigno a cada una?
* formateo alguna como ext3 o ext4 ?
tengo algunas dudas con lo del grub porque todavia nunca instale pero con probar no pierdo nada, si alguno me tira el ABC de esta instalación, o lo que nunca tengo que hacer sera bienvenida la sugerencia.
Lo que me sige intrigando es porque en una pc anda al pelo y en la otra no, yo pienso que el problema viene por el lado del hard, pero bueno veremos como sale todo, cuando tengas novedades posteo.
Gracias de nuevo

---

### Post by pablo.s on 2009-05-02
> **RENGOdeDIA said:**
> * voy a poder seguir usando el resto del pen o lo que me sobre para almacenar datos y que lo pueda usar en win? (yo calculo que si)

Yo particionaría de esta forma:
---Primera partición-------------
3 GB para Windows en Fat32

---Segunda partición-------------
1 GB para Swap

---Tercera partición--------------
2,5 GB para / en ReiserFS (o Ext3)

---Cuarta partición---------------
1,5 GB para /home en Reiser (o Ext3)

> **RENGOdeDIA said:**
> * cuantas particiones me recomiendan que haga y cuanto espacio le asigno a cada una?

Explicado arriba.

> **RENGOdeDIA said:**
> * formateo alguna como ext3 o ext4 ?

Explicado arriba también.

Acordate del paso de guardar Grub
en la MBR del pendrive, que es un
paso crucial.

---

### Post by staar on 2009-05-02
si es un pendrive, NO es recomendable usar un filesystem con journaling como ext3, ext4 o reiserfs, ya que el número de escrituras en el disco aumenta mucho y eso disminuye la vida útil de la memoria, mejor usa ext2, problemas de velocidad no vas a tener ya que los tiempos de acceso son casi nulos comparados con los de un disco común...

es muy importante eso de escribir el grub en el pendrive, acordate, en el instalador de ubuntu, en el último paso, con el botón Avanzado...

que no te bootee en tu casa puede ser muy bien un problema de hard, algunas mothers no soportan booteo desde USB (la mía entre ellas ¬¬)...

saludos

---

### Post by pablo.s on 2009-05-02
Ciertisimo lo que comentás,
staar, pero mi recomendación
la fundamento por dos lados:

1) Las posibilidades de perder
datos al retirar un pendrive a
las apuradas (caso comparable
con un apagón electrico) son
bastantes. En casos como ese
un FS con journaling me parece
mas conveniente por la cuestión
de recuperación de datos.

2) El tema de las escrituras de
datos es mas o menos de unas
100.000 en la vida util de un
pendrive. Si tomamos en cuenta
que cuestan menos de cien pesos
en casi cualquier lado, privilegio
los datos antes que el pendrive.

Como siempre un gusto leer tus
aportes. Saludos.

---

### Post by staar on 2009-05-02
tenés razón pablo, para preservar datos, si sería conveniente un sistema con journaling, y en ese caso sería recomendable usar ext4 antes que ext3, ya que escribe menos en el disco, sería como el 'punto medio'...
sinceramente, nunca use reiser, asi que no se como vendrá la mano en comparación con ext, en términos de Nº de escrituras...

saludos

PD: hay que tener en cuenta que es un pendrive de 8 gb, salen algo más de 100 p, asi que un poco hay que preservarlo también :-D , no hay porque fundirlo antes de tiempo :-D ...

---

### Post by EnriqueK on 2009-05-02
No es el tema, pero vale la pena la alternativa de crear un Live DVD de toda tu instalación con Remastersys y usas el pendrive para almacenar solamente la carpeta de usuario mediante un enlace simbólico en la /home  del Live DVD que apunte a la carpeta de usuario en el pendrive, el resultado es que te podés llevar todo tu sistema a cualquier PC en donde te permitan bootear y además los datos serán persistentes por que quedarán almacenados en el pendrive y de paso este tendrá mucha menos reescrituras.

---

### Post by RENGOdeDIA on 2009-05-04
Buenas, les cuento que instale Ubuntu JJ en el pen, tenia dudas con grub pero salió todo bien, lo probé en la compu del trabajo y booteó lo mas bien, arrancó el grub y pude elegir el SO, pero....
ahora lo probé en la de mi casa (donde tenía problemas antes) y anda peor, directamente se cuelga despues de la autodetección de discos y no responde nada, no tengo teclado asi que no puedo hacer Ctrl+Alt+Supr, la tengo que resetear desde el botón Reset del frente de la CPU. Me llama la atención que queda encendida la luz de la disquetera...
Espero comentarios. Gracias por leer.
Slds

---

### Post by pablo.s on 2009-05-04
> **RENGOdeDIA said:**
> no tengo teclado asi que no puedo hacer Ctrl+Alt+Supr, la tengo que resetear desde el botón Reset del frente de la CPU. Me llama la atención que queda encendida la luz de la disquetera...

¿Cómo no tenés teclado?

Te va a costar un poco usar
la maquina.

---

### Post by guillermolisi on 2009-05-04
> **RENGOdeDIA said:**
> Buenas, les cuento que instale Ubuntu JJ en el pen, tenia dudas con grub pero salió todo bien, lo probé en la compu del trabajo y booteó lo mas bien, arrancó el grub y pude elegir el SO, pero....
ahora lo probé en la de mi casa (donde tenía problemas antes) y anda peor, directamente se cuelga despues de la autodetección de discos y no responde nada, no tengo teclado asi que no puedo hacer Ctrl+Alt+Supr, la tengo que resetear desde el botón Reset del frente de la CPU. Me llama la atención que queda encendida la luz de la disquetera...
Espero comentarios. Gracias por leer.
Slds

Para mi que los USB de esa maquina tienen algun problema o el BIOS tiene algun bug que produce ese efecto.

No es Ubuntu ni el pendrive ni el procedimiento utilizado para generarlo, asi que hay algo en el hardware/BIOS de esa PC que desde USB se tara.

Posibilidades/ganas de actualizar la BIOS y luego ver que resulta ?
La fuente estara en buenas condiciones ?

---

### Post by RENGOdeDIA on 2009-05-04
> **pablo.s said:**
> ¿Cómo no tenés teclado?

Te va a costar un poco usar
la maquina.

Me refería a que no llega a reconocer el teclado en el arranque, se cualga antes...:confused::confused:

---

### Post by RENGOdeDIA on 2009-05-04
> **guillermolisi said:**
> 

Posibilidades/ganas de actualizar la BIOS y luego ver que resulta ?
La fuente estara en buenas condiciones ?

Si se puede resolver voy a probar, asi se aprende no? 

Con respecto a la fuente no creo que este mal, por lo menos los puertos USB nunca me dieron problemas. Que es lo que puede tener la fuente ?

Saludos

---

### Post by guillermolisi on 2009-05-04
> **RENGOdeDIA said:**
> Si se puede resolver voy a probar, asi se aprende no? 

Con respecto a la fuente no creo que este mal, por lo menos los puertos USB nunca me dieron problemas. Que es lo que puede tener la fuente ?

Saludos
Que esta medio pinchada. Algun electrolitico seco producto del paso del tiempo, malas condiciones de trabajo, ventilacion insuficiente y mucho calor que terminan en sacar de punto de trabajo en regimen al circuito y comienza a trabajar forzada hasta que algun componente se va degradando. Los electroliticos son la parte mas sensible y que mas errores aleatorios dan porque lo que es estado solido o funciona o se quemo.

A partir de esto, la fuente empieza a entregar tensiones fuera de valor, corrientes tambien fuera de rango, levanta mas temperatura, etc. y cuando le enchufas algo que consume y exige a la fuente ese resto que ya no tiene, no funca. El consumo maximo de un puerto USB es de 500mA (o por lo menos hasta no hace mucho estaba en ese limite). Mas alla de eso podes quemar algo (igual, un pendrive deberia estar por debajo de ese valor).

La fuente es una de las partes de la PC que mas bola hay que darle al momento de armar/comprar un equipo.

Tambien es de buena practica limpiarla con aire comprimido cada tanto porque la tierra tapa los disipadores de los transistores de potencia.

---

### Post by RENGOdeDIA on 2009-05-05
Sugerencias con respecto a la BIOS?
No se si esto va aca o tendria que abrir un tema nuevo en la sección hardware.
Disculpas si meto la pata
Gracias de antemano
Saludos

---

### Post by zampes on 2009-05-05
Hola RengodeDía (y cojo de noche XD)
En mi experiencia, lo de que se quede en initframs es un problema con el ACPI. Cuando llega la pantalla de opciones  de booteo de Ubuntu -donde te da la opción de ejecutar sin cambios a la pc y todo eso- fijate en las opciones de booteo que aparecen en la parte inferior de la pantalla. Elegí la que dice pci=noacpi o algo parecido, para que tu bios y ciertas partes de tu hardware no entren en conflicto, que es lo que suele colgar el booteo en initframs... en mi nueva hp fue lo mismo...

Ojalá esto te ayude!
Posteá de vuelta para avisarnos que tal te fue!
Suerte

---

### Post by guillermolisi on 2009-05-06
> **RENGOdeDIA said:**
> Sugerencias con respecto a la BIOS?
No se si esto va aca o tendria que abrir un tema nuevo en la sección hardware.
Disculpas si meto la pata
Gracias de antemano
Saludos

Buscaria en la pagina del fabricante de la motherboard para ver si disponibilizo alguna version mas nueva del BIOS que estas usando.

Tendrias que tener a mano la version del BIOS en uso para compararla con la que sea mas nueva para la marca y modelo de motherboard, leer las instrucciones del fabricante para proceder a la actualizacion (algunas permiten actualizar via Internet y otras necesitan de un diskette y un programa que actualice (flashing) el EEPROM (integrado donde se graba el BIOS).

Generalmente el fabricante hace un pequeño comentario sobre que novedades o arreglos se logran con la nueva version, asi que por ahi tenes suerte y solucionan un bug con los ports USB, si es que tiene un bug.

Revisar la fuente o probar con otra de mayor potencia tambien podria ser una solucion y la de iniciar con la opcion NO ACPI es otra alternativa (plan A, plan B, plan C).

---

### Post by RENGOdeDIA on 2009-05-10
> **guillermolisi said:**
> Buscaria en la pagina del fabricante de la motherboard para ver si disponibilizo alguna version mas nueva del BIOS que estas usando.

Tendrias que tener a mano la version del BIOS en uso para compararla con la que sea mas nueva para la marca y modelo de motherboard, leer las instrucciones del fabricante para proceder a la actualizacion (algunas permiten actualizar via Internet y otras necesitan de un diskette y un programa que actualice (flashing) el EEPROM (integrado donde se graba el BIOS).

Generalmente el fabricante hace un pequeño comentario sobre que novedades o arreglos se logran con la nueva version, asi que por ahi tenes suerte y solucionan un bug con los ports USB, si es que tiene un bug.

Revisar la fuente o probar con otra de mayor potencia tambien podria ser una solucion y la de iniciar con la opcion NO ACPI es otra alternativa (plan A, plan B, plan C).

Bueno, buscando encontre que hay una versión mas nueva de la BIOS para mi MB, yo tengo la 1.9 y la nueva es 2.1, la cual ya me baje, pero todavia no quiero actualizarla porque antes quiero hacer backup de mis datos, o no es necesario que haga respaldo? pregunto por que me dijeron que hay posibilidades de que no funcione.
Otra duda, en el caso que no ande, se puede volver a la versión anterior haciendo un Clear CMOS o son dos cosas distintas y tendría que instalar la versión anterior?
Gracias de antemano
Saludos!

---

### Post by guillermolisi on 2009-05-11
> **RENGOdeDIA said:**
> Bueno, buscando encontre que hay una versión mas nueva de la BIOS para mi MB, yo tengo la 1.9 y la nueva es 2.1, la cual ya me baje, pero todavia no quiero actualizarla porque antes quiero hacer backup de mis datos, o no es necesario que haga respaldo? pregunto por que me dijeron que hay posibilidades de que no funcione.
Otra duda, en el caso que no ande, se puede volver a la versión anterior haciendo un Clear CMOS o son dos cosas distintas y tendría que instalar la versión anterior?
Gracias de antemano
Saludos!
Si el flashing de una BIOS falla y la motherboard no contempla un backup del BIOS anterior te quedaste sin maquina, asi nomas.
El Clear CMOS no hace rollback, solo restituye la configuracion a los valores por defecto.

Si el flashing lo haces desde la diskettera, primero usala bien y mucho para evitar errores de lectura por acumulacion de polvo en el cabezal. Luego, identifica muy bien que diskettes estan en buenas condicines y nunca dan errores en su formateo ya que un diskette fallado es garantia que el flashing sale mal.

Y si la placa tiene posibilidad de actualizar via Internet y tenes una buena conexion, dale por ese lado (me parece mas seguro que el diskette).

De todas las motherboards a las que le actualice el BIOS solamente me fallo una y tuve la suerte que como era vieja el chip tenia zocalo, busque un chip igual y lo volvi a actualizar. Esta de la falla fue porque me fallo el diskette.

El backup del disco no me parece tan necesario (en realidad deberias hacer backup periodicamente) porque el disco no se toca cuando actualizas el BIOS.

---

### Post by RENGOdeDIA on 2009-05-21
> Si el flashing de una BIOS falla y la motherboard no contempla un backup del BIOS anterior te quedaste sin maquina, asi nomas.
:shock: Bueno la verdad que me preocupa que me pueda quedar sin nada y como no es de suma necesidad que pueda bootear desde el pen en esta PC por ahora lo voy a dejar acá, ya que conseguí otro disco y voy a instalar ubuntu JJ. 
Abro otro post para algunas consultas por que ya no tiene que ver con este tema.
Gracias a todos, realmente esta comunidad es genial. 
Saludos!!!!

---

