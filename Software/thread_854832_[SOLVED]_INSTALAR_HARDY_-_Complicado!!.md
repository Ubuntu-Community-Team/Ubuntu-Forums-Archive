---
title: "[SOLVED] INSTALAR HARDY - Complicado!!"
date: 2008-07-09
forum: Software
---

### Post by h9005 on 2008-07-09
Buenas les comento que perdi todo mi dia libre tratando de instalar el hardy heron ubuntu studio 8.04 pero no pude!!!! Probe todas las formas y se clava al cargar los programas despues de pedir el proxy, cuando esta cargando el lenguaje... tuve que actualizar el bios y asi y todo no hay caso. A veces avanzó y empezo a descargar los programas pero ahi quedó. Trate de volver a la version anterior (7.10) pero tambien quedaba clavada al cargar el lenguaje. La vez anterior lo mismo, demore muy mucho en instalar ubuntu 7.10. Espero que solucionen estos problemas porque creo que es la principal barrera que aleja a los usuarios del sistema. sigue siendo un dolor de ******* instalar un linux en el sistema... ahora quedo funcionando pero como consola, no carga el modo grafico ni a palos.

---

### Post by pol666 on 2008-07-09
se queda al 83% cuando dice Analizando la Replica (APT)?

Si es eso, saca el cable de red de tu modem, te da un aviso y la instalacion continua

---

### Post by niko_3100 on 2008-07-09
Eso es porque me parece y no estoy seguro que te baja las actualizaciones para estar al dia.

---

### Post by h9005 on 2008-07-09
He probado sacar el cable y no pasa nada, queda ahi, al 28%, o al 42... no entiendo xq se clava tambien antes de eso y tanto...

---

### Post by pol666 on 2008-07-09
Entonses lo que digo queda descartado.

**posibles problemas.**
[LIST]
[*]Disco Rigido con fallas (yo supongo que puede ser eso)
[*]Lectora anda mal
[*]CD mal grabado (esa no creo)
[/LIST]

---

### Post by faktorqm on 2008-07-10
Agarrá y directamente desenchufá el cable de red. Luego pone el cd, al no encontrar red, nunca va a bajar los paquetes, por lo tanto hará una instalación base. Una vez que esté instalado, lo enchufas y te fijas que pasa. Si sigue sin andar, esta vez por otro motivo, proba la memoria con el memtest86+, o bajate el alternate cd e instalalo, primero con red para probar, luego sin red si falló. Salu2!

---

### Post by h9005 on 2008-07-10
Perdon por las malas palabras jajaja. La grabadora es una sata asus con dos semanas de uso. Vuela! El rigido esta particionado para la distro studio 7.10 que costo instalar pero no tanto. El cd no creo porque intente usar la distro anterior 7.10 y se clava en el mismo lugar (al guardar el lenguaje o comenzar a descargar al rigido los programas, despues de que pide el proxy para la apt). Alguna opcion del bios? Tuve que cambiar para que pueda iniciar desde el cd la memoria a configuracion manual, porque sino no entraba.

---

### Post by h9005 on 2008-07-10
Se clava en instalar y seleccionar programas en le 1%... y ahi queda! Alguien tiene fósforos?
Ya no se que mas hacer... puede ser porque el disco sea ata y el dvd sata?

---

### Post by sergiom99 on 2008-07-10
Y si probas con otro CD? o sea, otra version de *buntu. proba con el LiveCD de Kubuntu por ejemplo. A ver que pasa.
Si podes, pasanos que hard tenes instalado, para darnos una idea de que estamos hablando.
suerte!

---

### Post by valucha on 2008-07-10
[COLOR="DarkOrchid"]Tenés los requerimientos mínimos para instalarlo desde el Live CD?... Porque mirá que para instalarlo de esa forma se necesitan más recursos que para correrlo una vez instalado.[/COLOR]

---

### Post by GaBrIeEl on 2008-07-10
eso te está sucediendo porque has instalado anteriormente ubuntu... elimina todas las particiones con el administrador de Mi PC ( en Windows) o arranca desde el cd o dvd de windows y borrales el formato, amí me sucedio eso y es porque habia instalado anterior mente el S.o y lo queria reinstalar dps de aberlo borrado.... Proba haciendo eso, borra la particion del disco en donde lo queres instalar y volver a instalarlo... Hasta luego espero que te sirva de algo :P

---

### Post by h9005 on 2008-07-11
Buenas a todos he solucionado el asunto. Hice lo siguiente: estaba instalando a un rigido ata desde una unidad sata. La memoria impedia iniciar desde el dvd así que tuve que reconfigurarla a manual. Tuve que actualizar el bios también para que me dejara bootear desde el dvd. Aún así una vez que iniciaba ya el instalador sucedian los problemas que postee mas arriba. Probe la version anterior (instalarla de vuelta) pero lo mismo, por lo que conclui que no era el dvd. Deshabilite el sata, puse de nuevo la unnidad dvd ata y listo, funciono sin problemas. Lo único el nuevo sistema no me funciona con la configuracion automática de memoria, sino con la manual. Espero que sirva de ayuda, ya voy a postear los datos de mi máquina.

---

