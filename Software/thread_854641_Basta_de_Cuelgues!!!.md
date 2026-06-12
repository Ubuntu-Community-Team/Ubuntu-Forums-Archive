---
title: "Basta de Cuelgues!!!"
date: 2008-07-09
forum: Software
---

### Post by _kAz_ on 2008-07-09
Otra vez yo con lo mismo!!!

Loco, como puede ser que Ubuntu se me cuelgue con el Abiword o el OpenOffice Writer? No da!!! Si fuera que estaba reproduciendo alguna página con flash o algo más pesado. BASTA!

Alguien por favor digame que puede estar pasando. En su momento creí que era el Firefox, después el flash, después el sonido, después la placa de video... ya no sé que pensar, lo único que se es que **no da que se cuelgue cuando estoy navegando un .doc!**

O sea no puedo realizar un tarea hiper-básica porque se congela todo (no me deja hacer absolutamente nada, ni reiniciar la sesión). Había desinstalado un paquete powernowd o algo así, pero no sirvió de nada tampoco.

---

### Post by vk-cdg on 2008-07-09
Te lo hace aleatoriamente y en cualquier momento, con el programa que tengas abierto?

Tenés el otro sistema operativo como para probar usarla un rato con el?
Mas de una vez es un tema de hrdware, una memoria floja  o un ventilador medio sucio que hace que el micro caliente por demás.

---

### Post by _kAz_ on 2008-07-09
> **vk-cdg said:**
> Te lo hace aleatoriamente y en cualquier momento, con el programa que tengas abierto?

Tenés el otro sistema operativo como para probar usarla un rato con el?
Mas de una vez es un tema de hrdware, una memoria floja  o un ventilador medio sucio que hace que el micro caliente por demás.

Si lo hace cuando se le canta digamos, e indistintamente con cualquier procesador de texto (mas frecuente en los ultimos tiempos, a veces se me cuelga con otros programas).

Y sucede sólo con Ubuntu Hardy, con el anterior Kubuntu 7.10 nunca pasó así tan recurrentemente.

Como decís puede ser un problema de hard, que se yo, se me ocurre que quizas si bajo los drivers oficiales de mi placa de video ATI capaz se solucione.
Sino no sé, cuando decís "memoria floja" te referís a que capaz que esté medio suelta? Servirá tocar un poco a ver si está todo bien puesto y de paso veo que onda los ventiladores (que por cierto cuando arranca hace un quilombo barbaro)?

---

### Post by Hei Ku on 2008-07-09
A mi me empezo a hacer eso, y descubri que era porque uno de los discos moria de repente. Eso me llevo a descubrir que la fuente estaba mal y me habia quemado el disco y un slot de memoria. En general, si linux se cuelga por completo es una incompatibilidad complicada con el hardware o un problema de hardware directamente.
En el momento de colgarse se te cuelga el teclado tambien? (si apretas caps lock te prende y apaga la luz o nada?)

---

### Post by Mauro22 on 2008-07-09
Proba agregando nohz=off en la linea de booteo del kernel



Eso deshabilita un agregado que pusieron en HH para el manejo del cpu y otra cosas, algo como tickness o algo asi para el ahorro de energia en portatiles, :S que provoca cuelgues en algunos hardware.


Probalo...

:guitar:

---

### Post by niko_3100 on 2008-07-09
Proba desabilitando el tracker y ese indexado ue te alentiza mal la maquina.

---

### Post by santiagoward2000 on 2008-07-10
Hola!
_kAz_, ¿puede ser que tengas algun tipo raro de fuentes instaladas? Yo recien instale las fuentes **Moon Phases**, y cuando las quise poner en el AbiWord para ver como eran y que letra era cada una, se me colgo el Abi.
Yo ya tenia algunas fuentes asi por Conky (las **weather**), pero no me lo colgaban. Hoy encontre por aca tirado el archivo con las fuentes, y quise ver como eran. Probe unas flechas que habia, y todo bien. Pero cuando pase el cursor por las **Moon Phases**, se colgo todo tratando de cargar la vista previa. Cerre el Abi, probe de nuevo y se colgo igual. Ni siquiera llegue a escribir algo como para probar.
No se si tenga algo que ver con tu caso, es solo una idea.
Suerte!

---

