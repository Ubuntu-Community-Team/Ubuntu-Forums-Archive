---
title: "Problemas para arrancar Ubuntu 10.04"
date: 2010-12-07
forum: Software
---

### Post by marcelo_bur on 2010-12-07
Hola. Tengo Ubuntu 10.04 instalado dentro de XP con Wubi. Lo utilizo en esta forma desde hace varios meses sin mayores problemas. Pero desde ayer por la tarde, en ocasión en que estaba usando XP para scanear un libro (es mucho más rápido que XSane y no se cuelga), al querer pasar nuevamente a Ubuntu reinicio la máquina, elijo ubuntu en el menu, enter, y la maquina se reinicia sola, o bien llego al menu de Ubuntu, enter y se reinicia, o bien quiere arrancar y se queda. Ayer apagué la maquina por completo y luego pude ingresar, hoy ya mi dió más trabajo y recién luego de reiniciar y apagar/encender varias veces pude entrar a Ubuntu.

Alguna idea de que puede estar pasando en mi máquina???

Desde ya muchas gracias.

---

### Post by biale on 2010-12-07
Mientras a alguien se le ocurre algo mas concreto, probá en verificar desde WXP al disco rígido completo. Datos y areas libres...

---

### Post by marcelo_bur on 2010-12-07
Hola. Gracias por la idea, apenas disponga de unas horas para dedicarme tranquilo a ver todo esto voy a correr  Chkdsk en XP a ver que pasa. De últimas tendré que reinstalar Ubuntu, pero eso es lo que se supone que no se hace usualmente con este sistema operativo. 
El problema comenzó en forma repentina y, pensando, lo unico inusual fue que probando usar el scaner desde un programa de manipulación de imágenes, Infantwiev, este se colgó y lo cerré desde el administrador de tareas de XP, sin embargo no veo que sea motivo para que luego no arranque bien Ubuntu, o tal vez si... Si sigo sin poder solucionarlo tal vez deba intentar instalar Lucid en una partición del disco que solo contiene datos, bue, la verdad es que no se mucho, pero sobre la marcha ire viendo y seguro algo voy a aprender.
Saludos

---

### Post by marcelo_bur on 2010-12-08
Hola. En verdad lo que pasa me resulta muy extraño. Como Ubuntu lo tengo instalado con Wubi consideré posible que algo ocurrido en windows afectase el normal inicio de Ubuntu, por lo tanto y ante todo corri el antivirus, a pesar de que uso muy poco XP, salió todo bien. Corri la aplicación de XP para reparar archivos, algo reparó, pero ni tiempo a leer el informe me dio. Probé y el problema subsistía.Se me ocurrió restarurar XP a un punto anterior al inicio del problema, tampoco sirvió. Lo único que me permite llegar a acceder a Ubuntu es iniciar primero con Windows, luego apagar la máquina, encender nuevamente y ahi si, como por milagro y hasta el momento, inicia Ubuntu correctamente.

¿¿Alguna idea de que problema en el software puede causar esto o simplemente es cosa "E MANDINGA"???

Saludos

---

### Post by biale on 2010-12-08
Ambos comparten el sistema de archivos lógico NTFS. O sea que si bajo Win hay problemas, podrían repercutir en Ubuntu.

Lo que no se es si "ademas" hay algún utilitario wubi que a su vez permita verificar off-line internamente las particiones que ve Ubuntu. Y eventualmete acceder a los datos almacenados.

En otro orden de cosas, hace un tiempo (1 año?) hubo un problema con wubi. En aquel momento cuando corrío una actualización de Ubuntu, resultó que no era compatible con wubi y destruyó el arranque. O sea que si los problemas persisten, habría que considerar algún googleo de búsqueda...

---

### Post by biale on 2010-12-08
Se cruzaron los mensajes...

Depende lo que haya reparado. Fijate en la administración de Windows, sucesos, aplicaciones, item Winlogon.

---

### Post by marcelo_bur on 2010-12-08
Hola Biale. En verdad no sabía donde buscar el informe en Win, creo que aprendí mucho más de Linux en algo más de un año que lo que aprendí de Win en casi una década. Asi que haré eso. En cuanto a Googlear el problema, ya lo he hecho, pero no he encontrado nada similar, quizás ahora seria conveniente que busque sobre el tema de la compatibilidad, aunque si el arranque estuviese destruido supongo que no habría forma de hacerlo funcionar, y menos con sistemas tan sin lógica como los de debo usar, ni tampoco hubo una actualización del kernel justo antes de que inicie el problema y creo que tampoco ninguna otra de cualquier tipo. Lo que comentas del problema de Wubi hace un tiempo me afecto, ni modo de recuperar Ubuntu, debi desinstalarlo desde Win y realizar una nueva instalación, y asi funcionó bien hasta hace dos días.
Saludos y gracias.

---

### Post by biale on 2010-12-08
De acuerdo, yo le apostaría mas a un problema del sistema de archivos que a uno de wubi.

> Lo que comentas del problema de Wubi hace un tiempo me afecto

A mi también me afecto mucho: de ahi en mas dejé de considerarlo como alternativa...

---

### Post by marcelo_bur on 2010-12-08
Si, aunque no tengo ni idea de como solucionarlo. 
Mi mayor problema es que en estos momentos la única máquina que tengo a mano es esta, la otra se la dejé a mi hija menor y la note de la mayor no anda muy bien. Y mi sitio se actualiza normalmente todos los dias, especialmente en algunos sectores. Así que quedarme sin máquina por unos dias es un problema para mi, porque no se si quienes lean esto puedan tener una idea de lo complicado que puede llegar a ser explicarle a mi hija menor que me tiene que regresar la máquina por unos dias....
Saludos

---

