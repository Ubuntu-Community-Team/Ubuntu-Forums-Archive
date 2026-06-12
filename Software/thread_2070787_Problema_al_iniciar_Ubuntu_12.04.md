---
title: "Problema al iniciar Ubuntu 12.04"
date: 2012-10-13
forum: Software
---

### Post by Senger on 2012-10-13
Hola a todos, como va?

Soy nuevo por acá, espero estar posteando en el lugar indicado y no romper ninguna regla.

Bueno, la cuestión es la siguiente: Hace unos meses adquirí una PC nueva (que me vino con una copia trucha de Win7) y al día siguiente le instale Ubuntu 12.04 junto con el Win7, para probarlo. Luego de aproximadamente dos meses me di cuenta que no use Win7 mas que para bajar Ubuntu, así es que decidí formatear todo y dejar solamente Ubuntu (ya que me habían quedado algunas cosas medias colgadas).

Hoy a la mañana me dispuse a concretar la labor. Hice un backup de mis archivos, inserte el CD que había utilizado para instalar previamente Ubuntu 12.04 y reinicie.

La instalacion se concreto normalmente, sin ningun detalle. Luego, reinicio la PC para que ya arranque con la version instalada y aca aparece el problema:
1º) Se queda "cargando" un monton de tiempo (da la impresion de que se cuelga, pero luego de 10 minutos aprox logra "arrancar").
2º) La pantalla aparece desfasada. La foto lo describe mejor que mis palabras. Si el mouse lo moves "afuera" de la pantalla, aparece del otro lado al estilo pacman que sale de un lado y entra del otro, y los limites laterales estan al medio (por ahi no se puede cruzar con el mouse).
3º) Si bien dije que arranca, lo puse entre comillas ya que llega a eso que se ve y ahi se queda. Solo se mueve el mouse, pero si cliqueo los botones tampoco responden. Quizas si la dejo mas tiempo ahi sigue cargando mas cosas, no probe.
4º) Lo instale dos veces, por las dudas. Las dos lo mismo.
5º) Un detalle: Cuando lo habia instalado hace unos dos meses, tambien me hizo lo mismo pero luego de reiniciarla una o dos veces algo se "acomodo" y listo... Quedo funcionando al pelo.

[IMG]http://ubuntuone.com/0ihn8BtVsa6bSUlDAxgRm6[/IMG]



¿Alguien sabrá qué puede ser? Por el momento estoy bajando nuevamente el archivo instalador y voy a probar de meterlo en un pendrive a ver qué pasa...

Gracias de antemano.

---

### Post by guillermolisi on 2012-10-13
Antes de seguir instalando y reinstalando, mi recomendacion es actualizar al dia el sistema.

Para ello vas a una consola presionando la combinacion de teclas Ctrl+Alt+F1 (puede ser F1 a F6), procedes a ingresar al sistema con tu usuario y contraseña y luego escribis ```
sudo apt-get update
```
donde te pedira nuevamente tu contraseña (mientras la escribas, el cursor no se movera ni mostrara caracteres en pantalla, asi que presta especial atencion para no cometer errores de tipeo).

Cuando termina de actualizar el cache de paquetes, ingresas ```
sudo apt-get dist-upgrade
``` y aceptas para que actualice todo lo que tenga pendiente.

Una vez finalizada la actualizacion reinicia el sistema y despues contanos como quedo, asi partimos de una base mas firme para aconsejarte posibles soluciones.

---

### Post by Senger on 2012-10-14
> **guillermolisi said:**
> Antes de seguir instalando y reinstalando, mi recomendacion es actualizar al dia el sistema.

Para ello vas a una consola presionando la combinacion de teclas Ctrl+Alt+F1 (puede ser F1 a F6), procedes a ingresar al sistema con tu usuario y contraseña y luego escribis ```
sudo apt-get update
```
donde te pedira nuevamente tu contraseña (mientras la escribas, el cursor no se movera ni mostrara caracteres en pantalla, asi que presta especial atencion para no cometer errores de tipeo).

Cuando termina de actualizar el cache de paquetes, ingresas ```
sudo apt-get dist-upgrade
``` y aceptas para que actualice todo lo que tenga pendiente.

Una vez finalizada la actualizacion reinicia el sistema y despues contanos como quedo, asi partimos de una base mas firme para aconsejarte posibles soluciones.

Hola, gracias por responder!

El problema es que no puedo hacer eso... No puedo hacer nada :(
Una vez que llego ahí, ahí se queda... Solo se mueve el mouse. Lo único que hace es: 1) La prendo. 2) Carga el sistema durante muuuuchoooo tiempo. 3) Llega ahí y dejándola 40 minutos no avanza mas que eso (ayer probé, quizás mas tiempo llegue a hacer algo).

**Edito**: Recién me propuse instalarlo desde el pen drive y entre en el bios para que bootee desde el USB. Cuando hice esto y la reinicie (me había olvidado de conectar el pen) arranco perfecto! Apareció el menú de selección de "modo normal" "a prueba de fallos" y todo eso (que nunca aparece, como que lo saltea), le di al normal y arranco excelente. La reinicie para ver si se había solucionado con eso y vuelve a arrancar mal.

Ahora lo instale desde el USB y pasa lo mismo...

El problema esta en el arranque, quizás sea algo de la configuración del bios. ¿Qué puede ser que haga que no aparezca el menú de selección del principio?



YA SE SOLUCIONO!
No se qué toque... Pero arranco y ya esta caminando.

---

### Post by guillermolisi on 2012-10-15
Para que aparezca el menu del Grub, que te permite elegir que version de Kernel, que modo de inicio, probar RAM, etc., hay que presionar una tecla despues de ver la pantalla de inicio del BIOS de la PC y antes de la pantalla de arranque de Ubuntu. Para ello acostumbro usar Shift izquierdo.

---

