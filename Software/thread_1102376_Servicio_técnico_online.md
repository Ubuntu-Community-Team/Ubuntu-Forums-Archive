---
title: "Servicio técnico online"
date: 2009-03-21
forum: Software
---

### Post by erdosain9 on 2009-03-21
Hola.  Quería saber cuántas maneras existen para hacer servicio técnico online... hasta ahora sólo conozco vnc... existe otra?
Saludos y gracias

---

### Post by Hei Ku on 2009-03-21
depende para qué. Llegado el caso, podes hacerlo hasta por ftp, irc, o msn. A que estas apuntando?

---

### Post by z37a on 2009-03-21
> **Hei Ku said:**
> depende para qué. Llegado el caso, podes hacerlo hasta por ftp, irc, o msn. A que estas apuntando?

Me parece que lo que quiere es saber como ingresar a maquinas de clientes para ofrecer servicio tecnico.

Tenes varias maneras en Linux(tambien en windows, pero no va al caso), la mas usada creo yo seria el ssh, por este medio podes ingresar rapidamente a otro equipo y hacer lo que quieras, usando poco ancho de banda, la contra que no tenes interfaz grafica(en realidad podes lebantar X desde el otro lado pero no es muy util ya que incrementa el ancho de banda, pero para hacerlo lo haces "ssh [usuario]@[host] -X [aplicacion]"), tambien podes iniciar secion remotamente, en la pantalla de arranque en el login podes usar esta opcion, te come crudo el ancho de banda pero esta buena y tambien claro el VNC.

---

### Post by sebastianabate on 2009-03-24
> **z37a said:**
> Me parece que lo que quiere es saber como ingresar a maquinas de clientes para ofrecer servicio tecnico.

Tenes varias maneras en Linux(tambien en windows, pero no va al caso), la mas usada creo yo seria el ssh, por este medio podes ingresar rapidamente a otro equipo y hacer lo que quieras, usando poco ancho de banda, la contra que no tenes interfaz grafica(en realidad podes lebantar X desde el otro lado pero no es muy util ya que incrementa el ancho de banda, pero para hacerlo lo haces "ssh [usuario]@[host] -X [aplicacion]"), tambien podes iniciar secion remotamente, en la pantalla de arranque en el login podes usar esta opcion, te come crudo el ancho de banda pero esta buena y tambien claro el VNC.

Un problema con estas soluciones es que no te permiten ver el escritorio de la persona que está logueada en ese momento, lo único que te permiten hacer es arrancar nuevas instancias de los programas, o nuevas sesiones (excepto claro vnc).
Otro problema es que cuando no estás en una PC con Linux tenés que instalar Cygwin/X11 (o alguna otra alternativa) para poder levantar cualquier programa gráfico.

Si el soporte online lo tenés que hacer sólo a PC's con Windows podés usar LogMeIn, que funciona de maravillas, y tiene un cliente vía web Java que podés usar en Linux con Firefox sin problemas (yo lo uso con varios de mis clientes)

Si el soporte online lo tenés que hacer a PC's con Linux, la única alternativa a LogMeIn que encontré es [http://www.yuuguu.com/home](http://www.yuuguu.com/home), pero sinceramente no lo pude probar porque el .deb que tienen disponible para descargar es para i386, y yo estoy usando x86-84. Pero si te animás a probarlo contá cómo te fué, para poder tenerlo en cuenta en el futuro.

---

### Post by sebastianabate on 2009-03-24
> **sebastianabate said:**
> 
Si el soporte online lo tenés que hacer a PC's con Linux, la única alternativa a LogMeIn que encontré es [http://www.yuuguu.com/home](http://www.yuuguu.com/home), pero sinceramente no lo pude probar porque el .deb que tienen disponible para descargar es para i386, y yo estoy usando x86-84. Pero si te animás a probarlo contá cómo te fué, para poder tenerlo en cuenta en el futuro.

ACTUALIZACIÓN: Me entró la curiosidad, es feriado, no tengo nada que hacer, por lo que me puse a probar Yuuguu, y la verdad que está muy bueno para dar soporte remoto. Se basa en mensajería; lo que se instala es un cliente de mensajería basado en Java, que tiene soporte para la gran mayoría de los protocolos en uso hoy en día (Gtalk, Yahoo, ICQ, MSN, etc). Una vez agregados los contactos al cliente en cuestión, se tiene la opción de compartir el escritorio con ellos, enviándoles un link que les da acceso directo vía Browser/Java al control de la máquina.
También tiene la opción de dar acceso sin necesidad de tener el contacto agregado, vía un PIN que se tiene que ingresar en la página de Yuuguu (muy práctico para soporte esporádico)

La primera impresión es que refresca la imágen un poco más lento que LogMeIn (aunque no sé si esto se debe a que lo probé contra una máquina virtual que tengo en mi misma PC), pero a diferencia de LogMeIn, te indica cuánto falta para que el refresh se complete (en segundos en la máquina controlada, y en % en el visor web), como para que el técnico sepa si el comando que acaba de ejecutar no funcionó, o simplemente falta que se refresque la pantalla; y el usuario no se impaciente pensando que lo abandonaron.

Otra diferencia con LogMeIn es que es necesaria la intervención del usuario para poder acceder a la PC (si no te invitan, no la podés controlar)

Otro dato es que el .deb que hay disponible es para Hardy, pero yo lo probé en Intrepid y funcionó sin problemas.

Espero que esto te sirva.