### Post by marcelo_bur on 2010-12-11
Hola de nuevo. Este tema se esta quedando abajo y yo sigo sin poder resolver esto.
Les cuento cual es mi rutina actualmente:
Por la mañana (generalmente) enciendo la máquina, aparece la pantalla para bootear con las opciones Windows y Ubuntu, elijo Ubuntu y la máquina se reinicia sola, aparece nuevamente la pantalla para que elija, elijo windows, inicio sesión sin problemas y una vez cargado completamente el SO 
**[COLOR="Red"]apago[/COLOR]** completamente la máquina. Vuelvo a encenderla, aparece la pantalla con las dos opciones, elijo Ubuntu y arranca sin dificultades. La uso durante todo el día (de ser posible no cambio nunca a windows, ya que solo lo utilizo para scanear), apago la máquina cuando me voy a dormir. Y al otro día de nuevo toda la historia...

Por favor... alguna idea de que es lo que pasa????

---

### Post by hectorivand on 2010-12-11
> **marcelo_bur said:**
> Hola de nuevo. Este tema se esta quedando abajo y yo sigo sin poder resolver esto.
Les cuento cual es mi rutina actualmente:
Por la mañana (generalmente) enciendo la máquina, aparece la pantalla para bootear con las opciones Windows y Ubuntu, elijo Ubuntu y la máquina se reinicia sola, aparece nuevamente la pantalla para que elija, elijo windows, inicio sesión sin problemas y una vez cargado completamente el SO 
**[COLOR="Red"]apago[/COLOR]** completamente la máquina. Vuelvo a encenderla, aparece la pantalla con las dos opciones, elijo Ubuntu y arranca sin dificultades. La uso durante todo el día (de ser posible no cambio nunca a windows, ya que solo lo utilizo para scanear), apago la máquina cuando me voy a dormir. Y al otro día de nuevo toda la historia...

Por favor... alguna idea de que es lo que pasa????

Te tiro algo... sectores defectuosos en el disco que no permita montarlo el arranque de Ubuntu, por eso reinicia?

Usa alguna herramienta como HDD Regenerator para asegurarte que el disco esta en buenas condiciones, si no lo está es muy probable que te lo repare.

Saludos
nacho

---

### Post by biale on 2010-12-11
¿Te fijaste en el registro de sucesos de WXP que fué lo que arregló el Scandisk? Es importante...

Mas ideas. PC de escritorio? Durante la noche asegurate que la compu quede desenchufada. Y lo primero a la mañana sería ingresar al BIOS para chequear la batería: la fecha y la hora no deben haber cambiado.

Fundamental! En la sentencia de arranque de Ubuntu (10.04 Lucid?) habría que borrar donde dice "quiet splash" para ver que error es el que tira antes del reinicio. Si fuera un arranque grub se haría directamente desde el archivo /boot/grub/grub.cfg. 
Siendo Wubi es posible que las sentencias de arranque de Ubuntu no esten alli. Aclaro que nunca instalé con Wubi

Otro si. Intentar arrancar con el nucleo de respaldo. O bien en modo de recuperación. Todo esto para intentar determinar que esta pasando...

Y por supuesto un backup de los datos y configuraciones por las dudas, es decir el /home

---

### Post by marcelo_bur on 2010-12-11
Hola.
Lo que más me llama la atención es que arranca bien despues de iniciar XP y volver a apagar la pc.
Respecto a pasar ese programa para reparar el disco, bueno, lei bastante y no estoy muy seguro de eso, intentaré con scandik de nuevo.
Busque el archivo "winlogon" en el registro de sucesos de Windows pero no lo encontré, ni nada con ese nombre, mañana copio todo el contenido desde la fecha del comienzo de la falla y lo transcribo aquí.
La alimentación de electricidad de la pc queda cortada todas las noches desde el estabilizador de tensión, hoy por las dudas voy a desenchufar todo, a ver si hace diferencia.
No se puede intentar arrancar con el núcleo de respaldo ni en modo de recuperación, las únicas opciones que te da la maquina al arrancar es elegir entre xp o Ubuntu, luego de elegir Ubuntu, y cuando arranca bien, recien te muestra todas las opciones.
En cuanto a respaldos, los hago periodicamente, pero desde que se inició el problema manejo todo lo realmente importante desde un par de pendrives, subo diariamente información a terabox y también ocupo algo de espacio en mi servidor,la menos importante, en directorios protegidos. En cuanto a respaldar **todo** el home, no se me había ocurrido, mañana lo hago y veo también todo es resto, hasta donde mis conocimientos me lo permitan.
El /boot/grub/grub.cfg. esta presente, pero creo que debe ser el que me muestra en segunda instancia, no con el que tengo problemas , el cual supongo que depende de Wubi. Sin embargo ahora recuerdo que, si no me equivoco, en XP se genera una carpeta "Ubuntu" que contiene unos pocos archivos, voy a ver que hay por ahí también.
Gracias por orientarme hacia nuevas posibles causas del problema.
Saludos.

---

### Post by marcelo_bur on 2010-12-12
Hola.
Esta mañana he comenzado a investigar los items sugeridos. En primer  lugar la máquina quedó totalmente desconectada de la red electrica hasta  el momento de usarla, hace un ratito apenas.
Ingresé al BIOS y todo, hasta donde yo se, se ve normal. Sali del menú e intenté ingresar directamente a Ubuntu, la maquina se reinicia como viene ocurriendo los últimos días.

Acabo de revisar y tengo este directorio C:\ubuntu\winboot, dentro del mismo se encuentrasn tres archivos: wubidr, wubidr.cfg y wubidr.mbr.
El contenido del archivo wubidr.cfg es el siguiente:

```

set show_panic_message=true

if search -s -f -n /ubuntu/disks/root.disk; then
    if loopback loop0 /ubuntu/disks/root.disk; then
        set root=(loop0)
        if [ -e /boot/grub/grub.cfg ]; then
            if configfile /boot/grub/grub.cfg; then
                set show_panic_message=false
            fi
        else
            if [ -e /grub/grub.cfg ]; then
                if configfile /grub/grub.cfg; then
                    set show_panic_message=false
                fi
            fi
        fi
    fi
fi

if [ ${show_panic_message} = true ]; then
    if search -s -f -n /ubuntu/install/boot/grub/grub.cfg; then
        if configfile /ubuntu/install/boot/grub/grub.cfg; then
            set show_panic_message=false
        fi
    else
        if search -s -f -n /grub.cfg; then
            if configfile /grub.cfg; then
                set show_panic_message=false
            fi
        fi
    fi
fi

if [ ${show_panic_message} = true ]; then
    echo "It is not possible to boot from the Ubuntu image."
    echo "Please verify that the Ubuntu installation was not removed."
    echo "If that is not the case, please check that the Windows filesystem"
    echo "is not corrupted: reboot into Windows and run: chkdsk /r"
    echo "Then try again."
fi


```

los otros dos, si no estoy equivocado, son archivos binarios que no puedo comprender en absoluto.

También he notado que en C:\ estan presentes los archivos **wubidr** que, casualmente, fue creado el día que comenzó el problema. Los he copiado a un pendrive y voy a proceder a eliminarlo a ver si soluciona algo, ya que no debería afectar a XP y siempre puedo restaurarlo.

Envio este post y sigo buscando y publicando información...

---

### Post by biale on 2010-12-12
Es evidente que al arrancar Windows esta arreglando algo, que a su vez permite que Ubuntu arranque posteriormente. El problema sería determinar que arregla y porque.

> No se puede intentar arrancar con el núcleo de respaldo ni en modo de recuperación, las únicas opciones que te da la maquina al arrancar es elegir entre xp o Ubuntu, luego de elegir Ubuntu, y cuando arranca bien, recien te muestra todas las opciones.

O sea que el problema lo tiene Wubi. Puede ser un problema lógico en Wubi, puede ser que le cueste abrir los archivos que simulan a las particiones de Ubuntu, etc

> Busque el archivo "winlogon" en el registro de sucesos de Windows pero no lo encontré

MI PC/ Mouse boton derecho/ Administrar/ Visor de sucesos/ Tipo "Aplicacion"/ Buscar Origen = Winlogon (o usar el filtro)
Puede haber un problema en la física del HDD o en NTFS. Postear lo que aparezca.

Y de paso mirar en Origen "Sistema" todos los rojos y amarillos que aparezcan.

> pero creo que debe ser el que me muestra en segunda instancia, no con el que tengo problemas

Estoy de acuerdo...

> respaldar todo el home, 

En formato tar, eventualmente comprimido.

Algo ya no esta funcionando bien y por las dudas hay que prepararse mentalmente a una migración, lo menos traumática posible. 

(1) Se que es posible montar los archivos de Wubi en modo off-line, usando un arranque live de algo (que no se). Vas a tener que investigar al respecto, y hacer alguna prueba.

(2) Un balance de espacios en el disco. Cuantas particiones, Espacio libre, espacio que ucupa Ubuntu...

---

### Post by marcelo_bur on 2010-12-12
Ahora voy a subir capturas de pantalla de detalles que me fue imposible copiar y pegar.

**La primer imagen no tiene nada que ver, fue un error mio con la numeración**

---

### Post by marcelo_bur on 2010-12-12
Hola Biale. Gracias por indicarme la ruta correcta. La unica entrada de Winlogon es la que corresponde a la comprobación de disco que yo programé luego de comenzar el problema. El informe es el siguiente:

```

Comprobando el sistema de archivos en C:
El tipo del sistema de archivos es NTFS.


Se ha programado una comprobación del disco.
Windows comprobará ahora el disco.                                         
La Id. de objetos múltiples en las entradas de índice 0x19
señalan al mismo archivo 0x94f.
Eliminando una entrada del índice $O del archivo 25.
La Id. de objetos múltiples en las entradas de índice 0x19
señalan al mismo archivo 0x3073.
Eliminando una entrada del índice $O del archivo 25.
La Id. de objetos múltiples en las entradas de índice 0x19
señalan al mismo archivo 0x3d56.
Eliminando una entrada del índice $O del archivo 25.
La entrada de índice de la Id. del objeto 0x19 señala al archivo 0x36a3
pero el archivo no tiene la Id.del objeto.
Eliminando una entrada del índice $O del archivo 25.
La entrada de índice de la Id. del objeto 0x19 señala al archivo 0x305a
pero el archivo no tiene la Id.del objeto.
Eliminando una entrada del índice $O del archivo 25.
La entrada de índice de la Id. del objeto 0x19 señala al archivo 0x36b1
pero el archivo no tiene la Id.del objeto.
Eliminando una entrada del índice $O del archivo 25.
La entrada de índice de la Id. del objeto 0x19 señala al archivo 0x26b0
pero el archivo no tiene la Id.del objeto.
Eliminando una entrada del índice $O del archivo 25.
La entrada de índice de la Id. del objeto 0x19 señala al archivo 0x3cb8
pero el archivo no tiene la Id.del objeto.
Eliminando una entrada del índice $O del archivo 25.
La entrada de índice de la Id. del objeto 0x19 señala al archivo 0x3cb9
pero el archivo no tiene la Id.del objeto.
Eliminando una entrada del índice $O del archivo 25.
La entrada de índice de la Id. del objeto 0x19 señala al archivo 0x3bf4
pero el archivo no tiene la Id.del objeto.
Eliminando una entrada del índice $O del archivo 25.
La entrada de índice de la Id. del objeto 0x19 señala al archivo 0x952
pero el archivo no tiene la Id.del objeto.
Eliminando una entrada del índice $O del archivo 25.
La entrada de índice de la Id. del objeto 0x19 señala al archivo 0x3335
pero el archivo no tiene la Id.del objeto.
Eliminando una entrada del índice $O del archivo 25.
La entrada de índice de la Id. del objeto 0x19 señala al archivo 0x3c41
pero el archivo no tiene la Id.del objeto.
Eliminando una entrada del índice $O del archivo 25.
La entrada de índice de la Id. del objeto 0x19 señala al archivo 0x3d17
pero el archivo no tiene la Id.del objeto.
Eliminando una entrada del índice $O del archivo 25.
La entrada de índice de la Id. del objeto 0x19 señala al archivo 0x3e54
pero el archivo no tiene la Id.del objeto.
Eliminando una entrada del índice $O del archivo 25.
La entrada de índice de la Id. del objeto 0x19 señala al archivo 0x3ec6
pero el archivo no tiene la Id.del objeto.
Eliminando una entrada del índice $O del archivo 25.
La entrada de índice de la Id. del objeto 0x19 señala al archivo 0x3e24
pero el archivo no tiene la Id.del objeto.
Eliminando una entrada del índice $O del archivo 25.
La entrada de índice de la Id. del objeto 0x19 señala al archivo 0x3e19
pero el archivo no tiene la Id.del objeto.
Eliminando una entrada del índice $O del archivo 25.
La entrada de índice de la Id. del objeto 0x19 señala al archivo 0x3e17
pero el archivo no tiene la Id.del objeto.
Eliminando una entrada del índice $O del archivo 25.
La entrada de índice de la Id. del objeto 0x19 señala al archivo 0x2df6
pero el archivo no tiene la Id.del objeto.
Eliminando una entrada del índice $O del archivo 25.
La entrada de índice de la Id. del objeto 0x19 señala al archivo 0x2dec
pero el archivo no tiene la Id.del objeto.
Eliminando una entrada del índice $O del archivo 25.
La entrada de índice de la Id. del objeto 0x19 señala al archivo 0x2dd9
pero el archivo no tiene la Id.del objeto.
Eliminando una entrada del índice $O del archivo 25.
La entrada de índice de la Id. del objeto 0x19 señala al archivo 0x2dda
pero el archivo no tiene la Id.del objeto.
Eliminando una entrada del índice $O del archivo 25.
La entrada de índice de la Id. del objeto 0x19 señala al archivo 0x2ddc
pero el archivo no tiene la Id.del objeto.
Eliminando una entrada del índice $O del archivo 25.
La entrada de índice de la Id. del objeto 0x19 señala al archivo 0x2ddd
pero el archivo no tiene la Id.del objeto.
Eliminando una entrada del índice $O del archivo 25.
La entrada de índice de la Id. del objeto 0x19 señala al archivo 0x2dde
pero el archivo no tiene la Id.del objeto.
Eliminando una entrada del índice $O del archivo 25.
La entrada de índice de la Id. del objeto 0x19 señala al archivo 0x2de0
pero el archivo no tiene la Id.del objeto.
Eliminando una entrada del índice $O del archivo 25.
La entrada de índice de la Id. del objeto 0x19 señala al archivo 0x2de1
pero el archivo no tiene la Id.del objeto.
Eliminando una entrada del índice $O del archivo 25.
La entrada de índice de la Id. del objeto 0x19 señala al archivo 0x2de4
pero el archivo no tiene la Id.del objeto.
Eliminando una entrada del índice $O del archivo 25.
La entrada de índice de la Id. del objeto 0x19 señala al archivo 0x2de5
pero el archivo no tiene la Id.del objeto.
Eliminando una entrada del índice $O del archivo 25.
La entrada de índice de la Id. del objeto 0x19 señala al archivo 0x2de6
pero el archivo no tiene la Id.del objeto.
Eliminando una entrada del índice $O del archivo 25.
La entrada de índice de la Id. del objeto 0x19 señala al archivo 0x2de2
pero el archivo no tiene la Id.del objeto.
Eliminando una entrada del índice $O del archivo 25.
La entrada de índice de la Id. del objeto 0x19 señala al archivo 0x2de8
pero el archivo no tiene la Id.del objeto.
Eliminando una entrada del índice $O del archivo 25.
La entrada de índice de la Id. del objeto 0x19 señala al archivo 0x2de9
pero el archivo no tiene la Id.del objeto.
Eliminando una entrada del índice $O del archivo 25.
La entrada de índice de la Id. del objeto 0x19 señala al archivo 0x2b56
pero el archivo no tiene la Id.del objeto.
Eliminando una entrada del índice $O del archivo 25.
La entrada de índice de la Id. del objeto 0x19 señala al archivo 0x3d4c
pero el archivo no tiene la Id.del objeto.
Eliminando una entrada del índice $O del archivo 25.
La entrada de índice de la Id. del objeto 0x19 señala al archivo 0x3d4d
pero el archivo no tiene la Id.del objeto.
Eliminando una entrada del índice $O del archivo 25.
La entrada de índice de la Id. del objeto 0x19 señala al archivo 0x3d50
pero el archivo no tiene la Id.del objeto.
Eliminando una entrada del índice $O del archivo 25.
La entrada de índice de la Id. del objeto 0x19 señala al archivo 0x3d51
pero el archivo no tiene la Id.del objeto.
Eliminando una entrada del índice $O del archivo 25.
La entrada de índice de la Id. del objeto 0x19 señala al archivo 0x3d4e
pero el archivo no tiene la Id.del objeto.
Eliminando una entrada del índice $O del archivo 25.
La entrada de índice de la Id. del objeto 0x19 señala al archivo 0x3d4f
pero el archivo no tiene la Id.del objeto.
Eliminando una entrada del índice $O del archivo 25.
La entrada de índice de la Id. del objeto 0x19 señala al archivo 0x3d52
pero el archivo no tiene la Id.del objeto.
Eliminando una entrada del índice $O del archivo 25.
La entrada de índice de la Id. del objeto 0x19 señala al archivo 0x3d55
pero el archivo no tiene la Id.del objeto.
Eliminando una entrada del índice $O del archivo 25.
La entrada de índice de la Id. del objeto 0x19 señala al archivo 0x3d5b
pero el archivo no tiene la Id.del objeto.
Eliminando una entrada del índice $O del archivo 25.
La entrada de índice de la Id. del objeto 0x19 señala al archivo 0x3d5c
pero el archivo no tiene la Id.del objeto.
Eliminando una entrada del índice $O del archivo 25.
La entrada de índice de la Id. del objeto 0x19 señala al archivo 0x2ef5
pero el archivo no tiene la Id.del objeto.
Eliminando una entrada del índice $O del archivo 25.
Limpiar incoherencias sin importancia en la unidad.
Liberando 289 entradas de índice no usadas del índice $SII del archivo 0x9.
Liberando 289 entradas de índice no usadas del índice $SDH del archivo 0x9.
Liberando 289 descriptores de seguridad no usados.
CHKDSK ha encontrado espacio libre marcado como asignado en el
mapa de bits de la tabla maestra de archivos (MFT).
Windows ha hecho algunas correciones en el sistema de archivos.

  83007816 KB de espacio total en disco.
  47452596 KB en 30469 archivos.
     10116 KB en 3316 índices.
         0 KB en sectores defectuosos.
    167700 KB en uso por el sistema.
El archivo de registro ha ocupado      65536 kilobytes.
  35377404 KB disponibles en disco.

      4096 bytes en cada unidad de asignación.
  20751954 unidades de asignación en disco en total.
   8844351 unidades de asignación disponibles en disco.

Información interna:
a0 82 01 00 03 84 00 00 ba b0 00 00 00 00 00 00  ................
93 0a 00 00 00 00 00 00 d9 01 00 00 00 00 00 00  ................
06 ff 6a 03 00 00 00 00 f0 41 c6 25 00 00 00 00  ..j......A.%....
d0 4d 6b 08 00 00 00 00 00 00 00 00 00 00 00 00  .Mk.............
00 00 00 00 00 00 00 00 26 77 9d 38 00 00 00 00  ........&w.8....
40 3e 8b a0 00 00 00 00 f0 3d 07 00 05 77 00 00  @>.......=...w..
00 00 00 00 00 d0 46 50 0b 00 00 00 f4 0c 00 00  ......FP........

Windows ha finalizado la comprobación del disco.
Espere mientras se inicia el sistema.


```