### Post by _kAz_ on 2008-07-12
> **santiagoward2000 said:**
> Hola!
_kAz_, ¿puede ser que tengas algun tipo raro de fuentes instaladas? Yo recien instale las fuentes **Moon Phases**, y cuando las quise poner en el AbiWord para ver como eran y que letra era cada una, se me colgo el Abi.
Yo ya tenia algunas fuentes asi por Conky (las **weather**), pero no me lo colgaban. Hoy encontre por aca tirado el archivo con las fuentes, y quise ver como eran. Probe unas flechas que habia, y todo bien. Pero cuando pase el cursor por las **Moon Phases**, se colgo todo tratando de cargar la vista previa. Cerre el Abi, probe de nuevo y se colgo igual. Ni siquiera llegue a escribir algo como para probar.
No se si tenga algo que ver con tu caso, es solo una idea.
Suerte!

Estoy utilizando en el theme una fuente que se llama Kurier, y es .otf (intenté pasarla a ttf pero me resigné porque habia que usar el FontForge y era un lio y no llegaba a ningun lado). Quizás también sea que abro documentos que fueron creados con Word y en el Writer o el Abiword utiliza tipografías diferentes a las originales del documento.
Pero efectivamente ya se hizo común que al abrir alguno de estos procesadores de texto se cuelgue.:(

---

### Post by _kAz_ on 2008-07-12
> **Hei Ku said:**
> A mi me empezo a hacer eso, y descubri que era porque uno de los discos moria de repente. Eso me llevo a descubrir que la fuente estaba mal y me habia quemado el disco y un slot de memoria. En general, si linux se cuelga por completo es una incompatibilidad complicada con el hardware o un problema de hardware directamente.
En el momento de colgarse se te cuelga el teclado tambien? (si apretas caps lock te prende y apaga la luz o nada?)

No hace nada de nada, la unica solucion es resetear, muere pc, teclado y mouse.

---

### Post by _kAz_ on 2008-07-12
> **Mauro22 said:**
> Proba agregando nohz=off en la linea de booteo del kernel
Eso deshabilita un agregado que pusieron en HH para el manejo del cpu y otra cosas, algo como tickness o algo asi para el ahorro de energia en portatiles, :S que provoca cuelgues en algunos hardware.
Mmmmm donde encuentro el archivo? Soy re newbie en esto... Al respecto también pensé en desinstalar los kernels viejos, leí por ahí, pero no se si me servirá para esto.

> **niko_3100 said:**
> Proba desabilitando el tracker y ese indexado ue te alentiza mal la maquina.

Creo que en algun momento lo desinstale/deshabilite, además de esas cosas referidas a lo de ahorro de energía (que creo que también me mencionaron por acá), pero algunos los volvi a poner porque cuando quería apagar la máquina se demoraba añares en aparecer el cuadro de dialogo de salida.

---

### Post by Mauro22 on 2008-07-12
> **_kAz_ said:**
> Mmmmm donde encuentro el archivo? Soy re newbie en esto... Al respecto también pensé en desinstalar los kernels viejos, leí por ahí, pero no se si me servirá para esto.


Cuando prendas la pc y llegas al grub:

1) Si tenes grub grafico apreta ESC
2) sobre la linea de ubuntu apretas la e
3) otra vez la e
4) al final agregas nohz=off
5) apretas b


Fijate si durante esta sesion se te cuelga

---

### Post by Hei Ku on 2008-07-13
> **_kAz_ said:**
> No hace nada de nada, la unica solucion es resetear, muere pc, teclado y mouse.

Lo mas probable es que tengas un problema de hardware o incompatibilidad severa de drivers y el hardware. Es casi lo unico que te puede colgar un Linux de esa manera.
Fijate en /var/log los archivos dmesg y messages a ver si encontras algo raro (errores, warnings, etc.)

---

### Post by niko_3100 on 2008-07-13
Probaste desinstalando el programita powernowd ??? A mi se me colgaba desinstale ese daemon y bendita solucion.

---

### Post by Apipote on 2008-07-14
Es impresionante y frustrante leer en los foros de habla inglesa el tema de los cuelgues. 

Según entiendo luego de FF 7.10...y a muchísimos usuarios.

Cual es concretamente el problema?? porque por lo que leí no solo se culpa a los drivers propietarios.