---

### Post by sebastianabate on 2009-03-25
> **sebastianabate said:**
> 
Si el soporte online lo tenés que hacer a PC's con Linux, la única alternativa a LogMeIn que encontré es [http://www.yuuguu.com/home](http://www.yuuguu.com/home), pero sinceramente no lo pude probar porque el .deb que tienen disponible para descargar es para i386, y yo estoy usando x86-84. Pero si te animás a probarlo contá cómo te fué, para poder tenerlo en cuenta en el futuro.

ACTUALIZACIÓN2: Hoy un cliente me consultó sobre soluciones de Terminal Server sobre Linux, y por supuesto le comenté sobre [FreeNX]("http://freenx.berlios.de/") (FOSS) y [NoMachine]("http://www.nomachine.com") (Propietario pero con una versión Free de hasta dos usuarios concurrentes), y contándole las características del producto se me vino a la cabeza este post.

Ambos tienen una opción de conexión que se llama Shadow que permite conectarse a una sesión X local ya iniciada (tipo VNC), pero además permiten iniciar nuevas sesiones independientes de las que corre el usuario local, y encima con muchísimo mejor desempeño que VNC y algunos agregados interesantes (transferencia de archivos vía SAMBA, soporte de sonido, impresión remota, etc; aunque sólo con NoMachine). Y todo esto tunelizado automáticamente vía SSH, lo que lo hace muy seguro.
Lo acabo de instalar en una VM (los paquetes de NoMachine; más tarde pruebo con FreeNX), y funcionó de maravillas; y la instalación no pudo ser más simple: bajar 3 paquetes .deb que suman un poco más de 20 MB e instalarlos en la PC servidora (y asegurarse de tener corriendo el SSH en la misma), bajar e instalar el cliente NX en la PC cliente (hay para Linux, Windows, OSX y Solaris), conectarse y... Listo, control remoto de la sesión de cualquier usuario con una calidad de imágen y respuesta en el refresco de la imágen inmejorable.
Sinceramente una opción muy piola para reemplazar al querido VNC sobre vínculos no muy rápidos (teóricamente funciona hasta con conexiones de módem), y además mucho más bersátil.

---

### Post by guillermon on 2009-07-29
Hola sebastianabate (y quien más me ayude): no abro otro post, pues hay muchos sobre escritorios remotos, pero yo no logro entender los pasos. He estado leyendo lo que comentaste sobre Yuuguu, y quizás eso sí lo pueda hacer, pero no entiendo si en la visualización del escritorio remoto se podrán hacer modificaciones (o si solo es visualizar). 
   Describo el problema: por un lado, instalé Xubuntu 8.04 actualizado luego a 8.10 a mi madre, y vivimos lejos. Ella está teniendo problemas sencillos, como no poder crear un acceso directo, etc; muchas partes están en inlgés (lo que lo complica aún más) y por teléfono logramos solucionar lo que aguantan los nervios... Pensé que la alternativa sería que yo ingrese a su pc, haga los cambios, y listo. Pero leo cosas y no es tan sencillo, y para ello yo debería tener muy en claro los pasos para indicarle qué hacer a ella. De ahí que dicho Yuuguu es algo más sencillo (de todos modos si yo veo, es más fácil). Ocurre también que soy curioso, y me gustaría hacerlo.
   ¿qué opinan? ¿hay algún tutorial para lego?

Gracias!

---

### Post by Mauro22 on 2009-07-29
Ubuntu ya viene instalado con el cliente vnc (creo que le dicen vinagre), lo que te faltaria es darle permisos a las 2 pcs de compartir escritorio y poner por ejemplo en nautilus vnc://IP y listo, yo lo hice una vez y no hubo problemas... espero que te ayude

---

### Post by guillermon on 2009-07-29
> **Mauro22 said:**
> Ubuntu ya viene instalado con el cliente vnc (creo que le dicen vinagre), lo que te faltaria es darle permisos a las 2 pcs de compartir escritorio y poner por ejemplo en nautilus vnc://IP y listo, yo lo hice una vez y no hubo problemas... espero que te ayude

Gracias por la respuesta Mauro. Cómo hago para darle permisos? No tendría que tener en claro la ip de la otra pc? cómo hago para conectarme a ella entre todas las pc del mundo conectadas a internet? Me ayudas en estos pasos?
Gracias!!

---

### Post by Mauro22 on 2009-07-29
Para setearlo tenes que ir Sistema -> Preferencia -> Escritorio Remoto

Es algo asi:

[IMG]http://img29.imageshack.us/img29/2620/vinagre.jpg[/IMG]

Seguro algo cambia en la version que tenes vos, este es Karmic.


Ahi tenes las opciones de "Permitir a otros usuarios..."

Mas abajo en "Security" tenes para ponerle la contraseña y eso...



Por lo de la ip hay dos posibilidades, la más facil y sin progrmas de por medio es preguntarla (ejemplo, te metes en "http://www.cual-es-mi-ip.net/" y ahi te sale). La segunda opcion es tener una cuenta en no-ip por ejemplo que lo que hace es mapear la direccion ip, o sea creas una cuenta que diga "oficina.ubuntu.com" y sin importar que ip tengas vos te conectas siempre.

Como veras, es mas rapido la primera y la segunda es por si no tenes a quien preguntarle =D


Esa ventana tiene que ser parecida en Xubuntu y Ubuntu, ya que Xubuntu tiene un aire a Gnome..


:popcorn:

---