---

### Post by marcelo_bur on 2010-12-12
Bueno... Ya no se que más hacer o mirar en XP, intentaré arrancar Ubuntu.
Gracias por la ayuda.

---

### Post by marcelo_bur on 2010-12-12
Bien, como todos los dias, luego de haber iniciado sesión en XP Ubuntu arrancó perfectamente. Tengo alguna esperanza de que la culpa haya sido de ese archivo que tan curiosamente se creo el día del inicio del problema, pero deberé esperar a mañana para comprobarlo.
Saludos y gracias por la ayuda que me están brindando.

---

### Post by marcelo_bur on 2010-12-13
Hola. Todo lo que hice ayer fue en vano, la máquina no arrancó directamente esta mañana, ahora estoy en Windows y, con suerte, cuando termine aqui la apagaré y arrancará con Ubuntu.
Hoy corri Scandisk para que busque y repare en lo posible sectores defectuosos del disco. Una vez terminado el proceso solo aparecio un cartelito que decia "Operación completa", sin ningún informe. Busque el informe en el visor de sucesos, cosa fácil ya que apenas habia comenzado a usar la máquina, ninguna referencia a reparaciones o errores.
Les dejo una una captura de pantalla donde se muestran las particiones del disco.
Saludos

---

### Post by marcelo_bur on 2010-12-13
Aqui estoy de nuevo, desde Ubuntu. Creo que si cargando Windows, apagando la máquina por completo y volviendola a prender se soluciona el problema, debe haber "algo" que se carga en la memoria en forma transitoria desde Windows, no encuentro otra explicación. Solo que no tengo idea del "QUE" ni del "PORQUE".
Saludos

---

### Post by biale on 2010-12-13
Perfecto, ese tipo de errores no deberían aparecer. Solo se acepta la recuperación de indices y descriptores "no usados".

Supongo que la partición desconocida es para el soporte HW de la computadora?

Entretanto, se podría pensar en reinstalar los paquetes correspondientes al arranque de Wubi (?) Habría que ubicarlos con Synaptic...

Ubuntu apaga bien, preparandose para el próximo arranque? Que pasa si le reinicias Ubuntu, en lugar de apagarlo?

---

### Post by marcelo_bur on 2010-12-13
Hola Biale. La partición desconocida es una partición extendida o virtual que crea Wubi para Ubuntu.
No creo posible reparar este problema desde Ubuntu porque de alguna forma el dual boot que no me funciona esta alojado en Windows, pero igual me voy a fijar.
Solo me restaria hacer pruebas con un live CD, pero sinceramente tengo miedo de terminar de estropear todo y, lo peor, es que no encuentro en la red comentarios sobre nada parecido para guiarme. Lo que debería restaurarse es el dual boot que Wubi crea en Windows, pero, aun asi, me sigue llamando la atención que se recupere con tan solo cargar primero XP.
Todo un rompecabezas para mi. Supongo que a la larga terminaré por reinstalar Lucid con Wubi o bien en la partición del disco que se ve en el detalle y que contiene datos.
Saludos

---

