---
title: "[SOLVED] Problemas con la Barra de Menu"
date: 2008-05-16
forum: Software
---

### Post by lushnok on 2008-05-16
No sé si la frase correcta es "barra de menú" o "Panel de borde superior e inferior", el caso es que al iniciar (y voler a reiniciar por lógica win) ubuntu 8.04 no me aparecen las barras en cuestión, no la de arriba, ni la de abajo.
Busqué en la web y no encontré más que un treah en catalán... no entiendo mucho de linux, menos de catalán y no quise meter los garfios...
Justo que había terminado de migrar mis cuentas de correo desde outlook! Instalé Ubuntu el sábado pasado y pensé que ya estaba ok para funcionar todo desde acá...

Para graficar un poco más qué pasa les dejo una impresión de pantalla.

Tenía configurado el cube, y otras cosas del compiz.

¿alguna idea?

Mañana tendré que seguir con windows :( 

PD: como verán, no puedo acceder a la terminal... por lo que también pediría ayuda sobre ese detalle :S

---

### Post by Kabezon on 2008-05-16
Alt+F2 y poné
> gnome-panel 

Es lo único que se me ocurre. Si no funciona, ingeniátelas para abrir una terminal (no, no existe un atajo predemitado para abrirla) y poné:
> sudo apt-get update
sudo apt-get install --reinstall gnome-panel
Después volvé a probar si el primer comando funciona (hacé un restart por si acaso...) Si no funciona, hasta ahí llegan mis conocimientos :P

*Edito*
Para abrir una terminal hace Alt+F2 y poné
> gnome-terminal

---

### Post by lushnok on 2008-05-16
Kabezón, 

Gracias, pero no pasó  nada de nada...
¿el comando de reinstall, lo copio tal como lo pusiste? Si es así, naranjas.

¿alguna otra sugerencia?

---

### Post by lushnok on 2008-05-16
Esto podría darnos una sugerencia de ¿qué hacer?

---

### Post by valucha on 2008-05-16
[COLOR="DarkOrchid"]¿Es posible que hayas desisntalado algunn programa como el soundjuicer, tomboy, etc? alguno que cuando lo desinstalaste te dió un mensaje que decia que además ibas a desisntalar ubuntu-desktop o grnome-desktop?

A mi me pasó con Hardy (con las otras versiones no) siempre los desinstalaba y ahora no pude porque me pasaba eso...

Yo no tuve tiempo de arreglarlo,porque estaba con parciales y necesitaba la compu, pero probá poniendo alt+f2 y después ahi escribi "synaptic" y después reinstalá el soundjuicer o alguno de esos (los que desisntalaste) y fijate si funciona...

Si lo hace era ese el problema, sino, avisame y te digo que otra cosas pude haber hecho que pudieron causar ese problema...

Saludos.[/COLOR]

---

### Post by lushnok on 2008-05-16
Gracias Valucha.

desinstalé "evolution" por que seguía bajando los mails aun habiendo instalado thunderbird2.

al apretar alt f2 no baja la terminal... asi que voy con alt ctrl f2, pero sin el entorno gráfico digamos...

ahora tuve que volver a win, pero esta noche probaré de nuevo.

---

### Post by Kabezon on 2008-05-16
> **lushnok said:**
> Kabezón, 

Gracias, pero no pasó  nada de nada...
¿el comando de reinstall, lo copio tal como lo pusiste? Si es así, naranjas.

¿alguna otra sugerencia?
Qué sé yo... podrías abrir una terminal y escribir gnome-panel a ver qué te sale, después copiarlo y pegarlo acá. A mí me sale esto, mirá:
> kabezon@kabezon-desktop:~$ gnome-panel
A panel is already running.


---

### Post by lushnok on 2008-05-16
Bien, la cosa siguió así:
* CTRL ALT F2 y a una terminal: ahi puse gnome-panel y me dijo que no estaba instalado. 
* ejecuto: sudo apt-get install gnome-panel, al instalarlo salgo del "modo" terminal (CTRL ALT F5).
* reinicio y al reiniciar aparecen las barras en cuestión, pero con tres errores (no aparece las apps "switch user" "trash" ni "mixer") y me pregunta en cada uno si quiero borrar o no borrarlos. Como aparecieron actualizaciones, pensé que ubuntu detecto que fataban esas apps, actualicé, reinicié y siguen apareciendo los errores.

Adjunto pantallazo.

PD: como el tema de que no aparecian las barras se terminó, pero aparecieron temas como correlato del problema, no sé si tendran que dar el problema como solucionado y luego discutir esto en otro thread.

---

### Post by Kabezon on 2008-05-16
> **lushnok said:**
> Bien, la cosa siguió así:
* CTRL ALT F2 y a una terminal: ahi puse gnome-panel y me dijo que no estaba instalado. 
* ejecuto: sudo apt-get install gnome-panel, al instalarlo salgo del "modo" terminal (CTRL ALT F5).
* reinicio y al reiniciar aparecen las barras en cuestión, pero con tres errores (no aparece las apps "switch user" "trash" ni "mixer") y me pregunta en cada uno si quiero borrar o no borrarlos. Como aparecieron actualizaciones, pensé que ubuntu detecto que fataban esas apps, actualicé, reinicié y siguen apareciendo los errores.

Adjunto pantallazo.

PD: como el tema de que no aparecian las barras se terminó, pero aparecieron temas como correlato del problema, no sé si tendran que dar el problema como solucionado y luego discutir esto en otro thread.
Supongo que el problema es que no están instalados los applets. 
> sudo apt-get install gnome-applets

---

### Post by lushnok on 2008-05-16
Almost there! :D

Gracias gente, ya aparece todo... menos el user switch. Pero como no creo necesitarlo (solo yo uso la máquina) ¿no sería necesario ponerlo, digo, lo borro la próxima vez que inicie sesión, no?

Si lo borro, entonces, problema resuelto.

PD: en alguna metida de garfios (por que acá, todo pasa por que uno lo hace así) hice algo que no permite al thunderbird iniciar... con la consiguiente incomodidad de no poder trabajar con un servidor de correo... ¿abro otro thread para eso, no?

---

### Post by Kabezon on 2008-05-16
> **lushnok said:**
> Almost there! :D

Gracias gente, ya aparece todo... menos el user switch. Pero como no creo necesitarlo (solo yo uso la máquina) ¿no sería necesario ponerlo, digo, lo borro la próxima vez que inicie sesión, no?

Si lo borro, entonces, problema resuelto.

PD: en alguna metida de garfios (por que acá, todo pasa por que uno lo hace así) hice algo que no permite al thunderbird iniciar... con la consiguiente incomodidad de no poder trabajar con un servidor de correo... ¿abro otro thread para eso, no?
Recomendaría que sí. Supongo que el user switcher no sale porque no debe estar instalado tampoco. Hacé una cosa, buscá gnome-panel en Synaptic y dale click derecho, instalá todas las aplicaciones recomendadas. Hacé lo mismo con gnome-applets.

---

### Post by valucha on 2008-05-16
[COLOR="DarkOrchid"]Bueno, al parecer encontramos el error que al desinstalar algún programa dentro del paquete gnome-desktop o ubuntu-desktop no recuerdo, te desisntala el gnome-panel...
Es un bug? o es una nueva "forma de que conserves ese metapaquete"? porque antes no pasaba.[/COLOR]

---

### Post by lushnok on 2008-05-16
Pues, yo a "conciencia" no desinstalé ninguno de los dos. 
Lo que sí quise hacer fue desisntalar el Evolution mail, por que usaría el Thunderbird (al condicional ahora, por que no responde!!).

Pero sí, se solucionó todo reinstalando desde el evolution mail hasta el gnome-desktop.

Gracias a los dos.

PD: el resto de la conversa, por ahora me excede.

---

### Post by AionAlexiel on 2008-11-24
Buenas a todos, acaba de sucederme lo mismo y a pesar de la alegria al encontrar este post temo que no logre aboslutamente nada, no me ha sido posible

Tratare de resumir lo que paso:

Llevo 2 dias en Ubuntu y estaba revizando paquetes y repositorios, instale el thunderbird y luego pense

Thunderbird+Evolution=Perdida de Recursos, Thunderbird mata Evo.

Asi que procedi a desinstalar Evolution y todo normal, apague el equipo y a dormir, volvi y sorpresa, sin aboslutamente ninguna barra, de no ser por que a traves de la ayuda se puede acceder a mozilla me ubiera fregado.

Encontre este post y realize:

Ctr+Alt+F2

Loguee

$ gnome-panel

Nada, asi que procedi

$sudo apt-get install gnome-panel
$sudo apt-get update

Luego continue a instalar el origen del problema, evolution

$ sudo apt-get install evolution
$ sudo apt-get update

Y tambien el escritorio de ubuntu

$ sudo apt-get install ubuntu-desktop
$ sudo apt-get update

$ sudo apt-get upgrade

Y finalmente los gnome-applets aunque creo que ya los habia instalado el ubuntu-desktop

$ sudo apt-get install gnome-applets
$ sudo apt-get update

$ sudo apt-get upgrade

logout

Luego Ctr+Alt+F7 para salir (no se por que pero con F5 no me deja salir de la terminal, solo se limpia).

El resultado fue absolutamente nada, como sino hubiera hecho nada, reinicie el quipo y misma historia, la verdad ya no se que hacer  cuando revizo el gnome-panel desde la terminal

$ gnome-panel

Obteniendo:

Cannot open display:
Ejecute <<gnome panel --help>> para ver una lista de omandos

Luego recorde las viejas mañas de windows y como aun tengo escritorio por fin meti un lanzador (parece sencillo pero llevo 2 dias en lunix, no tenia idea de que es eso, afortunada curiosidad en el panico) e introduje el comando gnome-terminal y funciono para abrirlo. Si el problema es en GNOME debo asumir que la aprte de terminal esta en otra parte que no me tire, cierto? pues sino ni siquiera me cargaria entorno grafico :S

Lso comandos son las opciones pero de activar sonido o no y ese tipo de cosas, por favor necesito ayuda.

Uso Ubuntu 8.04 LTS Desktop Edition
------

Bueno, cuando hize lo de abrir la terminal me quede pensando si podria forzar de la misma manera a arrancar el gnome-panel y funciono, asi que finalmente volvieron las barras y estan intactas, ojala en la proxima version no se tenga este inconveniente o exista una forma de evitarlo para los primiparos que sobra decir que me meti un buen susto :)

---

### Post by andresic on 2009-05-05
Disculpen que re-tome este tema pero a mi me paso lo mismo con el evolution y segui los pasos que postearon al pie de la letra y el resultado fue que solo me aparece una pantalla negra sin poder entrat a nigun lugar y sin poder hacer nada mas 
que podu haver pasado??

---

### Post by NickCis on 2009-05-05
Segun lo que tengo entendido al desinstalar evolution / etc, desinstalaron ubuntu-desktop (o parte de el), haciendo que muchas de las aplicaciones de las que gnome usaba no esten mas, causando problemas.
Proba instalando ubuntu-desktop:
"sudo apt-get install ubuntu-desktop" y si te dice que ya esta instalado pone esto "sudo apt-get install --reinstall ubuntu-desktop" que para que reinstale.

Saludos, comenta si se te soluciona el problema :P.

---

