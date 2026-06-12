---
title: "[AYUDA] No inicia aMSN"
date: 2008-08-05
forum: Software
---

### Post by ax2_85 on 2008-08-05
Tengo ese problema, cuando intento entrar al amsn este no inicia, se queda en iniciando sesion por muuucho tiempo y no pasa nada...

---

### Post by pedrogfrancisco on 2008-08-05
Yo no hablo español :(

Pero entiendo.

Es una "mudança" de protocolo, mira aqui: [http://www.amsn-project.net/forums/viewtopic.php?t=5552](http://www.amsn-project.net/forums/viewtopic.php?t=5552) .

Y aqui: [http://ubuntuforums.org/showthread.php?t=880424&highlight=amsn](http://ubuntuforums.org/showthread.php?t=880424&highlight=amsn) [in english]

---

### Post by ax2_85 on 2008-08-05
vc fala portugues? eu entendo, pode me explicar bem o que é isso?

---

### Post by beniwtv on 2008-08-05
Hola,

Lo que te pasa es que Microsoft ha cambiado una parte del protocolo (simplemente lo han quitado).

Lo que tienes que hacer es desinstalar aMSN desde el Synaptic e instalar la version más reciente de la página de aMSN (0.97.2).

Si quieres, mientras también puedes conectar sin problemas con Pidgin o Kopete.

Un saludo,

---

### Post by pol666 on 2008-08-05
no hablamos ni Ingles ni Portuguez pero pedrogfrancisco se expreso bien, es una mudanZa de protocolos ;)

---

### Post by ax2_85 on 2008-08-05
Entiendo que es el foro de español, pero como me di cuenta que hablaba en portugues se lo pregunte, ademas era el unico q me habia contestado hasta el momento.

Voy a probar desinstalado y volviendo a instalar.

---

### Post by ax2_85 on 2008-08-05
Listo, tema solucionado :)

---

### Post by pol666 on 2008-08-05
Buenisimo, podes marcar como Solved

---

### Post by javier-2714 on 2008-08-05
hola tengo el mismo problema uso ubuntu 7.04 como instalo la nueva vercion ya que  baje en autopacage .deb pero tengo problemas de dependencia con las verciones y no se compilar agradeseria alguna ayuda saludos.

---

### Post by leo_rockway on 2008-08-05
@javier-2714: no sé si querés usar especificamente aMSN, pero podrías bajar el último emesene y ver si ese te funciona.
Está escrito en Python así que no es necesario compilar.

---

### Post by javier-2714 on 2008-08-06
leo_rockway  El emesene lo prove hace un tiempo atras y no me gusto no podia enviar archivos y al querer abrir mi correo no hacia nada me llebo bien con el amsn me gustaria tener la ultima vercion si alguien me puede orientar como instalarlo se agradeseria.

---

### Post by juanman on 2008-08-06
> **javier-2714 said:**
> leo_rockway  El emesene lo prove hace un tiempo atras y no me gusto no podia enviar archivos y al querer abrir mi correo no hacia nada me llebo bien con el amsn me gustaria tener la ultima vercion si alguien me puede orientar como instalarlo se agradeseria.

Actualmente emesene puede enviar archivos y se puede abrir sin problemas el correo tambien...

Igualmente, si queres usar amsn, en hardy acaba de salir una actualizacion (la 0.97+final-0ubuntu5.1) q soluciona el problema, supongo q en feisty tambien habra salido... Asi que solo tenes q actualizar el sistema...

---

### Post by ax2_85 on 2008-08-06
Como hago para poner el tema solved?

---

### Post by javier-2714 on 2008-08-06
El tema es que en los repositorios de feisty solo esta la 0.96 y yo baje de un foro la 0.97b en paquete .deb es la que estaba usando sin problemas y fesity no hay actualizacion para esta version no se como hacer.

---

### Post by Barasuishou on 2008-08-06
hola, a mi me pasaba lo mismo pero descargo el archivo para reinstalarlo, y me tira que no pudo por que no tengo una versión actualizada de glibc_2.0. minimo, yo tengo ubuntu de 64 bits, como hago ???

---

### Post by leo_rockway on 2008-08-06
Pueden probar bajar el paquete de Intrepid [0] y ver si se satisfacen todas las dependencias en la versión de Ubuntu que estén usando. Están para bajar los páquetes en ambas arquitecturas (i386 y amd64).

[0] [http://packages.ubuntu.com/intrepid/amsn](http://packages.ubuntu.com/intrepid/amsn)

---

### Post by juanman on 2008-08-06
Mmm antes q el paquete de Intrepid prueben el de Hardy que funciona...
Y sino borren el amsn desde synaptic e instalen el autopackage de la web de amsn [http://www.amsn-project.net/linux-downloads.php](http://www.amsn-project.net/linux-downloads.php)

---

### Post by javier-2714 on 2008-08-07
Baje el autopackage me tira error Error: Unable to prepare package AMSN MSN client.

tambien el .deb de Hardy , intrepid los dos lo mismo problemas de dependencias Error:Dependency is not satisfiable: libc6 

me fije en synaptic esta instalada libc6 quiere la vercion mas nueva que usa Hardy que mas puedo probar saludos.

---

### Post by juanman on 2008-08-07
Si falla el autopackage, creo q no te va a quedar otra q compilarlo desde las fuentes... Bajate el amsn sources y segui estas instrucciones: [http://amsn-project.net/wiki/Installing_Tarball](http://amsn-project.net/wiki/Installing_Tarball)

---

### Post by javier-2714 on 2008-08-11
Hola nuevamente estoy empeñado en instalar la 0.97.2 del amsn en feisty y no puedo me baje el tarball  estoy luchando para compilarlo no entiendo ingles pero estoy tratando supestamenpe instale las dependencias que me pide se instalo me aparesio el enlase simbolico pero le doy doble clik y no pasa nada pongo en consola amsn y mi tira esto :

javier@javier-desktop:~$ amsn
Error in startup script: extra characters after close-brace
    while executing
"set command [list  $self  {*}$Snit_optionInfo(configure-$option)  $option]
            "
    (procedure "snit::RT.CacheConfigureCommand" line 36)
    invoked from within
"snit::RT.CacheConfigureCommand  $type $selfns $win $self $option"
    (procedure "::snit::RT.method.configurelist" line 7)
    invoked from within
"::snit::RT.method.configurelist $type $selfns $win $self $args"
    (procedure "::snit::RT.method.configure" line 4)
    invoked from within
"$self configure -width $arrow1width"
    (procedure "::pixmapscrollbar::Snit_constructor" line 154)
    invoked from within
"::pixmapscrollbar::Snit_constructor ::pixmapscrollbar ::pixmapscrollbar::Snit_inst1 .plugins_log.ys .plugins_log.ys -command {.plugins_log.info yview}"
    ("eval" body line 1)
    invoked from within
"eval [linsert $arglist 0  ${type}::Snit_constructor $type $selfns $instance $instance]"
    (procedure "RT.ConstructInstance" line 9)
    invoked from within
"RT.ConstructInstance $type $selfns $name $args"
    (procedure "::snit::RT.widget.typemethod.create" line 53)
    invoked from within
"scrollbar $window.ys -command "$window.info yview""
    (procedure "::pluginslog::draw" line 12)
    invoked from within
"::pluginslog::draw"
    invoked from within
"if { $initialize_amsn == 1 } {
     ::pluginslog::draw
}"
    (file "pluginslog.tcl" line 210)
    invoked from within
"source pluginslog.tcl"
    ("uplevel" body line 27)
    invoked from within
"uplevel \#0 {

        # amsncore.tcl is already loaded but we'll re-source it here in case we manually do reload_files
        source amsncore.tcl
        source audio.tc..."
    (procedure "reload_files" line 2)
    invoked from within
"reload_files"
    (file "/usr/bin/amsn" line 272)
javier@javier-desktop:~$ 

no se por que se ponen esas caritas cuando pego lo de la consola en su lugar hay 2 veces : 
me podrían decir que me falta o que hice mal se los agradeceria.

---

### Post by tuxxy on 2008-08-11
[http://www.getdeb.net/app/aMSN](http://www.getdeb.net/app/aMSN)

---

### Post by javier-2714 on 2008-08-11
No funciona en feisty  hay problemas con las versiones de las dependencias que requiere ya lo puse antes no queda otra que compilarlo y ya busque en un montón de foros hice todo como dicen pero no me inicia alguno que sepa compilar que me ayude saludos.

---

### Post by Barasuishou on 2008-08-11
si, yo trate de instalarlo y no me deja me dice que noseque de las dependencias en hardy x64, no lo puedo updatear :S

---

### Post by juanman on 2008-08-11
> **javier-2714 said:**
> Hola nuevamente estoy empeñado en instalar la 0.97.2 del amsn en feisty y no puedo me baje el tarball  estoy luchando para compilarlo no entiendo ingles pero estoy tratando supestamenpe instale las dependencias que me pide se instalo me aparesio el enlase simbolico pero le doy doble clik y no pasa nada pongo en consola amsn y mi tira esto :

javier@javier-desktop:~$ amsn
Error in startup script: extra characters after close-brace
    while executing
"set command [list  $self  {*}$Snit_optionInfo(configure-$option)  $option]
            "
    (procedure "snit::RT.CacheConfigureCommand" line 36)
    invoked from within
"snit::RT.CacheConfigureCommand  $type $selfns $win $self $option"
    (procedure "::snit::RT.method.configurelist" line 7)
    invoked from within
"::snit::RT.method.configurelist $type $selfns $win $self $args"
    (procedure "::snit::RT.method.configure" line 4)
    invoked from within
"$self configure -width $arrow1width"
    (procedure "::pixmapscrollbar::Snit_constructor" line 154)
    invoked from within
"::pixmapscrollbar::Snit_constructor ::pixmapscrollbar ::pixmapscrollbar::Snit_inst1 .plugins_log.ys .plugins_log.ys -command {.plugins_log.info yview}"
    ("eval" body line 1)
    invoked from within
"eval [linsert $arglist 0  ${type}::Snit_constructor $type $selfns $instance $instance]"
    (procedure "RT.ConstructInstance" line 9)
    invoked from within
"RT.ConstructInstance $type $selfns $name $args"
    (procedure "::snit::RT.widget.typemethod.create" line 53)
    invoked from within
"scrollbar $window.ys -command "$window.info yview""
    (procedure "::pluginslog::draw" line 12)
    invoked from within
"::pluginslog::draw"
    invoked from within
"if { $initialize_amsn == 1 } {
     ::pluginslog::draw
}"
    (file "pluginslog.tcl" line 210)
    invoked from within
"source pluginslog.tcl"
    ("uplevel" body line 27)
    invoked from within
"uplevel \#0 {

        # amsncore.tcl is already loaded but we'll re-source it here in case we manually do reload_files
        source amsncore.tcl
        source audio.tc..."
    (procedure "reload_files" line 2)
    invoked from within
"reload_files"
    (file "/usr/bin/amsn" line 272)
javier@javier-desktop:~$ 

no se por que se ponen esas caritas cuando pego lo de la consola en su lugar hay 2 veces : 
me podrían decir que me falta o que hice mal se los agradeceria.

Proba instalando tk8.4 y tk8.4-dev y recompilando... Bajaste la version de tk8.4 o la de tk8.5?


PD: Para q no te convierta :P a una carita, cuando mandes el mensaje tilda la casilla "Disable smilies in text"

---

### Post by juanman on 2008-08-11
> **Barasuishou said:**
> si, yo trate de instalarlo y no me deja me dice que noseque de las dependencias en hardy x64, no lo puedo updatear :S

Pastea el error, deberia funcionar sin problemas en hardy...

---

### Post by javier-2714 on 2008-08-13
Baje la tk8.4 y ya instale tk8.4 y tk8.4-dev no se que mas quiere no se interpretar lo que tira es lo mismo que ya puse yo tengo feisty saludos.

---

### Post by javier-2714 on 2008-08-13
Bueno finalmente lo conseguí pude compilarlo despues de romperme la cabeza un par de días  el tema era que tenia instalado tcl8.5, tk8.5 y ademas busque en forma manual y elimine todo lo que había con amsn después lo volví a compilar y buala abrió y funciona perfecto la 0.97.2 en feisty saludos.

[http://tecnicoslinux.com.ar/node/197](http://tecnicoslinux.com.ar/node/197)

---