### Post by biale on 2010-12-13
Ante todo me corrijo: Wubi se maneja desde Windows. Parece que el arranque se maneja desde tres archivos, el boot.ini de Win apunta a un "algo.mbr" que sería el arrancador y este a su vez le da control a un archivo "sin extension" que continua el proceso.

Aqui hay detalles interesantes:
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

Tomarlo con pinzas:
[http://www.ehow.com/how_7465639_uninstall-reinstall-wubi.html#ixzz17zd4ZePb](http://www.ehow.com/how_7465639_uninstall-reinstall-wubi.html#ixzz17zd4ZePb)

No me parece logico que Wubi requiera de una partición (?) ya que la idea es no tocar nada de lo que ya hay. A veces las notebooks suelen traer ese tipo de particiones "técnicas". Como la ve gparted?

Atencion que la partición D puede contener la carpeta "Mis Documentos". Habría que correrla de lugar antes de voltear la partición.

De todas maneras la idea sería "migrar" lo que ya hay y no "reinstalar" de cero.

---

### Post by marcelo_bur on 2010-12-13
Hola Biale. El primer link tiene datos realmente interesantes, el segundo no lo considero de gran ayuda. Mañana por la mañana voy a intentar algunas de las soluciones más sencillas, pero deberé dejar para el domingo la lectura a fondo y la busqueda y reparación de archivos que recomienda la publicación. Lo mejor de esto es que finalmente es un topico donde se menciona especificamente el problema que estoy padeciendo. 
Gracias por el link, mantendré el tema actualizado con lo que vaya haciendo y sus resultados, a ver si lo podemos marcar algún dia como SOLVED.
Saludos

---

### Post by biale on 2010-12-13
El metodo para migrar, o para acceder a la instalación si a Wubi se le ocurre dejar de arrancar sería algo asi:

(1) Montar offline las partiones truchas como se pueda. En este caso root.disk

Boot the Ubuntu Desktop CD, or another LiveCD, then mount the windows partition:

sudo mkdir /win
sudo mount /dev/sda1 /win

Replace sda1 with the appropriate device (a = disk, 1 = partition number), then mount the virtual disk therein

sudo mkdir /vdisk
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk

Now the content of the virtual disk will be visible under /vdisk.

Hasta aqui podes probar sin riesgo. Lo que sigue hay que pensarlo mas.

(2) Con cp -axv copiar los contenidos a particiones reales previamente armadas a manopla.  O eventualmente intentar alguna reparación:

To check the filesystem you can use:

sudo fsck /win/ubuntu/disks/root.disk

(3) Retocar la fstab y con el supergrub disk arrancar al Ubuntu corrido de lugar. Idem para Windows, antes de tocar al sector de arranque

(4) Recien ahora instalar grub.

---

### Post by marcelo_bur on 2010-12-13
Hola. Todo esto me lo tengo que tomar con calma y paciencia. Mi principal objetivo es que, al menos, pueda arrancar siempre bien XP y desde ahí ver que es lo que se puede hacer. Mis conocimientos son limitados, la migración la veo, por esos motivos, algo riesgosa. Mi objetivo es lograr reparar el problema y, de no lograrlo, decidir entre desinstalar desde el panel de control de Win y reinstalar nuevamente con Wubi o bien reinstalar usando la partición que tengo con datos.
Saludos

---

### Post by marcelo_bur on 2010-12-14
Hola de nuevo. Sigo investigando este problema. Creí que encontraría la solución utilizando estas lineas del link que me dejó Biale:

"
**Windows Missing hal.dll**

 This is a  frequent error seen on Wubi installations.  It leaves Windows unable to  boot and complains about a missing "C:\windows\system32\hal.dll" which  is the Hardware Abstraction Layer for Windows. 
This problem can be fixed by using the following steps. 

[LIST=1]
[*]Boot-up an Ubuntu [LiveCd]("https://help.ubuntu.com/community/LiveCD") 
[*]On the top taskbar  click on the "Places" menu  
[*]Select  your Windows partition (it will only be shown by its partition size) 
[*]Navigate to  windows/system32/dllcache 
[*]Copy  hal.dll from there to windows/system32/ 
[*]Reboot.
[*]"""
[/LIST]
Sin embargo el archivo hal.dll está presente en el directorio **windows/system32** lo cual elimina esta posibilidad.

Así que pasé a la segunda posibilidad donde podría estar el error:

"Note that sometimes files are moved by Windows into a hidden folder  called c:\found.000. You need to have c:\ubuntu\disks\root.disk and  c:\ubuntu\disks\boot. If you do not see those, look for found.000. You  need to change the Windows Explorer settings to be able to see hidden  folders first, then move the files from found.000 to their original  location."

Aquí la cosa se me pone un poco más confusa y no estoy seguro de esto.
Por comenzar no existe ninguna carpeta **c:\found.000, T**engo el archivo c:\ubuntu\disks\root.disk y la carpeta c**:\ubuntu\disks\boot**, sin embargo lo que me confunde es que esta carpeta solo contiene otra carpeta **c:\ubuntu\disks\boot\grub** la cual a su vez está vacia. Pero tambien tengo el directorio **c:\ubuntu\winboot\** el cual contiene los tres archivos que mencione en un mensaje anterior.

Aparentemente, y según mi entender, la máquina arranca con Ubuntu luego de hacerlo con XP por lo que dice esta frase: 

"Ubuntu cannot be booted if Windows has not been shut down cleanly, you  have to clear the Windows filesystem from Windows (there is no chkdsk  equivalent for Linux yet)."


Alguna sugerencia???

Saludos

---

### Post by marcelo_bur on 2010-12-14
Y por último acabo de hacer esto:

"If Wubi fails to start, boot into Windows, run chkdsk /r from Windows on  the same drive where you have installed Ubuntu, shutdown cleanly and  then try to boot into Ubuntu again."

El informe es el siguiente:

Comprobando el sistema de archivos en C:
El tipo del sistema de archivos es NTFS.

Se ha programado una comprobación del disco.
Windows comprobará ahora el disco.                                         
Liberando 29 entradas de índice no usadas del índice $SII del archivo 0x9.
Liberando 29 entradas de índice no usadas del índice $SDH del archivo 0x9.
Liberando 29 descriptores de seguridad no usados.
CHKDSK está comprobando los datos de archivo (etapa 4 de 5)...
Comprobación de datos de archivo terminada.
CHKDSK está comprobando el espacio disponible (etapa 5 de 5)...
La comprobación de espacio libre se ha completado.

  83007816 KB de espacio total en disco.
  47518916 KB en 30850 archivos.
     10252 KB en 3327 índices.
         0 KB en sectores defectuosos.
    167704 KB en uso por el sistema.
El archivo de registro ha ocupado      65536 kilobytes.
  35310944 KB disponibles en disco.

      4096 bytes en cada unidad de asignación.
  20751954 unidades de asignación en disco en total.
   8827736 unidades de asignación disponibles en disco.

Saludos

---

### Post by marcelo_bur on 2010-12-14
Aqui estoy, ahora con Ubuntu. Siguen los problemas y las situaciones llamativas. Comprobé que si REINICIO la máquina luego de haberse cargado Windows, la máquina sigue reiniciandose cuando quiero entrar a Ubuntu. Sin embargo si APAGO la máquina y la vuelvo a encender Ubuntu carga bien.
Ya no se que pensar...

Saludos.

---

### Post by marcelo_bur on 2010-12-14
PREGUNTA:

¿Podré salir del paso arrancando la máquina con un cd con SuperGrub2?????
Saludos

---

### Post by biale on 2010-12-14
Marcelo:

El último chkdsk fue impecable. Descarto ahora un problema en NTFS.

Con el SGD no vas a poder levantar a Ubuntu, o lo hace Wubi o no arranca, que es lo que suele suceder. De lo poco que pude encontrar...

Sin riesgos, podes probar en copiar bajo Windows:

c:\ubuntu\winboot\wubildr  hacia  c:\wubildr

Hay reportes de problemas con Wubi, y no del año pasado sino de este año, muy recientes.

Lo mejor sería: (1) (Importante) verificar que el/los archivos de Wubi se puedan montar en un arranque live usando el método que ya escribí (2) Averiguar que tiene la partición desconocida (manual del equipo) y hasta que punto se puede borrar. (3) Prepararse mentalmente y con tranquilidad para una instalación mas nativa.

Entretanto, hay que tener en cuenta que las actualizaciones de Ubuntu que puedan afectar el arranque pueden arreglar o empeorar.

¿En Win, ademas de los archivos root y swap, hay un archivo home?

---

### Post by marcelo_bur on 2010-12-14
Hola Biale.
Ya tengo el archivo c:\wubildr, este es justamente el que figuraba creado el día en que inició el problema y no el día en que hice la instalación, pero ya lo cambié por el original, que estaba respaldado, asi que por ese lado nada.
No existe un archivo "home", mañana me voy a tomar un rato para publicar todo el árbol de carpetas y archivos relacionados con la instalación de Ubuntu dentro de XP (que no es muy grande por otra parte).
Saludos

---

### Post by marcelo_bur on 2010-12-15
Bueno, aqui esta lo que prometí en el mensaje anterior, espero que se entienda, no tengo mucho tiempo ni soy muy aficcionado a hacer este tipo de cosas.

---

### Post by marcelo_bur on 2010-12-15
Y por ahora abandono este tema, aunque no así la investigación del mismo por completo. Mientras pueda arrancar la máquina como hasta el día de hoy así la seguiré usando hasta que, o bien se arregle solo el problema o ya no pueda entrar a Ubuntu. Entretanto ire buscando cuando tengo tiempo nueva información. Pero estos últimos dias este problema me ha perjudicado en mi trabajo por el tiempo que le he dedicado al mismo.
Saludos

---

### Post by marcelo_bur on 2010-12-17
En el poco tiempo de que he dispuesto esta semana he seguido buscando información y soluciones. Hasta el momento todo sigue igual.
Publico este mensaje para que el tema no quede en el olvido.
Saludos

---

### Post by marcelo_bur on 2010-12-19
Hola. Hoy domingo, con algo de fiaca pero más tiempo para mis cosas, decidí seguir investigando el problema del que trata este tema. Como todos los días antes de iniciar en XP lo intenté directamente con Ubuntu, por si las moscas. Y hoy había muchas moscas, arrancó sin ningún problema. Ahora veré si esto es permanente, solo ocurre en dias feriados o que. Tal vez alguna de las velas que prendí dio resultado, pero no recuerdo de que color era la última...
Así que dejo pendiente la investigación para el próximo domingo, si el problema reaparece. Y si no lo hace, tendré que comenzar a creer en los milagros de Navidad y dejar las cosas así.
Saludos

---

### Post by marcelo_bur on 2010-12-20
Hola. Segundo día que la máquina arranca normalmente.
Ayer recordé, luego de escribir aqui, que el sábado hubo una actualización de sistema, aunque no recuerdo, salvo por el navegador Chromium, cuales fueron los archivos incluidos. Supongo que ahi debe encontrarse la razón de que ahora funcione nuevamente en forma normal.
Saludos

---

### Post by biale on 2010-12-20
Fijate en /var/log/apt los paquetes actualizados. Si actualizo el kernel, también ha tocado el arranque y probablemente tambien solucionado el problema.

---

### Post by marcelo_bur on 2010-12-20
Hola Biale.
Estaba seguro de que no se había acutalizado el kernel porque cuando eso ocurre pide reiniciar la máquina, y eso no había ocurrido.
De todas formas busqué las actualizaciones para postearlas aqui y, de casualidad, noté algo que puede ser interesante; el día anterior al inicio del problema también hubo una actualización y no lo recordaba.
Dejo los detalles de cada una, a ver si vos que sabes más de esto encontras alguna relación, o mejor, como tengo alguna duda respecto a la fecha exacta del inicio del problema, dudo entre el 7 y el 8 de diciembre, dejo todas las del periodo:

```
Start-Date: 2010-12-07  12:29:44
Upgrade: chromium-browser-inspector (7.0.517.44~r64615-0ubuntu0.10.04.1, 8.0.552.215~r67652-0ubuntu0.10.04.1), chromium-browser (7.0.517.44~r64615-0ubuntu0.10.04.1, 8.0.552.215~r67652-0ubuntu0.10.04.1), grub-pc (1.98-1ubuntu8, 1.98-1ubuntu9), dnsmasq-base (2.52-1, 2.52-1ubuntu0.1), grub-common (1.98-1ubuntu8, 1.98-1ubuntu9)
End-Date: 2010-12-07  12:30:31

Start-Date: 2010-12-08  08:57:39
Upgrade: libmagickcore2-extra (6.5.7.8-1ubuntu1, 6.5.7.8-1ubuntu1.1), libmagickcore2 (6.5.7.8-1ubuntu1, 6.5.7.8-1ubuntu1.1), libmagick++2 (6.5.7.8-1ubuntu1, 6.5.7.8-1ubuntu1.1), libmagickwand2 (6.5.7.8-1ubuntu1, 6.5.7.8-1ubuntu1.1), libssl0.9.8 (0.9.8k-7ubuntu8.4, 0.9.8k-7ubuntu8.5), imagemagick (6.5.7.8-1ubuntu1, 6.5.7.8-1ubuntu1.1), openssl (0.9.8k-7ubuntu8.4, 0.9.8k-7ubuntu8.5), perlmagick (6.5.7.8-1ubuntu1, 6.5.7.8-1ubuntu1.1)
End-Date: 2010-12-08  08:59:07

Start-Date: 2010-12-10  09:24:13
Upgrade: libkrb5-3 (1.8.1+dfsg-2ubuntu0.3, 1.8.1+dfsg-2ubuntu0.4), libkrb5support0 (1.8.1+dfsg-2ubuntu0.3, 1.8.1+dfsg-2ubuntu0.4), xulrunner-1.9.2 (1.9.2.12+build1+nobinonly-0ubuntu0.10.04.1, 1.9.2.13+build3+nobinonly-0ubuntu0.10.04.1), mysql-common (5.1.41-3ubuntu12.7, 5.1.41-3ubuntu12.8), libk5crypto3 (1.8.1+dfsg-2ubuntu0.3, 1.8.1+dfsg-2ubuntu0.4), firefox (3.6.12+build1+nobinonly-0ubuntu0.10.04.1, 3.6.13+build3+nobinonly-0ubuntu0.10.04.1), update-inetd (4.35, 4.35ubuntu0.1), firefox-gnome-support (3.6.12+build1+nobinonly-0ubuntu0.10.04.1, 3.6.13+build3+nobinonly-0ubuntu0.10.04.1), libmysqlclient16 (5.1.41-3ubuntu12.7, 5.1.41-3ubuntu12.8), firefox-branding (3.6.12+build1+nobinonly-0ubuntu0.10.04.1, 3.6.13+build3+nobinonly-0ubuntu0.10.04.1), libgssapi-krb5-2 (1.8.1+dfsg-2ubuntu0.3, 1.8.1+dfsg-2ubuntu0.4)
End-Date: 2010-12-10  09:24:48

Start-Date: 2010-12-17  09:51:42
Upgrade: libc-bin (2.11.1-0ubuntu7.5, 2.11.1-0ubuntu7.6), libapparmor1 (2.5-0ubuntu3, 2.5.1-0ubuntu0.10.04.1), gnome-settings-daemon (2.30.1-0ubuntu1, 2.30.1-0ubuntu1.1), libapparmor-perl (2.5-0ubuntu3, 2.5.1-0ubuntu0.10.04.1), chromium-browser-inspector (8.0.552.215~r67652-0ubuntu0.10.04.1, 8.0.552.224~r68599-0ubuntu0.10.04.1), libc-dev-bin (2.11.1-0ubuntu7.5, 2.11.1-0ubuntu7.6), chromium-browser (8.0.552.215~r67652-0ubuntu0.10.04.1, 8.0.552.224~r68599-0ubuntu0.10.04.1), libc6-i686 (2.11.1-0ubuntu7.5, 2.11.1-0ubuntu7.6), libc6-dev (2.11.1-0ubuntu7.5, 2.11.1-0ubuntu7.6), apparmor (2.5-0ubuntu3, 2.5.1-0ubuntu0.10.04.1), apparmor-utils (2.5-0ubuntu3, 2.5.1-0ubuntu0.10.04.1), libc6 (2.11.1-0ubuntu7.5, 2.11.1-0ubuntu7.6)
End-Date: 2010-12-17  09:52:49
```

Saludos

---

### Post by biale on 2010-12-20
Todo lo que diga "grub", le va a pasar muy cerca...

Dije kernel porque hay una actualizacion del kernel dando vueltas. Por las dudas no la apliques durante las fiestas.

Lo demas no me suena, pero tampoco creas que se demasiado.

---

### Post by marcelo_bur on 2010-12-21
Ok Biale, por las dudas no correré actualizaciones hasta entrado enero.
Lo curioso es que en la actualización que pudo ser la causa del problema si hay dos referencias a grub, pero no encuentro ninguna en la que posiblemente la haya resuelto.
Saludos

---