:(

---

### Post by FlyerDie on 2008-07-14
Que te hace pensar que sea un problema de soft y no de hard?

A mi me paso con una maquina que tenia window$ (along time ago) que me dejaba freezada la pantalla...mouse duro..etc.

Resultado, un banco de memoria defectuoso...no era ningun programa, era una memoria.

Saludos

---

### Post by Apipote on 2008-07-14
> Resultado, un banco de memoria defectuoso...no era ningun programa, era una memoria.

Voy a revisar ese tema. 
En cada livecd, cuando bootea, hay una aplicación para eso no??

---

### Post by Apipote on 2008-08-27
> Proba agregando nohz=off en la linea de booteo del kernel



Eso deshabilita un agregado que pusieron en HH para el manejo del cpu y otra cosas, algo como tickness o algo asi para el ahorro de energia en portatiles, :S que provoca cuelgues en algunos hardware.


Probalo...

En efecto, se acabaron mi cuelgues, este es un bug del Kernel que espero lo solucionen pronto. 

Slds

---

### Post by ArgentinoGuy on 2008-08-29
Hola,

a mi me pasa algo similar, tengo una notebook hp dv6720la y lo que me sucede por ahi es que abro un terminal y se pone gris en la espera de ejecutarse, y ahi queda... cuando sucede eso se decir, epa se puso loca bueno reinicio y aprieto el boton de apagado y nada... la unica solucion es irme a consola y halt.
a todo esto se me cuelgan esas cosas pero estoy navegando de lo mas bien, escuchando musica y con el pidgin abierto, y esas cosas funcionan barbaro.

A alguno le pasa algo parecido? o le paso? o tienen el amigo de un primo lejano que le haya pasado? :P

desde ya muchas gracias y saludos!

---

### Post by niko_3100 on 2008-08-29
proba desinstalando el paquete powernowd y tambien desde "sesiones" que no abra al inicio el tracker, que te indexa todo el libro me parece para hacer busquedas mas facil, el tema e que te hace laburar mucho el disco. Yo lo tengo deshabilitado todo lo que tenga nombre tracker.

---

### Post by eldragon on 2008-08-29
yo no deshabilitaria el tracker, al principio era muy molesto, no andaba bien, pero ahora es una maravilla, lo uso frecuentemente para buscar documentos.

cuando se cuelga la maquina....en vez de hacer un hard reset, es recomendable usar las sysrq funciones del kernel. y probar si estas responden. en cuyo caso, el kernel sigue andando (al menos en funcionalidad minima). y podes evitar perdidas de informacion por no desmontar correctamente los discos.

cita de wikipedia en ingles
> 
To perform a safe reboot of a Linux computer which has otherwise locked up, the QWERTY (or AZERTY) mnemonic "Raising Skinny Elephants Is Utterly Boring" or "Raising Elephants Is So Utterly Boring", the more sensible "Reboot Even If System Utterly Broken" or simply remembering the word "BUSIER" backwards, is often useful. It stands for

     unRaw (take control of keyboard back from X),
      tErminate (send SIGTERM to all processes, allowing them to terminate gracefully),
      kIll (send SIGKILL to all processes, forcing them to terminate immediately),
       Sync (flush data to disk),
       Unmount (remount all filesystems read-only),
    reBoot. These keystrokes should be entered a few seconds apart. 


en pocas palabras.

ALT-SYSRQ - R
ALT-SYSRQ - E
ALT- SYSRQ - I
ALT- SYSRQ - S
ALT - SYSRQ - U
ALT - SYSRQ - B

eso hace: 
R: le saca el control del teclado a X
E: termina todos los procesos
I: Mata todos los procesos
S: vacia buffers al disco
U: desmonta / monta como RO los sistemas de archivos.
B: reinicia.


muy util cuando la maquina no quiere darnos bola.

---

### Post by chamus on 2008-09-05
Que tal gente? A ver si alguien me puede ayudar, porque hace rato que vengo con problemas de cuelge, la maquina muere por completo! Mouse, luces del teclado, todo. Tengo una compaq f500, Sempron 3400+, 2.5 gb de ram, como todas las otras.
Primero como todos tenia instalado Vista y ubuntu comenzaro a colgarse, solo con ubuntu, nunca con vista.
Desinstale vista y ahora tengo solo Hardy. 
vamos a lo que ya he provado:
  No tengo software restringidos, he puesto nvidia correctamente, me funciona fusion y todo. Sin solucion.
  He mirado los logs del sys en Var/log/syslog y no aparece ningun error o warning.
 Pense en la temperatura; uso el sensord con alarma para bajar la temperatura y se cuelga aun estando fria(55° o 60°) se cuelga a veces sin hacer nada! en el escritorio mientras no la uso!!
 Desinstale el powernowd, nada.
 He tratado de poner nohz=off en el grub, pero los cambias alli no persisten al reiniciar se borran!

  Que mas puedo hacer para solucionar esto??

  Saludos y por favor sugieran.

---

### Post by niko_3100 on 2008-09-05
Para mi tiene algo que ver la memoria esa ram, las compaq presario f500 soportan hasta 2 gb de ram, te reconoce la bios los 2,5?? y ubuntu tambien? y vista tambien?

---

### Post by faktorqm on 2008-09-08
chamus: mira este post para poner nohz... [http://ubuntuforums.org/showpost.php?p=5734634&postcount=3](http://ubuntuforums.org/showpost.php?p=5734634&postcount=3)

---

### Post by chamus on 2008-09-09
Bueno, despues del  fin de semana he tratado de usar mi notebook pero nada! Se cuelga cada diez, quince minutos!! Imposible.
La memoria de 2,5 Gb es reconocida por el bios, vista y ubuntu sin problemas! Aun asi hoy trate sacando una usando solo lo soportado por manual pero no!
En cuanto a editar el menu del grub, se me hace imposible, antes ya habia podido modificarlo, pero ahora no. He tratado desde el inicio al bootear  y tambien editando el archivo, pero los cambios no aparecen!
Para postear esto tube que reiniciar como 8 veces!! Ayer no pude ni usar la pc! 
Que mas queda por hacer?

---

### Post by ramiro_md on 2008-09-09
A mi tambien se me suele colgar por unos segundos el sistema, tengo 754 excatamente mb de ram. Con gusty nunca me paso, ahora con hardy si, debe ser hardy..sera cuestión de espeerar ¿intrepid ibex?.

---

### Post by WanderingKnight on 2008-09-09
> 
En cuanto a editar el menu del grub, se me hace imposible, antes ya habia podido modificarlo, pero ahora no. He tratado desde el inicio al bootear y tambien editando el archivo, pero los cambios no aparecen!

Ehm, primero y principal, estás seguro de que poniendo esa opción se soluciona el problema?

Segundo, cuando editás el menu.lst, estás seguro de que lo hacés con privilegios de root y guardás tus cambios?

---

### Post by chamus on 2008-09-09
No estoy seguro que sea la solucion, pero es una posibilidad que he leido.
Para editar el archivo lo hago con  sudo gedit /boot/grub/menu.lst
y tambien lo he hecho buscando abriendo un nautilus y buscando el archivo.
Los cambios quedan guardados, ya que al reiniciar abro el archivo y alli esta todo, pero parece que no ejecutase esas lineas.
Ahora he visto que al iniciar despues del grub aparece esto "pci bios bug #81 found, con algunos numeros mas que no he podido anotar. Puede tener algo que ver?

Saludos y gracias por la ayuda!Aunque deba seguir iendo como solucionar esto.

---

### Post by WanderingKnight on 2008-09-09
Por qué decís entonces que no se ejecuta???

Si queda guardado queda guardado y se ejecuta así, a menos que estés modificando una entrada de kernel incorrecta.

Hay algo básico en el troubleshooting de problemas que es: si funciona de alguna manera, entonces algo se modificó que hizo que se solucione. Si modificando manualmente la entrada al bootear (e para editar, agregás la opción, b para bootear) se soluciona, entonces joya, eso lo soluciona. Pero si no se soluciona de esa forma, entonces hay que probar de otra forma.

Probá agregando noapic y nolapic en las opciones una vez que hayas averiguado que eso no funciona.

---

### Post by chamus on 2008-09-09
cualquier cosa que agrege en el archivo editando con gedit cuando booteo con el grub y edito no veo las lineas, cosa que deberia pasar, o no? Si edito manualmente( con e y b y todo eso) al apretar b y reiniciar las lineas puestas desaparecen!
Ademas ahora cuando trato de arrancar con el recovery mode dice: 
error 15: file not found
Y el menu.lst no lo he modificado!!
He notado que estos dos dias, lunes martes los cuelges se han inyensificado!! para postear esto se me colgo 3 veces!!

---

